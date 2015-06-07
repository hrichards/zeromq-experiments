# zeromq-experiments
Playing around with ZeroMQ concurrency framework.


# Setup

It was a real headache to get these examples going, but once I did, the needed
commands are very simple.  I still have a lot to learn about the C ecosystem.

First, library setup.

On Ubuntu, since all libraries needed for compilation aren't available via
`apt-get install`, so I installed everything I needed from source tarballs,
retrieved via the following commands, and installed in that order:

```
wget http://download.zeromq.org/zeromq-4.1.1.tar.gz
wget https://download.libsodium.org/libsodium/releases/libsodium-1.0.3.tar.gz
wget http://download.zeromq.org/czmq-3.0.1.tar.gz
```

Each project's website explains any other updates available via `apt-get
install` that you might need to install these requirements.

As a note to myself, I was looking for some consistency in the C project build
system, and I seem to have found some: every project listed above uses some
variant of the following command list to build, test, and install itself:

```
./configure
make && make check
make install
```

`configure` being part of the `autoconf` package, and the `make check` target
being the test suite.  Only Sodium had a test suite target: you should look
into it to see what a C test suite looks like.

The final problem I had was getting the examples from the "zguide" ZeroMQ docs working:

```
git clone --depth=1 https://github.com/imatix/zguide.git
```

First, some observations:

1.  There is a `build` script in the `examples` directory in the zguide that
    can correctly build one or more targets in the project.
2.  If you look at `build`, it sets some vars and does some arg parsing, but
    then hands things off to its co-script, `c`, in the same directory.
3.  `c` has a `-v` flag that can be used to see verbose output.

Finally, if you look at the output of the verbose run above, you see that `-l`
directives are being issued for the two big libraries in these projects, `zmq`
and `czmq`.  Since `hello-world` only relies on `zmq`, I just added the `-l
zmq` flag.

Thus the command to compile the first example in the zguide without using the
shipped build system, and the one I've added to that directory's README, is the
following:

```
gcc hello-world.c -lzmq
```
