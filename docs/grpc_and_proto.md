# GRPC and PROTOBUF

### Sources
- GRPC Intro : https://grpc.io/docs/what-is-grpc/introduction/
- Protobuf intro : https://protobuf.dev/getting-started/cpptutorial/
- installation guide : https://grpc.io/docs/languages/cpp/quickstart/#install-grpc

### Installation
- Clone grpc from : https://github.com/grpc/grpc.git 
- Use cmake to build. Ensure you have cmake built with ncurses (ccmake)
- run `mkdir build; cd build; cmake ..`
- cmake options which need to be set are
    - `-DgRPC_INSTALL=ON`
    - `-Dprotobuf_INSTALL=ON` in order to ensure that the right protoc is installed in the system 
    - `-DCMAKE_INSTALL_PREFIX` in case you want to install somewhere other than the default path
- run make and make install


## Notes
### Intro
- A framework used to facilitate RPC calls between clients and servers (usually remote).
- services and functions are defined in a proto file.
- Feels like calling a local function. GRPC wraps around all the underlying logic
- Clients have something called a **stub**, aka ***client stub***
- Servers run gprc-server
- Protobuf converts the proto file into a serialized binary format. Fast and efficient to communicate rather than xml for example

### Proto file
- Proto files usually writing in **proto3** syntax
- Example message:
```
message Dude {
  string name = 1;
  int32 id = 2;
  bool is_cool = 3;
}
```

