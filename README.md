
[BASH](#bash)

[VIM](#vim)

# bash
```bash
##############################################################################
by https://github.com/skywind3000/awesome-cheatsheets
# 常用快捷键（默认使用 Emacs 键位）
##############################################################################

CTRL+A              # 移动到行首，同 <Home>
CTRL+B              # 向后移动，同 <Left>
CTRL+C              # 结束当前命令
CTRL+D              # 删除光标前的字符，同 <Delete> ，或者没有内容时，退出会话
CTRL+E              # 移动到行末，同 <End>
CTRL+F              # 向前移动，同 <Right>
CTRL+G              # 退出当前编辑（比如正在 CTRL+R 搜索历史时）
CTRL+H              # 删除光标左边的字符，同 <Backspace>
CTRL+K              # 删除光标位置到行末的内容
CTRL+L              # 清屏并重新显示
CTRL+N              # 移动到命令历史的下一行，同 <Down>
CTRL+O              # 类似回车，但是会显示下一行历史
CTRL+P              # 移动到命令历史的上一行，同 <Up>
CTRL+R              # 历史命令反向搜索，使用 CTRL+G 退出搜索
CTRL+S              # 历史命令正向搜索，使用 CTRL+G 退出搜索
CTRL+T              # 交换前后两个字符
CTRL+U              # 删除字符到行首
CTRL+V              # 输入字符字面量，先按 CTRL+V 再按任意键
CTRL+W              # 删除光标左边的一个单词
CTRL+X              # 列出可能的补全
CTRL+Y              # 粘贴前面 CTRL+u/k/w 删除过的内容
CTRL+Z              # 暂停前台进程返回 bash，需要时可用 fg 将其切换回前台
CTRL+_              # 撤销（undo），有的终端将 CTRL+_ 映射为 CTRL+/ 或 CTRL+7

ALT+b               # 向后（左边）移动一个单词
ALT+d               # 删除光标后（右边）一个单词
ALT+f               # 向前（右边）移动一个单词
ALT+t               # 交换字符
ALT+BACKSPACE       # 删除光标前面一个单词，类似 CTRL+W，但不影响剪贴板

CTRL+X CTRL+X       # 连续按两次 CTRL+X，光标在当前位置和行首来回跳转 
CTRL+X CTRL+E       # 用你指定的编辑器，编辑当前命令


##############################################################################
# BASH 基本操作
##############################################################################

exit                # 退出当前登陆
env                 # 显示环境变量
echo $SHELL         # 显示你在使用什么 SHELL

bash                # 使用 bash，用 exit 返回
which bash          # 搜索 $PATH，查找哪个程序对应命令 bash
whereis bash        # 搜索可执行，头文件和帮助信息的位置，使用系统内建数据库
whatis bash         # 查看某个命令的解释，一句话告诉你这是干什么的

clear               # 清初屏幕内容
reset               # 重置终端（当你不小心 cat 了一个二进制，终端状态乱掉时使用）


##############################################################################
# 目录操作
##############################################################################

cd                  # 返回自己 $HOME 目录
cd {dirname}        # 进入目录
pwd                 # 显示当前所在目录
mkdir {dirname}     # 创建目录
mkdir -p {dirname}  # 递归创建目录
pushd {dirname}     # 目录压栈并进入新目录
popd                # 弹出并进入栈顶的目录
dirs -v             # 列出当前目录栈
cd -                # 回到之前的目录
cd -{N}             # 切换到目录栈中的第 N个目录，比如 cd -2 将切换到第二个


##############################################################################
# 文件操作
##############################################################################

ls                  # 显示当前目录内容，后面可接目录名：ls {dir} 显示指定目录
ls -l               # 列表方式显示目录内容，包括文件日期，大小，权限等信息
ls -1               # 列表方式显示目录内容，只显示文件名称，减号后面是数字 1
ls -a               # 显示所有文件和目录，包括隐藏文件（.开头的文件/目录名）
ln -s {fn} {link}   # 给指定文件创建一个软链接
cp {src} {dest}     # 拷贝文件，cp -r dir1 dir2 可以递归拷贝（目录）
rm {fn}             # 删除文件，rm -r 递归删除目录，rm -f 强制删除
mv {src} {dest}     # 移动文件，如果 dest 是目录，则移动，是文件名则覆盖
touch {fn}          # 创建或者更新一下制定文件
cat {fn}            # 输出文件原始内容
any_cmd > {fn}      # 执行任意命令并将标准输出重定向到指定文件
more {fn}           # 逐屏显示某文件内容，空格翻页，q 退出
less {fn}           # 更高级点的 more，更多操作，q 退出
head {fn}           # 显示文件头部数行，可用 head -3 abc.txt 显示头三行
tail {fn}           # 显示文件尾部数行，可用 tail -3 abc.txt 显示尾部三行
tail -f {fn}        # 持续显示文件尾部数据，可用于监控日志
nano {fn}           # 使用 nano 编辑器编辑文件
vim {fn}            # 使用 vim 编辑文件
diff {f1} {f2}      # 比较两个文件的内容
wc {fn}             # 统计文件有多少行，多少个单词
chmod 644 {fn}      # 修改文件权限为 644，可以接 -R 对目录循环改权限
chgrp group {fn}    # 修改文件所属的用户组
chown user1 {fn}    # 修改文件所有人为 user1, chown user1:group1 fn 可以修改组
file {fn}           # 检测文件的类型和编码
basename {fn}       # 查看文件的名字（不包括路径）
dirname {fn}        # 查看文件的路径（不包括名字）
grep {pat} {fn}     # 在文件中查找出现过 pat 的内容
grep -r {pat} .     # 在当前目录下递归查找所有出现过 pat 的文件内容
stat {fn}           # 显示文件的详细信息


##############################################################################
# 用户管理
##############################################################################

whoami              # 显示我的用户名
who                 # 显示已登陆用户信息，w / who / users 内容略有不同
w                   # 显示已登陆用户信息，w / who / users 内容略有不同
users               # 显示已登陆用户信息，w / who / users 内容略有不同
passwd              # 修改密码，passwd {user} 可以用于 root 修改别人密码
finger {user}       # 显示某用户信息，包括 id, 名字, 登陆状态等
adduser {user}      # 添加用户
deluser {user}      # 删除用户
w                   # 查看谁在线
su                  # 切换到 root 用户
su -                # 切换到 root 用户并登陆（执行登陆脚本）
su {user}           # 切换到某用户
su -{user}          # 切换到某用户并登陆（执行登陆脚本）
id {user}           # 查看用户的 uid，gid 以及所属其他用户组
id -u {user}        # 打印用户 uid
id -g {user}        # 打印用户 gid
write {user}        # 向某用户发送一句消息
last                # 显示最近用户登陆列表
last {user}         # 显示登陆记录
lastb               # 显示失败登陆记录
lastlog             # 显示所有用户的最近登陆记录
sudo {command}      # 以 root 权限执行某命令


##############################################################################
# 进程管理
##############################################################################

ps                        # 查看当前会话进程
ps ax                     # 查看所有进程，类似 ps -e
ps aux                    # 查看所有进程详细信息，类似 ps -ef
ps auxww                  # 查看所有进程，并且显示进程的完整启动命令
ps -u {user}              # 查看某用户进程
ps axjf                   # 列出进程树
ps xjf -u {user}          # 列出某用户的进程树
ps -eo pid,user,command   # 按用户指定的格式查看进程
ps aux | grep httpd       # 查看名为 httpd 的所有进程
ps --ppid {pid}           # 查看父进程为 pid 的所有进程
pstree                    # 树形列出所有进程，pstree 默认一般不带，需安装
pstree {user}             # 进程树列出某用户的进程
pstree -u                 # 树形列出所有进程以及所属用户
pgrep {procname}          # 搜索名字匹配的进程的 pid，比如 pgrep apache2

kill {pid}                # 结束进程
kill -9 {pid}             # 强制结束进程，9/SIGKILL 是强制不可捕获结束信号
kill -KILL {pid}          # 强制执行进程，kill -9 的另外一种写法
kill -l                   # 查看所有信号
kill -l TERM              # 查看 TERM 信号的编号
killall {procname}        # 按名称结束所有进程
pkill {procname}          # 按名称结束进程，除名称外还可以有其他参数

top                       # 查看最活跃的进程
top -u {user}             # 查看某用户最活跃的进程

any_command &             # 在后台运行某命令，也可用 CTRL+Z 将当前进程挂到后台
jobs                      # 查看所有后台进程（jobs）
bg                        # 查看后台进程，并切换过去
fg                        # 切换后台进程到前台
fg {job}                  # 切换特定后台进程到前台

trap cmd sig1 sig2        # 在脚本中设置信号处理命令
trap "" sig1 sig2         # 在脚本中屏蔽某信号
trap - sig1 sig2          # 恢复默认信号处理行为

nohup {command}           # 长期运行某程序，在你退出登陆都保持它运行
nohup {command} &         # 在后台长期运行某程序
disown {PID|JID}          # 将进程从后台任务列表（jobs）移除

wait                      # 等待所有后台进程任务结束


##############################################################################
# 常用命令：SSH / 系统信息 / 网络
##############################################################################

ssh user@host             # 以用户 user 登陆到远程主机 host
ssh -p {port} user@host   # 指定端口登陆主机
ssh-copy-id user@host     # 拷贝你的 ssh key 到远程主机，避免重复输入密码
scp {fn} user@host:path   # 拷贝文件到远程主机
scp user@host:path dest   # 从远程主机拷贝文件回来
scp -P {port} ...         # 指定端口远程拷贝文件

uname -a                  # 查看内核版本等信息
man {help}                # 查看帮助
man -k {keyword}          # 查看哪些帮助文档里包含了该关键字
info {help}               # 查看 info pages，比 man 更强的帮助系统
uptime                    # 查看系统启动时间
date                      # 显示日期
cal                       # 显示日历
vmstat                    # 显示内存和 CPU 使用情况
vmstat 10                 # 每 10 秒打印一行内存和 CPU情况，CTRL+C 退出
free                      # 显示内存和交换区使用情况
df                        # 显示磁盘使用情况
du                        # 显示当前目录占用，du . --max-depth=2 可以指定深度
uname                     # 显示系统版本号
hostname                  # 显示主机名称
showkey -a                # 查看终端发送的按键编码

ping {host}               # ping 远程主机并显示结果，CTRL+C 退出
ping -c N {host}          # ping 远程主机 N 次
traceroute {host}         # 侦测路由连通情况
mtr {host}                # 高级版本 traceroute
host {domain}             # DNS 查询，{domain} 前面可加 -a 查看详细信息
whois {domain}            # 取得域名 whois 信息
dig {domain}              # 取得域名 dns 信息
route -n                  # 查看路由表
netstat -a                # 列出所有端口
netstat -an               # 查看所有连接信息，不解析域名
netstat -anp              # 查看所有连接信息，包含进程信息（需要 sudo）
netstat -l                # 查看所有监听的端口
netstat -t                # 查看所有 TCP 链接
netstat -lntu             # 显示所有正在监听的 TCP 和 UDP 信息
netstat -lntup            # 显示所有正在监听的 socket 及进程信息
netstat -i                # 显示网卡信息
netstat -rn               # 显示当前系统路由表，同 route -n
ss -an                    # 比 netstat -an 更快速更详细
ss -s                     # 统计 TCP 的 established, wait 等

wget {url}                # 下载文件，可加 --no-check-certificate 忽略 ssl 验证
wget -qO- {url}           # 下载文件并输出到标准输出（不保存）
curl -sL {url}            # 同 wget -qO- {url} 没有 wget 的时候使用

sz {file}                 # 发送文件到终端，zmodem 协议
rz                        # 接收终端发送过来的文件


##############################################################################
# 变量操作
##############################################################################

varname=value             # 定义变量
varname=value command     # 定义子进程变量并执行子进程
echo $varname             # 查看变量内容
echo $$                   # 查看当前 shell 的进程号
echo $!                   # 查看最近调用的后台任务进程号
echo $?                   # 查看最近一条命令的返回码
export VARNAME=value      # 设置环境变量（将会影响到子进程）

array[0]=valA             # 定义数组
array[1]=valB
array[2]=valC
array=([0]=valA [1]=valB [2]=valC)   # 另一种方式
array=(valA valB valC)               # 另一种方式

${array[i]}               # 取得数组中的元素
${#array[@]}              # 取得数组的长度
${#array[i]}              # 取得数组中某个变量的长度

declare -a                # 查看所有数组
declare -f                # 查看所有函数
declare -F                # 查看所有函数，仅显示函数名
declare -i                # 查看所有整数
declare -r                # 查看所有只读变量
declare -x                # 查看所有被导出成环境变量的东西
declare -p varname        # 输出变量是怎么定义的（类型+值）

${varname:-word}          # 如果变量不为空则返回变量，否则返回 word
${varname:=word}          # 如果变量不为空则返回变量，否则赋值成 word 并返回
${varname:?message}       # 如果变量不为空则返回变量，否则打印错误信息并退出
${varname:+word}          # 如果变量不为空则返回 word，否则返回 null
${varname:offset:len}     # 取得字符串的子字符串

${variable#pattern}       # 如果变量头部匹配 pattern，则删除最小匹配部分返回剩下的
${variable##pattern}      # 如果变量头部匹配 pattern，则删除最大匹配部分返回剩下的
${variable%pattern}       # 如果变量尾部匹配 pattern，则删除最小匹配部分返回剩下的
${variable%%pattern}      # 如果变量尾部匹配 pattern，则删除最大匹配部分返回剩下的
${variable/pattern/str}   # 将变量中第一个匹配 pattern 的替换成 str，并返回
${variable//pattern/str}  # 将变量中所有匹配 pattern 的地方替换成 str 并返回

${#varname}               # 返回字符串长度

*(patternlist)            # 零次或者多次匹配
+(patternlist)            # 一次或者多次匹配
?(patternlist)            # 零次或者一次匹配
@(patternlist)            # 单词匹配
!(patternlist)            # 不匹配

array=($text)             # 按空格分隔 text 成数组，并赋值给变量
IFS="/" array=($text)     # 按斜杆分隔字符串 text 成数组，并赋值给变量
text="${array[*]}"        # 用空格链接数组并赋值给变量
text=$(IFS=/; echo "${array[*]}")  # 用斜杠链接数组并赋值给变量

A=( foo bar "a  b c" 42 ) # 数组定义
B=("${A[@]:1:2}")         # 数组切片：B=( bar "a  b c" )
C=("${A[@]:1}")           # 数组切片：C=( bar "a  b c" 42 )
echo "${B[@]}"            # bar a  b c
echo "${B[1]}"            # a  b c
echo "${C[@]}"            # bar a  b c 42
echo "${C[@]: -2:2}"      # a  b c 42  减号前的空格是必须的

$(UNIX command)           # 运行命令，并将标准输出内容捕获并返回
varname=$(id -u user)     # 将用户名为 user 的 uid 赋值给 varname 变量

num=$(expr 1 + 2)         # 兼容 posix sh 的计算，使用 expr 命令计算结果
num=$(expr $num + 1)      # 数字自增
expr 2 \* \( 2 + 3 \)     # 兼容 posix sh 的复杂计算，输出 10

num=$((1 + 2))            # 计算 1+2 赋值给 num，使用 bash 独有的 $((..)) 计算
num=$(($num + 1))         # 变量递增
num=$((num + 1))          # 变量递增，双括号内的 $ 可以省略
num=$((1 + (2 + 3) * 2))  # 复杂计算


##############################################################################
# 事件指示符
##############################################################################

!!                  # 上一条命令
!^                  # 上一条命令的第一个单词
!:n                 # 上一条命令的第n个单词
!:n-$               # 上一条命令的第n个单词到最后一个单词
!$                  # 上一条命令的最后一个单词
!-n:$               # 上n条命令的最后一个单词
!string             # 最近一条包含string的命令
!^string1^string2   # 最近一条包含string1的命令, 快速替换string1为string2
!#                  # 本条命令之前所有的输入内容
!#:n                # 本条命令之前的第n个单词, 快速备份cp /etc/passwd !#:1.bak


##############################################################################
# 函数
##############################################################################

# 定义一个新函数
function myfunc() {
    # $1 代表第一个参数，$N 代表第 N 个参数
    # $# 代表参数个数
    # $0 代表被调用者自身的名字
    # $@ 代表所有参数，类型是个数组，想传递所有参数给其他命令用 cmd "$@" 
    # $* 空格链接起来的所有参数，类型是字符串
    {shell commands ...}
}

myfunc                    # 调用函数 myfunc 
myfunc arg1 arg2 arg3     # 带参数的函数调用
myfunc "$@"               # 将所有参数传递给函数
myfunc "${array[@]}"      # 将一个数组当作多个参数传递给函数
shift                     # 参数左移

unset -f myfunc           # 删除函数
declare -f                # 列出函数定义


##############################################################################
# 条件判断（兼容 posix sh 的条件判断）：man test
##############################################################################

statement1 && statement2  # and 操作符
statement1 || statement2  # or 操作符

exp1 -a exp2              # exp1 和 exp2 同时为真时返回真（POSIX XSI扩展）
exp1 -o exp2              # exp1 和 exp2 有一个为真就返回真（POSIX XSI扩展）
( expression )            # 如果 expression 为真时返回真，输入注意括号前反斜杆
! expression              # 如果 expression 为假那返回真

str1 = str2               # 判断字符串相等，如 [ "$x" = "$y" ] && echo yes
str1 != str2              # 判断字符串不等，如 [ "$x" != "$y" ] && echo yes
str1 < str2               # 字符串小于，如 [ "$x" \< "$y" ] && echo yes
str2 > str2               # 字符串大于，注意 < 或 > 是字面量，输入时要加反斜杆
-n str1                   # 判断字符串不为空（长度大于零）
-z str1                   # 判断字符串为空（长度等于零）

-a file                   # 判断文件存在，如 [ -a /tmp/abc ] && echo "exists"
-d file                   # 判断文件存在，且该文件是一个目录
-e file                   # 判断文件存在，和 -a 等价
-f file                   # 判断文件存在，且该文件是一个普通文件（非目录等）
-r file                   # 判断文件存在，且可读
-s file                   # 判断文件存在，且尺寸大于0
-w file                   # 判断文件存在，且可写
-x file                   # 判断文件存在，且执行
-N file                   # 文件上次修改过后还没有读取过
-O file                   # 文件存在且属于当前用户
-G file                   # 文件存在且匹配你的用户组
file1 -nt file2           # 文件1 比 文件2 新
file1 -ot file2           # 文件1 比 文件2 旧

num1 -eq num2             # 数字判断：num1 == num2
num1 -ne num2             # 数字判断：num1 != num2
num1 -lt num2             # 数字判断：num1 < num2
num1 -le num2             # 数字判断：num1 <= num2
num1 -gt num2             # 数字判断：num1 > num2
num1 -ge num2             # 数字判断：num1 >= num2


##############################################################################
# 分支控制：if 和经典 test，兼容 posix sh 的条件判断语句
##############################################################################

test {expression}         # 判断条件为真的话 test 程序返回0 否则非零
[ expression ]            # 判断条件为真的话返回0 否则非零

test "abc" = "def"        # 查看返回值 echo $? 显示 1，因为条件为假
test "abc" != "def"       # 查看返回值 echo $? 显示 0，因为条件为真

test -a /tmp; echo $?     # 调用 test 判断 /tmp 是否存在，并打印 test 的返回值
[ -a /tmp ]; echo $?      # 和上面完全等价，/tmp 肯定是存在的，所以输出是 0

test cond && cmd1         # 判断条件为真时执行 cmd1
[ cond ] && cmd1          # 和上面完全等价
[ cond ] && cmd1 || cmd2  # 条件为真执行 cmd1 否则执行 cmd2

# 判断 /etc/passwd 文件是否存在
# 经典的 if 语句就是判断后面的命令返回值为0的话，认为条件为真，否则为假
if test -e /etc/passwd; then
    echo "alright it exists ... "
else
    echo "it doesn't exist ... "
fi

# 和上面完全等价，[ 是个和 test 一样的可执行程序，但最后一个参数必须为 ]
# 这个名字为 "[" 的可执行程序一般就在 /bin 或 /usr/bin 下面，比 test 优雅些
if [ -e /etc/passwd ]; then   
    echo "alright it exists ... "
else
    echo "it doesn't exist ... "
fi

# 和上面两个完全等价，其实到 bash 时代 [ 已经是内部命令了，用 enable 可以看到
[ -e /etc/passwd ] && echo "alright it exists" || echo "it doesn't exist"

# 判断变量的值
if [ "$varname" = "foo" ]; then
    echo "this is foo"
elif [ "$varname" = "bar" ]; then
    echo "this is bar"
else
    echo "neither"
fi

# 复杂条件判断，注意 || 和 && 是完全兼容 POSIX 的推荐写法
if [ $x -gt 10 ] && [ $x -lt 20 ]; then
    echo "yes, between 10 and 20"
fi

# 可以用 && 命令连接符来做和上面完全等价的事情
[ $x -gt 10 ] && [ $x -lt 20 ] && echo "yes, between 10 and 20"

# 小括号和 -a -o 是 POSIX XSI 扩展写法，小括号是字面量，输入时前面要加反斜杆
if [ \( $x -gt 10 \) -a \( $x -lt 20 \) ]; then
    echo "yes, between 10 and 20"
fi

# 同样可以用 && 命令连接符来做和上面完全等价的事情
[ \( $x -gt 10 \) -a \( $x -lt 20 \) ] && echo "yes, between 10 and 20"


# 判断程序存在的话就执行
[ -x /bin/ls ] && /bin/ls -l

# 如果不考虑兼容 posix sh 和 dash 这些的话，可用 bash 独有的 ((..)) 和 [[..]]:
https://www.ibm.com/developerworks/library/l-bash-test/index.html


##############################################################################
# 流程控制：while / for / case / until 
##############################################################################

# while 循环
while condition; do
    statements
done

i=1
while [ $i -le 10 ]; do
    echo $i; 
    i=$(expr $i + 1)
done

# for 循环：上面的 while 语句等价
for i in {1..10}; do
    echo $i
done

for name [in list]; do
    statements
done

# for 列举某目录下面的所有文件
for f in /home/*; do 
    echo $f
done

# bash 独有的 (( .. )) 语句，更接近 C 语言，但是不兼容 posix sh
for (( initialisation ; ending condition ; update )); do
    statements
done

# 和上面的写法等价
for ((i = 0; i < 10; i++)); do echo $i; done

# case 判断
case expression in 
    pattern1 )
        statements ;;
    pattern2 )
        statements ;;
    * )
        otherwise ;;
esac

# until 语句
until condition; do
    statements
done

# select 语句
select name [in list]; do
  statements that can use $name
done


##############################################################################
# 命令处理
##############################################################################

command ls                         # 忽略 alias 直接执行程序或者内建命令 ls
builtin cd                         # 忽略 alias 直接运行内建的 cd 命令
enable                             # 列出所有 bash 内置命令，或禁止某命令
help {builtin_command}             # 查看内置命令的帮助（仅限 bash 内置命令）

eval $script                       # 对 script 变量中的字符串求值（执行）


##############################################################################
# 输出/输入 重定向
##############################################################################

cmd1 | cmd2                        # 管道，cmd1 的标准输出接到 cmd2 的标准输入
< file                             # 将文件内容重定向为命令的标准输入
> file                             # 将命令的标准输出重定向到文件，会覆盖文件
>> file                            # 将命令的标准输出重定向到文件，追加不覆盖
>| file                            # 强制输出到文件，即便设置过：set -o noclobber
n>| file                           # 强制将文件描述符 n的输出重定向到文件
<> file                            # 同时使用该文件作为标准输入和标准输出
n<> file                           # 同时使用文件作为文件描述符 n 的输出和输入
n> file                            # 重定向文件描述符 n 的输出到文件
n< file                            # 重定向文件描述符 n 的输入为文件内容
n>&                                # 将标准输出 dup/合并 到文件描述符 n
n<&                                # 将标准输入 dump/合并 定向为描述符 n
n>&m                               # 文件描述符 n 被作为描述符 m 的副本，输出用
n<&m                               # 文件描述符 n 被作为描述符 m 的副本，输入用
&>file                             # 将标准输出和标准错误重定向到文件
<&-                                # 关闭标准输入
>&-                                # 关闭标准输出
n>&-                               # 关闭作为输出的文件描述符 n
n<&-                               # 关闭作为输入的文件描述符 n
diff <(cmd1) <(cmd2)               # 比较两个命令的输出


##############################################################################
# 文本处理 - cut
##############################################################################

cut -c 1-16                        # 截取每行头16个字符
cut -c 1-16 file                   # 截取指定文件中每行头 16个字符
cut -c3-                           # 截取每行从第三个字符开始到行末的内容
cut -d':' -f5                      # 截取用冒号分隔的第五列内容
cut -d';' -f2,10                   # 截取用分号分隔的第二和第十列内容
cut -d' ' -f3-7                    # 截取空格分隔的三到七列
echo "hello" | cut -c1-3           # 显示 hel
echo "hello sir" | cut -d' ' -f2   # 显示 sir
ps | tr -s " " | cut -d " " -f 2,3,4  # cut 搭配 tr 压缩字符


##############################################################################
# 文本处理 - awk / sed 
##############################################################################

awk '{print $5}' file              # 打印文件中以空格分隔的第五列
awk -F ',' '{print $5}' file       # 打印文件中以逗号分隔的第五列
awk '/str/ {print $2}' file        # 打印文件中包含 str 的所有行的第二列
awk -F ',' '{print $NF}' file      # 打印逗号分隔的文件中的每行最后一列 
awk '{s+=$1} END {print s}' file   # 计算所有第一列的合
awk 'NR%3==1' file                 # 从第一行开始，每隔三行打印一行

sed 's/find/replace/' file         # 替换文件中首次出现的字符串并输出结果 
sed '10s/find/replace/' file       # 替换文件第 10 行内容
sed '10,20s/find/replace/' file    # 替换文件中 10-20 行内容
sed -r 's/regex/replace/g' file    # 替换文件中所有出现的字符串
sed -i 's/find/replace/g' file     # 替换文件中所有出现的字符并且覆盖文件
sed -i '/find/i\newline' file      # 在文件的匹配文本前插入行
sed -i '/find/a\newline' file      # 在文件的匹配文本后插入行
sed '/line/s/find/replace/' file   # 先搜索行特征再执行替换
sed -e 's/f/r/' -e 's/f/r' file    # 执行多次替换
sed 's#find#replace#' file         # 使用 # 替换 / 来避免 pattern 中有斜杆
sed -i -r 's/^\s+//g' file         # 删除文件每行头部空格
sed '/^$/d' file                   # 删除文件空行并打印
sed -i 's/\s\+$//' file            # 删除文件每行末尾多余空格
sed -n '2p' file                   # 打印文件第二行
sed -n '2,5p' file                 # 打印文件第二到第五行


##############################################################################
# 排序 - sort
##############################################################################

sort file                          # 排序文件
sort -r file                       # 反向排序（降序）
sort -n file                       # 使用数字而不是字符串进行比较
sort -t: -k 3n /etc/passwd         # 按 passwd 文件的第三列进行排序
sort -u file                       # 去重排序


##############################################################################
# 快速跳转 - https://github.com/rupa/z
##############################################################################

source /path/to/z.sh               # .bashrc 中初始化 z.sh
z                                  # 列出所有历史路径以及他们的权重
z foo                              # 跳到历史路径中匹配 foo 的权重最大的目录
z foo bar                          # 跳到历史路径中匹配 foo 和 bar 权重最大的目录
z -l foo                           # 列出所有历史路径中匹配 foo 的目录及权重
z -r foo                           # 按照最高访问次数优先进行匹配跳转
z -t foo                           # 按照最近访问优先进行匹配跳转


##############################################################################
# 键盘绑定
##############################################################################

bind '"\eh":"\C-b"'                # 绑定 ALT+h 为光标左移，同 CTRL+b / <Left>
bind '"\el":"\C-f"'                # 绑定 ALT+l 为光标右移，同 CTRL+f / <Right>
bind '"\ej":"\C-n"'                # 绑定 ALT+j 为下条历史，同 CTRL+n / <Down>
bind '"\ek":"\C-p"'                # 绑定 ALT+k 为上条历史，同 CTRL+p / <Up>
bind '"\eH":"\eb"'                 # 绑定 ALT+H 为光标左移一个单词，同 ALT-b 
bind '"\eL":"\ef"'                 # 绑定 ALT+L 为光标右移一个单词，同 ALT-f 
bind '"\eJ":"\C-a"'                # 绑定 ALT+J 为移动到行首，同 CTRL+a / <Home>
bind '"\eK":"\C-e"'                # 绑定 ALT+K 为移动到行末，同 CTRL+e / <End>
bind '"\e;":"ls -l\n"'             # 绑定 ALT+; 为执行 ls -l 命令


##############################################################################
# 网络管理：ip / ifconfig / nmap ...
##############################################################################

ip a                               # 显示所有网络地址，同 ip address
ip a show eth1                     # 显示网卡 IP 地址
ip a add 172.16.1.23/24 dev eth1   # 添加网卡 IP 地址
ip a del 172.16.1.23/24 dev eth1   # 删除网卡 IP 地址
ip link show dev eth0              # 显示网卡设备属性
ip link set eth1 up                # 激活网卡
ip link set eth1 down              # 关闭网卡
ip link set eth1 address {mac}     # 修改 MAC 地址
ip neighbour                       # 查看 ARP 缓存
ip route                           # 查看路由表
ip route add 10.1.0.0/24 via 10.0.0.253 dev eth0    # 添加静态路由
ip route del 10.1.0.0/24           # 删除静态路由

ifconfig                           # 显示所有网卡和接口信息
ifconfig -a                        # 显示所有网卡（包括开机没启动的）信息
ifconfig eth0                      # 指定设备显示信息
ifconfig eth0 up                   # 激活网卡
ifconfig eth0 down                 # 关闭网卡
ifconfig eth0 192.168.120.56       # 给网卡配置 IP 地址
ifconfig eth0 10.0.0.8 netmask 255.255.255.0 up     # 配置 IP 并启动
ifconfig eth0 hw ether 00:aa:bb:cc:dd:ee            # 修改 MAC 地址

nmap 10.0.0.12                     # 扫描主机 1-1000 端口
nmap -p 1024-65535 10.0.0.12       # 扫描给定端口
nmap 10.0.0.0/24                   # 给定网段扫描局域网内所有主机
nmap -O -sV 10.0.0.12              # 探测主机服务和操作系统版本


##############################################################################
# 有趣的命令
##############################################################################

man hier                           # 查看文件系统的结构和含义
man test                           # 查看 posix sh 的条件判断帮助
man ascii                          # 显示 ascii 表
getconf LONG_BIT                   # 查看系统是 32 位还是 64 位
bind -P                            # 列出所有 bash 的快捷键
mount | column -t                  # 漂亮的列出当前加载的文件系统
curl ip.cn                         # 取得外网 ip 地址和服务商信息
disown -a && exit                  # 关闭所有后台任务并退出
cat /etc/issue                     # 查看 Linux 发行版信息
lsof -i port:80                    # 哪个程序在使用 80 端口？
showkey -a                         # 取得按键的 ASCII 码
svn diff | view -                  # 使用 Vim 来显示带色彩的 diff 输出
mv filename.{old,new}              # 快速文件改名
time read                          # 使用 CTRL-D 停止，最简单的计时功能
cp file.txt{,.bak}                 # 快速备份文件
sudo touch /forcefsck              # 强制在下次重启时扫描磁盘
find ~ -mmin 60 -type f            # 查找 $HOME 目录中，60 分钟内修改过的文件
curl wttr.in/~beijing              # 查看北京的天气预报
echo ${SSH_CLIENT%% *}             # 取得你是从什么 IP 链接到当前主机上的
echo $[RANDOM%X+1]                 # 取得 1 到 X 之间的随机数
bind -x '"\C-l":ls -l'             # 设置 CTRL+l 为执行 ls -l 命令
find / -type f -size +5M           # 查找大于 5M 的文件
chmod --reference f1 f2            # 将 f2 的权限设置成 f1 一模一样的
curl -L cheat.sh                   # 速查表大全


##############################################################################
# 常用技巧
##############################################################################

# 列出最常使用的命令
history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head

# 列出所有网络状态：ESTABLISHED / TIME_WAIT / FIN_WAIT1 / FIN_WAIT2 
netstat -n | awk '/^tcp/ {++tt[$NF]} END {for (a in tt) print a, tt[a]}'

# 通过 SSH 来 mount 文件系统
sshfs name@server:/path/to/folder /path/to/mount/point

# 显示前十个运行的进程并按内存使用量排序
ps aux | sort -nk +4 | tail

# 在右上角显示时钟
while sleep 1;do tput sc;tput cup 0 $(($(tput cols)-29));date;tput rc;done&

# 从网络上的压缩文件中解出一个文件来，并避免保存中间文件
wget -qO - "http://www.tarball.com/tarball.gz" | tar zxvf -

# 性能测试：测试处理器性能
python -c "import test.pystone;print(test.pystone.pystones())"

# 性能测试：测试内存带宽
dd if=/dev/zero of=/dev/null bs=1M count=32768

# Linux 下挂载一个 iso 文件
mount /path/to/file.iso /mnt/cdrom -oloop

# 通过主机 A 直接 ssh 到主机 B
ssh -t hostA ssh hostB

# 下载一个网站的所有图片
wget -r -l1 --no-parent -nH -nd -P/tmp -A".gif,.jpg" http://example.com/images

# 快速创建项目目录
mkdir -p work/{project1,project2}/{src,bin,bak}

# 按日期范围查找文件
find . -type f -newermt "2010-01-01" ! -newermt "2010-06-01"

# 显示当前正在使用网络的进程
lsof -P -i -n | cut -f 1 -d " "| uniq | tail -n +2

# Vim 中保存一个没有权限的文件
:w !sudo tee > /dev/null %

# 在 .bashrc / .bash_profile 中加载另外一个文件（比如你保存在 github 上的配置）
source ~/github/profiles/my_bash_init.sh

# 反向代理：将外网主机（202.115.8.1）端口（8443）转发到内网主机 192.168.1.2:443
ssh -CqTnN -R 0.0.0.0:8443:192.168.1.2:443  user@202.115.8.1

# 正向代理：将本地主机的 8443 端口，通过 192.168.1.3 转发到 192.168.1.2:443 
ssh -CqTnN -L 0.0.0.0:8443:192.168.1.2:443  user@192.168.1.3

# socks5 代理：把本地 1080 端口的 socks5 的代理请求通过远程主机转发出去
ssh -CqTnN -D localhost:1080  user@202.115.8.1

# 终端下正确设置 ALT 键和 BackSpace 键
http://www.skywind.me/blog/archives/2021


##############################################################################
# 有用的函数
##############################################################################

# 自动解压：判断文件后缀名并调用相应解压命令
function q-extract() {
    if [ -f $1 ] ; then
        case $1 in
        *.tar.bz2)   tar -xvjf $1    ;;
        *.tar.gz)    tar -xvzf $1    ;;
        *.tar.xz)    tar -xvJf $1    ;;
        *.bz2)       bunzip2 $1     ;;
        *.rar)       rar x $1       ;;
        *.gz)        gunzip $1      ;;
        *.tar)       tar -xvf $1     ;;
        *.tbz2)      tar -xvjf $1    ;;
        *.tgz)       tar -xvzf $1    ;;
        *.zip)       unzip $1       ;;
        *.Z)         uncompress $1  ;;
        *.7z)        7z x $1        ;;
        *)           echo "don't know how to extract '$1'..." ;;
        esac
    else
        echo "'$1' is not a valid file!"
    fi
}

# 自动压缩：判断后缀名并调用相应压缩程序
function q-compress() {
    if [ -n "$1" ] ; then
        FILE=$1
        case $FILE in
        *.tar) shift && tar -cf $FILE $* ;;
        *.tar.bz2) shift && tar -cjf $FILE $* ;;
        *.tar.xz) shift && tar -cJf $FILE $* ;;
        *.tar.gz) shift && tar -czf $FILE $* ;;
        *.tgz) shift && tar -czf $FILE $* ;;
        *.zip) shift && zip $FILE $* ;;
        *.rar) shift && rar $FILE $* ;;
        esac
    else
        echo "usage: q-compress <foo.tar.gz> ./foo ./bar"
    fi
}

# 漂亮的带语法高亮的 color cat ，需要先 pip install pygments
function ccat() {
    local style="monokai"
    if [ $# -eq 0 ]; then
        pygmentize -P style=$style -P tabsize=4 -f terminal256 -g
    else
        for NAME in $@; do
            pygmentize -P style=$style -P tabsize=4 -f terminal256 -g "$NAME"
        done
    fi
}


##############################################################################
# 好玩的配置
##############################################################################

# 放到你的 ~/.bashrc 配置文件中，给 man 增加漂亮的色彩高亮
export LESS_TERMCAP_mb=$'\E[1m\E[32m'
export LESS_TERMCAP_mh=$'\E[2m'
export LESS_TERMCAP_mr=$'\E[7m'
export LESS_TERMCAP_md=$'\E[1m\E[36m'
export LESS_TERMCAP_ZW=""
export LESS_TERMCAP_us=$'\E[4m\E[1m\E[37m'
export LESS_TERMCAP_me=$'\E(B\E[m'
export LESS_TERMCAP_ue=$'\E[24m\E(B\E[m'
export LESS_TERMCAP_ZO=""
export LESS_TERMCAP_ZN=""
export LESS_TERMCAP_se=$'\E[27m\E(B\E[m'
export LESS_TERMCAP_ZV=""
export LESS_TERMCAP_so=$'\E[1m\E[33m\E[44m'

# ALT+hjkl/HJKL 快速移动光标，将下面内容添加到 ~/.inputrc 中可作用所有工具，
# 包括 bash/zsh/python/lua 等使用 readline 的工具，帮助见：info rluserman
"\eh": backward-char
"\el": forward-char
"\ej": next-history
"\ek": previous-history
"\eH": backward-word
"\eL": forward-word
"\eJ": beginning-of-line
"\eK": end-of-line


##############################################################################
# References
##############################################################################

https://github.com/Idnan/bash-guide
http://www.linuxstall.com/linux-command-line-tips-that-every-linux-user-should-know/
https://ss64.com/bash/syntax-keyboard.html
http://wiki.bash-hackers.org/commands/classictest
https://www.ibm.com/developerworks/library/l-bash-test/index.html
https://www.cyberciti.biz/faq/bash-loop-over-file/
https://linuxconfig.org/bash-scripting-tutorial
https://github.com/LeCoupa/awesome-cheatsheets/blob/master/languages/bash.sh
https://devhints.io/bash
https://github.com/jlevy/the-art-of-command-line
https://yq.aliyun.com/articles/68541

# vim: set ts=4 sw=4 tw=0 et :
```
# vim
```bash
##############################################################################
# VIM CHEATSHEET (中文速查表)  -  by skywind (created on 2017/10/12)
# Version: 47, Last Modified: 2020/10/10 11:02
# https://github.com/skywind3000/awesome-cheatsheets
##############################################################################


##############################################################################
# 光标移动
##############################################################################

h                   光标左移，同 <Left> 键
j                   光标下移，同 <Down> 键
k                   光标上移，同 <Up> 键
l                   光标右移，同 <Right> 键
CTRL-F              下一页
CTRL-B              上一页
CTRL-U              上移半屏
CTRL-D              下移半屏
0                   跳到行首（是数字零，不是字母O），效用等同于 <Home> 键
^                   跳到从行首开始第一个非空白字符
$                   跳到行尾，效用等同于 <End> 键
gg                  跳到第一行，效用等同于 CTRL+<Home>
G                   跳到最后一行，效用等同于 CTRL+<End>
nG                  跳到第n行，比如 10G 是移动到第十行
:n                  跳到第n行，比如 :10<回车> 是移动到第十行
10%                 移动到文件 10% 处
15|                 移动到当前行的 15列
w                   跳到下一个单词开头 (word: 标点或空格分隔的单词)
W                   跳到下一个单词开头 (WORD: 空格分隔的单词)
e                   跳到下一个单词尾部 (word: 标点或空格分隔的单词)
E                   跳到下一个单词尾部 (WORD: 空格分隔的单词)
b                   上一个单词头 (word: 标点或空格分隔的单词)
B                   上一个单词头 (WORD: 空格分隔的单词)
ge                  上一个单词尾
)                   向前移动一个句子（句号分隔）
(                   向后移动一个句子（句号分隔）
}                   向前移动一个段落（空行分隔）
{                   向后移动一个段落（空行分隔）
<enter>             移动到下一行首个非空字符
+                   移动到下一行首个非空字符（同回车键）
-                   移动到上一行首个非空字符
H                   移动到屏幕上部
M                   移动到屏幕中部
L                   移动到屏幕下部
fx                  跳转到下一个为 x 的字符，2f/ 可以找到第二个斜杆
Fx                  跳转到上一个为 x 的字符
tx                  跳转到下一个为 x 的字符前
Tx                  跳转到上一个为 x 的字符前
;                   跳到下一个 f/t 搜索的结果
,                   跳到上一个 f/t 搜索的结果
<S-Left>            按住 SHIFT 按左键，向左移动一个单词
<S-Right>           按住 SHIFT 按右键，向右移动一个单词
<S-Up>              按住 SHIFT 按上键，向上翻页
<S-Down>            按住 SHIFT 按下键，向下翻页
gm                  移动到行中
gj                  光标下移一行（忽略自动换行）
gk                  光标上移一行（忽略自动换行）


##############################################################################
# 插入模式：进入退出
##############################################################################

i                   在光标处进入插入模式
I                   在行首进入插入模式
a                   在光标后进入插入模式
A                   在行尾进入插入模式
o                   在下一行插入新行并进入插入模式
O                   在上一行插入新行并进入插入模式
gi                  进入到上一次插入模式的位置
<ESC>               退出插入模式
CTRL-[              退出插入模式（同 ESC 等价，但更顺手）


##############################################################################
# INSERT MODE - 由 i, I, a, A, o, O 等命令进入插入模式后
##############################################################################

<Up>                光标向上移动
<Down>              光标向下移动
<Left>              光标向左移动
<Right>             光标向右移动
<S-Left>            按住 SHIFT 按左键，向左移动一个单词
<S-Right>           按住 SHIFT 按右键，向右移动一个单词
<S-Up>              按住 SHIFT 按上键，向上翻页
<S-Down>            按住 SHIFT 按下键，向下翻页
<PageUp>            上翻页
<PageDown>          下翻页
<Delete>            删除光标处字符
<BS>                Backspace 向后删除字符
<Home>              光标跳转行首
<End>               光标跳转行尾
CTRL-W              向前删除单词
CTRL-O              临时退出插入模式，执行单条命令又返回插入模式
CTRL-\ CTRL-O       临时退出插入模式（光标保持），执行单条命令又返回插入模式
CTRL-R 0            插入寄存器（内部 0号剪贴板）内容，CTRL-R 后可跟寄存器名
CTRL-R "            插入匿名寄存器内容，相当于插入模式下 p粘贴
CTRL-R =            插入表达式计算结果，等号后面跟表达式
CTRL-R :            插入上一次命令行命令
CTRL-R /            插入上一次搜索的关键字
CTRL-F              自动缩进
CTRL-U              删除当前行所有字符
CTRL-V {char}       插入非数字的字面量
CTRL-V {number}     插入三个数字代表的 ascii/unicode 字符
CTRL-V 065          插入 10进制 ascii 字符（两数字） 065 即 A字符
CTRL-V x41          插入 16进制 ascii 字符（三数字） x41 即 A字符
CTRL-V o101         插入  8进制 ascii 字符（三数字） o101 即 A字符
CTRL-V u1234        插入 16进制 unicode 字符（四数字）
CTRL-V U12345678    插入 16进制 unicode 字符（八数字）
CTRL-K {ch1} {ch2}  插入 digraph（见 :h digraph），快速输入日文或符号等
CTRL-D              文字向前缩进
CTRL-T              文字向后缩进


##############################################################################
# 文本编辑
##############################################################################

r                   替换当前字符
R                   进入替换模式，直至 ESC 离开
s                   替换字符（删除光标处字符，并进入插入模式，前可接数量）
S                   替换行（删除当前行，并进入插入模式，前可接数量）
cc                  改写当前行（删除当前行并进入插入模式），同 S
cw                  改写光标开始处的当前单词
ciw                 改写光标所处的单词
caw                 改写光标所处的单词，并且包括前后空格（如果有的话）
c0                  改写到行首
c^                  改写到行首（第一个非零字符）
c$                  改写到行末
C                   改写到行尾（同c$）
ci"                 改写双引号中的内容
ci'                 改写单引号中的内容
cib                 改写小括号中的内容
cab                 改写小括号中的内容（包含小括号本身）
ci)                 改写小括号中的内容
ci]                 改写中括号中内容
ciB                 改写大括号中内容
caB                 改写大括号中的内容（包含大括号本身）
ci}                 改写大括号中内容
cit                 改写 xml tag 中的内容
cis                 改写当前句子
c2w                 改写下两个单词
ct(                 改写到小括号前
c/apple             改写到光标后的第一个apple前
x                   删除当前字符，前面可以接数字，3x代表删除三个字符
X                   向前删除字符
dd                  删除当前行
d0                  删除到行首
d^                  删除到行首（第一个非零字符）
d$                  删除到行末
D                   删除到行末（同 d$）
dw                  删除当前单词
diw                 删除光标所处的单词
daw                 删除光标所处的单词，并包含前后空格（如果有的话）
di"                 删除双引号中的内容
di'                 删除单引号中的内容
dib                 删除小括号中的内容
di)                 删除小括号中的内容
dab                 删除小括号内的内容（包含小括号本身）
di]                 删除中括号中内容
diB                 删除大括号中内容
di}                 删除大括号中内容
daB                 删除大括号内的内容（包含大括号本身）
dit                 删除 xml tag 中的内容
dis                 删除当前句子
dip                 删除当前段落(前后有空白行的称为一个段落)
dap                 删除当前段落(包括前后空白行)
d2w                 删除下两个单词
dt(                 删除到小括号前
d/apple             删除到光标后的第一个apple前
dgg                 删除到文件头部
dG                  删除到文件尾部
d}                  删除下一段
d{                  删除上一段
u                   撤销
U                   撤销整行操作
CTRL-R              撤销上一次 u 命令
J                   链接多行为一行
.                   重复上一次操作
~                   替换大小写
g~iw                替换当前单词的大小写
gUiw                将单词转成大写
guiw                将当前单词转成小写
guu                 全行转为小写
gUU                 全行转为大写
<<                  减少缩进
>>                  增加缩进
==                  自动缩进
CTRL-A              增加数字
CTRL-X              减少数字


##############################################################################
# 复制粘贴
##############################################################################

p                   粘贴到光标后
P                   粘贴到光标前
v                   开始标记
y                   复制标记内容
V                   开始按行标记
CTRL-V              开始列标记
y$                  复制当前位置到本行结束的内容
yy                  复制当前行
Y                   复制当前行，同 yy
yiw                 复制当前单词
3yy                 复制光标下三行内容
v0                  选中当前位置到行首
v$                  选中当前位置到行末
viw                 选中当前单词
vib                 选中小括号内的东西
vi)                 选中小括号内的东西
vi]                 选中中括号内的东西
viB                 选中大括号内的东西
vi}                 选中大括号内的东西
vis                 选中句子中的东西
vip                 选中当前段落(前后有空白行的称为一个段落)
vap                 选中当前段落(包括前后空白行)
vab                 选中小括号内的东西（包含小括号本身）
va)                 选中小括号内的东西（包含小括号本身）
va]                 选中中括号内的东西（包含中括号本身）
vaB                 选中大括号内的东西（包含大括号本身）
va}                 选中大括号内的东西（包含大括号本身）
gv                  重新选择上一次选中的文字
:set paste          允许粘贴模式（避免粘贴时自动缩进影响格式）
:set nopaste        禁止粘贴模式
"?yy                复制当前行到寄存器 ? ，问号代表 0-9 的寄存器名称
"?d3j               删除光标下三行内容，并放到寄存器 ? ，问号代表 0-9 的寄存器名称
"?p                 将寄存器 ? 的内容粘贴到光标后
"?P                 将寄存器 ? 的内容粘贴到光标前
:registers          显示所有寄存器内容
:[range]y           复制范围，比如 :20,30y 是复制20到30行，:10y 是复制第十行
:[range]d           删除范围，比如 :20,30d 是删除20到30行，:10d 是删除第十行
ddp                 交换两行内容：先删除当前行复制到寄存器，并粘贴
"_[command]         使用[command]删除内容，并且不进行复制（不会污染寄存器）
"*[command]         使用[command]复制内容到系统剪贴板（需要vim版本有clipboard支持）


##############################################################################
# 文本对象 - c,d,v,y 等命令后接文本对象，一般为：<范围 i/a><类型>
##############################################################################

$                   到行末
0                   到行首
^                   到行首非空字符
tx                  光标位置到字符 x 之前
fx                  光标位置到字符 x 之处
iw                  整个单词（不包括分隔符）
aw                  整个单词（包括分隔符）
iW                  整个 WORD（不包括分隔符）
aW                  整个 WORD（包括分隔符）
is                  整个句子（不包括分隔符）
as                  整个句子（包括分隔符）
ip                  整个段落（不包括前后空白行）
ap                  整个段落（包括前后空白行）
ib                  小括号内
ab                  小括号内（包含小括号本身）
iB                  大括号内
aB                  大括号内（包含大括号本身）
i)                  小括号内
a)                  小括号内（包含小括号本身）
i]                  中括号内
a]                  中括号内（包含中括号本身）
i}                  大括号内
a}                  大括号内（包含大括号本身）
i'                  单引号内
a'                  单引号内（包含单引号本身）
i"                  双引号内
a"                  双引号内（包含双引号本身）
2i)                 往外两层小括号内
2a)                 往外两层小括号内（包含小括号本身）
2f)                 到第二个小括号处
2t)                 到第二个小括号前


##############################################################################
# 查找替换
##############################################################################

/pattern            从光标处向文件尾搜索 pattern
?pattern            从光标处向文件头搜索 pattern
n                   向同一方向执行上一次搜索
N                   向相反方向执行上一次搜索
*                   向前搜索光标下的单词
#                   向后搜索光标下的单词
:s/p1/p2/g          将当前行中全替换p1为p2
:%s/p1/p2/g         将当前文件中全替换p1为p2
:%s/p1/p2/gc        将当前文件中全替换p1为p2，并且每处询问你是否替换
:10,20s/p1/p2/g     将第10到20行中所有p1替换为p2
:., ns/p1/p2/g      将当前行到n行中所有p1替换为p2
:., +10s/p1/p2/g    将当前行到相对当前行加10行的区间中所有p1替换为p2
:., $s/p1/p2/g      将当前行到最后一行中所有p1替换为p2
:%s/1\\2\/3/123/g   将“1\2/3” 替换为 “123”（特殊字符使用反斜杠标注）
:%s/\r//g           删除 DOS 换行符 ^M


##############################################################################
# VISUAL MODE - 由 v, V, CTRL-V 进入的可视模式
##############################################################################

>                   增加缩进
<                   减少缩进
d                   删除高亮选中的文字
x                   删除高亮选中的文字
c                   改写文字，即删除高亮选中的文字并进入插入模式
s                   改写文字，即删除高亮选中的文字并进入插入模式
y                   拷贝文字
~                   转换大小写
o                   跳转到标记区的另外一端
O                   跳转到标记块的另外一端
u                   标记区转换为小写
U                   标记区转换为大写
g CTRL-G            显示所选择区域的统计信息
<Esc>               退出可视模式


##############################################################################
# 位置跳转
##############################################################################

CTRL-O              跳转到上一个位置
CTRL-I              跳转到下一个位置
CTRL-^              跳转到 alternate file (当前窗口的上一个文件）
%                   跳转到 {} () [] 的匹配
gd                  跳转到局部定义（光标下的单词的定义）
gD                  跳转到全局定义（光标下的单词的定义）
gf                  打开名称为光标下文件名的文件
[[                  跳转到上一个顶层函数（比如C语言以大括号分隔）
]]                  跳转到下一个顶层函数（比如C语言以大括号分隔）
[m                  跳转到上一个成员函数
]m                  跳转到下一个成员函数
[{                  跳转到上一处未匹配的 {
]}                  跳转到下一处未匹配的 }
[(                  跳转到上一处未匹配的 (
])                  跳转到下一处未匹配的 )
[c                  上一个不同处（diff时）
]c                  下一个不同处（diff时）
[/                  跳转到 C注释开头
]/                  跳转到 C注释结尾
``                  回到上次跳转的位置
''                  回到上次跳转的位置
`.                  回到上次编辑的位置
'.                  回到上次编辑的位置


##############################################################################
# 文件操作
##############################################################################

:w                  保存文件
:w <filename>       按名称保存文件
:e <filename>       打开文件并编辑
:saveas <filename>  另存为文件
:r <filename>       读取文件并将内容插入到光标后
:r !dir             将 dir 命令的输出捕获并插入到光标后
:close              关闭文件
:q                  退出
:q!                 强制退出
:wa                 保存所有文件
:cd <path>          切换 Vim 当前路径
:pwd                显示 Vim 当前路径
:new                打开一个新的窗口编辑新文件
:enew               在当前窗口创建新文件
:vnew               在左右切分的新窗口中编辑新文件
:tabnew             在新的标签页中编辑新文件


##############################################################################
# 已打开文件操作
##############################################################################

:ls                 查案缓存列表
:bn                 切换到下一个缓存
:bp                 切换到上一个缓存
:bd                 删除缓存
:b 1                切换到1号缓存
:b abc              切换到文件名为 abc 开头的缓存
:badd <filename>    将文件添加到缓存列表
:set hidden         设置隐藏模式（未保存的缓存可以被切换走，或者关闭）
:set nohidden       关闭隐藏模式（未保存的缓存不能被切换走，或者关闭）
n CTRL-^            切换缓存，先输入数字的缓存编号，再按 CTRL + 6


##############################################################################
# 窗口操作
##############################################################################

:sp <filename>      上下切分窗口并在新窗口打开文件 filename
:vs <filename>      左右切分窗口并在新窗口打开文件 filename
CTRL-W s            上下切分窗口
CTRL-W v            左右切分窗口
CTRL-W w            循环切换到下一个窗口
CTRL-W W            循环切换到上一个窗口
CTRL-W p            跳到上一个访问过的窗口
CTRL-W c            关闭当前窗口
CTRL-W o            关闭其他窗口
CTRL-W h            跳到左边的窗口
CTRL-W j            跳到下边的窗口
CTRL-W k            跳到上边的窗口
CTRL-W l            跳到右边的窗口
CTRL-W +            增加当前窗口的行高，前面可以加数字
CTRL-W -            减少当前窗口的行高，前面可以加数字
CTRL-W <            减少当前窗口的列宽，前面可以加数字
CTRL-W >            增加当前窗口的列宽，前面可以加数字
CTRL-W =            让所有窗口宽高相同
CTRL-W H            将当前窗口移动到最左边
CTRL-W J            将当前窗口移动到最下边
CTRL-W K            将当前窗口移动到最上边
CTRL-W L            将当前窗口移动到最右边
CTRL-W x            交换窗口
CTRL-W f            在新窗口中打开名为光标下文件名的文件
CTRL-W gf           在新标签页中打开名为光标下文件名的文件
CTRL-W R            旋转窗口
CTRL-W T            将当前窗口移到新的标签页中
CTRL-W P            跳转到预览窗口
CTRL-W z            关闭预览窗口
CTRL-W _            纵向最大化当前窗口
CTRL-W |            横向最大化当前窗口


##############################################################################
# 标签页
##############################################################################

:tabs               显示所有标签页
:tabe <filename>    在新标签页中打开文件 filename
:tabn               下一个标签页
:tabp               上一个标签页
:tabc               关闭当前标签页
:tabo               关闭其他标签页
:tabn n             切换到第n个标签页，比如 :tabn 3 切换到第三个标签页
:tabm n             标签移动
:tabfirst           切换到第一个标签页
:tablast            切换到最后一个标签页
:tab help           在标签页打开帮助
:tab drop <file>    如果文件已被其他标签页和窗口打开则跳过去，否则新标签打开
:tab split          在新的标签页中打开当前窗口里的文件
:tab ball           将缓存中所有文件用标签页打开
:set showtabline=?  设置为 0 就不显示标签页标签，1会按需显示，2会永久显示
ngt                 切换到第n个标签页，比如 2gt 将会切换到第二个标签页
gt                  下一个标签页
gT                  上一个标签页


##############################################################################
# 书签
##############################################################################

:marks              显示所有书签
ma                  保存当前位置到书签 a ，书签名小写字母为文件内，大写全局
'a                  跳转到书签 a所在的行
`a                  跳转到书签 a所在位置
`.                  跳转到上一次编辑的行
'A                  跳转到全文书签 A
['                  跳转到上一个书签
]'                  跳转到下一个书签
'<                  跳到上次可视模式选择区域的开始
'>                  跳到上次可视模式选择区域的结束
:delm a             删除缓冲区标签a
:delm A             删除文件标签A
:delm!              删除所有缓冲区标签(小写字母), 不能删除文件标签和数字标签
:delm A-Z           删除所有文件标签(大写字母)
:delm 0-9           删除所有数字标签(.viminfo)
:delm A-Z0-9        删除所有文件标签和数字标签

 
##############################################################################
# 常用设置
##############################################################################

:set nocompatible   设置不兼容原始 vi 模式（必须设置在最开头）
:set bs=?           设置BS键模式，现代编辑器为 :set bs=eol,start,indent
:set sw=4           设置缩进宽度为 4
:set ts=4           设置制表符宽度为 4
:set noet           设置不展开 tab 成空格
:set et             设置展开 tab 成空格
:set winaltkeys=no  设置 GVim 下正常捕获 ALT 键
:set nowrap         关闭自动换行
:set ttimeout       允许终端按键检测超时（终端下功能键为一串ESC开头的扫描码）
:set ttm=100        设置终端按键检测超时为100毫秒
:set term=?         设置终端类型，比如常见的 xterm
:set ignorecase     设置搜索忽略大小写(可缩写为 :set ic)
:set noignorecase   设置搜索不忽略大小写(可缩写为 :set noic)
:set smartcase      智能大小写，默认忽略大小写，除非搜索内容里包含大写字母
:set list           设置显示制表符和换行符
:set number         设置显示行号，禁止显示行号可以用 :set nonumber
:set relativenumber 设置显示相对行号（其他行与当前行的距离）
:set paste          进入粘贴模式（粘贴时禁用缩进等影响格式的东西）
:set nopaste        结束粘贴模式
:set spell          允许拼写检查
:set hlsearch       设置高亮查找
:set ruler          总是显示光标位置
:set incsearch      查找输入时动态增量显示查找结果
:set insertmode     Vim 始终处于插入模式下，使用 ctrl-o 临时执行命令
:set all            列出所有选项设置情况
:syntax on          允许语法高亮
:syntax off         禁止语法高亮


##############################################################################
# 帮助信息
##############################################################################

:h tutor            入门文档
:h quickref         快速帮助
:h index            查询 Vim 所有键盘命令定义
:h summary          帮助你更好的使用内置帮助系统
:h CTRL-H           查询普通模式下 CTRL-H 是干什么的
:h i_CTRL-H         查询插入模式下 CTRL-H 是干什么的
:h i_<Up>           查询插入模式下方向键上是干什么的
:h pattern.txt      正则表达式帮助
:h eval             脚本编写帮助
:h function-list    查看 VimScript 的函数列表 
:h windows.txt      窗口使用帮助
:h tabpage.txt      标签页使用帮助
:h +timers          显示对 +timers 特性的帮助
:h :!               查看如何运行外部命令
:h tips             查看 Vim 内置的常用技巧文档
:h set-termcap      查看如何设置按键扫描码
:viusage            NORMAL 模式帮助
:exusage            EX 命令帮助
:version            显示当前 Vim 的版本号和特性


##############################################################################
# 外部命令
##############################################################################

:!ls                运行外部命令 ls，并等待返回
:r !ls              将外部命令 ls 的输出捕获，并插入到光标后
:w !sudo tee %      sudo以后保存当前文件
:call system('ls')  调用 ls 命令，但是不显示返回内容
:!start notepad     Windows 下启动 notepad，最前面可以加 silent
:sil !start cmd     Windows 下当前目录打开 cmd
:%!prog             运行文字过滤程序，如整理 json格式 :%!python -m json.tool


##############################################################################
# Quickfix 窗口
##############################################################################

:copen              打开 quickfix 窗口（查看编译，grep等信息）
:copen 10           打开 quickfix 窗口，并且设置高度为 10
:cclose             关闭 quickfix 窗口
:cfirst             跳到 quickfix 中第一个错误信息
:clast              跳到 quickfix 中最后一条错误信息
:cc [nr]            查看错误 [nr]
:cnext              跳到 quickfix 中下一个错误信息
:cprev              跳到 quickfix 中上一个错误信息


##############################################################################
# 拼写检查
##############################################################################

:set spell          打开拼写检查
:set nospell        关闭拼写检查
]s                  下一处错误拼写的单词
[s                  上一处错误拼写的单词
zg                  加入单词到拼写词表中
zug                 撤销上一次加入的单词
z=                  拼写建议


##############################################################################
# 代码折叠
##############################################################################

za                  切换折叠
zA                  递归切换折叠
zc                  折叠光标下代码
zC                  折叠光标下所有代码
zd                  删除光标下折叠
zD                  递归删除所有折叠
zE                  删除所有折叠
zf                  创建代码折叠
zF                  指定行数创建折叠
zi                  切换折叠
zm                  所有代码折叠一层
zr                  所有代码打开一层
zM                  折叠所有代码，设置 foldlevel=0，设置 foldenable
zR                  打开所有代码，设置 foldlevel 为最大值
zn                  折叠 none，重置 foldenable 并打开所有代码
zN                  折叠 normal，重置 foldenable 并恢复所有折叠
zo                  打开一层代码
zO                  打开光标下所有代码折叠


##############################################################################
# 宏录制
##############################################################################

qa                  开始录制名字为 a 的宏
q                   结束录制宏
@a                  播放名字为 a 的宏
@@                  播放上一个宏
@:                  重复上一个ex命令（即冒号命令）


##############################################################################
# 其他命令
##############################################################################

CTRL-X CTRL-F       插入模式下文件路径补全
CTRL-X CTRL-O       插入下 Omnifunc 补全
CTRL-X CTRL-N       插入模式下关键字补全
CTRL-X CTRL-E       插入模式下向上滚屏
CTRL-X CTRL-Y       插入模式下向下滚屏
CTRL-E              向上滚屏
CTRL-Y              向下滚屏
CTRL-G              显示正在编辑的文件名，以及大小和位置信息
g CTRL-G            显示文件的：大小，字符数，单词数和行数，可视模式下也可用
zz                  调整光标所在行到屏幕中央
zt                  调整光标所在行到屏幕上部
zb                  调整光标所在行到屏幕下部
ga                  显示光标下字符的 ascii 码或者 unicode 编码
g8                  显示光标下字符的 utf-8 编码字节序
gi                  回到上次进入插入的地方，并切换到插入模式
K                   查询光标下单词的帮助
ZZ                  保存文件（如果有改动的话），并关闭窗口
ZQ                  不保存文件关闭窗口
CTRL-PgUp           上个标签页，GVim OK，部分终端软件需设置对应键盘码
CTRL-PgDown         下个标签页，GVim OK，部分终端软件需设置对应键盘码
CTRL-R CTRL-W       命令模式下插入光标下单词
CTRL-INSERT         复制到系统剪贴板（GVIM）
SHIFT-INSERT        粘贴系统剪贴板的内容（GVIM）
:set ff=unix        设置换行为 unix
:set ff=dos         设置换行为 dos
:set ff?            查看换行设置
:set nohl           清除搜索高亮
:set termcap        查看会从终端接收什么以及会发送给终端什么命令
:set guicursor=     解决 SecureCRT/PenguiNet 中 NeoVim 局部奇怪字符问题
:set t_RS= t_SH=    解决 SecureCRT/PenguiNet 中 Vim8.0 终端功能奇怪字符
:set fo+=a          开启文本段的实时自动格式化
:earlier 15m        回退到15分钟前的文件内容
:.!date             在当前窗口插入时间
:%!xxd              开始二进制编辑
:%!xxd -r           保存二进制编辑
:r !curl -sL {URL}  读取 url 内容添加到光标后
:g/^\s*$/d          删除空行
:g/green/d          删除所有包含 green 的行
:v/green/d          删除所有不包含 green 的行
:g/gladiolli/#      搜索单词打印结果，并在结果前加上行号
:g/ab.*cd.*efg/#    搜索包含 ab,cd 和 efg 的行，打印结果以及行号
:v/./,/./-j         压缩空行
:Man bash           在 Vim 中查看 man，先调用 :runtime! ftplugin/man.vim 激活
/fred\|joe          搜索 fred 或者 joe
/\<\d\d\d\d\>       精确搜索四个数字
/^\n\{3}            搜索连续三个空行


##############################################################################
# Plugin - https://github.com/tpope/vim-commentary
##############################################################################

gcc                 注释当前行
gc{motion}          注释 {motion} 所标注的区域，比如 gcap 注释整段
gci{                注释大括号内的内容
gc                  在 Visual Mode 下面按 gc 注释选中区域
:7,17Commentary     注释 7 到 17 行


##############################################################################
# Plugin - https://github.com/junegunn/vim-easy-align
##############################################################################

:EasyAlign =        以第一个匹配的=为中心对齐
:EasyAlign *=       匹配并且对齐所有=


##############################################################################
# Plugin - https://github.com/tpope/vim-unimpaired
##############################################################################

[space              向上插入空行
]space              向下插入空行
[e                  替换当前行和上一行
]e                  替换当前行和下一行
[x                  XML 编码
]x                  XML 解码
[u                  URL 编码
]u                  URL 解码
[y                  C 字符串编码
]y                  C 字符串解码
[q                  上一个 quickfix 错误
]q                  下一个 quickfix 错误
[Q                  第一个 quickfix 错误
]Q                  最后一个 quickfix 错误
[f                  切换同目录里上一个文件
]f                  切换同目录里下一个文件
[os                 设置 :set spell
]os                 设置 :set nospell
=os                 设置 :set invspell
[on                 显示行号
]on                 关闭行号
[ol                 显示回车和制表符 :set list
]ol                 不显示回车和制表符 :set nolist
[b                  缓存切换到上一个文件，即 :bp
]b                  缓存切换到下一个文件，即 :bn
[B                  缓存切换到第一个文件，即 :bfirst
]B                  缓存切换到最后一个文件，即 :blast


##############################################################################
# Plugin - https://github.com/skywind3000/asyncrun.vim
##############################################################################

:AsyncRun ls        异步运行命令 ls 结果输出到 quickfix 使用 :copen 查看
:AsyncRun -raw ls   异步运行命令 ls 结果不匹配 errorformat


##############################################################################
# Plugin - https://github.com/gaving/vim-textobj-argument
##############################################################################

cia                 改写函数参数
caa                 改写函数参数（包括逗号分隔）
dia                 删除函数参数
daa                 删除函数参数（包括逗号分隔）
via                 选取函数参数
vaa                 选取函数参数（包括逗号分隔）
yia                 复制函数参数
yaa                 复制函数参数（包括逗号分隔）


##############################################################################
# 网络资源
##############################################################################

最新版本            https://github.com/vim/vim   
Windows 最新版      https://github.com/vim/vim-win32-installer/releases
插件浏览            http://vimawesome.com
reddit              https://www.reddit.com/r/vim/
正确设置 ALT/BS 键  http://www.skywind.me/blog/archives/2021
视频教程            http://vimcasts.org/
中文帮助            http://vimcdoc.sourceforge.net/doc/help.html
中文版入门到精通    https://github.com/wsdjeg/vim-galore-zh_cn
五分钟脚本入门      http://www.skywind.me/blog/archives/2193
脚本精通            http://learnvimscriptthehardway.stevelosh.com/
中文脚本帮助        vimcdoc.sourceforge.net/doc/eval.html
十六年使用经验      http://zzapper.co.uk/vimtips.html
配色方案            http://vimcolors.com/


##############################################################################
# TIPS
##############################################################################

- 永远不要用 CTRL-C 代替 <ESC> 完全不同的含义，容易错误中断运行的后台脚本
- 很多人使用 CTRL-[ 代替 <ESC>，左手小指 CTRL，右手小指 [ 熟练后很方便
- 某些终端中使用 Vim 8 内嵌终端如看到奇怪字符，使用 :set t_RS= t_SH= 解决
- 某些终端中使用 Vim 8.2+ 会看到一些奇怪字符，使用 :set t_TI= t_TE= 解决
- 某些终端中使用 NeoVim 如看到奇怪字符，使用 :set guicursor= 解决
- 使用 MS-Terminal 如果进入 Vim/NVim 会默认替换模式设置 :set t_u7= 解决
- 多使用 ciw, ci[, ci", ci( 以及 diw, di[, di", di( 命令来快速改写/删除文本
- 在行内左右移动光标时，多使用w b e或W B E，而不是h l或方向键，这样会快很多
- SHIFT 相当于移动加速键， w b e 移动光标很慢，但是 W B E 走的很快
- 自己要善于总结新技巧，比如移动到行首非空字符时用 0w 命令比 ^ 命令更容易输入
- 在空白行使用 dip 命令可以删除所有临近的空白行，viw 可以选择连续空白
- 缩进时使用 >8j  >}  <ap  >ap  =i}  == 会方便很多
- 插入模式下，当你发现一个单词写错了，应该多用 CTRL-W 这比 <BackSpace> 快
- y d c 命令可以很好结合 f t 和 /X 比如 dt) 和 y/end<cr>
- c d x 命令会自动填充寄存器 "1 到 "9 , y 命令会自动填充 "0 寄存器
- 用 v 命令选择文本时，可以用 o 掉头选择，有时很有用
- 写文章时，可以写一段代码块，然后选中后执行 :!python 代码块就会被替换成结果
- 搜索后经常使用 :nohl 来消除高亮，使用很频繁，可以 map 到 <BackSpace> 上
- 搜索时可以用 CTRL-R CTRL-W 插入光标下的单词，命令模式也能这么用
- 映射按键时，应该默认使用 noremap ，只有特别需要的时候使用 map
- 当你觉得做某事很低效时，你应该停下来，u u u u 然后思考正确的高效方式来完成
- 用 y复制文本后，命令模式中 CTRL-R 然后按双引号 0 可以插入之前复制内容
- 某些情况下 Vim 绘制高亮慢，滚屏刷新慢可以试试 set re=1 使用老的正则引擎
- Windows 下的 GVim 可以设置 set rop=type:directx,renmode:5 增强显示


##############################################################################
# References
##############################################################################

https://github.com/groenewege/vimrc/blob/master/vim_cheat_sheet.txt
http://blog.g-design.net/post/4789778607/vim-cheat-sheet
http://www.keyxl.com/aaa8263/290/VIM-keyboard-shortcuts.htm
http://jmcpherson.org/editing.html
http://www.fprintf.net/vimCheatSheet.html
http://www.ouyaoxiazai.com/article/24/654.html
http://bbs.it-home.org/thread-80794-1-1.html
http://www.lpfrx.com/wp-content/uploads/2008/09/vi.jpg
http://michael.peopleofhonoronly.com/vim/
https://github.com/hobbestigrou/vimtips-fortune/blob/master/fortunes/vimtips
https://github.com/glts/vim-cottidie/blob/master/autoload/cottidie/tips



# vim: set ts=4 sw=4 tw=0 noet noautoindent fdm=manual :
```
# VIM
```bash
##############################################################################
# https://github.com/skywind3000/awesome-cheatsheets
##############################################################################


##############################################################################
# 光标移动
##############################################################################

h                   光标左移，同 <Left> 键
j                   光标下移，同 <Down> 键
k                   光标上移，同 <Up> 键
l                   光标右移，同 <Right> 键
CTRL-F              下一页
CTRL-B              上一页
CTRL-U              上移半屏
CTRL-D              下移半屏
0                   跳到行首（是数字零，不是字母O），效用等同于 <Home> 键
^                   跳到从行首开始第一个非空白字符
$                   跳到行尾，效用等同于 <End> 键
gg                  跳到第一行，效用等同于 CTRL+<Home>
G                   跳到最后一行，效用等同于 CTRL+<End>
nG                  跳到第n行，比如 10G 是移动到第十行
:n                  跳到第n行，比如 :10<回车> 是移动到第十行
10%                 移动到文件 10% 处
15|                 移动到当前行的 15列
w                   跳到下一个单词开头 (word: 标点或空格分隔的单词)
W                   跳到下一个单词开头 (WORD: 空格分隔的单词)
e                   跳到下一个单词尾部 (word: 标点或空格分隔的单词)
E                   跳到下一个单词尾部 (WORD: 空格分隔的单词)
b                   上一个单词头 (word: 标点或空格分隔的单词)
B                   上一个单词头 (WORD: 空格分隔的单词)
ge                  上一个单词尾
)                   向前移动一个句子（句号分隔）
(                   向后移动一个句子（句号分隔）
}                   向前移动一个段落（空行分隔）
{                   向后移动一个段落（空行分隔）
<enter>             移动到下一行首个非空字符
+                   移动到下一行首个非空字符（同回车键）
-                   移动到上一行首个非空字符
H                   移动到屏幕上部
M                   移动到屏幕中部
L                   移动到屏幕下部
fx                  跳转到下一个为 x 的字符，2f/ 可以找到第二个斜杆
Fx                  跳转到上一个为 x 的字符
tx                  跳转到下一个为 x 的字符前
Tx                  跳转到上一个为 x 的字符前
;                   跳到下一个 f/t 搜索的结果
,                   跳到上一个 f/t 搜索的结果
<S-Left>            按住 SHIFT 按左键，向左移动一个单词
<S-Right>           按住 SHIFT 按右键，向右移动一个单词
<S-Up>              按住 SHIFT 按上键，向上翻页
<S-Down>            按住 SHIFT 按下键，向下翻页
gm                  移动到行中
gj                  光标下移一行（忽略自动换行）
gk                  光标上移一行（忽略自动换行）


##############################################################################
# 插入模式：进入退出
##############################################################################

i                   在光标处进入插入模式
I                   在行首进入插入模式
a                   在光标后进入插入模式
A                   在行尾进入插入模式
o                   在下一行插入新行并进入插入模式
O                   在上一行插入新行并进入插入模式
gi                  进入到上一次插入模式的位置
<ESC>               退出插入模式
CTRL-[              退出插入模式（同 ESC 等价，但更顺手）


##############################################################################
# INSERT MODE - 由 i, I, a, A, o, O 等命令进入插入模式后
##############################################################################

<Up>                光标向上移动
<Down>              光标向下移动
<Left>              光标向左移动
<Right>             光标向右移动
<S-Left>            按住 SHIFT 按左键，向左移动一个单词
<S-Right>           按住 SHIFT 按右键，向右移动一个单词
<S-Up>              按住 SHIFT 按上键，向上翻页
<S-Down>            按住 SHIFT 按下键，向下翻页
<PageUp>            上翻页
<PageDown>          下翻页
<Delete>            删除光标处字符
<BS>                Backspace 向后删除字符
<Home>              光标跳转行首
<End>               光标跳转行尾
CTRL-W              向前删除单词
CTRL-O              临时退出插入模式，执行单条命令又返回插入模式
CTRL-\ CTRL-O       临时退出插入模式（光标保持），执行单条命令又返回插入模式
CTRL-R 0            插入寄存器（内部 0号剪贴板）内容，CTRL-R 后可跟寄存器名
CTRL-R "            插入匿名寄存器内容，相当于插入模式下 p粘贴
CTRL-R =            插入表达式计算结果，等号后面跟表达式
CTRL-R :            插入上一次命令行命令
CTRL-R /            插入上一次搜索的关键字
CTRL-F              自动缩进
CTRL-U              删除当前行所有字符
CTRL-V {char}       插入非数字的字面量
CTRL-V {number}     插入三个数字代表的 ascii/unicode 字符
CTRL-V 065          插入 10进制 ascii 字符（两数字） 065 即 A字符
CTRL-V x41          插入 16进制 ascii 字符（三数字） x41 即 A字符
CTRL-V o101         插入  8进制 ascii 字符（三数字） o101 即 A字符
CTRL-V u1234        插入 16进制 unicode 字符（四数字）
CTRL-V U12345678    插入 16进制 unicode 字符（八数字）
CTRL-K {ch1} {ch2}  插入 digraph（见 :h digraph），快速输入日文或符号等
CTRL-D              文字向前缩进
CTRL-T              文字向后缩进


##############################################################################
# 文本编辑
##############################################################################

r                   替换当前字符
R                   进入替换模式，直至 ESC 离开
s                   替换字符（删除光标处字符，并进入插入模式，前可接数量）
S                   替换行（删除当前行，并进入插入模式，前可接数量）
cc                  改写当前行（删除当前行并进入插入模式），同 S
cw                  改写光标开始处的当前单词
ciw                 改写光标所处的单词
caw                 改写光标所处的单词，并且包括前后空格（如果有的话）
c0                  改写到行首
c^                  改写到行首（第一个非零字符）
c$                  改写到行末
C                   改写到行尾（同c$）
ci"                 改写双引号中的内容
ci'                 改写单引号中的内容
cib                 改写小括号中的内容
cab                 改写小括号中的内容（包含小括号本身）
ci)                 改写小括号中的内容
ci]                 改写中括号中内容
ciB                 改写大括号中内容
caB                 改写大括号中的内容（包含大括号本身）
ci}                 改写大括号中内容
cit                 改写 xml tag 中的内容
cis                 改写当前句子
c2w                 改写下两个单词
ct(                 改写到小括号前
c/apple             改写到光标后的第一个apple前
x                   删除当前字符，前面可以接数字，3x代表删除三个字符
X                   向前删除字符
dd                  删除当前行
d0                  删除到行首
d^                  删除到行首（第一个非零字符）
d$                  删除到行末
D                   删除到行末（同 d$）
dw                  删除当前单词
diw                 删除光标所处的单词
daw                 删除光标所处的单词，并包含前后空格（如果有的话）
di"                 删除双引号中的内容
di'                 删除单引号中的内容
dib                 删除小括号中的内容
di)                 删除小括号中的内容
dab                 删除小括号内的内容（包含小括号本身）
di]                 删除中括号中内容
diB                 删除大括号中内容
di}                 删除大括号中内容
daB                 删除大括号内的内容（包含大括号本身）
dit                 删除 xml tag 中的内容
dis                 删除当前句子
dip                 删除当前段落(前后有空白行的称为一个段落)
dap                 删除当前段落(包括前后空白行)
d2w                 删除下两个单词
dt(                 删除到小括号前
d/apple             删除到光标后的第一个apple前
dgg                 删除到文件头部
dG                  删除到文件尾部
d}                  删除下一段
d{                  删除上一段
u                   撤销
U                   撤销整行操作
CTRL-R              撤销上一次 u 命令
J                   链接多行为一行
.                   重复上一次操作
~                   替换大小写
g~iw                替换当前单词的大小写
gUiw                将单词转成大写
guiw                将当前单词转成小写
guu                 全行转为小写
gUU                 全行转为大写
<<                  减少缩进
>>                  增加缩进
==                  自动缩进
CTRL-A              增加数字
CTRL-X              减少数字


##############################################################################
# 复制粘贴
##############################################################################

p                   粘贴到光标后
P                   粘贴到光标前
v                   开始标记
y                   复制标记内容
V                   开始按行标记
CTRL-V              开始列标记
y$                  复制当前位置到本行结束的内容
yy                  复制当前行
Y                   复制当前行，同 yy
yiw                 复制当前单词
3yy                 复制光标下三行内容
v0                  选中当前位置到行首
v$                  选中当前位置到行末
viw                 选中当前单词
vib                 选中小括号内的东西
vi)                 选中小括号内的东西
vi]                 选中中括号内的东西
viB                 选中大括号内的东西
vi}                 选中大括号内的东西
vis                 选中句子中的东西
vip                 选中当前段落(前后有空白行的称为一个段落)
vap                 选中当前段落(包括前后空白行)
vab                 选中小括号内的东西（包含小括号本身）
va)                 选中小括号内的东西（包含小括号本身）
va]                 选中中括号内的东西（包含中括号本身）
vaB                 选中大括号内的东西（包含大括号本身）
va}                 选中大括号内的东西（包含大括号本身）
gv                  重新选择上一次选中的文字
:set paste          允许粘贴模式（避免粘贴时自动缩进影响格式）
:set nopaste        禁止粘贴模式
"?yy                复制当前行到寄存器 ? ，问号代表 0-9 的寄存器名称
"?d3j               删除光标下三行内容，并放到寄存器 ? ，问号代表 0-9 的寄存器名称
"?p                 将寄存器 ? 的内容粘贴到光标后
"?P                 将寄存器 ? 的内容粘贴到光标前
:registers          显示所有寄存器内容
:[range]y           复制范围，比如 :20,30y 是复制20到30行，:10y 是复制第十行
:[range]d           删除范围，比如 :20,30d 是删除20到30行，:10d 是删除第十行
ddp                 交换两行内容：先删除当前行复制到寄存器，并粘贴
"_[command]         使用[command]删除内容，并且不进行复制（不会污染寄存器）
"*[command]         使用[command]复制内容到系统剪贴板（需要vim版本有clipboard支持）


