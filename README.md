# SendWithdrawContract

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0; 
contract sendWithdrawMoney {
    
    uint public balanceReceived;

    // deposit function
    function deposit() public payable {
        balanceReceived += msg.value;
    }
    // view contract balance

    function getContractBalance() public view returns (uint){
        return address(this).balance;
     }
    // withdraw all ether from smart contract 
     function withdrawall() public {
        address payable to = payable(msg.sender);
        to.transfer(getContractBalance());
     }
    // withdraw to a payable address
    function withdrawtoAddress ( address payable to) public {
        to.transfer(getContractBalance());
    }
}

