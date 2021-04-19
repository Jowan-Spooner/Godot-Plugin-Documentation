# Easy Godot Plugin/Addon Documentation

A simple way to add documentation to a plugin/addon.

*The documentation used in the dialogic plugin (WIP):* 
![grafik](https://user-images.githubusercontent.com/42868150/115240238-d4222e00-a11f-11eb-98d1-5a3495192519.png)


## How to use
This repository is supposed to be something you can add to your plugin as fast as possible.

To use this, download the repository. Add the Documentation folder to your plugins folder.

All the content you want to show in your documentation goes into the subfolder 'Content'.
This project is supposed to work with markdown files, like the ones on github.

There are multiple ways to include the documentation in your addon/plugin:

- You can use the DocumentationViewer.tscn file. 
  Just add it to your plugins page (maybe as a tab or something similar). 
  This option should work out of the box.

- Use the premade building blocks DocsPageViewer.tscn and DocumentationTree.tscn.
  These are easy to integrate into your code. Just have a look at the DocumentationViewer scene.
  You can also easily add the documentation tree to an existing tree you have (like dialogic).

## Background
This was originally created for the dialogic plugin by emilio coppola. 

