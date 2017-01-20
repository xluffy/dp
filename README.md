Docker
======

## 1. Build JDK Image from Dockerfile

- master: don't test with travis
- dl: [![Build Status](https://travis-ci.org/xluffy/dp.svg?branch=dl)](https://travis-ci.org/xluffy/dp)

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
xluffy/jdk     1.8      24d9252eefed        2 days ago          576.9 MB
xluffy/jre     1.8      436bf6fb1682        2 days ago          346.6 MB
```
