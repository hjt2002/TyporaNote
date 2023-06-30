# Shell编程基础

## linux介绍：

进程process：一个正在执行中的程序 带有唯一标识符ID PID

文件file：数据的集合 在文件系统中存在路径 用'/'分隔

目录directory：文件的特殊形式 用来保存其他文件类型

符号链接symbolic link：在文件系统中指向另外一个文件

## Shells的种类

sh、ksh、bash、zsh

## shell的使用

```bash
<command> <options> <arguments>
```

### 变量

定义变量

${var_name} ({}是可选的) 在定义变量时不能使用空格 

环境变量

\$SHELL   $PATH

系统变量

$$	$?	$1

一些典型的命令

```bash
cat <filename> #显示文件内容
date #显示系统时间
ps #列出当前正在运行的进程
```

### 目录导航

```bash
cd <directory name> #导航命令
/ #root directory
~ #home directory
pwd #显示当前目录
ls #列出当前目录所有的文件/列出指定路径目录下的文件
	# 参数
	ls -a #显示所有文件(包括dot文件)
    ls -l #显示long format（包含detailed info）
```

### 文件和目录操作

![image-20230510202933553](./assets/image-20230510202933553.png)

![image-20230510203031702](./assets/image-20230510203031702.png)

```bash
alias #列出命令别名
```

## 输入输出

![image-20230510203809705](./assets/image-20230510203809705.png)

可以使用'>' or '<'来重定向redirect

### 输出重定向

符号 >	从一个程序中保存输出结果到一个文件中

![image-20230510204010749](./assets/image-20230510204010749.png)

### 错误重定向

stdout和stderr都是将screen作为默认的输出目标位置

使用符号**'2>'**

![image-20230510204405868](./assets/image-20230510204405868.png)

符号差别 **>**在原文件末尾覆盖 	和 	**>>**在原文件末尾追加

### 输入重定向

符号 < 从文件中读取输入

```bash
 cat > inputfile < source_file
```

**<<** 	☞在键入（输入）某个标志[symbol]后输入流结束

```bash
cat > inputfile << EOF
```

## 文件权限

linux is a multi-user environment

对每个文件，它的权限被设置为 User(owner)	Group	Other(everyone)

-l命令可以显示文件权限

对每个组可以有rwx三种访问方式access mode

用10bits来表示文件权限:1-3-3-3	"type"-User-Group-Others

使用chmod来改变文件权限

![image-20230510205708576](./assets/image-20230510205708576.png)

### chmod

```bash
chmod: [ref][operator][modes] file
ref: 'u' for user, 'g' for group, 'o' for others, 'a' for all
operator:'+' to add, '-' to move,'=' to set
mode:'r' for read,'w' for write,'x' for execute

```

![image-20230510205956791](./assets/image-20230510205956791.png)

数字模式![image-20230510210029400](./assets/image-20230510210029400.png)

## 符号链接

符号链接是一种特殊的文件形式可以指向一个其他的文件

![image-20230510210132377](./assets/image-20230510210132377.png)

### 硬链接

具体的物理数据位置

当源文件改变（移动或删除）时，硬链接也改变

### 软连接 

类似于Windows的快捷方式

当源文件改变（移动或删除位置）时，软连接不更新

## 特殊权限

![image-20230510210850115](./assets/image-20230510210850115.png)

## Job

![image-20230510210921844](./assets/image-20230510210921844.png)

![image-20230510210940643](./assets/image-20230510210940643.png)

![image-20230510210947641](./assets/image-20230510210947641.png)

## 管道

和重定向相似 链接不同命令的输入和输出

```bash
ls -l | grep "^d"
```

![image-20230511192639218](./assets/image-20230511192639218.png)

## tar 

​	使用tar命令来创建/解压压缩包

![image-20230511193014366](./assets/image-20230511193014366.png)

![image-20230511193030273](./assets/image-20230511193030273.png)

## wget

![image-20230511193225034](./assets/image-20230511193225034.png)

## rpm yum

rpm: Redhat package manager

yum: Yellowdog Updater Modified

## apt-get

自动更新包的版本

## Vim

## Shell编程

### 特殊字符

