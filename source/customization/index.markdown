---
layout: default
title: "客制化"
---
## <span id="snippets">程式码片段（Snippets）</span>

程式码片段将经常重复使用的程式码储存起来，可以让你只输入几个关键字，按下 Tab 自动完成其余的部份。

Sublime Text 的程式码片段与 Textmate 完全相容，档案以 _.sublime-snippet_（XML 格式）为副档名，以下这是个范例：

``` xml
<snippet>
    <content><![CDATA[def ${1:method_name}
  $0
end]]></content>
    <tabTrigger>def</tabTrigger>
    <scope>source.ruby</scope>
    <description>def … end</description>
</snippet>
```

* `content`：程式码片段的内容；
* `tabTrigger`：触发自动完成这段程式码的关键字；
* `scope`：选择哪类的档案会触发这段程式码；
* `description`：给人类阅读的友善描述；

`$1`、`$2`、`$3` 是按 <kbd>Tab</kbd> 自动移动的位置（<kbd>Shift</kbd> + <kbd>Tab</kbd> 回到上个位置），`${1:method_name}` 会选取这段文字（占位符的意思），`$0` 是 <kbd>Tab</kbd> 移动的最后一个位置。

<!-- TODO: 未翻译完整：http://docs.sublimetext.info/en/latest/reference/snippets.html -->

## <span id="macros">巨集（Macros）</span>

当你需要大量重复动作完成相同的作业，巨集是个简单的自动化工具可以帮你完成。Sublime Text 的巨集定义在 _.sublime-macro_ 档案（JSON 格式）。

使用快捷键 <kbd>Ctrl</kbd> + <kbd>Q</kbd> 开始记录，再按一次停止；刚刚记录的巨集不会储存成档案，只会暂时放在 buffer 里面，要执行刚刚的巨集可以使用快捷键 <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Q</kbd>；如果要把刚刚的巨集储存成档案，可以从选单栏选取 _Tools_ >> _Save Macro_ 存到 _User/_ 目录下。

你也可以手建一份巨集档案，以下这是范例：

``` json
[
    {"command": "move_to", "args": {"to": "hardeol"}},
    {"command": "insert", "args": {"characters": "\n"}}
]
```

