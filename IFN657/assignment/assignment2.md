# IFN657 Assignment2 讲解
作者：pan

+ 概述  
 用的cares，自己跟着操作，cares库用的1.7.5，样例输入来自官方，库在最底下。  
我要三连！！！  
我要三连！！！  
我要三连！！！ 

+ assignment要求  
1. 那个方法导致的漏洞？程序输入是什么会导致这个漏洞？  
ares_create_query 输入以类似'\.'结尾
2. 漏洞发生在hareness文件的哪里  
40行，调用了如上方法
3. 如何利用漏洞做事  
crash program 
4. 如何修复此漏洞？  
升级到12或者更新的版本
5. 提交crash文件  

+ 作业章节
1. 介绍
2. 介绍程序，介绍测试C文件
3. fuzz过程
4. 结果分析
5. 结论

+ FUZZ指令流程  
1. 装环境
先要有assignment1的环境  
sudo apt-get install afl++ libtool  
2. 作业目录
tar xzvf c-ares.tgz 解压缩  
3. 前进到c-ares目录  
cd c-ares  
./buildconf  
export AFL_USE_UBSAN=1  
export AFL_USE_ASAN=1  
./configure CC=afl-gcc CXX=afl-g++ LD=afl-gcc --enable-shared=no  
make  
4. 退回到作业目录
afl-clang -I ./c-ares -DCARES_STATICLIB -DHAVE_CONFIG_H -o cares-harness cares-harness.c ./c-ares/.libs/libcares.a  
准备测试文件夹 mkdir input 里面东西自己放  
准备输出文件夹 mkdir output  
5. 开始  
afl-fuzz -m none -i input -o output ./cares-harness @@
6. 遇到问题  
内存不够 make -j 4  
core dump： sudo su

+ gdb调试指令  
info stack  
info parc show

+ github  
libfuzzer workshop cares https://github.com/Dor1s/libfuzzer-workshop/tree/master/lessons/06  
cares https://github.com/c-ares/c-ares  