# Design notebook entry

## Last week's critique

The main way I worked with the feedback was by taking the suggestions of similar examples and doing more research into those.
Since one comment was about it seeming like Prezi, I explored various example Prezi presentations and, although I do like that they are more fluid with everything being spatially connected, their structure is still relatively restrictive in my opinion with their fixed linear flow and hierarchical branching.
So I may borrow some of the Prezi features, but hope to offer more beyond their structure.
I looked at interactive videos as well and their capabilities are more in line with what I want to create, but I don't want my presentations to need a video base and want them to be more aimed toward an output that someone could use to present rather than something someone would explore on their own.
So again, I could definitely use some of those features, but since it's a slightly different domain, I want to tailor mine more toward presentation capabilities.
I looked a bit at React and Swagger which were a couple suggestions in class, but I was unable to see how they would apply to my project.

I've thought a bit about what my intermediate representation will be and am currently thinking it will be a list of HTML components with a separate CSS output for styling for the elements and a list of JavaScript instructions for each transition.
This is definitely likely to change though once I actually start implementing it.

I also agreed that it is very helpful to have specific ideas prepared for class so I can get helpful feedback, so I considered how I will condense my main ideas here to highlight what I most need help with and also give a clear description of where I am so far.

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

The main things I worked on this week were creating an [example output](<https://hmc-cs111-spring2023.github.io/project-code-occamkg/work%20files/basicPres0/example%20output>) and designing an [example syntax](<https://github.com/hmc-cs111-spring2023/project-code-occamkg/tree/master/work%20files/basicPres0/example%20syntax>).
I spent most of my time on creating the output because I also needed to refamiliarize myself with web language programming.

I got a lot of the basics down in terms of what I will need for every output.
For example, in the JS file, I worked on how to translate the keyboard input into navigating the presentation timeline, which is a fundamental part of presentations.
Similarly, in the style, I figured out how to make a content area that can be defined by the aspect ratio and fill the screen no matter its shape which is also essential for presentations that can function consistently.

I kept the example pretty basic (only text elements so far), but I wanted to add capabilities that exemplify how these web languages can expand presentation capabilities, so I made sure to include transitions that affect style of different elements (I changed size and opacity of text).
I also had fun messing around with transitions and tried to replicate typical slide transitions as simply as possible by creating a `flyOutRight` effect.

For the syntax, I tried coming up with a way to express my example output efficiently and clearly (not very successfully).
I separated out the class styling because I think that should just remain as pure CSS.
I may change this if I want to add my own styles and have them be as easy to add to classes as the built-in styles.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I must admit, the syntax I have is not great.
I was fixated on the idea that I should have two sections: one for presentation elements and one for transitions, but it feels a bit unnatural.
I was considering splitting them into separate files like HTML and JS, but since the transitions all use the elements by name, I'm not sure splitting the files would be best for the user.

I am also very unsatisfied with my use of many brackets and braces.
It makes this language more like a very large data structure than a language, which I think makes it less intuitive.
I _did_ distinguish between brackets and braces by using `[brackets]` when order matters and `{braces}` when it doesn't, but I'm not sure that helps much.

**What questions do you have for your critique partners? How can they best help
you?**

I think the biggest questions I have are about my example syntax.
Firstly, I would like an honest opinion about how readable it is currently.
Would separating the elements and transitions into separate files make it more or less readable?
Secondly, I would appreciate any suggestions for how I could make it more intuitive. Is there any grammar that seems excessive and can be cut? Does there seem to be some grammar missing that could make the code more readable?

Also, I appreciate any comments on similar programs I can look into.
I liked looking into the other presentation softwares to see possible features I could incorporate into my project as well as analyze the limitations of current programs and consider how I could avoid those limitations where appropriate.

Finally, if there is anything in my example output that seems like it could be written more cleanly, I am open to any suggestions.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

I probably spent around 8 hours outside of class because I needed to work a lot on getting familiar with CSS and JavaScript again.

**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

Well I didn't work at all on parsing/interpreting, so I'm not as far as I had expected, but I think a lot of what I learned working on the project this week will make adding presentation features (my future milestones) much easier.
Also, I feel like designing a syntax without feedback before developing parsers/interpreters is probably not a good idea anyway, so making a fundamental working parser and interpreter can be my next week's goal.

However, despite my progress not aligning with my goals, I really enjoyed my work this week and what I got out of it.
I thought a lot about syntax decisions and many possible ways to convert the syntax into my desired output.
