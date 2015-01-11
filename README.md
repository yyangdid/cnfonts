# chinese-fonts-setup - A fonts config tool enforcing double-width Chinese character display

*Author:* Feng Shu <tumashu@gmail.com><br>
*Version:* 0.0.1<br>

`chinese-fonts-setup` 是一个emacs中文字体配置工具。可以比较方便地
实现中文字体和英文字体等宽（也就是大家常说的中英文对齐）。

这个package特别适用于需要处理中英文混合表格的中文org-mode用户。

### 过程展示 ###

    http://www.tudou.com/programs/view/v7Kr0_a9INw/

### 下载 ###

    https://github.com/tumashu/chinese-fonts-setup

### 安装 ###
1. 配置melpa源，参考：http://melpa.org/#/getting-started
2. M-x package-install RET chinese-fonts-setup RET
3. 在emacs配置文件中（比如: ~/.emacs）添加如下代码：

```lisp
(require 'chinese-fonts-setup)
```

### 配置 ###
chinese-fonts-setup 使用profile的概念，来实现特定的环境使用特定的
字体配置，比如：在编程时使用 “Consolas + 微米黑”，在阅读文章时使用
“PragmataPro + 黑体”。

每一个profile都是一个emacs-lisp文件。其中包括了英文字体设置，中文字体设置
以及中文字体调整系数（scale）。

chinese-fonts-setup 默认使用三个profile: profile1, profile2 和 profile3,
如果想使用其他有意义的名称，可以使用下面类似的方式配置:

```lisp
(setq cfs-profiles
    '("program" "org-mode" "read-book"))
```

所有的profile文件都保存在`cfs-profiles-directory`对应的目录中。
如果profile文件不存在，`chinese-fonts-setup` 将使用其自带的fallback
信息来配置字体。

在运行profile编辑命令`cfs-edit-profile`的时候，缺失的falback文件
将会自动创建，其原始内容为软件包自带的fallback信息。

`chinese-fonts-setup` 默认不会覆盖已经存在的profile文件。当需要重置
某个profile文件时，可以使用命令：`cfs-regenerate-profile`。这个命令
会强制覆盖profile文件，请做好备份。

切换 profile 的命令有：

1. `cfs-switch-profile` (使用ido切换profile)
2. `cfs-next-profile`   (直接切换到下一个profile)

如果当前的profile不适合时，可以通过`cfs-edit-profile`来编辑当前
的profile文件。chinese-fonts-setup自带一个profile-edit编辑模式。

1.  C-c C-c     `cfs-test-fontscale-at-point`
                 察看字体显示效果
2.  C-up        `cfs-increment-fontscale-at-point`
                 增大光标下的scale数字，同时显示增加后的字体对齐效果
3.  C-down      `cfs-decrement-fontscale-at-point`
                 减小光标下的scale数字，同时显示减小后的字体对齐效果

注意配置完成后，可能需要重启 Emacs。(参考： http://debbugs.gnu.org/db/17/1785.html)

### 调整字体大小 ###
`chinese-fonts-setup` 使用下述两个命令调整字体大小:

1.  `cfs-increase-fontsize` 增大字体大小
2.  `cfs-decrease-fontsize` 减小字体大小

在调整字体大小的同时，字号信息也通过customize-save-variable函数保存到~/.emacs中了。

### 使用斜体和粗斜体 ###
`chinese-fonts-setup` 默认使用正常字体代替斜体，粗体代替粗斜体。这样设置的原因是：
大多数英文等宽字体包含的斜体不能将(9 10.5 11.5 12.5 14 16 18 20 22)这几个字号完全覆盖。
如果想使用斜体和粗斜体，请使用下面的设置：

```lisp
(setq cfs-ignore-italic nil)
(setq cfs-ignore-bold-italic nil)
```

与此同时，你要使用一个包含粗体和粗斜体的英文等宽字体。

### 参考文章 ###

1. http://baohaojun.github.io/perfect-emacs-chinese-font.html
2. http://zhuoqiang.me/torture-emacs.html


---
Converted from `chinese-fonts-setup.el` by [*el2markdown*](https://github.com/Lindydancer/el2markdown).
