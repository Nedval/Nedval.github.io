---
layout: post
title:  "利用 CloudFlare 為 GitHub Pages 加上免費的 SSL 憑證"
date:   2016-01-14 20:36:47
categories: github
---

![CloudFlare](https://www.cloudflare.com/logo/logo-guideline-illustrations_background-white.png)

# 0x00 預先準備 #
- 已經擁有 GitHub Pages
- 擁有自己的域名 Ex: `nedval.me`
- 使用 [CloudFlare](https://www.cloudflare.com) 作為 DNS
+ 設定一個子域名給 GitHub Pages
1. 在 GitHub Pages 的根目錄下建立一個檔名為 `CNAME` 的檔案
2. 內容為子域名 Ex: `pages.nedval.me`
3. 上傳至 GitHub  

# 0x01 在 CloudFlare 中新增 CNAME 紀錄 #  
登入 CloudFlare 後  
選擇上方的 DNS 頁籤  
接著就可以新增一筆 CNAME 的子網域的記錄  
並指向 GitHub Pages 的 Domain Ex: `__USERNAME__.github.io`  
以本站為例  
![CloudFlare Screen Shot]({{ site.url }}/images/1452776113.png)

設定後，選擇右方的那朵雲  
![CloudFlare Screen Shot]({{ site.url }}/images/1452776202.png)

接著選擇上方的 Crypto 頁籤  
將 SSL 的部分選擇 Flexible  
![CloudFlare Screen Shot]({{ site.url }}/images/1452777848.png)

這樣就可以用 https 以及自訂的子網域開啟 GitHub Pages 了  

# 0x02 設定自動轉址 #
可以在 CloudFlare 中設定若 client 端用 http 協定連線時
自動轉至 https 協定

選擇 CloudFlare 上方的 Pages Rules 頁籤
接著新增一筆 rule 將 http 的網址 forward 至 https
![CloudFlare Screen Shot]({{ site.url }}/images/1452778433.png)

# 0xFF 參考資料 #
- [Setting up a custom domain with GitHub Pages](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages/)
- [CloudFlare one-click SSL](https://www.cloudflare.com/ssl/)
