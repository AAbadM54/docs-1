### Overview

The images in this repository contain OpenJDK binaries that are built with binaries from [AdoptOpenJDK](https://adoptopenjdk.net/).

Java and all Java-based trademarks and logos are trademarks or registered trademarks of Oracle and/or its affiliates.

### What is AdoptOpenJDK ?

AdoptOpenJDK is a community of Java user group members, Java developers and vendors who are advocates of OpenJDK, the open source project which forms the basis of the Java programming language and platform. AdoptOpenJDK provides prebuilt OpenJDK binaries from a fully open source set of build scripts and infrastructure. AdoptOpenJDK builds and tests binaries for different source code streams based upon OpenJDK. Our binaries undergo extensive testing, and the Releases have passed all the available OpenJDK test suites and our additional tests (donated by the community), ensuring the best quality binary available.

### Images

There are two types of Docker images here: the Java Development Kit (JDK), and a small footprint version of the JDK (slim). These images can be used as the basis for custom built images for running your applications.

##### Multi-Arch Image

Docker Images for the following architectures are now available:

-	x86\_64, ppc64le, s390x, aarch64

### How to use this Image

To run a pre-built jar file with the JRE image, use the following commands:

```dockerfile
FROM %%IMAGE%%:8-jdk
RUN mkdir /opt/app
COPY japp.jar /opt/app
CMD ["java", "-jar", "/opt/app/japp.jar"]
```

You can build and run the Docker Image as shown in the following example:

```console
docker build -t japp .
docker run -it --rm japp
```

If you want to place the jar file on the host file system instead of inside the container, you can mount the host path onto the container by using the following commands:

```dockerfile
FROM %%IMAGE%%:jdk
CMD ["java", "-jar", "/opt/app/japp.jar"]
```

```console
docker build -t japp .
docker run -it -v /path/on/host/system/jars:/opt/app japp
```
