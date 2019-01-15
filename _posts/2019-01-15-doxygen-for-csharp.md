---
title: Automatically Generating doxygen Documentation in Visual Studio
categories: [code]
tags: [Csharp, Visual Studio, documentation, doxygen]
---

To automatically generate `doxygen` HTML documentation for your classes after a build, complete the following steps. 

1. [Download](http://www.stack.nl/~dimitri/doxygen/download.html) the binary distribution of `doxygen` for Windows. 
2. Create a folder `docs` within the main project. 
3. Execute the following command to generate a `doxygen` configuration file. (Put it in the `docs` folder.)
```
doxygen -g CustomList.doxygen
```
4. Set the following variables in the `doxygen` configuration file: ``PROJECT_NAME``, ``OUTPUT_DIRECTORY``, ``EXTRACT_ALL``, ``EXCLUDE``, ``GENERATE_LATEX``
5. Add the following line to the "Post-build event command line" text box under the [project's build events](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-specify-build-events-csharp). 
```
doxygen $(ProjectDir)docs\$(ProjectName).doxygen
```
6. Rebuild your project.