## shell 脚本面试题
* shell脚本是什么，它是必需的吗？

```makrdown
答:一个Shell脚本是一个文本文件，包含一个或多个命令。作为系统管理员，我们经常需要使用多个命令来完成一项任务，我们可以添加这些所有命令在一个文本文件(Shell脚本)来完成这些日常工作任务。
```
* 什么是默认登录shell，如何改变指定用户的登录shell

```makrdown
答:在Linux操作系统，“/bin/bash”是默认登录shell，是在创建用户时分配的。使用chsh命令可以改变默认的shell
```
* 可以在shell脚本中使用哪些类型的变量?

```markdown
答：在shell脚本，我们可以使用两种类型的变量：

系统定义变量
用户定义变量

系统变量是由系统系统自己创建的。这些变量通常由大写字母组成，可以通过“set”命令查看。

用户变量由系统用户来生成和定义，变量的值可以通过命令“echo $<变量名>”查看。
```
* 如何将标准输出和错误输出同时重定向到同一位置?

```bash
2>&1 (ls /home/lawrence/a.txt > oo.txt 2 >&1)

or
&> (ls /home/lawrence/a.txt &>oo.txt)

```
*  shell脚本中“if”语法如何嵌套?

```bash
if [ condition ]; then
    command1
    command2
else
     if  [ condition ]; then
         command1
         command2
     else
         command1
         command2
      fi
      
fi
    
```

* shell脚本中“$?”标记的用途是什么？

```markdown
答：在写一个shell脚本时，如果你想要检查前一命令是否执行成功，在if条件中使用“$?”可以来检查前一命令的结束状态。简单的例子如下：
```
```bash
[lawrence@edu github_com]$ ls
DevOps  Golang  Linux  Python
[lawrence@edu github_com]$ echo $?
0
# 如果结束状态不是0，说明命令执行失败
```
* 在shell脚本中如何比较两个数字 ?

```bash
# 答：在if-then中使用测试命令（ -gt 等）来比较两个数字，例子如下：

#!/bin/bash
n=10
m=20
if [ $n  -gt $m ]; then
    echo "n is gt m"
 else
     echo "n is lt m"
fi
```
* shell脚本中break命令的作用 ?

```markdown
答：break命令一个简单的用途是退出执行中的循环。我们可以在while和until循环中使用break命令跳出循环。
```
* shell脚本中continue命令的作用 ?

```markdown
答：continue命令不同于break命令，它只跳出当前循环的迭代，而不是整个循环。continue命令很多时候是很有用的，例如错误发生，但我们依然希望继续执行大循环的时候
```
*  告诉我shell脚本中Case语句的语法 ?

```bash
case $1 in
    start|Start)
        command1
        command2
        ;;
    stop|Stop)
           command1
           command2
           ;;
     restart)
         command1
         command2
         ;;
 esac
```
* shell脚本中while循环语法 ?

```markdown
答：如同for循环，while循环只要条件成立就重复它的命令块。不同于for循环，while循环会不断迭代，直到它的条件不为真。基础语法：
```
```bash
while [ condition ]; do
    command1
    command2
 done
```
* 如何使脚本可执行 ?

```markdown
答：使用chmod命令来使脚本可执行。例子如下：
```
```bash
chmod  a+x /home/lawrence/test.sh
chmod 755 /home/lawrence/test.sh
```
*  “#!/bin/bash”的作用 ?

```markdown
答：#!/bin/bash是shell脚本的第一行，称为jie释器。这里#符号叫做bash，而! 叫做 bash。它的意思是命令通过 /bin/bash 来执行。
```
* shell脚本中for循环语法 ?

```markdown
答：for循环的基础语法：
```
```bash
for  var in list
do
     command1
     command2
done
```
* 如何调试shell脚本 ?

```markdown
答：使用'-x'参数（sh -x /home/lawrence/test.sh）可以调试shell脚本。另一个种方法是使用‘-nv’参数( sh -nv /home/lawrence/test.sh)
```
* shell脚本如何比较字符串?

```markdown
答：test命令可以用来比较字符串。测试命令会通过比较字符串中的每一个字符来比较。
```
* Bourne shell(bash) 中有哪些特殊的变量 ?

```markdown
答：下面的表列出了Bourne shell为命令行设置的特殊变量。
````
```bash
内建变量    解释
$0     命令行中的脚本名字
$1     第一个命令行参数
$2     第二个命令行参数
$9     第九个命令行参数
${10}  第十个命令行参数
$#     命令行参数的数量
$@     所有参数列表。如”$@”用「”」括起来的情况、以”$1” “$2” … “$n” 的形式输出所有参数。

$?    最后运行的命令的结束代码（返回值）
$$    Shell本身的PID（ProcessID）
$!    Shell最后运行的后台Process的PID 
$*    所有命令行参数，以空格隔开
```
* 在shell脚本中，如何测试文件 ?

```markdown
答：test命令可以用来测试文件。基础用法如下表格：

Test         用法
-d 文件名    如果文件存在并且是目录，返回true
-e 文件名    如果文件存在，返回true
-f 文件名    如果文件存在并且是普通文件，返回true
-r 文件名    如果文件存在并可读，返回true
-s 文件名    如果文件存在并且不为空，返回true
-w 文件名    如果文件存在并可写，返回true
-x 文件名    如果文件存在并可执行，返回true
```
* 在shell脚本中，如何写入注释 ?

```markdown
答：注释可以用来描述一个脚本可以做什么和它是如何工作的。每一行注释以#开头
```
```bash
#!/bin/bash
# this is a command
echo "$USER $UID"
```
* 如何让 shell 就脚本得到来自终端的输入?

```markdown
答：read命令可以读取来自终端（使用键盘）的数据。read命令得到用户的输入并置于你给出的变量中。例子如下：
```
```bash
#!/bin/bash
echo "Please enter your name"
read name
echo "My Name is $name"
```
* 如何取消变量或取消变量赋值 ?

```markdown
答：“unset”命令用于取消变量或取消变量赋值。语法如下所示：
```
```bash
unset <变量名>
```
* 如何执行算术运算 ?

```bash
$ expr 45 + 34
t=$[ 12 + 45 ]
echo $t
```
* do-while语句的基本格式 ?

```markdown
答：do-while语句类似于while语句，但检查条件语句之前先执行命令（LCTT 译注：意即至少执行一次。）。下面是用do-while语句的语法
```
```bash
do
{
command1
}while (condition)
```
* 在shell脚本如何定义函数呢 ?

```markdown
答：函数是拥有名字的代码块。当我们定义代码块，我们就可以在我们的脚本调用函数名字，该块就会被执行。示例如下所示：
```
```bash
[ function ] 函数名 [()]
{
命令;
[return int;]
}
```
