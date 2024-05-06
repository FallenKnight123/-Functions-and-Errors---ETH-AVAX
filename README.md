# StatementExample Smart Contract

This Solidity smart contract implements the require(), assert(), and revert() statements. It allows users to add and remove balance while ensuring certain conditions are met and handling potential errors gracefully.

## Getting Started

### Prerequisites

To interact with the smart contract, you'll need:
- A web browser
- An internet connection

### Running in Remix IDE

1. Open your web browser and navigate to [Remix IDE](https://remix.ethereum.org/).

2. Create a new file in Remix IDE and name it `StatementExample.sol`.

3. Copy the content of `StatementExample.sol` from this repository and paste it into the newly created file.
   
   // SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StatementExample {
    uint256 public balance;

    function addBalance(uint256 _amount) public {
        // Use require to ensure _amount is at least 100
        require(_amount >= 100, "Amount must be at least 100");

        // Use assert to check if adding _amount to balance overflows
        assert(balance + _amount > balance);

        balance += _amount;
    }

    function removeBalance(uint256 _amount) public {
        // Use require to ensure _amount is not greater than balance
        require(_amount <= balance, "Insufficient balance");

        // Revert if removing _amount results in underflow
        if (balance - _amount > balance) {
            revert("Underflow error");
        }

        balance -= _amount;
    }
}


5. Compile the smart contract by clicking on the "Solidity Compiler" tab in Remix IDE and then clicking on the "Compile" button.

6. Once the contract is successfully compiled, switch to the "Deploy & Run Transactions" tab.

7. Ensure that you have the appropriate environment selected (e.g., JavaScript VM, Injected Web3, etc.).

8. Deploy the contract by clicking on the "Deploy" button.

9. You can now interact with the deployed contract using the provided user interface in Remix IDE.
