# Flow controls

The ability to run some code depending on if conditions is true

## Conditions

**Expression:**

- Conjunction: &&
- Disconjunction: ||
- Not: !

**Types of condition:**

- entity: `entity @e[tag=hi]`
- block
- blocks
- data
  - block
  - entity
  - storage
- predicate
- score

**Scoreboard operation support:**

- == Equal
- \> Greater than
- < Less than
- <= Greater than, equal
- \>= Less than, eqaul

**Array and Map operation support:**

- == Equal

## if Expressions

In MCB `if` is an expression allows you to run your branch of code on conditions, it returns a value.

**Basic if-else expression:**

```kt
if(num % 2 == 1){
    say odd
}else{
    say even
}
```

**returned value if-expression:**

```kt
fun is_odd(num:int){
    return if(num %2 == 1){
        say 'is ood'
        -> true
    }else{
        say 'is even'
        -> false
    }
}

fun is_even(num:int){
    return if(num % 2 == 0) -> true else -> false
}
```

## for loops

The `for` loop in MCB came up with many difference way to using it.

Now MCB have two types of `for`

### **`for....in`**

This type of `for` is looping anything in MCB that provides an iterator.

**Iterator in MCB:**

- array
- range

**Syntax:**

```kt
for(i in 1..10){
    // ...
}
```

**Basic of for....in :**

```kt
for(i in 1..10){
    say hi
}
```

### **`for`**

This type of `for` is looping until a condition expression is false.

**Syntax:**

```kt
for(initial; condition; step){
    //....
}
```

**Basic of for:**

```ts
let foo:score<dummy>
for(int<foo> i=0; i<10; i++){
    // ....
}
```

## while and do....while loops

`while` and `do....while` loops is looping their block until a condition expression is false and beware of endless loop if your condition is not going false that mean you will traped in an endless loop

### while

```kt
while(conditions){
    // ...
}

while(i<10){
    // ....
    i++
}
```

### do....while

```kt
do{
    // ....
}while(conditions)

do{
    // ....
    i--
}while(i>10)
```
