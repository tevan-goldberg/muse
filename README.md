# Muse
### a simple language for jamming!

[The Muse Editor](https://hackclub.github.io/muse/)

Muse is a simple language embedded in a JavaScript environment.

To create a song create a muse and pass in your code.

```
createMuse().play("a4+ ;- [ c5 ; e5 ] x 4")

```

The language has notes: a | a# | b | c | c# | d | d# | e | f | f# | g | g#  
with an optional number 1 - 10 for pitch.

```
a4
```

You can lengthen notes with a "+" after:

```
a4+
a4++
a4+++
```

or shorten them with a "-" after:

```
a4-
a4--
a4---
```

each "+" or "-" correpsonds to a power of 2

A pause is ";" which can also be lengthened or shortened

so an arpeggio is 

```
a4 ; c5 ; e5
```

and a chord is

```
a4 c5 e5

```

A group is denoted with brackets "[ ]"

```
[ a4 c5 e5 ]++

```

To repeat something use "x" and some number

```
[ a4 c5 e5 ; ] x 4

```

createMuse also takes some optional arguments for beats per minute and wave type

```
createMuse({ bpm: 10, type: "sine" }) // type can be sine | sawtooth | triangle | square

```

You can also use samples that are listed on the right.

```
createMuse().play(`bubbles ; bubbles -`)

```

To play multiple tracks at once pass multiple strings into the play method.

```
createMuse().play(`a4 ; e4 ; d5 ;`, `; c5 ; e4 ; d5 ;`)

```

You can also bind functions to keys with the bindKey function. The key will correspond to the keydown event key and the value to the callback function.

Here is an example keyboard with the bindKey function:

```
const key = 4
const type = "triangle" // sine | triangle | square | sawtooth

const a = () => createMuse({ type }).play(`a${key}`)
const s = () => createMuse({ type }).play(`b${key}`)
const d = () => createMuse({ type }).play(`c${key+1}`)
const f = () => createMuse({ type }).play(`d${key+1}`)
const g = () => createMuse({ type }).play(`e${key+1}`)
const h = () => createMuse({ type }).play(`f#${key+1}`)
const j = () => createMuse({ type }).play(`g${key+1}`)
const k = () => createMuse({ type }).play(`a${key+1}`)
const l = () => createMuse({ type }).play(`b${key+1}`)

// these keys get bound
bindKeys({ 
  a, 
  s, 
  d, 
  f, 
  g, 
  h, 
  j, 
  k, 
  l 
})

```

The console on the right of the editor just logs whatever was played.




