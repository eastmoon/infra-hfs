# HTTP File Server

本專案是基於 Apache 為基礎設置簡易的文件服務器。

HTTP File Server ( HTTP 文件服務器 )，是專門用於發布和共享文件設計了一個免費的 Web 服務器，然而 HFS 是歷史悠久的稱呼，因其設計簡單，在 Apache 被設定為基礎功能，亦稱為 Directory Browsing；現今直接使用 HFS 建置的方式，多會替代為啟用 Apache 來設置。

Apaxy 是採用 Apache 的 [Autoindex](https://httpd.apache.org/docs/2.4/mod/mod_autoindex.html) 模組設計的 Http File Server，其設計是利用 .htaccess 檔案規劃目錄操作與呈現方式。

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

### Timezone

原則上，Apaxy 是經由 Apache 使用伺服器的 ls 指令取得目錄中的檔案資訊，並將此資訊經由 .htaccess 規範呈現，因此，若要調整時區 ( timezone ) 則需指定容器的時區，以此呈現。

```
export TZ='Asia/Taipei'
```

若使用容器啟動服務，則可透過以下指令設定時區

```
docker run -ti --rm -e "TZ=Asia/Taipei" apaxy
```

### Nginx upload API

基於 Nginx 建置一個 Upload 並將檔案共享於 ```share``` 目錄，其主要設計基於 [ngx_http_dav_module](https://nginx.org/en/docs/http/ngx_http_dav_module.html) 模組所實踐的 [WebDAV](https://zh.wikipedia.org/zh-tw/WebDAV) 規範。

+ 開啟服務：```upload up```
+ 關閉服務：```upload down```

測試指令：

```
## 上傳檔案
curl -T README.md http://localhost:8081/upload/readme.md

## 刪除檔案
curl -X DELETE http://localhost:8081/upload/readme.md
```
> 雖然有設定 MKCOL、COPY、MOVE 方式，但參考文獻[Samples of WebDAV requests with curl and wget](https://github.com/WebDAVDevs/webdav-request-samples/blob/master/webdav_curl.md)操作並無法正常

## 參考

+ [HTTP File Server - wiki](https://en.wikipedia.org/wiki/HTTP_File_Server)
    - [網頁伺服器 (Web Server) + FTP](http://dic.vbird.tw/linux_server/unit10.php)
+ [Directory Browsing - sciencedirect](https://www.sciencedirect.com/topics/computer-science/directory-browsing)
+ [Why Is Directory Listing Dangerous?](https://www.acunetix.com/blog/articles/directory-listing-information-disclosure/)
