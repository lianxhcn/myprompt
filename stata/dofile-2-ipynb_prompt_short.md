# Stata → Jupyter Notebook 转换（快速版）

## 任务
将 Stata do 文件或代码片段转换为 `.ipynb` 格式，用于 VSCode + nbstata 环境，最终通过 Quarto 编译为中文讲义。

---

## 核心要求

### 代码切割
- **每块 5-10 行**（嵌套结构可放宽至 50 行）
- **绘图命令必须单独成块**（否则只显示最后一个图）
- 按功能切割：数据导入、清洗、分析、可视化各自独立
- 输出控制：`gen`、`list` 等命令前加 `quie`，避免冗长输出

### Markdown 文本块
- **每个代码块前 2-3 句说明**
- 使用列表呈现步骤、要点、注意事项
- 必要时用 LaTeX 公式（下划线转义：`\text{var\_name}`）
- 风格：简洁明了，学术但不冗长

### 标点符号
- 中文标点：，。！？；：""''（）
- 圆括号统一用英文：`()`
- 中英文混排时适当加空格

### Callout 框
适度使用 Quarto callout 框强调关键信息：
```markdown
::: {.callout-note}
## 注意事项
- 确保数据路径正确
- 预先安装外部命令
:::
```
类别：note（注意）、warning（警告）、tip（提示）、important（重要）

### 公式规范
```markdown
行内公式：回归系数 $\beta$ 
独立公式（上下各空一行）：

$$
Y_i = \beta_0 + \beta_1 X_i + \varepsilon_i
$$

注意：变量名下划线转义 `\text{var\_name}`
```

---

## 输出格式
- 标准 `.ipynb` JSON 格式，UTF-8 编码
- Stata kernel 配置
- 可在 VSCode 中直接运行
- 兼容 Quarto render

---

## 使用方法
**直接粘贴 do 文件内容或上传文件即可开始转换。**

    

  
