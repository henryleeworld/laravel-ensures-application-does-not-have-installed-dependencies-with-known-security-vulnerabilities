# Laravel 11 確保應用程式沒有安裝已知安全漏洞的依賴套件

引入 roave 的 security-advisories 套件來擴增確保應用程式沒有安裝已知安全漏洞的依賴套件，如果有一個容易受到攻擊的依賴套件被駭客利用，就可能導致資料洩漏或伺服器被利用，且使用有漏洞的依賴套件，都會破壞應用程式的防護，讓各種攻擊形式接踵而來，使用第三方套件儘管可以節省開發時間，但必須能時時追蹤資安訊息，以便即時更新。

## 使用方式
- 把整個專案複製一份到你的電腦裡，這裡指的「內容」不是只有檔案，而是指所有整個專案的歷史紀錄、分支、標籤等內容都會複製一份下來。
```sh
$ git clone
```
- 將 __.env.example__ 檔案重新命名成 __.env__，如果應用程式金鑰沒有被設定的話，你的使用者 sessions 和其他加密的資料都是不安全的！
- 當你的專案中已經有 composer.lock，可以直接執行指令以讓 Composer 安裝 composer.lock 中指定的套件及版本。
```sh
$ composer install
```
- 產生 Laravel 要使用的一組 32 字元長度的隨機字串 APP_KEY 並存在 .env 內。
```sh
$ php artisan key:generate
```

----

## 畫面截圖
![](https://i.imgur.com/1ZggpAQ.png)
> 利用安裝的套件有相依套件的衝突來避免安裝已知安全漏洞的依賴套件
