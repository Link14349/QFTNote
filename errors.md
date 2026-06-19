# 待核查问题清单

以下问题需要对照标准教材（Peskin & Schroeder, Schwartz）进一步核实。
Claude 复核记录见每条下方的「复核」段。

---

## 1. 顶点修正反项 δ_e 系数（✅ 已修复：根因同 #23）

**文件**: `renormalization.tex` 第 1540、1550、1564 行

**完整推导（已逐项重算）**: 这里的关键在于发散部分与有限部分的前因子**天然不同**：
$$\bar\Gamma^\mu_{loop}=-\frac{ie^3}{8\pi^2}\!\int\!\Big(\tfrac1\epsilon-\gamma+\ln4\pi-2-\ln\tfrac\Delta{\mu^2}\Big)\gamma^\mu+\frac{ie^3}{16\pi^2}\!\int\!\frac{\mathcal N^\mu}{\Delta},$$
其中发散部分（$\propto\int\ell^2/(\ell^2-\Delta)^3$）系数 1/8π²，有限部分（$\propto\int1/(\ell^2-\Delta)^3$）系数 1/16π²，两者差因子 2（来自 $\ell^2$ 积分多出的 $d/2=2$）。有限部分的分子
$$\mathcal N^\mu=\gamma_\alpha(\slashed K+m)\gamma^\mu(\slashed P+m)\gamma^\alpha=-2\slashed P\gamma^\mu\slashed K-2m^2\gamma^\mu+4m[(1-2x_1)p+(1-2x_2)k]^\mu,$$
$\slashed P=(1-x_1)\slashed p-x_2\slashed k$, $\slashed K=(1-x_2)\slashed k-x_1\slashed p$。**这正是笔记原来写的 A^μ（三项结构全部正确，含第三项 (1-2x_i)）。**

**问题的真相**: 笔记原来用**单一前因子 1/16π² + $A^\mu=\mathcal N^\mu$**，等于
"发散部分 1/16π²（错，应 1/8π² → δ_e 错半）+ 有限部分 1/16π²×$\mathcal N^\mu$（恰好对）"。

**✅ 修复（4 处）**:
- 第 1540 行前因子 `-ie³/16π²` → `-ie³/8π²`（修对发散/δ_e）。
- 第 1564 行前因子 `+ie³/16π²` → `+ie³/8π²`。
- 第 1550 行 `δ_e=-e³/32π²(…)` → `-e³/16π²(…)`。
- **第 1545-1546 行 $A^\mu$ 减半**（`-2[…]→-[…]`、`-2m²→-m²`、`4m[…]→2m[…]`），即令 $A^\mu=\tfrac12\mathcal N^\mu$，以便在单前因子 1/8π² 下有限部分 $\tfrac{ie^3}{8\pi^2}\cdot\tfrac12\mathcal N^\mu=\tfrac{ie^3}{16\pi^2}\mathcal N^\mu$ 保持原来的（正确）数值不变。

**净效果**: δ_e 修正为 -e³/16π²；有限/g-2 部分数值**与原来相同**（原本就对），只是改写成 (1/8π²)×(½𝒩^μ)。

**独立验证**: Ward-Takahashi Z₁=Z₂ 要求 δ_e=e·δ_ψ=-e³/16π²（δ_ψ 见第 1475 行），与修复值一致。✓ 有限项 𝒩^μ 的 σ^{μν}q_ν 部分给出 a_e=α/2π（系数 e²/16π²×𝒩^μ，正确量级）。✓

**Δ 复核**: 第 1544 行 Δ 正确（仅 x₁↔x₂、p↔k 的标注约定差异，自洽）。

**仍未做**: 本节虽题为"电子反常磁矩"，但正文止于重整化后顶点表达式，**未真正做 Gordon 分解提取出 a_e=α/2π 的数值**（如需我可补）。

**建议对照**: Peskin & Schroeder §6.3（g-2）、§10.3、(A.44) 及 Ward 恒等式 Z₁=Z₂。

---

## 3. φ³ 理论三点函数积分（✅ 已修复：32π²→16π²）

**文件**: `renormalization.tex` 第 1078-1079 行

