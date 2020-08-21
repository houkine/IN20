# IFN657 Tutorial 2 Buffer Overflow Part 1

## 正题
+ 测试ASLR
1. 查看ASLR是否打开    
    ![check gcc,gdb](../images/tutorial4_image1.png)  
2. 准备测试用C程序  
    ![check gcc,gdb](../images/tutorial4_image2.png)  
3. 运行C程序  
    ![check gcc,gdb](../images/tutorial4_image3.png)  
4. 关闭ASLR  
    ![check gcc,gdb](../images/tutorial4_image4.png)  
5. 再次执行C程序
    ![check gcc,gdb](../images/tutorial4_image5.png)  

+ 测试危险C程序
1. 代码  
    ![check gcc,gdb](../images/tutorial4_image6.png)
2. 执行  
    ![check gcc,gdb](../images/tutorial4_image7.png)

+ python
1. 安装python  
    ![check gcc,gdb](../images/tutorial4_image8.png)
2. 代码  
    ![check gcc,gdb](../images/tutorial4_image9.png)
3. 查看运行结果并保存  
    ![check gcc,gdb](../images/tutorial4_image10.png)
4. gdb调试  
    ![check gcc,gdb](../images/tutorial4_image11.png)