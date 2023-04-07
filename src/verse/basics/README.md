# Preface

The information contained here is best learned by typing it in (not copying!) while you read. Create a new verse script in UEFN and follow along!

> Use this information in additon to the [Official Verse documentation]({{ book.external.links.uefn_verse.learn }}) along with the [Verse Language Reference]({{ book.external.links.uefn_verse.language_reference }}).

> {% include [book.partials.path, '/download_vs_code.md'] | join %}

# Verse Basics

While learning a new programming language, or programming in general, can feel like a daunting task, it's much easier to digest when broken up into chunks. We'll review the very basics of Verse, starting with comments.

## Comments

Comments in code are like little notes that you leave for your future self or team members. They are defined with the pound sign (`#`) before a line of text.

```ruby
# This is a comment and won't be recognized as code by UEFN.

# Comments can be put
# on multiple lines

SomeCodeHere() # They can even be put on the same line as other code!
```

I can hear you thinking to yourself, "But I wrote this code, of course I know what it does and how it works!". That may be true a day or even a week from now, but what about 6 months or a year from now. Putting in a helpful comment can save you, and your teammates, hours or even days of headaches! A great example of good commenting pratice is in our [Custom NPC Dialog Example]({{ book.examples.path }}/custom_npc_dialog/README.md)

## Numbers

Numbers are widely used in programming. You an use them to perform math operations, track the amount of coins a player has, how full the gas tank in your vehicle is, etc. In Verse, there are 2 types of numbers: `whole` and `fractional`. Whole numbers have the data type of `int` and fractional numbers have the data type of `float`, which we'll see more when we talk about variables.

```ruby
1      # A whole number is a number without a fractional component i.e. no decimal places after the number
-1     # Whole numbers can also be negative
3.14   # Fractional numbers are numbers with a decimal point
-3.14  # Fractional numbers can also be negative
```

## Strings

Another important concept in programming is the `string` data type. A `string` can be a word or a sentence which can be used to display text to the player, for example.

```ruby
"Verse is my favorite programming language!"
```

We can see that strings are words separated by spaces surrounded by double quotes (`"`).

### Concatenation

Concatenation means to combine multiple items into a single item. There are two ways in Verse to use string concatenation:

1. Strings can use the `+` operator to combine multiple strings into one.
2. Strings can insert variables into a word or sentence using opening and closing curly braces (`{}`).

> Variables are coming up next and operators after that!

```ruby
"This is a very " + "long sentence that is " + "broken up with multiple strings"

AmountOfCoins : int = 10
MyName : string = "I have {AmountOfCoins} coins!" # Produces the string "I have 10 coins!"
```


## Variables

Variables are an essential part of programming. A variable allows the programmer to store data of certain types to use, or change, later in the program. Variables in Verse are immutable by default. The naming convention for variables differ from language to language, but in Verse, they start with an upppercase letter using camel case.

```ruby
NumberOfItems : int = 15
```

Whoa! What does that mean?! Let's break this down:

1. `NumberOfItems` is the variables name. We give it a name so that we can refer to it later in our program.
2. The syntax `: int` tells UEFN that we want to make this variable an int type.
3. The last part `= 15` means we give this variable the value of `15`.

Let's see some more examples of variables:

```ruby
NPCName : string = "Viktor"
IsOnFire : logic = false
PI : float = 3.14
```

Don't worry if you don't recognize some of these data types. We'll go over them in future lessons!

> The [UEFN documentation]({{ book.external.links.uefn_verse.common_types }}) has even more examples of the different types of variables you can use!

### Updating Variables

If Verse variables are immutable by default, how do we change them? There is a special keyword in Verse called `var`. Using `var` before the name of a variable makes it mutable, allowing us to change it with the help of the `set` keyword.

```ruby
var IsOnFire : logic = true

...some other code here to put out the fire...

set IsOnFire = false
```

If you forget to use either the `var` or `set` keywords, both VS Code will show you errors with a reason why it's failing and UEFN will give you errors when you try to build your Verse code in the editor.

Numbers can use a special operator syntax when updating their value.

> We'll get into operators next.

```ruby
var NumberOfCoins : int = 10

# Update the value
set NumberOfCoins = NumberOfCoins + 5
# or
set NumberOfCoins += 5
```

