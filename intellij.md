# intellij

[GitHub - judasn/IntelliJ-IDEA-Tutorial: IntelliJ IDEA 简体中文专题教程](https://github.com/judasn/IntelliJ-IDEA-Tutorial)

https://cdk8s.gitbook.io/github/introduce

+ 安装后生成的目录说明、VM 设置（新用户必看）

+ UI 主题、字体、编辑区主题、文件编码修改、乱码问题（新用户必看）

+ Hello World 的 Java 项目创建和项目配置文件
  
  + Compact Empty Middle Packages

+ 版本控制讲解（SVN + Git）
  
  + Show directories with changed descendants
  
  + Move to Another Changelist

+ 实时代码模板
  
  + 支持变量参数设置
  
  + 支持最后位置的定位
  
  + 支持获取当前类名和当前方法名（本质是内置函数）

+ 特殊代码模板：Postfix Completion

+ IntelliJ IDEA 推荐设置（新人重点）
  
  + 代码提示和补充功能不区分大小写
  
  + 自动优化导入的包
  
  + 对指定代码类型进行默认折叠或是展开的设置
  
  + 复制所选的行数完整内容
  
  + 默认 Ctrl + 空格 快捷键是基础代码提示、补充快捷键，但是由于我们中文系统基本这个快捷键都被输入法占用了，所以我们发现不管怎么按都是没有提示代码效果的，原因就是在此。我个人建议修改此快捷键为 Ctrl + 逗号
  
  + 显示内存使用情况
  
  + 所有打开的文件名 Tab 非单行显示
  
  + 设置增加打开的文件 Tab 个数

+ IntelliJ IDEA 常用细节-2
  
  + 对某些文件进行添加到收藏夹，然后在收藏夹组件窗口中可以查看到我们收藏的文件
  
  + `Alt + F1` + `1` 快捷键来定位当前文件所在 Project 组件窗口中的位置
  
  + 选中要被折叠的代码按 `Ctrl + Alt + T` 快捷键，选择自定义折叠代码区域功能

+ 最特殊的快捷键 Alt + Enter 介绍
  
  + 在 接口类 中，如果光标当前所在的方法，已经在 接口实现类 中生成了，则此快捷键的效果是跳转
  
  + 在 接口类 中添加一个方法后，让该 接口实现类 也跟着生成
  
  + 对当前光标所在类，创建子类，常用在对接口生成接口实现类
  
  + 添加 doc，只能把光标放在方法名或是变量名等这类元素上才会有
  
  + 快速移除当前类所继承的接口，并且同时清空已经写好的该接口所有的 Override 方法。光标只能方式 **接口实现类** 上的 **接口对象单词** 上才可以实现
  
  + 修改光标当前元素的作用域
  
  + 给调用的方法生成返回值，根据返回值自动强转
  
  + 对光标所在的对象进行包导入
  
  + 
