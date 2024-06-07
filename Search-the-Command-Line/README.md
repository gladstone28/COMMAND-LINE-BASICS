

Search the Command Line
Search with grep, find, history, and Ctrl + R!

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
