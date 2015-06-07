It works!  So cool.

Now, here's an example session:

```
[hunter@hunter-VirtualBox:~/zeromq-experiments/hello-world][master]./hello-world-server &
[1] 18121
[hunter@hunter-VirtualBox:~/zeromq-experiments/hello-world][master]jobs
[1]+  Running                 ./hello-world-server &
[hunter@hunter-VirtualBox:~/zeromq-experiments/hello-world][master]./hello-world-client
Connecting to hello world server…
Sending Hello 0…
Received Hello
Received World 0
Sending Hello 1…
Received Hello
Received World 1
Sending Hello 2…
Received Hello
Received World 2
Sending Hello 3…
Received Hello
Received World 3
Sending Hello 4…
Received Hello
Received World 4
Sending Hello 5…
Received Hello
Received World 5
Sending Hello 6…
Received Hello
Received World 6
Sending Hello 7…
Received Hello
^C
[hunter@hunter-VirtualBox:~/zeromq-experiments/hello-world][master]fg 1
./hello-world-server
^C
```

You comple both client and server with `make`, and then you set
`hello-world-server` running in the background, and then use the `client` to
talk to it.
