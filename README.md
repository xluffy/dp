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
