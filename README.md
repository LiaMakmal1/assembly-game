# Assembly maze game

A Pac-Man-style maze game written in x86 assembly (TASM, IDEAL mode) for DOS, built in high school. Collect every dot on the board while staying away from the ghosts: each dot is worth one point, and eating all of them wins the game.

## How it works

- **Graphics:** VGA mode 13h (320×200, 256 colors). The board, player and ghosts are drawn pixel by pixel through BIOS video interrupts (`int 10h`), with sprites stored as coordinate tables.
- **Collision detection:** before each move the game reads the color of the target pixels (`int 10h`, read-pixel), so walls, dots and ghosts are told apart by color.
- **Game flow:** start screen with instructions, live score, a win screen when all dots are eaten, and a game-over screen with the final score and a play-again prompt.
- No external libraries: everything is done with DOS and BIOS interrupts.

## How to run

You need [DOSBox](https://www.dosbox.com/) and Turbo Assembler (TASM). Inside DOSBox, from the folder with `base.asm`:

```
tasm base.asm
tlink base.obj
base.exe
```
