# Logical gates
This logical gates program takes the inputs as a and b and returns the output as y after passing through the various logical gates that are AND gate and NOT gate.

## Description

This program is a simple program of working of logical AND gate and NOT gate that takes the input as a and b then passes through the And gate and returns the output as X, then that output X of AND gate taken as an input of the NOT gate and then the final output get recieved as Y. It contains various files such as circuits, contracts, scripts, types, hardhat.config.ts, gitignore, etc. circuits file contains the main code of input, output and their logics based on the used gates, hardhat.config.ts contains the program for mumbai network and the related url and private key, also the dotenv is get installed. Also in metamask wallet, matic network got added through which the matic transaction can take place in wallet. For MATIC, mumbai faucet has been used but it can provide matic only once in 24 hrs and for that account's has to be pasted on mumbai faucet. Also mumbai testnet is used for showing the transactions of MATIC.

## Getting Started
### Executing program
       
```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Niks_Token {
    string public my_token;
    uint256 private total_Supply;
    mapping(address => uint256) private _balances;
    
    event Transfer(address indexed from, address indexed to, uint256 value);
    event Burn(address indexed account, uint256 amount);
    event Mint(address indexed account, uint256 amount);

    constructor(string memory Nikhils_Token, uint256 TotalSupply) {
        my_token = Nikhils_Token;
        total_Supply = TotalSupply;
        _balances[msg.sender] = total_Supply;
        emit Transfer(address(0), msg.sender, total_Supply);
    }

    function Total_Supply() external view returns (uint256) {
        return total_Supply;
    }

    function balanceOf(address account) external view returns (uint256) {
        return _balances[account];
    }

    function transfer(address recipient, uint256 amount) external returns (bool) {
        _transfer(msg.sender, recipient, amount);
        return true;
    }

    function burn(uint256 amount) external returns (bool) {
        require(amount <= _balances[msg.sender], "Balance not available to burn...");
        _balances[msg.sender] -= amount;
        total_Supply -= amount;
        emit Burn(msg.sender, amount);
        emit Transfer(msg.sender, address(0), amount);
        return true;
    }

    function mint(address account, uint256 amount) external returns (bool) {
        require(account != address(0), "Account address not correct");
        total_Supply += amount;
        _balances[account] += amount;
        emit Mint(account, amount);
        emit Transfer(address(0), account, amount);
        return true;
    }

    function _transfer(address sender, address recipient, uint256 amount) internal {
        require(amount <= _balances[sender], "Balance is not available to transfer");

        _balances[sender] -= amount;
        _balances[recipient] += amount;
        emit Transfer(sender, recipient, amount);
    }
}                            
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile M_m3p3.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Niks_Token" contract from the dropdown menu, and then click on the "Deploy" button. 

Once the contract is deployed, you can interact with it by clicking on various functions. Click on the "Niks_Token" contract in the left-hand sidebar, and then click on the functions for transactions, getting the results accordingly as burning or adding of tokens.

## Authors
Nikhil Upadhyay

## License
This project is licensed under the MIT License
