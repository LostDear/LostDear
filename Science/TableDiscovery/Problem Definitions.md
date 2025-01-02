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






