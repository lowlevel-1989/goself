~~~
$ mkdir /tmp/vinicio
$ sudo ./goself --help
$ sudo ./goself --unshare --fork
$ sudo umount /tmp/vinicio
~~~

~~~
[./goself --unshare --fork]
[]
INIT LOADER 195498
     SET CLONE_NEWNS

[init --unshare --fork loader]
[loader]
     LOADER 195502
        test 1 [] -> ls /tmp/vinicio/
        test 1 [] -> test
        test 1 [] -> vicky

     FORK EXEC

[init unshare]
[unshare]
     UNSHARE 195506
        mkdir /tmp/vinicio/test
        err mkdir ->  mkdir /tmp/vinicio/test: file exists
        test 2 [] -> ls /tmp/vinicio/
        test 2 [] -> test
        test 2 [] -> vicky

        mount /tmp/vinicio
        err mount ->  <nil>
        err mount ->  <nil>
        test 3 [] -> ls /tmp/vinicio/

        test 4 [goroutine] -> ls /tmp/vinicio/

        mkdir /tmp/vinicio/test1
        err mkdir ->  <nil>
        mkdir /tmp/vinicio/test2
        err mkdir ->  <nil>
        mkdir /tmp/vinicio/test3
        err mkdir ->  <nil>

        test 5 [with data] -> ls /tmp/vinicio/
        test 5 [with data] -> test1
        test 5 [with data] -> test2
        test 5 [with data] -> test4

        test 6 [with data goroutine] -> ls /tmp/vinicio/
        test 6 [with data goroutine] -> test1
        test 6 [with data goroutine] -> test2
        test 6 [with data goroutine] -> test4

        test 7 [with data goroutine] -> ls /tmp/vinicio/
        test 7 [with data goroutine] -> test1
        test 7 [with data goroutine] -> test2
        test 7 [with data goroutine] -> test4
~~~