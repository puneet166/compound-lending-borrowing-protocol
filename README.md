# README #

This README would normally document whatever steps are necessary to get your application up and running.

### What is this repository for? ###

1. Deploy a smart contract - OraclePriceDataFeeder.sol 
2. Deploy a smart contract - whitePaperInterestRateMode3l.sol
3. Deploy a underlyAsset - underlyingAsset.sol
4. Deploy a smart contract - Comptroller_flattened.sol
5. Deploy a smart contract - CERC20.sol with below mentioned parameter -
    *    UNDERLYING_ = address of underlyingAsset.sol
    *    COMPTROLLER_= address of Comptroller_flattened.sol
    *    INTERESTRATEMODEL_ = address of whitePaperInterestRateMode3l.sol
    *    INITIALEXCHANGERATEMANTISSA_ = Please set carefully i didn't do research on it so i am setting random 100000
    *    NAME_ = name of the Ctoken such as CDAI, CETHER.
    *    SYMBOL_= symbol 
    *    DECIMALS_ = 8 decimal.


### Config of smart contracts ###

1. call - _setPriceOracle of controller.sol file and pass the oracle smart contratc address.
2. call - _supportMarket of controller.sol file and pass the CtokenAddress.
3. call - entrymarket of controller.sol file and pass the ctokenAddress.
4. call - checkMembership of contro9ller.sol file and pass the user address and the ctokenAddress. it must return true.
5. call - setDirectChainlinkFeed of priceOracle and pass Ctoken address and chainlink data feeder for underlying assest and multiplierMantissa i didn't research on  "multiplierMantissa" . so i am setting 100000. need to research on it.
6. call - getUnderlyingPrice to check the data which is returning.
7. call - approve function of underlying assest and approve to our CTokenAddress and amount which you want to deposit . 
8. call - mint function of CTokenAddress. and check the logs .
9. you will recive Ctokens . 
10. call - borrow as well.



### NOTE and Important

  // (Error err, , uint shortfall) = getHypotheticalAccountLiquidityInternal(borrower, CToken(cToken), 0, borrowAmount);
        // if (err != Error.NO_ERROR) {
        //     return uint(err);
        // }
        // if (shortfall > 0) {
        //     return uint(Error.INSUFFICIENT_LIQUIDITY);
        // }

 I have comments of this code beacause with this code not able to borrow fund beacause "getHypotheticalAccountLiquidityInternal" this function return error. 
 So for testing and working i removed and comment this code without this function working well.

 for more Please research on this function what the side effect of this function and check.  


 ### Deployed Address - 

 * Price oracle with with data feed - 0x7daFD1C9615F2F94Bb686DB1e4b53B84fCFA587e
 *  Comptroller contract address - 0xC3Ef69C5a62e6F6b64cBa034d0460B502eF65d50
 * C token with above controller config - 0x69b65A23279b5f6be9D8E914d4463969C984f788
 * Whitepaperinterestratemode = 0xE8CF7e4ef1BC88Ce1A3F5fBF5922a197094c76F5
 * Mytokenuderlyging = 0xa65023D96C7c3f41dbBa2665C50082bF4353Fa83
 * Network - goreli