We can see that we can use `+=` to update the value of the numbers of coins we have without stating the variable name twice i.e. `NumberOfCoins = NumberOfCoins + 5`. This special syntax can also be used with other math operators: `-=`, `*=`, `/=`.

## Operators

Operators are special constructs in programming that allow us to perform operations like Math. Math is an important skill to have in video game programming. Don't worry! The math we'll do here is really easy to follow. Let's cover the most used operators in Verse.

```ruby
1 + 1    # The `+` operator allows us to perform addition.
10 - 1   # The `-` operator allows us to perform subtraction.
5 / 2.5  # The `/` operator allows us to perform division.
5 * 2    # The `*` operator allows us to perform multiplication.
```

## Optionals

An optional value is a variable that either does or doesn't have value. Optional values are great when you might have some data or you might not.

```ruby
var MaybeNPCName : ?string = false
```

The syntax for optional values is `?data_type`, specifically a question mark (`?`) followed by the name of the data type i.e. `?string`. We see that `MaybeNPCName` is set to a value of `false` to begin with. This means we don't have a `string` value when we define this variable.

### Updating Optionals

As our program progresses, we now have the need to assign `MaybeNPCName` to a `string` value.

```ruby
set MaybeNPCName = option{ "Francis" }
```

To set the new value of an optional data type, we need to wrap the type of value, `string` in this case, with an `option` object.

> Although not required, it's common to see the word `Maybe` to start an optional variable name. This makes it instantly recognizable that it is an optional value.

### Retrieving Values

To retieve the value of an optional data type, we need to use a `logical statement`. A `logical statement` is a construct that can succeed or fail. Those will be covered next but here is a preview.

```ruby
if (Name := MaybeNPCName?):
    # ...do something with Name...
```

> Logic and objects will be covered in further detail later.

## Logic

Logic is important in any program. It is used to determine if something can or can't happen. We'll go over what logic is and how to use it.

The way we use logic in Verse is by using an `if` statement. Like mentioned, `if` is used to determine `if` something can or can't happen.

```ruby
IsOnFire : logic = true

if (IsOnFire?):
    ScreamInPanic()
```

> When checking an `if` condition with a question mark (`?`), this is called a `query`.

The structure of an `if` statement is broken down as `if (condition-to-check):`. It's required that we use a colon (`:`) after the closing parenthesis (`)`). The next line needs to start with 4 lines of empty space, equal to pushing the TAB key on your keyboard once.

> Verse is a `whitespace dependent` language, meaning if you don't have enough whitespace, or whitespace in the wrong location in your code, it will give you errors.

We also notice that when we set `IsOnFire` to `true`, we did not use a question mark (`?`). With the `logic` data type, we "ask" the variable if it is `true` or `false`. When used in an `if` statement, we "ask" the variable by adding a question mark (`?`) to the end of the variable name with no spaces.

The line that says `ScreamInPanic()` is a method. We'll get into methods a bit later.

`If` statements can also be used in different ways. When we ended the line with the colon (`:`), it created what is known as a `block`. We'll also cover the details of blocks later.

### Branching Logic

As stated before, `if` is used to determine if something can or **can't** happen. In programming, this is known as a `branch`.

```ruby
IsOnFire : logic = true

if (IsOnFire?):
    ScreamInPanic()
else:
    EatSomeLunch()
```

> If we are on fire, we scream in panic! If we are **not** on fire, we eat some lunch.

Expanding the previous example, we can see that there is new information here. Optionally, after the main `if` block, we an add the `else` keyword. You will notice that the `else` keyword is indented the same amount of spaces that the `if` keyword is (0 tabs / spaces, in this case). An `else` always has to line up with the `if` keyword.

Logic branches can be used many, many times within the same `if` statement. We can add additional `if` statements when we attach another `if` to the `else`:

```ruby
IsOnFire : logic = false
IsHungry : logic = true

if (IsOnFire?):
    ScreamInPanic()
else if (IsHungry?):
    EatSomeLunch()
else:
    PlayFortnite()
```

> If we are on fire, we scream in panic! If we are **not** on fire **and** we are hungry, we eat some lunch. Otherwise, we play some Fortnite! 😀

 ### Logical Modifiers

 Logical modifiers allow us to combine conditions into a single `if` statement. These are able to be mixed and matched to produce some interesting effects.

