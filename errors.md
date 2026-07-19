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

## 中优先级

### 2. $\Pi(0)=0$ 的表述与 $\overline{\mathrm{MS}}$ 方案不一致

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

## 低优先级

### 3. 附录中的三处公式笔误

**文件位置**：`common-math-conclusion.tex` 第 55、126、131 行附近。

**当前内容**：

1. Stirling 估计中写成 `nn^n`。
2. 第 126 行第二个积分仍使用 $u^{y-1}$。
3. 第 131 行的 $(s(1-t))$ 缺少指数。

**为何可疑**：对应位置按上下文应分别为 $n^n$、$v^{y-1}$ 和 $(s(1-t))^{y-1}$。

**建议对照**：本文件相邻推导；标准 Stirling 公式与 Beta/Gamma 函数换元证明。
