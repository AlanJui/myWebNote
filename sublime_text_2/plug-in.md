# Plug-in

必裝的 Plug-in:

1. Emmet
2. HTML-CSS-JS Prettify
3. AutoFileName
4. GitGutter

## Emment

HTML Tag 輸入，自動化。

## HTML-CSS-JS Prettify

自動調整 HTML / CSS / JavaScript 檔案內容的「縮排」。

### GitHub

    https://github.com/victorporof/Sublime-HTMLPrettify

### 設定檔－.jsbeautifyrc

#### 修訂設定檔

  1. Ctrl+Shift+P or Cmd+Shift+P in Linux/Windows/OS X

  2. type htmlprettify, select Set Prettify Preferences

  3. 將 indent-size 自「4」改為「2」

```
    {
      "html": {
        ......
        ......
        "indent_size": 2, // Indentation size
        ......
        ......
      },
      "css": {
        ......
        ......
        "indent_size": 2, // Indentation size
        ......
        ......
      },
      "js": {
        ......
        ......
        "indent_size": 2, // Indentation size
        ......
        ......
      }
    }

```

## AutoFileName

對於「檔案」所在之 Path 路徑及 Filename 檔名，可協助使用者，自動完成輸入。

## GitGutter

與git整合，可自動識別檔案內容的「修訂」處：Add/Delete 。


