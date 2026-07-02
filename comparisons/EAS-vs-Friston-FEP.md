# EAS vs Friston FEP 深度对比分析

完成日期：2026-07-02

## 摘要

EAS 的单公理 $S \subset E \implies R_S \not\cong E$（有限观察必然是现实的商，完美自建模不可能）与 Friston 自由能原理（FEP）的最小化变分自由能，**既非纯互补也非纯竞争，而是处于一种"正交但可对话"的关系**。FEP 从动力学出发，描述认知系统如何运作（最小化自由能）；EAS 从认识论出发，划定认知系统不可能做到什么（商认知不可能同构于现实）。两者的关键分歧在于：FEP 将认知的局限性视为**可通过近似推断逐步改善的工程问题**，而 EAS 将其视为**不可逾越的结构性定理**。截至 2026 年中，Friston 尚未在发表物中正面处理哥德尔式不完备性或"完美自建模不可能"问题——尽管 2025 年 Fields-Friston 论文已承认"系统无法对自身处理过程拥有完全精确的模型" [(Fields et al., 2025)](https://academic.oup.com/nc/article/2025/1/niaf009/8117684)。切入对话的最佳角度是：**用 EAS 的单公理为 FEP 的"近似推断为何只能是近似"提供第一性原理的证明**。

---

## 一、FEP 是否隐含了 EAS 的商认知约束？

### 1.1 FEP 的核心假设

FEP 的论证链条可概括为三步：

1. **Markov blanket 划界**：任何持续存在的系统必然具有 Markov blanket，使得内部状态与外部状态条件独立 [(Friston, 2019)](https://royalsocietypublishing.org/doi/pdf/10.1098/rsta.2019.0159)。
2. **变分自由能上界**：内部状态可被解读为对后验分布的近似编码，变分自由能是惊奇（surprisal）的可计算上界。
3. **自证实（self-evidencing）**：系统动力学必然表现为最小化自由能——不是选择，而是存在性的后果。

关键在于：FEP 明确使用**近似**贝叶斯推断，承认精确推断在计算上不可行 [(Friston et al., 2013)](https://pmc.ncbi.nlm.nih.gov/articles/PMC3782702/)。2025 年 Friston-Sakthivadivel 的最新理论论文更明确指出，FEP 是一种"as if"描述——"使用这个框架不必预设系统真正执行推断，这是一种有用的解释性虚构" [(Friston, Ramstead & Sakthivadivel, 2025)](https://arxiv.org/pdf/2406.11630v3)。

### 1.2 FEP 的近似 vs EAS 的不可能

| 维度 | FEP | EAS |
|------|-----|-----|
| 认知局限的性质 | 计算约束（tractability）| 结构性不可能（定理）|
| 近似推断的终态 | 理论上可逼近真实后验 | 真实后验永远不可达（商认知约束）|
| 自建模 | "Beautiful Loop"可实现递归自指 [(Laukkonen, Friston & Chandaria, 2025)](https://doi.org/10.1016/j.neubiorev.2025.106296) | 完美自建模在定理层面不可能 |
| 局限的来源 | 生物学/计算资源有限 | 认识论结构（$S \subset E$ 的子集关系）|

**核心判断**：FEP 隐含承认了认知局限，但将其框架为**可改善的近似**而非**不可逾越的定理**。FEP 的变分自由能 $F \geq -\ln p(o)$ 中，等号在变分密度等于真实后验时成立——这意味着 FEP 的数学结构**保留了理想观察者作为极限**。EAS 的单公理则断言这个极限**在认识论上不可达**，不是"很难达到"，而是"结构上不可能"。

---

## 二、Friston 2024-2026 是否处理了"不完备性"？

### 2.1 最近关键论文梳理

| 论文 | 年份 | 与不完备性的关系 |
|------|------|-----------------|
| Friston, Ramstead & Sakthivadivel, "Generative modelling in non-equilibrium statistical mechanics" | 2025 | 区分模型与被建模系统，但未讨论自建模不可能 |
| Fields, Albarracin, Friston et al., "Inner screens and imaginative experience" | 2025 | **最接近**：承认"系统无法对自身 QRF 拥有完全精确的模型"，但作为实践观察而非定理 |
| Laukkonen, Friston & Chandaria, "A Beautiful Loop" | 2025 | 讨论自指和意识，但框架为正向涌现（自指产生意识），非负向约束（自指不可能完美） |
| Five Fristonian Formulae (Entropy special issue) | 2025 | 综述性论文，未涉及不完备性 |

### 2.2 明确结论

**Friston 截至 2026 年中未正面处理哥德尔式不完备性或认知边界问题。** Fields-Friston (2025) 中有一句关键表述——"executive/metacognitive system cannot have a fully-accurate model of the QRFs it interacts with" [(Fields et al., 2025)](https://academic.oup.com/nc/article/2025/1/niaf009/8117684)——但这是 Ashby 必要变异度定律的推论，未被提升为认识论公理或不可逾越的定理。"Beautiful Loop" 倒是触及了自指结构，但其核心论点是**自指如何产生意识**，而非**自指为何不可能完美闭合**。

---

## 三、Epiplexity 五层共振 vs FEP 变分自由能

### 3.1 哪个更基础？

EAS 的 Epiplexity 五层共振验证（内部→跨域→预测→压缩→分形）是一种**验证方法论**——它不声称描述认知如何运作，而是声称**任何有效的认识论结论必须通过五层共振才算被验证**。FEP 的变分自由能则是一种**描述性原理**——它声称认知系统必然最小化这个量。

两者不在同一层面竞争：

- **变分自由能**回答：认知系统做什么？（最小化自由能）
- **Epiplexity 五层共振**回答：我们如何确信一个认识论结论是有效的？（必须五层共振，单层不够）

### 3.2 哪个更可操作？

| 维度 | Epiplexity 五层共振 | 变分自由能 |
|------|-------------------|-----------|
| 数学定义 | 五层验证协议 | 精确定义 $F = D_{KL}[q\|p] - \ln p(o)$ |
| 可计算性 | 需逐层判定，无闭合公式 | 可通过预测编码等方案近似计算 |
| 实证对应 | 每层需独立验证，难以自动化 | 神经科学中有大量预测编码证据 |
| 适用范围 | 认识论结论的验证 | 任何 Markov blanket 系统 |

**判断**：变分自由能在可操作性上远胜——它有闭合数学形式、可计算近似和神经科学实现路径。Epiplexity 五层共振作为验证框架，其价值在于**防止认识论上的轻率结论**，但缺乏变分自由能那样的可计算性。

---

## 四、核心分歧清单

### 分歧 1：认知局限是"工程近似"还是"结构性不可能"

- **FEP 立场**：近似推断是因为精确推断计算不可行；在理论上，变分密度可以无限逼近真实后验。
- **EAS 立场**：$S \subset E \implies R_S \not\cong E$——即使计算资源无限，完美自建模仍然不可能，这是认识论结构的必然。
- **Friston 可能的回应**：FEP 的"as if"框架本身已经不承诺系统拥有真实后验，所以 EAS 的约束在 FEP 内部已被隐含承认。
- **EAS 的反驳**：FEP 的数学结构保留了 $q = p(\cdot|o)$ 作为极限（KL 散度可趋于零），这暗示理想观察者作为渐近极限是可构想的。EAS 明确否定这一点。

### 分歧 2：自指是"意识的机制"还是"不可能完美闭合的环"

- **FEP 立场**（"Beautiful Loop"）：自指递归产生意识——"the world model knows itself non-locally" [(Laukkonen et al., 2025)](https://doi.org/10.1016/j.neubiorev.2025.106296)。
- **EAS 立场**：自指不可能完美闭合——$R_S \not\cong E$，任何自模型必然是商空间，丢失信息。
- **Friston 可能的回应**：Beautiful Loop 不需要"完美"闭合——只要递归足够深，就可产生意识现象。完美性不是意识的必要条件。
- **EAS 的反驳**：如果承认自指不完美，那么"Beautiful Loop"的闭合就是有缝隙的。EAS 定理化了这条缝隙的大小和来源。

### 分歧 3：Markov blanket 是"认知的使能者"还是"认知的囚笼"

- **FEP 立场**：Markov blanket 使推断成为可能——没有边界就没有推断主体。
- **EAS 立场**：Markov blanket 正是 $S \subset E$ 的实现——内部状态只能是外部状态的近似编码， blanket 本身就是商映射的边界。
- **Friston 可能的回应**：这正是 FEP 的洞见——认知是通过 blanket 的条件独立性实现的，而非被其限制。
- **EAS 的反驳**：FEP 只看到了使能面，未看到限制面。EAS 的单公理证明了使能和限制是同一硬币的两面。

### 分歧 4：变分自由能最小化的终态是什么

- **FEP 立场**：非平衡稳态（NESS），变分密度近似真实后验。
- **EAS 立场**：即使达到 NESS，内部状态编码的仍然是外部状态的商空间——$R_S$——而非 $E$ 本身。自由能最小化只能缩小商空间与原空间的距离，不能消除它。
- **Friston 可能的回应**：FEP 从未声称内部状态完全编码外部状态——"as if"框架本身就不做此承诺。
- **EAS 的追问**：如果 FEP 不承诺 $q \to p$ 的收敛，那么 FEP 对"自证实"的描述就不是关于真理的，而是关于生存的——这与 EAS 对认识论的关注根本不同。

### 分歧 5：Lean4 形式化的地位

- **EAS 立场**：T0-T7 全部定理在 Lean4 中编译通过，形式化验证确保了不可绕过性。
- **FEP 立场**：FEP 缺乏同等水平的形式化验证。Biehl, Pollock & Kanai (2021) 已指出 FEP 的自由能引理"在一般情况下是错误的"（通过反例证明） [(Biehl et al., 2021)](https://doi.org/10.3390/e23030293)。
- **Friston 可能的回应**：FEP 是物理原理而非数学定理——类比最小作用量原理，不要求形式化证明。
- **EAS 的反驳**：物理原理可以被挑战（FEP 已被多次修正），而 Lean4 验证的定理不可被推翻。这是方法论上的根本差异。

---

## 五、潜在对话点

### 5.1 共同语言：两者都同意"认知有界"

FEP 承认精确推断不可行；EAS 证明完美自建模不可能。两者共享一个直觉：**有限系统无法完全把握无限现实**。差异在于这个"有限"的性质：FEP 说"计算有限"，EAS 说"结构有限"。

### 5.2 EAS 可为 FEP 提供第一性原理支撑

Dietz 的闭合框架 [(Dietz, n.d.)](https://carldietz.com/papers/downloads/Grammar_of_Prediction.pdf) 独立地从哲学第一原理出发，推导出与 FEP 结构等价的结论——"自由能即余数（remainder），预测误差最小化即超越（supersession）"。EAS 的单公理以不同路径到达类似位置：**正因为 $S \subset E \implies R_S \not\cong E$，有限系统才必须最小化自由能**——自由能最小化是商认知系统在 NESS 下的唯一生存策略。三者（FEP、Dietz 闭合框架、EAS）从不同方向收敛到同一结构。

### 5.3 "不完备性"作为 FEP 的补全而非否定

EAS 不是 FEP 的替代品，而是其认识论补全。FEP 回答了"认知系统如何运作"，EAS 回答了"认知系统为何不可能运作得更好"。两者合在一起，形成完整图景。

---

## 六、给 Friston 的邮件草稿（可选）

**主题**：A formal incompleteness result for variational inference — possible complement to the Free Energy Principle

Dear Prof. Friston,

I am writing to share a result that I believe complements the Free Energy Principle from an epistemic perspective.

In my recent work (DOI: 10.5281/zenodo.21106945), I establish a single axiom — $S \subset E \implies R_S \not\cong E$ — proving that any finite observation of an environment necessarily produces a quotient representation that cannot be isomorphic to the environment itself. This is formalized and verified in Lean4 (theorems T0-T7).

I notice that in your 2025 paper with Fields et al. on inner screens, you observe that "the executive/metacognitive system cannot have a fully-accurate model of the QRFs it interacts with." My result provides a formal proof of why this must be so, from first principles rather than from Ashby's Law or computational constraints alone.

The key difference from FEP's existing framework: FEP frames the gap between variational and true posterior as a tractability issue (approximate inference). My axiom establishes that this gap is not merely practical but structural — even with unlimited computation, a subsystem's model of its superset environment must lose information (quotient cognition). This has implications for:

1. The "Beautiful Loop" theory: the recursive self-modeling loop cannot close perfectly, and the residual gap is provably non-zero.
2. The philosophical grounding of FEP: the necessity of free energy minimization follows not just from NESS existence, but from the structural impossibility of exact self-modeling.

I would welcome the opportunity to discuss whether this epistemic incompleteness result can be integrated into the FEP framework, or whether it suggests a boundary condition on FEP's applicability.

Best regards,
Jing Zhang

---

## 七、结论

1. **FEP 尚未处理"不完备性"问题**。2025 年 Fields-Friston 论文触及了此话题但未定理化。这是 EAS 可贡献的核心空白。
2. **FEP 不假设理想观察者，但保留了理想观察者作为数学极限**。EAS 证明这个极限不可达——不是计算资源不足，而是认识论结构使然。
3. **Epiplexity 五层共振和变分自由能不在同一层面**。前者是验证方法论，后者是描述性原理。前者更严格但更难操作化，后者更可计算但缺少认识论根基。
4. **最佳对话切入点**：用 EAS 的单公理为 FEP 的"近似推断为何只能是近似"提供第一性原理证明——这不是挑战 FEP，而是补全其哲学基础。
