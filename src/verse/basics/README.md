# Preface

The information contained here is best learned by typing it in (not copying!) while you read. Create a new verse script in UEFN and follow along!

> Use this information in additon to the [Official Verse documentation]({{ book.external.links.uefn_verse.learn }}) along with the [Verse Language Reference]({{ book.external.links.uefn_verse.language_reference }}).

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

## Logic

Logic is important in any program. It is used to determine if something can or can't happen. We'll go over what logic is and how to use it.

The way we use logic in Verse is by using an `if` statement. Like mentioned, `if` is used to determine `if` something can or can't happen.

```ruby
IsOnFire : logic = true

if (IsOnFire?):
    ScreamInPanic()
```

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

### Logic Context

Vere supplies us with an idea called a `context`. A `context` is a specific place in our code where special, extraordinary things can happen. It sounds strange at first, and to be honest, it kind of is, but `context`s are super powerful. The `if` statement provides us with a fallible `context`. This means the conditions we check for in an `if` statement can fail!

```ruby
IsOnFire : logic = false

if (IsOnFire?):
    ...do something if on fire...
```

Since `IsOnFire` is given the value of `false`, we can see that this `if` statement has "failed" to satisfy the condition, thus we will not do anything since we are not on fire.

### If Variables

We can also assign a variable inside the condition of an `if` statement. This is useful when you have a method that can either succeed or fail, and if it succeeds, then you can retrieve that variable.

```ruby
if (Coins := GetPlayerCoins[]):
    ...do something with Coins variable...
```

Wait a minute! We saw how to create a variable and that's not how we did it before! This is a special case where you do not have to define the data type of the variable explicitly. UEFN knows what type of data the `GetPlayerCoins` method gives us, which is super handy! We can also notice that we call the method with square brackets (`[]`) instead of parenthesis (`()`) here. If a method has a chance to fail, we have to use square brackets!

> I know I promised we would talk about methods soon... and we will! Stay tuned!

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

### Iteration

Iteration may be a scary sounding word; I know it was for me when I was a new programmer. It is a term in programming that means "go over each item, one at a time". We can use iterators to process or manipulate each piece of data, one item at a time. To do this, we will introduce the `for` keyword:

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

    <span>I have 5 lives left!</span><br/>
    <span>I have 4 lives left!</span><br/>
    <span>I have 3 lives left!</span><br/>
    <span>I have 2 lives left!</span><br/>
    <span>I have 1 lives left!</span><br/>
    <span>I'm dead!</span><br/>
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

I'm not going to give you the solution to this one. Let me know in the [Official Discord]({{ book.external.links.fornite_creative_discord }}) (`@glinesbdev`) server what your solution was.
