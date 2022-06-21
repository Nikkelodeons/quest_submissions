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
![image](https://user-images.githubusercontent.com/22729328/174701199-0dd42b60-c83d-4d49-a4bd-63ea4d124a48.png)


Create a dictionary or array that contains the Struct you defined
```
pub contract Recipes {

    pub var recipeDict: {String: Recipe}

    pub struct Recipe{

        pub let name: String
        pub let diet: String
        pub let prep_time: Int
        pub let cook_time: Int

        init(_name: String, _diet: String, _prep_time: Int, _cook_time: Int){
            self.name = _name
            self.diet = _diet
            self.prep_time = _prep_time
            self.cook_time = _cook_time
        }
    }

    init() {
        var recipe = Recipe(_name: "eggplant parm", 
                            _diet: "vegetarian",
                            _prep_time: 20,
                            _cook_time: 40)
        self.recipeDict = {}
        self.recipeDict[recipe.name] = recipe
    }


}
```

Create a function to add to that array/dictionary.
```
pub contract Recipes {

    pub var recipeDict: {String: Recipe}

    pub struct Recipe{

        pub let name: String
        pub let diet: String
        pub let prep_time: Int
        pub let cook_time: Int

        init(_name: String, _diet: String, _prep_time: Int, _cook_time: Int){
            self.name = _name
            self.diet = _diet
            self.prep_time = _prep_time
            self.cook_time = _cook_time
        }
    }

    pub fun addRecipe(name: String, diet: String, prep_time: Int, cook_time: Int){
        let newRecipe = Recipe(_name: name,
                               _diet: diet,
                               _prep_time: prep_time,
                               _cook_time: cook_time)

        self.recipeDict[name] = newRecipe

    }

    init() {
        var recipe = Recipe(_name: "eggplant parm", 
                            _diet: "vegetarian",
                            _prep_time: 20,
                            _cook_time: 40)
        self.recipeDict = {}
        self.recipeDict[recipe.name] = recipe
    }


}
```

Add a transaction to call that function in step 3.
```
import Recipes from 0x01

transaction(name:String, diet: String, prep_time: Int, cook_time: Int){

    prepare(signer: AuthAccount) {}

    execute {
        Recipes.addRecipe(name:name, diet:diet, prep_time: prep_time, cook_time:cook_time)
    }
}
```

Add a script to read the Struct you defined.
![image](https://user-images.githubusercontent.com/22729328/174704925-50dc7a4c-c72e-4a0e-b323-d9fc2d4dbb2c.png)



## Chapter 3 - Day 1
1. In words, list 3 reasons why structs are different from resources.
    - Structs can be copied.  Resources cannot be copied
    - Structs can be overwritten.  Resources cannot be overwritten
    - Structs can be created whenever you want.  Resources cannot be created whenever you want.

2. Describe a situation where a resource might be better to use than a struct.
    - NFTs are meant to be unique therefore resources can accommodate this attribute since they cannot be copied.

3. What is the keyword to make a new resource?
    - create

4. Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?
    - No.  Resources can only be created via the "create" keyword which can only be used inside a contract

5. What is the type of the resource below?

      pub resource Jacob {

      }
        - type is Jacob

6. Let's play the "I Spy" game from when we were kids. I Spy 4 things wrong with this code. Please fix them.
      ```
      pub contract Test {

          // Hint: There's nothing wrong here ;)
          pub resource Jacob {
              pub let rocks: Bool
              init() {
                  self.rocks = true
              }
          }

          /* -----------------  WRONG ----------------------
          pub fun createJacob(): Jacob { // there is 1 here
              let myJacob = Jacob() // there are 2 here
              return myJacob // there is 1 here
          }
          --------------------  WRONG ----------------------*/

          //--------------- CORRECT ---------------
          pub fun createJacob(): @Jacob{
              let myJacob: @Jacob <- create Jacob()
              return <- myJacob
          }
      }
      ```
      
## Chapter 3 - Day 2
Write your own smart contract that contains:
- Two state variables: 
    - An array of resources 
    - A dictionary of resources. 
- Fcn to remove each of them
- Fcn to add to each of them. 

```
pub contract Recipes {

    pub var recipeArray: @[SavoryRecipe]
    pub var recipeDict: @{String: SavoryRecipe} 

    pub resource SavoryRecipe {
        pub let _name: String
        pub let _prep_time: Int
        pub let _cook_time: Int
        init() {
            self.name = _name
            self.prep_time = _prep_time
            self.cook_time = _cook_time
        }
    }
  
    pub fun addRecipeToArray(recipe: @SavoryRecipe) {
        self.recipeArray.append(<- recipe)
    }

    pub fun addRecipeToDict(recipe: @SavoryRecipe) {
        let key = recipe.name
        
        let oldRecipe <- self.recipeDict[key] <- recipe
        destroy oldRecipe
    }

    pub fun removeRecipeFromArray(index: Int): @SavoryRecipe {
        return <- self.recipeArray.remove(at: index)
    }
    
    pub fun removeRecipeFromDict(key: String): @SavoryRecipe {
        let recipe <- self.recipeDict.remove(key: key)!
        return <- recipe
    }

    init() {
        self.recipeArray <- []
        self.recipeDict <- {}
    }

}
```


## Chapter 3 - Day 3
1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.

2. Create a script that reads information from that resource using the reference from the function you defined in part 1.

3. Explain, in your own words, why references can be useful in Cadence.
  - References are a convenient way to access resources without having to move them around


## Chapter 3 - Day 4
## Chapter 3 - Day 5

## Chapter 4 - Day 1
## Chapter 4 - Day 2
## Chapter 4 - Day 3
## Chapter 4 - Day 4

## Chapter 5 - Day 1
## Chapter 5 - Day 2
## Chapter 5 - Day 3

