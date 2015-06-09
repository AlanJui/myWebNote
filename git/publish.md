# Publish

## 發行到 Git Pages

先確定 .gitignore 檔案中的設定，不可以有「dist」；若有刪除之動作，需記得 commit 。

    $ git commit -am "Remove dist/ from .gitignore"

（1）執行 build ，以便在 dist  目錄中，產生可發行之包裝。

    $ grunt serve:dist --force

（2）發行到 Git Pages

    $ git subtree push --prefix dist origin gh-pages

【附註】：

毋須依循 Git Pages 官網建議的作法，先在 GitHub 建立 gh-pages 的 Branch 。

若已在 GitHub 建立了 gh-pages branch ，可依下列作法刪除：

    $ git push origin --delete gh-pages

