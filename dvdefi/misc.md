## exponential notation
To avoid floating point inaccuracies that come with varying hardware, solidity uses fixed point arithmetic instead of floating point. Tokens define a decimal value that represents how many decimals of precision the token supports.
### example
ExampleToken with 5 decimals of precision.
```
100000 == 1        Example Token
1      == 1/100000 Example Token
```
## ETH
Ethereum currency used in transactions.
## WEI
1e18 WEI is equal to 1 ETH.
See [[#exponential notation]]
## GWEI
Stands for giga-wei, or 1 billion WEI. Gas costs are usually quotes in GWEI.
## Gas
Gas is the unit to represent the amount of computational effort to perform specific operations on the Ethereum network.
## ERC20
Token standard used to define how contracts trade tokens with one another.
One of the popular token standards, there are other token standards as well.
## Transaction
Refers to an action initiated by an externally owned account ([[#Accounts#External]]). This can be a request between one EOA and another, or an EOA sending a request to a contract account. A transaction can be thought of a request that sends data from an EOA to another account that updates state of the Ethereum network.
## Accounts
### External
- also known as externally owned accounts (EOA)
- represented by a private/public key pair
- controlled by anyone who knows the private key
- creation of an external account costs nothing
- can initiate transactions
### Contract
- represented by an address
- controlled by owner, which is initially the account that created the contract
- creation has a cost
- cannot autonomously initiate transactions
	- can however initiate transactions in response to receiving a transaction request
## Solidity ABI
### Function Selector
The first four bytes of the call data for a function call specifies the function to be called. It is the first (left, high-order in big-endian) four bytes of the Keccak-256 hash of the signature of the function. The signature is defined as the canonical expression of the basic prototype without data location specifier, i.e. the function name with the parenthesized list of parameter types. Parameter types are split by a single comma - no spaces are used.
> add(uint256,uint256)

The return value type is not considered to be part of the signature.
### Arguments
All arguments are encoded padded to 32 bytes with zeros in big endian byte order.
#### Numbers
`uint[n]` types, where `n` is a maximum of 256 bits, are all encoded as is and padded to 32 bytes. Signed numbers are sign extended to int256.
#### Bool
`bool` is treated as `uint8` type.
#### Address
`address` is treated as a `uint160` type.
#### Arrays
The encoded argument is an offset into the input data where the rest of the data is stored. The argument is again padded to 32 bytes.
## Inline Assembly
```
assembly {
	call(g, a, v, in, insize, out, outsize)
}
```
> call contract at address a with input `mem[in…(in+insize))` providing g gas and v wei and output area `mem[out…(out+outsize))` returning 0 on error (eg. out of gas) and 1 on success

The input memory follows the solidity ABI encoding to specify the target function and arguments.