**复核（Claude）**:
- Feynman 参数化与分母符号**正确**。按第 1078 行的动量分配（传播子 l², (p+l)², (k-l)²），配方得 Δ = m² - p²x₁(1-x₁) - k²x₂(1-x₂) - 2x₁x₂ p·k，与第 1079 行完全一致，包括 `-2x₁x₂ p·k` 的负号。这一条原始疑虑可消除。
- **新发现**: 整体系数疑似差因子 2。三传播子顶点：(-ig)³·(i)³ = g³，Feynman trick 带 Γ(3)=2! 的因子，∫d⁴l/(2π)⁴ 1/(l²-Δ)³ = -i/(32π²Δ)，故
  $$= g^3\cdot 2\int dx_1dx_2\left(\frac{-i}{32\pi^2\Delta}\right) = -\frac{ig^3}{16\pi^2}\int dx_1dx_2\frac1\Delta.$$
  即应为 `-ig³/16π²`，而非当前的 `-ig³/32π²`。（φ³ 三角顶点修正对称因子为 1，不应再除 2。）请核实 Feynman trick 的 2! 因子是否漏乘。

**根因（已定位）**: 见问题 #23——附录 `common-math-conclusion.tex:315` 的 Feynman 参数化公式**漏写了 (n-1)! 因子**。n=2 时 (n-1)!=1 无影响（故 φ⁴ 计算无误），但 n=3 时缺了 2!=2，正是此处因子 2 的来源。

**✅ 修复（2 处已改）**:
- `common-math-conclusion.tex:315`（#23）已补上 (n-1)! 并新增带幂次的一般公式。
- `renormalization.tex:1079` 系数已由 `-ig³/32π²` 改为 `-ig³/16π²`。
（δ_g=0 的结论不受影响，第 1083 行无需改。）

**建议对照**: Peskin Eq.(A.39)、(A.44)。

> ⚠️ **同源警告**：问题 **#1（δ_e，p.211）也是同一根因**。QED 顶点修正（`renormalization.tex:1539-1540`）同样是 3 个传播子（n=3），若也漏了 2!，则 `第1540行` 前因子应由 `-ie³/16π²` 改为 `-ie³/8π²`，进而 `δ_e`（第1550行）由 `-e³/32π²` 改为 `-e³/16π²`——这恰好满足 Ward 恒等式 Z₁=Z₂。**本次未改 #1（你只授权了 #3）**，需要的话我可以一并修正。

---

## 4. 真空极化 Π(p²) 系数（系数与符号均正确；但 Π(0)=0 的说法与 MS̄ 不一致）

**文件**: `renormalization.tex` 第 1399、1403 行；说法见第 1286 行

**复核（Claude）**:
- 第 1399 行系数 `e²/2π²` = 2α/π **正确**，符号也正确。我从第 1391 行圈图发散部分（∫x(1-x)=1/6）出发，配合 δ_A=-e²/12π²(…)（第 1395 行），重新推导得到
  $$\Pi(p^2)=\frac{e^2}{2\pi^2}\int_0^1 dx\,x(1-x)\ln\frac{m^2-p^2x(1-x)-i\epsilon}{\mu^2},$$
  与文中一致。系数无误，这条原始疑虑可消除。
- **但需注意**: 第 1286 行声称「Π(0)=0」。在本文实际采用的 MS̄ 方案下，Π(0)=e²/(12π²)·ln(m²/μ²) ≠ 0（仅当 μ=m 才为零）。光子仍保持无质量（极点 p²=0 不变）这一结论不受影响，但「Π(0)=0」「Π(p²)>0」的表述属于 on-shell（减除后）语境，与 MS̄ 的 Π 不符，建议措辞上区分方案，或明确说这里指减除后的 Π̂(p²)=Π(p²)-Π(0)。

**建议对照**: Peskin Eq.(7.90)。

---

## 6. 有质量矢量场的正则动量 Π^{0i}（✅ 复核：正确）

**文件**: `gaugetheory.tex` 第 26-34 行

