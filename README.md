# Minimal Account Abstraction for Ethereum and ZkSync

This project provides a simple implementation of account abstraction for Ethereum and ZkSync. It includes minimal account contracts, comprehensive tests, and deployment scripts.

## Overview

Account abstraction allows for greater flexibility and customization in how accounts manage their authentication and transaction execution. By decoupling the logic of account management from the core protocol, developers can create more complex and feature-rich accounts that can support multi-signatures, social recovery, meta-transactions, and more.

This project contains two main contracts:
- **MinimalAccount**: A minimal account implementation for Ethereum.
- **ZkMinimalAccount**: A minimal account implementation for ZkSync.

Both contracts aim to provide basic functionalities for account validation and transaction execution.

## Features of Account Abstraction

With account abstraction, you can achieve:
- **Custom Signature Validation**: Implement custom logic for validating transaction signatures.
- **Multi-Signature Accounts**: Require multiple parties to sign off on transactions.
- **Social Recovery**: Allow account recovery through trusted contacts.
- **Meta-Transactions**: Enable users to submit transactions without holding native tokens, with fees paid by a third party.
- **Batch Transactions**: Execute multiple operations within a single transaction.

## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/save-the-planet08/minimal-account-abstraction.git
    cd minimal-account-abstraction
    ```

2. Install the dependencies:
    ```sh
    forge install
    ```

3. Compile the contracts:
    ```sh
    forge build
    ```

## Contracts

### ZkMinimalAccount

The ZkMinimalAccount is a minimal account implementation for ZkSync. It implements the `IAccount` interface and provides basic functions for validating and executing transactions.

Key features:
- **Transaction Validation**: Validates the transaction using a custom `_validateTransaction` function.
- **Transaction Execution**: Executes transactions either from the bootloader or the account owner.
- **Fee Payment**: Handles transaction fee payments to the bootloader.

Key functions:
- `validateTransaction`: Validates incoming transactions.
- `executeTransaction`: Executes a transaction if called by the bootloader or the owner.
- `executeTransactionFromOutside`: Allows external execution of transactions.
- `payForTransaction`: Manages the payment of transaction fees.
- `prepareForPaymaster`: Prepares the transaction for a paymaster.

### MinimalAccount

The MinimalAccount is a minimal account implementation for Ethereum. It also implements the `IAccount` interface and provides basic functionalities for user operation validation and transaction execution.

Key features:
- **Signature Validation**: Validates user operation signatures using ECDSA.
- **Transaction Execution**: Allows the execution of transactions by the entry point or the account owner.
- **Prefunding**: Manages prefunding of account operations.

Key functions:
- `execute`: Executes a transaction if called by the entry point or the owner.
- `validateUserOp`: Validates user operations, ensuring the signature is correct and managing prefunding.
- `getEntryPoint`: Returns the address of the entry point contract.

## Deployment

Deployment scripts are provided for both Ethereum and ZkSync. These scripts are located in the `scripts` directory and use Foundry for deployment.

To deploy the contracts:

- `forge script scripts/Deploy.s.sol`

## Tests
This project includes comprehensive tests for both contracts using Foundry. The tests cover various aspects of account validation and transaction execution.

To run the tests:

- `forge test`

Note: There is a known issue with the testZkValidateTransaction test. This test was not fixed due to prolonged wait times during ZkSync test execution.


## Authors

Author: Frederik Pietratus
Based on the course by Patrick Collins





