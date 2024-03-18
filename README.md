# Performance Regression Analysis in the data.table Package
## Description:
This repository aims to investigate performance regressions in the data.table package by examining its history, creating relevant performance tests, and using atime to analyze the performance of different code branches (before regression, regression, fix regression). Additionally, it provides a GitHub Action called r-asymptotic-testing that allows you to perform asymptotic testing on your data.table repository package upon every push/pull request.

## To Start:
To begin, conduct the atime test for the different code branches (before regression, regression, fix regression) to identify potential performance issues. Here is an example of how to perform the atime test
NB: Set up the necessary environment and dependencies, ensuring that the data.table package and the atime package are installed and loaded.

Generate a plot to showcase the fixes made in the data.table package using the atime package. Utilize the atime_versions function to track the fixes across different versions. Pass the following named arguments to atime::atime_versions: N, setup, expr, and the different code branches. More documentation of the atime package can be found here. The documentation provides detailed information on how to use the atime package for performance analysis and tracking changes across different versions

Use the plot function to visually represent the execution times of the expression evaluated across different versions of the data.table package.

## Example Usage
A. Provide links to the issue(s) comment(s) containing the original code(s) that reported the regression. If there are multiple issues with code exhibiting the regression, include links to each issue along with a summary of the observed symptoms in your own words.

B. Link to the pull request (PR) that caused the regression. Explain the cause of the performance regression in the data.table code using your own words.

C. Link to the PR that fixed the regression. Describe the changes made to fix the regression in your own words.

D. Provide links to your atime test code(s) and plot(s) that illustrate the performance regression and its fix. If there are multiple issues with code exhibiting regressions, include links and plots for each issue.

R atime code file(s)
png atime figure file(s)

## Inputs:
Links to the issue(s) comment(s) with the original code(s) reporting the regression.
Link to the pull request (PR) that caused the regression.
Link to the PR that fixed the regression.
Links to the atime test code(s) and plot(s) illustrating the performance regression and its fix.

## Outputs:
Visualizations of the performance regressions and fixes.

# Performance Regression Analysis
