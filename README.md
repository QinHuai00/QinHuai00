# 严文跃 · AI 应用开发

27 届计算机科学与技术本科，求职方向：**AI 应用开发 / 大模型应用开发**。
习惯把大模型能力做成"能跑、能测、能讲清楚"的工程，而不是停在 Demo 阶段。

## 🚀 项目

### [resume-parser-agent](https://github.com/QinHuai00/resume-parser-agent)

简历 → 结构化 JSON 的抽取 Agent：解析（docx/pdf/txt + OCR 钩子）→ 抽取（JSON Schema 注入提示词）→ 校验（Pydantic：邮箱/手机号/年限/禁止多余字段）→ **修复**（把 ValidationError 原文回灌模型，只修错字段）→ **证据溯源**（每个字段必须给出原文逐字片段，对不上就置 null 并记入 `dropped_fields`）。

自建 12 份合成简历评测集 + 可控注入故障的模拟模型：**结构合法率 91.7% → 100%，平均修复轮次 0.08；100% 脏输入下仍为 100%**。批量接口异步化（立即返回 task_id、后台协程、信号量限并发、单份失败隔离），**36 个离线用例** + GitHub Actions CI。
`Python` `FastAPI` `Pydantic v2` `JSON Schema` `httpx` `pypdf` `pytest` `GitHub Actions`
[设计取舍](https://github.com/QinHuai00/resume-parser-agent/blob/main/docs/DESIGN_DECISIONS.md) ｜ [评测结果](https://github.com/QinHuai00/resume-parser-agent/blob/main/eval/results.md)

### [rag-knowledge-base](https://github.com/QinHuai00/rag-knowledge-base)

企业知识库 RAG 问答系统，已完成 V1 → V4 优化：文档解析 → 父子块切分 → 向量 + BM25 双路召回 → RRF 融合 → 规则精排 → 引用溯源 → 低置信度拒答。
自带 **53 条评测集**与四级消融实验：V4 使**小节级 Recall@1 从 93.6% 提升到 100%、MRR 从 0.968 提升到 1.000、nDCG@5 从 0.976 提升到 1.000**（离线模式，口径见仓库）。零依赖可跑，配置 Key 后自动切换真实模型。
`Python` `FastAPI` `RAG` `BM25` `RRF` `评测` `GitHub Actions`
[优化实录](https://github.com/QinHuai00/rag-knowledge-base/blob/main/docs/optimization-log.md)

### [ai-resume-matcher](https://github.com/QinHuai00/ai-resume-matcher)

AI 简历—岗位匹配助手：JD / 简历结构化 → 可解释三维评分（硬性要求 + 技能覆盖 + 经历相关度）→ 缺失技能与分级改写建议。
用**留一交叉验证（LOOCV）** 校准权重，**MAE 从 6.5 降到 4.4、Spearman 0.979、分档准确率 100%**；SQLite 缓存、asyncio 批量、**53 个单元测试**（含缓存键评分配置指纹）。
`Python` `LLM 结构化输出` `LOOCV` `SQLite` `Streamlit` `GitHub Actions`
[优化实录](https://github.com/QinHuai00/ai-resume-matcher/blob/main/docs/optimization-log.md)

> 上面三个仓库都按"可运行、可评测、可复现"的标准做：README + 单元测试 + GitHub Actions CI + 优化实录/设计取舍文档。
> 离线数字只验证工程链路与相对改进，不代表真实模型效果；接入真实 API 后需用同一脚本重测。

## 📚 复现与二次开发（学习记录）

### [rag-kb-pro](https://github.com/QinHuai00/rag-kb-pro)

本地知识库 RAG 的上游复现 + 二次开发（上游：[lhh737/KnowledgeBase-RAG-LLM-System](https://github.com/lhh737/KnowledgeBase-RAG-LLM-System)，MIT，`upstream/` 内保留逐字快照与版权头）。
做三件事：① 定位并修复上游 `add_texts(metadata=)` 被 `**kwargs` 静默吞掉导致元数据全空的缺陷（用最小复现类把行为锁进单测）；② 把 `similarity_threshold`（实为 `k`）拆成 `top_k` + `dense_min_score`；③ 加混合检索（BM25 + 向量 + RRF）、可插拔 Embedder（真实 DashScope / 离线确定性）、28 题评测脚手架与 FastAPI 服务层。

真实结果（离线 HashingEmbedder，28 题）：bm25/hybrid Top-1 92.9%、hybrid 关键词命中@3 89.3%（bm25 82.1%）；**hybrid+rerank 反而掉 3.6pt Top-1**——负结论原样保留在 `eval/results.md`。63 个离线用例，CI 全绿。
`Python` `BM25` `RRF` `FastAPI` `评测` `pytest`
[评测结果](https://github.com/QinHuai00/rag-kb-pro/blob/main/eval/results.md) ｜ [设计取舍](https://github.com/QinHuai00/rag-kb-pro/blob/main/docs/DESIGN.md)

## 🧰 技术栈

- **语言**：Python（主力）、SQL、JavaScript / HTML
- **大模型应用**：OpenAI 兼容 API、Prompt Engineering、结构化输出与 JSON 校验 / 错误回灌修复、字段级证据溯源、引用溯源与低置信度拒答
- **RAG / 检索**：文档解析与清洗、父子块切分、BM25、RRF、规则精排、Embedding（BGE，可选接入）、评测（Recall@K / MRR / nDCG@5 / 要点覆盖率）
- **工程**：FastAPI、Pydantic v2、SQLite、asyncio、WebSocket、Git、Linux 常用命令、pytest / unittest、GitHub Actions
- **评测方法**：自建 QA 评测集、四级消融实验、留一交叉验证、MAE / Spearman / 分档准确率、可复现的故障注入

## 📫 联系

- GitHub：[@QinHuai00](https://github.com/QinHuai00)