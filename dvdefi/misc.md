## exponential notation
To avoid floating point inaccuracies that come with varying hardware, solidity uses fixed point arithmetic instead of floating point. Tokens define a decimal value that represents how many decimals of precision the token supports.
### example
ExampleToken with 5 decimals of precision.
`100000 == 1        Example Token`
`1      == 1/100000 Example Token`
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
