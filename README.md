# Performance Regression Analysis in the data.table Package
## Description:
This repository aims to investigate performance regressions in the data.table package, creating relevant performance tests, and using atime to analyze the performance of different data.table versions (before regression, regression, fix regression).

The repository is structured with different folders. One of the folders, named ["Working Examples"](https://github.com/DorisAmoakohene/PerformanceTest_data.table/tree/master/Working%20Examples), houses performance tests that are fully prepared for immediate use. There is another folder named ["Work in Progress"](https://github.com/DorisAmoakohene/PerformanceTest_data.table/tree/master/Work%20In%20Progress) within the repository, which contains various performance tests that are currently being worked on and are not yet finalized.
The third folder labeled ["partially completed"](https://github.com/DorisAmoakohene/PerformanceTest_data.table/tree/master/Partially%20Completed), contains issues that can be utilized, but misses one commit id (before) due to installations problems. However, there is a possibility that these issue of installation can be resolved in the future.

Each folder includes a subfolders named after the PR/Issue numbers. Inside the PR/Issue folder, you'll find an RMD file containing the code used for the test, along with PNG files displaying the resulting images.


## Details on how to perform a performance regression test
To begin, conduct the atime test for the different data.table versions (before regression, regression, fix regression) to identify potential performance issues.
NB: Set up the necessary environment and dependencies, ensuring that the data.table package and the atime package are installed and loaded.

Generate a plot to showcase the fixes made in the data.table package using the atime package. Utilize the atime_versions function to track the fixes across different versions of the package. 
Pass the following named arguments to atime::atime_versions: N, setup, expr, and the different versions. More documentation of the atime package can be found [here](https://github.com/tdhock/atime). The documentation provides detailed information on how to use the atime package for performance analysis and tracking changes across different versions.

Use the plot function to visually represent the execution times of the expression evaluated across different versions of the data.table package.

To understand more on how to perform an data.table performance test and create a new test, read this [blog]().


## Each of the examples below will be categorized using the labels A, B, C, and D.

A. Provide links to the issue(s) comment(s) containing the original code(s) that reported the regression. If there are multiple issues with code exhibiting the regression, include links to each issue along with a summary of the observed symptoms in your own words.

B. Link to the pull request (PR) that caused the regression. Explain the cause of the performance regression in the data.table code using your own words.

C. Link to the PR that fixed the regression. Describe the changes made to fix the regression in your own words.

D. Provide links to your atime test code(s) and plot(s) that illustrate the performance regression and its fix. If there are multiple issues with code exhibiting regressions, include links and plots for each issue.

R atime code file(s)
png atime figure file(s)

To ensure that a particular test is working correctly and that the plot is accurate, you should verify the following:

1. The graph should exhibit an increasing trend, either by a factor of N or linearly. However, there may be special cases where the graph remains stagnant, as demonstrated in example 3.
2. The "Before" and "Fixed" data points should either have the same movement or show faster progress compared to the "Regression" data point.


# Performance Regression Analysis

# 1.

  A. discusses regression: this link discusses the issue of Performance Regression with .N and := [issue5424](https://github.com/Rdatatable/data.table/issues/5424) other issues that was discussed includes [issues5366](https://github.com/Rdatatable/data.table/issues/5366) Significantly slower performance time-based rolling and [issue5371](https://github.com/Rdatatable/data.table/issues/5371)Memrecycle Performance Regression.
These issues address performance-related concerns and propose potential fixes or improvements to the data.table package
   
   B. The cause of the regression is related to the addition of the snprintf function in the assign.c.
   [CausesRegression](https://github.com/Rdatatable/data.table/pull/4491)
   
   C. The Regression was fixed by creating targetDesc function and adding snprintf in assign.c
   [Fixes Regression](https://github.com/Rdatatable/data.table/commit/e793f53466d99f86e70fc2611b708ae8c601a451)

   D.
   [link to my atime code](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Working%20Examples/PR%205424/Performance%20regression%20with%235424.Rmd)

   ![Plot showing the 3 branches(Regression,Fixed and Before) of Issue#5424](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Working%20Examples/PR%205424/atime.list.png)

   ![Plot showing the 3 branches(Regression,Fixed and Before) of Issues5366](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Working%20Examples/PR%205424/atime.list.2.png)
   
   ![Plot showing the 3 branches(Regression,Fixed and Before) of Issues5371]()


  # 2.
  
 A. This issue reported a  performance regression when performing group computations, specifically when running R's C eval on each group (q7 and q8) in the db-benchmark, indicating a  slowness in the implementation of the code.[link to comment that reported Regression](https://github.com/Rdatatable/data.table/issues/4200)
  
 B. This is the [PR]( https://github.com/Rdatatable/data.table/pull/4558) that discusses the 
Cause of the Regression: [The regression was specifically related to the evaluation of C code within each group of data, specifically q7 and q8 in the "db-benchmark"](https://github.com/Rdatatable/data.table/issues/4200#issue-555186870)  which appears that the regression occurred during the evaluation of C code within these particular groups, indicating a performance issue or slowness in the implementation of the code.

C. Fixed:  
[The regression was fixed Regression by the addition of const int nth = getDTthreads]( https://github.com/Rdatatable/data.table/pull/4558/files)

D.
[link to my atime code](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Working%20Examples/PR%204200/groupby%20with%20dogroups%20(R%20expression)%20performance%20regression%20%234200.Rmd)

![Plot showing the 3 branches(Regression,Fixed and Before) of the issues#4200](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Working%20Examples/PR%204200/atime.list.4200.png)


# 3.

A. The issue that reported the regression is [here](https://github.com/Rdatatable/data.table/issues/3735). They reported that selecting by row number from a data.table is much slower than from a data.frame. 

B. I couldn’t find the specific pull request that caused the regression. 

C. The pull request that fixed the regression can be found [here](https://github.com/Rdatatable/data.table/pull/4488). However, I couldn’t find specific details about the changes made to fix the regression. It’s likely that the changes involved optimizing the way data.table handles row selection to make it more efficient. 

D. [This is the link to my atime code](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Working%20Examples/PR%204488/Selecting%20from%20data.table%20by%20row%20is%20very%20slow%20%233735%20-%20Copy.Rmd)

![Plot showing the the memory and time metrics of the issue from the atime](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Working%20Examples/PR%204488/atime.list.3735.png)


# 4.

D. [This is the link to my atime code](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Working%20Examples/PR%205427/setDT%20extremely%20slow%20for%20very%20wide%20input%20%235426%20-%20Copy.Rmd)

![Plot showing the the memory and time metrics of the issue from the atime](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Working%20Examples/PR%205427/atime.list.5427.png)


# 5.

A. This issue reported that when using the dt[selector, foo := bar] syntax  with an index defined, the performance of that operation can be significantly slower compared to when there is no index.[Major performance drop of keyed := when index is present #4311](https://github.com/Rdatatable/data.table/issues/4311)

B. [Causes Regression](https://github.com/Rdatatable/data.table/issues/4311
) The regression  was caused by utilizing the ":=" operator with an index present while modifying data by reference.

C. [Fixes Regression by passing shallow(dt.s4) to the isS4() function](https://github.com/Rdatatable/data.table/pull/4440)

D. [Link to my atime code showing this Regression](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Partially%20Completed/PR%204440/Remove%20deep%20copy%20of%20indices%20from%20shallow.Rmd)

![Plot showing the 3 branches(Regression,Fixed and Before) of the issues#4440](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Partially%20Completed/PR%204440/atime.list.4440.png)


# 6.

A. [The user mentions that the shift() function in data.table version 1.9.6 is slow when applied to many groups](https://github.com/Rdatatable/data.table/issues/1534). 

B.The exact cause or specific use case is not elaborated upon in the issue.[visit here to read more](https://github.com/Rdatatable/data.table/issues/1534)

C.[The pull request address the issue by allowing GForce optimization for lapply even without using .SD1.](https://github.com/Rdatatable/data.table/pull/5205)

D. [This is the link to my atime code](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Partially%20Completed/PR%205205/shift%20in%20data.table%20v1.9.6%20is%20slow%20for%20many%20groups%20%231534%20-%20Copy.Rmd)

![Plot showing the the memory and time metrics of the issue from the atime](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Partially%20Completed/PR%205205/atime.list.1534.png)


# 7

D. [This is the link to my atime code](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Partially%20Completed/PR%204655/%5B%5B%20by%20group%20performance%20%234655.Rmd)

![Plot showing the the memory and time metrics of the issue from the atime](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Partially%20Completed/PR%204655/atime.list.4646.png)

This issue is related the the above grph and was fixed by the same PR

![Plot showing the the memory and time metrics of the issue from the atime](https://github.com/DorisAmoakohene/PerformanceTest_data.table/blob/master/Partially%20Completed/PR%204655/atime.list.4655.png)
