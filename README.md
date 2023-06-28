# ETH_Interm
The program provided is an example of a smart contract written in Solidity.This program is an e-auction smart contract written in Solidity that incorporates the require(), assert(), and revert() statements.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has a several function like place bid to place a bid in the auction higestBidder to see the address of the highest bidder, highestBid to see the highest amount, cancel auction, auction end and withdraw.

## Getting Started

### Executing program

To run this program, we have used Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., ethintrem.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract AssertionExample {
    uint256 public x;
      uint256 public a;
        uint256 public b;

    function setX(uint256 _x) external {
        require(_x > 0, "Value must be greater than zero");
        x = _x;
    }

    function assertExample(uint256 _a, uint256 _b) external  {
         a = _a;
         b = _b;
        assert(a >= b);
    }

    function revertExample() external pure {
        string memory message = "An error occurred";
        revert(message);
    }
}



```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile ethproof.sol" button.
Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "ethpintrem" contract from the dropdown menu, and then click on the "Deploy" button.
Once the contract is deployed, you can enter the value of x, a and b and use the require, assert and revert function.
In this, the AssertionExample contract has three functions that showcase the usage of require(), assert(), and revert().

The setX function demonstrates the use of require(). It takes an input _x and sets the state variable x to its value. However, before setting the value, it uses require() to validate that _x is greater than zero. If the condition evaluates to false, the function will throw an exception with the given error message.

The assertExample function showcases the assert() statement. Inside the function, two local variables a and b are declared and assigned values. Then, the assert() statement checks if a is greater than or equal to b. If the condition is false, it indicates an internal error, and the transaction will be reverted.

The revertExample function demonstrates the use of revert(). It simply reverts the current transaction with a given error message.
## Authors

Navneet Shahi 



## License

This project is licensed under the MIT License. You are free to modify and distribute the code for personal and educational purposes.
