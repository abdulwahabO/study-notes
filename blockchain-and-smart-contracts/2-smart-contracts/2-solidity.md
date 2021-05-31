## Source files and contracts

A Solidity source file can contain any number of contract definitions, import directives and pragma directives, struct and function definitions etc.

The compiler expects every source file to contain a machine readable license header. E.g.
`// SPDX-License-Identifier: MIT`. If the source is not open source, `UNLICENSED` can be used in place of a license identifier.

The `pragma` keyword is used to enable certain compiler features or checks. The version pragma statement e.g., `pragma solidity ^0.5.2;` is used to protect against compilation by a compiler that is incompatible with the specified version. 

Import statements can be use to import global symbols declared in another file. E.g.
`import "./filename.sol" as SymbolName`. The symbols can then be used in the current file e.g., `SymbolName.someFunction(x,y)`.

NatSpec comments are used to document public symbols of a contract. [Learn more](https://docs.soliditylang.org/en/latest/natspec-format.html#natspec)

Every Solidity contract can have declarations for:

* `structs` - A struct is a composite type that contains one or more variables.
* `state variables` - These are varibles whose values are permanently stored on the Blockchain.
* `functions` - Executable units of code that can be defined inside or outside a contract.
* `function modifiers` - This can be used to alter the behavior of a function.
* `events` - An abstraction on the EVM's logging functionality. Dapps can use, contracts cannot.
* `enums` - custom type with a finite set of constant.
* `errors` - Allow for custom names and data for failure scenarios.

See [Source file Layout](https://docs.soliditylang.org/en/latest/layout-of-source-files.html) and [Contracts Overview](https://docs.soliditylang.org/en/latest/structure-of-a-contract.html) in the official documentations.

## Types

The concepts of `undefined` and `null` values do not exist in Solidity. Instead, uninitialized variables have a default value that depends on the type. 

### Value types

These are always copied (passed by value) when used in assignments or as function arguments. These are the language primitives. These are: 

* boleans - `true`, `false` 
* integers - `int8`/ `uint8` to `int256`/`uint256`, in steps of 8(i.e., 8, 16, 32...). `int` and `uint` are aliases for `int256` and `uint256`
* addresses - `address` and `address payable` (The later can receive ether, the former cannot)
* contracts - Variables representing a contract.
* Fixed-size byte arrays - `bytes1` to `bytes32`
* String literals - can be in "double" or 'single' qoutes, and support some escape characters.
* Unicode literals - String literals prefixed with `unicode` keyword.
* Hexadecimal literals - prefixed with keyword `hex`. E.g., `hex"001122FF"` 
* Enums - (explicitly convertible to integer types)
* Function types - [Read More About Function Types](https://docs.soliditylang.org/en/latest/types.html#function-types)

NOTE: Where `X` is an integer type, `type(X).max/min` can be use to get the max or min value that type can hold e.g `type(uint8).max` will return 255.

NOTE: By default, all arithmetic operations are checked for integer overflow or underflow. I.e., if the result of an operation falls outside the range for the variable to which it is been assigned, the call is reverted through a failing assertion. This can be disabled using an `unchecked{...}` block, in which case undeflowing or overflowing values are wrapped.

NOTE: Fixed point numbers are not yet fully supported. Floating point numbers do not exist in Solidity.

NOTE: `address payable` can be implicitly converted to `address`. The reverse must be explicit in the form of `address payable xyz = payable(address)`. Contracts can be converted to `address`, and contracts that can receive ether can also be explictly converted to `address payable`. This makes it possible to use `address(this).balance` to query the balance of the current contract.

NOTE: `bytes20`, `uint160`, contracts, and literals can be explicitly converted to and from an `address`.

NOTE: `transfer` and `balance` are functions of `address`. They return/take Wei amount as output/input.

### Reference Types

These values are not copied during variable assignment or when passed as function argument. When using these types, the data area where they are stored(`storage`, `memory` or `calldata`) has to be part of their definition. 

The location of data also affects the schematics of assignment:

* Assigments between `memory` variables are not copied. A new reference is created instead.
* Any assignment to `storage` is copied.
* Assignments from `storage` to a local storage variable creates a reference type, not a copy.

Reference types:

* Arrays - can be of dynamic(`T[]`) or fixed sized(`T[n]`). E.g., `uint8[][3]` is a fixed size array containing three dynamically sized arrays(uint[]). `string[]` is dynamic array of strings. Array elements can be of ANY type.
* `bytes` and `string` - These are special kinds of arrays.
* `struct` - Composite types containing many valuables.
* mapping types - Declared as `mapping(keyType => valueType)` 

NOTE:  It is not possible to resize memory arrays. The `push()` and `pop()` functions are not available for memory arrays. 

NOTE: Mapping type keys can be: Any built-in types, contracts, and enums. Arrays, mappings and structs cannot be keys. Values can be of ANY type. A `keccak256` hash of the keys is used to look up values.

NOTE: The only data location for mappings is `storage`. They are for state variables, function storage reference types, and parameters for library functions. Mappings cannot be used as as parameters or return parameters of contract functions that are publicly visible. 

NOTE: Mappings that are state variables can be marked as `public`, and a getter is automatically created. The getter takes a variable of the key type as a argument, and returns the value matching that key.

NOTE: For the `enum` type, the default value is its first member.

The `delete` keyword can be used to reset the value stored in a variable to it's default. See [delete](https://docs.soliditylang.org/en/latest/types.html#operators-involving-lvalues)

Learn more about [Arrays](https://docs.soliditylang.org/en/latest/types.html#arrays)
and [Reference Types](https://docs.soliditylang.org/en/latest/types.html#reference-types)

## Units and Global Variables

Numbers can take a suffix of `wei`, `gwei` and `ether` to specify subdenomination of Ether.
1 wei = 1 x 10^-18 ether. Ether amounts can be specified as `1 wei`, `2 ether`, etc. Numbers without a suffix are assumed to be in Wei. So, `5 == 5 wei or 5 x 10^-18 ether`.

Time literals without a suffix are assumed to be seconds. `4 == 4 seconds`.
One of `seconds`, `minutes`, `hours`, `days` and `weeks` can be used as a suffix for a time unit.
These suffixes can not be applied to variable, instead they can be applied as such: `variable * 1 days`

Block, message and transaction properties are available in the properties `block.*`, `msg.*`, `tx.*`;

Type information can be obtained from `type(X).*` where `X` is a built-in type or a contract.

See [Units and Global Variables](https://docs.soliditylang.org/en/latest/units-and-global-variables.html)


## Control structures and expressions

The `revert` statement is used to create errors. loops and if statements are similar to those in JavaScript. 

Internal function calls happen within a contract. External function calls happen via message calls to another contract. A function call to another contract DOES NOT create a new transaction, instead it creates a message call that is part of the current transaction.

Function call arguments can be passed by name in any order. E.g., `setDetails({name: "Ade", age: 25})`

A new contract can be created from within another by use of the `new` keyword. Contracts created this way can use a salt, so that the address is known before hand.

Tuples can be used to return a fixed-size collection of different types from a function.

```solidity
fn get() returns (int, string) {
    return (4, "A string literal");
}

(int value, string label) = get();
```

Solidity uses exceptions to revert state changes. `Panic(uint256)` is used for errors that should not happen and cannot be handle by the code. While `Error(string)` is used for expected errors.

The `require` function either creates an error without any data or an error of type `Error(string)`. It should be used to ensure valid conditions.

The `assert` function will throw a `Panic` and should be used to check for internal errors that should not be happening. E.g., division by zero.

The `revert` keyword is used for custom errors manually. E.g.,

```solidity
if (!condition) revert SomeCustomError();
```

NOTE: Using a custom error instance will usually be much cheaper than a string description, because you can use the name of the error to describe it, which is encoded in only four bytes. A longer description can be supplied via NatSpec which does not incur any costs.

```solidity
/// This is thrown when the transaction is sent from an address with blah blah...
error UnauthorizedTransactionError();
```

A try/catch clause can be used to catch any errors in an external contract call.

```solidity
    SomeContract c; // This a contract known to current one. (imported or defined)

    try c.getSomething(uint someInt) returns (string name, int age) {
        // do something with return values.
        string name2 = name;
    } catch Error(string memory res) {

    } catch Panic(uint code) {

    } catch(bytes memory data) {

    }
```

## Contracts

When a contract is created, its constructor is executed once. Only one constructor is allowed, so overloading is not supported. After the constructor is executed, the code for the contract is deployed on the EVM. This deployed code does not include the constructor or any internal functions that are only called by the constructor.

Functions and state variables can be:

* `external` - Part of the contract interface. Can be called by other contracts and via transactions, cannot be called internally. This cannot be used for state variables.

* `public` - Can be called by other functions internally, by other contracts and via transactions. For public state variables, this annotation causes a getter to be generated.

* `internal` - Can only be called internally and by contracts that derive from the current contract. This is the default visibility for state variables.

* `private` - Not visible to derived contracts.

For a public array that is a public state variable, the getter only returns one element(specified by index). This is to reduce high gas fees. To get the entire array in one call, one must define a function.

Function modifiers are a declarative way of changing the behaviour of a function. E.g., automatically checking a condition before executing the function. Modifiers can be overridden by a inheriting contract if they are marked `virtual`.

`_` in the modifier definition is replace by the function body at runtime. So they essentially wrap round the function.

State variables can be declared as `constant`(set at compile time) or `immutable`(set during construction). Constant varibles can also be declared at file level. These variables are not kept in storage, instead each occurence is replaced with the value. These also use less gas than mutable state variables.

View functions "promise" not to modify state. `Pure` functions promise not read or modify state.

Contracts can have at most one receive function. Defined as `receive() external payable { ... }`. If this function or a fallback function does not exist, then the contract cannot receive Ether and will error. A fallback function is used if none of the defined functions the function name in a transaction or if a receive ether function does not exist.

_Events_ are built on the EVM's logging abstraction. Dapps can subscribe and listen to events through an Ethereum client. When events are created, they can have arguments which are stored in the `transaction log`. When event parameters(up to three) are `indexed` they are stored in a special data structure known as a `topic`. Anonymous events can have up to four indexed parameters. For named events, the hash of the event signature is the first topic(i.e `topics[0]`). Indexed parameters of reference type will simply have the `keccak256` hash of their argument stored in the topic.

_Errors_ can have parameters. They cannot be overloaded or overridden, but they can be inherited. New instance can only be created using `revert`. Errors can only be caught by a transaction sender or external caller when they happen in the called function, reverts happening in an internal function cannot be caught by the transaction sender or message caller.

When a contract inherits from another, only one contract is created and stored on the blockchain. The parent contract code is compiled as part of the child contract. If the constructor of an inherited contract has a parameter, The argument is the signature of the inheriting contract.

`Abstract contracts` have at least one function that is not implemented. `Interfaces` contain only functions that are not implemented.

The code contained in libraries is executed in the context of the calling contract. I.e., `this` would refer to the calling contract.