```ruby
IsOnFire : logic = false
IsHungry : logic = true

if (IsOnFire? and IsHungry?):
    ScreamInPanic()
    EatSomeLunch()
else:
    PlayFortnite()
```

> If we are on fire **and** we are hungry, first scream in panic then eat some lunch.

`and` is another keyword which means that both conditions have to be true. If they aren't both true at the same time, then we don't perfom the code in that branch. We also have another keyword: `or`.

```ruby
IsOnFire : logic = false
IsHungry : logic = true

if (IsOnFire? or IsHungry?):
    ScreamInPanic()
    EatSomeLunch()
else:
    PlayFortnite()
```

> If we are on fire **or** we are hungry, first scream in panic then eat some lunch.

`or` is used to to check if either condition is true. If at least one of them is true, then perform the code in that branch. Otherwise, move on.

The final keyword we can use to modify an `if` statement is `not`. `not` means, "check if the conditon is the opposite of it's value" (😵), meaning `not true` is `false` and `not false` is `true`.

```ruby
IsOnFire : logic = false
IsHungry : logic = true

if (IsHungry? and not IsOnFire?):
    ScreamInPanic()
    EatSomeLunch()
else:
    PlayFortnite()
```

> If we are hungry **and** we are **not** on fire, first scream in panic then eat some lunch.

### Equality

When talking about equality in programming, we referring to "is value **exactly equal** to another value or **not**". There are two operators that are used for this purpose.

> Once we cover the details of methods, we'll cover the details operators.

```ruby
# Check if something is equal with the equality operator `=`

NumberOfCoins : int = 10

if (NumberOfCoins = 10):
    # ...perform some more code...

# Check if something is not equal the inequality operator `<>`

if (NumberOfCoins <> 1):
    # ...perform some more code...
```

We can notice that the `equality` operator is the same as assigning a value to a variable, `=`, and we have a new operator `<>` which checks for `inequality`, meaning if two values are **not equal** to one another.

### Logic Context

Vere supplies us with an idea called a `context`. A `context` is a specific place in our code where special, extraordinary things can happen. It sounds strange at first, and to be honest, it kind of is, but `context`s are super powerful. The `if` statement provides us with a fallible `context`. This means the conditions we check for in an `if` statement can fail!

```ruby
IsOnFire : logic = false

if (IsOnFire?):
    # ...do something if on fire...
```

Since `IsOnFire` is given the value of `false`, we can see that this `if` statement has "failed" to satisfy the condition, thus we will not do anything since we are not on fire.

### If Variables

We can also assign a variable inside the condition of an `if` statement. This is useful when you have a method that can either succeed or fail, and if it succeeds, then you can retrieve that variable.

```ruby
if (Coins := GetPlayerCoins[]):
    # ...do something with Coins variable...
```

Wait a minute! We saw how to create a variable and that's not how we did it before! This is a special case where you do not have to define the data type of the variable explicitly. UEFN knows what type of data the `GetPlayerCoins` method gives us, which is super handy! We can also notice that we call the method with square brackets (`[]`) instead of parenthesis (`()`) here. If a method has a chance to fail, we have to use square brackets!

> I know I promised we would talk about methods soon... and we will! Stay tuned!

### Single Line Expressions

When you have an `if` statement that contains a single `else` branch, but not `else if`, you can use a special syntax to help with readability.

```ruby
IsOnFire : logic = true

if (IsOnFire?) then ScreamInPanic() else EatSomeLunch()

# Instead of

if (IsOnFire?):
    ScreamInPanic()
else:
    EatSomeLunch()
```

The syntax breakdown here is `if (condition) then DoSomethingWhenTrue() else DoSomethingWhenFalse()`.

### Single Line Dot Expressions

Identical to `Single Line Expressions` in purpose but written in a different way. This also imporoves readability and it's less typing (win! 😀).

```ruby
IsOnFire : logic = true

if (IsOnFire?) . ScreamInPanic() ; EatSomeLunch()

# Instead of

if (IsOnFire?):
    ScreamInPanic()
else:
    EatSomeLunch()
```

