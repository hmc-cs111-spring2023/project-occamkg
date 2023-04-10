# Design notebook entry

## Last week's critique

I think the biggest decision I made based on the critique were syntax changes.
Firstly, I separated the element and transition files since that seemed like there was a general consensus on that.
Also, I realized that the transition syntax is regular which makes things easier, whereas the element syntax is not.
To help with parsing that, based on Prof. Wiedermann's suggestion I decided to actually slightly modify my syntax to fit with YAML which has already built interpreters making it easy to parse.

I also liked the suggestion of separating the elements and transitions by frame, so I made sure the syntax would allow that (although I don't enforce it).
I also thought a bit about what defaults I will want to have since that does seem to be a pretty useful standard feature when designing presentations.
I currently have some default styles in a sheet I will link to every output HTML (that can easily be overwritten), but in terms of parsing, it's a bit more complicated to make sure the right elements have the right default styles etc.

## Description

This work I primarily worked on trying to interpret the element syntax I have into a preliminary HTML file.
This also involved changing my syntax quite a bit as I made design decisions.
Since I switched to YAML, it was pretty straightforward to parse the syntax into a usable form, but writing the HTML proved to be a bit more difficult.
I tried several different libraries that each had their strengths and weaknesses, but eventually I settled on `lxml` since it allows straightforward creation of DOM elements, can parse HTML files and HTML text, and can easily select DOM elements based on selectors (with the help of `cssselect`).

In terms of the actual logic of my interpreter, I tried to keep it pretty basic so it would allow for creating the basic case I made last week.
I know I'll definitely have to change a bit to make it more flexible for different designs (especially in terms of layout), but I tried to make it codable later on without too much reorganizing of the parsing process.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

Currently, I'm still very open to any feedback about the syntax.
I changed the transition syntax a bit and I'm planning to make the interpreter for that this week, so I guess any ideas of what's good/what could be improved with that syntax would be most helpful.

I also haven't looked at how the regular parsing works yet nor good practices for editing/writing JavaScript files with Python, so if there's any pointers for either of those, that would be helpful.

I'm still definitely going to be doing a bit of work on the element interpreter, so I am open to feedback on how that functions as well, but don't currently have any specific questions about it.

**What questions do you have for your critique partners? How can they best help
you?**

The main questions mostly from above are:
* Does the transition syntax seem reasonable? Could it be improved?
* Do you have any suggestions for where to start with regular parsing?
* Do you know of any good Python libraries for editing/writing JavaScript files?
* How does the modified YAML syntax for elements seem? I don't want to change host syntax now, but any suggestions within the YAML constraints would be helpful!
* Does my parsing strategy seem reasonable? I haven't gotten a chance to comment much, so if it's unreadable, no worries.
* What presentation functionalities would be useful/interesting to you?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

I probably spent about 8 hours outside class this week.

**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

I definitely learned a lot about parsing and it was fun to consider the logical flow for how to interpret this context free syntax.
I especially liked working with how to manage references to other objects by name.

When converting my syntax to YAML, it also helped me think critically about what I really needed in my language and what I didn't.
Most of it actually made my syntax cleaner and more concise in my opinion, but one thing I wasn't quite able to satisfactorily resolve was how to create elements without names (if the user doesn't want to name them and doesn't need to reference them).
