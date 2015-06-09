# Node

## 切換 NodeJS 版本

### 安裝 n Node Module

    $   sudo npm install -g n


### 切換 NodeJS

用法參考：

```
Usage:
n                            # Output versions installed
n latest                     # Install or activate the latest node release
n stable                     # Install or activate the latest stable node release
n <version>                  # Install node <version>
n use <version> [args ...]   # Execute node <version> with [args ...]
n bin <version>              # Output bin path for <version>
n rm <version ...>           # Remove the given version(s)
n --latest                   # Output the latest node version available
n --stable                   # Output the latest stable node version available
n ls                         # Output the versions of node available

```

#### 安裝並切換到某 n.r 版本

先安裝 node 0.10.33 版本；並切換到此版本。

    $ n 0.10.33
