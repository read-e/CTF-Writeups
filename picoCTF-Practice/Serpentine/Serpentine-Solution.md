# Serpentine
Liam Reidy

**Instructions:** Find the flag in the Python script!

Serpentine is an interactive python program that has an option to "print the flag". Selecting that option does not actually print the flag, it prints a message telling the user to take a look at the source code.

```
    Y
  .-^-.
 /     \      .- ~ ~ -.
()     ()    /   _ _   `.                     _ _ _
 \_   _/    /  /     \   \                . ~  _ _  ~ .
   | |     /  /       \   \             .' .~       ~-. `.
   | |    /  /         )   )           /  /             `.`.
   \ \_ _/  /         /   /           /  /                `'
    \_ _ _.'         /   /           (  (
                    /   /             \  \
                   /   /               \  \
                  /   /                 )  )
                 (   (                 /  /
                  `.  `.             .'  /
                    `.   ~ - - - - ~   .'
                       ~ . _ _ _ _ . ~

Welcome to the serpentine encourager!


a) Print encouragement
b) Print flag
c) Quit
```

Viewing the source code reveals that there is a print_flag function which has been replaced in the if statement on the user's input:
```python
elif choice == 'b':
      print('\nOops! I must have misplaced the print_flag function! Check my source code!\n\n')
```

Replacing the print statement with the print_flag function prints the flag. Frnakly, there are infinite ways to solve this challenge because the print_flag method works. The flag is stored in the script as a hex that is ored with a word also in the script. The hex could have even been decoded, but it probably would have taken longer.

```python
elif choice == 'b':
      print_flag()
```