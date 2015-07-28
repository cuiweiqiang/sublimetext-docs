---
layout: default
title: "基本概观"
---
## <span id="directories">目录结构</span>

### <span id="data-directory">Data 目录</span>

可携式版本（portable）的 Sublime Text 2 所有跟使用者有关的资料，都放在 _Data_ 目录下（_Sublime Text 2/Data_）；安装版本则因为系统平台的不同，预设路径是放在以下这些地方：

* Windows：_%APPDATA%\Sublime Text 2_
* OS X：_~/Library/Application Support/Sublime Text 2_
* Linux：_~/.config/sublime-text-2_

所有 Sublime Text 2 相关配置的档案，都放在这些目录下。<i class="icon-folder-open"></i>

### <span id="package-directory">Packages 目录</span>

![sublime-packages](/images/sublime-packages.png)

_Packages_ 目录就放在 _Data_ 目录下。

_Packages_ 目录非常重要，所有程式语言、标记语言的语法上色档案，以及各种客制化的外挂资源，全部都是放在这个目录底下。Sublime Text 2 的 package 意义上就像 Firefox 的 add-on、Google Chrome 的 extension，加强原本没有的功能，可由开发者透过 Sublime Text 2 的 API 用 Python 自行开发，请见 [Python 控制台与 Python API](#python-console-and-python-api)。

你可以直接从 Sublime Text 2 的选单：_Preferences_ >> _Browse Packages_ 开启系统中 _Packages_ 这个目录的位置，也可以用[指令面板（Command Palette）](/file-management-and-command-palette#command-palette)呼叫，虽然你目前可能还不知道这是什么，不过很快就会介绍到。

当你浏览这个目录的时候会看到很多程式语言的名字，里面通常放的都是支援这些语言的语法上色规则，或是巨集、自动完成的程式码片段等等，可是其中有两个看起来很不一样，那就是 _Default_、_User_ 这两个目录。

#### <span id="default-package">Default package</span>

_Packages/Default_ 是存放所有 Sublime Text 2 预设的程式、巨集、偏好设定的档案等等，这里的档案理论上都不应该去动它。

<!-- TODO: 加上中文化的连结。 -->

#### <span id="user-package">User package</span>

通常有些未封装的 package，或是自制的语法、巨集或外挂，那么 _Packages/User_ 是放置这些档案的最佳地点。

当 Sublime Text 2 进行软体更新时，不会去更改 _User_ 这个资料夹的档案，因此你的偏好设定、快捷键设定等等，都应该要放在这个地方，而不是去修改 Default 目录下的档案，这个部分会在[客制化](/customization)进一步说明。

## <span id="python-console-and-python-api">Python 控制台与 Python API</span>

这章节的资讯对有兴趣开发 Sublime Text 2 外挂的开发者比较有用，对于一般的编辑器使用者只需要知道，Sublime Text 能够让人用 Python 自行开发想要的功能。

在 Windows 和 Linux 上，Sublime Text 2 有内建的 Python 直译器，让开发者撰写外挂时，能够快速地检视设定，以及测试 API calls。这个内建的 Python 直译器只用来与外挂 API 互动，而不是用来做一般的程式开发；而在 OS X 上 Sublime Text 2 则是用系统内建的 Python，这意思就是说如果你更改了系统上的 Python 版本，很有可能会造成 Sublime Text 2 出现问题。

Python 控制台是内嵌在 Sublime Text 2 的一个小视窗，能够输入 Python 程式码然后执行它，而 Sublime Text 或是它的外挂也会从这里输出讯息，如果发现某个功能或是某个外挂没作用了，可以打开这个控制台找到错误讯息。

要打开 Sublime Text 2 的 Python 控制台可以用快捷键按下 <kbd>Ctrl</kbd> + <kbd>`</kbd>，或是从选单中选择 _View_ >> _Show Console_。

## <span id="textmate-compatibility">TextMate 相容</span>

Sublime Text 2 几乎能够完整地相容 Textmate 的 bundles 和配色主题，这个资讯对想从 TextMate 转用 Sublime Text 的使用者非常有用。

TextMate 是 OS X 上非常知名的编辑器，想当初曾有很多人为了它而买了 Mac，可见这魅力有多大！可是 TextMate 自己不争气，让许多曾经爱过它的人失望（那不包括我！XD）。<i class="icon-hand-up"></i>

TextMate 已经有发展相当成熟的社群替它撰写不少好用的 bundles（bundles 意义上等同于 Sublime Text 2 的 packages），只要把 TextMate bundle 放在 _Packages_ 目录下就可以用，但是 Sublime Text 2 对 bundle 的 command 并不支援。

## <span id="vi-emulation">Vi 模拟模式</span>

Vi 是「古时候」相当经典的编辑器，他让开发者能够只用键盘便完成所有的操作；而 Vim 是改良后的版本，目前仍然被广泛地使用。<i class="icon-pencil"></i>

Sublime Text 透过 Vintage 这个内建的 package，提供了 vi 模拟模式，让你可以使用 vi 的指令模式来操作 Sublime Text。（相容 TextMate 又可以模拟 Vi，Sublime Text 真是强大的太邪恶了！XD）

这个 Vintage package 预设是被忽略的，要启用这个模式，选择 _Preferences_ >> _Settings - User_ 或是用快捷键 <kbd>Command</kbd> + <kbd>,</kbd> 偏好设定的档案，将原本的内容：

    "ignored_packages": ["Vintage"]

改成：

    "ignored_packages": []

一旦这个模式被启用，你应该可以看到「INSERT MODE」文字出现在左下角的状态栏里。

Vintage 一开始预设是 insert mode，这样的好处是让不熟悉模式概念的初学者，一开始不会因为敲不出字来而感到太大的挫折。可以在[偏好设定](/customization#how-to-change-settings)里加上这行，取消这个预设值：

    "vintage_start_in_command_mode": true

Vintage 这个 package 包含常用的 Vi 指令，例如：<kbd>d</kbd>（删除）、<kbd>y</kbd>（复制）、<kbd>c</kbd>（修改）、<kbd>g</kbd><kbd>u</kbd>（小写）、<kbd>g</kbd><kbd>U</kbd>（大写）、<kbd>g</kbd><kbd>~</kbd>（交换大小写）、<kbd>g</kbd><kbd>?</kbd>（rot13）等等，也包括许多移动插字符号的方式，例如：<kbd>h</kbd>、<kbd>j</kbd>、<kbd>k</kbd>、<kbd>l</kbd> 和 <kbd>W</kbd>、<kbd>w</kbd>、<kbd>e</kbd>、<kbd>E</kbd>、<kbd>G</kbd>、<kbd>gg</kbd>等等，几乎该有的都有了。

不一样的是，当切换到 insert mode 时，就是一般的 Sublime Text 2 的编辑型态，这时的快捷键就如同平时的 Sublime Text 2 一样，Vi insert mode 的快捷键在这里并不适用。

此外，如果要用 Ex mode 需要另外安装 [VintageEx](https://github.com/SublimeText/VintageEx) 这个 package。

如果你在 OS X Lion 平台上使用 Sublime Text 2 的 Vintage，会发现长压按键不会重复动作，而是跳出一个气泡框提示你选择各种变异字。这在 command mode 非常不方便，这是因为系统设定的缘故，如果想要修正这个问题，可以在终端机里输入这行指令：

    defaults write com.sublimetext.2 ApplePressAndHoldEnabled -bool false

最后，Vintage 提供以下这些 <kbd>ctrl</kbd> 按键的快捷键：

* <kbd>ctrl</kbd> + <kbd>[</kbd>：Escape
* <kbd>ctrl</kbd> + <kbd>R</kbd>：复原上一步
* <kbd>ctrl</kbd> + <kbd>Y</kbd>：往下卷动一行
* <kbd>ctrl</kbd> + <kbd>E</kbd>：往上卷动一行
* <kbd>ctrl</kbd> + <kbd>F</kbd>：往下卷动一个页面
* <kbd>ctrl</kbd> + <kbd>B</kbd>：往上卷动一个页面

然而在 Windows 和 Linux 上，这些按键会与 Sublime Text 2 原本的一些快捷键冲突，所以这些快捷键预设是关闭的，你可以在[偏好设定](/customization#how-to-change-settings)里加上以下这行来启用：

    "vintage_ctrl_keys": true
