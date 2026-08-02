# nano-Harness

> **[CN] 从零实现包在大模型外面的 Agent Harness（执行基础设施）**  
> **[EN] Building LLM Agent Execution Harnesses from Scratch with Python & Jupyter Notebooks**

---

## 📌 简介 / Overview

**[CN]**  
**nano-Harness** 是一个基于 Python 的微型 Agent 执行基础设施教学与实验库。我们主张：“**决定 Agent 可靠性的往往不是模型本身，而是包在它外面的 Harness**”。本项目参考综述论文 [*Agent Harness Engineering: A Survey*](https://picrew.github.io/LLM-Harness/) 提出的 **ETCLOVG 七层架构体系**（Execution, Tool, Context, Lifecycle, Observability, Verification, Governance）构建，采用 **Notebook-first** 理念，用最小可运行、真实 API 驱动、可观测的代码带你逐层拆解现代 Agent 执行机制。

**[EN]**  
**nano-Harness** is a minimal educational Python repository for building LLM Agent execution harnesses. We demonstrate that *"agent reliability is often governed by its execution harness rather than the model itself"*. Built upon the **ETCLOVG 7-layer architecture** (Execution, Tool, Context, Lifecycle, Observability, Verification, Governance) proposed in [*Agent Harness Engineering: A Survey*](https://picrew.github.io/LLM-Harness/), it provides self-contained, real-API-driven, and highly observable code to unpack modern agent infrastructure step-by-step.

---

## ✨ 核心特色 / Key Features

- 📖 **Notebook-first / 单文件自包含**  
  **[CN]** 每个核心机制均独立封装在一个可直接运行的 `.ipynb` 中，无需跨文件跳转。  
  **[EN]** Each core mechanism is independently encapsulated in a runnable `.ipynb` file, eliminating the overhead of navigating across files.

- 🔑 **真实 API 驱动 / Real API Driven**  
  **[CN]** 拒绝静态 Mock 数据，所有运行与输出均由统一 `.env` 配置的真实 LLM Backend 产生。  
  **[EN]** Eliminates static mock data; all executions and outputs are driven by real LLM Backends configured via a unified `.env` file.

- 🔍 **运行时可观测 / Runtime Observability**  
  **[CN]** 如同在 PyTorch 中打印 Tensor Shape，全程可视化输出输入上下文、工具调用决策、权限控制与 Trace 树。  
  **[EN]** Just like printing tensor shapes in PyTorch, it visually logs input contexts, tool-calling decisions, permission controls, and trace trees.

---

## 📁 项目结构 / Project Structure

核心教学 Notebooks 存放在 [`notebooks/`](./notebooks) 目录下：  
*Core educational notebooks are located in the [`notebooks/`](./notebooks) directory:*

```text
notebooks/
├── 00_core_nanoProviderAdapter_minimal.ipynb   # [Core] 统一 LLM Provider 接口与配置校验
├── 00_core_nanoMessageProtocol_minimal.ipynb   # [Core] 结构化消息协议与状态 Diff
├── 00_core_nanoToyEnv_minimal.ipynb            # [Core] 可重置隔离的玩具执行环境
└── 00_core_nanoAgentLoop_minimal.ipynb         # [Core] 极简 Agent 核心执行循环
```
```text
notebooks/
├── 00_core_nanoProviderAdapter_minimal.ipynb   # [Core] Unified LLM Provider Interface & Config Validation
├── 00_core_nanoMessageProtocol_minimal.ipynb   # [Core] Structured Message Protocol & State Diff
├── 00_core_nanoToyEnv_minimal.ipynb            # [Core] Isolated & Resettable Toy Execution Environment
└── 00_core_nanoAgentLoop_minimal.ipynb         # [Core] Minimal Agent Core Execution Loop
```