& * ? [] <> | () ` # $ = '' "" {} ; \

不能将这些字符用于文件/字符命名

### 变量

系统变量：\$# \$0 \$1 \$n \$* \$@ \$? \$$

环境变量：HOME PATH LOGNAME TERM

自定义的变量对于其它程序是不可见的，需要使用`export`命令来将其添加到linux环境中

用户定义的变量

![image-20230511194322280](./assets/image-20230511194322280.png)

### 引用Quotes

shell scripts有三种引用

![image-20230511194437200](./assets/image-20230511194437200.png)

#### 单引用

![image-20230511194533782](./assets/image-20230511194533782.png)

```bash
echo 'The total is nearly $750'
```

#### 双引用

![image-20230511194649652](./assets/image-20230511194649652.png)

```bash
echo "$LOGNAME made \$1000 in `date+%B`"
output: 'logname made $1000 in march'
```

#### 反引号Back quotes

![image-20230511195016060](./assets/image-20230511195016060.png)

### 条件命令执行

![image-20230511195316604](./assets/image-20230511195316604.png)

#### if else语句

![image-20230511195524376](./assets/image-20230511195524376.png)

![image-20230511195614084](./assets/image-20230511195614084.png)

elif

![image-20230511195630773](./assets/image-20230511195630773.png)

#### case

![image-20230511200751080](./assets/image-20230511200751080.png)

#### 条件操作符

```bash
-eq: equal
-ne: not equal
-lt: less than
-gt: greater than
-le: less and equal
-ge: greater and equal
-a -o !: and or not
```

条件选项

![image-20230511195856721](./assets/image-20230511195856721.png)

### 默认值

### set命令

![image-20230511195959547](./assets/image-20230511195959547.png)

### 临时文件

![image-20230511200037564](./assets/image-20230511200037564.png)

### test

![image-20230511200204172](./assets/image-20230511200204172.png)

![image-20230511200518253](./assets/image-20230511200518253.png)

### read命令

![image-20230511200828102](./assets/image-20230511200828102.png)

### while loop

![image-20230511200915593](./assets/image-20230511200915593.png)

break/continue语句

![image-20230511201019552](./assets/image-20230511201019552.png)

### until

![image-20230511201131999](./assets/image-20230511201131999.png)

### select

![image-20230511201213746](./assets/image-20230511201213746.png)

### for

![image-20230511201249226](./assets/image-20230511201249226.png)

for循环的默认迭代列表

![image-20230511201336476](./assets/image-20230511201336476.png)

数字迭代

![image-20230511201358036](./assets/image-20230511201358036.png)

### 数值计算

\+ 	\- 	\*	/ 	%

### 函数

![image-20230511201643445](./assets/image-20230511201643445.png)

可以通过命令行来传递参数

```bash
#函数定义
backup_one_file()
{
	cp $1 $backupdir
	echo $1 has been backed up
}
#函数调用
backup_one_file report.txt
```

函数返回值

![image-20230511201945311](./assets/image-20230511201945311.png)

### 截取变量的部分值

![image-20230511202052275](./assets/image-20230511202052275.png)

操作字符串

```bash
${#string} # 给出字符串长度
${string:position} # 从Posistion处截取字串
${string:position:length} # 截取长度为length的字串
```

### 数组变量

![image-20230511202353364](./assets/image-20230511202353364.png)

# 正则表达式

Regular Expressions are sets of characters and meta characters that match patterns.

一个正则表达式包含如下内容：

character set

anchor

modifiers

## 正则通配符

![image-20230511203254940](./assets/image-20230511203254940.png)

## 正则的格式

![image-20230511203339686](./assets/image-20230511203339686.png)

一个标准的正则表达式

```bash
[character]{times}[character]{times}...
```

![image-20230511203535891](./assets/image-20230511203535891.png)

![image-20230511203602772](./assets/image-20230511203602772.png)

## 正则中的字符

![image-20230511203749899](./assets/image-20230511203749899.png)

#### 特殊字符

```bash
^ # 匹配行首
$ # 匹配行尾
\b # 匹配一个单词的边界位置
\B # 匹配任何一个不是单词边界的位置
```

![image-20230511204004997](./assets/image-20230511204004997.png)

![image-20230511204057014](./assets/image-20230511204057014.png)

```bash
*	# 任何一个重复字符 
?	# 零个或一个字符
+	# 一个或多个字符
```

#### {}

```bash
{n}	# ☞对应的正则表达式重复n次 n>=0
{n,} # 指对应的正则表达式至少重复n次
{n,m} # 指对应的正则表达式至少重复n次，至多m次
```

![image-20230511205748025](./assets/image-20230511205748025.png)

#### Group ()

![image-20230511205838175](./assets/image-20230511205838175.png)

![image-20230511210811214](./assets/image-20230511210811214.png)

![image-20230511210828231](./assets/image-20230511210828231.png)

![image-20230511210846741](./assets/image-20230511210846741.png)

正则匹配规则是贪心匹配

## gerp

![image-20230511211217647](./assets/image-20230511211217647.png)

egrep

![image-20230511211232887](./assets/image-20230511211232887.png)

## sed

![image-20230511211253143](./assets/image-20230511211253143.png)

![image-20230511211311489](./assets/image-20230511211311489.png)

![image-20230511211843504](./assets/image-20230511211843504.png)

## awk

![image-20230511211938384](./assets/image-20230511211938384.png)

![image-20230511212002800](./assets/image-20230511212002800.png)



# GCC Makefile的使用

## gcc 编译过程

1. pre-processing:handling the '#' lines 预处理 ![image-20230510191809694](./assets/image-20230510191809694.png)
2. compile:spell check and syntax analyze 词法/语法检查![image-20230510191818822](./assets/image-20230510191818822.png)
3. assemble:create binary '.o' file 编译![image-20230510191826031](./assets/image-20230510191826031.png)
4. link:combine the target files,lib files to create binary executable file 链接![image-20230510191840067](./assets/image-20230510191840067.png)

## Makefile

命名：GNUmakefile makefile Makefile (如同时存在三种命名，采取优先级为从左（优先）到右)

语法：[format]

```bash
target name:prerequisites names
[tab]commands

[example:]
main:main.o stack.o maze.o
	gcc main.o stack.o maze.o -o main
```

![image-20230510191007492](./assets/image-20230510191007492.png)















