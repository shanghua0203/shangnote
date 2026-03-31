# AI小工具

## SSH-server配置
```
# ssh server
sudo apt update && sudo apt install openssh-server -y
sudo systemctl [動作] ssh
# enable：開機自動啟動
# start、stop、restart、status、disable
```

### 解析port number
```
netstat -tulnp 
```
- t：tcp
- u：udp
- l：listen
- n：不解析
- p：process id

## 無密碼登入
本地端私鑰作為鑰匙，在遠端放置公鑰作為鎖頭，難以解，最安全  
### 在linux上執行
```
mkdir -p ~/.ssh
cd ~/.ssh
vimauthorized_keys #貼上windows上的.ssh/id_rsa.pub公鑰
```

## opencode
