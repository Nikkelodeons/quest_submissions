# quest_submissions

## Chapter 1 - Day 1

Explain what the Blockchain is in your own words. 
- A blockchain is a distributed database that stores data on nodes of a computer network

Explain what a Smart Contract is. 
- A smart contract is an application that determines the rules in which users can interact with the blockchain

Explain the difference between a script and a transaction.
- A script allows users to view data and is free.  A transaction makes changes to data on the blockchain and costs money. 

## Chapter 1 - Day 2

What are the 5 Cadence Programming Language Pillars?
- Safety & Security
- Clarity
- Approachability
- Developer Experience
- Resource Oriented Programming

In your opinion, even without knowing anything about the Blockchain or coding, why could the 5 Pillars be useful (you don't have to answer this for #5)?
- The 5 pillars could be useful to:
  - make it easier for more developers to learn Cadence thus attracting more developers to flow
    - the more developers on flow, the more applications exist for users to interact on flow which could increase user participation on the flow blockchain
  - make it easy to ensure the security of smart contracts so users' valuables are not compromised on the blockchain
  - make the flow blockchain more mainstream


## Chapter 2 - Day 1

1. Deploy a contract to account 0x03 called "JacobTucker". Inside that contract, declare a constant variable named is, and make it have type String. Initialize it to "the best" when your contract gets deployed.
![image](https://user-images.githubusercontent.com/22729328/172503932-31f58283-4c98-41a5-8c7a-d24d379a4c55.png)

2. Check that your variable is actually equals "the best" by executing a script to read that variable. Include a screenshot of the output.
![image](https://user-images.githubusercontent.com/22729328/172503850-77036141-28c9-4ff6-91f7-52d7a46b94dc.png)


## Chapter 2 - Day 2

1. Explain why we wouldn't call changeGreeting in a script.
    - The changeGreeting function literally changes data in the greeting string in the contract.  Anything that modifies data on the blockchain is a transaction.  Scripts only view data on the blockchain.

2. What does the AuthAccount mean in the prepare phase of the transaction?
    - AuthAccount is what is used to access data in the signer's account in order to approve a transaction.

3. What is the difference between the prepare phase and the execute phase in the transaction?
    - In the prepare phase, we have access to the data in the account.  In the execute phase we do not. The execute phase is where we change data on the blockchain.

4. This is the hardest quest so far, so if it takes you some time, do not worry! I can help you in the Discord if you have questions.
Add two new things inside your contract:

A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber
Add a script that reads myNumber from the contract

<img width="1220" alt="image" src="https://user-images.githubusercontent.com/22729328/173421055-e315e80e-f23f-44f7-b2db-db2262dbb2e3.png">
<img width="1220" alt="image" src="https://user-images.githubusercontent.com/22729328/173421226-38d8c946-9bed-4ddd-8701-39800cc0901c.png">

Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.

<img width="1220" alt="image" src="https://user-images.githubusercontent.com/22729328/173421322-8afce685-fb53-413c-bd41-214b7edf8b90.png">
<img width="1220" alt="image" src="https://user-images.githubusercontent.com/22729328/173421384-ea30f2cf-eb9d-475a-a7d4-38ef642aa1f6.png">


## Chapter 2 - Day 3
In a script, initialize an array (that has length == 3) of your favourite people, represented as Strings, and log it.
![image](https://user-images.githubusercontent.com/22729328/174155297-e6486f56-9f08-4fd8-9011-33a47a59c4fa.png)

In a script, initialize a dictionary that maps the Strings Facebook, Instagram, Twitter, YouTube, Reddit, and LinkedIn to a UInt64 that represents the order in which you use them from most to least. For example, YouTube --> 1, Reddit --> 2, etc. If you've never used one before, map it to 0!
![image](https://user-images.githubusercontent.com/22729328/174154924-82014a79-5aa2-41d0-8b88-ee45386c2df5.png)

Explain what the force unwrap operator ! does, with an example different from the one I showed you (you can just change the type).
Given an optional type can be either a datatype or a nil, the force unwrap declares whether the variable is in fact the datatype or the nil, ie:

```
pub fun main(): String {                                                // return type is expected to be a String
  var sampleDict: {String: String} = {"Mary": "J", "Biggie": "Smalls"}
  return sampleDict["Mary"]!                                            //without !, the return type would be String?
}
```

Using this picture below, explain...

- What the error message means: 
  - The expected return type is a String.  An optional was returned instead
- Why we're getting this error: 
  - Dictionaries return optionals by default.  Therefore the return type should be an optional or the element returned should be forced unwrapped to reveal a String
- How to fix it:

  - Option 1: 
    ```
    pub fun main(): String? {
      let thing: {Address: String} = {0x01: "One", 0x02: "Two", 0x03: "Three"}
      return thing[0x03]
    }
    ```

  - Option 2:
    ```
    pub fun main(): String {
      let thing: {Address: String} = {0x01: "One", 0x02: "Two", 0x03: "Three"}
      return thing[0x03]!
    }
    ```

## Chapter 2 - Day 4

Deploy a new contract that has a Struct of your choosing inside of it (must be different than Profile).

Create a dictionary or array that contains the Struct you defined.

Create a function to add to that array/dictionary.

Add a transaction to call that function in step 3.

Add a script to read the Struct you defined.


## Chapter 3 - Day 1
## Chapter 3 - Day 2
## Chapter 3 - Day 3
## Chapter 3 - Day 4
## Chapter 3 - Day 5

## Chapter 4 - Day 1
## Chapter 4 - Day 2
## Chapter 4 - Day 3
## Chapter 4 - Day 4

## Chapter 5 - Day 1
## Chapter 5 - Day 2
## Chapter 5 - Day 3

