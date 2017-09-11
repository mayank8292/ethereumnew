pragma solidity ^0.4.4;


contract User_Contract {
  
   struct PII {
   bytes32 PIIHash;
   string ExposePII;
    }
   string PIIType;
   mapping (string => PII) piis;
  
   function addPII(string piiType, bytes32 piiHash) returns (bool){
   PIIType= piiType;
   piis[piiType].PIIHash=piiHash;
   return true;
   }
   
   function getPII(string piitype) returns(bytes32){
   bytes32 piihash;
   piihash = piis[piitype].PIIHash;
   return (piihash);
   }
   
   function updatePII(string piitype, bytes32 updatedhash) returns (bool){
   piis[piitype].PIIHash=updatedhash;
   return true;
   }
   
   function deletePII(string piitype) returns (bool){
   delete piis[piitype];
   delete piitype;
   return true;
   }
   
   function exposePII(string piitype, string exposepii) returns (bool){
   piis[piitype].ExposePII=exposepii;
   return true;
   }
}
