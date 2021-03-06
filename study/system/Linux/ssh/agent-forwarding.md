# Agent-forward

## 1. 理解：
一般用公钥登陆时都会在本地机器上进行运算，利用本地机器上的私钥验证身份。但是当我们通过跳板机连接远程机器的时候，跳板机上没有我们的私钥（也不应该有），这时候就做不了身份验证。除非我们在跳板机上也弄一套公私钥对，但这样就意味着我们的身份有两个了，并不是唯一的。通过ssh的agent-forwarding，可以解决这个问题，达到只用本地机器上一对公私钥就能到处登陆。

## 2. 操作：
1. 首先把公钥放在想要登陆的所有机器上。
2. 本地机器上运行：
```sh
ssh-agent bash
ssh-add <私钥位置>
ssh-add -l  # 查看已经添加的私钥
```
3. 然后从本地机器连接跳板机的时候用
```sh
ssh -A <远程跳板机器>
```
此后在跳板机上一切ssh的身份判断，都会转移到本地机器上进行，利用本地存在的私钥进行计算。