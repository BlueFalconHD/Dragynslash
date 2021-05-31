# Dragynslash
### A program based on Asciidots.

## Rules

#### Speed:

1 tile per 10ms
Runs operations, commands, prints, simulated value, etc, but skips the content. All outer parts of commands/statements are counted as tiles.
Ex:
`:---(+ .10.)----` Takes 90ms.

---

## Statements
#### *Reverse order if Dragyn is moving left*

Commands
`/ command here \`
`/ > .10.\` (If statement)

Operations
`(dragyn-in <operation> value)`
`(+ .10.)` Adds 10 to dragyn that passes over operation.

Simulated Values
`.value.`
`.10.`
`."Hello World".`

Prints
`[thing to print]`
`[-]` Prints dragyn that passes over print's value
`[."I'm a dragyn!".]` Prints "I'm a dragyn!" when dragyn passes over print.
`[.69.]` Prints '69' to the console when dragyn passes over print.

Sets
`{value}`
`{.1000.}` Sets dragyn's value who passes over set to 1000.

Unicode Decode
`!unicode number!`
`!.69.!` Interprets 'E'

Unicode Encode
`% ascii character %`
`%."E".%` Encodes 'E' to 69

Add 1
`.`

---

#### Query statements wait for the user to press enter until continuing the program.

Query Input
`? query message ?`                                  
`?."What is your name".?` Returns what user inputted.
                                                    
Query number-only input                                
`$ query message $`                                   
`$."How old are you?".$` Returns what user inputted.

---

Comment
`# comment #`
`# This is the main segment #`

Dragyn's Value
`&val&` Returns dragon's value


## Command Types (see commands)

If
`/ incoming dragyn's value <operation> compare value\`
Sets incoming dragyn's value to 0 if comparation is false and 1 if comparation is true.

EX:
`:-{.1000.}--/>.10.---[-]`
Would return 1.

Then
`/|\`
If value of dragyn is equal to 1, follows the pipe down. If value of dragyn is 0, continues. The pipe in the slashes is skipped and if Dragyn's value = 1, it will move to the tile directly below the pipe.

## Movement

Horizontal Path
`-` Moves Dragyn along path

Spawn Dragyn
`:` Spawns a Dragyn moving horizontally.

Pipe/Down
`|` Moves Dragyn along downwards at normal speed. 

Direction Change
`>` Turns Dragyn right.
`<` Turns Dragyn left.
`^` Turns Dragyn up.
`v` Turns Dragyn down. Not needed at then Command Type
`+` Crossing. Paths don't interact.

## Examples

### Favorite Number

```
# Spawn Dragyn #

         :---------$."What is your favorite number?".$---v
             # For this example, user inputted 10 #      |
                                                         |
[."? How is that your favorite number?".]-[-]-/|\---/<10\<
                                               >-[-]-[."! That's my favorite number!".]-
```
```
Terminal:
10? How is that your favorite number?
```

Other outcome:

```
# Spawn Dragyn #

         :---------$."What is your favorite number?".$---v
             # For this example, user inputted 20 #      |
                                                         |
[."? How is that your favorite number?".]-[-]-/|\---/<10\<
                                               >-[-]-[."! That's my favorite number!".]-
```
```
Terminal:
20! That's my favorite number!
```


### Truth Machine

```
            :---$."Input either 0 or 1 - Truth Machine".$---/|\--------------[.0.]-
                                                             |
                                                        v----<---------<
                                                        |              |
                                                        >------[.1.]---^

            # It is best to indent the first parts of each line to add #
            # extra space and room for more lines.                     # 
```
```
Terminal:  INPUT WAS 1
11111111111111111111111111111111111111111111111111111111111111111111111111111111111
(Infinite ones)
```
```
Terminal: INPUT WAS 0
0
```
