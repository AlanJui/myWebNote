# Grunt

## Q & A
### 執行安裝時，發生 lock 問題

    npm install grunt


[解法]：

    sudo chown -R `whoami` ~/.npm
    sudo chown -R `whoami` /usr/local/lib/node_modules
    sudo chown -R `whoami` /usr/local
