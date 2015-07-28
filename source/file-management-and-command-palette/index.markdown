---
layout: default
title: "档案导览与指令面板"
---
## <span id="goto-anything">传送门？（Goto Anything）</span>

Goto Anything 就像游戏[传送门](http://www.youtube.com/watch?v=QjF_AAiTPxk)，让你快速地开启任何档案，使用快捷键 <kbd>Command</kbd> + <kbd>P</kbd> 打开它，当输入文字会立即搜寻、连结到相似档名的档案，并且即时预览。输入的内容可以是路径上目录及档案的关键字，不必输入很精准、很完整的单字，最后 Sublime Text 会为你选择一个最佳的结果。

除此之外，Sublime Text 2 的 Goto Anything 还有其他的特异功能，就是可以结合以下各种符号，执行不同的操作：

* `#`：在档案内执行模糊搜寻；
* `@`：搜寻档案内的 symbols，指的是类别名或者是方法名，快捷键是 <kbd>Command</kbd> + <kbd>R</kbd>；
* `:`：插字符号移往该档案指定的行数，快捷键是 <kbd>control</kbd> + <kbd>G</kbd>；

## <span id="sidebar">侧边栏</span>

侧边栏可以总览整个专案的所有档案，就像 Windows 的档案总管、OS X 的 Finder 那样。被加进侧边栏的档案，也就是可以被 [Goto Anything](/file-management-and-command-palette#goto-anything) 搜寻到的档案。

可以用快捷键 <kbd>Command</kbd> + <kbd>K</kbd>、<kbd>Command</kbd> + <kbd>B</kbd> 显示或隐藏侧边栏。

你也可以用方向键来浏览侧边栏，但是必须先透过快捷键 <kbd>Control</kbd> + <kbd>0</kbd> 将目前游标的焦点移往侧边栏，反之，要移回来按一下 <kbd>Esc</kbd> 即可。当然，你也可以用滑鼠来点，效果都是一样的，但是既然键盘那么方便为什么还要用滑鼠呢？:)

在侧边栏里，敲击右键呼叫功能选单，这里提供一些常见的基本档案操作。

<!-- TODO: 加上 sidebar enhacements 外挂 -->

## <span id="command-palette">指令面板（Command Palette）</span>

指令面板是 Sublime Text 2 中使用内建指令、或是呼叫外挂的功能非常好用的东西，使用快捷键 <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> 开启此面板。这个面板指令是读取自所有的 `.sublime-commands` 档案。

以下例子是 _Packages/Default/Default.sublime-commands_ 档案的一小部分：

``` json
[
  { "command": "clear_bookmarks", "caption": "Bookmarks: Clear All" },
  { "command": "select_all_bookmarks", "caption": "Bookmarks: Select All" },

  { "caption": "Indentation: Convert to Tabs", "command": "unexpand_tabs", "args": {"set_translate_tabs": true} },
  { "caption": "Indentation: Convert to Spaces", "command": "expand_tabs", "args": {"set_translate_tabs": true} },
  { "caption": "Indentation: Reindent Lines", "command": "reindent", "args": {"single_line": false} }
]
```

稍微解释一下这里的意思：

* `caption`：显示在指令面板中的文字；
* `command`：要执行的指令名称；
* `args`：借由指令传入的参数；

因此你可以在指令面板中找到像是「Bookmarks: Clear All」、「Bookmarks: Select All」等这样的指令，按下输入时就会触发执行该命令。

## <span id="projects">专案（Project）</span>

专案群组是以你的工作需求为单位，将档案、资料夹加入到一个专案群组中，储存它然后命名。选择 _Project_ >> _Save Project As..._，便可在 Sublime Text 2 建立这样的专案群组，并且透过快捷键 <kbd>Command</kbd> + <kbd>Control</kbd> + <kbd>P</kbd> 在不同专案群组之间快速切换。

建立专案群组时，专案资料会以 JSON 格式储存在 _.sublime-project_ 档案里，同时 Sublime Text 2 也会自动生成一个附档名为 _.sublime-workspace_ 的档案，用来储存当下的使用环境，例如哪些档案被打开、哪些被修改，甚至连视窗卷动到哪都会被记录起来。

_.sublime-project_ 是可以自己修改的，可支援三个顶层节点，分别是：

* `"folders"`：每个资料夹都必须要有路径（`path`），选择性地可以加上 `folder_exclude_patterns` 或 `file_exclude_patterns` 设定来排除特定的目录或档案。路径可以是此专案的箱端路径，也可以是绝对路径。或许你还会想要替他们取个名字，这将会显示在侧边栏；
* `"settings"`：用来覆写个人的[偏好设定](/customization#settings)，例如设置缩进的空格数，好让编辑这个专案的人都可以保持统一的程式码风格；
* `"build_systems"`：给专案指定的 [Build System](/others#build-system) 设定，每一项设定都必须指定名称（`name`）；

例子：

``` json
{
  "folders":
  [
    {
      "path": "src",
      "folder_exclude_patterns": ["backup"]
    },
    {
      "path": "docs",
      "name": "Documentation",
      "file_exclude_patterns": ["*.css"]
    }
  ],
  "settings":
  {
    "tab_size": 8
  },
  "build_systems":
  [
    {
        "name": "List",
        "cmd": ["ls"]
    }
  ]
}
```

而 `.sublime-workspace` 是由编辑器自己产生，不应该去动它。

此外，你也可以从终端机用 Sublime Text 2 的[命令列工具](/others#command-line)，以 `.sublime-project` 档案作为参数开启专案，例如 `subl --project example.sublime-project`。
