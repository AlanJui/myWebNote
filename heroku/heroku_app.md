# 建立 Heroku App

## 以 CLI 指令建立 App

### (1) App 名稱由自己決定

```
$ heroku apps:create yo-bangular

Creating yo-bangular... done, stack is cedar-14
https://yo-bangular.herokuapp.com/ | https://git.heroku.com/yo-bangular.git
Git remote heroku added

```

### (2) App 名稱由 Heroku 自動決定

```
$ heroku create

Creating thawing-dawn-3593... done, stack is cedar-14
https://thawing-dawn-3593.herokuapp.com/ | https://git.heroku.com/thawing-dawn-3593.git
Git remote heroku added

```

## 在 Heroku 平台透過 GUI 介面建立 App

登入 Heroku 官網，建立App

    * Name: my-angular-fs
    * Heroku Git Repo: git@heroku.com:my-angular-fs.git

## 建立 Local Repo 與 Heroku App 的連結

回到 Local Repo，執行下列指令：

```
$ heroku login
Enter your Heroku credentials.
Email: alanjui.1960@gmail.com
Password (typing will be hidden):
Authentication successful.
```

```
$ heroku git:remote -a my-angular-fs
Git remote heroku added
```

## 設定 Mongodb

### 加入 MongoDB Add-ons

```
$ heroku addons:add mongolab --app my-angular-fs
Welcome to MongoLab.  Your new subscription is being created and will be available shortly.  Please consult the MongoLab Add-on Admin UI to check on its progress.
Use `heroku addons:docs mongolab` to view documentation.
```

### 設定 Heroku 為 Production 環境

```
$ heroku config:set NODE_ENV=production
```







