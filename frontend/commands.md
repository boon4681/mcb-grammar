# Commands

## Minecraft commands

Just a vanilla minecraft command that you see in the game. MCB compiler will throw an error if the command is in an incorrect-format.

## Unsafe commands

Unsafe command is a command that came up with plugins or mods.
MCB compiler cannot handle those command so you need to use unsafe block to use it.

Also you cannot use multilines command in unsafe block too.

```ts
unsafe {
    // ...unsafe command...
}
```
