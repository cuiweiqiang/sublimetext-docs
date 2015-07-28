---
layout: default
title: "Package 和 Plugin"
---
## <span id="package">Package</span>

Package 放在 _Packages/_ 目录下，主要用来组织同类型功能的档案，通常一个典型的 package 里面会包含以下这些档案：

* 建构系统（Build System）：_.sublime-build_
* 快捷键设定：_.sublime-keymap_
* 巨集：_.sublime-macro_
* 选单栏：_.sublime-menu_
* 外挂程式：_.py_
* preferences：_.tmPreferences_
* 选项设定：_.sublime-settings_
* 语法定义：_.tmLanguage_
* 语法片段：_.sublime-snippet_
* 布景主题：_.sublime-theme_

<!-- TODO: 不知道该怎么翻 .tmPreferences 这部份…… -->

有些 package 可能只是存放一些档案，提供资料给其他外挂或 Sublime Text 的核心功能，例如拼音检查就是使用 _PackagesLanguage - English_ 这个 package 目录。

## <span id="plugin">Plugin</span>

Sublime Text 2 的外挂可以用 Python 语言开发，如果你擅长使用 Python 便可以自行开发扩充 Sublime Text 的功能，让它变得更好用！外挂可以使用已经存在的[指令](/customization#commands)，或是建立自己的指令。

你可以将别人写好的外挂，或是自己写的外挂脚本，放在以下这几个位置，都可以被 Sublime Text 读取到：

* _Packages_
* _Packages/&lt;pkg_name&gt;/_

因此如果将外挂放在非以上这些目录，或是更深入的目录内，就会无法被读取到，我建议都放在 _User/_ 目录下比较好备份管理。

更多外挂的参考资料：[Plugins](http://docs.sublimetext.info/en/latest/extensibility/plugins.html)

## <span id="package-control">什么是 Package Control</span>

![sublime-package-control](/images/sublime-package-control.png)

[Package Control](http://wbond.net/sublime_packages/package_control) 不是内建功能，事实上它只是 Sublime Text 2 的一个 package，由 [Will Bond](http://wbond.net/) 所开发。因为实在是太方便了所以几乎与 Sublime Text 2 紧密结合在一起，成为安装 Sublime Text 2 时第一个必装的 package。

Package Control 是功能相当完整的 package manager，让搜寻、安装跟移除 Sublime Text  package 变得相当方便，协助自动更新外挂，也因此几乎所有的外挂开发者，都会将自己的作品提交到 Package Control 上。

这个概念就像是用 Google Chrome 的 Chrome Web Store 安装扩充套件吧！

## <span id="install-package-control">安装 Package Control</span>

还记得先前介绍过的 [Python 控制台](/basic-concepts/#python-console-and-python-api)吗？快捷键 <kbd>Ctrl</kbd> + <kbd>`</kbd>，或是从选单栏选择 _View_ >> _Show Console_ 打开它，将以下程式码复制贴上到控制台中，然后按下输入：

    import urllib2,os; pf='Package Control.sublime-package'; ipp=sublime.installed_packages_path(); os.makedirs(ipp) if not os.path.exists(ipp) else None; urllib2.install_opener(urllib2.build_opener(urllib2.ProxyHandler())); open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); print('Please restart Sublime Text to finish installation')

Package Control 将会开始安装，完成时可能需要重新启动 Sublime Text 2。

### <span id="install-package">安装 Package</span>

![install-package](/images/sublime-package-control-install.gif)

用快捷键 <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> 打开指令面板，输入「install package」找到正确指令后按下输入，便会列出 Package Control 上所有可安装的 packages，搜寻要安装的 package 按下输入即开始安装。

### <span id="remove-package">移除 Package</span>

与[安装 Package](/package-control#remove-package) 方法相同，打开指令面板后输入「remove package」，会列出所有已安装的 packages，从这里选择需要删除的 package。

注意一点，如果有相关的设定档放在 _Package/User/_ 目录下，并不会自动被删除，这部份需要自己手动移除。
