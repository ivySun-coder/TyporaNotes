# 量子色动力学笔记

## Yang-mills gauge theory by Bassetto等

### 1.4 BRST代数的表示

#### Singlet(单态)和doublet(双重态)

> ![](../../Library/Application Support/typora-user-images/image-20260501113036602.png)
>
> Singlet(单态)和doublet(双重态):
>
> 在 BRST 对称性的框架下，**singlet**（单态）和 **doublet**（双重态/二重态）是指状态空间在 BRST 算符 $Q_B$ 作用下的不可约表示（Irreducible Representations）的分类。
>
> 由于 BRST 算符具有**幂零性（Nilpotency）**，即 $Q_B^2 = 0$，这极大地限制了表示的结构。我们可以从数学和物理两个层面来理解这两个概念：
>
> ### 1. Singlet (单态)
>
> 单态是指仅包含一个状态 $|\psi\rangle$ 的表示，它满足以下条件：
>
> - **被 $Q_B$ 湮灭**：$Q_B |\psi\rangle = 0$。
> - **非平凡性**：它不能表示为另一个状态的 BRST 变换，即不存在 $|\chi\rangle$ 使得 $|\psi\rangle = Q_B |\chi\rangle$。
>
> 在物理上，这对应于 **BRST 上同调（BRST Cohomology）** 的类。根据 Kugo-Ojima 判据，只有单态才对应于**物理态（Physical States）**。它们具有正定的模，且与规范自由度无关。
>
> ### 2. Doublet (双重态)
>
> 双重态是指由两个状态 $\{|u\rangle, |v\rangle\}$ 构成的表示，它们通过 $Q_B$ 相互联系：
>
> - $Q_B |u\rangle = |v\rangle$
> - $Q_B |v\rangle = 0$ （这是 $Q_B^2 = 0$ 的必然结果）
>
> 在物理上，双重态描述的是**非物理自由度**（如鬼场 ghost、反鬼场 anti-ghost 以及纵向极化的规范场）。
>
> - 这类状态通常成对出现，它们的量子数（如能量、动量 $k$）相同，但 ghost 数 $G$ 相差 1。
> - **模的抵消**：在计算散射矩阵（S-matrix）的幺正性时，双重态中的两个状态对物理量的贡献会相互抵消（即所谓的“度规退化”机制），从而保证非物理粒子不会出现在末态中。
>
> ------
>
> ### 为什么只有这两类？
>
> 这完全是由 $Q_B^2 = 0$ 决定的。
>
> - 如果存在一个“三重态” $\{|1\rangle, |2\rangle, |3\rangle\}$ 使得 $Q_B |1\rangle = |2\rangle$ 且 $Q_B |2\rangle = |3\rangle$，那么根据幂零性，$|3\rangle = Q_B^2 |1\rangle$ 必须等于 0。
> - 因此，任何更长的链条都会在第二步断掉，退化回双重态或单态。
>
> 正如您正在研究的量子场论进阶内容（如 LSZ 还原或 BCFW 递归），理解 BRST 荷如何将希尔伯特空间划分为物理区（单态）和非物理区（双重态）是证明理论幺正性的核心步骤。

#### 在BRST代数中，对物理态的定义

> 在BRST代数中，对物理态的定义：
>
> 这是一个非常关键的术语误解，实际上你的理解刚好**记反了**。在数学（上同调理论）和量子场论（BRST 荷）中，定义物理态的标准逻辑是：
>
> **物理态是 Closed（闭的），但不是 Exact（恰当的）。**
>
> 我们可以结合你提供的截图和 BRST 上同调（Cohomology）的定义来澄清这一点：
>
> ### 1. 术语的严格定义
>
> 在 BRST 对称性中，我们有一个算符 $Q_B$，它满足幂零性 $Q_B^2 = 0$。
>
> - **Closed (闭)**：如果一个态 $|\psi\rangle$ 满足 $Q_B |\psi\rangle = 0$，我们称它是 **Closed**。它位于 $Q_B$ 的核（Kernel）中。
> - **Exact (恰当)**：如果一个态 $|\psi\rangle$ 可以写成 $|\psi\rangle = Q_B |\phi\rangle$ 的形式，我们称它是 **Exact**。它位于 $Q_B$ 的像（Image）中。
>
> ### 2. 为什么物理态必须是 "Closed but not Exact"？
>
> 根据 $Q_B^2 = 0$ 的性质，所有的 **Exact** 态必然都是 **Closed** 的（因为 $Q_B(Q_B |\phi\rangle) = 0$）。但反过来不一定成立。
>
> - **为什么要 Closed？**
>
>   BRST 荷 $Q_B$ 生成规范变换。物理态必须在规范变换下是不变的（或者说被规范对称性所选择），所以必须满足 $Q_B |\text{phys}\rangle = 0$。
>
> - **为什么不能是 Exact？**
>
>   如果一个物理态是 Exact 的（即 $|\psi\rangle = Q_B |\phi\rangle$），那么它的**内积（Norm）必然为 0**：
>
>   $$\langle \psi | \psi \rangle = \langle \psi | Q_B |\phi\rangle = \langle Q_B \psi | \phi\rangle = 0$$
>
>   （这里利用了 $Q_B$ 是厄米算符且 $|\psi\rangle$ 是闭态的性质）。在物理上，零模态（Zero-norm states）不具有可观测性，属于非物理的部分。
>
> 因此，真正的物理态定义为 **BRST 上同调类**：
>
> $$H_{BRST} = \frac{\text{Ker} Q_B}{\text{Im} Q_B} = \frac{\text{Closed States}}{\text{Exact States}}$$
>
> 