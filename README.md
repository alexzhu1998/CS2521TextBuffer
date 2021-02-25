# CS2521 TextBuffer 
A simple Text Buffer implementation using C, and doubly linked list data structure.

## Table of Content
* [General Info](#general-info)
* [Screenshots](#screenshots)
* [Technologies](#technologies)
* [Setup](#setup)
* [Code Examples](#code-examples)
* [Features](#features)
* [Status](#status)
* [Source](#source)

## General Info
This is a crude C implementation of text buffers that forms the basis of shell terminal text buffers. While it has no standard input, and it requires users to manipulate the functions directly, it has standard output.

## Technologies
C17 was the version of C used.
Ensure gcc is installed on the computer

## Setup
To compile the test functions:
```
$ gcc -Wall -Werror -std=c11 -O -lm -o testTextbuffer testTextbuffer.c textbuffer.c
$ gcc -Wall -Werror -std=c11 -g -lm -o testTextbuffer testTextbuffer.c textbuffer.c
```
To Run the test functions:
```
$ ./testTextbiffer
```

## Code Examples
Merge the two textbuffers at different positions along the text buffer
```
TB tb1 = newTB("hello there,\nhow\nare\nthings\n");
	TB tb2 = newTB("pretty good,\nhows\nthings\nfor\nyou\n");
	TB tb3 = newTB("hello there,\nhow\nare\nthings\n");
	TB tb4 = newTB("pretty good,\nhows\nthings\nfor\nyou\n");
	TB tb5 = newTB("hello there,\nhow\nare\nthings\n");
	TB tb6 = newTB("pretty good,\nhows\nthings\nfor\nyou\n");	
	
	mergeTB(tb1,3,tb2);
	mergeTB(tb3,1,tb4);
	mergeTB(tb5,5,tb6);
	
	char *text1 = dumpTB(tb1, false);
	char *text12 = dumpTB(tb3, false);
	char *text13 = dumpTB(tb5, false);	
	
	printf("%s",text1);
	printf("%s",text12);
	printf("%s",text13);	
	
	free(text1);
	free(text12);
	free(text13);
	
	releaseTB(tb1);
	releaseTB(tb3);
	releaseTB(tb5);
```
Expected Output
```
hello there,
how
pretty good,
hows
things
for
you
are
things
pretty good,
hows
things
for
you
hello there,
how
are
things
hello there,
how
are
things
pretty good,
hows
things
for
you
```


Output the difference between two textbuffers
```
	TB tb1 = newTB("\n\n\n\nsdfdsf\nsdf\naafb\n");    
	TB tb2 = newTB("\n\na\nbc\n\n\n\n\n\n\n");
	char* text = dumpTB(tb2,true);
	free(text);
	char* diffText = diffTB(tb1,tb2); 
	printf("%s\n",diffText);
	free(diffText);
	releaseTB(tb1);  
	releaseTB(tb2);
```
Expected Output
```
+,3,a
-,4
+,4,bc
-,5
+,5,
-,6
+,6,
-,7
+,7,
-,8
+,9,
+,10,
+,11,
```

## Features
The following functions are implemented:
* newTB: Initialise Textbuffer
* dumpTB: Convert Textbuffer to Strings
* releaseTB: Free the memory occupied by the given textbuffer
* linesTB: Return the number of lines of the given textbuffer
* addPrefixTB: Add a given prefix to all lines between 'from' and 'to', inclusive
* mergeTB: Merge textbuffer 2 into textbuffer 1 at specific line position
* pasteTB: Copy textbuffer 2 into textbuffer 1 at specific line position
* cutTB: Cut the line sbetween and including 'from' and 'to' out of the given textbuffer 'tb' into a new textbuffer
* searchTB: Return a linked list of match nodes containing the positions of all of the matches of string 'search' in 'tb'
* deleteTB: Remove the lines between 'from' and 'to' (inclusive) from the given textbuffer 'tb'
* formRichText: Search every line of the given textbuffer for every occurrence of a set of specified substituion and alter them accordingly
* diffTB: Show which lines of text are added or deleted to get from tb1 to tb2
* (To be implemented) undoTB: 
* (To be implemented) redoTB:

## Status
Shelved

## Contact
Created by Alex Zhu. 
