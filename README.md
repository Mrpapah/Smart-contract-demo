# Smart-contract-demo
 A basic ERC-20 smart contract built with Solidity and deployed using Hardhat. Includes deployment scripts and test cases.
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("MyToken", "MTK") {
        _mint(msg.sender, initialSupply);
    }
}
const hre = require("hardhat");

async function main() {
  const MyToken = await hre.ethers.getContractFactory("MyToken");
  const myToken = await MyToken.deploy(1000000);

  await myToken.deployed();
  console.log("Token deployed to:", myToken.address);
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
