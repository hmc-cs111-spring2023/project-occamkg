# Design notebook entry

## Last week's critique

One thing I found especially helpful for my programming this week was suggestions for features.
For example, some features that were brought up included adding slide numbers, translating elements not off the page, and making it easy to change the order that things show up.
I added the slide number along with on-screen back and forward controls with the number also functioning as a text input for easy navigation.
I created parsing for any transformations, so not only translations, but also rotations, scaling, and skewing are now all possible.
I also kept the syntax clearly separated by transition group (indicated by the `-->`), so it should be easy to reorder by simply cutting and pasting the entire transition in a different place.
Unfortunately the out-transition is usually on the same key press as the next in-transition, so I may try to distinguish these further in the future.
However, I allow for both `\\ inline comments` and `\* block comments *\`, so those can also be used to break up logical groups.

Additionally, I used Prof. Wiedermann's suggestions for using `_` for unnamed elements (it works great!) and instead of writing to an existing JavaScript file, I realized I could write to an individual file and source it before the other scripts in the HTML.
I ended up just storing JSON in this file, but still opted for having it as a JS file so I don't have to use web requests to load it into a variable.

## Description

This week I wrote the parser for transitions and added a few features.
For writing the transition parser, I ended up deciding to have a basic JavaScript file that has the functions all presentations need.
Then separately, I can source the output of my transition parser which I decided to make a JSON list.
Currently, I have it as a list with each element representing a transition and each transition containing a list the elements and effects to apply.
I have all the transitions simplified into three types now: adding/removing classes, adding/removing transformations (translations, rotations, scaling, stretching), and changing element styles

With both parsers working, I was able to replicate my presentation from last week into a [copy](<https://hmc-cs111-spring2023.github.io/project-code-occamkg/work%20files/testPres0/output>) produced by my program from the code.
I also added a new [test presentation](<https://hmc-cs111-spring2023.github.io/project-code-occamkg/work%20files/testPres1/presentation>)!
Some things I wanted to show with this are translating and scaling objects (images in this case), adding and removing classes (the blur added/removed from the text), and full size background images (the puppy!).
The source input for this presentation can be found [here](<https://github.com/hmc-cs111-spring2023/project-code-occamkg/tree/master/work%20files/testPres1>) with the output in the `presentation` folder.
I'm pretty satisfied with the transition syntax, but the element syntax is a bit bulky, so I may look into simplifying it further.
I also added the slide number with some navigation controls, so that will be on every presentation.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

Currently, whenever I want to render a change, I first have to save my file and then run the command `python path/to/program/run.py`.
VS Code already has a very convenient feature (Open with Live Server) that rerenders HTML pages whenever you save anything in the workspace,
but since my code doesn't output the HTML when it's saved, I can't take advantage of this.
Ideally, what I would like is for the user to be able to choose/make a folder for their presentation and then have the code generate blank `.yaml`, `.css`, and `.frame` files.
Then, whenever any files in this folder are saved, it would output the resulting web files.
I'm fine with the user needing to install additional software (such as Python), but I would like this to function on its own once those are installed.

Additionally, I'm always looking for more features to add.

**What questions do you have for your critique partners? How can they best help
you?**

- I'm always open to more feature suggestions since the idea of this DSL is to allow more flexibility than what is in most presentation softwares, so probably a lot of things I haven't even considered.

- If there are any suggestions for how I could make the element code ([example](<https://github.com/hmc-cs111-spring2023/project-code-occamkg/blob/master/work%20files/testPres1/elements.yaml>)) more readable, I would love to hear it.

- One very small, but also very annoying thing I was struggling with was adding transformations.
I can add to the transformation list for individual elements and that works fine, but if the element has class-specified transformations before this, adding the element-specific transformations takes priority and cancels out the class-specific transformations rather than adding to them, so if anyone knows of a good solution to avoid this canceling, that would be helpful.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

Way more than I should have/want to admit.

**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

I really got a lot out of parsing using two different methods in this project: I enjoyed parsing the YAML data structures while also figuring out how to parse my own unique syntax using regular expressions.
I am also adding more features now which is what I was really excited about for this project, so that has been a good (maybe too good) motivation for working on the project.

Also, something I din't think much about in my contract was how I would package up the project, but considering my different options there as well has been a great learning experience.
