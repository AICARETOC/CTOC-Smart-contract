# CTOC Smart Contract Documentation

## Overview

CTOC is an ERC20 token smart contract with additional features such as pausability, burnable tokens, time-based and vesting-based token locking mechanisms, and role-based access control.

## Contract Inheritance

The CTOC contract inherits from the following contracts:

- `Pausable`: Allows pausing and unpausing of token transfers
- `Ownable`: Provides basic access control mechanism with an owner
- `Supervisable`: Introduces a vesting admin role for specific functions
- `Burnable`: Only the owner of the token can be burn
- `Lockable`: Implements vesting-based token locking
- `ERC20`: Standard implementation of the ERC20 token interface

## Key Features

1. **Pausability**: The contract owner can pause and unpause all token transfers.
2. **Burnable Tokens**: Only the owner of the token can be burn.
3. **Token Locking**:
  - Vesting-based locking: Tokens can be locked with a vesting schedule.
4. **Role-Based Access Control**:
  - Owner: Has overall control of the contract.
  - Vesting Admin: Can manage vesting.
  - Locker: Can vesting locks.
  - Burner: Can burn tokens.

## Initial Supply

The initial supply of CTOC tokens is set to 5,000,000,000 tokens (considering 18 decimals).

## Main Functions

### Owner Functions

- `pause()`: Pause all token transfers.
- `unpause()`: Unpause token transfers.
- `addLocker(address account)`: Add a new locker.
- `removeLocker(address account)`: Remove a locker.
- `recoverERC20(address tokenAddress, uint256 tokenAmount)`: Recover any ERC20 tokens sent to the contract.
- `renounceOwnership()`: Renounce ownership of the contract.
- `transferOwnership(address newOwner)`: Transfer ownership to a new address.

### Vesting Admin Functions

- `removeVestingLock(address account)`: Remove a vesting lock for an account.
- `renounceVestingadminOwnership()`: Renounce vesting admin ownership.
- `transferVestingadminOwnership(address newVestingadmin)`: Transfer vesting admin ownership.

### Locker Functions

- `addVestingLock(address account, uint256 startsAt, uint256 period, uint256 count)`: Add a vesting lock for an account.

### Burner Functions

- `burn(uint256 amount)`: Burn a specific amount of tokens.

### Public View Functions

- `getVestingLock(address account)`: Get details of the vesting lock for an account.
- `getVestingLockedAmount(address account)`: Get the total vesting-locked amount for an account.
- `getAllLockedAmount(address account)`: Get the total locked amount (time + vesting) for an account.

## Events

The contract emits various events for important actions:

- `OwnershipTransferred`
- `VestingadminOwnershipTransferred`
- `LockerAdded`, `LockerRemoved`
- `VestingLocked`, `VestingUnlocked`
