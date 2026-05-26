# 0526

## ansible

### 特色
- **無代理程式碼架構**  
  目標主機（Managed Nodes）不需要安裝任何常駐程式（Daemon/Agent）。Ansible 完全依賴標準傳輸協定——Linux/Unix 使用 SSH（預設為 OpenSSH），Windows 使用 WinRM 或 WSMAn。這大幅減少了目標主機的資源消耗與安全漏洞風險。
- **宣告式語法**  
  使用者透過 YAML 格式定義系統的「最終期望狀態（Desired State）」，而非撰寫繁瑣的程序式指令（Imperative Commands）。Ansible 會自行判斷如何將系統從目前狀態轉移至目標狀態。
- **冪等性**  
  這是 Ansible 最核心的特性。同一個 Playbook 無論執行一次或一萬次，只要目標系統狀態與宣告相符，Ansible 就不會變更任何設定，確保系統的穩定性與一致性，避免重複設定引發的副作用。
- **推模式**  
  與 Puppet 或 Chef 的「拉模式 (Pull)」不同（端點主機定期向中央伺服器同步設定），Ansible 採用「推模式」。所有決策與指令皆由控制端（Control Node）主動發起並推送到目標主機，便於即時控管與稽核。

### 元件解析
```
+-------------------------------------------------------+
|                    Control Node                       |
|  +------------+  +-----------+  +------------------+  |
|  |  Playbook  |  | Inventory |  | Ansible Config   |  |
|  +-----+------+  +-----+-----+  +--------+---------+  |
|        |               |                 |            |
|        v               v                 v            |
|  +-------------------------------------------------+  |
|  |                 Ansible Core                    |  |
|  |     (Modules, Plugins, Execution Engine)        |  |
|  +----------------------+--------------------------+  |
+-------------------------|-----------------------------+
                          | SSH / WinRM
                          v
          +---------------+---------------+
          |                               |
          v                               v
+-------------------+           +-------------------+
|   Managed Node    |           |   Managed Node    |
|  (Linux Server)   |           | (Windows Server)  |
+-------------------+           +-------------------+
```

### 使用語法
```ansible [群組名稱] [模組名稱] -a "[參數]"```  
範例：```ansible server1 -m command -a "ip a s"  
**注意：**`command`適用設模組，不寫`-m command'也可以執行，可以變成-->  
`ansible server1 -a "ip a s"`

### 複雜指令(shell模組)
如果你想使用的指令比較複雜，裡面包含管線命令（|）或大於符號（>），用 command 模組會出錯，這時候就要改用 shell 模組：  
```
ansible ervers -m shell -a "ip a s | grep -A 3 ens33"
```  
也可以加上參數（例如 chdir），讓電腦先切換到 /tmp 資料庫資料夾，再執行 pwd 看路徑：
```
ansible servers -m shell -a "chdir=/tmp pwd"
回傳：
web | CHANGED | rc=0 >>
/tmp
db | CHANGED | rc=0 >>
/tmp
```

建立a.txt寫入haaaaa  
```
ansible servers -m shell -a "chdir=/tmp echo haaaaa > a.txt"
```
接著db和web裝置的root帳號下就有內容為haaaaa的a.txt檔案了  
- 不切換資料夾  
  ```
    ansible servers -m shell -a "echo haaaaa > /tmp/b.txt"
  ```
  
