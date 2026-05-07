# 相关项目与文献

> 本文档记录与 UKCGA 概念相关的现有工作，用于对比和借鉴。

## 参数高效微调 (PEFT)

### LoRA
- **核心思想**：低秩适配，仅训练低秩矩阵
- **与 UKCGA 的关系**：UKCGA 的 MLA 可能借鉴 LoRA 的低秩思想
- **关键差异**：LoRA 修改参数，UKCGA 尝试避免参数修改
- **参考**：https://github.com/huggingface/peft

### Prompt Tuning
- **核心思想**：优化软提示嵌入
- **与 UKCGA 的关系**：UKCGA 的 SIP 可能借鉴软提示思想
- **关键差异**：Prompt Tuning 仍绑定特定模型
- **参考**：https://arxiv.org/abs/2104.08691

## 知识编辑

### ROME / MEMIT
- **核心思想**：定位并编辑模型中的特定知识
- **与 UKCGA 的关系**：DKE 可能借鉴知识定位思路
- **关键差异**：ROME 直接修改参数，UKCGA 尝试外部存储差异
- **参考**：https://github.com/zjunlp/EasyEdit

### 关键观察
知识编辑领域的主要挑战（副作用、可扩展性）也是 UKCGA 需要面对的问题。

## 记忆增强网络

### Neural Turing Machine
- **核心思想**：可微分外部记忆
- **与 UKCGA 的关系**：双存储架构的灵感来源
- **关键差异**：NTM 是模型架构，UKCGA 是用户层系统
- **参考**：Graves et al., 2014

### Differentiable Neural Computer
- **核心思想**：带记忆网络的神经网络
- **与 UKCGA 的关系**：复杂读写机制的参考
- **关键差异**：DNC 复杂度高，UKCGA 追求极简

## 用户记忆系统

### LangChain Memory
- **核心思想**：对话历史管理
- **与 UKCGA 的关系**：应用场景重叠
- **关键差异**：LangChain 是非参数化，UKCGA 探索参数化
- **参考**：https://github.com/langchain-ai/langchain

### 观察
大多数现有方案选择非参数化路线（RAG、上下文等），UKCGA 探索参数化是否可行。

## 模型合并

### Task Arithmetic
- **核心思想**：通过向量运算合并模型能力
- **与 UKCGA 的关系**：DKE 可看作特殊任务向量
- **关键差异**：Task Arithmetic 用于模型级，UKCGA 用于用户级
- **参考**：https://github.com/ist-daslab/tars

## 持续学习

### 终身学习 (Lifelong Learning)
- **核心思想**：模型持续学习新知识
- **与 UKCGA 的关系**：遗忘机制的设计参考
- **关键差异**：终身学习关注模型进化，UKCGA 关注用户隔离

## 对比总结

| 方向 | 参数化 | 版本无关 | 用户级 | 可遗忘 |
|------|--------|----------|--------|--------|
| LoRA | ✅ | ❌ | ❌ | ⚠️ |
| ROME | ✅ | ❌ | ❌ | ⚠️ |
| LangChain | ❌ | ✅ | ✅ | ✅ |
| UKCGA (目标) | ✅ | ✅ | ✅ | ✅ |

## 关键差距

目前没有发现同时满足以下条件的方案：
1. 参数化（低存储成本）
2. 版本无关（灵活部署）
3. 用户级（多用户支持）
4. 可遗忘（隐私合规）

这正是 UKCGA 试图探索的空间。

## 待调研方向

- [ ] 超网络 (Hypernetworks) 在用户个性化的应用
- [ ] 模型压缩领域的相关技术
- [ ] 联邦学习与用户隐私保护
- [ ] 神经架构搜索 (NAS) 在适配中的应用

---

*如果你知道其他相关项目，欢迎补充。*
