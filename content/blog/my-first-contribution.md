+++
date = "2017-03-03T00:18:22-06:00"
title = "My first open source contribution"
+++

![image](/img/gitmerge.png)

I felt so cool when I first started using Github to manage my little Python scripts a month ago. I felt like a pro; I was using the same system that countless other programmers use daily to build well-known projects. I felt potential: would my Github profile one day be full of awesomeness? 

It seems like everyone says to start off by contributing to a project on Github. It's pretty intimidating though! All of the code I see on Github is way over my head. And what if I make a mistake? But I found a way to start small as I set up this website. The Hugo documentation is pretty disorganized, and it was a struggle for me to understand what was going on when I first used Hugo. The documentation for this site's theme, Cocoa-EH, is also very lacking. I occurred to me that Hugo really could use my help in improving its docs. 

Well, as of today, I have given my help to an open source project; a Hugo collaborator accepted [my pull request](https://github.com/spf13/hugo/pull/3103) to update the official [tutorial on setting up automated deployment with Wercker](http://gohugo.io/tutorials/automated-deployments/). Here's how it all went down… 

Last week, I went through the frustrating process of [setting up my website to be automatically deployed to Github](/blog/automated-deployment/). I spent hours cursing at my computer monitor, figuring things out through trial and error. Somewhere along the line, I decided that I would go back and update the guide once I figured everything out. 

And that's what I did last weekend: I forked the Hugo repository and fixed the broken links, the out of date screenshots, the obsolete instructions. I pasted everything into Word for a spell check, and then submitted a pull request. I watched as Hugo's various continuous integration services checked my PR. Honestly, it seemed pretty silly that they checked my build even though all I edited was docs. 

"Whatever," I thought. 

Slowly, four green checks appeared. "All checks have passed," Github said. 

It was time to wait for approval.

I regularly checked Github for the next two days, impatiently waiting for my request to be approved so that I could write this very blog post about it. Finally, my request was approved. I excitedly looked at the tutorial on Hugo's website to admire my handiwork. Everything looked perfect until I got to the very bottom of the page. The last revision date was way off! It was showing the date that the tutorial was first created, not the date that I had set for "lastmod" in the post's front matter. 

I posted a comment on my pull request asking what the cause was. A Hugo collaborator pointed out to me that the CI builds had actually printed an error in their outputs saying that my "lastmod" setting couldn't be parsed. I had put "lastmod: 2017-**2**-26" instead of "lastmod: 2017-**02**-26". Apparently, CI builds actually do matter, even if you're not touching the software's code! From now on, I will always be thorough and check the CI outputs. 

Anyways, another pull request later and I had corrected my little mistake. At last, my work was done. Today you can view my changes to the tutorial in all their glory [on Hugo's website](http://gohugo.io/tutorials/automated-deployments/)!

After that first experience, I feel a lot more confident about giving a small helping hand to some big projects. I'm more excited than ever to make more pull requests on Github. For now, my contributions will mostly be in documentation because I encounter a lot of open source projects with spotty and disorganized docs. I see this as a big problem; good docs help new users (like me) pick up programs (like Hugo) with minimal frustration. I want to be a part of ensuring that open source documentation is organized, well-written, and useful. 
