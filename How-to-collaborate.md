There ain't no such thing as a [free lunch](https://en.wikipedia.org/wiki/There_ain%27t_no_such_thing_as_a_free_lunch). If you want a better portapack, there is no better way to get it than collaborating.

# Write documentation

There is a lot of missing documentation about all the features, so it is really important to write clean and detailed instructions for them. In this current wiki, you can modify or add new content with a normal Github account. 

1. Select a topic you think you can master. It can be an specific app, function of an app or feature or procedure related with your PortaPack
2. Check the following sources:
    * https://github.com/mossmann/hackrf/wiki
    * https://github.com/furrtek/portapack-havoc/wiki
    * https://github.com/sharebrained/portapack-hackrf/wiki
3. To create a new section, you have to edit the sidebar and then edit the page. To modify any actual section, just do it directly. Try to follow the same language and style used in the other articles of the Wiki.

For learning about the text formatting, check the [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

# Coding new stuff or fixing bugs

I know what are you thinking: "I am not an expert, I do not know C++, I am not capable, etc", but nobody really is until they do. The easiest way to get a bug fixed or a new feature is to code it yourself.

So, setup the environment and compile the code as instructed below. Modify something dumb: the title bar of an app, some button, ... compile again and test. Try to understand how things works; this is exactly how everyone gets involved. 

> While you learn, you can add comments and rename variables if you think it will help others to understand the code. **This is also a very appreciated contribution.**

## Environment setup

### Fork the repository
1. Download and install [Github desktop](https://desktop.github.com/)
2. Log to Github, open the [repository](https://github.com/eried/portapack-mayhem) and click **Fork** on the top right
3. In your Fork, Click **Clone** and **Open in Desktop**
4. Follow the rest of instructions in Github desktop

### Prepare for compilation
1. [Compile your fork](Compile-firmware)
2. As noted in the details on the previous step, the first time _it might_ take a long time to finish. The result will be left on the `build` folder, on the root of your fork

## Start coding

You can check the following [brief video](https://youtu.be/cYLzmMFe7-E) that shows the most of the steps described below.

### Work on the code
1. Install [Visual Studio Code](https://code.visualstudio.com/download)
2. Open the root directory of your local copy of the Fork
3. Change something
4. Run the image from Kitematic to compile
5. Go to step 3 until finished

It is recommended to work in [branches](https://help.github.com/en/desktop/contributing-to-projects/creating-a-branch-for-your-work), but as a beginner, it is ok to work on your master branch. 

Create [commits](https://help.github.com/en/desktop/contributing-to-projects/committing-and-reviewing-changes-to-your-project) with your changes after you complete them. 

Just keep in mind:
* Keep it simple, the fewer commits, affected files and lines, the better
* Use a descriptive name for the commits, add the URL of the issue if you were fixing something specific
* The project needs to compile successfully after each commit

### Submit your changes
This is the last stage. Your new feature or fix is ready and this is how you submit the changes:

1. Publish the branch (if necessary) and push all the commits
2. Do a [pull request](https://help.github.com/en/desktop/contributing-to-projects/creating-an-issue-or-pull-request). Use a descriptive title and description if you think is necessary
3. Just follow the interaction on Github now