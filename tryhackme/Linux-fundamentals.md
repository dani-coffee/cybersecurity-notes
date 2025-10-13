# ⚙️ **Commands**
• **ls** -lists all items in the current directory (basic info: file and directory names)
##### ✏️examples:
        -ls
        -ls ~/Documents (if there's Documents folder in desktop)

• **ll** - it's just ls with the flag -l, meaning it lists all items in the current directory but in a long format(more details: file permissions,number of links,owner name, group name,file size,modification date/time,filename)        

• **cd** - change directory (I have to insert a path(folders!!!))
 ##### ✏️examples:
         -cd Desktop (if I'm at my home directory and i do ls, i see Documents,I can do cd Desktop to got to this directory)
         -cd ..    ➝ I go back 1 step in my currrent path
         -cd ~    ➝ I go back to the home directory no matter where I currently am
         -cd ~/Desktop    ➝ if I wanna go back to Desktop directory 

• **echo** - prints an output to the terminal (adds automatically a newline in the end of a line,unless i add the flag -n)
#####  ✏️examples:
        -echo Hello world!    ➝ prints Hello world!
        -echo file1.txt
        -echo hi! > file1.txt
        -echo hi! >> file1.txt 

• **cat** -prints the contents of the inserted file
#####   ✏️examples:
            -cat file1.txt
            -cat ~/Desktop/file1.txt    ➝ I don't have to use cd to enter to the directory containing the file I want to print,I can just insert the parh adter using                cat

• **nano** - edit file in terminal (easiest way for now click ctrl+O to save,enter,then ctrl+X to exit)
#####   ✏️examples:
        -nano file1.txt
       
• **pwd** - shows full path to the current directory

• **find** - instead of continuously using ls and cd, I use this command to find what I need in the current directory and its subdirectories
##### ✏️examples:
        -find -name "file2.txt"    ➝ finds path of file2.txt,from current directory
        🔸note: in fact it's equivalent to find . -name "file2.txt" , the dot means the current directory
        -find -name "file1*"    ➝ using a wildcard means that any suffix is acceptable-this matches any file that starts with 'file1'

• **grep** - instead of using cat which prints all of the contents in a file ,I use this command to print the specific data I need and i prints the relevant output lines
##### ✏️examples: 
        -grep "passwords" file1.txt
        -grep -i "word" file1.txt    ➝ this one means case insensitive search and will search for WoRd ,WORD etc...
        -grep -c "word" file1.txt     ➝ counts how many lines contain the word "word"
        -grep -E "^" file1.txt    ➝ equivalent to cat file1.txt,'^'means the start of every line,-E stands for extended regular expression which enables extended regex         syntax.(like OR operator,or grouping expressions)

 






# ⚙️ **Operators**
• **'&'** - allows to execute background operations while being able to do another operation
##### ✏️examples:
        echo "Start"
        sleep 5 &
        echo "I can type this immediately"


• **'&&'** - like in any other programming language ,it means logical and 
#####  ✏️examples:
    -echo Hi && echo There    ➝ prints  Hi
                                        There
                                        

• **'>'** - redirects output to the indicated file
        🔸note:if the indicated file doesn't exist, a new file with this name is created,otherwise the contents of the indicated fle are overwritten with the current             output.
#####  ✏️examples:
        -echo hi! > file1.txt


• **'>>'** - similar to '>' but this one appends,meaning even if the indicated file exists, it just adds the output to the file's original output 




# ⚙️ **Keyboard_useful_combinations**
• **ctrl+l**    ➝ clears terminal

•using ~ meaning I point to the home directory,so instead of writing home i can write ~
