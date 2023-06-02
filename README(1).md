# Project: Contract use Successfully require(), assert(), and revert() statements.

This Solidity program is a simple "BasicBankContract" program that demonstrates the basic syntax and functionality of the Solidity programming language. The purpose of this program is to serve as a starting point of BasicBankContract for those who are new to Solidity and want to get a feel for how it works.

## Description

This program is a simple contract of BasicBankContract written in Solidity, A programming language used for developing smart contracts on the Ethereum blockchain. This contract is made as per requirments which is defined inside the smart contract. This program have 3 Error handling functions which are:  require(), assert(), and revert(). This contract is defined with mapping(address=>uint) balance and it have 5 functions getDeployerAccountAddress, deposit, getBalance, withdraw, and transferBalance, with the assert() 1 condition inside the getDeployerAccountAddress function, require() 1 condition inside the getBalance function, require() 2 condition inside the withdraw function, and revert() 1 condition inside the transferBalance function. For the testing of these function you can check!

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website or Remix - Etheruem IDE. Create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., FunctionsAndErrosChallenge.sol). Copy and paste the following code into the file:

### Code
```javascript
// SPDX-License-Identifier: MIT

pragma solidity 0.8.0;

/*
        Project must provide the following to be successfully completed:
   
Functionality

    Contract successfully uses require()
    Contract successfully uses assert()
    Contract successfully uses revert() statements

Explanation

    Code read-aloud is submitted
    Code read-aloud is complete (all steps explained)
    Code read-aloud is clear and understandable

*/

// SPDX-License-Identifier: MIT

/*Functionality

    Contract successfully uses require()
    Contract successfully uses assert()
    Contract successfully uses revert()

Explanation

    Code read-aloud is submitted
    Code read-aloud is complete (all steps explained)
    Code read-aloud is clear and understandable */

pragma solidity ^0.8.0;

contract BasicBankContract 
    {
    mapping (address => uint) balance;
    address owner;

    constructor () {
        owner = msg.sender;
    }

    modifier onlyOwner 
    {
        require (owner == msg.sender, "Warning you are not the owner");_;
    }
    
    function getDeployerAccountAddress () onlyOwner public view returns (address) 
    {
        address account = msg.sender;
        assert (owner == account);
        return account;
    }

     function deposit () public payable
    {   require (msg.value > 0, "Amount must be greater than 0");
        balance [msg.sender] += msg.value;
    }
    
    function getBalance () onlyOwner public view returns (uint)
    {  
        return balance [msg.sender]; 
    }

    function withdraw(uint amount) payable public 
    {
    require(amount > 0, "Amount must be greater than zero");
    require(balance[msg.sender] >= amount, "Insufficient balance");
    payable(msg.sender).transfer(amount);
    }

    function transferBalance(address _receiver, uint _amount) public payable 
    {
        if (balance[msg.sender] < _amount) 
    {
        revert("Insufficient balance");
    }
        balance[msg.sender] -= _amount;
        balance[_receiver] += _amount;
    }


}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile Token.sol" button.
## Explanation
https://www.loom.com/share/44de64d9442b4a4fb5608b89ae92d83f
## Authors

Contributors names and contact info

ex. Reahbar Khan  
ex. https://github.com/Reahbar


## License

This project is licensed under the [MIT] License - see the LICENSE.md file for details
