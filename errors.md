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

## 2. QED Lagrangian 中裸耦合与重整化耦合的约定

**文件**: `renormalization.tex` 第 1089 行

**当前内容**（已修正场量记号）:
```latex
\mathcal L=-\frac14F_r^2+\bar\psi_r(i\slashed\partial-m)\psi_r-e\bar\psi_r\slashed A_r\psi_r
-\frac14\delta_A F_r^2+\delta_\psi\bar\psi_r(i\slashed\partial)\psi_r-\delta_m\bar\psi_r\psi_r
-\delta_e\bar\psi_r\slashed A_r\psi_r.
```

**问题**: 这里 e 未加下标 r，暗示是裸耦合常数。但重整化 Lagrangian 通常使用物理耦合 e_r，然后通过 Z_e 关联裸耦合。需确认：
- e 是裸耦合还是物理耦合？
- δ_e 的设定（是否包含 e 的重整化）是否与 δ_A, δ_ψ, δ_m 的变化自洽？

**建议对照**: Peskin & Schroeder Ch. 10 中 QED 重整化的标准约定。

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

## 5. Wick 旋转围道图中的极点位置标注

**文件**: `renormalization.tex` 第 571-574 行

**问题**: Wick 旋转围道图中标注的极点为 `-m + iε/2` 和 `m - iε/2`。对于传播子 `i/(p² - m² + iε)`，p⁰ 复平面上的极点位置应为：
$$p^0 = \pm\sqrt{|\vec{p}|^2 + m^2 - i\epsilon} \approx \pm(E_{\vec{p}} - i\epsilon')$$

图中标注的 `-m + iε/2` 和 `m - iε/2` 是 m 而非 E_p 的近似（忽略了动量），可能在 p=0 特例下成立，但需在正文中说明这是示意性的。

---

## 核查优先级

| 优先级 | 编号 | 影响范围 |
|-------|------|---------|
| 高 | 1. δ_e 系数 | 直接影响反常磁矩等物理预测 |
| 高 | 2. 裸/重整化耦合约定 | 影响整个 QED 重整化方案的自洽性 |
| 中 | 3. φ³ 三点函数 | 仅影响 φ³ 理论部分 |
| 中 | 4. 真空极化系数 | 影响光子传播子的修正 |
| 低 | 5. Wick 旋转图 | 仅示意性，不影响结果 |
