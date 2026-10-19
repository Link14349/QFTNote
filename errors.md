# 待核查问题清单

本文件只保留尚未核实或尚未处理的问题，并按优先级排列。用户核实后自行删除对应条目。下文旧条目的 PDF 页码是 Noether 小节重整前记录的物理页码；2026-09-18 重整使后续章节分页变化，应优先按文件位置与公式内容定位。

## 需要人工复核表达的

本栏记录新增或改写后需要本人确认的说明性文字，不表示已判定存在数学错误。核实后由本人删除对应条目；其余待核查问题仍按下方优先级维护。

### 待复核：经典场论 Noether 定理部分的整体重写

**文件位置**：`freefield.tex` 第 73--699 行，标签 `sec:classical-noether`，即“经典场论”中的整个“Noether定理”小节。

**当前内容**：根据 `symmetry.md` 重写并扩充了这一节，保留本笔记的 $(+---)$ 约定，依次讨论变分对称性与拉回、第一定理、内禀及平移／Lorentz 对称性的例子、Weyl／共形对称性、第二定理，以及 Noether's Trick；补充了与后文 Ward 恒等式的流符号衔接。

**需要人工复核的表达**：本次涉及整节结构、说明文字和推导的改写，虽已做一致性检查，仍需本人确认其准确性、适用范围及是否符合自己的理解。

- [ ] 运动方程对称性、离壳变分对称性、微分同胚协变性与固定背景对称性的区分是否清楚；拉回及背景结构的说明是否容易误读。
- [ ] 第一定理中离壳恒等式与在壳守恒的关系、背景度规变化的附加条件，以及 $(+---)$ 下 Hilbert 能动张量的定义和符号是否表达充分。
- [ ] 复标量 $U(1)$、标量平移／Lorentz、Maxwell 和 Dirac 平移例子的组织与详略是否合适；正则张量、Hilbert 张量、改进项及自旋部分的区别是否讲清。
- [ ] Weyl 迹恒等式、曲率耦合标量及改进张量、共形等距与补偿 Weyl 变换、共形流的推导是否自然；“先变分再取平直极限”和局部适用范围的提醒是否足够。
- [ ] 第二定理及 Einstein／Maxwell／标量 QED 三例，是否清楚体现无需使用运动方程的恒等关系；形式伴随不取复共轭的约定是否明确。
- [ ] Noether's Trick 与第二定理的区别、局域化参数导数项的保留，以及 $j$、$\widetilde j$ 与后文 Ward 恒等式的整体符号衔接是否清晰；整节术语和表述是否符合笔记风格。

**建议对照的参考来源**：本次重写所据的 [symmetry.md](/Users/link/Documents/zhihu/symmetry.md)；本笔记 `preparation.tex` 的符号约定、复标量守恒荷及 `path-integral.tex` 的 Ward 恒等式；David Tong《Quantum Field Theory》§1.3；Avery 与 Schwab《Noether's Second Theorem and Ward Identities for Gauge Symmetries》§2。

### 待复核：Schwinger–Dyson 中路径积分导数、编时导数与接触项的区分

**文件位置**：`path-integral.tex` 第 533--567 行，标签 `sd-time-ordering-contact`、`sd-time-derivative-contact`；以及 `schwinger-dyson-expansion.tex` 第 10 行的附录提醒。

**PDF 位置**：2026-10-19 编译版本正文第 109--110 页、附录第 246 页；后续分页变化时以源文件标签为准。

**当前内容**：根据所提供的两张截图新增说明，区分路径积分平均与算符期望，列出编时关联函数求导时的等时对易子接触项；进一步介绍 $\mathcal T^*$ 与普通 $\mathcal T$ 的区别，并以实标量场的一阶、二阶时间导数解释 Schwinger–Dyson 方程中的 $-i\delta^4(x-y)$ 项。

**需要人工复核的表达**：

- [ ] 路径积分中的导数插入等于对关联函数求导的表述，以及“同一正则化下的分布意义”的限定是否充分、清楚。
- [ ] “先对未求导的场编时，再求导”对 $\mathcal T^*$ 的说明是否准确，是否需要进一步限定插入类型及接触点处的定义。
- [ ] “不能直接当作普通编时乘积内的算符运动方程并令其为零”是否清楚区分了路径积分插入与算符运动方程，避免误读为算符运动方程失效。
- [ ] 玻色算符、虚时间及费米交换符号的适用范围说明是否合适；实标量场例子中“标准动能项、无导数相互作用”的前提是否足够醒目。
- [ ] 附录对导数位置与接触项来源的提醒是否与正文及原有记号一致，整段详略是否符合笔记风格。

**建议对照的参考来源**：本次提供的截图（式 (2.37) 及紧接的编时求导公式）；本笔记的时间顺序算符定义及 Feynman 传播子方程；[Tom Magorsch 的 Schwinger–Dyson 推导](https://notes.tommago.com/notes/Schwinger-Dyson-equations/)（用于对照实标量场等时对易子及接触项）。

## 高优先级

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
