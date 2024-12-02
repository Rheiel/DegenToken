# DegenToken Smart Contract

DegenToken is an ERC-20 token designed for blockchain-based gaming, enabling players to earn, trade, and redeem tokens for in-game items. The contract is built using Solidity and integrates OpenZeppelin's libraries for security and standardization.

---

## Features

- **ERC-20 Token:** Implements the standard ERC-20 functionality with zero decimal places for whole-number transactions.
- **Ownership Control:** Utilizes OpenZeppelin's `Ownable` to restrict certain operations to the contract owner.
- **Minting & Burning:** Tokens can be minted by the owner and burned by any player to manage supply.
- **In-Game Items:** Players can redeem tokens for unique in-game items, stored on the blockchain.
- **Inventory Management:** Each player's redeemed items are stored and accessible through the blockchain.

---

## Contract Details

### Token Details
- **Token Name:** Degen
- **Symbol:** DGN
- **Decimals:** 0 (No fractional tokens)

---

## Functions

### Core Functions

- **`mint(address to, uint256 amount)`**
  - Mints new tokens to the specified address.
  - *Only callable by the contract owner.*

- **`burnTokens(uint256 amount)`**
  - Burns a specified amount of tokens from the caller's balance.
  - *Reverts if the caller’s balance is insufficient.*

- **`transferTokens(address recipient, uint256 amount)`**
  - Transfers tokens from the sender to a recipient.
  - *Requires sender approval and sufficient balance.*

### Game Item Functions

- **`redeem(uint256 itemId)`**
  - Allows players to redeem a specific game item by burning the required amount of tokens.
  - *Reverts if the player’s balance is insufficient or item ID is invalid.*

- **`getGameItems()`**
  - Returns a list of all available game items.

- **`getOwnedItems()`**
  - Returns the list of items owned by the caller.

### Utility Functions

- **`getBalance()`**
  - Returns the caller’s token balance.

- **`decimals()`**
  - Returns `0`, indicating no fractional tokens.

---

## Events

- **`ItemRedeemed(address indexed redeemer, uint256 itemId, string itemName, uint256 itemCost)`**
  - Emitted when a player redeems an item, logging the player’s address, item ID, name, and cost.

---

## Usage

1. **Deployment:**
   Deploy the contract to the Ethereum blockchain using a compatible wallet or IDE like Remix.

2. **Minting Tokens:**
   The contract owner can mint tokens using the `mint` function.

3. **Redeeming Items:**
   Players can redeem tokens for items by calling the `redeem` function with a valid item ID.

4. **Inventory Check:**
   Players can view their owned items with `getOwnedItems()` and available items with `getGameItems()`.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Requirements

- **Solidity Version:** ^0.8.18
- **Dependencies:**
  - [OpenZeppelin ERC20](https://docs.openzeppelin.com/contracts/4.x/erc20)
  - [OpenZeppelin Ownable](https://docs.openzeppelin.com/contracts/4.x/access-control#ownable)

---

## Security Considerations

- Ensure the contract owner carefully manages the `mint` function to prevent token inflation.
- Players should verify item IDs and costs before redeeming to avoid errors.

---

## Contact

For further questions or support, feel free to contact the development team.

