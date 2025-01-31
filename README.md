

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

### Functions in Solidity

Functions in Solidity are blocks of code designed to perform specific tasks, such as storing or retrieving data. Here's a breakdown of key concepts related to functions in Solidity.

### Function Definition

A function in Solidity is defined using the `function` keyword, followed by the function name, parameters (optional), and the function body enclosed in curly braces.

- **Basic Function Structure**:
  ```solidity
  function functionName() public {
      // Function logic goes here
  }
  ```

### Function Visibility

Functions in Solidity can have one of the following visibility specifiers:

- **`public`**: The function can be called both internally (within the contract) and externally (by other contracts or transactions). If a function is marked `public`, it is accessible from both inside the contract and from other contracts or accounts.
  
- **`internal`**: The function can only be accessed within the current contract or contracts that inherit from it. It is not visible to external actors.
  
- **`external`**: The function is only accessible externally and cannot be called from within the contract. It is designed for interactions with other contracts or users.

- **`private`**: The function can only be accessed within the current contract. It is completely hidden from external calls, even by derived contracts.

By default, if no visibility specifier is provided, functions are considered `internal`.

### Function Types

Solidity functions can be categorized based on their side effects:

- **`view` functions**: These functions can read state variables but cannot modify them. They do not alter the blockchain state and therefore do not consume gas when called externally.

  - Example of a `view` function:
    ```solidity
    function retrieve() public view returns(uint256) {
        return favoriteNumber;
    }
    ```
  
- **`pure` functions**: These functions cannot read or modify state variables. They only rely on the input parameters and do not interact with the blockchain state. These functions are free of gas costs when called externally.
  
  - Example of a `pure` function:
    ```solidity
    function multiply(uint256 x, uint256 y) public pure returns(uint256) {
        return x * y;
    }
    ```

### Function Parameters and Return Values

Functions can accept **parameters** (input values) and return **values**. The parameters are defined inside the parentheses `()` after the function name, and the return type is defined using the `returns` keyword.

- Example with parameters and a return value:
  ```solidity
  function add(uint256 a, uint256 b) public pure returns(uint256) {
      return a + b;
  }
  ```

### Function Modifiers

Modifiers are special functions that can be used to change the behavior of other functions. They allow you to add pre-conditions or restrictions before or after the execution of a function.

- Example of a simple modifier:
  ```solidity
  modifier onlyOwner() {
      require(msg.sender == owner, "Not the contract owner");
      _;
  }

  function setFavoriteNumber(uint256 _favoriteNumber) public onlyOwner {
      favoriteNumber = _favoriteNumber;
  }
  ```

### Example: Full Contract with Functions

Here’s an example that demonstrates a contract with different functions (including `view` and `pure`):

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

contract SimpleStorage {
    uint256 public favoriteNumber;  // State variable

    // Store function: Stores a number in the contract
    function store(uint256 _favoriteNumber) public {
        favoriteNumber = _favoriteNumber;
    }

    // View function: Returns the stored favorite number
    function retrieve() public view returns(uint256) {
        return favoriteNumber;
    }

    // Pure function: Returns a constant value
    function add(uint256 a, uint256 b) public pure returns(uint256) {
        return a + b;
    }
}
```

- Functions in Solidity are defined with the `function` keyword, and their visibility can be `public`, `internal`, `external`, or `private`.
- Functions can be `view` (read from state) or `pure` (do not interact with state).
- Functions can take parameters and return values.
- **Modifiers** allow you to restrict or modify the behavior of functions.
