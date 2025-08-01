Solidity Visibility Specifiers

Solidity provides four visibility specifiers to manage access control:

Visibility Specifiers
- Public: Accessible from anywhere (inside the contract, derived contracts, external contracts, and externally via transactions).
- Private: Only accessible within the contract where they are defined.
- Internal: Accessible within the contract and its derived contracts (inherited contracts).
- External: Only accessible from outside the contract (via transactions or external contract calls).

These specifiers apply to both variables (state and local) and functions, with some differences in behavior and use cases.

Visibility Specifiers for Variables
State Variables
State variables are stored on the blockchain and persist between function calls. Their visibility affects how they can be accessed:

- Public:
    - Can be accessed internally, by derived contracts, other contracts, and externally (e.g., via a client like Web3.js).
    - Automatically generates a getter function with the same name as the variable, allowing external read access.
    - Public variables are readable externally even without explicit function calls, but writing requires a function.
- Private:
    - Only accessible within the contract where defined; not accessible by derived contracts or externally.
    - Private does not mean "secure" on the blockchain; data is still visible in the blockchain's public state.
    - Default visibility for state variables if no specifier is provided.
    - Not directly accessible externally unless a public function exposes it.
- External: Not applicable to state variables. Solidity restricts external to functions only, as variables are not callable entities.

Local Variables
Local variables (defined within functions) do not use visibility specifiers, as their scope is limited to the function they are defined in. They are not accessible outside the function, regardless of the contract's structure.

Visibility Specifiers for Functions
Functions in Solidity handle the logic of the contract, and their visibility determines where they can be called from:

- Public:
    - Callable from anywhere: within the contract, derived contracts, other contracts, or externally via transactions.
    - Public functions are the most permissive and should be used cautiously to avoid unintended access.
- Private:
    - Only callable within the contract where defined; not accessible by derived contracts or externally.
    - Improves modularity and security by restricting access to sensitive operations.
- Internal:
    - Callable within the contract and by derived contracts through inheritance.
    - Default visibility for functions if no specifier is provided.
    - Not callable externally unless wrapped by a public function.
- External:
    - Only callable from outside the contract (via transactions or by other contracts); not callable internally or by derived contracts without explicit mechanisms.
    - Cannot be called internally without using this, which incurs additional gas costs.