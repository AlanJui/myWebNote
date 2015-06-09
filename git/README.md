# Git

## 初次納管到遠端 Repo

先完成 GitHub Repo 的建置。建置時「選項」：（1）不加 gitignore；（2）不加 ReadMe 。

    $ git init

    $ git add .

    $ git commit -m "Initial Project"

    $ git tag -a "V0.1" -m "剛完成 Create Project , 最阁的狀態"

    $ git remote add origin git@github.com:AlanJui/myAngular.git

    $ git push -u origin master

    $ git push --tags

