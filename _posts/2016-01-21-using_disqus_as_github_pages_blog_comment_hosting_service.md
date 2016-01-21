---
layout: post
title:  "使用 DISQUS 作為 GitHub Pages 的留言系統"
date:   2016-01-21 23:28:24
categories: github
---

![DISQUS](https://a.disquscdn.com/dotcom/d-85f7dd1/img/brand/disqus-logo-blue-white.png)

# 0x00 預先準備 #
- 註冊 [DISQUS](https://disqus.com)

# 0x01 新增站台 #  
登入 DISQUS 後前往 [Engage](https://publishers.disqus.com/engage)
點選 `Start Using Engage`  
![DISQUS Screen Shot]({{ site.url }}/images/1453387559.png)

將站台資料填寫完畢  
![DISQUS Screen Shot]({{ site.url }}/images/1453387651.png)

# 0x02 取得嵌入留言板需要的程式碼 #
完成前一個步驟之後  
會進到以下頁面  
![DISQUS Screen Shot]({{ site.url }}/images/1453387828.png)

選擇 `Universal Code`
將第一段程式碼複製下來  
![DISQUS Screen Shot]({{ site.url }}/images/1453387899.png)

# 0x03 修改樣板 #
在 Jekyll 的安裝的路徑底下找到 `_config.yml` 檔案
找地方加上
{% highlight text %}
comments: true
{% endhighlight %}

接著找到 `_layouts/post.html` 檔案  
在檔案的最下方新增兩行程式碼  

{% raw %}
	{% if site.comments %}
	//add the "Universal Embed Code" here
	{% endif %}
{% endraw %}

並且在那兩行程式碼中間插入
將剛剛複製下來的 [Universal Embed Code](http://docs.disqus.com/developers/universal/)

# 0x04 修改 Universal Code #

剛才複製的 Universual Code 中有一段為
{% highlight js %}
/*
var disqus_config = function () {
    this.page.url = PAGE_URL; // Replace PAGE_URL with your page's canonical URL variable
    this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
{% endhighlight %}

需要將註解拿掉並且把 `PAGE_URL` 修改為 `{% raw %}"{{ site.url }}{{ page.url }}"{% endraw %}`
修改後的程式碼為  
{% highlight js %}
var disqus_config = function () {
    this.page.url = "{% raw %}{{ site.url }}{{ page.url }}{% endraw %}";
};
{% endhighlight %}

# 0x05 上傳 GitHub #  
  
將修改後的樣板上傳之後應該就會看到 DISQUS 的留言區塊囉！  
![DISQUS Screen Shot]({{ site.url }}/images/1453389903.png)

# 0xFF 參考資料 #

- [Jekyll Installation Instructions](https://help.disqus.com/customer/portal/articles/472138-jekyll-installation-instructions)