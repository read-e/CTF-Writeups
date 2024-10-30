# Specializer

Liam Reidy

**Instructions:** Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer. Additional details will be available after launching your challenge instance.

We start this challenge by sshing into the computer using the given credentials. We immediately find that commands like `ls` and `cat` do not work, but `pwd` does.

By pressing tab twice to 'autocomplete' a command, we get a list of available commands:
```
Specialer$ 
!          bg         compgen    do         exec       function   kill       pwd        shopt      true       wait
./         bind       complete   done       exit       getopts    let        read       source     type       while
:          break      compopt    echo       export     hash       local      readarray  suspend    typeset    {
[          builtin    continue   elif       false      help       logout     readonly   test       ulimit     }
[[         caller     coproc     else       fc         history    mapfile    return     then       umask      
]]         case       declare    enable     fg         if         popd       select     time       unalias    
alias      cd         dirs       esac       fi         in         printf     set        times      unset      
bash       command    disown     eval       for        jobs       pushd      shift      trap       until    
```

Well, `echo` can be used to display the contents of a file, but what files do we have to choose from?

Using `cd` and pressing tab autocompletes what files we have to choose from:
```Specialer$ cd 
.hushlogin  .profile    abra/       ala/        sim/
```

So three directories. I `cd`ed into each, each having 2 text files in it. In the `ala/` directory, there is a text file named `kazam.txt`. Using a command to echo the contents, we get the flag:
```bash
Specialer$ echo "$(<kazam.txt)"
```
