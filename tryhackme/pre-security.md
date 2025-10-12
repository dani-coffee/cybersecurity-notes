##commands##
•ls-lists all items in the current folder 
ex: ls
ls ~/Documents (if there's Documents folder in desktop)

•pwd-shows current path

•find-instead of continuously using ls and cd, I use this command to find what j need jnside a folder 
ex: find ~/Documents -name "file1.txt"
    find . -name "file2.txt"
    -->using . means searching in the current folder

•grep-instead of using cat which prints all of the contents ina file for example,or all the contents of a folder ,I use this command to print the specific contents I need
ex: grep "passwords" file1.txt
#variations
1.grep -i "word" file1.txt 
-->this one means case insensitive search and will search for WoRd ,WORD etc...
2.grep -c "word" file1.txt 
--->counts how many lines contain the word "word"