The syntax breakdown here is `if (condition) . DoSomethingWhenTrue() ; DoSomethingWhenFalse()`.

## Arrays

When we create a variable like `MyGrade : string = "A+"`, we can only assign a singluar value to the variable. Arrays help us hold many different values for a single data type.

```ruby
Numbers : []int = array{} # This creates an empty array
```

The syntax of an array is a bit different from a regular variable. When we define the data type of the array, we put open and closing square brackets `[]` before the data type, `int`. This tells UEFN that we want to use an array data type. The varaible's value, the information after the equal sign (`=`), is a new array `object`. Objects are also super important in programming and will be covered later.

> An object is defined by it's name followed by open and closing curly braces i.e. array{}

The above example will assign an `empty array` to the `Numbers` variable. This means it doesn't currently store any data. To create an array that actually stores data, we put some information between the `{` and `}`.

```ruby
Numbers : []int = array{ 1, 2, 3, 4, 5 }
```

Notice how each new number in this array is followed by a comma (`,`). This separates the values from each other. For each new piece of information stored in an array, it needs to be separated from the other by a comma.

### Indexing

Arrays have this concept called an `index`. An `index` is simply the location of an item in an array. Indexing an array can fail because indexing an array is by giving it an arbitrary number as an index.

```ruby
Numbers = []int = array{ 1, 2, 3, 4, 5 }

if (SecondNumber := Numbers[1]):
    # ...do something the second number...
```

There has to be something wrong with the above code, right? Why would the `SecondNumber` be at index `1`? Isn't that the first number? In most programming languages, Verse included, arrays are called `0 indexed`, which simply means that the first item in the array starts at index `0`, not `1`. What happens if we want to get the sixth number in the array?

```ruby
Numbers : []int = array{ 1, 2, 3, 4, 5 }

if (SixthNumber := Numbers[5]):
    # ...do something with SixthNumber variable...
```

This example will halt (stop) the execution of your program immediately. When you try to get the sixth number with the 5th index, it will cause an array out of bounds error to happen, meaning the program tried to access more elements in the array than were defined. When indexing an array in this manner, you must be very careful not to try to access more elements than there are stored inside.

### Updating Arrays

Say you want to change the second item inside an array. How would you go about doing that? Items in arrays can be updated or changed. This is another operation that can fail so we need to use an `if` statement.

```ruby
Numbers : []int = array{ 1, 2, 3, 4, 5 }

if (set Numbers[1] = 10) {}
```

Even though we aren't doing anything in the block of the `if` statement, this operation can fail if the progam tries to index the array outside the defined bounds.

As a learning experience, try to index an array outside of its bounds or update an array with an index that is greater than its bounds. What happens?

### Iteration

Iteration may be a scary sounding word; I know it was for me when I was a new programmer. It is a term in programming that means "go over each item, one at a time". We can use iterators to process or manipulate each piece of data, one item at a time. This is the "safe" way to index into an array because you cannot go outside of its bounds. To do this, we will introduce the `for` keyword:

```ruby
Numbers : []int = array{ 5, 4, 3, 2, 1 }

for (Number : Numbers):
    Print("I have {Number} of lives left!")

Print("I'm dead!")
```

> Print is a method provided by UEFN that allows us to print messages to the log of our game. This example uses string interpolation, which is a topic we will get to when we talk about the details of strings.

The syntax when using for is `for (Item : Collection):`. A collection is a group of data bundled together. Arrays are a type of collection and we will cover another collection type shortly.

Code using the `for` keyword is often called a `for loop`. A `for loop` defines another variable inside its parenthesis (`()`) to allow us to get at each number, one at a time. The `Number` variable can only be used inside the `for loop`'s block. If you try to use it before or after the loop's block, you will get an error. This is known as scoping.

What the above code will does is define a new variable called `Number` which will contain the values `1`, `2`, `3`, `4`, and `5` each time the loop executes. A loop executes over a collection from front to back `for` each item inside the collection. When there are no more items, it stop executing and moves onto the next line of code after the block.

Do you know what the output to this `for` loop would be? An important part of programming is to be able to visualize, as best you can, the outcome of the code before it's even run!

> Did you have a think about it? I sure hope so; it's good for ya 😉.

