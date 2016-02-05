# <a href="http://meta.codegolf.stackexchange.com/a/7632/46231">N-Player Battleship</a>
#### <a href="http://meta.codegolf.stackexchange.com/a/7632/46231">king-of-the-hill</a>
---
## The Rules
* The field is a 5N by 5N grid, where N is the number of playing bots.
* The controller places each player's ships randomly.
* Each player can see their own ships and all the shots they have made, successful or otherwise.
* Each player can also see other players' successful shots.
* Each player gets one shot per turn.
* Each player's fleet consists of, for a total of 21 squares altogether
 * 1 aircraft carrier - 5 squares
 * 1 battleship - 4 squares
 * 2 destroyers - 3 squares
 * 3 assault boats - 2 squares
* You are allowed to keep state information between turns, but not between rounds/games.

## The Specs
### Input

* Input will consist of one positive integer followed by a string of characters, like so: `3 "S X . S O M S . H"`.

* You can assume the input will be correctly formed, and that the leading integer will always correctly divulge the side-length.

* The key of symbols is as follows:

```
3
S X .
S O M
S . H

Key:
3 This board has a side-length of 3. This board can support 0.6 players.
. Unknown (i.e., it's empty or no one has attacked there yet)
O A piece of your ship that has not been hit.
X A piece of your ship that has been hit.
M One of your missed attacks.
H A hit from another player.
S Any part of a ship that has been sunk, yours or an enemy's.
```

* Input may be taken through `stdin` or in the form of command line arguments.

* You may write and supply a helper script which parses and reformats the input in any way convenient for your language.

### Output
* Output must be a pair of positive integers in the format `x y`.

* Output may be written to `stdout` or `stderr`, or it may be written to a regular file, as long as the regular file's name is deterministic and known, or you provide a helper script which `cat`s the file to `stdout` at the end of your bot's turn.

* You must not write any other data to the same stream as your program's result. That is, if you write your answer to `stderr`, you may write junk to `stdout` and regular files but not `stderr`.

* If you write to a non-`stdout` stream, you should provide a helper script which redirects the content of that stream to its `stdout` such that the controller can read it.

### Other semantics

* The top-leftmost index of the grid (the first element of the board string) has an index like `0, 0`.

* On a board with side-length `x`, position `x, x` will always refer to the bottom-leftmost index on the board.

* The controller purges the working directory of alien or new files. Any data written to regular files will be lost after the controller has finished processing that cycle.

* Helper scripts should work in at least a POSIX shell or Windows Batch.