+++
title = "CodeRED Exploration"
date = "2018-01-04T22:39:50-06:00"
+++

## Nov. 4, 2017 5:00 AM - En Route
Two months ago, I hopped on a charter bus at 5:00 in the morning and headed for Houston. Busy writing and debugging my LC3 programming assignment on my laptop, I didn't even realize at first when we arrived at the University of Houston campus. When I finally looked around just as we were pulling to a stop, I recognized some of the faintly familiar buildings. Over a year ago, CodeRED Curiosity was my first ever hackathon. Now, CodeRED Exploration would be my fourth. My team was completely different this time. It comprised three good friends and fellow UT Austin students: Bala (ECE), Leon (CS), and Max (Math). 

We got off the bus and walked into the student union, led by a friendly event organizer who directed us upstairs where registration was taking place. I was surprised to see unoccupied CodeRED volunteers waiting for us behind a desk, where one year ago there had been an enormous line that snaked around the entire building. This time, the people from our bus were the only ones there. 

For the next hour, we waited in the auditorium where the opening ceremony would be held. Max, Leon and I decided to sit in the front row, much to Bala's annoyance. We tried to come up with a last-minute idea, speaking loudly to each other, trying to think over the terrible electronic music being blasted through the room's sound system. I developed a headache that grew worse over time, aggravated by booming bass notes that rumbled my chest. The crowd behind me was growing too, about doubling in size, but never even approaching what it was last year. Just as I thought I could no longer tolerate the head-rattling output from the subwoofers, the music stopped and CodeRED's head organizer stepped up to the podium to speak. 

As soon as the opening ceremony was over, my teammates and I headed to the business building and scouted for a private room to work in. Finding the doors to every small room locked, we settled with sharing a larger room with other teams. We left our backpacks on a table and headed back to the lobby to find free goodies from the sponsors. 

## Nov. 4, 2017 1:30 PM - Picking a Project
When we came back, other teams had already begun hacking. We knew that we needed to decide on a project, quickly. We had a few ideas that we had come up with in the week before the event, but couldn't agree upon which one to work on. As we debated, I discovered that we each had different goals coming into the event. Leon and Bala were interested in learning something new: machine learning and augmented reality, respectively. Max wanted to try to win a prize by completing one of the challenges given to us by the CodeRED sponsors. I wanted to have a finished product by the end of the hackathon. 

An hour passed, during which we intensely discussed and reduced of our list of ideas through the process of elimination. The first workshop of the day was beginning soon. It was going to be on creating a chatbot with Microsoft LUIS, and we hoped that it would inspire us toward an idea. As we got ready to head off to the workshop room, Leon declared that we shouldn't return until we'd chosen what our project would be. We all agreed.

I quickly found out during the workshop that LUIS was not interesting to me. Rather than following along with the presenter, I took the time to search for a compromise between our conflicting interests. As the workshop wrapped up and everyone began to leave the room, my team and I stood around each other.

"We're not going back until we decide on something," Leon insisted.

Bala made a push for a text messaging idea that he had told us about earlier. It wasn't augmented reality, but he thought it would be fun to use the Twilio API. Leon and Max ended up conceding, and we finally settled upon Bala's suggestion. I was inwardly pleased, as the idea seemed simple enough that we would be able to finish it within 24 hours.

We lucked out on the way back and happened upon a very small, unlocked room. It was normally reserved for business graduate students, according to the sign on the door. We soon found out that the door automatically locked. We had no problem opening the door from the inside, but it was locked to outsiders, which probably confirmed that we weren't supposed to be in the room.  No matter; the worst thing that could happen was that we would be asked to leave. We made the decision to move our belongings to the new room, where we would have a quieter and more focused environment to work. We dealt with the locked door by keeping at least one of us inside the room at all times to allow in the others. 

Perhaps these are superfluous details to you, but my primary purpose in writing this story is to facilitate my own recollection of the event in the future. I'll get on with the main story; a story of how a few inexperienced hackers, working on a supposedly easy project, fell short of their expectations.

## Nov. 4, 2017 3:45 PM - The Google Grind
Bala's idea was to create a service that gave users access to phone numbers in their Google contacts from any SMS-enabled phone. The service would use the Twilio API to have a phone number that users could text. Whenever a user was without their phone, they could use another person's phone to text our service's Twilio number. In their message would be their phone number, some kind of security measure, and a contact name. Our server would look up the contact from Google, find the contact's number, and text it back to the user through Twilio. 

