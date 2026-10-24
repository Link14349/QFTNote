# 待核查问题清单

本文件只保留尚未核实或尚未处理的问题，并按优先级排列。用户核实后自行删除对应条目。下文旧条目的 PDF 页码是 Noether 小节重整前记录的物理页码；2026-09-18 重整使后续章节分页变化，应优先按文件位置与公式内容定位。

## 需要人工复核表达的

本栏记录新增或改写后需要本人确认的说明性文字，不表示已判定存在数学错误。核实后由本人删除对应条目；其余待核查问题仍按下方优先级维护。

## 高优先级

### 21. 双势阱手稿中的多瞬子计数与阶乘不一致

**文件位置**：`ssb.tex`，“稀薄瞬子气体与多次隧穿”中保留的手稿注释；原图 `8acb8a2017526d2093cc69747085d0a7.jpg` 中部。

**当前内容**：手稿先写“$n$ 个 instanton 和 $n-1$ 个 anti-instanton”，随后将贡献写为 $(kT\mathrm e^{-S_E})^n/n!$。

**为何可疑**：按前一句，事件总数是 $2n-1$，不等于后一式中的幂次和阶乘参数。请确认原稿第二个 $n$ 是否本意表示瞬子与反瞬子的总数。整理稿保留原句及公式于源码注释，正文另用 $N$ 明确表示总数，并按原稿最后的双曲正弦结果展开奇数次贡献；此处记号对应仍待本人核实。

