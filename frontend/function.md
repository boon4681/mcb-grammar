# Functions

Functions in MCB declared with `fun` keyword, and Minecraft commands can only be used inside functions. Any codes that is used outside function will run with top piority by `minecraft:tags\functions\load.json`

on compile time file name is folder and function_name is file_name

**Basic Function:**

```kt
// normal function without parameters and output
fun function_name(){
    ...codes...
}

// function with parameters
fun function_name(param_1:type,param_2:type,...){
    ...code...
}

// function with parameters and output
fun function_name(param_1:type,param_2:type,...) -> return_type{
    ...code...
    return value
}
```

Examples:

```kt
// src/hello.ts
fun hi(){
    say hi
}

fun is_odd(num:int){
    if(num % 2 == 1){ // read about if in flow controls
        say odd
    }
    say even
}

hi() // call function

is_odd(1) // function with parameter
```

Compiled directory:

```log
build_folder
├ data
|  ├ minecraft
|  |  └ tags
|  |     └ functions
|  |        └ load.json
|  └ example
|     └ functions
|        ├ hello
|        |   ├ ifs
|        |   |  └ mcb.hello.is_odd.ifs.0.mcfunction
|        |   ├ hi.mcfunction
|        |   └ is_odd.mcfunction
|        └ load.mcfunction
└ pack.mcmeta
```

**Function Modifiers:**

Modifiers are prefixed keywords that modify function, attaching metadata to function that compiler can be used to compiled code by modifier property.

- `load` make your function run after datapack was loaded, triggered by `minecraft:tags\functions\load.json`

    ```kt
    load fun hello(){
        say hello
    }
    ```

- `tick` make your function run every-tick by `minecraft:tags\functions\tick.json`

    ```kt
    tick fun hi(){
        say hi
    }
    ```

Also you can combined modifiers by place whitespace between.

```kt
tick load fun hello(){
    say hello
}
```
