This project is from [lw3](https://learnweb3.io/courses/c1d7081b-63a9-4c6e-b35c-9fcbbad418b2/lessons/acd04999-1230-4533-b6de-6b4e4978914c)

The associated smart contract is deployed on the Sepolia testnet at: [0x0BC94C6322020D7c3EEf4506cD71485460D0e794](https://sepolia.etherscan.io/address/0x0BC94C6322020D7c3EEf4506cD71485460D0e794)

Here is the smart contract code:
```solidity
//SPDX-License-Identifier: Unlicense
pragma solidity ^0.8.0;

contract Whitelist {
  uint8 public maxWhitelistedAddresses;
  uint8 public numAddressesWhitelisted;

  // True if user is whitelisted.
  mapping(address => bool) public whitelistedAddresses;

  constructor(uint8 _maxWhitelistedAddresses) {
    maxWhitelistedAddresses = _maxWhitelistedAddresses;
  }

  function addAddressToWhitelist() public {
    // Checks that the user is not already whitelisted.
    require(!whitelistedAddresses[msg.sender], "User has already been whitelisted!");
    // Checks that the ehitelist is not full.
    require(numAddressesWhitelisted < maxWhitelistedAddresses, "Limit reached!");

    whitelistedAddresses[msg.sender] = true;
    numAddressesWhitelisted += 1;
  }
}
```



