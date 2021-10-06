# HTTP File Server

本專案是基於 Apache 為基礎設置簡易的文件服務器。

HTTP File Server ( HTTP 文件服務器 )，是專門用於發布和共享文件設計了一個免費的 Web 服務器，然而 HFS 是歷史悠久的稱呼，因其設計簡單，在 Apache 被設定為基礎功能，亦稱為 Directory Browsing；現今直接使用 HFS 建置的方式，多會替代為啟用 Apache 來設置。

## 建置

### Apache HTTP Server

基於 Apache 建置一個 HFS 並分享 ```share``` 內容

+ 開啟服務：```apache up```
+ 關閉服務：```apache down```

### Theme

Apache 的 HFS，可經由設定 ```.htaccess``` 來規劃不同風格的 HFS，以下為參考範例：

+ [Apaxy](https://oupala.github.io/apaxy/)
+ [Apache-Directory-Listing](https://github.com/ramlmn/Apache-Directory-Listing)
+ [CSS Styling Apache Directory Listings.](https://www.linickx.com/css-styling-apache-directory-listings)

在此則基於 Apaxy 專案建置一個 HFS 並分享 ```share``` 內容

+ 開啟服務：```apaxy up```
+ 關閉服務：```apaxy down```

由於 Apaxy 的設計結構，不建議直接替換在根目錄位置，避免替換掉相關樣式設定，且可依據掛載來建立多個分享子目錄。

## 參考

+ [HTTP File Server - wiki](https://en.wikipedia.org/wiki/HTTP_File_Server)
    - [網頁伺服器 (Web Server) + FTP](http://dic.vbird.tw/linux_server/unit10.php)
+ [Directory Browsing - sciencedirect](https://www.sciencedirect.com/topics/computer-science/directory-browsing)
+ [Why Is Directory Listing Dangerous?](https://www.acunetix.com/blog/articles/directory-listing-information-disclosure/)