Our first step was dividing into roles. Max and I would work on creating a server that could interact with the Twilio and Google People (contacts) APIs. Leon and Bala would work on setting up a database for the server to connect to. I also came up with the project's name: Lost-n-Phoned, a play on the phrase Lost-n-Found. 

The next thing we did was decide as a team what kind of database we would use to store user authentication data. Bala offered to use what he had learned the weekend before at HackTX to set up a MongoDB instance. However, if we used Oracle Cloud for our database, we would be eligible to win Oracle's prize. We opted for the latter option, hoping that using Oracle Cloud would have the additional benefit of being a good learning experience. 

As Bala and Leon started setting up an Oracle account, Max and I started setting up a Flask project and reading Twilio's API docs. Twilio was surprisingly easy to set up and use; they had a Python helper package with well-documented methods that made life very easy. It was when we got to the Google People API integration that we first ran into trouble. 

First of all, Google's docs were disorganized, spread across multiple websites, outdated, and often contradictory. It didn't take long for us to realize that we were in way over our heads. OAuth2 was not easy to understand, and Google's Python modules for connecting to their APIs were very confusing to use. To make matters worse, Google's code examples had errors in them. For at least an hour, we tried to use a set of their modules as instructed by some docs we found. When we found another page—which told us to use different modules—we scrapped our nonfunctional code and switched over. Later, after the event, I discovered that the modules we were using at first were deprecated! There was no indication whatsoever in the outdated docs. 

Another couple of hours passed with lots of reading, lots of testing, and no progress. Sometime during this standstill, Bala switched tasks and joined Max and I in working with the API. We couldn't get users to give us permissions to their Google contacts, let alone access those contacts. We needed to generate a unique Google authentication URL for the user to visit and log into their Google account. What we did in the end was copy and paste a full example from Google's docs, and then work from there. 

By about 11:00 PM, with the help of fellow hacker Dustin Kazi, we were able to receive a message from a user, reply with a generic authentication link that redirected to a unique Google login page, and then obtain the user's contacts in JSON form from Google. Foolishly thinking that the registration and authentication process was mostly complete, we celebrated and rested as Leon continued working to setup the SQL database. 

## Nov. 5, 2017 12:00 AM - Intermission
We were all exhausted and sleepy by midnight. I asked everyone to come take a walk outside with me, hoping to wake them up and give them the energy to make a final push to finish the project. We moved a trash can to block the door from closing and locking us out, and left. We stumbled upon a close game of real-life Angry Birds at the end of the hall and spectated, hoping to participate in the next game. Unfortunately, we found out after the match ended that that was the final one. 

I suggested that we walk to the student union, where my high school teammates and I had played arcade games the year before during CodeRED Curiosity. When we got there, we were foiled again; we only made it a few steps inside the door before a sanitation worker told us that the building was closed. Not discouraged by our second disappointment, we headed back outside, walked around, and found a building that was still open. Inside it was a curved hallway and an unlocked, empty lecture room where we pretended to be students and teachers. I took a candid photo of my friends in the hallway before we returned to the business building.

![image](/img/bala-leon-max-uh.jpg)

## Nov. 5, 2017 1:00 AM - So Close, Yet So Far
We took turns playing energetic hip-hop music when we got back to our tiny room. Max and Bala worked on formatting the complicated JSONs that the Google People API was giving us while I started reading SQL docs to help Leon. There was something wrong with the SQL commands that Leon's code was sending to his database. Reading up about SQL syntax didn't help except to verify that his commands were already syntactically correct. There must have been a mistake with his table names, or some related oversight. Whatever it was, I realized that I was of little help to Leon. I got out my blanket and laid down on the floor. Max and Bala, having successfully printed the user's contacts on the terminal, laid down as well. I soon drifted off.

My alarm woke me up four hours later, at 8:00. Leon and Bala were awake, staring at their laptops. I'm not sure if Leon slept at all. He greeted me and told me that the database was operational. Too tired to celebrate, I weakly congratulated him.

My head was throbbing and my entire body begged me for just 30 more minutes of sleep. Every little movement required an extraordinary effort, but I forced myself to open my laptop. I pulled Leon's latest code, which was in a separate file named sql.py (Max, Bala, and I had been working in sms.py). Squinting at the code, I discovered that Leon had coded new user registration logic, as well as a challenge-response authentication scheme! Neither were complete, but I could tell he was creating a system where the server sent the user a plaintext number and the user replied with their password (another number) multiplied by the plaintext number. 

