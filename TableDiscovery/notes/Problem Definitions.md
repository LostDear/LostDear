## 标签管理
table-retrieval
- table-overlap-detection
- table-discovery

## Join and Union Search in Table Search

**Definition  (Table Join Search).** Given a set of tables $\mathcal{T} = \{T_{1}, T_{2}, \cdots, T_{N}\}$, a query table $T_{q}$ and a specific column $A_{s}^{q}$ of $T_{q}$, table join search 
aims to find a subset $\mathcal{T}_{q} \subset \mathcal{T}$ that each $T_{i} \in \mathcal{T}_{q}$ and each $T_{j} \in \mathcal{T} \setminus \mathcal{T}_{q}$ satisfy Eq.(1),
$$
\exists A_{u}^{i} \in T_{i}, \forall A_{v}^{j} \in T_{j} \rightarrow S(A_{u}^{i}, A_{s}^{q}) > S(A_{v}^{j}, A_{s}^{q})
$$

**Definition  (Table Union Search).** Given a set of tables $\mathcal{T} = \{T_{1}, T_{2}, \cdots, T_{N}\}$, a query table $T_{q}$, table union search aims to find a subset $\mathcal{T}_{q} \subset \mathcal{T}$ 
that each $T_{i} \in \mathcal{T}_{q}$ and each $T_{j} \in \mathcal{T} \setminus \mathcal{T}_{q}$ satisfy Eq. (2),

$$
S(\text{Schema}(T_{i}), \text{Schema}(T_{q})) > S(\text{Schema}(T_{j}), \text{Schema}(T_{q}))
$$

where $S(\text{Schema}(T_{i}), \text{Schema}(T_{q}))$ is a similarity measure that compares the schemas (i.e., column names, data types) of $T_{i}$ and $T_{q}$.

## Distinctiveness maximization in datasets assemblage

**Definition 1  (Distinctiveness):** Suppose $q(d)$ is the tuple set returned by applying query $q$ to dataset $d$, and $Q(d)$ is the union of the tuple sets returned by each $q \in Q$ on $d$, referred to as: $Q(d) = \bigcup_{q \in Q} q(d)$. The distinctiveness $\mathscr{D}(S, d_u, Q)$ of a set of datasets $S$ is the size of the union of  $Q(d)$ over all $d \in S \cup d_u$. That is: $\mathscr{D}(S, d_u, Q) = \left| \bigcup_{d \in S \cup d_u} Q(d) \right|$.

**Definition 2 (Multi-dataset-query cardinality estimation (MCE))**: Given a set $D$ of datasets and a query set $Q$, $MCE$ estimates the cardinality of $Q$for $D$, which is the size of the  union of $Q(d)$ over each dataset $d ∈ D, i.e$., $∣⋃  d∈D Q(d)∣$

**Definition 3 (Distinctiveness Maximization (DM))**: Given a budget $B$, a query set $Q$, a base dataset $d_u$, a set $D$ of candidate datasets, and a pricing function $p$, the $DM$ problem returns a subset $S^∗ ⊆ D$ that yields the maximum distinctiveness within the budget $B$. Formally, we have$$S^* = \operatorname{argmax}_{S \subseteq D} \mathscr{D}(S, d_u, Q) \;\;\;\; \text{s.t.} \; \sum_{d \in S} p(d) \leq B$$
**Definition 4 (Maximum Coverage (MC))**: Given a universe of elements $V = {e_1, ..., e_n},$ a list of sets$\{S_i^′ ⊆ V \}_i^{m=1}$,(possibly overlapping), and a bound $K < m$, the goal is to find a collection $S$ of sets such that $| U_{S' \in {S}} {S^′}|$ is maximized and $|S| = K$.

>[!note] 以下内容首次出现在Determining the Largest Overlap between Tables

**Definition 2.1 (Attribute Mapping)**. Given two tables $R(X)$ and $S (Y)$, where $X$ and $Y$ denote their schemas ($i.e.$, their attribute sets), an attribute mapping (or simply mapping) between $R(X )$ and $S (Y )$ is defined as a bijective function $M$ that maps a subset of $X$ to a subset of $Y$ :
$$M:X_M \subseteq X \rightarrow Y_M \subseteq Y$$
Due to the bijectivity of the mapping, the attribute sets have the same size $(|X_M | = |Y_M |)$, no attribute in X is mapped to more than one attribute in $Y$ , and no attribute in $Y$ is mapped from more than one attribute in $X$ .

**Definition 2.2 (Table Overlap)**. Given a mapping M, defined between tables $R(X )$ and $S (Y )$ considering the attribute subsets $X_M ⊆ X$ and $Y_M ⊆ Y$ , the table overlap $O_M$ is the bag intersection between the bags of the tuples obtained through the projection of $R(X)$on $XM$ and $S (Y)$on $Y_M$ :
$$O_M = R[X_M] \uplus S[Y_M]$$

**Definition 2.3 (Overlap Area)**. We define the overlap area $A_M$ as the number of cells contained in the overlap $O_M$ :$$A_M = |X_M|*|O_M|$$
where $|X_M|$ and $|O_M|$ represent the width and the height of the rectangle of overlapping cells between the two tables, respectively. We also refer to $A_M$ as the area of mapping M.


**Definition 2.4 (Largest Overlap).** Let $O$ be the set of overlaps determined by all possible mappings between $R(X )$ and $S (Y )$. We define the set of the largest overlaps $O^∗ ⊆ O$ as those overlaps that have the maximum area:
$$O^* = \{  O_{M^*} \in \mathscr{O}  | A_{M^*} \geq A_M, \forall O_M \in O \}$$
We refer to the mappings of $O^∗$ as top mappings, denoted as $M^∗$. Note that the number of top mappings (in most cases just one) is equal to the number of largest overlaps.

$$
\frac{1}{2}
$$
