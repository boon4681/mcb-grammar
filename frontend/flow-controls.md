# Flow controls

The ability to run some code depending on if conditions is true

## Conditions

**Expression:**

- Conjunction: &&
- Disconjunction: ||

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
fun is_odd(num:int){
    return if(num %2 == 1){
        -> true
    }else{
        -> false
    }
}

fun is_even(num:int){
    return if(num % 2 == 0) -> true else -> false
}
```