**建议对照的参考来源**：手稿末尾的 $\sinh(kT\mathrm e^{-S_E})$；[David Tong，Supersymmetric Quantum Mechanics，第 2 章 §2.2 的稀薄瞬子气体推导](https://davidtong.org/pdfs/teaching/supersymmetric-quantum-mechanics/susyqm2.pdf)，尤其是有序中心积分与奇偶次数求和。

### 1. Weyl/Dirac 章节中的场与张量记号

**文件位置**：`spinor.tex` 第 337、341、349、393 行附近。

**PDF 位置**：第 128 页上部至中部（Weyl 旋量例子中的三个公式）；第 129 页中部（“Dirac旋量”小节开头的 Lagrangian）。

**当前内容**：

1. Dirac Lagrangian 的两个动能项都写成了 $\psi_R$，第二项为
   $$i\psi_R^\dagger\sigma^\mu\partial_\mu\psi_R.$$
2. $\psi_L$ 的 Lorentz 变换末尾写成了 $\psi_R$。
3. $\delta\psi_L\frac12(\dots)\sigma^j\psi_R$ 缺少等号，末尾使用了 $\psi_R$。
4. 三维反对称张量写成了 $\sigma_{ijk}$。

**为何可疑**：第 393 行的第二项按左右手旋量分解应涉及 $\psi_L$ 与 $\bar\sigma^\mu$；第 337、341 行讨论的对象都是 $\psi_L$；三维完全反对称张量通常记为 $\epsilon_{ijk}$。这些写法与本章后文的 Dirac Lagrangian 展开也不一致。

**建议对照**：本文件第 417 行附近的 $\bar\psi(i\slashed\partial-m)\psi$ 展开；Peskin & Schroeder §3.2；Schwartz §10。

### 2. 表面发散度的中间量纲计数可疑

**文件位置**：`renormalization.tex` 第 209、220--223 行附近。

**PDF 位置**：第 198 页上部至中部（“量纲分析”小节，$\Delta_f$ 公式之后至表面发散度 $D$ 的第一个公式）。

**当前内容**：正文称“$f$场的传播子动量量纲为 $2\Delta_f$”，并写出
$$
D=\sum_f2I_f\Delta_f+\sum_iN_i\mathcal D_i-\sum_i dN_i+d.
$$

**为何可疑**：内线传播子在高动量下应贡献负的动量次数；Dirac 传播子行为是 $p^{-1}$，也不等于 $p^{-2\Delta_\psi}=p^{-3}$。当前中间式似乎无法推出后面的 $D=d-\sum_fE_f\Delta_f-\sum_iN_i\Delta_i$。

**建议对照**：Peskin & Schroeder §10.1 的 superficial degree of divergence 计数；Schwartz 的 power counting 章节。

### 3. $\phi^3$ 一圈二点 1PI 图中疑似混入非 1PI 图

**文件位置**：`renormalization.tex` 第 980--1026 行附近。

**PDF 位置**：第 213 页中部至下部（“$\phi^3$理论的重整化”中的质量重整化图、两个一圈结果以及 $\delta_Z=\delta_m=0$ 的结论）。

**当前内容**：质量重整化中将气泡图与一个通过单根内线连接蝴蚪圈的图相加，得到极点相消，并据此声称 $\delta_Z=\delta_m=0$。

**为何可疑**：连接蝴蚪的单根线一切即断，看起来并非 1PI 二点图；标准 $\phi^3$ 一圈二点函数的发散性还应按时空维数和 tadpole/one-point counterterm 的处理分别讨论。

**建议对照**：标准 $\phi^3$ 理论的 1PI 二点函数和 tadpole 重整化；Peskin & Schroeder §10；Schwartz 重整化章节。

### 4. QED 质量反项 $\delta_m$ 的量纲不对

**文件位置**：`renormalization.tex` 第 1120--1124、1515--1527 行附近。

**PDF 位置**：第 215 页上部（QED 反项 Lagrangian）；第 219 页下部至第 220 页上部（电子自能的发散部分与 $\delta_\psi,\delta_m$ 公式）。

**当前内容**：Lagrangian 中写有 $-\delta_m\bar\psi_r\psi_r$，但后面得到
$$
\delta_m=-\frac{e^2}{4\pi^2}\left(\frac1\epsilon+\ln4\pi-\gamma\right),
$$
右边没有质量因子。

**为何可疑**：按当前 Lagrangian 定义，$\delta_m$ 应具有质量量纲；圈图发散部分也显式正比于 $m$。可能是缺少一个 $m$，或前面本意是 $-m\delta_m\bar\psi\psi$。

**建议对照**：Peskin & Schroeder §10.2 的 QED electron self-energy counterterms；Schwartz QED renormalization 章节。

### 5. QED 传播子与反常磁矩推导中的多处公式笔误

**文件位置**：`renormalization.tex` 第 1357、1374、1628 行附近。

**PDF 位置**：第 217 页中部（resummed 电子传播子）及下部（$\Gamma^\mu$ 的 Lorentz 结构讨论）；第 221 页中部（$x_1,x_2$ 交换奇偶分解公式）。

**当前内容**：(1) resummed 电子传播子分母末尾写成 $-i\epsilon$，而前面均为 $+i\epsilon$；(2) $\Gamma^\mu$ 的线性组合中写了自由指标不匹配的 $(p-k)^\nu$；(3) 系数奇偶分解式中出现 `x_1^-x_1`。

**为何可疑**：分别与 Feynman prescription、自由指标一致性及前一行的代数式冲突。

**建议对照**：本文件相邻公式；Peskin & Schroeder §6.2、§10.2 及 vertex form factors 的推导。

### 6. Callan--Symanzik 方程推导中导数消失

**文件位置**：`renormalization.tex` 第 1672--1684 行附近。

**PDF 位置**：第 222 页中部至下部（“Callan-Symanzik方程”小节中，裸场关联函数的求导式及紧随其后的定理）。

**当前内容**：
$$
0=\partial_{\ln\mu}\langle\phi_{bare}\cdots\rangle
=\partial_{\ln\mu}Z_\phi^{n/2}\langle\phi\cdots\rangle
=Z_\phi^{n/2}G^{(n)}.
$$

**为何可疑**：对乘积求导后不应直接变成未求导的 $Z_\phi^{n/2}G^{(n)}$，这一步也无法直接支持紧接着给出的 Callan--Symanzik 算符。

**建议对照**：Peskin & Schroeder §12.2；Schwartz 的 Callan--Symanzik equation 推导。

### 7. 自旋平均振幅平方的左边缺少平方

**文件位置**：`spinor.tex` 第 1863、1939 行附近。

**PDF 位置**：第 165 页上部至中部（“树图阶散射计算”小节开头的自旋平均定义）；第 166 页下部（Bhabha 散射最终的 $|\mathcal M_{aver}|$ 公式）。

**当前内容**：两处左边均写为 $|\mathcal M_{aver}|$，但右边分别是 $|\mathcal M|^2$ 的自旋平均以及量纲为 $e^4$ 的结果。

**为何可疑**：按后文散射截面公式及第 1915 行的记法，左边应当也是 $|\mathcal M_{aver}|^2$。

**建议对照**：本文件第 1915、2017、2077 行附近；Peskin & Schroeder §5.1 的 spin sums/averages。

## 中优先级

### 22. 双势阱手稿两页之间的二次涨落系数不一致

**文件位置**：`ssb.tex`，标签 `ssb-quadratic-fluctuation` 后的手稿注释；原图 `bd8d715216ee7801bde989efad9b65af.jpg` 页末与 `8acb8a2017526d2093cc69747085d0a7.jpg` 页首。

**当前内容**：第一页的泛函 Taylor 展开含 $\frac12\int\delta x\mathcal M_\tau\delta x$；第二页首行的指数写成 $-\int\delta x\mathcal M_\tau\delta x$，而随后的算符仍定义为 $\mathcal M_\tau=U''-\d^2/\d\tau^2$。

**为何可疑**：两页之间似乎漏了 $1/2$；不能在不重定义算符或积分变量的情况下直接省去。整理稿保留第一页的二阶展开，并在源码注释中记录第二页的原写法，没有将两式当作已经核实的相等表达式。

**建议对照的参考来源**：`preparation.tex` 中“泛函的Taylor展开”；手稿第一页末尾的两项二次型；[Tong，Supersymmetric Quantum Mechanics，§2.2 的 Gaussian fluctuations](https://davidtong.org/pdfs/teaching/supersymmetric-quantum-mechanics/susyqm2.pdf)。

### 23. 双势阱手稿的涨落行列式归一化未明示

**文件位置**：`ssb.tex`，标签 `ssb-determinant-ratio` 及紧邻的手稿注释；原图 `8acb8a2017526d2093cc69747085d0a7.jpg` 的“Now”一行。

**当前内容**：手稿将 $(\det'\mathcal M_\tau)^{-1/2}$ 直接写为 $\sqrt{12}\,\omega$，后面再补上基态零点能的时间因子。

**为何可疑**：这个数值通常指相对于参考算符 $\mathcal M_0=-\d^2/\d\tau^2+\omega^2$ 的行列式比值的平方根，而非未经归一化的绝对行列式。请确认手稿中的行列式是否已隐含参考归一化，以及零模测度中的 $1/\sqrt{2\pi}$ 约定。整理稿保留原写法于注释，并将参考传播核 $K_0(T)$、参考算符和相对前因子分开列出，便于本人核查。

**建议对照的参考来源**：手稿后续的 $k=\omega\sqrt{6S_E/\pi}$；[Tong，Supersymmetric Quantum Mechanics，§2.2，式 (2.30)--(2.32)](https://davidtong.org/pdfs/teaching/supersymmetric-quantum-mechanics/susyqm2.pdf) 对零模与简谐振子归一化的处理；Coleman，Aspects of Symmetry，“The Uses of Instantons”。

### 19. Fock 空间的直和起点似乎遗漏真空扇区

**文件位置**：`freefield.tex`，“自由实标量场的量子化”中的“Fock空间”定义，第 879 行附近。

**当前内容**：$\mathcal H=\bigoplus_{n=1}\mathcal H_n$，其中 $\mathcal H_n$ 被定义为 $n$ 粒子空间。

**为何可疑**：从 $n=1$ 开始不包含零粒子真空 $\ket0$，但前后文均将它作为该自由场 Hilbert 空间中的态使用。请确认是否应包含 $\mathcal H_0=\mathrm{span}\{\ket0\}$。本次仅新增真空波泛函例子，保留原定义。

**建议对照的参考来源**：本文件紧邻的“真空态”定义及 $\mathcal H_n$ 的构造式；玻色 Fock 空间的零粒子扇区定义。

### 20. 场论路径积分的真空投影中时间端点及态标签需核查

**文件位置**：`path-integral.tex`，“场论路径积分”小节，第 120--137 行附近。

**当前内容**：引入 $T\to T(1-i\epsilon)$ 后，多处左边写为 $\braket{\phi_f,-\infty|\phi_i,+\infty}$；丢弃高能态后，第一行右边仍含 $\braket{\phi_f|n}\braket{n|\phi_i}$，已无对 $n$ 的求和。

**为何可疑**：前文设 $T=t_f-t_i\to+\infty$，后文真空振幅也使用末态 $+\infty$、初态 $-\infty$，与这些左边的时间顺序不一致；投影后保留下来的态标签也应与真空 $\Omega$ 对照。原公式未修改。

**建议对照的参考来源**：本小节第 115--119 行的能量本征态展开，以及第 132 行的真空振幅分解式。

### 17. 泛函空间记号与变分定义需核查

**文件位置**：`preparation.tex`，“泛函基础简述”的“泛函”和“变分”定义。

**当前内容**：先以 $\mathscr F$ 表示函数空间、$\mathcal F$ 表示泛函集合，后又将 $\mathcal F$ 用作函数空间；变分定义中写 $f:\mathcal F\times\mathbb R\to\mathcal F$，并直接代入 $\phi+\varepsilon\delta$。

**为何可疑**：空间记号及值域不一致；一般非线性泛函未必能作用于含 $\delta$ 分布的输入，该差商可能只能作为形式记号。本次恢复原定义，只按要求调整和补充例子，未修改此处。

**建议对照的参考来源**：`reference.bib` 的 `functionals`（Lancaster 与 Blundell，§1）；用光滑方向 $\phi+s\eta$ 定义一阶变分的标准做法。

### 18. $\delta(g(x))$ 换元公式中的阶跃函数变量需核查

**文件位置**：`preparation.tex`，“泛函”小节末尾的换元定理。

**当前内容**：第二行求和项后写 $\Theta(b-x)\Theta(x-a)$，且未声明零点为简单零点。

**为何可疑**：$x$ 已被积分掉，区间筛选应针对各零点 $x_i$；分母 $|g'(x_i)|$ 要求 $g'(x_i)\ne0$，端点零点也需说明约定。本次保留原公式，待本人核查。

**建议对照的参考来源**：Dirac 分布的简单零点换元恒等式 $\delta(g(x))=\sum_i\delta(x-x_i)/|g'(x_i)|$；本文件该定理的第一行求和范围。

### 14. 旁注中 Wick 定理的适用条件需核查

**文件位置**：`freefield.tex`，注“Wick定理的适用范围”（搜索该标题定位）。

**当前内容**：“我们并没有利用到任何Free Field的性质, 因此Wick定理也是可以适用于接下来的Interaction Theory的.”

**为何可疑**：前面的证明使用了产生、湮灭部分之间为数值分布的对易子。这里需区分相互作用绘景中的自由场与完整的相互作用 Heisenberg 场；当前措辞可能被理解为对后者也直接成立。本次仅转换旁注格式，保留原文待核查。

**建议对照的参考来源**：本节引理 `lemma:psi_commute`；Peskin & Schroeder §4.3 关于 Wick 定理及相互作用绘景的讨论。

### 15. 两点关联函数被称为“概率密度”需核查

**文件位置**：`freefield.tex`，注“两点关联函数的意义”（搜索该标题定位）。

**当前内容**：将 $\braket{x|y}$ 称为在 $y$ 激发粒子、在 $x$ 测量到它的“概率密度”。

**为何可疑**：态的内积通常对应振幅，且这里的关联函数未必为实数或非负数，不能直接视为概率密度；还需核查场激发态的归一化及位置测量的解释。本次保留原文待核查。

**建议对照的参考来源**：本节关联函数定义与前一节 $\ket{x}$ 的定义；Peskin & Schroeder §2.4 关于标量场传播的讨论。

### 16. Coulomb 规范旁注末尾疑似缺少积分号

**文件位置**：`gaugetheory.tex`，注“Coulomb规范下的对易关系”末尾的 `align` 环境。

**当前内容**：两行右端分别以 `i\ddd p`、`-\ddd p` 开头，未写 `\int`。

**为何可疑**：这一步由上方含动量积分的场对易子求导而来，积分体元前的积分号似乎在抄写中遗漏。本次保留公式待核查。

**建议对照的参考来源**：本文件紧邻该注之前的 $[A^i_{\vec x},E^j_{\vec y}]$ 动量积分表达式，以及 `packages.tex` 中 `\ddd` 的定义。

### 13. Ward--Takahashi 接触项的相位因子与复标量记号需核查

**文件位置**：`path-integral.tex` 第 556--562、581--592 行；对照 `freefield.tex` 中标签 `complex-scalar-u1-current` 的相位变换。

**当前内容**：一般 Ward 恒等式的接触项系数为 $-i\Delta\phi$，但随后对复标量 $U(1)$ 的特例写为 $iQ_j$，并在关联函数内使用 $\bar\psi$，文字却称其为 $\psi^*$。

**为何可疑**：沿用前文 $\Delta\psi=i\psi$、$\Delta\psi^*=-i\psi^*$，直接代入一般式给出的因子为 $-i(iQ_j)=Q_j$，与特例中的 $iQ_j$ 不同。还需确认复标量的 $\bar\psi$ 是否确指 $\psi^*$。后续动量空间表达式也应一起检查傅里叶变换与 $i$ 的约定。本次未修改路径积分章节。

**建议对照**：本文件紧邻的一般 Ward 恒等式及 $i[Q,\phi]=\Delta\phi$；[Avery 与 Schwab，§3.2--3.3](https://arxiv.org/html/1510.07038#S3.SS2) 的路径积分 Ward 推导（对照时保留本书自己的作用量与流的符号约定）。

### 12. Noether 小节之前的矢量场 Euler--Lagrange 分部积分需核查

**文件位置**：`freefield.tex` 第 45--60 行，经典场论“矢量场的 Euler--Lagrange 方程”的证明；本次仅重写其后的 Noether 小节，未改动此处。

**当前内容**：定义 $\Pi^{\mu\nu}=\partial\mathcal L/\partial F_{\mu\nu}$，随后将变分的边界项写为
$$
2\partial_{[\mu}(\Pi^{\mu\nu}\delta A_{\nu]}),
$$
并在体项中使用 $(\partial_{[\mu}\Pi^{\mu\nu})\delta A_\nu$。

**为何可疑**：此处反对称化括号跨越了重复的哑指标，第二个表达式还只有左方括号，不能清楚表示合法的指标反对称化。应从 $\Pi^{\mu\nu}(\partial_\mu\delta A_\nu-\partial_\nu\delta A_\mu)$ 对照分部积分，检查边界项与 $\Pi^{[\mu\nu]}$ 的位置及二倍因子；需与后面的方程 $B^\mu-2\partial_\nu\Pi^{[\nu\mu]}=0$ 保持一致。

**建议对照**：本节的 $F_{\mu\nu}=\partial_\mu A_\nu-\partial_\nu A_\mu$ 定义；新 Noether 小节的自由 Maxwell 例子；[David Tong《Quantum Field Theory》§1.1、§1.3](https://www.damtp.cam.ac.uk/user/tong/qft/qfthtml/S1.html) 的 Euler--Lagrange 与变分分部积分方法。

### 8. $\Pi(0)=0$ 的表述与 $\overline{\mathrm{MS}}$ 方案不一致

**文件位置**：`renormalization.tex` 第 1319 行附近；相关结果见第 1449、1453 行附近。

**PDF 位置**：第 216 页下部（全光子传播子公式后的 $\Pi(0)=0$ 文字）；第 219 页上部（“真空极化”小节的 $\overline{\mathrm{MS}}$ 结果）。

**当前内容**：正文声称 $\Pi(0)=0$，但本节在 $\overline{\mathrm{MS}}$ 方案下得到
$$
\Pi(p^2)=\frac{e^2}{2\pi^2}\int_0^1\!\d x\,x(1-x)
\ln\frac{m^2-p^2x(1-x)-i\epsilon}{\mu^2},
$$
因此一般有
$$
\Pi(0)=\frac{e^2}{12\pi^2}\ln\frac{m^2}{\mu^2}\neq0.
$$

**为何可疑**：$\Pi(0)=0$ 是 on-shell 减除条件；在 $\overline{\mathrm{MS}}$ 方案下仅当 $\mu=m$ 时才成立。光子极点仍位于 $p^2=0$，但这不等价于未经 on-shell 减除的 $\Pi(0)$ 必须为零。

**建议对照**：Peskin & Schroeder Eq. (7.90) 及真空极化的 on-shell/$\overline{\mathrm{MS}}$ 重整化条件。

### 9. $\phi^4$ 维数调控圈图的积分变量前后不一致

**文件位置**：`renormalization.tex` 第 784--809 行附近。

**PDF 位置**：第 208 页中部（“利用维数调控计算圈图”中的四点图、圈积分及 Feynman 参数化结果）。

**当前内容**：内线标记与分母使用 $k$、$p-k$，但积分测度写成 $\int\mu^{2\epsilon}\,\mathrm d^dp$。

**为何可疑**：$p$ 在同一式中已是外部总动量，圈动量应与分母一致地用 $k$。

**建议对照**：本文件第 784--809 行的图与后续 Feynman 参数化；标准 $\phi^4$ one-loop four-point integral。

### 10. 物理质量记号 $m_p$ 与 $m_P$ 不一致

**文件位置**：`renormalization.tex` 第 871--882 行附近。

**PDF 位置**：第 210 页上部至中部（$\overline{\mathrm{MS}}$ 方案下物理质量 $m_p^2$ 的定义）；同页下部的 RG 条件改用 $m_P$。

**当前内容**：文字与 RG 条件使用 $m_P$，但中间的物理质量公式左边写成 $m_p^2$。

**为何可疑**：大小写不一致会让读者无法确定是同一物理量还是两个不同定义。

**建议对照**：本文件第 871--882 行的文字定义和后续 RG 方程。

## 低优先级

### 11. 附录中的三处公式笔误

**文件位置**：`common-math-conclusion.tex` 第 55、126、131 行附近。

**PDF 位置**：第 227 页上部（Stirling 估计的被积函数展开）；第 228 页中部和下部（$\Gamma(x)\Gamma(y)$ 的两步换元公式）。

**当前内容**：

1. Stirling 估计中写成 `nn^n`。
2. 第 126 行第二个积分仍使用 $u^{y-1}$。
3. 第 131 行的 $(s(1-t))$ 缺少指数。

**为何可疑**：对应位置按上下文应分别为 $n^n$、$v^{y-1}$ 和 $(s(1-t))^{y-1}$。

**建议对照**：本文件相邻推导；标准 Stirling 公式与 Beta/Gamma 函数换元证明。
