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


..............................................................................................


 // function withdrawALL() public {
//     uint amount = getContractBalance();
//     address payable to = payable(msg.sender);
//     to.transfer(amount);
//     balancedReceived -= amount;   // Subtract the withdrawn amount
// }

 // function withdrawToaddress(address payable to) public {
//     uint amount = getContractBalance();
//     to.transfer(amount);
//     balancedReceived -= amount;
// }



...............................................................................................

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.2 <0.9.0;
contract simpleSample {
string public myString = "Hello World";


    function updateString( string memory _newString) public payable {
       if(msg.value == 1 ether) {
         myString = _newString;
       } else {
         (bool success, ) = payable(msg.sender).call{value: msg.value}("");
            require(success, "Transfer failed");
       }
    }
}

// send eth to update the string.

.........................................................................


