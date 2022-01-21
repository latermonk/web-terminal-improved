



#   web-based  terminal


##   浏览器将主机的信息(ip, 用户名, 密码, 请求的终端大小等)进行加密, 传给后台, 并通过HTTP请求与后台协商升级协议. 协议升级完成后, 后续的数据交换则遵照web Socket的协议.
##  后台将HTTP请求升级为web Socket协议, 得到一个和浏览器数据交换的连接通道
##  后台将数据进行解密拿到主机信息, 创建一个SSH 客户端, 与远程主机的SSH 服务端协商加密, 互相认证, 然后建立一个SSH Channel
##  后台和远程主机有了通讯的信道, 然后后台将终端的大小等信息通过SSH Channel请求远程主机创建一个 pty(伪终端), 并请求启动当前用户的默认 shell
##  后台通过 Socket连接通道拿到用户输入, 再通过SSH Channel将输入传给pty, pty将这些数据交给远程主机处理后按照前面指定的终端标准输出到SSH Channel中, 同时键盘输入也会发送给SSH Channel
##  后台从SSH Channel中拿到按照终端大小的标准输出后又通过Socket连接将输出返回给浏览器, 由此变实现了Web Terminal






















#  backend

https://github.com/chengjoey/web-terminal
