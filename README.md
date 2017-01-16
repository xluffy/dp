Docker
======

## 1. Build JDK imagefrom Dockerfile

Download jdk source

```
cd jdk1.8 && mkdir -pv src
curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u51-b16/jdk-8u51-linux-x64.tar.gz" > src/jdk-8u51-linux-x64.tar.gz
```

```
docker build -t xluffy/jdk:1.8 -f Dockerfile .
```
