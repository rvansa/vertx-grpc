# Fork information

This is a forked version of the Vert.x project intended to be used before the support for CRaC lands in the official version. The artifact should be published on these Maven coordinates:

```
<dependency>
   <groupId>io.github.crac.io.vertx</groupId>
   <artifactId>vertx-grpc</artifactId>
   <version>[version].CRAC.[number]</version>
</dependency>
```

where `[version]` matches a released Vert.x gRPC version and `[number]` is an increasing numeric identifier representing version of CRaC-related updates.

## Managing CRaC-enhanced versions

Here is an example of enhancing version `4.3.8`, using changes that are applied on top of the `4.3` branch (in branch `4.3_crac`):

```
./enhance.sh 4.3.8 0
git push 4.3.8.CRAC.0
```

When there's an update in the `4.3` branch, `4.3_crac` should be rebased (using `git rebase` rather than merge) on top of that.

# Vert.x gRPC

Currently for Vert.x 3.4.0-SNAPSHOT

- [Documentation](src/main/asciidoc/java/index.adoc)
- [Vert.x gRPC Java Compiler](https://github.com/vert-x3/vertx-grpc-java-compiler)

Supports:

- client and server
- server scaling
- ssl configuration with options
- auto close in Verticle

Todo:

- contribute support to grpc-java Netty implementation to provide async start/shutdown
- worker integration ?

## Plugin installation

To use vertx-grpc-protoc-plugin with the protobuf-maven-plugin, add a [custom protoc plugin configuration section](https://www.xolstice.org/protobuf-maven-plugin/examples/protoc-plugin.html).

```
<protocPlugins>
    <protocPlugin>
        <id>vertx-grpc-protoc-plugin</id>
        <groupId>io.vertx</groupId>
        <artifactId>vertx-grpc-protoc-plugin</artifactId>
        <version>[VERSION]</version>
        <mainClass>io.vertx.grpc.protoc.plugin.VertxGrpcGenerator</mainClass>
    </protocPlugin>
</protocPlugins>
```

And add the [vertx-grpc](https://github.com/vert-x3/vertx-grpc) dependency:

```
<dependency>
  <groupId>io.vertx</groupId>
  <artifactId>vertx-grpc</artifactId>
  <version>[VERSION]</version>
</dependency>
```