<details>
    <summary style="display: list-item;">Answer</summary>

    <div style="margin-top: 1rem;">
        <code>I have 5 lives left!</code><br/>
        <code>I have 4 lives left!</code><br/>
        <code>I have 3 lives left!</code><br/>
        <code>I have 2 lives left!</code><br/>
        <code>I have 1 lives left!</code><br/>
        <code>I'm dead!</code><br/>
    </div>
</details>

## Maps

A `map` is another Verse collection that holds key-value pairs of data, that is to say that we can assign a piece of data to a specific name (similar to a variable but not the same). Like arrays, they can hold multiple values.

```ruby
Resources : [string]int = map{}
```

The syntax for the `map` data type is `[key_type]value_type`. We have created a `map` with `string` keys and `int` values. Like arrays, we can initialize the map when we create it.

```ruby
Resources : [string]int = map{ "Wood" => 5, "Stone" => 1, "Steel" => 99, "Coins" => 0 }
```

When creating the key-value pairs of a map, the syntax is `key => value`. This assigns a given `value` to a given `key`. Maps are really useful when you want to give a collection of similar data names without creating multiple variables for each value.

Remember when I said iterators, like `for`, work on collections? We can also use map in `for loops`:

```ruby
Resources : [string]int = map{}

for (Resource -> Amount : Resources):
    Print("I have {Amount} {Resource}!")
```

The syntax of a `for loop` when used with a `map` is `for (Key -> Value : Collection):`. This creates two new variables to use in the `for loop`'s block. These names can be anything, but it's most useful when they are related to the collection being iterated over.

I'm not going to give you the output to this one. Let me know in the [Official Discord]({{ book.external.links.fornite_creative_discord }}) (`@glinesbdev`) server what your solution is.

### Updating Maps

Updating a map is similar to updating an array except instead of indexing by a number, we update the value by its key name.

```ruby
var Resources : [string]int = map{ "Wood" => 5, "Stone" => 1, "Steel" => 99, "Coins" => 0 }

if (set Resources["Coins"] = 10), CoinsAmount := Resources["Coins"]:
    Print("I have {CoinsAmount} of Coins!")
```

No only can we update a `map`'s value by its key, but we can immediately retreive that new value in a new varaible and then get the contents of that varaible, assuming that those two operations didn't fail.


### Removing Items

Unlike arrays, it's possible to remove items from a `map`, it's an operation that can fail. This will give you the chance to see a full method definition before we break methods down in detail.

```ruby
RemoveItemFromMap(Resources : [string]int, KeyToRemove : string) : [string]int =
    # Create a new map to replace the old one (Resources)
    var Result : [string]int = map{}

    # We can combine a `for` and an `if`, in a way. It will iterate over the items in the
    # collection if they meet the condition:
    #
    # If the `KeyToRemove` isn't equal to each key (`Resource`) in the map
    # add it to the new map
    for (Resource -> Amount : Resources, Key <> KeyToRemove):
        set Result[Resource] = Amount

    # Returning a result means that the value of this method will give back the new map
    return Result
```

## Methods

Methods are a way in programming to encapsulate different behavior or perform different steps in a specific order. Let's take the method example from above and break it down:

* `RemoveItemFromMap` -> The name of the method we can use to call (activate) the method at another part of our program.
* `(Resources : [string]int, KeyToRemove : string)` -> The signature of the method which dictates which types of variables this method takes, if any, but also how many and what they are called when used in the `method body`.
* `: [string]int` -> This is called the `return type` of the method. Like variables, methods also *can* give back specific types of data to work with later.
* `=` -> The equal sign (`=`) starts what's called the `method body` where the instructions of the method are defined.

### Into the Void

Unlike variables, methods don't **have** to return any type of data. This is a special type of method in programming called a `void` method. `void` methods just perform instructions without the expectation that the code calling the method will get anything back in return. These types of methods are useful when you need to perform multiple, potentially repeatable steps in your program.

```ruby
SetupPlayerInventory() : void =
    GiveResources()
    GiveWeapons()
    GiveBullets()
```

> The great things about methods is that methods can call other methods in their definition!

In this example, we can see that when we call `SetupPlayer()` somewhere in our code, we will do 3 things in order:

