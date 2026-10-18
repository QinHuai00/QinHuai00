# 严文跃 · AI 应用开发

27 届计算机科学与技术本科，求职方向：**AI 应用开发 / 大模型应用开发**。
习惯把大模型能力做成"能跑、能测、能讲清楚"的工程，而不是停在 Demo 阶段。

## 🚀 项目

### [rag-knowledge-base](https://github.com/QinHuai00/rag-knowledge-base)

企业知识库 RAG 问答系统：文档解析 → 语义切分 → 向量检索 → 引用溯源 → 低置信度拒答。
自带 24 条评测集与阈值校准脚本；离线可跑（不装依赖、不联网），配置 Key 后自动切换真实模型。
`Python` `FastAPI` `RAG` `向量检索` `评测` `GitHub Actions`

### [ai-resume-matcher](https://github.com/QinHuai00/ai-resume-matcher)

AI 简历—岗位匹配助手：JD / 简历结构化 → 可解释三维评分（60/25/15）→ 缺失技能清单与可执行的改写建议。
SQLite 缓存、asyncio 批量限流、45 个单元测试。
`Python` `LLM 结构化输出` `SQLite` `Streamlit` `asyncio`

> 两个仓库当前都是**初版 V1**：主链路可运行、有单元测试与评测脚本，后续优化路线写在各自 `docs/roadmap.md` 里。

## 🧰 技术栈

- **语言**：Python（主力）、SQL、JavaScript / HTML
- **大模型应用**：OpenAI 兼容 API、Prompt Engineering、结构化输出与校验重试、SSE 流式输出
- **RAG / 检索**：文档解析与清洗、语义切分、Embedding、向量检索、BM25、RRF、Rerank（学习中）
- **工程**：FastAPI、SQLite、Git、Linux 常用命令、Docker（了解）
- **评测**：自建 QA 评测集、Recall@K、拒答正确率、首字延迟 TTFT、结构化输出成功率

## 📫 联系

- GitHub：[@QinHuai00](https://github.com/QinHuai00)