We still had not finished the part of the program where the server sends the user their Google contacts—remember, we had only printed the contacts on the terminal—so I got to work. Now that the database was working and Leon had finished his helper functions in sql.py, I needed to connect to the database in sms.py to add the new user's credentials when they authenticated, and then later access the user's Google authentication token whenever they texted our Twilio number a name. 

The thing is, I didn't know that that was what I needed to do. None of us knew how the sms.py code worked at the time. The example code that we had copy-pasted used the flask.session dictionary to store credential data when a user authenticated. Since that wasn't a persistent way of storing credentials, the data would be lost every time we restarted the code. In addition, even if we kept the code running, there was some kind of bug with the way we were handling the credentials. We needed to use the credentials obtained in the `oauth2callback()` function in another function that could send a text to the user. There was no issue with connecting to Google and printing the user's contacts within `oauth2callback()` but for some reason, errors kept showing up when we tried to connect to the Google API within the `twilio()` function.

## Nov. 5, 2017 11:00 AM - Panic Sets In
Hearing a knocking, I opened the door to see a CodeRED coordinator who asked us to move our things downstairs into a mid-sized lecture room. All hackers were being moved into these lecture rooms, each of which hosted several teams. It was there that we would finish our hacks and eventually be judged. 

Our debugging efforts became frantic as time ran out. With only one hour left, we still had not figured out what was wrong. I requested my team's permission to use [FuckIt.py](https://github.com/ajalt/fuckitpy) to ignore the error we were getting, but nobody shared my amusement with the idea. Just minutes before hacks were due, Bala took my computer and added print statements to the program in a series of commits with silly messages, which you can find in [Lost-n-Phoned's git history](https://github.com/ljacob15/lost-and-phoned/commits/master). One minute before the end of hacking, we surrendered and hard-coded the server's responses for our presentation. The server would always reply to the user (one of us) with a phone number that we made up.

## Nov. 5, 2017 1:00 PM - Judging
Judging did not go very well. I knew there was a strong, energetic presenter somewhere within every member of the team, but he must have needed more sleep than the few hours we had allotted because he never showed up. Crippled by sleep deprivation, we completely failed to convey our enthusiasm for the project. Presentations were timed, and we were given only a few minutes to demo Lost-n-Phoned and sell to the judges why it was useful. And yet, we still had awkward pauses where nobody knew what to say or do. We should have been planning what needed to be said in the time we were busy trying to fix the code. 

When we finished speaking, the judges politely nodded their heads. They told us that they found our idea interesting, but not very useful. One lady said that she wouldn't feel comfortable handing her phone to a stranger for them to make texts and a phone call. Other judges agreed, noting that users would have trouble accessing Lost-n-Phoned if they were phoneless because strangers like the judges would not lend our users a phone to text with.

After our presentation was over, we headed downstairs to the food line to eat lunch. CodeRED volunteers were gratuitously placing as many sub sandwiches as they could on each person's plate as they walked through. When it was my turn, they gave me six sandwiches even though I declined all but the first. Someone running the event had evidently ordered way too much Jimmy John's. 

I walked off with my plateful and found my friend Usman from UT Austin eating with his teammates at a table near the food line. My team and I sat down and spent a half-hour commiserating with the other team. Usman's team had had a similar experience to ours; they were working with APIs for the first time and had a great deal of trouble using the Google Maps API. 

Upon returning to the room where we had presented, we were surprised to find a judge waiting for us. There was another round of judging that we didn't know about, with completely different judges, for the Oracle Cloud competition! Again we clumsily went through the pitch, again with enthusiasm lacking from both presenters and audience. These judges too, were unimpressed. Our use of the Oracle Cloud database was neither unique nor creative. 

## Nov. 5, 2017 3:00 PM - Final Moments
We were finally told to walk to a much larger lecture hall in a different building for the awards ceremony. As soon as I sat down, I knew I wouldn't be able to stay awake. I fall asleep during the final presentations at every hackathon I attend, and this one would be no different. Max and I were knocked out almost immediately. I only woke up for a brief moment when I heard Usman's voice from onstage. His team had won something, but I was too tired to pay attention. With my head down and my eyes closed, I clapped as Usman finished speaking and swiftly returned to my dreams.

CodeRED Exploration ended, and my teammates and I were soon in UH's student union, waiting for the bus that would take us back to Austin. My friends were joking about how impressive the team of high schoolers was. Apparently, they had won CodeRED's grand prize by creating a pen which, when used as a normal pen, would save what it wrote as text on a computer. Pretending to be the one of the high schoolers presenting at some future hackathon, Max said, "Do you guys know that thing called world hunger? Let's just say you don't need to worry about it anymore." We all laughed uncontrollably.

We ordered breakfast foods from McDonald's, even though it was well into the afternoon, and sat down at a table to quietly enjoy our last moments at the University of Houston together. I spent the time eating my pancakes and reminiscing about being in the exact same situation with my high school friends one year ago.

We were on the bus within the hour, but were delayed by some missing hackers that were supposed to be on the bus with us. At least one of them was on Usman's team. We eventually left without them, and Usman would later tell me that his teammate had stayed in Houston to do some other business. 

## Nov. 5, 2017 5:00 PM - Reflection
On the way back, I split my time between working on my LC3 assignment and reflecting on the hackathon. As the sun set and my friends slept, I determined that we had made several crucial mistakes. 

The first mistake was underestimating the difficulty of using the Google People API and Oracle Cloud. We should have chosen the idea before we came to the hackathon, and started the learning process earlier. A little experience with the tools that we were using for our project (such as Flask, the Google People API, and SQL) would have gone a long way and saved us some sleep. 

The second mistake was being disorganized because we didn't understand what we needed to do to create Lost-n-Phoned. There were many times during those 24 hours that one or more team members—including myself—did not know what we were supposed to be working on. This got especially bad after midnight as we became tired. Next time, we need to know exactly how our hack will work beforehand and plan out our roles and our code accordingly.

Thirdly, we had some communication problems. The disconnect in goals for the hackathon was a big problem that delayed us a long time from choosing an idea. We should have talked about this long before we got to Houston, not an hour into the hackathon! Also, Leon was on his own working on the database for so long that when he finished, he had coded some things that we had also coded, such as the registration process. In other words, there were functionality overlaps between Leon's sql.py and Max, Bala, and I's sms.py! We should have communicated how everything should be integrated together and what we needed from each other.

Lastly, we did not prioritize coding the core functionality of the hack. The single most important functionality of Lost-n-Phoned is sending the user their Google contacts via SMS. For some reason, we did not realize that the last step in achieving this was non-trivial to get working until the very end. As soon as we were able to connect to the API and retrieve contact data, we should have started working on texting the contacts to the user. Printing their contacts on the console was a step forward, but was not enough to celebrate; the core functionality was still unfinished.

I would later tell my teammates that I thought this last point was our greatest mistake. Weeks after CodeRED, Max told me that he used my lesson of "focusing on the core functionality" for a website that he had been wanting to create.

"I was thinking about learning to setup my Raspberry Pi to host a website," he said, "but then I remembered what you said about core functionality. There's no point in setting up my Pi if I don't have a website, so I think I'm going to learn to code one first."

I think the most important takeaways from CodeRED were:

1. We must know what our project will be before the event.

2. We should learn about and practice using the tools we'll need for the project.

3. If we follow the second point, we should be able to plan most of the project, how it will work, and what each team member's roles will be.

4. During the hackathon, we need to finish coding the core functionality first so that we have something working we can demo to the judges.

It has not been lost on me that the last three points are applicable to *all* projects in general, not just software for hackathons. I guess this goes to show that hackathons really can teach you lifelong skills, even if you aren't big on coding. 

Despite the blunders, I do not regret anything me or my team did at CodeRED Exploration. We had a huge amount of fun and learned a lot from our mistakes. This was the hardest I've ever worked at a hackathon and the closest I ever got to having a fully functioning project by the end of one. I certainly hope I can work with Bala, Leon, and Max again at later hackathons. They are hard-working, bright, and creative guys that I know I can find success with. We have since applied to other hackathons together, but I don't know yet if we'll be admitted into any.

## Nov. 9, 2017 and Onward - The Future of Lost-n-Phoned
A few days after the hackathon, I returned to the code and continued working on the project. I ended up deleting some of Leon's functions in sql.py that were overlapping with sms.py. I also deleted his security functions, which I feel bad about. I should have asked him first, but I think their removal was justifiable because he didn't tell the rest of the team that he was even coding the security, let alone how it worked or how we could use it. Today, the team has yet to come to an agreement about the best way to implement security for Lost-n-Phoned users, which prevents me from finishing the code.

I'll talk about that and the changes I made to Lost-n-Phoned post-CodeRED in my next blog post. 
