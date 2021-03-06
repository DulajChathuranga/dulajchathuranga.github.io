---
layout: post
title: The use of fread and fwrite in the C language
tags: [C, Programming]
comments: true
---


fread() and fwrite() are C file direct input/output functions defined in stdio.h library. fread() use to read from a file and fwrite() use to write to a file.

fread()

Function fread() reads data from the given data stream(4th parameter), to an array, pointed in to by a pointer(1st parameter).

{% highlight ruby %}
fread (ptr, size, n, inptr)
{% endhighlight %}

ptr - pointer to a block of memory (store what reads from inptr)

size - size of an element

n - number of elements to read

inptr - pointer to the input file

fread() reads from where it left off last time and returns the number of elements (n) successfully read.

This is a part of a program use fread().

{% highlight ruby %}

// Open input file
FILE *inptr = fopen (infile, "r");
//Check for a valid file
if (inptr == NULL)
{
    fprintf (stderr, "Could notopen %s", infile);
    return 1;
}
 
// Memory allocation for buffer
int *buffer = malloc(512);
 
// Read input file
while (fread (&buffer, 1, 512, inptr) == 512)
{
      // DO WHAT YOU NEED HERE
}
 
// Free memory from buffer
free(buffer);
 
// close infile
fclose(inptr);
 
return 0;
fwrite()

{% endhighlight %}

Function fwrite() write data to the given file pointed by 4th parameter, from data pointed by 1st parameter.

{% highlight ruby %}
fwrite (ptr, size, n, outptr)
{% endhighlight %}

ptr - pointer to a block of memory (contains data that write to outptr)

size - size of an element

n - number of elements to write

outptr - pointer to the output file

References:

C library function fread()
C library function fwrite()
C file input/output - Wikipedia
