# GCC Makefile的使用

## gcc 编译过程

1. pre-processing:handling the '#' lines 预处理 ![image-20230510191809694](./assets/image-20230510191809694.png)
2. compile:spell check and syntax analyze 词法/语法检查![image-20230510191818822](./assets/image-20230510191818822.png)
3. assemble:create binary '.o' file 编译![image-20230510191826031](./assets/image-20230510191826031.png)
4. link:combine the target files,lib files to create binary executable file 链接![image-20230510191840067](./assets/image-20230510191840067.png)

## Makefile

命名：GNUmakefile makefile Makefile (如同时存在三种命名，采取优先级为从左（优先）到右)

语法：[format]

```c
target name:prerequisites names
[tab]commands

[example:]
main:main.o stack.o maze.o
	gcc main.o stack.o maze.o -o main
```

![image-20230510191007492](./assets/image-20230510191007492.png)