# ernm
Estimation of fully/partially observed Exponential-Family Random     Network Models (ERNM). ERNMs are a generalization of ERGM (see the ergm     package) and Gibbs Fields, encompassing both as special cases


## Adding Statistics

The preferred method for users to use their own custom statistics is to create a package as in the example extension package in inst/examplePackage. Users can then directly call register*Statistic.

For Statistics that may be useful for the wider community. They can be integrated into the ERNM package as follows. This workflow also forces users to adequately test their statistics, which may be beneficial, especially for complex statistics.
1. Add to the inst/include/stats.h file. This is where the calculation of the statistics defined. Note for ERNM the dyadUpdate and discreteVertexUpdate and continVertexUpdate methods are crucial for the performance of the MCMC routine required to fit ERNMs.
2. Register the statistic with the src/statController.cpp file
3. Add the statistic to the test_stat.cpp file. This will then be run when the package is built to ensure the statistic is safe on the C++ end 
4. Add R tests in tests/testthat/test-stats.R to actually check the value of the statistic is as expected on the R end.
5. Rebuild the package and use the statistics.

After these steps you should be able to add new statistics to your local fork of the ERNM package, and then submit a PR to have those statistics integrated into the ERNM package for others to use.

## Test additions by Ramji on Nov 7, 2024
testing

## adding to the test1 branch