##############################################################################
# 文本对象 - c,d,v,y 等命令后接文本对象，一般为：<范围 i/a><类型>
##############################################################################

$                   到行末
0                   到行首
^                   到行首非空字符
tx                  光标位置到字符 x 之前
fx                  光标位置到字符 x 之处
iw                  整个单词（不包括分隔符）
aw                  整个单词（包括分隔符）
iW                  整个 WORD（不包括分隔符）
aW                  整个 WORD（包括分隔符）
is                  整个句子（不包括分隔符）
as                  整个句子（包括分隔符）
ip                  整个段落（不包括前后空白行）
ap                  整个段落（包括前后空白行）
ib                  小括号内
ab                  小括号内（包含小括号本身）
iB                  大括号内
aB                  大括号内（包含大括号本身）
i)                  小括号内
a)                  小括号内（包含小括号本身）
i]                  中括号内
a]                  中括号内（包含中括号本身）
i}                  大括号内
a}                  大括号内（包含大括号本身）
i'                  单引号内
a'                  单引号内（包含单引号本身）
i"                  双引号内
a"                  双引号内（包含双引号本身）
2i)                 往外两层小括号内
2a)                 往外两层小括号内（包含小括号本身）
2f)                 到第二个小括号处
2t)                 到第二个小括号前


