# IFN657 Assignment1 讲解
作者：pan  
只谈了要点，不要直接复制-粘贴到谷歌翻译，必须自己扩展。  
This document is only for reference.  
有不懂的发issue，也可以加messager，我的facebook：houk pan

## 基础
1. 环境  
ubuntu gcc gdb  
有的人没法编译，查看gcc-multilib装了没  
这里建议使用vm，老师上课用的那个Multipass没有界面，用的比较吃力
2. gcc编译  
要关掉ASLR(第5题再开)，代码在这儿：echo 0 | sudo tee /proc/sys/kernel/randomize_va_space  
编译之前准备好c语言源文件。不会用chmod的可以自己手敲  
gcc编译指令：gcc -w -m32 -g -fno-stack-protector -z execstack -o bo bo.c  bo是执行文件，执行时候用./bo，后面是源文件。
3. gdb  
gdb指令后面跟执行文件，不然进去要用file绑定。  
断点语法：b [line] 里面是行号  
运行：run  
反编译：disassemble [方法名]  
查看寄存器：info registers  
查看寄存器内部的值： x/x [pointer]  
语法变种为x/[number]x， 以pointer为起始地址向下打印number个值  
单步调试：先用layout asm进调试框，用si进行单步。里面也可以用其他指令。  
继续：c
4. 输入流  
大于号>是把左边的结果输到右边的程序  
小于号<，把右边的结果输入到左边的程序  
测密码时候会用到。

## buffer overflow  
1.  gets方法不计算输入长度。所以输入内容过多会导致栈溢出。
2. 根据第一题的结论，所以输入密码过长会修改到其他变量的值。题目要求修改trigger值而不修改返回值。办法是找到trigger值并填入。在栈里trigger值在passwd后面在ebp前面。可以先找passwd的位置，再推测，也可以通过esp和ebp去定位。T的ascii码是54(Hex)，自己留意ret的地址。ret的位置在ebp后4位，注意跳转到源代码的if语句，asm代码的main-cmp，检查不要跳错，有跳错自己改回来。
3. 这次修改return的值。先找到return的位置，就是在ebp+4的地方。要往哪里跳看自己选择。可往主函数的调用login的地方跳，可往login函数头跳，可往printf之前跳，皆可，题目很开放，但思路类似。
4. fgets
5. 我放弃。

## string format
6. printf(passwd)， 把用户输入的直接输出。如果用户输入特殊字符，会暴露内存。
7. %x, 左边补0的话加一个格式化语法 %08x
8. %s越多越好
9. 往trigger暴露的地址里面写值，用%x和%n配合。看代码可以发现在栈里有trigger和其指针t。然而写入的数据不在栈里，所以不能用tutorial教的办法操作。然而栈里有trigger的地址，所以思路就是找到那个地址然后操作。用%x剔除掉挡在前面的地址，然后当%n指向那个地址的时候，控制前面的数据数量来使其长度为84(Dec)是T的ascii。
10. hard code， 不要用%n， 检查用户输入。