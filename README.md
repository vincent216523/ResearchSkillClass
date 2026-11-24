Readme (Sorting Experiment)
==========================
This package contains the C source code "sort.c" for:
1. Reading a list of integers from a data file
2. Sorting the integers in ascending order using a pairwise exchange sort
3. Writing the sorted list to an output file
4. Recording the number of swaps and execution-time statistics

Usage Step
==========
a. Compilation
   Compile "sort.c" with a C compiler. For example, using GCC:

   Linux/macOS:
       gcc sort.c -o run

   Windows (GCC/MinGW):
       gcc -DWIN32 sort.c -o run.exe

b. Execution
   Run the program from the directory containing "config.txt".

   Linux/macOS:
       ./run

   Windows (PowerShell):
       .\run.exe

   The program reads "config.txt" automatically.

c. Input Files (Formats can be found in the Appendix)
   1. "config.txt" specifies the data filename, number of integers,
      and three additional parameters.
   2. The data file is specified in "config.txt". The supplied example
      uses "data.txt".
   3. "configurations.xlsx" is included among the supplied files,
      but is not read by "sort.c" and is not required for execution.

d. Output Files (Formats can be found in the Appendix)
   1. "output.txt" contains the sorted integers.
   2. "stat.txt" contains the total number of swaps.
   3. "time.txt" contains execution-time statistics

   Output files are created in the current working directory and
   overwritten on each run.

Appendix A. Format of Configuration File ("config.txt")
------------------------------------------------------
The file contains the following five values, conventionally one per line:

1. dataFilename: filename or path of the input data file (no whitespace)
2. size: number of integers to read and sort
3. parameter2: integer parameter
4. parameter3: integer parameter
5. parameter4: floating-point parameter

Example:
    data.txt
    10
    1000
    2000
    0.5

All five values must be supplied.
For a nonempty list, use a positive size and provide at least that many
valid integers in the data file. The program does not validate malformed
configuration values or missing data values.

Appendix B. Format of Data File (Example: "data.txt")
---------------------------------------------------
The data file contains integers separated by whitespace. Multiple integers may appear on the same line.

The program reads exactly "size" integers, as specified in "config.txt".
Any additional integers are ignored.

Example:
    10 8 5 2 3 7 6 2 4 1

Appendix C. Format of "output.txt"
---------------------------------
The file contains the sorted integers in ascending order on one line.
Each integer is followed by a space, and the line ends with a newline.
Duplicate values are preserved.

Output for the supplied example:
    1 2 2 3 4 5 6 7 8 10

Appendix D. Format of "stat.txt"
-------------------------------
The file contains one integer followed by a newline:

1. noOfSwapping: total number of swaps performed during sorting

The algorithm compares each element with every later element and swaps
the pair whenever the earlier value is larger. This statistic counts
swaps.

Output for the supplied example:
    33

Appendix E. Format of "time.txt"
-------------------------------
Values are written with ten digits after the decimal point.

1. Time for initialization, reading "config.txt", and reading the data
2. Time for copying the input list and sorting the copy
3. Time for writing the sorted list to "output.txt"
4. Overall time from the initial timing measurement through writing
   "output.txt"

There are no blank separator lines. These measurements report CPU time rather
than elapsed wall-clock time.

When WIN32 is defined during compilation, "time.txt" is empty.
The supplied "time.txt" is also empty.