##############################################################################
# 查找替换
##############################################################################

/pattern            从光标处向文件尾搜索 pattern
?pattern            从光标处向文件头搜索 pattern
n                   向同一方向执行上一次搜索
N                   向相反方向执行上一次搜索
*                   向前搜索光标下的单词
#                   向后搜索光标下的单词
:s/p1/p2/g          将当前行中全替换p1为p2
:%s/p1/p2/g         将当前文件中全替换p1为p2
:%s/p1/p2/gc        将当前文件中全替换p1为p2，并且每处询问你是否替换
:10,20s/p1/p2/g     将第10到20行中所有p1替换为p2
:., ns/p1/p2/g      将当前行到n行中所有p1替换为p2
:., +10s/p1/p2/g    将当前行到相对当前行加10行的区间中所有p1替换为p2
:., $s/p1/p2/g      将当前行到最后一行中所有p1替换为p2
:%s/1\\2\/3/123/g   将“1\2/3” 替换为 “123”（特殊字符使用反斜杠标注）
:%s/\r//g           删除 DOS 换行符 ^M


##############################################################################
# VISUAL MODE - 由 v, V, CTRL-V 进入的可视模式
##############################################################################

>                   增加缩进
<                   减少缩进
d                   删除高亮选中的文字
x                   删除高亮选中的文字
c                   改写文字，即删除高亮选中的文字并进入插入模式
s                   改写文字，即删除高亮选中的文字并进入插入模式
y                   拷贝文字
~                   转换大小写
o                   跳转到标记区的另外一端
O                   跳转到标记块的另外一端
u                   标记区转换为小写
U                   标记区转换为大写
g CTRL-G            显示所选择区域的统计信息
<Esc>               退出可视模式


