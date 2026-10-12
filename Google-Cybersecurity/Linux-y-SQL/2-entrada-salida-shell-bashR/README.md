# Linux: Input and Output in the Bash Shell

Activity on how the Bash shell receives input and transforms it into output using the `echo` and `expr` commands.

## Description

Using the Bash shell to communicate with the operating system. The `echo` command was used to generate specific text output, and the `expr` command was used to perform basic mathematical calculations. The `clear` command was used to clean the shell window.

## Scenario

As a security professional, it is important to understand how to communicate with a computer through the shell. In this lab, I entered specific text strings for the shell to output, and performed basic math calculations for the operating system to generate results.

## Tasks performed

1. **Generate output with `echo`**: ran `echo hello` and `echo "hello"` to output a text string. Quotes are optional but tell the shell to group a series of characters together.
2. **Generate output with `expr`**: used `expr` to perform basic calculations.
   - `expr 32 - 8` returned `24` (false positives out of 32 alerts).
   - `expr 3500 * 12` returned `42000` (expected login attempts in a year).
3. **Clear the Bash shell**: ran `clear` to erase all previous commands and output, returning the cursor to the top-left corner of the shell window.
4. **Optional extra calculations**: practiced more `echo` outputs and `expr` calculations using the operators `+`, `-`, `/`, and `*`.

## Key commands

```bash
echo hello
echo "hello"
echo "name"
expr 32 - 8
expr 3500 * 12
clear