* `GiveResources()`
* `GiveWeapons()`
* `GiveBullets()`

> Methods are best named as what actions they perform i.e. `GiveWeapons()`. This makes it clear what the method is doing so you don't have to revisit the method definition to figure out what it's supposed to be doing in the first place.

### Returning Values

When methods are expected to return a specific type of data, conveniently, we use the `return` keyword.

```ruby
GetNumberOfDaysInWeek() : int =
    return 7
```

Although this is a contrived example, it illustrates how we can get values out of methods. Verse also provides a way to return values without using the `return` keyword.

```ruby
GetNumberOfDaysInWeek() : int =
    7

# OR

GetNumberOfDaysInWeek() : int = 7
```

> Methods can be defined in single line of code, if it's short enough

The last line of code is always the `return` value in a method.

### Early Returns

Say we have have an array that contains some numbers. If it has a specific number in the array, we can perform some action and then `return` from the method early. This can be used with methods that return a data type or a `void` method.

```ruby
Numbers : []int = array{ 1, 2, 3 }

CalloutTheNumberTwo() : void =
    for (Number : Number):
        if (Number = 2):
            Print("We have the number 2!")
            return

        Print("We don't have the number 2...")
```

As we iterate over the `Numbers` array, we check to see if we have the number `2`. If we do, we `Print` a message to the screen and `return` from the function, no longer performing any actions within the method.

> We don't have to use `Print` or any other action here. It's totally valid to just use `return` on it's own.

