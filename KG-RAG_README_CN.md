# KG-RAG 论文整理（2025-2026）

本仓库用于整理 2025-2026 年各大顶会中与 **KG-RAG（Knowledge Graph Retrieval-Augmented Generation，知识图谱增强检索生成）** 和 **GraphRAG（图结构增强检索生成）** 相关的论文。

这里的 KG-RAG 范围包括：

- 显式使用知识图谱（Knowledge Graph, KG）的 RAG；
- 使用实体、关系、三元组、路径、子图进行检索增强的 RAG；
- 面向 KGQA（Knowledge Graph Question Answering）的 RAG；
- 使用图结构进行文档组织、证据检索、多跳推理或智能体决策的 GraphRAG。

---

## 目录

- [2025 年论文](#2025-年论文)
- [2026 年论文](#2026-年论文)
- [推荐阅读路线](#推荐阅读路线)
- [研究趋势总结](#研究趋势总结)
- [适合继续深入的研究方向](#适合继续深入的研究方向)

---

# 2025 年论文

## 1. KG²RAG: Knowledge Graph-Guided Retrieval Augmented Generation

- **会议/年份：** NAACL 2025
- **论文链接：** [Knowledge Graph-Guided Retrieval Augmented Generation](https://aclanthology.org/2025.naacl-long.449/)
- **PDF：** [ACL Anthology PDF](https://aclanthology.org/2025.naacl-long.449.pdf)
- **代码：** [GitHub](https://github.com/nju-websoft/KG2RAG)
- **关键词：** KG-guided retrieval, chunk expansion, chunk organization, multi-hop QA

**论文总结：**  
KG²RAG 是一篇非常典型的 KG-RAG 论文。传统 RAG 通常只依靠语义相似度检索文本 chunk，这会导致检索结果之间缺乏结构联系，尤其在多跳问答中容易出现证据不完整、上下文碎片化的问题。KG²RAG 的核心思想是：先通过普通语义检索得到 seed chunks，然后利用知识图谱中 chunk 之间的事实级关系进行扩展和组织，从而得到更连贯、更完整的上下文。

**值得关注的点：**

- 把 KG 用在普通向量检索之后，而不是完全替代向量检索；
- 利用 KG 做 chunk expansion，提升多跳问答中的证据覆盖率；
- 利用 KG 做 chunk organization，让最终输入 LLM 的上下文更有逻辑顺序。

---

## 2. SubgraphRAG: Simple is Effective

- **会议/年份：** ICLR 2025
- **论文链接：** [Simple is Effective: The Roles of Graphs and Large Language Models in Knowledge-Graph-Based Retrieval-Augmented Generation](https://openreview.net/forum?id=2NbxnNI94F)
- **arXiv：** [arXiv:2410.20724](https://arxiv.org/abs/2410.20724)
- **代码：** [GitHub](https://github.com/Graph-COM/SubgraphRAG)
- **关键词：** KG-based RAG, subgraph retrieval, KGQA, LLM reasoning

**论文总结：**  
SubgraphRAG 主要研究在 KG-based RAG 中，图结构和大语言模型分别起什么作用。它不是简单地把所有相关三元组塞给 LLM，而是从知识图谱中检索与问题相关的子图，再让 LLM 基于子图进行推理。论文强调：如果子图检索足够准确，即使使用相对简单的模型，也能在 KGQA 任务上取得不错效果。

**值得关注的点：**

- 把 KG-RAG 的检索单位从文本 chunk 转为 KG 子图；
- 分析图结构与 LLM 推理能力之间的关系；
- 适合用来理解“为什么 KG-RAG 不只是普通 RAG 加一个图”。

---

## 3. K-RagRec: Knowledge Graph Retrieval-Augmented Generation for LLM-based Recommendation

- **会议/年份：** ACL 2025
- **论文链接：** [Knowledge Graph Retrieval-Augmented Generation for LLM-based Recommendation](https://aclanthology.org/2025.acl-long.1317/)
- **PDF：** [ACL Anthology PDF](https://aclanthology.org/2025.acl-long.1317.pdf)
- **arXiv：** [arXiv:2501.02226](https://arxiv.org/abs/2501.02226)
- **代码：** [GitHub](https://github.com/Sjay-Wang/K-ragrec)
- **关键词：** KG-RAG, recommendation, LLM-based recommender system, structured retrieval

**论文总结：**  
K-RagRec 将 KG-RAG 用在推荐系统中。传统 LLM 推荐系统容易出现幻觉、缺少用户和物品之间的结构化关系理解等问题。该论文通过引入外部知识图谱，为 LLM 提供用户、物品、属性和关系等结构化信息，从而提高推荐结果的准确性和可解释性。

**值得关注的点：**

- KG-RAG 不只适用于问答，也可以用于推荐系统；
- KG 可以为 LLM 推荐提供结构化背景知识；
- 适合研究“知识图谱 + 推荐 + 大模型”的交叉方向。

---

## 4. MedGraphRAG: Medical Graph RAG

- **会议/年份：** ACL 2025
- **论文链接：** [Medical Graph RAG: Evidence-based Medical Large Language Model via Graph Retrieval-Augmented Generation](https://aclanthology.org/2025.acl-long.1381/)
- **PDF：** [ACL Anthology PDF](https://aclanthology.org/2025.acl-long.1381.pdf)
- **arXiv：** [arXiv:2408.04187](https://arxiv.org/abs/2408.04187)
- **代码：** [GitHub](https://github.com/MedicineToken/Medical-Graph-RAG)
- **关键词：** medical RAG, GraphRAG, evidence-based generation, medical QA

**论文总结：**  
MedGraphRAG 是医疗领域的 GraphRAG 框架。它通过构建医学图结构，把用户文档、医学知识源和医学术语体系连接起来，使 LLM 在回答医学问题时能够检索到更可信、更有证据支撑的内容。论文还设计了 U-Retrieval 机制，将精确检索和响应细化结合起来。

**值得关注的点：**

- KG-RAG 在高风险领域中的典型应用；
- 强调 evidence-based generation，即基于证据的生成；
- 适合研究医学问答、可信 RAG、专业领域 RAG。

---

## 5. D-RAG: Differentiable Retrieval-Augmented Generation for Knowledge Graph Question Answering

- **会议/年份：** EMNLP 2025
- **论文链接：** [D-RAG: Differentiable Retrieval-Augmented Generation for Knowledge Graph Question Answering](https://aclanthology.org/2025.emnlp-main.1793/)
- **PDF：** [ACL Anthology PDF](https://aclanthology.org/2025.emnlp-main.1793.pdf)
- **关键词：** KGQA, differentiable retrieval, GNN retriever, end-to-end training

**论文总结：**  
D-RAG 关注 KGQA 中的一个重要问题：很多 KG-RAG 方法的检索过程是不可微的，检索器和生成器很难端到端联合优化。该论文提出一个可微分的 RAG 框架，使用 GNN 对知识图谱进行编码和检索，并与 LLM 生成模块结合，从而让图检索和答案生成能够更紧密地协同。

**值得关注的点：**

- 从 pipeline 式 KG-RAG 走向可训练的 KG-RAG；
- 使用 GNN 作为图检索器；
- 适合研究“图神经网络 + RAG + KGQA”。

---

## 6. BYOKG-RAG: Multi-Strategy Graph Retrieval for Knowledge Graph Question Answering

- **会议/年份：** EMNLP 2025
- **论文链接：** [BYOKG-RAG: Multi-Strategy Graph Retrieval for Knowledge Graph Question Answering](https://aclanthology.org/2025.emnlp-main.1417/)
- **PDF：** [ACL Anthology PDF](https://aclanthology.org/2025.emnlp-main.1417.pdf)
- **arXiv：** [arXiv:2507.04127](https://arxiv.org/abs/2507.04127)
- **代码：** [GraphRAG Toolkit](https://github.com/awslabs/graphrag-toolkit)
- **关键词：** KGQA, multi-strategy retrieval, OpenCypher, custom KG

**论文总结：**  
BYOKG-RAG 面向 “Bring Your Own Knowledge Graph” 场景，也就是用户有自己的知识图谱。现实中的 KG 往往 schema 不统一、实体链接困难、结构差异很大。该论文结合 LLM 和多种图检索工具，让 LLM 生成问题实体、候选答案、推理路径和 OpenCypher 查询，再通过图工具检索相关上下文，最后生成答案。

**值得关注的点：**

- 面向真实场景中的自定义 KG；
- 结合 LLM 生成图查询和图检索工具；
- 对企业知识图谱、私有知识库问答有参考价值。

---

## 7. KG-RAG: Enhancing GUI Agent Decision-Making via Knowledge Graph-Driven Retrieval-Augmented Generation

- **会议/年份：** EMNLP 2025
- **论文链接：** [KG-RAG: Enhancing GUI Agent Decision-Making via Knowledge Graph-Driven Retrieval-Augmented Generation](https://aclanthology.org/2025.emnlp-main.274/)
- **PDF：** [ACL Anthology PDF](https://aclanthology.org/2025.emnlp-main.274.pdf)
- **arXiv：** [arXiv:2509.00366](https://arxiv.org/abs/2509.00366)
- **代码：** [GitHub](https://github.com/zhaoyuzhi/KG-RAG-GUI-Agent)
- **关键词：** GUI agent, UI transition graph, mobile agent, KG-RAG

**论文总结：**  
这篇论文将 KG-RAG 用在 GUI Agent 决策中。它把移动应用中的 UI 跳转关系转化为结构化知识，并通过 KG 驱动的检索方式帮助智能体选择下一步操作。相比只依赖当前屏幕截图或历史轨迹，KG-RAG 可以提供更明确的导航路径和任务上下文。

**值得关注的点：**

- KG-RAG 与智能体结合的代表性应用；
- 将 UI 转移图转化为可检索知识；
- 适合研究 Agent、GUI automation、任务规划方向。

---

## 8. KERAG: Knowledge-Enhanced Retrieval-Augmented Generation for Advanced Question Answering

- **会议/年份：** Findings of EMNLP 2025
- **论文链接：** [KERAG: Knowledge-Enhanced Retrieval-Augmented Generation for Advanced Question Answering](https://aclanthology.org/2025.findings-emnlp.329/)
- **PDF：** [ACL Anthology PDF](https://aclanthology.org/2025.findings-emnlp.329.pdf)
- **arXiv：** [arXiv:2509.04716](https://arxiv.org/abs/2509.04716)
- **关键词：** KG-based RAG, subgraph retrieval, filtering, summarization, QA

**论文总结：**  
KERAG 是一个完整的知识增强 RAG 框架。它首先从 KG 中检索较大的相关子图，然后对检索到的图结构进行过滤和总结，最后让 LLM 基于这些结构化知识进行推理和回答。它的重点不是单纯扩大检索范围，而是在扩大覆盖的同时控制噪声。

**值得关注的点：**

- 包含“子图检索—过滤—总结—生成”的完整流程；
- 适合复杂问答任务；
- 对研究 KG-RAG 中的噪声过滤很有参考价值。

---

## 9. LightRAG: Simple and Fast Retrieval-Augmented Generation

- **会议/年份：** Findings of EMNLP 2025
- **论文链接：** [LightRAG: Simple and Fast Retrieval-Augmented Generation](https://aclanthology.org/2025.findings-emnlp.568/)
- **PDF：** [ACL Anthology PDF](https://aclanthology.org/2025.findings-emnlp.568.pdf)
- **arXiv：** [arXiv:2410.05779](https://arxiv.org/abs/2410.05779)
- **代码：** [GitHub](https://github.com/HKUDS/LightRAG)
- **项目主页：** [LightRAG Project Page](https://lightrag.github.io/)
- **关键词：** GraphRAG, lightweight retrieval, entity-relation indexing, efficient RAG

**论文总结：**  
LightRAG 是一个轻量级 GraphRAG 框架。它通过实体和关系级别的索引，将文本中的结构化信息组织成图结构，从而同时支持低层实体信息和高层关系信息的检索。相比复杂的 GraphRAG 系统，它更强调简单、快速、实用。

**值得关注的点：**

- 工程实用性强；
- 适合个人复现和二次开发；
- 可以作为 KG-RAG/GraphRAG 项目的 baseline。

---

## 10. GFM-RAG: Graph Foundation Model for Retrieval Augmented Generation

- **会议/年份：** NeurIPS 2025
- **论文链接：** [NeurIPS Proceedings PDF](https://proceedings.neurips.cc/paper_files/paper/2025/file/33ca0b1102b54c191a9a45a05adafaf4-Paper-Conference.pdf)
- **arXiv：** [arXiv:2502.01113](https://arxiv.org/abs/2502.01113)
- **代码：** [GitHub](https://github.com/RManLuo/gfm-rag)
- **关键词：** Graph foundation model, GraphRAG, multi-hop QA, graph retrieval

**论文总结：**  
GFM-RAG 将 Graph Foundation Model 引入 RAG。它希望通过图基础模型学习图结构中的通用推理能力，并将这种能力迁移到不同知识图谱和问答任务中。相比只针对单一 KG 设计检索器，这篇论文更关注跨图泛化能力。

**值得关注的点：**

- 图基础模型与 RAG 的结合；
- 关注跨知识图谱泛化；
- 适合研究图模型、图预训练、GraphRAG 泛化能力。

---

## 11. HyperGraphRAG: Retrieval-Augmented Generation via Hypergraph-Structured Knowledge Representation

- **会议/年份：** NeurIPS 2025
- **论文链接：** [NeurIPS Proceedings](https://proceedings.neurips.cc/paper_files/paper/2025/hash/df55ee6e59f8ac4a625219e11fe9ddba-Abstract-Conference.html)
- **PDF：** [NeurIPS PDF](https://proceedings.neurips.cc/paper_files/paper/2025/file/df55ee6e59f8ac4a625219e11fe9ddba-Paper-Conference.pdf)
- **arXiv：** [arXiv:2503.21322](https://arxiv.org/abs/2503.21322)
- **代码：** [GitHub](https://github.com/LHRLAB/HyperGraphRAG)
- **关键词：** Hypergraph, GraphRAG, n-ary relations, knowledge representation

**论文总结：**  
HyperGraphRAG 认为普通图结构只能自然表示二元关系，而现实知识中经常存在多元关系。该论文使用超图来表示复杂事实，一个超边可以连接多个实体，从而比普通三元组结构表达更丰富的语义关系。

**值得关注的点：**

- 用超图增强 GraphRAG 的知识表达能力；
- 适合多实体、多关系、多条件事实；
- 对复杂知识建模和多跳推理有参考价值。

---

## 12. LEGO-GraphRAG: Modularizing Graph-based Retrieval-Augmented Generation for Design Space Exploration

- **会议/年份：** VLDB 2025 / PVLDB
- **论文链接：** [ACM DL](https://dl.acm.org/doi/10.14778/3748191.3748194)
- **PDF：** [PVLDB PDF](https://www.vldb.org/pvldb/vol18/p3269-cao.pdf)
- **arXiv：** [arXiv:2411.05844](https://arxiv.org/abs/2411.05844)
- **代码：** [GitHub](https://github.com/gzy02/LEGO-GraphRAG)
- **关键词：** GraphRAG framework, modular RAG, design space, system evaluation

**论文总结：**  
LEGO-GraphRAG 从系统角度对 GraphRAG 进行模块化拆解。它将 GraphRAG 拆成图构建、图检索、上下文组织、生成等模块，并分析不同模块选择对性能、成本和效率的影响。

**值得关注的点：**

- 适合系统性理解 GraphRAG；
- 可以帮助设计实验对比；
- 适合写综述、搭建框架或做系统优化。

---

# 2026 年论文

## 13. PathRAG: Pruning Graph-based Retrieval Augmented Generation with Relational Paths

- **会议/年份：** AAAI 2026
- **论文链接：** [AAAI OJS](https://ojs.aaai.org/index.php/AAAI/article/view/40268)
- **PDF：** [AAAI PDF](https://ojs.aaai.org/index.php/AAAI/article/view/40268/44229)
- **arXiv：** [arXiv:2502.14902](https://arxiv.org/abs/2502.14902)
- **代码：** [GitHub](https://github.com/BUPT-GAMMA/PathRAG)
- **关键词：** GraphRAG, path retrieval, path pruning, relation path prompting

**论文总结：**  
PathRAG 关注 GraphRAG 中的冗余检索问题。很多 GraphRAG 方法会检索大量实体、边和文本，导致上下文变长、噪声变多。PathRAG 的核心思想是从图中选择关键关系路径，并将这些路径转化为适合 LLM 理解的提示，从而减少无关信息。

**值得关注的点：**

- 把检索重点放在 relation path，而不是大规模子图；
- 适合研究 KG-RAG 的效率优化；
- 对路径剪枝、噪声过滤、多跳推理都有参考价值。

---

## 14. LogicRAG: You Don't Need Pre-Built Graphs for RAG

- **会议/年份：** AAAI 2026
- **论文链接：** [AAAI PDF](https://ojs.aaai.org/index.php/AAAI/article/view/40278/44239)
- **arXiv：** [arXiv:2508.06105](https://arxiv.org/abs/2508.06105)
- **代码：** [GitHub](https://github.com/chensyCN/LogicRAG)
- **关键词：** dynamic graph, adaptive reasoning structure, DAG, graph-free GraphRAG

**论文总结：**  
LogicRAG 研究一个很现实的问题：如果没有提前构建好的 KG，还能不能获得图结构对 RAG 的帮助？它通过在推理时动态分解问题，并构建 DAG 形式的自适应推理结构，让检索过程跟随问题逻辑展开。

**值得关注的点：**

- 不依赖预构建 KG；
- 在推理时动态构建 reasoning structure；
- 适合开放域问答和没有现成知识图谱的场景。

---

## 15. LeanRAG: Knowledge-Graph-Based Generation with Semantic Aggregation and Hierarchical Retrieval

- **会议/年份：** AAAI 2026
- **论文链接：** [AAAI PDF](https://ojs.aaai.org/index.php/AAAI/article/view/40789/44750)
- **arXiv：** [arXiv:2508.10391](https://arxiv.org/abs/2508.10391)
- **代码：** [GitHub](https://github.com/RaZzzyz/LeanRAG)
- **关键词：** hierarchical KG, semantic aggregation, structure-guided retrieval, redundancy reduction

**论文总结：**  
LeanRAG 通过语义聚合构建层次化知识图谱，并利用分层检索来降低冗余。相比直接在大图中检索，它先组织高层语义摘要和结构关系，再从高层到低层逐步定位相关证据。

**值得关注的点：**

- 通过层次化图结构减少检索冗余；
- 适合长文档、多文档场景；
- 对高效 KG-RAG 有较大参考价值。

---

## 16. TAdaRAG: Task Adaptive Retrieval-Augmented Generation via On-the-Fly Knowledge Graph Construction

- **会议/年份：** AAAI 2026
- **论文链接：** [AAAI OJS](https://ojs.aaai.org/index.php/AAAI/article/view/40774)
- **PDF：** [AAAI PDF](https://ojs.aaai.org/index.php/AAAI/article/view/40774/44735)
- **arXiv：** [arXiv:2511.12520](https://arxiv.org/abs/2511.12520)
- **关键词：** on-the-fly KG construction, task-adaptive RAG, intent routing, knowledge extraction

**论文总结：**  
TAdaRAG 提出根据当前任务动态构建知识图谱。它不是依赖固定 KG，而是根据任务意图从外部知识源中抽取实体关系，构造任务相关的临时 KG，再用于检索和生成。

**值得关注的点：**

- 动态 KG 构建；
- 根据任务自适应选择知识；
- 适合开放域 KG-RAG 和文档级 KG-RAG。

---

## 17. Privacy-protected Retrieval-Augmented Generation for Knowledge Graph Question Answering

- **会议/年份：** AAAI 2026
- **论文链接：** [AAAI OJS](https://ojs.aaai.org/index.php/AAAI/article/view/40534)
- **PDF：** [AAAI PDF](https://ojs.aaai.org/index.php/AAAI/article/view/40534/44495)
- **arXiv：** [arXiv:2508.08785](https://arxiv.org/abs/2508.08785)
- **代码：** [GitHub](https://github.com/NLPGM/ARoG)
- **关键词：** privacy-preserving KG-RAG, anonymous KG, KGQA, abstraction reasoning

**论文总结：**  
这篇论文关注私有知识图谱上的隐私保护 KG-RAG。它提出 ARoG 方法，在隐藏实体语义的同时，仍然允许模型通过关系和图结构进行检索与推理。也就是说，它试图让 LLM 在不知道敏感实体真实含义的情况下完成 KGQA。

**值得关注的点：**

- 面向私有 KG 和企业知识库；
- 关注 KG-RAG 中的隐私泄露风险；
- 适合研究安全 RAG、隐私保护 RAG。

---

## 18. When to Use Graphs in RAG

- **会议/年份：** ICLR 2026
- **论文链接：** [OpenReview](https://openreview.net/forum?id=i9q9xDMjG7)
- **arXiv：** [arXiv:2506.05690](https://arxiv.org/abs/2506.05690)
- **代码/Benchmark：** [GitHub](https://github.com/GraphRAG-Bench/GraphRAG-Benchmark)
- **关键词：** GraphRAG benchmark, evaluation, when GraphRAG helps, RAG vs GraphRAG

**论文总结：**  
这篇论文讨论一个非常关键的问题：什么时候应该使用 GraphRAG？并不是所有任务都需要图结构，有些任务普通 RAG 已经足够。论文构建了 GraphRAG-Bench，从事实检索、复杂推理、上下文总结、创造性生成等多个任务分析 GraphRAG 的优势和局限。

**值得关注的点：**

- 适合判断 KG-RAG 是否真的有必要；
- 有助于做 KG-RAG 综述和实验设计；
- 能帮助避免“为了用图而用图”。

---

## 19. LinearRAG: Linear Graph Retrieval Augmented Generation on Large-scale Corpora

- **会议/年份：** ICLR 2026
- **论文链接：** [OpenReview](https://openreview.net/forum?id=mCtfkypdm6)
- **arXiv：** [arXiv:2510.10114](https://arxiv.org/abs/2510.10114)
- **代码：** [GitHub](https://github.com/DEEP-PolyU/LinearRAG)
- **关键词：** scalable GraphRAG, relation-free graph, Tri-Graph, large-scale corpus

**论文总结：**  
LinearRAG 关注大规模语料上的 GraphRAG 效率问题。传统 GraphRAG 需要进行实体关系抽取，成本较高。LinearRAG 提出一种 relation-free 的层次图结构 Tri-Graph，减少关系抽取开销，使 GraphRAG 更适合大规模文档场景。

**值得关注的点：**

- 解决大规模 GraphRAG 的构建成本问题；
- 不依赖复杂关系抽取；
- 适合研究高效 GraphRAG 和工程化部署。

---

## 20. Youtu-GraphRAG: Vertically Unified Agents for Graph Retrieval-Augmented Complex Reasoning

- **会议/年份：** ICLR 2026
- **论文链接：** [OpenReview](https://openreview.net/forum?id=yCtgZ2G39E)
- **arXiv：** [arXiv:2508.19855](https://arxiv.org/abs/2508.19855)
- **代码：** [GitHub](https://github.com/TencentCloudADP/youtu-graphrag)
- **关键词：** agentic GraphRAG, graph schema, hierarchical knowledge tree, complex reasoning

**论文总结：**  
Youtu-GraphRAG 将 Agent 引入 GraphRAG 的完整流程，包括图构建、图索引、图检索和复杂推理。它通过 schema-guided extraction、community detection 和 hierarchical knowledge tree 等方法组织知识，再由智能体协调检索和推理过程。

**值得关注的点：**

- GraphRAG 与 Agent 的结合；
- 强调端到端的图构建和图检索流程；
- 适合研究 agentic RAG、复杂推理、多智能体知识检索。

---

## 21. QAFD-RAG: Query-Aware Flow Diffusion for Graph-Based RAG

- **会议/年份：** ICLR 2026
- **论文链接：** [OpenReview](https://openreview.net/forum?id=n28wnc2QTc)
- **arXiv：** [arXiv:2605.18775](https://arxiv.org/abs/2605.18775)
- **项目主页：** [Project Page](https://qafd-rag.github.io/)
- **关键词：** query-aware graph traversal, flow diffusion, theoretical guarantees, training-free retrieval

**论文总结：**  
QAFD-RAG 提出 query-aware flow diffusion，用查询相关的扩散过程来指导图检索。它会根据当前 query 动态调整图中边的重要性，从而让检索过程更倾向于找到与问题相关的子图。

**值得关注的点：**

- 有理论保证的图检索方法；
- 不只是启发式图遍历；
- 适合研究图检索算法和 KG-RAG 理论分析。

---

## 22. KG-IRAG: Beyond Single Pass, Looping Through Time: KG-IRAG with Iterative Knowledge Retrieval

- **会议/年份：** WWW 2026
- **论文链接：** [ACM DL](https://dl.acm.org/doi/abs/10.1145/3774904.3792745)
- **arXiv：** [arXiv:2503.14234](https://arxiv.org/abs/2503.14234)
- **关键词：** iterative retrieval, temporal reasoning, KG-RAG, multi-step reasoning

**论文总结：**  
KG-IRAG 关注迭代式知识检索。很多复杂问题不能通过一次检索解决，尤其是涉及时间关系、事件链和多步依赖的问题。KG-IRAG 通过多轮检索和查询更新，不断补充新的 KG 证据。

**值得关注的点：**

- 从单次检索转向多轮检索；
- 适合时序推理和复杂问答；
- 对构建闭环 KG-RAG 系统有参考价值。

---

## 23. RPO-RAG: Aligning Small LLMs with Relation-aware Preference Optimization for Knowledge Graph Question Answering

- **会议/年份：** WWW 2026
- **论文链接：** [ACM DL](https://dl.acm.org/doi/10.1145/3774904.3792730)
- **arXiv：** [arXiv:2601.19225](https://arxiv.org/abs/2601.19225)
- **代码：** [GitHub](https://github.com/KaeHyun/RPO-RAG)
- **关键词：** small LLM, KGQA, preference optimization, relation-aware alignment

**论文总结：**  
RPO-RAG 面向小模型 KGQA。它通过 relation-aware preference optimization，让小规模 LLM 更好地理解和利用 KG 中的关系路径。论文重点不是训练超大模型，而是让较小模型通过 KG 检索和偏好优化获得更强的推理能力。

**值得关注的点：**

- 适合单卡 GPU 资源有限的研究；
- 关注小模型与 KG-RAG 的结合；
- 可以作为轻量化 KG-RAG 的研究入口。

---

## 24. AnchorRAG: Towards Open-World Retrieval-Augmented Generation on Knowledge Graph: A Multi-Agent Collaboration Framework

- **会议/年份：** WWW 2026
- **论文链接：** [ACM DL](https://dl.acm.org/doi/10.1145/3774904.3792389)
- **arXiv：** [arXiv:2509.01238](https://arxiv.org/abs/2509.01238)
- **关键词：** open-world KG-RAG, anchor entity, multi-agent retrieval, KGQA

**论文总结：**  
AnchorRAG 面向开放世界 KG-RAG 场景。在真实 KGQA 中，问题中的实体不一定能直接链接到 KG 中的 anchor entity。该论文使用多智能体协作方式寻找候选锚点、进行多跳探索并综合证据路径。

**值得关注的点：**

- 解决开放世界 KG-RAG 中的实体链接困难；
- 使用多智能体协作进行 KG 检索；
- 适合研究鲁棒 KGQA 和开放域知识图谱问答。

---

## 25. MetaKGRAG: Metacognitive Knowledge Graph Retrieval Augmented Generation

- **会议/年份：** WWW 2026
- **论文链接：** [ACM DL](https://dl.acm.org/doi/10.1145/3770854.3780156)
- **arXiv：** [arXiv:2508.09460](https://arxiv.org/abs/2508.09460)
- **关键词：** metacognitive retrieval, closed-loop KG-RAG, path-aware refinement, self-correction

**论文总结：**  
MetaKGRAG 引入类似“元认知”的闭环机制，让系统能够感知当前检索是否充分，评估路径是否合理，并根据反馈调整后续检索。它不是一次性完成检索，而是通过 Perceive-Evaluate-Adjust 的循环逐步修正检索方向。

**值得关注的点：**

- KG-RAG 的自我反思和自我修正；
- 从 open-loop retrieval 走向 closed-loop retrieval；
- 适合研究智能体式 KG-RAG 和鲁棒推理。

---

## 26. What Breaks Knowledge Graph based RAG? Evidence from Reasoning under Knowledge Incompleteness

- **会议/年份：** EACL 2026
- **论文链接：** [ACL Anthology](https://aclanthology.org/2026.eacl-long.114/)
- **PDF：** [ACL Anthology PDF](https://aclanthology.org/2026.eacl-long.114.pdf)
- **arXiv：** [arXiv:2508.08344](https://arxiv.org/abs/2508.08344)
- **关键词：** KG-RAG evaluation, incomplete knowledge, robustness, benchmark, BRINK

**论文总结：**  
这篇论文研究 KG 不完整时 KG-RAG 会如何失败。现实知识图谱往往缺少关键边或关键三元组，如果模型过度依赖 KG 检索，就可能在缺失证据时给出错误答案。论文提出 BRINK 基准，用于评估 KG-RAG 在知识不完整条件下的推理能力。

**值得关注的点：**

- 直接关注 KG-RAG 的失败机制；
- 适合研究鲁棒性、对抗攻击和可靠性；
- 对 KG-RAG 安全评测非常有价值。

---

# 推荐阅读路线

如果刚开始做 KG-RAG，可以按照下面的顺序阅读：

1. **KG²RAG**  
   先理解最标准的 KG-guided RAG 流程：语义检索、KG 扩展、KG 组织。

2. **SubgraphRAG**  
   理解为什么 KG-RAG 的核心不只是“多放一些文本”，而是检索问题相关的子图。

3. **LightRAG**  
   学习一个相对轻量、容易复现、工程实用性强的 GraphRAG 框架。

4. **PathRAG**  
   学习如何从大图中筛选关键关系路径，减少上下文冗余和噪声。

5. **When to Use Graphs in RAG**  
   理解什么时候 GraphRAG 有用，什么时候普通 RAG 已经足够。

6. **D-RAG / BYOKG-RAG / KERAG**  
   深入 KGQA 场景下的图检索、可微检索、多策略检索和子图总结。

7. **LeanRAG / LinearRAG / LEGO-GraphRAG**  
   学习系统层面的 GraphRAG：可扩展性、模块化设计、层次化检索、成本控制。

8. **What Breaks KG-RAG / Privacy-protected KG-RAG**  
   关注 KG-RAG 的鲁棒性、隐私、安全和知识缺失问题。

---

# 研究趋势总结

## 1. 从文本 chunk 检索转向实体、关系、路径和子图检索

传统 RAG 的检索单位主要是文本片段，而 KG-RAG 更强调结构化证据，例如实体、三元组、关系路径和子图。KG²RAG、SubgraphRAG、D-RAG、PathRAG 和 BYOKG-RAG 都体现了这一趋势。

## 2. 从静态 KG 转向动态 KG 或即时图构建

现实中很多任务没有现成的高质量知识图谱。LogicRAG 和 TAdaRAG 说明，未来 KG-RAG 可能不再完全依赖预构建 KG，而是根据任务动态构建推理结构或临时知识图谱。

## 3. 从单次检索转向迭代检索和闭环检索

KG-IRAG 和 MetaKGRAG 表明，复杂问题通常需要多轮检索、评估和修正。KG-RAG 正在从一次性检索走向“检索—判断—再检索—再生成”的闭环流程。

## 4. 从追求准确率转向效率、成本和可扩展性

LightRAG、LeanRAG、LinearRAG、PathRAG 和 LEGO-GraphRAG 都在解决 GraphRAG 的效率问题，例如图构建成本高、检索上下文冗余、token 消耗大、运行速度慢等。

## 5. 从性能提升转向鲁棒性、隐私和安全

Privacy-protected KG-RAG 和 What Breaks KG-RAG 说明，未来 KG-RAG 不只是要提高准确率，还要处理私有 KG、敏感实体、知识缺失、错误路径、攻击注入等安全问题。

---

# 适合继续深入的研究方向

## 方向一：KG-RAG 的对抗攻击与鲁棒性评测

可以研究：

- 向 KG 中注入错误三元组；
- 删除关键推理边；
- 添加伪造实体；
- 构造误导性 relation path；
- 攻击实体链接或 anchor selection；
- 评估 KG-RAG 在知识缺失和知识污染下的表现。

相关论文：

- What Breaks Knowledge Graph based RAG?
- PathRAG
- BYOKG-RAG
- AnchorRAG
- Privacy-protected RAG for KGQA

---

## 方向二：轻量化 KG-RAG / 小模型 KGQA-RAG

适合 GPU 资源有限的个人研究。可以研究如何让 7B/8B 甚至更小的模型通过 KG 检索达到更强的复杂问答能力。

相关论文：

- RPO-RAG
- LightRAG
- LeanRAG
- LinearRAG
- SubgraphRAG

---

## 方向三：动态 KG 构建增强 RAG

不依赖现成知识图谱，而是从文档中抽取实体关系，构造任务相关的临时知识图谱。

相关论文：

- TAdaRAG
- LogicRAG
- KG²RAG
- Youtu-GraphRAG

---

## 方向四：路径检索与子图检索优化

研究如何从大规模 KG 中检索更短、更准、更少冗余的推理路径或子图。

相关论文：

- PathRAG
- SubgraphRAG
- D-RAG
- QAFD-RAG
- KERAG

---

## 方向五：KG-RAG 评测与 Benchmark

研究 KG-RAG 到底在哪些任务上有效、在哪些任务上无效，以及如何公平评价 KG-RAG。

相关论文：

- When to Use Graphs in RAG
- What Breaks Knowledge Graph based RAG?
- LEGO-GraphRAG
- GFM-RAG

---

# 备注

本列表主要关注 2025-2026 年各大顶会中与 KG-RAG / GraphRAG 相关的论文。部分论文标题中直接包含 KG-RAG，部分论文使用 GraphRAG、graph-based RAG、subgraph retrieval、KGQA with RAG 等表述。只要核心方法使用图结构知识来增强检索和生成，都被纳入本列表。
