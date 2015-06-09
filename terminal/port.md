# 解除Port佔用問題

## 檢查及排除問題SOP

（1）檢查 Port 3000 是否被佔用

```
＄ netstat -anp tcp | grep 3000
```

（2）檢查佔用 Port 3000 軟體的 PID

```
＄ lsof -i tcp:3000
```

（3）終止使用 Port 3000 的軟體

```
＄ kill <PID>
```

## 常用 Port No

* Node: 3000
* Node Debugger: 8080
* MongoDB: 27017


