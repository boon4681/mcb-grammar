# Comment

Leave a comment in your source code that the compiler will ignore but people reading your source code may find useful.

## Single line comment

Start the comment with two slashes, and the comment
continues until the end of the line

```ts
// this is a comment

// the idiomatic comment style
// hello
// this
// is
// a multilines comment
```

## Multilines comment

It have a little changed from **`Single line comment`**, You
Start the comment with `/*`, and comment continues until you end it with `*/`

```ts
/*

this
is
a
multilines
comment

*/
```

## Comment to datapack

If you want to leave a comment in compiled datapack you can do this.

```ts
belong
{
    // hello this comment belong to compiled datapack
}
```
