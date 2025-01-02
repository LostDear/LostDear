---
tags:
  - data-market
---
## Data Markets
### Paper List

| Paper Name                                                           | Year | Link                     |
| -------------------------------------------------------------------- | ---- | ------------------------ |
| visiting online data markets in 2022: A seller and buyer perspective | 2022 | [[#online data markets]] |


### online data markets
>[!quote] visiting online data markets in 2022: A seller and buyer perspective

**Seller Pipeline**
1. Identify Data To Be Sold.
2. Prepare data.  e.g  0->‘male',1-> 'female'
3. Documentation and Schema.
	According to the Arrows’ information paradox [21], buyers do not buy datasets that they do not know help them, while sellers do not release data without a payment.
4. Assign price and license.

**Buyer Pipeline**

1. Identify the need for external data sources.
2. Data Discovery.
3. Investigate potential purchase.

**Transaction**
数据交易有一个谈判的过程，卖家需要向买家说明未被公开的数据集的特征

**文中的调查**
这里选取BQ2,，这个问题对目前Table Discovery的方案有所帮助
>[!quote] Q2: How do you decide if a price is worth it? How do you value a dataset?
> **i)** metadata characteristics: high level dataset statistics included in the listing like titles, descriptions, data samples, identifiable vendor, open license, subscription plan, usage examples;
> **ii)** hidden characteristics: characteristics that only become apparent after negotiation rounds with sellers (such as quality e.g. number of missing values, price, size, update frequency, geographical source, rareness).

>[!note] 
>总结来说就是买家需要先看意向数据集的元数据，然后与卖家沟通未被公开的细节信息。
正如AWS MARKETPLACE上所展示的，数据集会公开Metadata，Schema，Additional Information

>[!hint] Value(Candidate Table) = a \* JoinScore(CandidateTable, QueryTable) + b \* UnionScore(CandidateTable, QueryTable)

![[Pasted image 20241229173326.png]]


## Table Discovery
### Paper List

| Paper Name                           | Year | Link                      | Publisher |
| ------------------------------------ | ---- | ------------------------- | --------- |
| Metam: Goal-Oriented Data Discovery. | 2023 |                           | ICDE      |
| Table union search with preferences  | 2023 | [[#TUS With Preferences]] | VLDB      |
|                                      |      |                           |           |

### TUS With Preferences

这篇论文将TUS和Preference结合，提出了一个Table Union Search with Preferences的问题
Preference包括Skyline、Diversity、Novelty等。

