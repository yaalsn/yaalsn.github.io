---
title: debug hotspot on macos
date: 2017-07-06 06:20:49
tags: hotspot
---
## 编译openjdk9
### 安装freetype

```bash
brew install freetype
```

### 安装ccache
```bash
brew install ccache
```

### 获取openjdk9源码
```bash
hg clone http://hg.openjdk.java.net/jdk9/jdk9 openjdk9
cd openjdk9
bash get_source.sh
```
### 编译
```bash
bash configure --with-freetype-include=/usr/local/include/freetype2 --with-freetype-lib=/usr/local/lib --with-debug-level=slowdebug --with-native-debug-symbols=internal --disable-warnings-as-errors SEPARATED_DEBUGINFO_FILES=false
make images
```
编译所需时间不长，十多分钟，期间可以来一发

## debug hostpot
用clion导入hotspot源码，Executale设置成build里的jdk/bin/java，before launch把build去掉，断点插入到JNI_CreateJavaVM函数中，开始debug！美滋滋～
