# NPM

安裝
====

### 安裝最新版本

```
    $ npm install express
```

### 安裝最新版本且要記錄

安裝PKG的最新版本，同時PKG的「版本編號」，需記錄至package.json檔案中。

#### 記錄到「dependencies」

```
    $ npm install --save express
```

#### 記錄到「devDependencies」

```
    $ npm install --save-dev gulp-ruby-sass
```

### 指明特定版本安裝

```
    $ npm install --save-dev gulp-ruby-sass@0.7.1
```


### 以系統管理者權限安裝

```
    $ sudo npm install -g yo
```


管理
====

### 查詢版本

#### 查詢npm的版本

```
    $ npm -v
```


#### 查詢某PKG，所有發行的版本

```
    $ npm view gulp-ruby-sass
```

#### 查詢某PKG，最近發行的版本

```
    $ npm view gulp-ruby-sass version
```

### 更新版本

更新npm到最新版本。

```
    $   sudo npm install -g npm@latest
```

### 更新專案中所有PKG到最新版本

進入「專案」所在之「資料夾路徑」；其中含package.json檔案，記錄專案已安裝之PKG。

```
    $ npm update
```

### 更新某PKG到最新版本

```
    $ npm update gulp-ruby-sass
```


