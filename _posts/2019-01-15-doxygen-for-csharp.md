---
title: Automatically Generating doxygen Documentation in Visual Studio
categories: [code]
tags: [Csharp, Visual Studio, documentation, doxygen]
---

To automatically generate `doxygen` HTML documentation for your classes after a build, complete the following steps. 

1. [Download](http://www.doxygen.nl/download.html) the binary distribution of `doxygen` for Windows. 
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

## Relevant Variables

| Variable Name (Tag) | Description | Default 
|---|---|---
| ``PROJECT_NAME`` | Single word (or sequence of words in double quotes) that identifies project
| ``OUTPUT_DIRECTORY`` | Relative or absolute directory into which documentation will be written
| ``EXTRACT_ALL`` | Whether to document all entities | ``NO``
| ``EXTRACT_PRIVATE`` | Whether to include private members | ``NO``
| ``EXTRACT_PACKAGE`` | Whether to include package members | ``NO``
| ``EXTRACT_STATIC`` | Whether to include static members | ``NO``
| ``INPUT`` | Files and/or directories that contain documented source files, separated with spaces. 
| ``RECURSIVE`` | Whether subjectories should be searched for input files | ``NO``
| ``GENERATE_LATEX`` | Whether to generate LaTeX output | ``YES``