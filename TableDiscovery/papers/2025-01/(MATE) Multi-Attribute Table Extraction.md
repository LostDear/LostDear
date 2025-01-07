---
tags:
  - table-discovery
  - table-join
year: 2024
---
## 来源


## 摘要


## 问题


###  设定


### 难点


### Definition


## Content
### XHash
1. 对每个字符串编码，对于37种常见字符（字母+数字+空格），每种字符占有一个（分段）segment，segment的长度为$\beta$，每个segment中1的位置表示该字符出现的位置，$\beta满足\arg \mathop{\max}\limits_{\beta}(\beta*37 < |\alpha|)$。
2. 对于一个数据湖，如果其中唯一值的个数为$C_{unique}$，对于长度为$|\alpha|$，且包含a个1的哈希编码，想要表示所有的唯一值，最小的a满足$a = \arg \mathop{\min}\limits_{a}\binom{|\alpha|}{a}$。e.g. 在 $C_{unique} = 700M，|\alpha|=128$时, a = 4。
3. 令$\beta=a-1$，即每个分段的长度为$a-1$，用剩余的$|\alpha| - (37*\beta)$位表示字符串的总长度。
4. 对哈希编码旋转，以减少位冲突。
5. 对于每一行的所有哈希编码做或运算，形成该行的super key。
### Index
该方案的索引沿用了倒排索引方案，使用value作为索引键，对应的值为{$(T_i,R_i,C_i,S_i)$}，即该值出现在哪些表中，同时记录出现位置和该行的super key。

## Previous Work



## 实验结果



## Future
Determining the Largest Overlap between Tables一文中指出该方案难以检测查询表与数据湖中的最大重叠。因为Mate要求用户指定连接键，而问题在于用户并不知道哪些列会产生最大重叠

## 候选引用

