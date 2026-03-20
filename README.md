# Tip-Jar-
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract TipJar {
    string public name = "Support me on Base!";
    address payable public creator;

    constructor() {
        creator = payable(msg.sender);
    }

    function tip() external payable {
        creator.transfer(msg.value);
    }

    function updateName(string memory _newName) external {
        require(msg.sender == creator, "Only creator");
        name = _newName;
    }
}
