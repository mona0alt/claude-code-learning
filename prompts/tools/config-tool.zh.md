# Config 工具提示词

## 概述

获取或设置 Claude Code 配置设置。

## 用法

- **获取当前值：**省略 "value" 参数
- **设置新值：**包含 "value" 参数

## 全局设置（存储在 ~/.claude.json）

- `allowWrite`：启用写操作 - true/false
- `allowRead`：启用读操作 - true/false
- `allowBash`：启用 bash 命令执行 - true/false
- `verbose`：启用详细输出 - true/false

## 项目设置（存储在 settings.json）

- `permissions.defaultMode`：默认权限模式 - "accept"、"review"、"refuse"、"plan"
- `permissions.allowPr`：允许创建 pull request - true/false
- `theme`：颜色主题 - "light"、"dark"、"system"
- `editorMode`：编辑器模式 - "default"、"vim"、"emacs"

## 示例

```json
{ "setting": "theme" }
{ "setting": "theme", "value": "dark" }
{ "setting": "editorMode", "value": "vim" }
{ "setting": "permissions.defaultMode", "value": "plan" }
```
