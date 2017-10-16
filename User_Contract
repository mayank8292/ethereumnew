pragma solidity ^0.4.4;

contract User_Contract {
  
   struct PII {
   bytes32 PIIHash;
   string ExposePII;
   address certifierAddr;
   bytes digCert;
    }
              
   string PIIType;
   address masterAddress;
   mapping (string => PII) piis;    //piis that are certified and approved by user
   mapping (string => PII) piis_in; //piis that  are certified "but yet to be approved by user
  
  //Constructor to initialize
  function User_Contract() public {
   
   masterAddress=msg.sender;
  }
  
  // Add or update a new Certified PII
   function addUpdPII(string piiType, bytes piiValue,string exposepii,bytes digcert) returns (bool){
   piis_in[piiType].PIIHash=sha3(piiValue);
   piis_in[piiType].ExposePII=exposepii;
   piis_in[piiType].certifierAddr=msg.sender;
   piis_in[piiType].digCert=digcert;
   return true;
   }
   
   // Delete a PII
   function deletePII(string piitype) returns (bool){
   delete piis[piitype];
   return true;
   }
   
   //Verify if the PII value match with the certified PII
    function verifyPII(string piiType, bytes piiValue) returns( bool ){
    if(sha3(piiValue)!=piis[piiType].PIIHash)
      { return false;}
     return true;
  }
  
 
  // User approve the certified PIIs
  function usrApprovePII(string userID,string password,string piitype) returns (bool)
  {
  //if(sha3(userID)!=piis["UserID"].PIIHash || sha3(password)!=piis["Password"].PIIHash || sha3(msg.sender)!=piis["UserAddress"].PIIHash)
    // {return false;}
  piis[piitype]=piis_in[piitype];
  delete(piis_in[piitype]);
  return true;
  }

       //get the full Non Approved PII object
   function getPIIS_IN(string piitype) returns(bytes32,string,address,bytes){
   return (piis_in[piitype].PIIHash,piis_in[piitype].ExposePII,piis_in[piitype].certifierAddr,piis_in[piitype].digCert);
   }
   
       //get the full User Approved PII object
   function getPII(string piitype) returns(bytes32,string,address,bytes){
   return (piis[piitype].PIIHash,piis[piitype].ExposePII,piis[piitype].certifierAddr,piis[piitype].digCert);
   }
   
  // Destroy the User Contract and return any funds to the user
  function destructMe(string userID,string password) returns (bool)
  {
  //if(sha3(userID)!=piis["UserID"].PIIHash || sha3(password)!=piis["Password"].PIIHash || sha3(msg.sender)!=piis["UserAddress"].PIIHash)
    //{return false;}
  selfdestruct(msg.sender);
  return true;
  }
  
}
