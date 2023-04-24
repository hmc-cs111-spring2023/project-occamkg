# Design notebook entry

## Last week's critique

I looked at the `Run on Save` plugin suggested by Prof. Wiedermann and it worked great for my application!

I also tried fully separating the "slide" sections with whitespace in both my example [element](<https://github.com/hmc-cs111-spring2023/project-code-occamkg/blob/master/work%20files/testPres1/elements.yaml>) file and my example [transition](<https://github.com/hmc-cs111-spring2023/project-code-occamkg/blob/master/work%20files/testPres1/frames.frame>) file and it still works fine, but the transition file does look a little weird with `-->` not at the start of the blocks that have a "transition out" effect before them.

## Description

The main things I worked on were:
- Restructuring how (and when) I render elements
- Allowing for sequences of transitions that chain together (not all start at the same time)
- Making the project render when any of the project files are saved

For rendering elements, I decided to make all elements render as invisible first and then "bubble up" visible when the transition calls for their visibility.
It was a little tricky to get it both forward and backward, but it eventually worked.

For allowing sequences of transitions, I slightly restructured how I store the transition data and then used the `transitionend` JavaScript event listener, so it was actually surprisingly easy.
I didn't create any new example programs, but I modified [this one](<https://hmc-cs111-spring2023.github.io/project-code-occamkg/work%20files/testPres1/presentation>) and I think the transitions are lot cleaner now.

For running the code when a file in a project is saved, I primarily relied on the VS Code extension [Run on Save](<https://marketplace.visualstudio.com/items?itemName=emeraldwalk.RunOnSave>). The user would only need to add a little code to their settings file the first time they use this DSL:
```
"emeraldwalk.runonsave": {
    "commands": [
        {
            "match": "\\.yaml$|\\.frame$|\\.css",
            "cmd": "python <path_to_download>/pres.py \"${fileDirname}\""
        }
    ]
}
```
where they replace `<path_to_download>` with the path that they downloaded this DSL to.
After that, it's pretty straightforward: once the output is generated, you can right click on the file and `Open with Live Server` in VS Code.
Then every time you save the element, transition, or style files, the page in the live server will update and you can see your results immediately.
Additionally, VS Code has a `Show Preview` option, but that is less reliable since it is lacking some current browser features including `@container`s which is how I size most things.
None of these VS Code features are necessary for the program though, so the user can just use it as-is and render it every time they save and refresh the browser manually if they prefer.

One thing I added for the auto render feature is `.config` files for folders that need to run the python script when they are saved.
To set up a project folder, I created a function [here](<https://github.com/hmc-cs111-spring2023/project-code-occamkg/blob/master/program/pres.py>) that you can call and it creates the `.config` file along with the other `.yaml`, `.frame`, and `.css` files.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I was hoping to make my "run" program an executable so the user could type the name followed by arguments to do things like change the project setup, render certain parts, etc.
I saw something about a python library that could convert python scripts to executables, but haven't looked much into that.

**What questions do you have for your critique partners? How can they best help
you?**

Does my method of creating "projects" seem intuitive and helpful?
Are there any suggestions for how I could improve the creation and rendering process?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

I probably spent about 8 hours outside of class working on the project this week.

**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

It has been nice packaging everything up to make my DSL it's own useful tool.
I hadn't really thought much about this at the start of the project, but as the project progressed, I realized it was something I wanted to get out of the project.
However, I did know from the start that I wanted to make it easy to view results of changes made in the code, so this week's work was satisfying for that.