pragma solidity ^0.4.4;

import "./User_Contract.sol";

contract Master_Contract {

  mapping (address => string)  userIDs;
  mapping (string => string)   roles;
  mapping (string => address)  userAddresses;
  address adminAddr;

  function Master_Contract(){
  adminAddr=msg.sender;
  }
  
 
  function addUser(string _userID, string _pwd,string _role,address userAddr) returns (bool){
   if((sha3(_role)==sha3("Certifier")) && (msg.sender!=adminAddr)) 
  {return false;}
  userAddresses[_userID] = userAddr;
  userIDs[userAddr] = _userID;
  roles[_userID] = _role;
  return true;
  }
  
  function getuserID(address useraddress) constant returns (string){
  return userIDs[useraddress];
  }
  
}