**复核（Claude）**: **自洽且正确**。在本文 (+---) 度规下 F^{0i}=∂⁰A^i-∂^iA⁰=-E^i，故 Π^{0i}=-F^{0i}=+E^i，与矩阵和第 34 行一致。后续哈密顿量推导（第 43-58 行）我也复核通过，最终 H=½E²+½B²+½m²φ²+½m²A⃗² 自洽。此条可删除。

---

## 7. Schwinger-Dyson 展开的组合因子（✅ 复核：正确）

**文件**: `schwinger-dyson-expansion.tex` 第 31 行

**复核（Claude）**: **三项系数 2,1,2 完全正确**。我按 Wick 缩并重算二阶：⟨φ²ₓφ²_y⟩=D_xxD_yy+2D_xy²，加上蝌蚪项，得
$$D_{12}-(g/2)^2\!\int(D_{1x}D_{xx}D_{yy}D_{y2}+2D_{1x}D_{xy}^2D_{y2}+2D_{1x}D_{xy}D_{yy}D_{x2}),$$
与第 31 行逐项吻合。此条可删除。

---

## 核查优先级

| 优先级 | 编号 | 影响范围 |
|-------|------|---------|
| ✅ | ~~1. δ_e 系数（与 Z₁=Z₂ 冲突）~~ | 已修复（→1/16π²），根因见 #23 |
| ✅ | ~~2. 裸/重整化耦合约定~~ | 已修复 |
| ✅ | ~~3. φ³ 三点函数整体系数（因子 2）~~ | 已修复（32π²→16π²），根因见 #23 |
| 中 | 4. Π(0)=0 措辞 vs MS̄ | 光子传播子修正的表述 |
| ✅ | ~~5. Wick 旋转图~~ | 已修复 |
| ✅ | ~~6. 有质量矢量场 Π^{0i}~~ | 复核正确，可删 |
| ✅ | ~~7. Schwinger-Dyson 组合因子~~ | 复核正确，可删 |
| ✅ | ~~8. Yang-Mills 术语大小写~~ | 已修复 |
| 中 | 9. 光子传播子 D_{μν} 符号 | gaugetheory.tex |
| 中 | 10. 标量QED Noether 流 A^ν 项 | gaugetheory.tex |
| 低 | 11. ξ 规范固定项缺平方 | gaugetheory.tex（排版/公式） |
| 低 | 12. pion 散射截面分母 | gaugetheory.tex |
| 低 | 13. 杂项小笔误 | freefield.tex 等 |

---

## 9. 光子传播子 D_{μν} 中 p_μp_ν 项符号（✅ 已修复）

**文件**: `gaugetheory.tex` 第 328 行

**问题**: 由第 319 行 G^{μν}=(-g^{μν}+(1-ξ)p^μp^ν/p²)/(p²+iε)（已验证为 O_{μν} 的正确逆），则 D_{μν}=iG_{μν}=−i/(p²+iε)·(g_{μν}−(1-ξ)p_μp_ν/p²)，p_μp_ν 项应为**减号**。佐证：第 365 行 Coulomb 势计算用的就是减号。

**✅ 修复**: 第 328 行 `(g_{\mu\nu}+(1-\xi)…)` → `(g_{\mu\nu}-(1-\xi)…)`。

---

## 10. 标量 QED 的 Noether 流 A^ν 项

**文件**: `gaugetheory.tex` 第 429 行

**当前内容**:
```latex
J^\nu=i(\psi\partial^\nu\psi^*-\psi^*\partial^\nu\psi-2e\psi\psi^*A^\nu)
```

**问题**: 直接用 Noether 公式 j^μ=(D^μψ)*(iψ)+(D^μψ)(-iψ*) 算得
$$J^\nu=i(\psi\partial^\nu\psi^*-\psi^*\partial^\nu\psi)+2e\psi\psi^*A^\nu,$$
即 A^ν 项应为 **+2eψψ*A^ν（在 i(...) 之外，实系数）**。第 429 行把它写在 i(...) 内、且为 -2e，展开后得 -2ieψψ*A^ν，与正确结果（+2e）的系数和因子 i 都不符。注意第 417/423 行的 J^ν=ie(…-2ieψψ*A^ν) 反而与正确的 Noether 流相差一个整体因子 e（即电流 = e×Noether），是自洽的；只有第 429 行有误。请核对。

---

