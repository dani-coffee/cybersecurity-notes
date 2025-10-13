##commands

•ls - lists all items in the current directory 
    examples:
        ls
        ls ~/Documents (if there's Documents folder in desktop)

•cd - change directory (I have to insert a path(folders!!!))
    examples:
        cd Desktop (if I'm at my home directory and i do ls, i see Documents,I can do cd Desktop to got to this directory)
        cd ..    --> I go back 1 step in my currrent path
        cd ~    --> I go back to the home directory no matter where I currently am
        cd ~/Desktop    --> if I wanna go back to Desktop directory

•echo - prints an output to the terminal
    examples:
        echo Hello world!    -->prints Hello world!
        echo file1.txt
        echo hi! > file1.txt    --> using > means the output will be in the file1.txt,if it exists,the old contents will be erased and replaced by hi!,if it doesn't             exist,a new file will be created with this output

•nano - edit file in terminal (easiest way for now click ctrl+O to save,enter,then ctrl+X to exit)
    examples:
        nano file1.txt
       
•pwd - shows current path

•find - instead of continuously using ls and cd, I use this command to find what j need jnside a folder 
    examples:
        find ~/Documents -name "file1.txt"
        find . -name "file2.txt"    -->using '.' means searching in the current folder

•grep - instead of using cat which prints all of the contents ina file for example,or all the contents of a folder ,I use this command to print the specific contents I need
    examples: 
        grep "passwords" file1.txt
        grep -i "word" file1.txt    -->this one means case insensitive search and will search for WoRd ,WORD etc...
        grep -c "word" file1.txt     --->counts how many lines contain the word "word"

 







##keyboard useful combinations
ctrl+l`-->clears terminal
