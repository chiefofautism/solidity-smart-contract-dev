

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

