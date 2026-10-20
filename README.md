# 严文跃 · AI 应用开发

27 届计算机科学与技术本科，求职方向：**AI 应用开发 / 大模型应用开发**。
习惯把大模型能力做成"能跑、能测、能讲清楚"的工程，而不是停在 Demo 阶段。

## 🚀 项目

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

> 两个仓库都按"可运行、可评测、可复现"的标准做：README + 单元测试 + GitHub Actions CI + 优化实录。
> 离线数字只验证工程链路与相对改进，不代表真实模型效果；接入真实 API 后需用同一脚本重测。

## 🧰 技术栈

- **语言**：Python（主力）、SQL、JavaScript / HTML
- **大模型应用**：OpenAI 兼容 API、Prompt Engineering、结构化输出与 JSON 校验 / 错误回灌重试、引用溯源与低置信度拒答
- **RAG / 检索**：文档解析与清洗、父子块切分、BM25、RRF、规则精排、Embedding（BGE，可选接入）、评测（Recall@K / MRR / nDCG@5 / 要点覆盖率）
- **工程**：FastAPI、SQLite、Git、Linux 常用命令、unittest、GitHub Actions
- **评测方法**：自建 QA 评测集、四级消融实验、留一交叉验证、MAE / Spearman / 分档准确率

## 📫 联系

- GitHub：[@QinHuai00](https://github.com/QinHuai00)
