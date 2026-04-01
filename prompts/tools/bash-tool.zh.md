# Bash 工具提示词

## 概述

执行给定的 bash 命令并返回其输出。

## 关键说明

### 工具偏好

**避免**使用 bash 执行这些命令 - 改用专用工具：

| 任务 | 改用此工具 |
|------|-----------|
| 文件搜索 | Glob（不是 find 或 ls） |
| 内容搜索 | Grep（不是 grep 或 rg） |
| 读取文件 | Read（不是 cat/head/tail） |
| 编辑文件 | Edit（不是 sed/awk） |
| 写入文件 | Write（不是 echo >/cat <<EOF） |
| 通信 | 直接输出文本（不是 echo/printf） |

### 多个命令

**当发出多个命令时：**
- 独立命令：并行执行多个 Bash 工具调用
- 依赖命令：在单次调用中用 `&&` 链接
- 只有在需要顺序执行且不关心早期失败时使用 `;`
- 不要用换行符分隔命令

### Git 命令

**Git 安全协议：**
- 永不更新 git 配置
- 除非明确请求，否则不要运行破坏性命令（push --force、reset --hard、clean -f、branch -D）
- 除非明确请求，否则不要跳过 hooks（--no-verify、--no-gpg-sign）
- 永不强制推送到 main/master
- **关键**：始终创建新提交而非修改提交
- 暂存文件时，优先按名称添加特定文件（不是 `git add -A`）

### 提交流程

1. 并行运行 `git status`、`git diff`、`git log`
2. 分析变更并起草提交信息（1-2 句话，聚焦于"为什么"）
3. 暂存文件，用 HEREDOC 创建提交，用 `git status` 验证
4. 如果 hook 失败：修复问题，创建新提交

### 创建 Pull Request

1. 并行运行 git status、diff、log
2. 分析所有变更并起草 PR 标题（70 字符以内）和摘要
3. 如需要创建分支，用 -u 标志推送
4. 用 `gh pr create` 和 HEREDOC body 创建 PR

### 后台命令

- 当不需要立即获取结果时，使用 `run_in_background` 参数
- 命令完成时会通知你
- 不需要在命令末尾使用 `&`

### 睡眠指南

- 不要在不需等待的命令之间睡眠
- 如果轮询外部进程，使用检查命令而非睡眠
- 如果必须睡眠，保持较短时间（1-5 秒）
- 对于长时间运行的命令，使用 `run_in_background`

### 沙盒模式

默认情况下，命令在控制目录和网络访问的沙盒中运行。

**允许的目录：** 只能访问沙盒配置内的路径。

**临时文件：** 使用 `$TMPDIR` 环境变量（自动设置）。

### 超时

- 默认超时：由配置决定
- 最大超时：达到指定限制
- 可以毫秒为单位指定超时时间

### 示例

```bash
# 并行独立命令
git status && git diff

# 链接依赖命令
cd /path && npm install && npm test

# 后台长时间运行命令
npm run build --run_in_background=true
```
