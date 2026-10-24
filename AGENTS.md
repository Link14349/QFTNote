# Introduction
这是我的QFT笔记，主要记录我自己学习QFT中的感悟和理解

# Task
- 你的任务主要是检查符号一致性、数学推导是否有误、文本格式(比如缺少句号，或者句号本来应该在式子里却到了下一行开头之类的)/排版的问题
- 你可以应当修改文本格式/排版的问题
- 禁止自行修改符号、数学推导等问题，必须告诉我让我来检查

# errors.md 维护
- 发现的符号不一致、数学推导可疑等问题，应追加到项目根目录的 `errors.md` 中
- `errors.md` 按优先级排列待核查问题，每个问题注明：文件位置、当前内容、为何可疑、建议对照的参考来源
- 用户核实后自行删除对应条目
- 纯格式/排版/拼写问题可以直接修复，不需要放入 errors.md

# LaTeX 编译
- 唯一正式入口是在项目根目录运行 `latexmk main.tex`；项目的 `.latexmkrc` 负责 XeLaTeX、Biber、交叉引用重跑和最终 PDF 输出。
- VS Code LaTeX Workshop 的默认 recipe 是 `latexmk (XeLaTeX, cached)`，保存时自动调用同一入口。不要恢复固定的四步 recipe，也不要给 `xelatex` 加冗余的 `-pdf`。
- 使用项目既有的 XeLaTeX、CTeX 字体和字号；禁止为了通过测试临时替换字体集。
- 编译命令（均在项目根目录执行）：
  ```sh
  # 日常增量编译；由 latexmk 决定是否重跑 XeLaTeX / Biber
  latexmk main.tex

  # 强制重排正文，但继续复用未变的 TikZ 图
  latexmk -g main.tex

  # 显式清除图形缓存并重建；更新 TeX / 字体后也应执行一次
  QFT_TIKZ_REBUILD=1 latexmk -g main.tex

  # 对照排版：使用相同字体直接绘图，不读取或生成图形缓存
  QFT_TIKZ_DISABLE=1 latexmk -g main.tex
  # 对照后再运行 latexmk main.tex 恢复正常缓存模式
  ```
- `.latexmkrc` 使用 `-shell-escape`，供 TikZ 调用 XeLaTeX 生成独立图；此选项是正式构建流程的一部分，不要擅自去掉。
- 需要 TeX Live 中的 `latexmk`（当前安装为 4.86a）、`xelatex`、`xdvipdfmx`、`biber`；MacTeX 通常从 `/Library/TeX/texbin` 提供这些命令。

## 输出与缓存
- `build/` 保存辅助文件、`main.xdv`、`main.pdf`、`main.synctex.gz` 和 `tikz/` 图形缓存，整个目录已被 Git 忽略。
- 完整编译成功后，`.latexmkrc` 的成功回调将最终 PDF 原子替换到根目录 `main.pdf`，失败时保留旧文件；VS Code 预览 `build/main.pdf`，以便配套使用同目录的 SyncTeX。
- **成功后必须保留构建缓存，不要自动清理。** 这取代旧版“完整编译后删除全部辅助文件”的要求。
- 仅在用户要求清理、缓存损坏或确需重建时，在项目根目录执行：
  ```sh
  # 仅清理主文档辅助文件，保留 PDF 与独立图形缓存
  latexmk -c main.tex

  # 删除全部构建缓存；保留根目录最后成功的 main.pdf
  rm -rf build
  ```
- 不要用 `latexmk -C` 代替上述清理命令，因为它还会删除最终 PDF。
- VS Code 禁用编译后自动清理，手动清理不递归进入图形缓存子目录。

## TikZ 缓存规则
- `tikz-cache.tex` 只导出使用 `\tikzsetnextfilename{唯一名称}` 显式命名的独立插图。目前已命名 9 张围道、Wick rotation 和 Schwinger–Dyson 插图。
- 公式内的小图、文档类的装饰图，以及 `remember picture` / `overlay` 等依赖页面位置的图不自动缓存。新增加缓存对象时，要核对尺寸、基线、字体和分页。
- 必须保留 `\tcbset{shield externalize=true}`：`important` 等 tcolorbox 环境内部也使用 TikZ，仅设 `only named=true` 不能保护其内部绘图。缺少此保护会让导出子进程错误扫描后续图环境，并报 `\caption outside float`。回归测试须包含“黑框在前、带图题的缓存插图在后”，以及子图环境。
- 图的正文改变时，TikZ 自身的内容检查会重新生成该图。`.latexmkrc` 还会计算 `packages.tex`、`tikz-cache.tex`、根目录 `.cls` / `.sty`、主文件导言区及构建配置的摘要；这些共享依赖改变时，自动使用新的缓存目录。
- 已命名插图应自包含：图中需要的局部定义放在 `tikzpicture` 内，共享定义放在 `packages.tex`。若新增图依赖其他数据文件、局部样式或外部宏，应将依赖加入 `.latexmkrc` 的 `@qft_dependencies`；不要仅依赖图片正文摘要。
- 图中的动态引用、计数器和页码不会被图片正文摘要自动追踪；不要将此类图直接加入缓存。图题、编号和 `\label` 应留在图形外，由主文档统一处理。
- 缓存按稳定的图名保存，避免在前文插图后导致全部后续图换名。切勿手动修改 `build/tikz-config.tex` 或缓存 PDF。

## 调用工具与验证
- 先检查 `git status --short`，保留用户尚未提交的改动。构建改动不能更改正文的符号、推导或编号规则。
- 使用终端工具执行上述命令，工作目录设为项目根目录。长编译可将输出重定向到临时日志，获得进程会话后轮询；不要同时启动两个写入同一个 `build/` 的编译。
- 若缺少工具，先用 `command -v latexmk xelatex xdvipdfmx biber` 检查路径，不能把“工具未找到”当作源码错误。
- 以进程退出状态、`build/main.log` 和 `build/main.blg` 判断结果。首次构建会生成图形缓存，耗时通常更长；不要中途将其判断为无响应。
- 修改构建流程后，应验证首次编译、无改动再次编译、正文修改复用图片、图片或共享样式修改触发重建；对实际 PDF 抽查图片、基线、编号和跨文件引用。不要声称未执行的全书编译或版式检查已通过。
- 在 Codex 沙箱中，XeLaTeX 可能因无法访问 macOS 字体服务而误报找不到 `STHeiti`。VS Code 使用同一 XeLaTeX 但运行在普通桌面环境，因此可能正常编译；项目和用户级 VS Code 配置没有额外的字体修补参数。
- 遇到这一问题，只有在运行环境允许并已获得必要授权时，才能在沙箱外重跑同一正式命令。若权限提升被禁止，报告限制，继续可行的配置与独立测试；不得改字体、绕过沙箱或把测试文档的成功当作正式全书验证。

# 注意
- 禁止自行修改符号、数学推导等问题!!!
