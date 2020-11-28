# Fuzzing with FuzzFactory

Running this command in `/grep-3.1/src` should configure, build, and install this package.
```
./configure && make && make install
```

The makefile in `/src` must be updated to use Fuzzfactory

This can be done by altering the makefile like shown below:

```
CC=WAYPOINTS=cmp ../../afl-clang-fast
```
or
```
CC=WAYPOINTS=cmp,mem ../../afl-clang-fast
```


The corpus is located at:
```
FuzzFactory/grep-3.1/src/seeds/words.txt
```

In `/src` run make and then the following command
```
../../afl-fuzz -p -i seeds -o results ./grep text.txt
```
Where text.txt is a large text file