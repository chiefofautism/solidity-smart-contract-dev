

### Compiler Directive

The `pragma` directive is used to specify which version of Solidity should be used to compile your code. It ensures that the compiler version is compatible with your contract.

- **Exact version**:
  ```solidity
  pragma solidity 0.8.19; // Use only version 0.8.19
  ```

- **Version range**:
  ```solidity
  pragma solidity ^0.8.19; // Use versions 0.8.19 and above, but below 0.9.0
  pragma solidity >=0.8.19 <0.9.0; // Use versions between 0.8.19 and 0.9.0 (excluded)
  ```

### SPDX License Identifier

- **SPDX License Identifier** is good practice to define licensing for the contract, although it’s not mandatory. It helps in legal sharing and usage.
  
- Example:
  ```solidity
  // SPDX-License-Identifier: MIT
  pragma solidity ^0.8.19;
  ```

- **MIT License**: This is a permissive open-source license allowing anyone to freely use, modify, and distribute the code.

### Writing the Smart Contract

1. **Start the contract** using the `contract` keyword followed by the name of the contract.
   ```solidity
   // SPDX-License-Identifier: MIT
   pragma solidity ^0.8.19;

   contract SimpleStorage {
       // Contract content will go here
   }
   ```

   In Solidity, a **contract** is like a **class** in Object-Oriented Programming.

### Solidity Types

Solidity supports several **elementary** types that can be combined to form more complex ones. Here's a summary of the most commonly used ones:

- **Boolean (`bool`)**: A true or false value.
- **Unsigned Integer (`uint`)**: A whole number that is non-negative (positive only).
- **Signed Integer (`int`)**: A whole number that can be positive or negative.
- **Address (`address`)**: A 20-byte value, often used to represent Ethereum addresses (e.g., from MetaMask).
- **Bytes (`bytes`)**: Raw byte data, useful for low-level storage.

### Variable Definition

Variables are used to store values, which can be of any data type mentioned above. A simple example is a Boolean variable:

```solidity
bool hasFavoriteNumber = true;  // A variable holding a boolean value (true or false)
```

You can specify the bit length of `uint` and `int` variables. For example, `uint256` means a 256-bit unsigned integer (which is the default for `uint`):

```solidity
uint256 favoriteNumber = 88;  // A 256-bit unsigned integer
```

It’s generally a good practice to be explicit when specifying the length of these data types.

### Example Contract with Variables

Here's an example that includes various types of variables in a smart contract:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.19;

contract SimpleStorage {
    // Basic types
    bool hasFavoriteNumber = true;
    uint256 favoriteNumber = 88;
    string favoriteNumberInText = "eighty-eight";
    int256 favoriteInt = -88;
    address myAddress = 0xaB1B7206AA6840C795aB7A6AE8b15417b7E63a8d;
    bytes32 favoriteBytes32 = "cat";
}
```

### Bytes and Strings

- **Bytes**: A collection of characters written in hexadecimal representation. You can define fixed-size bytes like `bytes1` or `bytes32`, or use dynamic arrays for flexible sizes.

```solidity
bytes1 minBytes = "A";        // Fixed-size byte array of 1 byte
bytes32 maxBytes = "Hello";   // Fixed-size byte array of 32 bytes
bytes dynamicBytes = "Flexible size byte array"; // Dynamic byte array
```

- **Strings**: Internally represented as dynamic byte arrays (`bytes` type). Strings are used specifically for text data, and they can be converted into byte arrays.

### Contract Logic

Here’s an example of storing a favorite number using a `uint256`:

```solidity
uint256 favoriteNumber;  // The variable is declared but not initialized

// The default value of an uninitialized uint256 is 0
```

**Important**: All variables in Solidity have **default values** if they are not explicitly initialized:
- `bool`: `false`
- `uint`: `0`
- `int256`: `0`
- `string`: `""` (empty string)
- `address`: `0x0000000000000000000000000000000000000000`
- `bytes`: Empty array
- `bytes32`: `0x0000000000000000000000000000000000000000000000000000000000000000`



