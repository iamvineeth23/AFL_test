# AFL_test
A simple implementation of fuzzing to learn using AFL fuzzer as explained in http://spencerwuwu-blog.logdown.com/posts/1366733-a-simple-guide-of-afl-fuzzer

## Overview:
The code takes strings as input and will print the same as output. But when the string "deadbeef" is given as an input, the code crashes. 
This simple case is run in AFL fuzzer as a trial case.

## Steps:
1. A simple C-code is saved in file 'test.c'
2. Compile using ``` afl-clang test.c ```
3. Test cases are in the directory 'testcases'
4. Output of the AFL fuzzer will be saved in the directory 'findings'
5. Run the fuzzer with  ```afl-fuzz -i testcases -o findings -t 20000 ./a.out```

OS X crash reporter triggers when the test case crashes, and generating the crash report takes substantially longer than afl-fuzz's default timeout of 20 milliseconds. This causes afl-fuzz to report all crashes as hangs. A simpler workaround is simply to increase the timeout, which can be done by passing the -t flag. This will seriously hurt performance if there are hangs, but works well enough for this test case. Thanks to https://www.mikeash.com/pyblog/friday-qa-2015-05-01-fuzzing-with-afl-fuzz.html for this workaround. 

The fuzzing process window is shown in the image below. The crash for the input "deadbeef" is found and hence the ```uniq crashes ``` value is 1.

<p align="center">
  <img width="460" height="300" src="https://user-images.githubusercontent.com/33487736/45077159-bb8ab400-b0ec-11e8-800e-591c296a6057.png">
</p>

<p align="center">
<span class="image-caption"> Fig. - AFL fuzzing window </span>
</p>
