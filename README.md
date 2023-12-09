# OpenIGTLink TrackingData Example

The following instruction is written for Linux/macOS environment, though the code should also work on Windows.


## Prerequisite

- C++ compiler
- CMake


## Building instruction

First, build the OpenIGTLink library. The detailed build instruction is available at (the OpenIGTLink library repository)[https://github.com/tokjun/OpenIGTLink/tree/test_rts_tdata/Examples/TrackingData]. The example code should work without any additional options. In a nutshell, 

~~~
$ cd <working directory>
$ git clone https://github.com/openigtlink/OpenIGTLink   # Clone the repository 
$ mkdir OpenIGTLink-build                                # Create a build directory
$ cd OpenIGTLink-build
$ cmake ../OpenIGTLink
$ make                                                   # Build the library. You may add -j option to run multiple jobs simultaneously.
~~~~

Once the OpenIGTLink has been built, you can build the example as follows:

~~~
$ cd <working directory>
$ git clone https://github.com/tokjun/IGTLTrackingDataTest # Clone the repository 
$ mkdir IGTLTrackingDataTest-build                         # Create a build directory
$ cd IGTLTrackingDataTest-build
$ cmake -DOpenIGTLink_DIR:PATH=../OpenIGTLink-build ../IGTLTrackingDataTest
$ make
~~~

If successful, the following two executable files should be in the build directory:
- TrackingDataClient
- TrackingDataServer

## Running the example program

Open two terminals, and run the following commands.

On the first terminal (server):
~~~
$ cd <working directory>/IGTLTrackingDataTest-build 
$ ./TrackingDataServer  18944
~~~

On the second terminal (client):
~~~
$ cd <working directory>/IGTLTrackingDataTest-build 
$ ./TrackingDataClient localhost 18944 10
~~~

Please note that `18944` is a TCP/IP port number. The port numbers for the server and the client must match. Any port number should work as long as the port is available and the user has a sufficient privilege. 













