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

contract Auction {
    address public auctioneer;
    address public highestBidder;
    uint public highestBid;
    bool public auctionEnded;

    mapping(address => uint) returnsPending;
    
    constructor() {
        auctioneer = msg.sender;
    }
    
    function placeBid() external payable {
        require(!auctionEnded, "Auction has already ended");
        require(msg.value > highestBid, "Bid value must be higher than the current highest bid");
        
        if (highestBid != 0) {

            returnsPending[highestBidder] += highestBid;
            // Return funds to the previous highest bidder
            assert(payable(highestBidder).send(highestBid));
        }
        
        highestBidder = msg.sender;
        highestBid = msg.value;
    }
    
    function endAuction() external {
        require(msg.sender == auctioneer, "Only the auctioneer can end the auction");
        require(!auctionEnded, "Auction has already ended");
        
        auctionEnded = true;
    }
    
    function withdraw() external {
        require(auctionEnded, "Auction has not ended yet");
        
        if (msg.sender == highestBidder) {
            // Transfer the winning bid amount to the highest bidder
            assert(payable(highestBidder).send(highestBid));
        }
    }

    function cancelAuction() public view  {
        require(msg.sender == auctioneer, "Only the auctioneer can cancel the auction");
        revert("Auction has been cancelled");
    }
}



```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile ethproof.sol" button.
Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "ethpintrem" contract from the dropdown menu, and then click on the "Deploy" button.
Once the contract is deployed, you can enter the bidding amount and click on the placeBid function to deploy the auction.
In this e-auction contract, we have the placeBid() function that allows bidders to place their bids by sending ether to the contract. The function uses the require() statement to check if the auction has not ended and if the bid value is higher than the current highest bid. It also includes the assert() statement to ensure that funds are returned to the previous highest bidder (if any) using the send() function.
The endAuction() function is used by the auctioneer to end the auction. It verifies that only the auctioneer can call this function using the require() statement.
The withdraw() function allows the highest bidder to withdraw their funds after the auction has ended. It uses the require() statement to check if the auction has ended and includes the assert() statement to transfer the winning bid amount to the highest bidder.
The cancelAuction() function allows the auctioneer to cancel the auction. It uses the require() statement to ensure that only the auctioneer can call this function and uses the revert() statement to revert the transaction with a custom error message.

## Authors

Navneet Shahi 



## License

This project is licensed under the MIT License. You are free to modify and distribute the code for personal and educational purposes.
