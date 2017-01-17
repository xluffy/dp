Docker
======

## 1. Build JDK Image from Dockerfile

Download jdk source

```
cd 8-oracle-jdk && mkdir -pv src
curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie" \
     "http://download.oracle.com/otn-pub/java/jdk/8u51-b16/jdk-8u51-linux-x64.tar.gz" \
     > src/jdk-8u51-linux-x64.tar.gz
```

```
docker build -t xluffy/jdk:1.8 -f Dockerfile .
```

## 2. Build JRE Image from Dockerfile

Download jre source

```
cd 8-oracle-jre && mkdir -pv src
curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie" \
     "http://download.oracle.com/otn-pub/java/jdk/8u51-b16/jre-8u51-linux-x64.tar.gz" >
     > src/jre-8u51-linux-x64.tar.gz
```

## 2. Result

```
xluffy/jre      1.8      4b9299e0cf64        39 minutes ago      517.6 MB
xluffy/jdk      1.8      c431ae95af3b        16 hours ago        735.4 MB
```