## 11. ξ 规范固定项缺平方

**文件**: `gaugetheory.tex` 第 306、310、343 行

**当前内容**: 多处把规范固定项写成 `-\frac{(\partial_\mu A^\mu)}{2\xi}`，缺一个平方。

**问题**: 应为 $-\frac{1}{2\xi}(\partial_\mu A^\mu)^2$。否则第 310 行后续推出的 O_{μν}=g_{μν}∂²-(1-1/ξ)∂_μ∂_ν 无法成立（该结果本身正确，说明确为漏写平方）。属公式笔误，建议本人确认后补上平方。

---

## 12. pion 散射的微分截面分母 & t 通道传播子动量

**文件**: `gaugetheory.tex` 第 577、585 行

**问题**:
1. 第 577 行 t 通道传播子分母写作 `(p-k')^2`，但 (p-k')²=u；按图（顶点 a 接 p 入、k 出）动量转移应为 (p-k)²=t。最终 `/t` 与结果 ie²(u-s)/t 正确，故 577 行分母处应为 (p-k)² 笔误。
2. 第 585 行 (dσ/dΩ)_CM 分母为 `64π²E_CM|\vec p_i|`。标准弹性 2→2 公式为 dσ/dΩ=|M|²/(64π²E_CM²)（即 64π²s）。当前 E_CM|p_i| 与 E_CM² 一般不等，疑似有误，请核对。

---

## 13. 杂项小笔误（freefield.tex）

**文件**: `freefield.tex` 第 553 行

**问题**: 动量算子写成 `P^i=∫∂^0φ∂^iπ d³x`，其中 ∂^iπ 疑应为 ∂^iφ（紧接其后的 `-∫φ_tφ_i d³x` 是正确的，φ_i=∂_iφ）。属笔误，不影响后续结论。

---

## 14. Yang-Mills：夸克规范群写错（概念性错误）

**文件**: `yang-mills.tex` 第 310 行

**当前内容**: 「Quark三色就代表其有三个生成元, 也就是规范群为 SU(2)」

**问题**: 此句两处错误：
1. 「三色」指基本表示是 **3 维**，对应规范群 **SU(3)**（QCD），不是 SU(2)。
2. 「三色 = 三个生成元」混淆了表示维数与生成元个数。SU(3) 有 **8 个生成元**（8 个胶子），而 SU(2) 才有 3 个生成元。

建议改为：夸克有 3 种颜色，处于 SU(3) 的基本表示（3 维），SU(3) 有 8 个生成元。属概念性错误，建议本人确认。

---

## 15. Yang-Mills：鬼场项结构常数下标 & 索引笔误

**文件**: `yang-mills.tex` 第 139、516 行

**问题**:
1. 第 139 行鬼场项写作 `gf_{aab}\partial^\mu\bar c^c A_\mu^a c^b`，结构常数下标 `f_{aab}` 重复了 a，应为 `f_{cab}`（与第 145 行一致）。
2. 第 516 行 `\delta_B\delta_B f` 第一项 `D_\mu c^a D_\mu c^b`，两个都是 μ；按其前的 ∂²f/∂A^a_μ∂A^b_ν 应为 `D_\mu c^a D_\nu c^b`。属索引笔误。

---

## 16. 路径积分：若干公式笔误

**文件**: `path-integral.tex` 第 112、287、596 行

**问题**:
1. 第 112 行场切片振幅指数中动能项 `(\phi_{j+1}(x)-\phi_j(x))/(2\Delta t^2)` 缺平方，应为 `(\phi_{j+1}-\phi_j)^2`。
2. 第 287 行 `+\frac{g}3!\phi^3` 应为 `\frac{g}{3!}`（当前渲染为 (g/3)!）。
3. 第 596 行 Yukawa 势开头写作 `U(r)=-\frac{g_1g_2 e^{-mr}}{4\pi r^2}`，分母 r² 应为 r（与第 634、640 行的推导结果 `4\pi r` 一致）。

---

## 17. 相互作用：真空图展开测度笔误

**文件**: `interaction.tex` 第 119-120 行

**问题**: 一阶/二阶真空图写作 `\int\d^3x`、`\int\d^3x\d^3y`，应为 `\d^4x`、`\d^4x\d^4y`（时空四维积分）。不影响后续结论。
（备注：第 485 行 2→2 散射截面 `|M|²|p_f|/(64π²E_CM²|p_i|)` 是**正确**的标准公式，可作为核对 gaugetheory 第 585 行问题#12 的参照。）

---

## 18. 标量QED EoM 漏项（低优先）

**文件**: `gaugetheory.tex` 第 416 行

**问题**: 复标量场 EoM 写作 `(\partial^2+m^2)\psi=-2ieA_\mu\partial^\mu\psi+e^2\psi A_\mu A^\mu`，缺少 `-ie(\partial_\mu A^\mu)\psi` 一项（在 Lorenz 规范 ∂·A=0 下才为零）。若未隐含取规范，建议补上或注明。

---

## 19. 预备知识：术语 / 公式笔误

**文件**: `preparation.tex` 第 634、691、723、807 行

**问题**:
1. 第 634 行「$N=a^\dagger a$, $N$ 是幺正算符, $N^\dagger=N$」——$N$ 是**厄米**算符（自伴），不是幺正算符。应改「厄米算符」。
2. 第 691 行相干态波函数 `\exp{-\frac12 m\omega(x-\sqrt{2/m\omega}\alpha)}` 指数内缺平方，应为 `(x-\dots)^2`（Gaussian）。
3. 第 723 行 `x'^\mu=\lambda&\mu_{~~\nu}x^\nu` 有杂散的 `&`，应为 `\Lambda^\mu_{~~\nu}`。
4. 第 807 行「Lorentz张量... 具有协变性的张量称为 Lorentz矢量」——定义的是张量却写成「矢量」，应为「Lorentz张量」。

---

## 20. 旋量：Weyl/Dirac 章节笔误

**文件**: `spinor.tex` 第 337、341、349、393 行

**问题**（均为笔误，最终结论正确）：
1. 第 393 行 Dirac 拉氏量 `\mathcal L=i\psi_R^\dagger\sigma^\mu\partial_\mu\psi_R+i\psi_R^\dagger\sigma^\mu\partial_\mu\psi_R-\dots`，第二项重复了 ψ_R，应为 `i\psi_L^\dagger\bar\sigma^\mu\partial_\mu\psi_L`（与第 417 行 `\bar\psi(i\slashed\partial-m)\psi` 展开一致）。
2. 第 337 行 ψ_L 的 Lorentz 变换末尾 `\psi_R` 应为 `\psi_L`。
3. 第 341 行 `\delta\psi_L\frac12(\dots)\sigma^j\psi_R` 缺等号，且 ψ_R 应为 ψ_L。
4. 第 349 行 `-\sigma_{ijk}\theta^j\dots`，`\sigma_{ijk}` 应为 `\epsilon_{ijk}`。

---

## 21. 旋量：Dirac 生成元推导中 [σⁱ,σʲ] 漏因子 2（✅ 已修复，含下游一行）

**文件**: `spinor.tex`（行号因后续编辑有偏移，当前约 508、515、539 行）

**问题**: `[σ^j,σ^k]=2iε_{jkl}σ^l`，但原文用成了 `iε`：
- `[\gamma^j,\gamma^k]=-[\sigma^j,\sigma^k]\otimes 1=-i\epsilon_{jkl}\sigma^l\otimes 1` 应为 `-2i\epsilon_{jkl}\sigma^l\otimes 1`。
- `\epsilon_{ijk}[\gamma^j,\gamma^k]=-2i\sigma^i` 应为 `-4i\sigma^i`。

**关键**: 仅改这两行会破坏下游 δψ。原文 δψ 的转动项写作 `i\epsilon_{ijk}\theta^i(\tfrac i4[\gamma^j,\gamma^k])`，本应是 `\tfrac i2\epsilon_{ijk}\theta^i(\tfrac i4[\gamma^j,\gamma^k])`（因 J^i=½ε_{ijk}S^{jk} 带 ½）。原文用"错的 −2iσ^i + 漏 ½"互相抵消恰好得到对的 δψ；要把 −4iσ^i 写对，δψ 的 ½ 也必须补上，否则 J^i 会从 σ^i/2 变成 σ^i/4。

**✅ 修复（3 处）**: 上述 `-i→-2i`、`-2i→-4i`，并把 δψ 转动项 `i\epsilon_{ijk}→\frac i2\epsilon_{ijk}`。修复后整条链自洽：δψ_rot=(i/2)θ^iσ^i、S^{μν}=i/4[γ^μ,γ^ν]、J^i=σ^i/2 全部正确。

---

## 22. 旋量 QED：散射截面若干疑点

**文件**: `spinor.tex` 第 1852-1853、1920、1996、2033 行

**问题**:
1. **Bhabha（第 1852-1853 行，建议核对因子 2）**: 由 `dσ/dΩ=|M|²/(64π²E_CM²)`（第 1848 行）与 `|M_aver|²=2e⁴X`，代入应得 `α²X/(2E_CM²)=α²X/(8E²)`。但第 1852 行写成 `α²/(2E_CM|\vec p_i|)·X`，第 1853 行得 `α²/(4E²)·X`。因 E_CM=2|p_i|=2E，`2E_CM²=4E_CM|p_i|`，故第 1852 行分母疑漏因子 2（应为 `4E_CM|p_i|`），最终应为 `α²X/(8E²)`。请核对。
2. **Møller（第 1920 行）**: `(s-2m)^2`、`(t-2m)^2` 中的 `2m` 量纲不对（s,t 是 mass²），应为 `(s-2m^2)^2`、`(t-2m^2)^2`（第 1921 行的 `s-2m^2`、`s-6m^2` 写法正确）。
3. **Compton |M|²（第 1996 行）**: `m^4-2u+m^2(3s+u)` 中 `-2u` 与其余 mass⁴ 项量纲不一致（u 是 mass²），疑似笔误/漏项，请核对标准 Compton 振幅。
4. **Klein-Nishina（第 2033 行）**: `dσ/dΩ=\frac{e^4}{64\pi^2m^2}\frac{\omega'^2}{\omega^2}(\frac{\omega'}{\omega}-\sin^2\theta)` 与第 2010 行 `|M|²=2e⁴(ω'/ω+ω/ω'-sin²θ)` 不一致：(a) 似乎漏了 `+ω/ω'` 项；(b) 前因子应为 `e^4/(32\pi^2 m^2)=α²/2m²`（标准 Klein-Nishina），当前 `e^4/64π²m²` 疑少因子 2。请核对。

---

## 23. 附录数学公式：两处实质错误 + 笔误

**文件**: `common-math-conclusion.tex`

**问题**:
1. **第 315 行 Feynman 参数化公式漏 (n-1)! 因子（重要，是 #3、#1 的根因）—— ✅ 已修复**：原写作
   $$\frac1{A_1\cdots A_n}=\int_0^1\!dx_1\cdots dx_n\,\delta(\textstyle\sum x_i-1)\frac1{[\sum A_ix_i]^n},$$
   已改为分子带 **(n-1)!**，并新增带幂次的一般公式
   $$\frac1{A_1^{\alpha_1}\cdots A_n^{\alpha_n}}=\frac{\Gamma(\sum\alpha_i)}{\prod\Gamma(\alpha_i)}\int\!\delta(\textstyle\sum x_i-1)\frac{\prod x_i^{\alpha_i-1}}{[\sum x_iA_i]^{\sum\alpha_i}}.$$
   n=2 时 (n-1)!=1 故第 320 行的 1/(AB) 无误，但 n≥3（如 φ³ 三角图、QED 顶点）会漏因子 2!=2。
2. **第 14 行带源 Gaussian 积分指数应为 A⁻¹（✅ 已修复）**：`\exp{\frac12 J^T A J}` → `\exp{\frac12 J^T A^{-1} J}`。注：path-integral.tex 第 256-257 行实际推导用的是 K⁻¹，本来就对，仅此参考公式写错。
3. 笔误：第 55 行 `nn^n` 应为 `n^n`（Stirling 估计，多写了一个 n，第 63 行结果正确）；第 126 行第二个积分 `u^{y-1}` 应为 `v^{y-1}`；第 131 行 `(s(1-t))` 漏指数，应为 `(s(1-t))^{y-1}`。

其余（Γ/B 函数性质、n 维超球面角 Ω_n=2π^{n/2}/Γ(n/2)、维数调控圈积分参考公式第 326–331 行）均**复核正确**。

---

## 复核覆盖范围说明（Claude）

本次已逐章通读并核对推导：`preparation.tex`、`freefield.tex`、`interaction.tex`、`path-integral.tex`、`gaugetheory.tex`、`spinor.tex`、`yang-mills.tex`、`renormalization.tex`、`schwinger-dyson-expansion.tex`、`common-math-conclusion.tex`（全部章节 + 附录均已核对）。
按项目约定，以上仅记录待核查项，未自行改动任何符号或数学推导；纯格式笔误也一并列出供你确认（避免误改物理内容）。

---

## PDF 页码对照（重建后刷新，229 页版；行号按 grep 内容定位）

**✅ 已修复**

| 编号 | 问题 | 文件:行 | PDF 页 |
|---|---|---|---|
| 1 | QED 顶点 δ_e/前因子/A^μ | renormalization.tex:1577 | **p.211** |
| 3 | φ³ 三点函数系数 32→16π² | renormalization.tex:1084 | **p.205** |
| 9 | 光子传播子 p_μp_ν 符号 +→− | gaugetheory.tex:328 | **p.109** |
| 13 | P^i 笔误 ∂ⁱπ→∂ⁱφ | freefield.tex:553 | **p.41** |
| 14 | 夸克规范群 SU(2)→SU(3) | yang-mills.tex:310 | **p.173** |
| 15 | 鬼场 f_{aab}→f_{cab}；δ_Bδ_Bf 索引 | yang-mills.tex:139 | **p.171** |
| 16 | 路径积分缺平方/`\frac{g}{3!}`/U(r) 分母 | path-integral.tex (112/287/598) | **p.86/90/97** |
| 17 | 真空图测度 d³x→d⁴x | interaction.tex:119 | **p.65** |
| 19 | 幺正→厄米/相干态平方/Λ/张量 | preparation.tex:636 等 | **p.22–26** |
| 21 | [σ,σ] 漏因子 2（含 δψ ½） | spinor.tex:508 | **p.126** |
| 22d | Møller (s-2m)²→(s-2m²)² | spinor.tex:1951 | **p.161** |
| 23a | Feynman 参数化 (n-1)! + 一般式 | common-math-conclusion.tex:315 | **p.223** |
| 23b | 带源 Gaussian A→A⁻¹ | common-math-conclusion.tex:14 | **p.217** |

**⬜ 待处理**

| 编号 | 问题 | 文件:行 | PDF 页 |
|---|---|---|---|
| 4 | "Π(0)=0" 表述 vs MS̄ | renormalization.tex:1312 | **p.208** |
| 10 | 标量QED Noether 流 A^ν 项 | gaugetheory.tex:429 | **p.112** |
| 11 | ξ 规范固定项缺平方 | gaugetheory.tex:306/310/343 | **p.108** |
| 12 | pion t 通道动量 & 截面分母 | gaugetheory.tex:585 | **p.114** |
| 18 | 标量QED EoM 漏 -ie(∂·A)ψ | gaugetheory.tex:416 | **p.111** |
| 20 | Weyl/Dirac 笔误 ψ_R 重复等 | spinor.tex:393 | **p.124** |
| 22a | Bhabha 截面疑差因子 2 | spinor.tex:1883 | **p.160** |
| 22b | Compton \|M\|² 量纲项 -2u | spinor.tex:2027 | **p.162** |
| 22c | Klein-Nishina 漏项/因子 | spinor.tex:2064 | **p.163** |
| 23c | Stirling `nn^n`；Γ 证明 u→v | common-math-conclusion.tex:55 | **p.218** |

**✅ 复核为正确（可删）**

| 编号 | 内容 | 文件:行 | PDF 页 |
|---|---|---|---|
| 6 | 有质量矢量场 Π^{0i}=E^i | gaugetheory.tex:34 | **p.100** |
| 7 | Schwinger-Dyson 组合因子 2,1,2 | schwinger-dyson-expansion.tex:33 | **p.226** |
