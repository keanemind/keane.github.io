+++
date = "2017-02-26T10:15:37-06:00"
title = "Automated deployment"
Best = true
+++

![image](/img/cogs.png)

On Friday, I spent a few hours of trial and error setting up automated deployment for this website. Automated deployment allows me to update my site more easily. First, I push changes to my website's source files to a source branch on my Github pages repository. Then, a Wercker application I set up builds my website from the files in the source branch. Finally, Wercker pushes the built website files to my master branch and the changes can be seen on the actual website. In this post, I'm going to journal what I did to set this up. 

I initially got the idea for the whole setup from [Peter Chuang's blog](https://novelist.xyz/tech/hugo-site-deployment-workflow/) (his blog is also the reason I'm using Hugo to create this website instead of Jekyll). I liked the idea of being able to track changes to my website source files on Github while using Github pages. However, I didn't like having to make changes to my source, push the changes to my source branch, build the website, and then push the new website to my master branch. Peter linked to [another blogger (Roman Coedo)](http://rcoedo.com/post/hugo-static-site-generator/) whose instructions he followed. Roman used Travis CI to automatically build and deploy his website to Github pages. I read his post, and his instructions required me to install Ruby. I didn't feel like doing that, so I looked for another guide elsewhere.

After some searching, I stumbled upon an [automated deployment tutorial](http://gohugo.io/tutorials/automated-deployments/) in Hugo's official documentation! This guide used Wercker instead of Travis CI, and did not require me to install anything. This all seemed great, but I quickly found three problems with the guide:

1\. The guide was rather outdated (I later discovered it was last updated in November 2015). As I followed the instructions, many of the screenshots were completely different from how the Wercker website looks today. Entire sections of the tutorial were impossible to follow because Wercker had changed.

2\. The guide neglected to describe how to give Wercker the theme for building my website. Following the instructions exactly caused Wercker to fail with an "Unable to find theme Directory" error.

3\. The guide only described deploying to a project page, not a user/organization page. This meant the guide covered deploying to a gh-pages branch, not the master branch. Since my Github pages repository is a user/organization page, the website files must go into the master branch. This seemed like a small issue that would be easy to work around, so I thought little of it.

[//]: # (It looks like Cocoa-eh doesn't allow for numbered lists. It forces bullets. Fix this?)

I followed the guide as closely as I could until I hit problem #2. Looking at the [source code](https://github.com/ArjenSchwarz/wercker-step-hugo-build) for the Wercker step the tutorial was having me use, I realized that the step did not install any Hugo themes even if you told it you wanted a certain theme. This meant that I needed to tell Wercker to download a theme. Clueless as to how Wercker worked, I looked at [Roman Coedo's Travis CI configuration file](https://github.com/rcoedo/rcoedo.github.io/blob/source/.travis.yml#L22). I looked up how to do bash commands in the Wercker documentation and then I adapted Coedo's script to my own Wercker.yml file like so:
```yaml
    - install-packages:
        packages: git
    - script:
        name: download theme
        code: |
            $(git clone https://github.com/keanemind/cocoa-eh-hugo-theme.git ./themes/cocoa-eh)
```
Since I modified the Cocoa-EH theme for my own use, I created a repository on Github for my theme and instructed Wercker to download that. 

Next, I spent some time trying to figure out how to get the deploy part of my Wercker.yml file working. It seemed like Wercker was completely ignoring the steps under deploy. Eventually, I figured out that Wercker had changed since the Hugo guide was written; I needed to create a deploy pipeline in Wercker. I did so, and then chained the deploy pipeline to the build pipeline. 

Now Wercker was finally running the steps under deploy. For the first time, Wercker completed both the build and deploy pipelines. I was elated to see that Wercker did actually upload the built website files to my Github pages repository. However, it created a gh-pages branch and uploaded them there instead of replacing my website in the master branch. I took a look at the Wercker step I was using for deploying. The creator, Luke Vivier, wrote in the instructions that I should have been able to specify which branch to deploy into. In the [source code](https://github.com/lvivier/step-gh-pages), it looked like specifying "branch: master" in my Wercker.yml [should have worked](https://github.com/lvivier/step-gh-pages/blob/master/run.sh#L39). But I didn't know enough of what was going on to figure out what was wrong, so I [forked](https://github.com/keanemind/step-gh-pages) the Wercker step and modified the code so that it always deployed into the master branch. 

Now I needed to make my fork a Wercker step so that Wercker would be able to find it and run it. I tried to submit my fork into the Wercker registry, but Wercker complained that the branch variable was unused because my change made it useless. I had to remove a section of code where the script determined what branch it should deploy to. Finally, Wercker accepted my step and I modified my Wercker.yml file to use it instead of Luke's step. 

I made a small change to my website source and pushed it to my Github source branch. After about two minutes, my master branch was replaced with the new compiled website and the change could be seen on my website. I was finally done.
