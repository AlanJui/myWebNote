# angular-fullstack

## 建立 Local Repo

    $ git init
    $ git add .
    $ git commit -m "Initial Project"

## 建立 Remote Repo

在 Bitbucket 建立 Repo ， RUL: git@bitbucket.org:AlanJui/angular-fullstack.git

## 首次自 Local Repo 存入 Remote Repo

```
$ git remote add origin git@bitbucket.org:AlanJui/angular-fullstack.git

$ git push -u origin --all # pushes up the repo and its refs for the first time
Branch master set up to track remote branch master from origin.
Everything up-to-date

$ git push -u origin --tags # pushes up any tags
Everything up-to-date

$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```


## 自 Local Repo 存入 Remote Repo

