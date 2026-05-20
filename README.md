# 长春理工大学本科生毕业设计 LaTeX 模板

本模板按长春理工大学计算机科学技术学院本科毕业设计常用格式整理，核心规则已写入 `custhesis.cls`，论文入口为 `main.tex`。

## 文件结构

- `custhesis.cls`：模板类文件，包含页面、字体、标题、页眉页脚、摘要、目录、图表、公式、参考文献、附录和致谢格式。
- `main.tex`：论文模板入口，正文为计算机专业算法研究类示例内容，提交前请替换为自己的论文内容。
- `chapters/`：正文各章示例。
- `appendices/`：附录示例。
- `fonts/sim/`：模板使用的中文字体和 Times New Roman 字体文件，保证在本地和 Overleaf 上可复现编译。
- `figures/cust-logo.png`：学校标识图，用于封面。

## 编译方式

推荐使用 XeLaTeX：

```bash
xelatex main.tex
xelatex main.tex
```

如果安装了 `latexmk`，也可以使用：

```bash
latexmk -xelatex main.tex
```

也可以直接运行：

```bash
make
```

如果本地没有完整 TeX Live，也可以安装 Tectonic 后编译：

```bash
tectonic -X compile -r 1 main.tex
```

## Overleaf 预览

上传 zip 后，打开 Overleaf 设置：

1. 新版 Overleaf：点击左下角齿轮图标；旧版 Overleaf：点击左上角 `Menu`。
2. 将 `Main document` 设为 `main.tex`。
3. 将 `Compiler` 设为 `XeLaTeX`。
4. 点击 `Recompile`，右侧即为 PDF 预览。
5. 如果仍然报错，点击 `Logs and output files`，复制第一条以 `!` 开头的错误及其前后 20 行。

常见错误是 Overleaf 默认使用 `pdfLaTeX`，本模板使用中文字体和 `ctex`，必须用 `XeLaTeX` 编译。
项目中已加入 `% !TeX program = xelatex` 和 `latexmkrc`，但仍建议在 Overleaf 菜单中手动确认一次编译器。

模板依赖常见宏包：`ctex`、`fontspec`、`xeCJK`、`geometry`、`fancyhdr`、`caption`、`amsmath`、`amssymb`、`booktabs`、`float`、`tocloft`、`hyperref`、`enumitem` 等。

## 格式映射

- 页面：A4，上下 2.54cm，左右 3.17cm。
- 正文：中文使用 `fonts/sim/` 中的宋体、黑体、仿宋和楷体文件，西文使用 `fonts/sim/` 中的 Times New Roman；1.25 倍行距，首行缩进 2 字符。
- 页眉：封面和原创承诺书不显示；摘要、目录、正文及后续部分显示“长春理工大学本科生毕业设计”，居中并带单线。
- 页码：摘要和目录使用大写罗马数字；正文起使用阿拉伯数字并从 1 开始。
- 标题：章标题宋体三号加粗居中；二级标题宋体四号加粗并缩进 2 字符；三级标题宋体小四加粗并缩进 2 字符。
- 图表：图题置于图下，表题置于表上，均为宋体五号；编号按章编排。
- 公式：按章编号，格式为“（1-1）”。
- 表格：示例使用 `booktabs` 三线表。
- 参考文献：提供手工编号环境 `custbibliography`，编号左对齐，条目按 Word 模板的普通段落式排版，条目格式按 GB/T 7714-2015 书写。

## 使用提示

在 `main.tex` 开头修改论文信息：

```tex
\custtitle{中文题名}
\custenglishtitle{English Title}
\custstudent{姓名}
\custmajor{专业}
\custstudentid{学号}
\custsupervisor{指导教师}
\custschool{学院}
\custdate{二〇二六年五月}
```

如果毕业类型为“本科生毕业论文”，同时修改：

```tex
\custdoctype{本科生毕业论文}
\custheadertitle{长春理工大学本科生毕业论文}
```

正文从 `\custmainmatter` 后开始。参考文献、附录和致谢使用模板提供的环境，不会强制另起新页，符合参考规范中“参考文献、附录、致谢不另起新页”的要求。

模板中的示例段落、题目、作者信息和参考文献条目均为通用示例内容，不包含个人信息或具体毕设课题，便于开源发布和二次定制。

## 字体说明

模板字体统一从 `fonts/sim/` 目录读取：宋体使用 `simsun.ttc`，宋体加粗使用 `simsun.ttc` 仿粗以贴近 Word 效果，黑体使用 `simhei.ttf`，仿宋使用 `FangSong_GB2312.ttf`，楷体使用 `SIMKAI.TTF`，西文使用 Times New Roman 的 `TIMES*.TTF`。模板不再引用 Fandol 字体。
