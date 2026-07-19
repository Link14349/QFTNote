# 待核查问题清单

本文件只保留尚未核实或尚未处理的问题，并按优先级排列。用户核实后自行删除对应条目。

## 高优先级

### 1. Weyl/Dirac 章节中的场与张量记号

**文件位置**：`spinor.tex` 第 337、341、349、393 行附近。

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

**当前内容**：正文称“$f$场的传播子动量量纲为 $2\Delta_f$”，并写出
$$
D=\sum_f2I_f\Delta_f+\sum_iN_i\mathcal D_i-\sum_i dN_i+d.
$$

**为何可疑**：内线传播子在高动量下应贡献负的动量次数；Dirac 传播子行为是 $p^{-1}$，也不等于 $p^{-2\Delta_\psi}=p^{-3}$。当前中间式似乎无法推出后面的 $D=d-\sum_fE_f\Delta_f-\sum_iN_i\Delta_i$。

**建议对照**：Peskin & Schroeder §10.1 的 superficial degree of divergence 计数；Schwartz 的 power counting 章节。

### 3. $\phi^3$ 一圈二点 1PI 图中疑似混入非 1PI 图

**文件位置**：`renormalization.tex` 第 980--1026 行附近。

**当前内容**：质量重整化中将气泡图与一个通过单根内线连接蝴蚪圈的图相加，得到极点相消，并据此声称 $\delta_Z=\delta_m=0$。

**为何可疑**：连接蝴蚪的单根线一切即断，看起来并非 1PI 二点图；标准 $\phi^3$ 一圈二点函数的发散性还应按时空维数和 tadpole/one-point counterterm 的处理分别讨论。

**建议对照**：标准 $\phi^3$ 理论的 1PI 二点函数和 tadpole 重整化；Peskin & Schroeder §10；Schwartz 重整化章节。

### 4. QED 质量反项 $\delta_m$ 的量纲不对

**文件位置**：`renormalization.tex` 第 1120--1124、1515--1527 行附近。

**当前内容**：Lagrangian 中写有 $-\delta_m\bar\psi_r\psi_r$，但后面得到
$$
\delta_m=-\frac{e^2}{4\pi^2}\left(\frac1\epsilon+\ln4\pi-\gamma\right),
$$
右边没有质量因子。

**为何可疑**：按当前 Lagrangian 定义，$\delta_m$ 应具有质量量纲；圈图发散部分也显式正比于 $m$。可能是缺少一个 $m$，或前面本意是 $-m\delta_m\bar\psi\psi$。

**建议对照**：Peskin & Schroeder §10.2 的 QED electron self-energy counterterms；Schwartz QED renormalization 章节。

### 5. QED 传播子与反常磁矩推导中的多处公式笔误

**文件位置**：`renormalization.tex` 第 1357、1374、1628 行附近。

**当前内容**：(1) resummed 电子传播子分母末尾写成 $-i\epsilon$，而前面均为 $+i\epsilon$；(2) $\Gamma^\mu$ 的线性组合中写了自由指标不匹配的 $(p-k)^\nu$；(3) 系数奇偶分解式中出现 `x_1^-x_1`。

**为何可疑**：分别与 Feynman prescription、自由指标一致性及前一行的代数式冲突。

**建议对照**：本文件相邻公式；Peskin & Schroeder §6.2、§10.2 及 vertex form factors 的推导。

### 6. Callan--Symanzik 方程推导中导数消失

**文件位置**：`renormalization.tex` 第 1672--1684 行附近。

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

**当前内容**：两处左边均写为 $|\mathcal M_{aver}|$，但右边分别是 $|\mathcal M|^2$ 的自旋平均以及量纲为 $e^4$ 的结果。

**为何可疑**：按后文散射截面公式及第 1915 行的记法，左边应当也是 $|\mathcal M_{aver}|^2$。

**建议对照**：本文件第 1915、2017、2077 行附近；Peskin & Schroeder §5.1 的 spin sums/averages。

## 中优先级

### 8. $\Pi(0)=0$ 的表述与 $\overline{\mathrm{MS}}$ 方案不一致

**文件位置**：`renormalization.tex` 第 1286 行附近；相关结果见第 1399、1403 行附近。

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

**当前内容**：内线标记与分母使用 $k$、$p-k$，但积分测度写成 $\int\mu^{2\epsilon}\,\mathrm d^dp$。

**为何可疑**：$p$ 在同一式中已是外部总动量，圈动量应与分母一致地用 $k$。

**建议对照**：本文件第 784--809 行的图与后续 Feynman 参数化；标准 $\phi^4$ one-loop four-point integral。

### 10. 物理质量记号 $m_p$ 与 $m_P$ 不一致

**文件位置**：`renormalization.tex` 第 871--882 行附近。

**当前内容**：文字与 RG 条件使用 $m_P$，但中间的物理质量公式左边写成 $m_p^2$。

**为何可疑**：大小写不一致会让读者无法确定是同一物理量还是两个不同定义。

**建议对照**：本文件第 871--882 行的文字定义和后续 RG 方程。

## 低优先级

### 11. 附录中的三处公式笔误

**文件位置**：`common-math-conclusion.tex` 第 55、126、131 行附近。

**当前内容**：

1. Stirling 估计中写成 `nn^n`。
2. 第 126 行第二个积分仍使用 $u^{y-1}$。
3. 第 131 行的 $(s(1-t))$ 缺少指数。

**为何可疑**：对应位置按上下文应分别为 $n^n$、$v^{y-1}$ 和 $(s(1-t))^{y-1}$。

**建议对照**：本文件相邻推导；标准 Stirling 公式与 Beta/Gamma 函数换元证明。
