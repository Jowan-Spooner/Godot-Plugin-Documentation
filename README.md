# Easy Godot Plugin/Addon Documentation

A simple way to add documentation to a plugin/addon.
⚠️ *Disclaimer: This is a work in progress. You can use it however you would like. But don't blame me if something doesn't work.*
This is supposed to work with a plugin that uses a main editor view!

*The documentation used in the dialogic plugin (WIP):* 
![grafik](https://user-images.githubusercontent.com/42868150/115240238-d4222e00-a11f-11eb-98d1-5a3495192519.png)


## How to use
This repository is supposed to be something you can add to your plugin as fast as possible.
Right now it can take a moment to integrate, but it works OKAY.


To use this, download the repository. Add the Documentation folder to your plugins folder.
Because this was designed for dialogic, you will have to fix some dependencies. I hope I can work on this so it works better out of the box.

Before starting to use the files you should add the DocsHelper singleton.
Do this in the \_ready() func or the \_enter_tree() func of your plugin script:
`add_autoload_singleton('DocsHelper', "res://addons/<YourPluginName>/Documentation/Scripts/DocsHelper.gd")`

All the content you want to show in your documentation goes into the subfolder 'Content'.
This project is supposed to work with markdown files, like the ones on github.

There are multiple ways to include the documentation in your addon/plugin:

- You can use the DocumentationViewer.tscn file. 
  Just add it to your plugins page (maybe as a tab or something similar). 
  This option should work out of the box.

- Use the premade building blocks DocsPageViewer.tscn and DocumentationTree.tscn.
  These are easy to integrate into your code. Just have a look at the DocumentationViewer scene.
  You can also easily add the documentation tree to an existing tree you have (like dialogic).

## What it can
The markdown parser was built on fenix-hubs markdown parser. [(FenixHub)](https://github.com/fenix-hub/godot-engine.file-editor)
It can show:
  - Headings 1-5, customizable styles
  - **Bold**
  - __Underlined__
  - *Italic*
  - `Mono`
  - ~~strikethrough~~
  - Links (also links to sections)
  - Images, if they are contained in the Contents folder (or a subfolder)

### Links
Links can be quite compley: 
  - If they go to an outside website, they will be opened in the browser.
  - If they go to a file in the Contents folder on github, it will try to open the corresponding file in the Content folder.
    E.g.: "https://github.com/Jowan-Spooner/dialogic/blob/plugin-docs/addons/dialogic/Documentation/Content/Tutorials/Images/Event_Choice.PNG" will work just fine, because it is contained in the Content folder. Godot will look at "res://addons/.../Documentation/Content/Tutorials/Images/Event_Choice.PNG"
    Through this, these links can work on github as well as in godot.
  - If they start with a # the DocsViewer will try to scroll to that section (like on github)
  - If they are just text (a godot path), the viewer will emit a signal.
    This signal can be easily interpreted as an open call, so that the page will be opened with the viewer.

Images can also have both links from inside the Contents folder or their corresponding github links. This way images can also work both on github and inside godot.

### Built a tree
The DocsHelper class can be used to add all necessary tree-items to an existing tree. With just a few lines of code, that tree can also be filtered.

### Page titles in the tree
The pages will take their titles from the first line of the file. They don't use the files name, so you can "rename" your page without breaking all the links.

## What it can not
Currently there are some things not possible to show, partially because I didn't add them yet, and paritally because the RichTextLabel isn't capable of doing so:
  - ***Bold and italic at the same time***
  - > Quotes
  - Break Lines

## How to edit the documentation
You can change the content however you want, for example by using a plain text editor.
But there are two things to think about, especilly if you want your docs to work on github AND in godot: Links and Images.

The best practice is to use relative links (like "./image" if the image is in the same folder like the document) for both. If you are working on github, you can alternativly use the github links, the scripts can handle them in godot.

In both cases it is good to NOT USE SPACES in the filenames. Github has a problem with them because links cannot contain spaces.

Two make editing the docs from godot easier, the DocsPageViewer has a enable_editing variable exported. Look for the DocsPageViewer you are using in your plugin. Enable the setting. There are two buttons in the corner now. Refresh and Edit. They can speed up your work quite a lot.
![grafik](https://user-images.githubusercontent.com/42868150/115277771-f4181880-a144-11eb-89ab-f69dddaf6893.png)


## Background
This was originally created for the dialogic plugin by emilio coppola. 
I took some code from the file editor plugin by [(FenixHub)](https://github.com/fenix-hub/godot-engine.file-editor).