As we saw in the [Removing Items](#removing-items) section for `map`, we can combine the `for` statement with any number of conditions. If all of those conditions are met, it performs the action.

```ruby
Numbers : []int = array{ 1, 2, 3 }
SkyIsBlue : logic = true

CalloutTheNumberTwo() : void =
    for (Number : Number, Number = 2, SkyIsBlue?):
        Print("We have the number 2 and the sky is blue!")
        return
```

Now we cannot do anything after the `return` in the `for loop` body as we did in the previous example i.e. `Print("We don't have the number 2...")`. To be able to interact with the `Number` variable in the body of the `for loop`, all of the conditions have to be met. Therefore, it will not do anything **until** the `Number` variable is equal to `2` and when `SkyIsBlue` is `true`. Otherwise, it does nothing.

### Side Effects

Methods cause things to happen, which is great! They can also be potentially dangerous... Meaning they can change the data in your program which may be something you didn't expect. This is especially true when using code that you didn't write.

```ruby
var NumberOfCoins : int = 100

# ...instructions of the program...

ChangeClothes() : void =
    # ...defines how clothes are changed...
    set NumberOfCoins -= 10 # An unintended side effect of changing our clothes is first buying a new set!
```

## Objects

Objects are also known as `container types`. This means they can contain different types of data like `variables` and `methods`. There are two different types of objects in Verse.

> We've already been using objects! The `array{}` object is a good example.

### Struct

A `struct`, short for `structure`, is a data type that is used to hold different types of data. Similar to a `map` but can hold different data types as well! These are special types of "variables" called `members`. "Variables" is wrapped in double quotes here because they cannot be referenced on their own, rather in the context of the object.

```ruby
# Define our custom struct
game_state := struct:
    NumberOfPlayers : int # It is not required to give a member an initial value
    GameStartDelay : float = 3.0 # but we can give it a value, if so desired.
```

The syntax of creating a `struct` is `name_of_struct := struct:`. Although not required, objects typically follow a naming convention known as snake case. We also notice that defining the data `members` of the struct is very similar to defining any other variable. Although, `members` of a `struct` cannot be mutable via the `var` keyword.

```ruby
game_state := struct:
    NumberOfPlayers : int
    var GameStartDelay : float = 3.0
```

> If we attempt this, UEFN will give us the error: Structs may not contain mutable members.

Structs can also have methods defined on them.

```ruby
game_state := struct:
    NumberOfPlayers : int
    var GameStartDelay : float = 3.0

(GameState : game_state).GetStartDelay() : float =
    GameState.GameStartDelay
```

We define the method *outside* the struct's definition as they cannot define methods within their definitions. The syntax to define a method on a struct is `(StructNameToUseInDefinition : name_of_struct).NameOfMethod(CanTakeArgumentsOrNot : type) : return_type =`

In the above example, we call the struct by the name of `GameState` which is used to return the `GameStartDelay` value of the struct. We have to define a new name for the struct followed by the struct's type to be able to interact with any of the struct's data members.

### Class

The main, and most powerful, container type in Verse is a `class`. Classes in programming are special because, like a `struct`, it can have data member variables as well as methods.

```ruby
player_data := class:
    MaybePlayerReference : ?player = false # Can set initial values for data members.
    NumberOfCoins : int # Not required to set an intial value.
    var IsDead : logic = false # Able to use mutable (changeable) values inside of a class.

    # We define methods directly in the class' definition!
    IsPlayerDead() : logic =
        if (IsDead?) . true ; false
```

Like a struct, the syntax to make a new class is `name_of_class := class:`. Two other major differences with classes vs structs:

* Variables can be mutable within the class' definition.
* Methods can be defined directly within the class.

To use a class (or struct), we need to make an instance of it. An instance is the concrete value of a class whereas the definitions we've seen so far are like the blueprints for an instance.

```ruby
PlayerData : player_data = player_data{}
```

When we create a new variable using our class (or struct) definition, we use the same syntax as we would when defining any other variable. The only difference is that the variable type is the object's name and the value is the object's name followed by curly braces `{}`.

This is a very important concept called `initialization` or `construction`, which means the creation, and optionally set up, of a new object.

> Again, just like the `array{}` object we've been using.

We can directly assign the data members of an object within the variable definition, if we want.

```ruby
PlayerData : player_data = player_data{ NumberOfCoins := 10 }
```

Note that we didn't assign values for `MaybePlayerReference` or `IsDead`. This is because in the definition (or blueprint) of the class, it is already set to a default value. You can either keep the default values or give them a new value for a given instance.

```ruby
DeadPlayerData : player_data = player_data{ NumberOfCoins := 0, IsDead := true }
```

> If you construct a new object and don't set a value for a member without a default value, UEFN will give you this error: Object archetype must initialize data member `NameOfDataMember`.

### Construction

Construction of a class is typically a separate method outside of a given class that will create a new instance of that class. This is useful if you want to keep your data members `internal` to that class. Constructor methods use an attribute called `<constructor>` which is specifically to denote that we're going to be creating an instance of a class.

> Attributes and visibility are talked about in [Visibility](#visibility) below.

```ruby
MakePlayerHelper<public><constructor>() : player_helper =
    PlayerCount := 10


player_helper<public> := class:
    PlayerCount<internal> : int
    GetPlayerCount<public>() : int
```

Classes are the only object types that can use `<constructor>` methods. Structs are not allowed to be constructed in this way.

### Inheritance

Remember when I said that classes were special when compared to structs? `Inheritance` is the secret sauce that classes and have structs do not. If you've ever created a new device using Verse, you've already used inheritance.

```ruby
# We're going to talk about modules very soon!
using { /Fortnite.com/Devices } # Importing an external module

my_device := class(creative_device):
    # ...definition of class...
```

Inheritance is a way to tell the program, "Okay, I'm not exatly this other class but I want to act like one". This means that you get **all** of the functionality, methods, dat members, etc., of another class to use in your own! This makes making complex objects much easier if most of what they do resides in another class' definition.

The syntax breakdown of inheriting from another class is `my_class := class(class_to_inherit):`.

If you inherit from another class, you may think to yourself, "But what can the other class do that I can use?". Hopefully you'll understand why you need to inherit from a specific class, but if not, you can easily find out what each class does with some explanations for each method / data member, if any. There are two primary ways to find this information:

1. Use the [UEFN API Reference]({{ book.external.links.uefn_verse.api_reference }}) website.
    * This website has pretty good explanations of each class. (Sometimes lacking a little bit 🙏)
2. Every UEFN project comes with the code definitions for everything you can use inside UEFN. These files all end in `.digest.verse`.
    * `Fortnite.digest.verse` -> This defines all of the Fortnite specific items like UI buttons, Devices, etc.
    * `Verse.digest.verse` -> This defines specifics of the Verse language.
    * `UnrealEngine.digest.verse` -> This defines things like building UI in code for a players, mathematical functions, etc.

It is **very** much worth your time to read through these files. Not only will you learn more about what's available to use, but more of the advanced language syntax available to all Verse programs.

A great example of a custom `creative_device` class is our [Custom NPC Dialog Example]({{ book.examples.path }}/custom_npc_dialog/README.md).

## Modules

A module is neither a `variable`, `data type`, `class`, `struct` or anything else we talked about so far. Modules are very special in programming. It's a way to group similar functionality into a named group. Sounds similar to a method but modules cannot be invoked (called, activated). Instead, you put the **definitions** of structs, classes and methods into these modules, but not their definitions.

```ruby
Helpers := module:
    player_helper := class:
    ui_helper := class:
    # ...other methods, classes and structs here...
```

To use a module, we need to use a new keyword called `using`; this brings everything the module has to offer into the current scope of your file.

Take a look at the `.digest.verse` files that I mentioned earlier and you can see lots and lots of examples of modules and how they are structured. You'll also see that you can use additional `using` statements in the body of a module as well!

### Submodules

Submodules are folders (or directories) that you add to your Verse files. The name of that folder is actually a module! All of the files defined in that folder, which contain classes, methods, etc., can be brought into another file in another submodule.

![Adding a Submodule]({{ book.partials.images_path }}/creating_device_instructions/new_verse_file.png)

> You can create a submodule by right clicking on the `Content` folder in the Verse explorer.

```ruby
# Helpers/player_helper.verse

player_helper := class:
    # ...definition of the helper class...


# Helpers/players.verse
using { Helpers.PlayerHelper }

players := class:
    # Everything in the `player_helper.verse` file is available here!
```

Structuring your code this way encourages developers to create code that is reusable, which can be re-used as often as needed!

## Visibility

Now is a good a time as ever to talk about visibility. Visibility is directly tied to a concept called `attributes`. Attributes go along with another concept called `specifiers`. I **highly recommend** you read over Epic's [Specifiers and Attributes](https://dev.epicgames.com/documentation/en-us/uefn/specifiers-and-attributes-in-verse) documentation page to understand more about them. We will go over the most commonly used attributes.

Attributes are put onto variables, methods, classes and structs. By default, all visibility attributes are `internal`.

```ruby
DoSomething<private>() : void
AmountOfCoins<internal> : int
player_helper<public> := class:
```

The syntax breakdown is `item<attribute>`. Let's go over each one and what they mean.

### Private

Private means that only the code in which this item is encapsulated in can interact with this item. If you import another module and it has `private`, classes, structs, data members or methods, you will not be able to access them.

```ruby
# Helpers/player_helper.verse
player_helper<private> := class:
    GetPlayerCount() : int


# Helpers/ui_helper.verse
using { PlayerHelper } # The module will still be found

ui_helper := class:
    SomeVariable : int = player_helper{}.GetPlayerCount() # This will cause an error because the `player_helper` class is set to private!
```

### Internal

Internal is the default visibility attribute and this means that it can only be used inside the file that it was created in. It is a lot like the private visibility but it can be used throught the file and not just the encapsulating object.

```ruby
MakePlayerHelper<constructor>() : player_helper =
    PlayerCount := 10 # We can set this because we are in the same file as the player_helper definition.

player_helper<public> := class:
    PlayerCount<internal> : int
```

### Public

Public is the easies attribute to understand. If something is marked as public, we can use it anywhere!

```ruby
# Helpers/player_helper.verse

player_helper<public> := class:
    GetPlayerCount<public>()


# Helpers/ui_helper.verse
using { PlayerHelper }

ui_helper := class:
    PlayerHelper : player_helper = player_helper{}
    GetTotalPlayers() : int = PlayerHelper.GetPlayerCount() # We can use this since it's a public method in a public class!
```

> If the `GetPlayerCount` method was not public, we could access the `player_helper` class but not the `GetPlayerCount` method.

## Conclusion

Although we are at the end of this document, that does not mean the Verse learning stops here! Check out the links to the [Official Verse documentation]({{ book.external.links.uefn_verse.learn }}) as well as the [Verse Language Reference]({{ book.external.links.uefn_verse.language_reference }}). These are going to be your best friends on your journey to better learn Verse.

If you're looking for more to learn, check out our [Examples]({{ book.examples.path }})!
