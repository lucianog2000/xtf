DEMO HACKHATON CHLINK


TO-DO

- **major** subsequent reedem gets more etfTokens [SOLVED]

- minor bug (depositsfunds) never return tokenPerwrap [SOLVED]

- bug in mint, does not reflect the contribution () [SOLVED]

- need to add minumum quantities depending on the price oracles! [SOLVED]

- we need to check what happens with the excess of ethers (native tokens) [SOLVED]

```

     for (uint256 j = 0; j < getTokenCountOfBundle(_bundleId); j += 1) {
                if (
                    getTokenOfBundle(_bundleId, j).assetContract ==
                    _tokensToWrap[i].assetContract
                ) {
                    tokenAlreadyInBundle = true;

                    // check if the token quantity + current quantity is not greater than the quantity required
                    
                    if (
                        getTokenOfBundle(_bundleId, j).totalAmount +
                            _tokensToWrap[i].totalAmount >
                        tokenQuantities[
                            getTokenOfBundle(_bundleId, j).assetContract
                        ]
                    ) {
                        _tokensToWrap[i].totalAmount =
                            tokenQuantities[
                                getTokenOfBundle(_bundleId, j).assetContract
                            ] -
                            getTokenOfBundle(_bundleId, j).totalAmount;
                    }
```

- we check bundleId was not already closed in an ETF need to make sure etf id starts from 1 [SOLVED]

```
        require(
            bundleIdToETFId[_bundleId] == 0,
            "ETFContract: bundleId was already closed for an ETF"
        );
```

- we need to add virtual to the CCIPReceiver.sol [CONTACTED CHAINLINK] [SOLVED IN NEWER VERSIONS]

  /// @notice IERC165 supports an interfaceId
  /// @param interfaceId The interfaceId to check
  /// @return true if the interfaceId is supported
  function supportsInterface(bytes4 interfaceId) public pure virtual override returns (bool) {
    return interfaceId == type(IAny2EVMMessageReceiver).interfaceId || interfaceId == type(IERC165).interfaceId;
  }


npx hardhat verify --network sepolia --constructor-args ./scripts/args2.js  0xfd454Ea2186E1f355c08ef98b9B66dfDC1ed7f8B