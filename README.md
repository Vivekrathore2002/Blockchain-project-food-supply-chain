# Blockchain-project-food-supply-chain

// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.0;
contract FoodSupplyChain {
 // Define struct for producer stage
 struct Producer {
 string crop;
 string pesticides;
 string fertilizers;
 string farmInfo;
 string farmingPractices;
 address producerAddress;
 }

 // Define struct for processing stage
 struct Processing {
 string factoryInfo;
 string equipmentInfo;
 string processingMethods;
 string distributionMethods;
 address processorAddress;
 }

 // Define struct for retailer stage
 struct Retailer {
 string foodItemInfo;
 uint256 quantity;
 uint256 timeOnShelf;
 address retailerAddress;
 }

 // Define mapping to store producers
 mapping (address => Producer) public producers;

 // Define mapping to store processors
 mapping (address => Processing) public processors;

 // Define mapping to store retailers
 mapping (address => Retailer) public retailers;

 // Define event for consumers to retrieve food supply chain information
 event FoodSupplyChainInfo(string crop, string pesticides, string
fertilizers, string farmInfo, string farmingPractices, string factoryInfo,
string equipmentInfo, string processingMethods, string distributionMethods,
string foodItemInfo, uint256 quantity, uint256 timeOnShelf);

 // Define function for producers to record their information
 function addProducer(string memory _crop, string memory _pesticides,
string memory _fertilizers, string memory _farmInfo, string memory
_farmingPractices) public {
 producers[msg.sender] = Producer(_crop, _pesticides, _fertilizers,
_farmInfo, _farmingPractices, msg.sender);
 }

 // Define function for processors to record their information
 function addProcessor(string memory _factoryInfo, string memory
_equipmentInfo, string memory _processingMethods, string memory
_distributionMethods) public {
 processors[msg.sender] = Processing(_factoryInfo, _equipmentInfo,
_processingMethods, _distributionMethods, msg.sender);
 }

 // Define function for retailers to record their information
 function addRetailer(string memory _foodItemInfo, uint256 _quantity,
uint256 _timeOnShelf) public {
 retailers[msg.sender] = Retailer(_foodItemInfo, _quantity,
_timeOnShelf, msg.sender);
 }

 // Define function for consumers to retrieve food supply chain information
 function getFoodSupplyChainInfo() public {
 emit FoodSupplyChainInfo(producers[msg.sender].crop,
producers[msg.sender].pesticides, producers[msg.sender].fertilizers,
producers[msg.sender].farmInfo, producers[msg.sender].farmingPractices,
processors[msg.sender].factoryInfo, processors[msg.sender].equipmentInfo,
processors[msg.sender].processingMethods,
processors[msg.sender].distributionMethods,
retailers[msg.sender].foodItemInfo, retailers[msg.sender].quantity,
retailers[msg.sender].timeOnShelf);
 }
}




