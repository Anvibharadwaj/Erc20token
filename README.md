# Creating a ERC20Token using Solidity

This Solidity program is a simple program that demonstrates the basic syntax and functionality of the Solidity programming language and how to create a token. The purpose of this program is to serve as a starting point for those who are new to Solidity and want to get a feel for how it works.

## Description

This program is a simple ERC20 token contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has a mainly 4 function the 1st one is used to increases the total supply by given value and 2nd is to destroy the token,3rd is to transfer tokens from one account to another and last function is used to to check the balance of an account.This code also contain one modifier and one constructor that contains state variable.This program serves as a simple and straightforward introduction to Solidity programming, and can be used as a stepping stone for more complex projects in the future.

## Getting Started
### Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., erc20token.sol). Copy and paste the following code into the file:


// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// Import the ERC20 interface
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    address public owner;

    // Define token details in the constructor
    constructor(string memory name, string memory symbol, uint256 totalSupply) ERC20(name, symbol) {
        owner = msg.sender;
        _mint(msg.sender, totalSupply);
    }

    // Function for the owner to mint new tokens
    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    // Function for burning tokens by any user
    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    // Modifier to restrict functions to the contract owner
    modifier onlyOwner() {
        require(msg.sender == owner, "Only owner can mint tokens");
        _;
    }
    
    // Function to transfer tokens from one account to another
    function transfer(address to, uint256 amount) public override returns (bool) {
        _transfer(msg.sender, to, amount);
        return true;
    }

    // Function to check the balance of an account
    function balanceOf(address account) public view override returns (uint256) {
        return super.balanceOf(account);
    }
}


To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.0" (or another compatible version), and then click on the "Compile erc20token.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar and provide the details as required and then click on transact. Select the "MyToken" contract from the dropdown menu, and then click on the multiple functions as neeeded.

Once the contract is deployed, you can interact with it by calling the mint,transferto,transferfrom,balanceof and burn function. Click on the "MyToken" contract in the left-hand sidebar, and then click on the "mint" function.After that add address and value Finally, click on the "transact" button to execute the function and retrieve the message.Similar for rest as well.

## Authors
Anvi Bharadwaj
