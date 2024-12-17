## 已经归档,进行最后的文档修复

## 交叉编译器路径配置
检查路径:使用export命令临时更改路径

编译器GCC

链接器LD

```set(CMAKE_C_COMPILER ../../cross-tool/bin/loongarch64-unknown-linux-gnu-gcc)```
```set(CMAKE_CXX_COMPILER ../../cross-tool/bin/loongarch64-unknown-linux-gnu-g++)```

## 代码布局
build/构建目录
init/：初始化代码
drv/：设备驱动
excp/：异常处理
mm/：内存管理
proc/：进程管理
fs/：文件系统
CMakeLists.txt 构建规则

## CMAKE_C_CFLAGS
本测试在真实运行中不要位置无关代码,不要优化,不要调试信息
```set(CMAKE_C_FLAGS "-Wall -Werror -O -fno-omit-frame-pointer -ggdb -MD -march=loongarch64 -mabi=lp64 -ffreestanding -fno-common -nostdlib -Iinclude -fno-stack-protector -fno-pie -no-pie")```
## CMAKE_EXE_LINKER_FLAGS
页面大小4096字节,代码加载地址0x9000000000200000

## 目标系统

```sudo apt-get install qemu qemu-user qemu-user-static```

构建QEMU硬件模拟器模拟LoongArch架构
