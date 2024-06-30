Lesson link:

https://www.codecademy.com/courses/learn-raspberry-pi-command-line/articles/search-the-command-line


## Search the Command Line

**Search with grep, find, history, and Ctrl + R!**

This article will give you the tools to search and find files, folders, and previously used commands within your command-line terminal. Gone are the days of scrolling through files and folders and guessing what directory you need. You will no longer waste valuable time trying to remember that command you need.

Search Files With grep
The grep command can be very useful when trying to find a word or phrase from a file. In the example below, grep searches the continents.txt file for the word “America” and returns the phrases that match, whether it is a title, paragraph, or line of code from the file.
```
$ grep America continents.txt 
```
output:
```
There are 41 countries in North America.
South America has 5.53% of the world's population.

```
It is important to know that grep is case-sensitive. If we want to ignore upper/lower case letters, we must use grep -i. This will make our search case insensitive.
```
$ grep -i Hoarding city_safety.txt

```

output:
```
Extreme hoarding is considered a mental illness.
Hoarding can lead to unsanitary and unhealthy living.
```
Although the word Hoarding was used in the search, the phrases with both hoarding and Hoarding were returned.

The above commands are a great way to get started with grep. If you are familiar with regular expressions, you can also use regular expressions to search for patterns in files. It is not necessary to know regular expressions for this article but if you’d like to learn more click here.



### Search Directories With grep
The grep -R command searches the contents of all files in a directory and outputs file names and lines containing matched results. -R stands for “recursive”.

$ grep -R Arctic /home/ccuser/workspace/geography

output:

/home/ccuser/workspace/geography/deserts.txt:Arctic Desert
/home/ccuser/workspace/geography/oceans.txt:Arctic Ocean
/home/ccuser/workspace/geography/islands/greenland.txt:Arctic Ocean

Above, grep -R searched the /home/ccuser/workspace/geography directory for the string “Arctic” and outputted file names and lines with matching results. Notice the third file in the output was located in geography/islands/ and islands/ is a subdirectory (child directory) of geography/. The grep command searches the contents of the files in the directory and its subdirectories.

If you would like to search all directories in your home directory, your current working directory must be the home directory (so that all other directories become subdirectories).

grep -Rl searches all files in a directory and outputs only file names with matched results (so no lines). l (a lowercase L) stands for “files with matches.”

$ grep -Rl Arctic /home/ccuser/workspace/geography

output:

/home/ccuser/workspace/geography/deserts.txt
/home/ccuser/workspace/geography/oceans.txt

Here grep -Rl searched the /home/ccuser/workspace/geography directory for the string “Arctic” and outputs file names with matched results.

Search by Name With find and grep
We’ve discussed how to search the contents of a file or directory, but let’s walk through how to search for a file or directory by name. We will use the find and grep commands to do this.

The find command will search every file name or subdirectory name within the current working directory. The example below runs find 2015 and returns every file or directory that has the name 2015.

This is an image of the command `find 2015` and the output that appears. The output includes every combination of the directory named `2015`.

When using find, you must search using the entire name of the file or directory. Notice below that when we search with part of the name such as find 5 (the 201 is omitted), then the error message says No such file or directory found. This is because there is no file or directory named 5.

This is an image of the command `find 5` and the output that appears. The output says `No such file or directory found`.

However, we can use both the find command and the grep command, joined by a pipe |, to search with any text pattern. A pipe | is used when combining two or more commands. The following example will ensure that every file or directory that has 5 in the name will be returned.

This is an image of the command `find | grep 5` and the output that appears. The output is a list of every directory combination that contains the number 5.

Note, the period . in the output means the current working directory. For example, if your current working directory was /home, then ./ccuser would translate to /home/ccuser.

### history Command List
As you are working in your command line, it can be very helpful to know which commands you have previously used. The history command will return a chronological list of all the commands that have been previously entered.

This is a screenshot of the `history` command and its output. The output is a list numbered 1 to 5 and the items are: `pwd`, `ls`, `cat file.py`, `cp file.py destination/`.

In the command line above, the history command returns all the commands that have been used: pwd, ls, cat file.py, cp file.py destination/, and history. The first command (pwd) is the oldest command entered and the fifth command (history) is the most recently entered command.

To run any of the commands from the history command list, enter ! with either the number that corresponds to the command or a text pattern. In the example below, both !3 and !ca execute cat file.py. The !3 command looks for and runs the third element from the command list and the !ca command will run the most recent command that matches the text pattern ca.

This is a screenshot of the command `!3`. It runs `cat file.py` and the output is `print("Hello")`.

This is a screenshot of the command `!ca`. It runs `cat file.py` and the output is `print("Hello")`.

After we run the history command and press enter, we can immediately cycle through the commands from the history command list with the up arrow, starting at the bottom of the history list. This will allow us to edit the command before we run it.

### history with grep
By using the history and grep commands joined with a pipe |, we can return all the previously used commands that match a text pattern.

This is a screenshot of the command `history | grep cd` and the output is `2 cd blog`, `5 cd 2014`, and `7 cd ..`, `12 cd 2015`, `14 history | grep cd`.

The command history | grep cd returned all the commands that have the text pattern cd. This can be extremely useful if you want to, for example, see all the commands that were used to move (mv) or remove (rm) files.

$ history | grep mv

$ history | grep rm

### history with tail
Using history with the tail command will return the last ten commands, as opposed to the whole history command list.

This is a screenshot of the command `history | tail` and the output. The output is a list of commands numbered from 6 to 15 because it is the last ten commands used.

We can also specify how many commands we would like to view. The following command will return the last three commands that were previously entered. You may enter any number in place of 3 if you wish to view a different amount.

This is an image of the command `history | tail -n 3` returning a list of the last three commands used.

### Clear history
To clear the history command list, enter history -c. This will delete the entire list of previously used commands.

Search Commands With ctrl + r
If you don’t want a list of commands to be returned, you can search for a specific command with the keys ctrl + r. After pressing ctrl + r the following text will appear in the command line:

This is a screenshot of the command line that reads `(reverse-i-search'':`.

Next, enter at least one character to start a search. In the example below, the letter c is entered. The command text cp file.py destination/ appears because it is the most recently used command that starts with a c. This is called a reverse search because it will first return the most recently used command.

This is an image of the ctrl + r search bar. The letter `c` has been entered and `cp file.py destination/` appeared.

Once we select cp file.py destination/ by pressing enter, the search line will disappear and the command cp file.py destination/ will run. If you want to edit the command text before running it, press the right or left arrow key before pressing enter.

You can also cycle through commands with the up or down arrows. This can be done before you enter any characters in the search. The cycle will start with the last command used. If you continue to press the up arrow, then it will continue to cycle through the commands till you get to the oldest command used in your history command list. If you enter a character or multiple characters in the search, you can still use the up or down arrows to cycle through every command, however, the only difference now is you will start with the command that matched the characters used in the search.

Great work completing this article! You should now be able to find locate most files, directories and previously used commands in the command line. Here’s a run down of what we covered:

- The grep command and how it can be used to search for content in specified files or all files in subdirectories
- The find command and how to locate files and directories by name with or without using grep
- The history command and how is used to locate previous executed commands
- Once located, previously executed commands can be run using the ! character
- Using grep, tail and the -c option to customize the behavior of history
- Using ctrl + r to perform a reverse search on commands
