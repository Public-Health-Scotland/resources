# Guidance on package management 


## Packrat Guidance

This Guidance will walk you through some of the most common tasks you’ll want to do with packrat, and explain the fundamental concepts behind Packrat package.

# Set up
You’re getting ready to start a new project, so you create a new directory that will eventually contain all the .R scripts, CSV data, and other files that are needed for this particular project.

You might need to make use of several R packages over this project. So before you start writing your code, make sure you set up the project directory to use Packrat with **packrat::init:**. Before that you might need to install Packrat package.

```
> install.packages("packrat")

Installing package into ‘C:/Users/marioa02/Documents/projects/project/packrat/lib/i386-w64-mingw32/3.5.0’
(as ‘lib’ is unspecified)
trying URL 'https://cran.rstudio.com/bin/windows/contrib/3.5/packrat_0.4.9-3.zip'
Content type 'application/zip' length 449877 bytes (439 KB)
downloaded 439 KB

package ‘packrat’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Users\marioa02\AppData\Local\Temp\RtmpoX0wtU\downloaded_packages
  
> packrat::init("~/projects/project")

Adding these packages to packrat:
            _        
    packrat   0.4.9-3

Fetching sources for packrat (0.4.9-3) ... OK (CRAN current)
Snapshot written to "C:/Users/marioa02/Documents/projects/project/packrat/packrat.lock"
Installing packrat (0.4.9-3) ... 
	OK (downloaded binary)
Initialization complete!

Restarting R session...
```

In case the current working directory is the project directory, you can omit the "path".

After initializing the project, you’re in a Packrat project. That means that you have your own library. Any packages you install from inside a packrat project are only available to that project. Any packages you install outside the packrat project will not be available to your packrat project.

# Manipulating packages

Manipulating (installing, removing, updating) packages in a Packrat project is quite simple. The only thing you have to do is open R/ Rstudio in Packrat project and then just install the packages you want.

```
> install.packages("reshape2")

package ‘reshape2’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Users\marioa02\AppData\Local\Temp\RtmpKUa5Sj\downloaded_packages
```
 You just installed the reshape2 package from CRAN into your project’s private package library.
 Using a snapshot you will save reshape2 and other packages that might have been installed in Packrat Package
 
```
> packrat::snapshot()

Adding these packages to packrat:
                 _         
    BH             1.66.0-1
    DBI            1.0.0   
    R6             2.2.2   
    RColorBrewer   1.1-2   
    Rcpp           0.12.17 
    assertthat     0.2.0   
    backports      1.1.2   
    base64enc      0.1-3  
    reshape2       1.4.3
    
Fetching sources for BH (1.66.0-1) ... OK (CRAN current)
Fetching sources for DBI (1.0.0) ... OK (CRAN current)
Fetching sources for R6 (2.2.2) ... OK (CRAN current)
Fetching sources for RColorBrewer (1.1-2) ... OK (CRAN current)
Fetching sources for Rcpp (0.12.17) ... OK (CRAN current)
Fetching sources for assertthat (0.2.0) ... OK (CRAN current)
Fetching sources for backports (1.1.2) ... OK (CRAN current)
Fetching sources for base64enc (0.1-3) ... OK (CRAN current)
Fetching sources for reshape2 (1.4.3) ... OK (CRAN current)

Snapshot written to "C:/Users/marioa02/Documents/projects/project/packrat/packrat.lock"
```
Snapshot checks the project’s private package library for packages that have been installed, changed or removed since the last time snapshot was called.
