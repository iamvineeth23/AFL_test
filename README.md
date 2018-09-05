# AFL_test
A simple implementation of fuzzing to learn/test AFL as explained in http://spencerwuwu-blog.logdown.com/posts/1366733-a-simple-guide-of-afl-fuzzer

## Overview:
The code takes strings as input and will print the same as output. But when the string "deadbeef" is given as an input, the code crashes. 
This simple case is run in AFL fuzzer as a trial case.

## Steps:
1. A simple C-code is saved in file 'test.c'
2. Compile using ``` afl-clang test.c ```


