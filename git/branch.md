# Branch

## 剛除 Remote Branch

適用於 Git V1.7 以後版本

    $ git push origin --delete <branchName>

## 開發新功能

### 建立新功能工作區

已進入 Master Branch

    $ git checkout -b signup

### 合併

    $ git checkout master
    $ git merege signup
    $ git branch -d signup

