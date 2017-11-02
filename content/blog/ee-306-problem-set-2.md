+++
title = "EE 306 Problem Set 2"
date = 2017-10-26T16:56:32-05:00
+++

"Implement F = A xor B using only two 2-to-1 muxes," Andy muttered. Andy, Bala, and I had just sat down in Thai, How Are You?, a restaurant on the Drag. Our menus were on the table, but we were looking down at our notebook journals, more concerned with ordering mux inputs than food. Andy's voice echoed in my mind. Labeled 5b, the words at the beginning of this paragraph were typed up in Problem Set 2 of our EE306 class. The challenge, just a few words long, sounded tantalizingly simple. We merely had to wire together two muxes in such a way that the combination outputted the XOR of the inputs. 

A mux:
![image](/img/mux.jpg)

The assignment was to make connections so that the combination of the two muxes would be an XOR:
![image](/img/two_muxes.jpg)

What a solution would look like:
![image](/img/two_mux_solution.jpg)

In a follow-up email to the class, Dr. Patt taunted us: "You could spend hours looking at the two muxes and not figure it out," he wrote. Not ones to back down from a challenge, we had spent the entire morning thinking the problem over. It was now late in the afternoon, and I had no idea how to even approach the problem anymore. What was the logical way to think about it? What is the meaning of XOR, and what does a MUX truly do? My mind blanked. It didn't even feel tired anymore; it felt numb.

"What would you guys like to drink?"

I looked up to see a waitress, who gazed back down at me expectantly.

"Water, please," we each said in turn. 

Sufficiently disrupted from our deep thought, we put down our notebooks and began perusing our menus. I ordered the safest choice, Pad Thai, because it was my first time at the restaurant. What followed was a pleasant chat with my two friends as we let the problem rest.

Time flew by, and I relaxed. Question 5b drifted further and further into the back of my mind as I enjoyed my lunch… 

Finally, we reached a point where our plates were empty and a lull in our conversation formed. 

"I got it," Andy said suddenly. "I was thinking about it this whole time while we talked. I got it now."

Of course, he was talking about 5b. I locked eyes with Bala. We shook our heads at each other, holding back smiles. Andy was trolling, and we both knew it. With a despicable grin, Andy quickly drew this:

![image](/img/andy_solution.jpg)

"See? Trivial," he added. 

Bala rolled his eyes as I simply looked at Andy, straight-faced.

"Alright, fine. I actually just wrote something random down," he laughed. 

"Let's try the truth table anyway," I suggested. It couldn't hurt to try.

We started checking the truth table produced by Andy's logic gate diagram against the truth table of an XOR function. There were four combinations of inputs and outputs. We quickly confirmed that the first two combinations were correct. There were thousands of possible ways to connect the muxes. Yet, as we checked the last two rows of the table, we were all thinking the same thing. Do I even need to say the rest? Of course he got it. Somehow, improbably, Andy had managed to randomly write down the solution.

None of us were satisfied with randomly stumbling upon the answer. I don't remember whether it was Andy or Bala, but one of them came up with the idea of solving the problem by writing a program to brute force all the possible ways to connect the muxes together. The program would check the truth table of every result and compare it with XOR for us. It sounded like fun, so we set off to the library with a mission in mind. Soon after we got there, we realized that we all use different languages; Andy likes C++, Bala is more familiar with Java, and I only know Python. On top of that, we each use different text editors! I saw the perfect opportunity for a contest.

Five minutes later, we were racing to write a working brute forcer. It was harder than I thought to plan out my script. We had to find every combination of the possible inputs A, B, 1, and 0. The confusing part was that we had to plug in 0s and 1s into A and B while checking the output against the XOR truth table.

It was a fun little thought exercise, which I somehow ended up winning. I had a bunch of for loops, and inside the deepest loop I plugged into A and B to check the output. By coincidence, the first solution that my program outputted happened to be the exact solution that we already knew was valid (thanks to Andy's good fortune). In the end, we determined that there were 8000 possible ways to wire the muxes, and 4 of those ways resulted in an XOR. 

[Here's the link to my brute force program.](https://github.com/keanemind/EE306/blob/master/5b_brute_forcer.py)

After that episode, we still had to finish the rest of the homework. We spent the entire evening working with other electrical engineering students on the rest of the problems. I still regret not taking a picture of five of my friends, crowded around a whiteboard in the Perry–Castañeda Library, trying to create a four bit comparator. It was one of the few times that I had my camera with me, and I missed my chance to memorialize that iconic moment.

We kept working in the library until it closed for the night and a security guard kicked us out. We went to Wendy's afterward and took a break, and then went to Vishruthi's (one of the people I was working with) room. Only then did we finally figure out how to implement the comparator.

That was a fun and memorable day even if it was a lot of hard work. I never thought I would enjoy spending a whole day on homework, but it makes more sense if I view it as spending time working on puzzles with friends. Being an EE student so far has had its ups and downs. I'm enjoying the challenge, but I'm unhappy that I don't have much free time to do things other than coursework. Perhaps this is more indicative of flaws in my time management abilities than my major. After all, my roommate Sammy is a fellow EE major who is more disciplined and efficient than me, and he seems to have a lot of free time on his hands.

I'll have to figure out how to work more efficiently soon; I'm going to be spending my next two weekends at hackathons, despite having an exam every week. I can only hope I'll survive it all to tell the tale, in future blog posts. 
