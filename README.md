# 「Sublime Text 手册」网站的源码

Sublime Text 手册网址：[http://docs.sublimetext.tw/](http://docs.sublimetext.tw/)

## 本地构建

    $ git clone https://github.com/chinghanho/sublimetext-docs.git
    $ cd sublimetext-docs
    $ bundle install
    $ middleman server

打开浏览器访问 [127.0.0.1:4567](http://127.0.0.1:4567)，That's all。

## 发现错误要怎么处理？

1. 点一下右上角的按钮，Fork it！
2. 建立一个你自己的 feature branch，例如：`git checkout -b typo-hotfix`
3. 提交你所做的变更：`git commit -am "鼎立相助 -> 鼎力相助"`
4. push 到你 GitHub 上的 repo：`git push origin typo-hotfix`
5. 发一个 Pull Request 给我吧！补上清楚的说明让我知道你为什么要修改。

除此之外你也可以在 [issues](https://github.com/chinghanho/sublimetext-docs/issues) 提出建议或疑问，是有关于这个网站的问题，不是 Sublime Text 的使用问题。XD

感谢！

## 授权

<a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/deed.zh_TW"><img alt="创建 CC 授权条款" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/3.0/88x31.png" /></a><br />本站內容系采用<a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/deed.zh_TW">创建 CC 姓名標示-相同方式分享 3.0 Unported 授权条款</a>授权。允许使用者重制、散布、传输及修改本著作（包括商业性利用）。使用时应附上本站链接，引用內容的授权请參见引用出处。
