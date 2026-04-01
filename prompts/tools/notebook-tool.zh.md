# NotebookEdit 工具提示词

## 概述

完全替换 Jupyter notebook 中特定单元格的内容。

## 关键信息

- 适用于 `.ipynb` 文件（Jupyter notebooks）
- Notebook 单元格可以包含代码、文本和可视化
- 常用于数据分析和科学计算

## 参数

- **notebook_path**: notebook 文件的绝对路径（不是相对路径）
- **cell_id**: 要编辑的单元格 ID
- **new_source**: 单元格的新内容
- **cell_type**: 单元格类型 — "code" 或 "markdown"

## 编辑模式

- **replace**（默认）：替换单元格内容
- **insert**：在指定索引处添加新单元格
- **delete**：删除指定索引处的单元格

## 单元格编号

单元格编号从 0 开始计数。
