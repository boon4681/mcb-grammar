# Functions

Functions in MCB declared with `fun` keyword, and Minecraft commands can only be used inside functions. Any codes that is used outside function will run with top piority by `minecraft:tags\functions\load.json`

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
fun hi(){
    say hi
}

fun isOdd(num:int){
    if(num % 2 == 1){ // read about if in flow controls
        say odd
    }
    say even
}

hi() // call function

isOdd(1) // function with parameter
```
