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

        pub var recipeArray: @[Recipe]
        pub var recipeDict: @{String: Recipe} 

        pub resource Recipe {
            pub let name: String
            pub let prep_time: Int
            pub let cook_time: Int
            init() {
                self.name = "Eggplant Parm"
                self.prep_time = 20
                self.cook_time = 50
            }
        }

        pub fun addRecipeToArray(recipe: @Recipe) {
            self.recipeArray.append(<- recipe)
        }

        pub fun addRecipeToDict(recipe: @Recipe) {
            let key = recipe.name

            let oldRecipe <- self.recipeDict[key] <- recipe
            destroy oldRecipe
        }

        pub fun removeRecipeFromArray(index: Int): @Recipe {
            return <- self.recipeArray.remove(at: index)
        }

        pub fun removeRecipeFromDict(key: String): @Recipe {
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

  ```
  pub contract Recipes {

    pub var recipeDict: @{String: Recipe} 

    pub resource Recipe {
        pub let name: String
        pub let prep_time: Int
        pub let cook_time: Int
        init( _name: String, _prep_time: Int, _cook_time: Int) {
            self.name = _name
            self.prep_time = _prep_time
            self.cook_time = _cook_time
        }
    }

    pub fun getReference(key: String): &Recipe {
        return (&self.recipeDict[key] as &Recipe?)!
    }

    init() {
        self.recipeDict <- {
            "Eggplant Parm": <- create Recipe(_name:"Eggplant Parm", _prep_time: 30, _cook_time: 50),
            "Manicotti": <- create Recipe(_name: "Manicotti", _prep_time: 20, _cook_time: 60)
        }
    }
  }
  ```

2. Create a script that reads information from that resource using the reference from the function you defined in part 1.

  ```
  import Recipes from 0x01

  pub fun main(): Int {
    let ref = Recipes.getReference(key: "Manicotti")
    return ref.cook_time
  }
  ```
3. Explain, in your own words, why references can be useful in Cadence.
    - References are a convenient way to access resources without having to move them around


## Chapter 3 - Day 4

1. Explain, in your own words, the 2 things resource interfaces can be used for (we went over both in today's content)
    - Implement requirements:  Resource interfaces can mandate that resources implement fields specified in the interface
    - Restrict access:  Resource interfaces allow you to restrict access to certain fields 

2. Define your own contract. Make your own resource interface and a resource that implements the interface. Create 2 functions. In the 1st function, show an example of not restricting the type of the resource and accessing its content. In the 2nd function, show an example of restricting the type of the resource and NOT being able to access its content.

![image](https://user-images.githubusercontent.com/22729328/174716066-4f31e574-6844-4fde-8fd6-8d6c495f1968.png)
![image](https://user-images.githubusercontent.com/22729328/174716142-2f509f97-c2aa-432f-bf66-4df64d9a796b.png)



3. How would we fix this code?
    ```
    pub contract Stuff {

        pub struct interface ITest {
          pub var greeting: String
          pub var favouriteFruit: String
        }

        // ERROR:
        // `structure Stuff.Test does not conform 
        // to structure interface Stuff.ITest`
        pub struct Test: ITest {
          pub var greeting: String
          pub var favouriteFruit: String //Add favouriteFruit here

          pub fun changeGreeting(newGreeting: String): String {
            self.greeting = newGreeting
            return self.greeting // returns the new greeting
          }

          init() {
            self.greeting = "Hello!"
            self.favouriteFruit = "Apple" //Initialize favouriteFruit here
          }
        }

        pub fun fixThis() {
          //let test: Test{ITest} = Test()
          let test: Test = Test()  //Remove interface restriction
          let newGreeting = test.changeGreeting(newGreeting: "Bonjour!") // ERROR HERE: `member of restricted type is not accessible: changeGreeting`
          log(newGreeting)
        }
    }
    ```

## Chapter 3 - Day 5

For today's quest, you will be looking at a contract and a script. You will be looking at 4 variables (a, b, c, d) and 3 functions (publicFunc, contractFunc, privateFunc) defined in SomeContract. In each AREA (1, 2, 3, and 4), I want you to do the following: for each variable (a, b, c, and d), tell me in which areas they can be read (read scope) and which areas they can be modified (write scope). For each function (publicFunc, contractFunc, and privateFunc), simply tell me where they can be called.

```
    access(all) contract SomeContract {
        pub var testStruct: SomeStruct

        pub struct SomeStruct {

            //
            // 4 Variables
            //

            pub(set) var a: String
            pub var b: String
            access(contract) var c: String
            access(self) var d: String

            //
            // 3 Functions
            //

            pub fun publicFunc() {}
            access(contract) fun contractFunc() {}
            access(self) fun privateFunc() {}


            pub fun structFunc() {
                /**************/
                /*** AREA 1 ***/
                /**************/
                
                /*
                Read: 
                [Var] - a
                [Var] - b
                [Var] - c
                [Var] - d
                
                Modified:
                [Var] - a
                [Var] - b
                [Var] - c
                [Var] - d
                
                Access Scope:
                [Fcn] - publicFunc()
                [Fcn] - contractFunc()
                [Fcn] - privateFunc()

             */
            }

            init() {
                self.a = "a"
                self.b = "b"
                self.c = "c"
                self.d = "d"
            }
        }

        pub resource SomeResource {
            pub var e: Int

            pub fun resourceFunc() {
                /**************/
                /*** AREA 2 ***/
                /**************/
                
                /*
                Read: 
                [Var] - a
                [Var] - b
                [Var] - c
                
                Modified:
                [Var] - a

                Access Scope:
                [Fcn] - publicFunc()
                [Fcn] - contractFunc()

             */
            }

            init() {
                self.e = 17
            }
        }

        pub fun createSomeResource(): @SomeResource {
            return <- create SomeResource()
        }

        pub fun questsAreFun() {
            /**************/
            /*** AREA 3 ****/
            /**************/
            
            /*
                Read: 
                [Var] - a
                [Var] - b
                [Var] - c
                
                Modified:
                [Var] - a

                Access Scope:
                [Fcn] - publicFunc()
                [Fcn] - contractFunc()

             */
        }

        init() {
            self.testStruct = SomeStruct()
        }
    }
```

This is a script that imports the contract above:

 ```
    import SomeContract from 0x01

    pub fun main() {
      /**************/
      /*** AREA 4 ***/
      /**************/
      
      /*
        Read: 
        [Var] - a
        [Var] - b
        
        Modified:
        [Var] - a

        Access Scope:
        [Fcn] - publicFunc()

     */
      
    }

 ```

## Chapter 4 - Day 1
1. Explain what lives inside of an account.
    - Contract code and all of your data (account storage) lives inside an account

2. What is the difference between the /storage/, /public/, and /private/ paths?
    - They have difference access level. 
    - /storage is only accessible to account owner
    - /public is accessible to anyone
    - /private is accessible to account owner and those owner gives access to

3. What does .save() do? What does .load() do? What does .borrow() do?
    - .save() saves data to account storage
    - .load() takes data out of account storage
    - .borrow() gets a reference to resource in storage in order to simply look at it

4. Explain why we couldn't save something to our account storage inside of a script.
    - account storage is not accessible from a script but from the prepare stage in a transaction

5. Explain why I couldn't save something to your account.
    - data is saved to /storage and /storage is only accessible to the account owner

6. Define a contract that returns a resource that has at least 1 field in it. 
    
    ```
      pub contract Recipes {

          pub resource Recipe {
              pub let name: String
              pub let prep_time: Int
              pub let cook_time: Int
              init( _name: String, _prep_time: Int, _cook_time: Int) {
                  self.name = _name
                  self.prep_time = _prep_time
                  self.cook_time = _cook_time
              }
          }

          pub fun createRecipe(): @Recipe{
              let myRecipe: @Recipe <- create Recipe(_name:"Eggplant Parm", _prep_time: 10, _cook_time: 40)
              return <- myRecipe
          }
      }
    ```

   Then, write 2 transactions:

      - i. A transaction that first saves the resource to account storage, then loads it out of account storage, logs a field inside the resource, and destroys it.

          - Save resource to account storage
              ```     
              import Recipes from 0x01

              transaction {

              prepare(acct: AuthAccount) {
                  acct.save(<- Recipes.createRecipe(), to: /storage/myRecipe)
              }

              execute {}

              }
              ```

          - Loads, logs, and destroys resource from account storage
              ```     
              import Recipes from 0x01

              transaction {

              prepare(acct: AuthAccount) {
                  let myRecipe <- acct.load<@Recipes.Recipe>(from: /storage/myRecipe)!

                  log(myRecipe.name)
                  destroy myRecipe
              }

              execute {}

              }
              ```

      - ii. A transaction that first saves the resource to account storage, then borrows a reference to it, and logs a field inside the resource.

          - Save resource to account storage
              ```     
              import Recipes from 0x01

              transaction {

              prepare(acct: AuthAccount) {
                  acct.save(<- Recipes.createRecipe(), to: /storage/myRecipe)
              }

              execute {}

              }
              ```

          - Borrows and logs resource from account storage
              ```     
              import Recipes from 0x01

              transaction {

              prepare(acct: AuthAccount) {
                  let myRecipe = acct.borrow<&Recipes.Recipe>(from: /storage/myRecipe) ?? panic("Could not borrow recipe")

                  log(myRecipe.name)
              }

              execute {}

              }
              ```
      
## Chapter 4 - Day 2
## Chapter 4 - Day 3
## Chapter 4 - Day 4

## Chapter 5 - Day 1
## Chapter 5 - Day 2
## Chapter 5 - Day 3

