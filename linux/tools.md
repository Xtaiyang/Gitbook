### 有用的Linux工具

**tmux**

- 是一个终端复用器（Terminal Multiplexer）
- Linux/Unix 系统下的命令行工具

功能：
- 在单个屏幕中管理多个终端
- 后台运行终端会话
- 允许断开连接后重新连接会话
- 分屏、多窗口管理

**awk**

awk 是一个强大的文本处理工具，主要用于处理和分析结构化的文本文件，特别是按行和列组织的数据。

**awk 的主要功能和特点**：

1. **数据处理**
- 可以轻松地处理以空格或制表符分隔的文本文件
- 支持按列（字段）提取和处理数据
- 能够执行复杂的文本转换和统计分析

2. **工作原理**
- 逐行读取输入文件
- 将每一行自动分割成若干字段（默认以空白字符分隔）
- 对每一行执行用户定义的操作

3. **基本语法**
```bash
awk 'pattern { action }' filename
```

4. **常用内置变量**
- `$0`：整行内容
- `$1, $2, $3`：第1、2、3个字段
- `NR`：当前行号
- `NF`：字段总数

5. **典型用法示例**

提取文件的第2列：
```bash
awk '{print $2}' filename
```

统计文件行数：
```bash
awk 'END {print NR}' filename
```

条件过滤（打印第3列大于100的行）：
```bash
awk '$3 > 100 {print $0}' filename
```

计算某一列的总和：
```bash
awk '{sum += $3} END {print sum}' filename
```

6. **高级特性**
- 支持正则表达式匹配
- 可以执行数学运算
- 内置字符串和数学函数
- 支持条件判断和循环
- 可以生成报告和格式化输出

7. **应用场景**
- 日志分析
- 系统监控
- 数据提取和转换
- 简单的数据统计
- 文本处理

**Pandoc**

Pandoc 是一个功能强大且灵活的开源文档转换工具，由 John MacFarlane 开发。它被誉为"文档转换的瑞士军刀"，能够将文档从一种格式转换为另一种格式，支持多种输入和输出格式。

1. **多格式支持**
   - **输入格式**：Markdown、HTML、LaTeX、Word (docx)、EPUB、reStructuredText、Textile、MediaWiki 等
   - **输出格式**：Markdown、HTML、LaTeX、PDF、Word (docx)、EPUB、幻灯片（如 Beamer、Reveal.js）、ODT、Plain Text 等

2. **命令行工具**
   Pandoc 主要通过命令行进行操作，用户可以通过简单的命令实现文档格式的转换。例如：
   ```bash
   pandoc input.md -o output.docx
   ```
   这条命令将 Markdown 文件 `input.md` 转换为 Word 文件 `output.docx`。

3. **高度可定制**
   Pandoc 提供了丰富的选项和参数，用户可以根据需要自定义转换过程。例如，可以指定模板、添加元数据、调整样式等。

4. **扩展性强**
   Pandoc 支持通过插件和过滤器扩展其功能。用户可以编写自定义过滤器来处理文档内容，或者使用现有的过滤器来实现特定的转换需求。

5. **学术写作支持**
   Pandoc 对学术写作提供了强大的支持，包括引用管理（通过 BibTeX 或 CSL）、数学公式渲染（LaTeX 或 MathML）以及复杂的文档结构。

**应用场景**：
- 文档格式转换：将 Markdown 文件转换为 Word、PDF、HTML 等格式
- 学术写作：生成符合学术规范的 PDF 文档，支持引用和数学公式
- 电子书制作：将文档转换为 EPUB 格式，适用于电子书阅读器
- 幻灯片生成：将 Markdown 或 LaTeX 文件转换为 Beamer 或 Reveal.js 格式的幻灯片
- 技术文档编写：将 reStructuredText 或 Markdown 文件转换为 HTML 或 PDF 格式的技术文档

**优点**：
- 灵活性：通过命令行参数和过滤器实现高度定制化
- 开源生态：拥有活跃的社区和丰富的插件资源
- 跨平台：适用于 Windows、macOS 和 Linux 等多种操作系统

**dos2unix**

dos2unix 是一个常用的命令行工具，用于将文件从 Windows 格式转换为 Unix/Linux 格式。主要区别在于：
- Windows 系统中，换行符是 \r\n（回车+换行）
- Unix/Linux 系统中，换行符是 \n（仅换行）

该工具可以移除文件中的 Windows 特定字符，同时还能清理一些隐藏的非打印字符（如不间断空格 U+00A0）。

**命令执行和输出**：

运行命令：`dos2unix funasr_demo.py`
输出信息：`dos2unix: converting file funasr_demo.py to Unix format...` 表示工具正在将文件转换为 Unix 格式。

如果没有报错，说明转换成功。

**替代方案**：

可以使用 Python 脚本或其他工具进一步清理文件。例如：
```bash
tr -d '\r' < funasr_demo.py > temp.py && mv temp.py funasr_demo.py
```
这个命令会移除文件中的回车符。

**预防措施**：

如果你经常在 Windows 和 Linux 系统之间传输文件，建议在编辑文件时使用支持跨平台的编辑器（如 VSCode），并确保文件格式统一为 Unix 格式。