##############################################################################
# 位置跳转
##############################################################################

CTRL-O              跳转到上一个位置
CTRL-I              跳转到下一个位置
CTRL-^              跳转到 alternate file (当前窗口的上一个文件）
%                   跳转到 {} () [] 的匹配
gd                  跳转到局部定义（光标下的单词的定义）
gD                  跳转到全局定义（光标下的单词的定义）
gf                  打开名称为光标下文件名的文件
[[                  跳转到上一个顶层函数（比如C语言以大括号分隔）
]]                  跳转到下一个顶层函数（比如C语言以大括号分隔）
[m                  跳转到上一个成员函数
]m                  跳转到下一个成员函数
[{                  跳转到上一处未匹配的 {
]}                  跳转到下一处未匹配的 }
[(                  跳转到上一处未匹配的 (
])                  跳转到下一处未匹配的 )
[c                  上一个不同处（diff时）
]c                  下一个不同处（diff时）
[/                  跳转到 C注释开头
]/                  跳转到 C注释结尾
``                  回到上次跳转的位置
''                  回到上次跳转的位置
`.                  回到上次编辑的位置
'.                  回到上次编辑的位置


##############################################################################
# 文件操作
##############################################################################

:w                  保存文件
:w <filename>       按名称保存文件
:e <filename>       打开文件并编辑
:saveas <filename>  另存为文件
:r <filename>       读取文件并将内容插入到光标后
:r !dir             将 dir 命令的输出捕获并插入到光标后
:close              关闭文件
:q                  退出
:q!                 强制退出
:wa                 保存所有文件
:cd <path>          切换 Vim 当前路径
:pwd                显示 Vim 当前路径
:new                打开一个新的窗口编辑新文件
:enew               在当前窗口创建新文件
:vnew               在左右切分的新窗口中编辑新文件
:tabnew             在新的标签页中编辑新文件


##############################################################################
# 已打开文件操作
##############################################################################

:ls                 查案缓存列表
:bn                 切换到下一个缓存
:bp                 切换到上一个缓存
:bd                 删除缓存
:b 1                切换到1号缓存
:b abc              切换到文件名为 abc 开头的缓存
:badd <filename>    将文件添加到缓存列表
:set hidden         设置隐藏模式（未保存的缓存可以被切换走，或者关闭）
:set nohidden       关闭隐藏模式（未保存的缓存不能被切换走，或者关闭）
n CTRL-^            切换缓存，先输入数字的缓存编号，再按 CTRL + 6


##############################################################################
# 窗口操作
##############################################################################

:sp <filename>      上下切分窗口并在新窗口打开文件 filename
:vs <filename>      左右切分窗口并在新窗口打开文件 filename
CTRL-W s            上下切分窗口
CTRL-W v            左右切分窗口
CTRL-W w            循环切换到下一个窗口
CTRL-W W            循环切换到上一个窗口
CTRL-W p            跳到上一个访问过的窗口
CTRL-W c            关闭当前窗口
CTRL-W o            关闭其他窗口
CTRL-W h            跳到左边的窗口
CTRL-W j            跳到下边的窗口
CTRL-W k            跳到上边的窗口
CTRL-W l            跳到右边的窗口
CTRL-W +            增加当前窗口的行高，前面可以加数字
CTRL-W -            减少当前窗口的行高，前面可以加数字
CTRL-W <            减少当前窗口的列宽，前面可以加数字
CTRL-W >            增加当前窗口的列宽，前面可以加数字
CTRL-W =            让所有窗口宽高相同
CTRL-W H            将当前窗口移动到最左边
CTRL-W J            将当前窗口移动到最下边
CTRL-W K            将当前窗口移动到最上边
CTRL-W L            将当前窗口移动到最右边
CTRL-W x            交换窗口
CTRL-W f            在新窗口中打开名为光标下文件名的文件
CTRL-W gf           在新标签页中打开名为光标下文件名的文件
CTRL-W R            旋转窗口
CTRL-W T            将当前窗口移到新的标签页中
CTRL-W P            跳转到预览窗口
CTRL-W z            关闭预览窗口
CTRL-W _            纵向最大化当前窗口
CTRL-W |            横向最大化当前窗口


##############################################################################
# 标签页
##############################################################################

:tabs               显示所有标签页
:tabe <filename>    在新标签页中打开文件 filename
:tabn               下一个标签页
:tabp               上一个标签页
:tabc               关闭当前标签页
:tabo               关闭其他标签页
:tabn n             切换到第n个标签页，比如 :tabn 3 切换到第三个标签页
:tabm n             标签移动
:tabfirst           切换到第一个标签页
:tablast            切换到最后一个标签页
:tab help           在标签页打开帮助
:tab drop <file>    如果文件已被其他标签页和窗口打开则跳过去，否则新标签打开
:tab split          在新的标签页中打开当前窗口里的文件
:tab ball           将缓存中所有文件用标签页打开
:set showtabline=?  设置为 0 就不显示标签页标签，1会按需显示，2会永久显示
ngt                 切换到第n个标签页，比如 2gt 将会切换到第二个标签页
gt                  下一个标签页
gT                  上一个标签页


##############################################################################
# 书签
##############################################################################

:marks              显示所有书签
ma                  保存当前位置到书签 a ，书签名小写字母为文件内，大写全局
'a                  跳转到书签 a所在的行
`a                  跳转到书签 a所在位置
`.                  跳转到上一次编辑的行
'A                  跳转到全文书签 A
['                  跳转到上一个书签
]'                  跳转到下一个书签
'<                  跳到上次可视模式选择区域的开始
'>                  跳到上次可视模式选择区域的结束
:delm a             删除缓冲区标签a
:delm A             删除文件标签A
:delm!              删除所有缓冲区标签(小写字母), 不能删除文件标签和数字标签
:delm A-Z           删除所有文件标签(大写字母)
:delm 0-9           删除所有数字标签(.viminfo)
:delm A-Z0-9        删除所有文件标签和数字标签

 
##############################################################################
# 常用设置
##############################################################################

:set nocompatible   设置不兼容原始 vi 模式（必须设置在最开头）
:set bs=?           设置BS键模式，现代编辑器为 :set bs=eol,start,indent
:set sw=4           设置缩进宽度为 4
:set ts=4           设置制表符宽度为 4
:set noet           设置不展开 tab 成空格
:set et             设置展开 tab 成空格
:set winaltkeys=no  设置 GVim 下正常捕获 ALT 键
:set nowrap         关闭自动换行
:set ttimeout       允许终端按键检测超时（终端下功能键为一串ESC开头的扫描码）
:set ttm=100        设置终端按键检测超时为100毫秒
:set term=?         设置终端类型，比如常见的 xterm
:set ignorecase     设置搜索忽略大小写(可缩写为 :set ic)
:set noignorecase   设置搜索不忽略大小写(可缩写为 :set noic)
:set smartcase      智能大小写，默认忽略大小写，除非搜索内容里包含大写字母
:set list           设置显示制表符和换行符
:set number         设置显示行号，禁止显示行号可以用 :set nonumber
:set relativenumber 设置显示相对行号（其他行与当前行的距离）
:set paste          进入粘贴模式（粘贴时禁用缩进等影响格式的东西）
:set nopaste        结束粘贴模式
:set spell          允许拼写检查
:set hlsearch       设置高亮查找
:set ruler          总是显示光标位置
:set incsearch      查找输入时动态增量显示查找结果
:set insertmode     Vim 始终处于插入模式下，使用 ctrl-o 临时执行命令
:set all            列出所有选项设置情况
:syntax on          允许语法高亮
:syntax off         禁止语法高亮


##############################################################################
# 帮助信息
##############################################################################

:h tutor            入门文档
:h quickref         快速帮助
:h index            查询 Vim 所有键盘命令定义
:h summary          帮助你更好的使用内置帮助系统
:h CTRL-H           查询普通模式下 CTRL-H 是干什么的
:h i_CTRL-H         查询插入模式下 CTRL-H 是干什么的
:h i_<Up>           查询插入模式下方向键上是干什么的
:h pattern.txt      正则表达式帮助
:h eval             脚本编写帮助
:h function-list    查看 VimScript 的函数列表 
:h windows.txt      窗口使用帮助
:h tabpage.txt      标签页使用帮助
:h +timers          显示对 +timers 特性的帮助
:h :!               查看如何运行外部命令
:h tips             查看 Vim 内置的常用技巧文档
:h set-termcap      查看如何设置按键扫描码
:viusage            NORMAL 模式帮助
:exusage            EX 命令帮助
:version            显示当前 Vim 的版本号和特性


##############################################################################
# 外部命令
##############################################################################

:!ls                运行外部命令 ls，并等待返回
:r !ls              将外部命令 ls 的输出捕获，并插入到光标后
:w !sudo tee %      sudo以后保存当前文件
:call system('ls')  调用 ls 命令，但是不显示返回内容
:!start notepad     Windows 下启动 notepad，最前面可以加 silent
:sil !start cmd     Windows 下当前目录打开 cmd
:%!prog             运行文字过滤程序，如整理 json格式 :%!python -m json.tool


##############################################################################
# Quickfix 窗口
##############################################################################

:copen              打开 quickfix 窗口（查看编译，grep等信息）
:copen 10           打开 quickfix 窗口，并且设置高度为 10
:cclose             关闭 quickfix 窗口
:cfirst             跳到 quickfix 中第一个错误信息
:clast              跳到 quickfix 中最后一条错误信息
:cc [nr]            查看错误 [nr]
:cnext              跳到 quickfix 中下一个错误信息
:cprev              跳到 quickfix 中上一个错误信息


##############################################################################
# 拼写检查
##############################################################################

:set spell          打开拼写检查
:set nospell        关闭拼写检查
]s                  下一处错误拼写的单词
[s                  上一处错误拼写的单词
zg                  加入单词到拼写词表中
zug                 撤销上一次加入的单词
z=                  拼写建议


##############################################################################
# 代码折叠
##############################################################################

za                  切换折叠
zA                  递归切换折叠
zc                  折叠光标下代码
zC                  折叠光标下所有代码
zd                  删除光标下折叠
zD                  递归删除所有折叠
zE                  删除所有折叠
zf                  创建代码折叠
zF                  指定行数创建折叠
zi                  切换折叠
zm                  所有代码折叠一层
zr                  所有代码打开一层
zM                  折叠所有代码，设置 foldlevel=0，设置 foldenable
zR                  打开所有代码，设置 foldlevel 为最大值
zn                  折叠 none，重置 foldenable 并打开所有代码
zN                  折叠 normal，重置 foldenable 并恢复所有折叠
zo                  打开一层代码
zO                  打开光标下所有代码折叠


##############################################################################
# 宏录制
##############################################################################

qa                  开始录制名字为 a 的宏
q                   结束录制宏
@a                  播放名字为 a 的宏
@@                  播放上一个宏
@:                  重复上一个ex命令（即冒号命令）


##############################################################################
# 其他命令
##############################################################################

CTRL-X CTRL-F       插入模式下文件路径补全
CTRL-X CTRL-O       插入下 Omnifunc 补全
CTRL-X CTRL-N       插入模式下关键字补全
CTRL-X CTRL-E       插入模式下向上滚屏
CTRL-X CTRL-Y       插入模式下向下滚屏
CTRL-E              向上滚屏
CTRL-Y              向下滚屏
CTRL-G              显示正在编辑的文件名，以及大小和位置信息
g CTRL-G            显示文件的：大小，字符数，单词数和行数，可视模式下也可用
zz                  调整光标所在行到屏幕中央
zt                  调整光标所在行到屏幕上部
zb                  调整光标所在行到屏幕下部
ga                  显示光标下字符的 ascii 码或者 unicode 编码
g8                  显示光标下字符的 utf-8 编码字节序
gi                  回到上次进入插入的地方，并切换到插入模式
K                   查询光标下单词的帮助
ZZ                  保存文件（如果有改动的话），并关闭窗口
ZQ                  不保存文件关闭窗口
CTRL-PgUp           上个标签页，GVim OK，部分终端软件需设置对应键盘码
CTRL-PgDown         下个标签页，GVim OK，部分终端软件需设置对应键盘码
CTRL-R CTRL-W       命令模式下插入光标下单词
CTRL-INSERT         复制到系统剪贴板（GVIM）
SHIFT-INSERT        粘贴系统剪贴板的内容（GVIM）
:set ff=unix        设置换行为 unix
:set ff=dos         设置换行为 dos
:set ff?            查看换行设置
:set nohl           清除搜索高亮
:set termcap        查看会从终端接收什么以及会发送给终端什么命令
:set guicursor=     解决 SecureCRT/PenguiNet 中 NeoVim 局部奇怪字符问题
:set t_RS= t_SH=    解决 SecureCRT/PenguiNet 中 Vim8.0 终端功能奇怪字符
:set fo+=a          开启文本段的实时自动格式化
:earlier 15m        回退到15分钟前的文件内容
:.!date             在当前窗口插入时间
:%!xxd              开始二进制编辑
:%!xxd -r           保存二进制编辑
:r !curl -sL {URL}  读取 url 内容添加到光标后
:g/^\s*$/d          删除空行
:g/green/d          删除所有包含 green 的行
:v/green/d          删除所有不包含 green 的行
:g/gladiolli/#      搜索单词打印结果，并在结果前加上行号
:g/ab.*cd.*efg/#    搜索包含 ab,cd 和 efg 的行，打印结果以及行号
:v/./,/./-j         压缩空行
:Man bash           在 Vim 中查看 man，先调用 :runtime! ftplugin/man.vim 激活
/fred\|joe          搜索 fred 或者 joe
/\<\d\d\d\d\>       精确搜索四个数字
/^\n\{3}            搜索连续三个空行


##############################################################################
# Plugin - https://github.com/tpope/vim-commentary
##############################################################################

gcc                 注释当前行
gc{motion}          注释 {motion} 所标注的区域，比如 gcap 注释整段
gci{                注释大括号内的内容
gc                  在 Visual Mode 下面按 gc 注释选中区域
:7,17Commentary     注释 7 到 17 行


##############################################################################
# Plugin - https://github.com/junegunn/vim-easy-align
##############################################################################

:EasyAlign =        以第一个匹配的=为中心对齐
:EasyAlign *=       匹配并且对齐所有=


##############################################################################
# Plugin - https://github.com/tpope/vim-unimpaired
##############################################################################

[space              向上插入空行
]space              向下插入空行
[e                  替换当前行和上一行
]e                  替换当前行和下一行
[x                  XML 编码
]x                  XML 解码
[u                  URL 编码
]u                  URL 解码
[y                  C 字符串编码
]y                  C 字符串解码
[q                  上一个 quickfix 错误
]q                  下一个 quickfix 错误
[Q                  第一个 quickfix 错误
]Q                  最后一个 quickfix 错误
[f                  切换同目录里上一个文件
]f                  切换同目录里下一个文件
[os                 设置 :set spell
]os                 设置 :set nospell
=os                 设置 :set invspell
[on                 显示行号
]on                 关闭行号
[ol                 显示回车和制表符 :set list
]ol                 不显示回车和制表符 :set nolist
[b                  缓存切换到上一个文件，即 :bp
]b                  缓存切换到下一个文件，即 :bn
[B                  缓存切换到第一个文件，即 :bfirst
]B                  缓存切换到最后一个文件，即 :blast


##############################################################################
# Plugin - https://github.com/skywind3000/asyncrun.vim
##############################################################################

:AsyncRun ls        异步运行命令 ls 结果输出到 quickfix 使用 :copen 查看
:AsyncRun -raw ls   异步运行命令 ls 结果不匹配 errorformat


##############################################################################
# Plugin - https://github.com/gaving/vim-textobj-argument
##############################################################################

cia                 改写函数参数
caa                 改写函数参数（包括逗号分隔）
dia                 删除函数参数
daa                 删除函数参数（包括逗号分隔）
via                 选取函数参数
vaa                 选取函数参数（包括逗号分隔）
yia                 复制函数参数
yaa                 复制函数参数（包括逗号分隔）


##############################################################################
# 网络资源
##############################################################################

最新版本            https://github.com/vim/vim   
Windows 最新版      https://github.com/vim/vim-win32-installer/releases
插件浏览            http://vimawesome.com
reddit              https://www.reddit.com/r/vim/
正确设置 ALT/BS 键  http://www.skywind.me/blog/archives/2021
视频教程            http://vimcasts.org/
中文帮助            http://vimcdoc.sourceforge.net/doc/help.html
中文版入门到精通    https://github.com/wsdjeg/vim-galore-zh_cn
五分钟脚本入门      http://www.skywind.me/blog/archives/2193
脚本精通            http://learnvimscriptthehardway.stevelosh.com/
中文脚本帮助        vimcdoc.sourceforge.net/doc/eval.html
十六年使用经验      http://zzapper.co.uk/vimtips.html
配色方案            http://vimcolors.com/


##############################################################################
# TIPS
##############################################################################

- 永远不要用 CTRL-C 代替 <ESC> 完全不同的含义，容易错误中断运行的后台脚本
- 很多人使用 CTRL-[ 代替 <ESC>，左手小指 CTRL，右手小指 [ 熟练后很方便
- 某些终端中使用 Vim 8 内嵌终端如看到奇怪字符，使用 :set t_RS= t_SH= 解决
- 某些终端中使用 Vim 8.2+ 会看到一些奇怪字符，使用 :set t_TI= t_TE= 解决
- 某些终端中使用 NeoVim 如看到奇怪字符，使用 :set guicursor= 解决
- 使用 MS-Terminal 如果进入 Vim/NVim 会默认替换模式设置 :set t_u7= 解决
- 多使用 ciw, ci[, ci", ci( 以及 diw, di[, di", di( 命令来快速改写/删除文本
- 在行内左右移动光标时，多使用w b e或W B E，而不是h l或方向键，这样会快很多
- SHIFT 相当于移动加速键， w b e 移动光标很慢，但是 W B E 走的很快
- 自己要善于总结新技巧，比如移动到行首非空字符时用 0w 命令比 ^ 命令更容易输入
- 在空白行使用 dip 命令可以删除所有临近的空白行，viw 可以选择连续空白
- 缩进时使用 >8j  >}  <ap  >ap  =i}  == 会方便很多
- 插入模式下，当你发现一个单词写错了，应该多用 CTRL-W 这比 <BackSpace> 快
- y d c 命令可以很好结合 f t 和 /X 比如 dt) 和 y/end<cr>
- c d x 命令会自动填充寄存器 "1 到 "9 , y 命令会自动填充 "0 寄存器
- 用 v 命令选择文本时，可以用 o 掉头选择，有时很有用
- 写文章时，可以写一段代码块，然后选中后执行 :!python 代码块就会被替换成结果
- 搜索后经常使用 :nohl 来消除高亮，使用很频繁，可以 map 到 <BackSpace> 上
- 搜索时可以用 CTRL-R CTRL-W 插入光标下的单词，命令模式也能这么用
- 映射按键时，应该默认使用 noremap ，只有特别需要的时候使用 map
- 当你觉得做某事很低效时，你应该停下来，u u u u 然后思考正确的高效方式来完成
- 用 y复制文本后，命令模式中 CTRL-R 然后按双引号 0 可以插入之前复制内容
- 某些情况下 Vim 绘制高亮慢，滚屏刷新慢可以试试 set re=1 使用老的正则引擎
- Windows 下的 GVim 可以设置 set rop=type:directx,renmode:5 增强显示


##############################################################################
# References
##############################################################################

https://github.com/groenewege/vimrc/blob/master/vim_cheat_sheet.txt
http://blog.g-design.net/post/4789778607/vim-cheat-sheet
http://www.keyxl.com/aaa8263/290/VIM-keyboard-shortcuts.htm
http://jmcpherson.org/editing.html
http://www.fprintf.net/vimCheatSheet.html
http://www.ouyaoxiazai.com/article/24/654.html
http://bbs.it-home.org/thread-80794-1-1.html
http://www.lpfrx.com/wp-content/uploads/2008/09/vi.jpg
http://michael.peopleofhonoronly.com/vim/
https://github.com/hobbestigrou/vimtips-fortune/blob/master/fortunes/vimtips
https://github.com/glts/vim-cottidie/blob/master/autoload/cottidie/tips



# vim: set ts=4 sw=4 tw=0 noet noautoindent fdm=manual :

```
