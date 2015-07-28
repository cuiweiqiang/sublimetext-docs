---
layout: default
title: "其他"
---
## <span id="build-system">Build System</span>

Build System 让你能够在 Sublime Text 2 内直接运行程式档案，除非你有明确指定路径，否则它会根据你的 `PATH` 寻找可执行的指令，因此你的 `PATH` 变数必须正确地被 Sublime Text 2 辨识。

在某些系统平台上，`PATH` 变数会随着从终端机 CLI 到 GUI 应用程式而改变，因此可能你在终端机里执行指令是正常的，可是在 Sublime Text 2 里却失效。

一种解决方式是在 _/User_ 目录下建立一个 _.sublime-build_ 档案（JSON 格式），例如：_Python.sublime-build_，使用 `cmd` 指定指令的绝对路径，这只有当你执行 build system 时才会改变 `PATH` 变数，完成之后将会自动恢复成原来的。

范例：

``` json
{
    "cmd": ["python", "-u", "$file"],
    "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
    "selector": "source.python"
}
```

* `cmd`：这句等于执行 `python -u /path/to/current/file.ext`；
* `file_regex`：Perl-style 的正则表达式，当 build system 失败时，这段就是用来捕捉错误讯息的档名，以及出错的程式码行数；
* `selector`：如果选单 _Tools >> Build System_ 是设置 Automatic 时，Sublime Text 2 将会根据这个设定，自动使用对应的指令；

## <span id="command-line">命令列工具（Command Line）</span>

Sublime Text 2 提供 CLI 工具：`subl`，让你能在终端机里用 Sublime Text 2 开启档案或是整个资料夹专案，或是将它设为像是 Git、Subversion 这类 Unix 工具的预设编辑器。

这个 `subl` CLI 工具在你安装 Sublime Text 2 时就已经包含在一起了，只需要建立一个捷径到 `PATH` 搜寻的路径上：

    ln -s "/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl

然后执行 `subl --help` 查看用法：

```
Sublime Text 2 Build 2217

Usage: subl [arguments] [files]         edit the given files
   or: subl [arguments] [directories]   open the given directories
   or: subl [arguments] -               edit stdin

Arguments:
  --project <project>: Load the given project
  --command <command>: Run the given command
  -n or --new-window:  Open a new window
  -a or --add:         Add folders to the current window
  -w or --wait:        Wait for the files to be closed before returning
  -b or --background:  Don't activate the application
  -s or --stay:        Keep the application activated after closing the file
  -h or --help:        Show help (this message) and exit
  -v or --version:     Show version and exit

--wait is implied if reading from stdin. Use --stay to not switch back
to the terminal when a file is closed (only relevant if waiting for a file).

Filenames may be given a :line or :line:column suffix to open at a specific
location.
```
