# CTOC Smart Contract Documentation

## Overview

CTOC is an ERC20 token smart contract with additional features such as pausability, burnable tokens, time-based and vesting-based token locking mechanisms, and role-based access control.

## Contract Inheritance

The CTOC contract inherits from the following contracts:

- `Pausable`: Allows pausing and unpausing of token transfers
- `Ownable`: Provides basic access control mechanism with an owner
- `Supervisable`: Introduces a vesting admin role for specific functions
- `Burnable`: Allows designated addresses to burn tokens
- `Lockable`: Implements time-based and vesting-based token locking
- `ERC20`: Standard implementation of the ERC20 token interface

## Key Features

1. **Pausability**: The contract owner can pause and unpause all token transfers.
2. **Burnable Tokens**: Designated burner addresses can burn their own tokens.
3. **Token Locking**:
  - Time-based locking: Tokens can be locked for a specific time period.
  - Vesting-based locking: Tokens can be locked with a vesting schedule.
4. **Role-Based Access Control**:
  - Owner: Has overall control of the contract.
  - Vesting Admin: Can manage vesting and time locks.
  - Locker: Can add time and vesting locks.
  - Burner: Can burn tokens.

## Initial Supply

The initial supply of CTOC tokens is set to 5,000,000,000 tokens (considering 18 decimals).

## Main Functions

### Owner Functions

- `pause()`: Pause all token transfers.
- `unpause()`: Unpause token transfers.
- `addBurner(address account)`: Add a new burner.
- `removeBurner(address account)`: Remove a burner.
- `addLocker(address account)`: Add a new locker.
- `removeLocker(address account)`: Remove a locker.
- `recoverERC20(address tokenAddress, uint256 tokenAmount)`: Recover any ERC20 tokens sent to the contract.
- `renounceOwnership()`: Renounce ownership of the contract.
- `transferOwnership(address newOwner)`: Transfer ownership to a new address.

### Vesting Admin Functions

- `removeTimeLock(address account, uint8 index)`: Remove a time lock for an account.
- `removeVestingLock(address account)`: Remove a vesting lock for an account.
- `renounceVestingadminOwnership()`: Renounce vesting admin ownership.
- `transferVestingadminOwnership(address newVestingadmin)`: Transfer vesting admin ownership.

### Locker Functions

- `addTimeLock(address account, uint256 amount, uint256 expiresAt)`: Add a time lock for an account.
- `addVestingLock(address account, uint256 startsAt, uint256 period, uint256 count)`: Add a vesting lock for an account.

### Burner Functions

- `burn(uint256 amount)`: Burn a specific amount of tokens.

### Public View Functions

- `getTimeLockLength(address account)`: Get the number of time locks for an account.
- `getTimeLock(address account, uint8 index)`: Get details of a specific time lock.
- `getTimeLockedAmount(address account)`: Get the total time-locked amount for an account.
- `getVestingLock(address account)`: Get details of the vesting lock for an account.
- `getVestingLockedAmount(address account)`: Get the total vesting-locked amount for an account.
- `getAllLockedAmount(address account)`: Get the total locked amount (time + vesting) for an account.

## Events

The contract emits various events for important actions:

- `OwnershipTransferred`
- `VestingadminOwnershipTransferred`
- `BurnerAdded`, `BurnerRemoved`
- `LockerAdded`, `LockerRemoved`
- `TimeLocked`, `TimeUnlocked`
- `VestingLocked`, `VestingUnlocked`