`command` 部分请参考[指令](/customization#commands)。

原则上巨集可以储存在任何 package 目录下，不过还是建议放在 _User/_ 目录下，Sublime Text 会自动读取 _Packages/_ 目录里所有的 _.sublime-macro_ 档案，你可以在选单 _Tools_ >> _Macros_ 下找到先前储存过的巨集。

## <span id="commands">指令（Commands）</span>

指令在 Sublime Text 中到处可见，快捷键设定、选单项目、巨集等等都会用到。有些指令是 Sublime Text 本身的核心功能，有些则是其他 Python 开发的外挂实作的。顺带一提，所有的指令都可以被 Python 外挂使用。

指令名称命名规则是小写，不同单字以下画线分离，例如 `hot_exit`；你也可以传入参数给指令，参数一概是 JSON 类型，以下在 [Python 控制台](/basic-concepts#python-console-and-python-api)执行指令的范例：

``` python
view.run_command("goto_line", {"line": 10})
view.run_command('insert_snippet', {"contents": "<$SELECTION>"})
view.window().run_command("prompt_select_project")
```

Sublime Text 2 指令参考列表：[Commands](http://docs.sublimetext.info/en/latest/reference/commands.html)

## <span id="completions">自动补全</span>

自动补全功能会根据 Sublime Text 的演算法，用 <kbd>Tab</kbd> 键快速补全最佳的单字，这个功能预设是启用的，你也可以在[偏好设定](/customization#settings)里将这个功能取消：

```
{
    "tab_completion": false
}
```

可以使用快捷键 <kbd>Ctrl</kbd> + <kbd>Space</kbd> 叫出自动补全选单，手动选择你要补全的字。你也能自己建立自动补全档案，以 JSON 格式储存在副档名为 _.sublime-completions_ 的档案，以下是个基本范例：

``` json
{
    "scope": "text.html - source - meta.tag, punctuation.definition.tag.begin",

    "completions":
    [
        { "trigger": "a", "contents": "<a href=\"$1\">$0</a>" },
        { "trigger": "abbr", "contents": "<abbr>$0</abbr>" },
        { "trigger": "acronym", "contents": "<acronym>$0</acronym>" }
    ]
}
```

* `scope`：决定哪类档案会使用这份自动补全清单；
* `completions`：自补补全的的阵列；

<!-- TODO: 未完成：http://docs.sublimetext.info/en/latest/reference/completions.html -->

## <span id="settings">偏好设定（Settings）</span>

![sublime-settings-default](/images/sublime-settings-default.png)

Sublime Text 2 的偏好设定都是用 JSON 格式储存在副档名为 `.sublime-settings` 的档案，不论是编辑器本身，或其他 package 的偏好设定，都是用这样的方式。这样看起来有点复杂，目的是为了更佳的客制化弹性。

### <span id="how-to-change-settings">如何修改偏好设定</span>

![sublime-default-settings](/images/sublime-default-settings.png)

Sublime Text 2 预设的偏好设定放在 _Packages/Default/Preferences.sublime-settings_，你可以从选单 _Preferences >> Settings - Default_ 打开它看看有哪些选项，每个选项旁边都有详细的注解，但是你不应该直接修改它，因为当软体升级时这些设定就会被重置。


个人的偏好设定档都应该放在 _Packages/User/_ 目录下，我们曾在[目录结构](/basic-concepts#user-package)章节介绍过，软体更新不会变更 _User/_ 目录下的档案。

你可以从选单 _Preferences_ >> _Settings - User_ 或是快捷键 <kbd>Command</kbd> + <kbd>,</kbd> 打开个人偏好设定的档案，如果先前从来没有建立过这份档案，那么 Sublime Text 2 会替你自动在 _Packages/User/_ 目录下建立 _Preferences.sublime-settings_。

### <span id="settings-type">设定档的区别</span>

不同设定档的用途以不同档案名称来区分，package 的设定档通常以自己的名称来命名。

此外，档名也会关联到这些设定档控制的档案，举例来说：有个档案副档名是 `.py`，它的语法定义在一个叫 _Python.tmLanguage_ 的档案里，那对应到的设定档就应该叫做 _Python.sublime-settings_。

如果要指定该设定档在某平台上才会生效，可以在档名后加上括号，例如：_Preferences (Linux).sublime-settings_，括号内的有效值可以是 Windows、OSX 或 Linux。

这些指定平台的设定档，在 _Packages/Users/_ 目录下会被忽略，这是为了要确保只有一个设定档留到最后[合并](/customization#order-of-precedence-of-sublime-settings-files)。

### <span id="order-of-precedence-of-sublime-settings-files">合并设定档的优先排序</span>

相同档名的设定档可能在不同位置会重复出现，Sublime Text 2 读取这些档案后先依照字母顺序排列，然后将他们合并，排在越后面的的设定档优先层级越高。

除了两个资料夹比较特殊：_Packages/Default/_ 与 _Packages/User/_，前者里的设定档将总是排在序列的第一个，后者则总是排在最后一个。

让我再说明更清楚，_Packages/User/_ 目录内的设定档，与其他相同名称的设定档相较，拥有更高的优先权，且不会随着软体更新而改变。

除此之外，Sublime Text 2 会自动维护一个 session 档案（放在跟 _Packages/_ 同级的 _Settings/_ 目录下），用来储存你编辑档案时的任何动作跟设定，例如搜寻了哪些字或是调整侧边栏宽度，都会随时更新在这个档案里，而这个档案里的设定，优先权将比任何一个可用的 `.sublime-setting` 设定档都还要更高。

最后需要知道的是，当你为某些设定值失效感到困惑时，这可能是因为某些设定依你的使用情况自己自动调整，例如与空格相关或语法的设定。

以下你可以看到 Sublime Text 2 在 OS X 上是如何处理设定档的优先顺序：

* _Packages/Default/Preferences.sublime-settings_
* _Packages/Default/Preferences (OSX).sublime-settings_
* _Packages/User/Preferences.sublime-settings_
* _Packages/Python/Python.sublime-settings_
* _Packages/User/Python.sublime-settings_
* session 资料
* 自动调整档案

### <span id="filetype-settings">档案类型的设定</span>

如果想要让某档案类型，使用指定的语法定义（语法高亮），例如我想要让 Gemfile、Vagrantfile 和 Thorfile 这些档案，预设自动使用 Ruby 的语法定义，可以这么做：

Ruby 的语法定义档案是 _Ruby.tmLanguage_，你需要建立一个相同名称的 _Ruby.sublime-settings_ 设定档，放在 _User/_ 目录下，然后档案加上以下内容：

``` json
{
  "extensions": [
    "Gemfile",
    "Vagrantfile",
    "Thorfile"
  ]
}
```

完成之后，当你重新打开这些档案，就可以看到可以自动使用 Ruby 的语法高亮了。

## <span id="key-bindings">快捷键组合设定（Key Bindings）</span>

Sublime Text 2 快捷键组合设定用 JSON 格式储存在副档名为 `.sublime-keymap` 的档案，为了与各个平台整合，每个平台都有各自对应的档案，也只有对应的平台才会读取该档案。命名规则是在档名后面加上括号：_Default (OSX).sublime-keymap_，有效值可以是 Windows、OSX 或 Linux。

### <span id="file-format">设定快捷键的语法格式</span>

快捷键设定的语法主要是由 `keys` 跟 `command` 组成，`command` 部分请参考[指令](/customization#commands)。以下是典型的 OS X 快捷键设定例子：

``` json
[
  { "keys": ["super+shift+n"], "command": "new_window" },
  { "keys": ["super+o"], "command": "prompt_open" }
]
```

当按下 <kbd>Command</kbd> + <kbd>O</kbd> 便会呼叫 `prompt_open` 这个命令。除此之外，也可以带参数传给命令：

``` json
[
  { "keys": ["shift+tab"], "command": "insert", "args": {"characters": "\t"} }
]
```

当按下 <kbd>Shift</kbd> + <kbd>Tab</kbd> 时呼叫 `insert` 命令，并将参数 `\t` 传给它。

还有一种进阶的写法，就是传入 `context` 给命令，快捷键会基于插字符号的前后关系或是其他情况而触发，或者是无效：

``` json
{ "keys": ["escape"], "command": "clear_fields", "context":
  [
    { "key": "has_next_field", "operator": "equal", "operand": true }
  ]
}
```

### <span id="defining-and-overriding-key-bindings">新增与修改快捷键设定</span>

Sublime Text 2 预设的快捷键设定档放在 _Packages/Default/Default (OSX).sublime-keymap_，也可从选单 _Preferences_ >> _Key Bindings - Default_ 打开这个档案。你可以依照个人的喜好，或者有些快捷键冲突无法使用，需要修改快捷键的设定，那么你可以参考这份档案的设定，将快捷键修改成你想要的按键。

就如同[偏好设定](/customization#how-to-change-settings)的档案一样，你应该在 _Packages/User/_ 目录下另建一个 _Default (OSX).sublime-keymap_，而不是直接修改 _Default/_ 目录下的东西。

快捷键设定档的合并方式与偏好设定一样，合并前的排序方式也几乎相同，进一步了解请参考[合并设定档的优先排序](/customization#order-of-precedence-of-sublime-settings-files)。

## <span id="plugin-settings-and-key-bindings">外挂的偏好设定与快捷键</span>

以 [SideBarEnhancements](https://github.com/titoBouzout/SideBarEnhancements) 这个外挂来举例，打开这个 package 可以找到以下这几种档案类型：_.sublime-commands_、_.sublime-keymap_、_.sublime-settings_，他们分别的作用是：

* _Commands.sublime-commands_：在[指令面板章节](/file-management-and-command-palette#command-palette)曾经介绍过，Sublime Text 2 会读取所有 _.sublime-commands_ 档案，然后列在指令面板中，你可以在这里找到可以用的指令；
* _Default.sublime-keymap_：这是外挂预设的快捷键配置，很有可能会跟你原本的一些快捷键冲突，因此需要自己把冲突的快捷键改掉；
* _Side Bar.sublime-settings_：这是给外挂用的偏好设定，你可以参考这里的设定，在 _Packages/User/_ 目录下新建一个 _Side Bar.sublime-settings_ 来覆蓋原本的。

当我们打开 _Commands.sublime-commands_ 可以看到以下的指令：

``` json
[
  { "caption": "File: Rename",    "command": "side_bar_rename" },
  { "caption": "File: Duplicate", "command": "side_bar_duplicate" }
]
```

现在想替外挂的 `side_bar_rename` 指令加上快捷键来使用，所以我们从选单栏点选 _Preferences_ >> _Key Bindings - User_，打开 _Default (OSX).sublime-keymap_（位在 _Packages/User/_ 下）加上：

``` json
[
  { "keys": ["f2"], "command": "side_bar_rename" }
]
```

以后直接按 <kbd>F2</kbd> 便可以重新命名档案名称了！Done！
