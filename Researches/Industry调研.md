# CCF-A/B 期刊会议近三年工业界发表论文调研
## 1. Mitigating Load Imbalance in Distributed Data Serving with Rack-Scale Memory Pooling（VMware）
[Mitigating Load Imbalance in Distributed Data Serving with Rack-Scale Memory Pooling | ACM Transactions on Computer Systems](https://dl.acm.org/doi/10.1145/3309986)
- Key-Value stores
- memory pooling technique
- mitigate load imbalance

## 2. Multi-objective Optimization of Data Placement in a Storage-as-a-Service Federated Cloud(AOS 20)
[Multi-objective Optimization of Data Placement in a Storage-as-a-Service Federated Cloud | ACM Transactions on Storage](https://dl.acm.org/doi/10.1145/3452741)
- modeled object placement as a multi-objective optimization problem
- cloud federation
- injection + Repari functions

## 3. PBS: An Efficient Erasure-Coded Block Storage System Based on Speculative Partial Writes(Alibaba with NUDT)
[PBS: An Efficient Erasure-Coded Block Storage System Based on Speculative Partial Writes](https://dl.acm.org/doi/10.1145/3365839)
- PARIX Block Storage(PBS)
- beyound erasure coding(EC)
- small-write-intensive
- speculative partial write scheme(fast small write)

## 4. A3C-DO: A Regional Resource Scheduling Framework Based on Deep Reinforcement Learning in Edge(HUST)
[A3C-DO: A Regional Resource Scheduling Framework Based on Deep Reinforcement Learning in Edge ](https://ieeexplore.ieee.org/document/9066896)
- propose a double offloading framework to simulate
- formulate the offloading as a Markov Decision process
- RL to make offloading decision

## 5.Detection of SLA Violation for Big Data Analytics Applications in Cloud(澳大利亚政府和学校合作 Alibaba dataset)
[Detection of SLA Violation for Big Data Analytics Applications in Cloud](https://ieeexplore.ieee.org/document/9097404)
- SLA violation detection
- predict and prevent SLA violation
- main on **hosted big data analytics applications(BDAAs)**




A[i]
ans[maxn]; // ans[i] 选定p为i的时候，通过变换能得到的非零段的个数
ans[2] // p = 2的时候，通过变换能得到的非零段的个数

target：$max(a[i]),0<=i<=max(A[i])+1$

区间更新:O(1): +x, -x, [x, y]
询问:O(1)

$a_{i-1}<a_i: ans[a_{i-1}+1 : a[i]] + 1$

b[i] = ans[i] - ans[i-1]
b[0] = 0

$ans[I] = \sum(b[i])$

ans[3] = b[0] + b[1] + b[2] + b[3] = ans[0] + ans[1] - ans[0] + ans[2] - ans[1] + ans[3] - ans[2] = ans[3]


b[3] = ans[3] - ans[2]

b[3] = ans[3] - ans[2] + 1

ans[2] = b[0] + b[1] + b[2] // b[3]的变化没有影响到它的前面

ans[3] = ans[2] + b[3] // b[3]的变化影响到了ans[3]

ans[4] = ans[2] + b[3] + b[4] // b[3]的变化影响到了ans[4]

......

ans[N] 




0 0 1 2

0 0 1 2 

0 0 1

ans: [1, 1] : ans[1]++

b[1]++, b[2]--: ans[1]++

0 0 1 2:
ans: [2,2] : ans[2] ++
b[2]++, b[3]--: ans[2]++

ans[1] = 1, ans[2] = 1



0 0 1 2 0 0 1 2




1e9

1e5

0 ~ 1e9

