# LSP 工具提示词

## 概述

与语言服务器协议（LSP）交互以获取代码智能功能。

## 支持的操作

### 导航
- **goToDefinition**: 查找符号定义位置
- **goToImplementation**: 查找接口或抽象方法的实现
- **findReferences**: 查找符号的所有引用

### 信息
- **hover**: 获取符号的悬停信息（文档、类型信息）
- **documentSymbol**: 获取文档中的所有符号（函数、类、变量）
- **workspaceSymbol**: 在整个工作区中搜索符号

### 调用层次结构
- **prepareCallHierarchy**: 获取位置处的调用层次结构项
- **incomingCalls**: 查找调用该位置函数的函数/方法
- **outgoingCalls**: 查找该函数调用的函数/方法

## 参数

所有操作需要：
- **filePath**: 要操作的文件
- **line**: 行号（1-based，与编辑器中显示一致）
- **character**: 字符偏移（1-based，与编辑器中显示一致）

## 注意

必须为文件类型配置 LSP 服务器。如果没有可用的服务器，将返回错误。
