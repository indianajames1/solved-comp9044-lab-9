Download Link: https://assignmentchef.com/product/solved-comp9044-lab-9
<br>



<h1>Your task</h1>

Write a Perl script makemake.pl to generate a Makefile that will build the C program whose source code is in the current directory.

The script takes no arguments, and writes the Makefile text to its standard output.

<h2>Assumptions</h2>

The current directory contains all code files from only one C program.

The C program is composed only of .c and .h files.

Exactly one .c file will contain a main() function.

The main() function appears on a line that matches the regexp

/^s*(int|void)s*mains*(/

No other line in the files matches this regex.

The executable is named after the file containing the main() function (without the .c)

Any line starting with #include is a genuine include line

(ignore multi-line comments and other preprocessor commands like #if)

All the dependencies that need to be included in the Makefile involve files that exist in the current directory

<h2>Example Output</h2>

Three example C programs are available as a <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/makemake/examples.zip">zip</a> <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/makemake/examples.zip">file</a>

Here is the output your program should produce for each of these examples:




<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>unzip /web/cs2041/20T2/activities/makemake/examples.zip</strong> Archive:  examples.zip    creating: easy/  extracting: easy/graphics.h   inflating: easy/graphics.c ….$ <strong>cd easy</strong> $ <strong>ls</strong> easymain.c  graphics.c  graphics.h  world.c  world.h$ <strong>../makemake.pl &gt;Makefile</strong>$ <strong>cat Makefile</strong># Makefile generated at Mon 27 Jul 17:24:51 AEST 2020CC = gccCFLAGS = -Wall -geasymain:   easymain.o graphics.o world.o$(CC) $(CFLAGS) -o <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="a581e5">[email protected]</a> easymain.o graphics.o world.ographics.o: graphics.h world.h graphics.c easymain.o: world.h graphics.h easymain.c world.o:    world.h world.c$ <strong>make</strong> gcc -Wall -g   -c -o easymain.o easymain.c gcc -Wall -g   -c -o graphics.o graphics.c gcc -Wall -g   -c -o world.o world.c gcc  -o easymain easymain.o graphics.o world.o$ <strong>cd ../medium</strong>$ <strong>ls</strong>a.c  a.h  aaa.c  aaa.h  b.c  b.h  bb.c  bb.h  c.c  c.h  common.h  main.c$ <strong>../makemake.pl &gt;Makefile</strong>$ <strong>cat Makefile</strong># Makefile generated at Mon 27 Jul 17:26:43 AEST 2020CC = gccCFLAGS = -Wall -gmain:   a.o aaa.o b.o bb.o c.o main.o$(CC) $(CFLAGS) -o <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="0a2e4a">[email protected]</a> a.o aaa.o b.o bb.o c.o main.ob.o:    b.h bb.h aaa.h b.cc.o:    c.h c.ca.o:    common.h a.h a.c bb.o:   bb.h aaa.h bb.c main.o: a.h c.h b.h bb.h aaa.h main.c$ <strong>make</strong> gcc -Wall -g   -c -o a.o a.c gcc -Wall -g   -c -o aaa.o aaa.c gcc -Wall -g   -c -o b.o b.c gcc -Wall -g   -c -o bb.o bb.c gcc -Wall -g   -c -o c.o c.c gcc -Wall -g   -c -o main.o main.c gcc  -o main a.o aaa.o b.o bb.o c.o main.o$ <strong>cd ../hard</strong>$ <strong>ls</strong> circ1.c  circ1.h  circ2.c  circ2.h  circmain.c$ <strong>../makemake.pl &gt;Makefile</strong>$ <strong>cat Makefile</strong># Makefile generated at Mon 27 Jul 17:29:14 AEST 2020CC = gccCFLAGS = -Wall -gcircmain:   circ1.o circ2.o circmain.o$(CC) $(CFLAGS) -o <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="9fbbdf">[email protected]</a> circ1.o circ2.o circmain.ocirc1.o:    circ1.h circ2.h circ1.c circmain.o: circ1.h circ2.h circmain.c circ2.o:    circ2.h circ1.h circ2.c$ <strong>make</strong> gcc -Wall -g   -c -o circ1.o circ1.c</td>

  </tr>

 </tbody>

</table>

gcc -Wall -g   -c -o circ2.o circ2.c gcc -Wall -g   -c -o circmain.o circmain.c gcc  -o circmain circ1.o circ2.o circmain.o

<h2>Further Requirements</h2>

You should include four standard lines at the front of every Makefile

# Makefile generated at <em>timestamp in format given above</em>

CC = gcc

CFLAGS = -Wall -g

There should be a blank line immediately before each Make rule

<h2>Hints</h2>

You could use a hash to represent all dependencies

The Perl expression `date` will generate a suitable timestamp

The Perl builtin glob is an easy way to get a list of the .c or .h files in the current directory

You do not need to produce rules for dependencies on standard .h files (e.g. stdio.h) You can assumes includes of standard libraries use &lt;…&gt; notation, e.g:

#include $lt;stdio.h&gt;

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest makemake</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab09_makemake makemake.pl</strong>

before Tuesday 04 August 21 00 to obtain the marks for this lab exercise.

Write a Perl regex which matches unary number iff it is composite (not prime).

In other words write a regex that matches a string of <em>n</em> ones iff <em>n</em> is composite.

A test program is provide to assist you in doing this:

Download <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/regex_prime/test_regex_prime.pl">test</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/regex_prime/test_regex_prime.pl">_</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/regex_prime/test_regex_prime.pl">re</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/regex_prime/test_regex_prime.pl">g</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/regex_prime/test_regex_prime.pl">ex</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/regex_prime/test_regex_prime.pl">_</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/regex_prime/test_regex_prime.pl">prime</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/regex_prime/test_regex_prime.pl">.</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/regex_prime/test_regex_prime.pl">pl</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/regex_prime/test_regex_prime.pl">,</a> or copy it to your CSE account using the following command:

$ <strong>cp -n /web/cs2041/20T2/activities/regex_prime/test_regex_prime.pl .</strong>

For example to test the regex <strong>^1(11)+1$</strong> against the integers 2 to 12, you can run

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>chmod 755 test_regex_prime.pl</strong>$ <strong>test_regex_prime.pl 2 12 ‘^1(11)+1$’</strong>2 = 11 unary – prime 3 = 111 unary – prime4    = 1111 unary – composite5    = 11111 unary – prime6    = 111111 unary – composite7    = 1111111 unary – prime8    = 11111111 unary – composite9    = 111111111 unary – prime10  = 1111111111 unary – composite11  = 11111111111 unary – prime12  = 111111111111 unary – composite</td>

  </tr>

 </tbody>

</table>

Put your solution in regex_prime.txt, for example:

$ <strong>test_regex_prime.pl 40 50 “$(cat regex_prime.txt)”</strong>

<ul>

 <li>= 1111111111111111111111111111111111111111 unary – composite</li>

 <li>= 11111111111111111111111111111111111111111 unary – prime</li>

 <li>= 111111111111111111111111111111111111111111 unary – composite</li>

 <li>= 1111111111111111111111111111111111111111111 unary – prime</li>

 <li>= 11111111111111111111111111111111111111111111 unary – composite</li>

 <li>= 111111111111111111111111111111111111111111111 unary – composite</li>

 <li>= 1111111111111111111111111111111111111111111111 unary – composite</li>

 <li>= 11111111111111111111111111111111111111111111111 unary – prime</li>

 <li>= 111111111111111111111111111111111111111111111111 unary – composite</li>

 <li>= 1111111111111111111111111111111111111111111111111 unary – composite</li>

 <li>= 11111111111111111111111111111111111111111111111111 unary – composite</li>

</ul>

Your regex must be less than 80 characters.

Hint: you can’t do this with a true regular expression, i.e using |*() alone, you need to use features that Perl adds.

Don’t google for other people solutions – see if you can come up with your own.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest regex_prime</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab09_regex_prime regex_prime.txt</strong>

before Tuesday 04 August 21 00 to obtain the marks for this lab exercise.