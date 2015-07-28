---
layout: default
title: "编辑"
---
## <span id="multiple-selections">多重选取</span>

通常每个文字编辑器都会有个搜寻（find）、替换（replace）的功能，用来一次更换档案里重复的文字，包括 Sublime Text 2 也有，但是在某些情况多重选取功能可以更有效率地修改文字。

使用快捷键 <kbd>Command</kbd> + <kbd>D</kbd> 选取插字符号所在位置的文字，重复使用这个快捷键，可以快速地依序重复选取档案里相同的文字，如果想要跳过目前选取的文字，可以使用 <kbd>Command</kbd> + <kbd>K</kbd> + <kbd>Command</kbd> + <kbd>D</kbd>，复原选取动作则用快捷键 <kbd>Command</kbd> + <kbd>U</kbd>。

也可以用快捷键 <kbd>Control</kbd> + <kbd>Shift</kbd> + 上下方向键，进行多重选取的操作。

## <span id="join-lines">合并多行</span>

![sublime-join-lines](/images/sublime-join-lines.gif)

假设有一个 array 在档案里这样写：

``` ruby
[
  "Facebook",
  "Google",
  "Twitter"
]
```

想要把它合并到同一行，除了可以透过[多重选取](/multiple-selections)功能快速地做到，其实还可以用合并多行（join lines）这个功能，会更方便。先将这个阵列整个选取起来，然后按下快捷键 <kbd>Command</kbd> + <kbd>j</kbd>，就会变成：

``` ruby
["Facebook", "Google", "Twitter"]
```

## <span id="swap-case">转换大小写</span>

![sublime-swap-case](/images/sublime-swap-case.gif)

<kbd>Command</kbd><kbd>k</kbd> + <kbd>Command</kbd><kbd>u</kbd>：转换文字为大写；

<kbd>Command</kbd><kbd>k</kbd> + <kbd>Command</kbd><kbd>l</kbd>：转换文字为小写；

将单字的字首转成大写，预设没有快捷键，你可以从[指令面板](/file-management-and-command-palette#command-palette)呼叫它，或是[自己设定快捷键](/customization#key-bindings)，例如加上这一行，可以用 <kbd>Command</kbd><kbd>k</kbd> + <kbd>Command</kbd><kbd>t</kbd> 呼叫它：

``` json [     { "keys": ["super+k", "super+t"], "command": "title_case" } ] ```

## <span id="ruler">尺规</span>

尺规会显示一条参考线，用来限制单行显示的字元数量，有的人认为这样有助于程式码的阅读。

你可以从选单栏 _View_ >> _Ruler_ 去选择要断行的字数，这样编辑器上就会显示一条参考线。

也可以从[偏好设定](/customization#settings)里加上自定的数值，或是显示多条参考线，例如：

``` json
[
    "rulers": [90, 110, 130]
]
```

## <span id="comment">注解</span>

可以选择多行，或是插字符号所在位置，然后用快捷键 <kbd>Command</kbd> + <kbd>/</kbd> 将选择的栏位注解起来。

如果你的使用程式语言有所谓的区块注解（block comment），且语法定义里也有定义，可以用快捷键 <kbd>Command</kbd> + <kbd>alt</kbd> + <kbd>/</kbd> 来使用区块注解。

## <span id="code-folding">程式码折叠</span>

## <span id="mark">标记</span>

## <span id="more">更多用法</span>
