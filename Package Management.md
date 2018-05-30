# Guidance on package management 

## Packrat Guidance

This Guidance will walk you through some of the most common tasks you’ll want to do with packrat, and explain the fundamental concepts behind Packrat package.

# Set up
You’re getting ready to start a new project, so you create a new directory that will eventually contain all the .R scripts, CSV data, and other files that are needed for this particular project.

You might need to make use of several R packages over this project. So before you start writing your code, make sure you set up the project directory to use Packrat with **packrat::init:**

```
> packrat::init("path")
```

In case the current working directory is the project directory, you can omit the "path".

After initializing the project, you’re in a Packrat project. That means that you have your own library. Any packages you install from inside a packrat project are only available to that project. Any packages you install outside the packrat project will not be available to your packrat project.

# Manipulating packages
