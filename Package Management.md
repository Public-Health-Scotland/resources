# Guidance on package management 

Package management ensures that R packages used within a project are tracked and that if someone else works on the project, they will have the correct versions of the correct packages. This helps mitigate the risk of different versions of packages leading to different users obtaining different results. 

There are several ways of doing this using R using R packages (packrat or checkpoint), distributions of R dedicated to package management (Anaconda) or software such as Docker. Within Transforming Publishing, the main method of package management is packrat. The majority of the guidance contained in this page is for packrat. 

## Packrat resources
- [Packrat basics](https://rstudio.github.io/packrat/) - introduction to packrat and its benefits
- [Packrat walkthrough](https://rstudio.github.io/packrat/walkthrough.html) - step by step guide on using packrat for package management
- [Managing package dependencies with packrat](https://www.rstudio.com/resources/webinars/managing-package-dependencies-in-r-with-packrat/) - helpful tutorial video on using packrat
- [Quick start guide](https://www.r-project.org/nosvn/pandoc/packrat.html) - packrat documentation

## Other resources
- [Checkpoint](https://cran.r-project.org/web/packages/checkpoint/vignettes/checkpoint.html) - using checkpoint
- [Docker](http://www.jimhester.com/2017/10/13/docker/) - using docker
