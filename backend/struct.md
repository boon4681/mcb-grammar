# Structure

## MCB types Wrapper

Wrapper is dominant class of type-object's

```ts
class Wrapper<T> {
    constructors(
        public name: string,
        public property: T
    )

    set(): string
    get(): string
            .
            .
            .
    some_function()...
}
```

## MCB types

MCB structure type-object's

```ts
class Type <T,Wrapper> {
    public value:T
    constructors(
        public name: string,
        public default_value:T,
        public default_target: string,
    ){
        this.value = default_value;
    }

    set(wrapper?: Wrapper,target?:string): string
    get(wrapper?: Wrapper): string
            .
            .
            .
    some_function()...
}
```

## MCB memory system

MCB memory system is purpose for variables transfer

```log
MEMORY REGISTER
--------------------------
| [                      |
|   id:0, name: "varia.. |
|   id:1, name: "varia.. |
|   id:2, name: "varia.. |
|       .                |
|       .                |
|       .                |
|   id: n, name: "...... |
| ]                      |
--------------------------
    ^
    |
    |____   {
                id: 0,
                name: "variable_name",
                type: <_class;int>,
                wrapper: <_object;scoreboard>,
                target: "@s",
                location: <_object;this.function>,
                borrow: false,
                default: value,       <------
            }                               |
                                            |
                                            |
    let variable_name:int<parent> as @s = value
```

MEMORY REGISTER

```log
[OBJECT STRUCTURE]
let hi:int<foo> as @s = 5;
{
    id: 0, // memory id
    name: "hi", // memory name
    type: "<_class;int>", // memory type
    wrapper: "<_object;scoreboard>", // memory wrapper
    target: "@s", // memory target
    location: "<_object;function>", // memory location
    borrow: false, // a compile option
}
```

References:

- type
- wrapper
- location
