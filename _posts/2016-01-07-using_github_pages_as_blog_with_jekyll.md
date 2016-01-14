---
layout: post
title:  "使用 GitHub Pages & Jekyll 作為部落格"
date:   2016-01-07 04:47:35
categories: github
---

![Octojekyll](https://jekyllrb.com/img/octojekyll.png)

# 本文使用的設備及作業系統 #
- PC: MacBook Pro (Retina, Mid 2012)
- OS: Mac OS X El Capitan

# 0x00 預先準備 #
- GitHub 帳號
- [GitHub Desktop](https://desktop.github.com)
- 安裝 Xcode Command Line Tool
{% highlight sh %}
$ xcode-select --install
{% endhighlight %}
- 確認 Ruby 版本為 2.0 以上
{% highlight sh %}
$ ruby --version
{% endhighlight %}
+ 路徑設定
1. 在家目錄底下建立 `Sites` 資料夾  
（若有其它習慣路徑請自行修改）
2. 於 `Sites` 底下建立放置 GitHub Pages 用的資料夾 `GitHub-Pages`  
 (若有自己喜好的名字可自行修改)
3. 於 `GitHub-Pages` 中建立一個檔名為 `Gemfile` 的純文字檔，並於內容寫入以下兩行
{% highlight text %}
source 'https://rubygems.org'  
gem 'github-pages'
{% endhighlight %}

# 0x01 安裝 bundler 以及 Jekyll #
打開終端機 `Terminal` 輸入以下指令安裝 `bundler`
{% highlight sh %}
$ sudo gem install bundler
{% endhighlight %}

切換至目的資料夾 `__PATH__` (ex: `~/Sites/GitHub-Pages`，若有不同請自行替換)  
利用 `bundler` 以及剛剛建立的 Gemfile 來安裝 Jekyll
{% highlight sh %}
$ cd __PATH__
$ bundle install
{% endhighlight %}

# 0x02 設定 Jekyll #
建立 jekyll project (將以下 `__USERNAME__` 換成自己的 GitHub 帳號 ex:`Nedval`)
{% highlight sh %}
$ jekyll new __USERNAME__.github.io
{% endhighlight %}

# 0x03 於本機執行 Jekyll #
切換至剛才建立的專案資料夾並執行 jekyll server
{% highlight sh %}
$ cd __USERNAME__.github.io
$ bundle exec jekyll serve
{% endhighlight %}
這樣就可以在瀏覽器輸入 `http://localhost:4000` 看到初始化的 GitHub Pages

![Jekyll Screen Shot]({{ site.url }}/images/1451853885.png)

# 0x04 利用 GitHub Desktop 上傳至 GitHub #  
打開 GitHub Desktop  
點選左上角的 `+` 號後，選擇 `Add`  
![GitHub Desktop Screen Shot]({{ site.url }}/images/1451852695.png)

接著選擇剛才建立的 `__USERNAME__.github.io` 資料夾  
將所有檔案 Commit 完之後，點選右上角的 `Publish`  
![GitHub Desktop Screen Shot]({{ site.url }}/images/1451853670.png)

當 Publish 完成之後就可以在瀏覽器中使用 `http://__USERNAME__.github.io` 連結看到剛才建立的頁面了

# 0xFF 參考資料 #
- [Using Jekyll with Pages](https://help.github.com/articles/using-jekyll-with-pages/)
