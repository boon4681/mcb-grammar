# Variables

MCB is a statically typed language. This means that variables do have types in declaration.

- Scoreboard
- Integer
- Float (upcoming) [on research]
- Array (find function is upcoming) [on research]
- Map

## Scoreboard

**Basic Declaration:**

```ts
// Format
let objective:score<minecraft:criteria>
//    ^--- variable_namve

// Example
let foo:score<dummy>
```

Compiled code:

```mcfunction
scoreboard objective add foo dummy
```

**Declared with DisplayName:**

```ts
// Format
let objective:score<minecraft:criteria> as DisplayName

// Example
let bar:score<dummy> as Boon
```

## Integer

**Basic Declaration (Selector):**

```ts
// Format
let variable_name:int<objective> = value

// Example
let foo:score<dummy> // Declare scoreboard
let zero:int<foo> = 0 // Declare integer value 0
let just_a_number:int<foo> = 20 // Declare integer value 20
let as_bar:int<foo> as bar = -10 // Declare integer value -10 as bar
```

Compiled code:

```mcfunction
scoreboard objective add foo dummy
scoreboard players set zero foo 0
scoreboard players set just_a_number foo 20
scoreboard players set bar foo 20
```

**Declared as Entity Selector:**

```ts
// Format
let variable_name:int<objective> as Selector
let variable_name:int<objective> as Selector = value

// Example
let foo:score<dummy> // Declare scoreboard
let zero:int<foo> as @p = 0 // Declare integer value 0
let just_a_number:int<foo> as @p = 20 // Declare integer value 20 as @p
```

Compiled code:

```mcfunction
scoreboard objective add foo dummy
scoreboard players set @p foo 0
scoreboard players set @p foo 20
```

**Assign variable to Selector:**

```ts
// Format
objective<Selector> = variable

// Example
let foo:score<dummy> // Declare scoreboard
let bar:int<foo> = 0 // Declare integer value 0
foo<@p> = bar
```

Compiled code:

```mcfunction
scoreboard objective add foo dummy
scoreboard players set bar foo 0
scoreboard players operations @p foo = bar foo
```

## Array

The represent of Array value in MCB is a sequence of variable in [], but in minecraft you can not access with the array directly so MCB have a Built-in function to do it for you.

Example : `["a","b","c","d","e"]`, `[1,2,3,4,5]`

**Basic Declaration:**

- Default Namespace is `mcb.gabages.arrays`
- Default TargetPath will be `random`

```ts
// Format
let variable_name:array = []

// Example
let bar:array
```

```ts
// Format
let variable_name:array<Namespace> as TargetPath = []

// Example
let bar:array<foo> as hello = []
let ree:array<woo> as me.hi = [1,2,3]
```

Compiled code:

```mcfunction
data modify storage foo hello set value []
data modify storage foo me.hi set value [1,2,3]
```

**Get and set value in variable:**

```ts
// Format
variable_name[index] // Get
variable_name[index] = value // Set

// Example
let foo:score<dummy> // Declare scoreboard
let bar:int<foo> = 0  // Declare integer value 0
let wow:int<foo> = 0  // Declare integer value 0
let list:array<hi> = [1,2,3]

wow = list[0] // Get list index 0 and Set it to wow variable
list[0] = 5 // Set index 0 in list to 5 [5,2,3]
```

Compiled code:

```mcfunction
scoreboard objective add foo dummy
scoreboard players set bar foo 0
scoreboard players set wow foo 0
data modify storage hi list set value [1,2,3]

execute store result score wow foo run data get storage hi list[0]
scoreboard players set 0 mcb.gabages 5
execute store result storage hi list[0] int 1 run scoreboard players get 0 mcb.gabages
```

**Built-in Functions:**

A built-in functions that make your life a lot easier than before, provided
`push`, `puff`, `pop`, `shift` and `find` function with function binding within

- **`push`** : Add one element to the end index of an array

    ```ts
    push(source:array, value:any) -> true | false
    ``` 

    ```ts
    let foo:array = [1,2,3,4,5]
    let bar:array = [1,2,3,4,5]
    // push
    push(foo,6) // foo: [1,2,3,4,5,6]

    // function binding
    bar --> push(6) // bar: [1,2,3,4,5,6]
    ```

- **`puff`** : Add one element to the start index of an array

    ```ts
    let foo:array = [1,2,3,4,5]
    let bar:array = [1,2,3,4,5]
    // puff
    puff(foo,0)// foo: [0,1,2,3,4,5]

    // function binding
    bar --> puff(1) // bar: [0,1,2,3,4,5]
    ```

- **`pop`** : Remove the last element from an array

    ```ts
    let foo:array = [1,2,3,4,5]
    // function binding
    foo --> pop // foo: [1,2,3,4]
    ```

- **`shift`** : Remove the first element from an array

    ```ts
    let foo:array = [1,2,3,4,5]
    // function binding
    foo --> shift // foo: [1,2,3,4]
    ```

- **`find`** : return the first element of an array that satisfies the testing function.

    `In testing-function you need to chooses the matches type of the input and array indexs, if not MCB will cast that value to the input type in testing function automatically. This will cause your testing-function to not working properly`

    ```ts
    let foo:array = [1,2,3,4,5]

    fun test(i: int){
        return i == 1
    }

    // find
    find(foo,test) // 1
    ```

## Map

The represent of storage in term of map/dict whatever you call.

**Basic Declaration:**

- Default Namespace is `mcb.gabages.maps`
- Default TargetPath is `random`

```ts
// Format
let variable_name:map = value

// Example
let foo:map = {}
```

```ts
// Format
let variable_name:map<Namespace> as TargetPath = value

// Example
let foo:map<bar> me = {}
```

**Built-in Function:**

- `del` : Delete (remove) data in dict

    ```ts
    let foo:map = {hello:"HI"}
    // del
    del(foo,"hello")

    // function binding
    foo --> del("hello")
    ```
