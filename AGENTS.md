# Introduction
这是我的QFT笔记，主要记录我自己学习QFT中的感悟和理解

# Task
- 你的任务主要是检查符号一致性、数学推导是否有误、文本格式(比如缺少句号，或者句号本来应该在式子里却到了下一行开头之类的)/排版的问题
- 你可以应当修改文本格式/排版的问题
- 禁止自行修改符号、数学推导等问题，必须告诉我让我来检查
- 禁止自行修改符号、数学推导等问题!!!

# errors.md 维护
- 发现的符号不一致、数学推导可疑等问题，应追加到项目根目录的 `errors.md` 中
- `errors.md` 按优先级排列待核查问题，每个问题注明：文件位置、当前内容、为何可疑、建议对照的参考来源
- 用户核实后自行删除对应条目
- 纯格式/排版/拼写问题可以直接修复，不需要放入 errors.md

# LaTeX 编译
- 编译方式以 `.vscode/settings.json` 中 LaTeX Workshop 的默认 recipe 为准：`xelatex -> biber -> xelatex -> xelatex`。
- 在项目根目录依次运行：
  ```sh
  xelatex -synctex=1 -interaction=nonstopmode -file-line-error main.tex
  biber main
  xelatex -synctex=1 -interaction=nonstopmode -file-line-error main.tex
  xelatex -synctex=1 -interaction=nonstopmode -file-line-error main.tex
  ```
- 仅做快速语法检查时，可以只运行第一条 `xelatex` 命令；需要更新参考文献、目录和交叉引用时，必须运行完整 recipe。
- 完整编译成功后，必须按照 `.vscode/settings.json` 中 `latex-workshop.latex.clean.fileTypes` 的列表清理辅助文件；保留最终生成的 `main.pdf`，不要把 `.aux`、`.bbl`、`.bcf`、`.blg`、`.log`、`.out`、`.run.xml`、`.synctex.gz`、`.toc` 等编译中间文件留在项目中。
- 在 Codex 沙箱中，XeLaTeX 可能因无法访问 macOS 字体服务而误报找不到 `STHeiti`。遇到这种情况，应在获得授权后于沙箱外重跑同一条 XeLaTeX 命令；不要通过临时切换 CTeX 字体集来代替项目的正式编译，因为这会改变字体度量和分页。
- `.vscode/settings.json` 当前还向 `xelatex` 传入了 `-pdf`；TeX Live 2025 的 XeLaTeX 会提示 `unrecognized option '-pdf'`，但仍继续编译。命令行编译时省略该冗余参数即可，编译流程与 VS Code recipe 保持一致。

# 注意
- 禁止自行修改符号、数学推导等问题!!!
