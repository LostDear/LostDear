---
tags:
  - table-retrieval
  - table-overlap-detection
year: "2024"
---
## 来源

> Zecchini, L., Bleifuß, T., Simonini, G., Bergamaschi, S., & Naumann, F. (2024). Determining the Largest Overlap between Tables. In Proceedings of the ACM on Management of Data (Vol. 2, Issue 1, p. 48:1-48:26). https://doi.org/10.1145/3639303
## 摘要
efficiently detect the largest overlap between two tables

## 问题
估计两表的最大重叠

### 设定
1. 表格可能会被复制到不同的web页面
2. 编辑者的表格之间可能存在冲突或重叠

### 难点
1. 表格数据允许行或列的顺序变更
![[Pasted image 20250102193633.png]]

### Definition
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

## Previous Work


## Content
![[Pasted image 20250103140702.png]]
![[Pasted image 20250103141013.png]]
> [!note] 关于Algorithm1的解释
> Seeds：表X和表Y所有可能的单映射对，每一个seed包含M：X->Y的一个映射，以及A：重叠的cell数量。只要两列的重叠数大于1就认定为可能映射（如Function1第6行所示）。而所有的多映射可以认定为多个单映射的组合。FindSeeds函数最终会按照A由大到小排序，返回所有可能的映射对。
> Line 3：正如文中第7页所示，最大重叠的上届由A最小的单映射决定（短板效应）。
> 


**Fig1**
![[Pasted image 20250103140718.png]]
> [!note] 关于Fig1的解释
> （b）是表X到表Y的单映射，及其重叠面积
> （c）单映射的组合，粗体为上界（列数* 最小单映射cell个数），另一个数为下界（最小单映射cell个数）

![[Pasted image 20250103162228.png]]
> [!note] 关于Function2的解释
>min($X_{Seeds},Y_{Seeds}$) 是因为仅允许单向一一映射
>n是当前层级，Seeds已排序好了，所以上界由Seed\[n-1\]决定
  A是重叠上届，当A > $\theta$时，才加入Levels集合

![[Pasted image 20250103162713.png]]


## 候选引用
>[!tip] [[Dataset Discovery in Data Lakes]]
>Alex Bogatu, Alvaro A. A. Fernandes, Norman W. Paton, and Nikolaos Konstantinou. 2020. Dataset Discovery in Data Lakes. In Proceedings of the IEEE International Conference on Data Engineering (ICDE). 709–720. https: //doi.org/10.1109/ICDE48307.2020.00067
