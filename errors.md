# 待核查问题清单

以下问题需要对照标准教材（Peskin & Schroeder, Schwartz）进一步核实。

---

## 1. 顶点修正反项 δ_e 系数

**文件**: `renormalization.tex` 第 1550 行

**当前内容**:
```latex
\delta_e=-\frac{e^3}{32\pi^2}\left(\frac1\epsilon-\gamma+\ln4\pi\right),
```

**问题**: 标准 QED 顶点重整化（Feynman 规范）的结果为：
$$Z_1 = 1 - \frac{e^2}{16\pi^2}\left(\frac{1}{\epsilon} - \gamma + \ln 4\pi\right)$$

按文中 Lagrangian 的写法（反项为 `-δ_e ψ̄_r A̸_r ψ_r`，不含额外 e 因子），若 δ_e 需吸收 e³ 量级，则系数为 1/(16π²) 或 1/(32π²) 取决于具体计算细节。目前 1/(32π²) 比常规结果 1/(16π²) 少了一个因子 2。

**建议对照**: 
- Peskin & Schroeder Eq. (7.47) 及相关推导
- Schwartz Ch. 19 中 QED 顶点修正部分

**上下文**: 该系数会影响后续的 Wilson 系数及物理预测（如反常磁矩的有限部分），需确保与所选方案自洽。

---

## 3. φ³ 理论三点函数积分的符号

**文件**: `renormalization.tex` 第 1078-1079 行

**问题**: φ³ 顶点修正的一圈积分直接声称收敛（不需要维度调控吸收无穷大），这在 Δ_g = 1 的 super-renormalizable 理论中是合理的。但积分的具体表达式（Feynman 参数化结果）和符号建议核实，尤其注意：
- 三个传播子的 Feynman 参数化（两个参数 x₁, x₂）是否正确
- 分母中的 `-2x_1x_2 p·k` 的符号（取决于动量流约定）

---

## 4. 真空极化 Π(p²) 的数值系数

**文件**: `renormalization.tex` 第 1399-1404 行

**问题**: 
```latex
\Pi(p^2)=\frac{e^2}{2\pi^2}\int_0^1\dx x(1-x)\ln\frac{m^2-p^2x(1-x)-i\epsilon}{\mu^2}.
```

标准结果为 `2α/π = e²/(2π²)`（其中 α = e²/(4π)），但有些教材会在 Π(p²) 的定义中包含额外的因子。建议确认：
- 文中 Π^{μν} = (p²g^{μν} - p^μ p^ν)Π(p²) 的约定与标准教材一致
- 积分后的闭合形式（第 1403 行）系数正确

**建议对照**: Peskin & Schroeder Eq. (7.90) 或 Schwartz Eq. (19.50)

---

---

## 核查优先级

| 优先级 | 编号 | 影响范围 |
|-------|------|---------|
| 高 | 1. δ_e 系数 | 直接影响反常磁矩等物理预测 |
| ✅ | ~~2. 裸/重整化耦合约定~~ | 已修复，e → e_r |
| 中 | 3. φ³ 三点函数 | 仅影响 φ³ 理论部分 |
| 中 | 4. 真空极化系数 | 影响光子传播子的修正 |
| ✅ | ~~5. Wick 旋转图~~ | 已修复，m→E_p |
| 中 | 6. 有质量矢量场正则动量 | gaugetheory.tex Π^{0i} 符号 |
| 低 | 7. Schwinger-Dyson 展开组合因子 | schwinger-dyson-expansion.tex 对称因子 |
| ✅ | ~~8. Yang-Mills 术语大小写~~ | 已修复 |

---

## 6. 有质量矢量场的正则动量 Π^{0i} 符号

**文件**: `gaugetheory.tex` 第 26-34 行

**当前内容**:
```latex
\Pi^{\mu\nu}=\pa{\mathcal L}{(\partial_\mu A_\nu)}=-F^{\mu\nu}
```
然后第 34 行：`$\Pi^{0i}=E^i$`

**问题**: 若 `Π^{μν} = -F^{μν}`，且 `F^{0i} = ∂^0 A^i - ∂^i A^0`，则 `Π^{0i} = -F^{0i}`。在 (-+++) 度规下，电场 E^i 通常定义为 `E^i = F^{i0}`，与 `F^{0i}` 可能差一个符号。需确认 `Π^{0i}=E^i` 在所选度规约定下是否自洽。

**建议对照**: 与 Proca 方程的矢量场量子化标准推导对照（如 Peskin Ch. 7 或 Schwartz Ch. 8）。

---

## 7. Schwinger-Dyson 展开的组合因子

**文件**: `schwinger-dyson-expansion.tex` 第 31 行

**当前内容**:
```latex
\braket{\phi_1\phi_2}=D_{12}-\left(\frac g2\right)^2\int \d^4x\d^4y
(2D_{1x}D_{xy}D_{xy}D_{y2}+D_{1x}D_{xx}D_{yy}D_{y2}+2D_{1x}D_{xy}D_{yy}D_{x2})
```

**问题**: 三项的系数分别为 2, 1, 2，对应三个二阶 Feynman 图（蝌蚪-蝌蚪串联、8字形、日落图）的组合因子。建议核实这些因子与 φ³ 理论的 Feynman 规则（顶点因子 g/2，对称因子）一致。
