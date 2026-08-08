# pure-harness

> **从零实现包在大模型外面的 Agent Execution Harness（执行基础设施）**  
> **Building LLM Agent Execution Harnesses from Scratch with Python & Jupyter Notebooks**

---

## 📌 简介 / Overview
 
**pure-harness** 是一个基于 Python 的微型 Agent 执行基础设施教学与实验库。就现阶段实践与生产而言，“**决定 Agent 可靠性的往往不是模型本身，而是包在它外面的 Harness**”。本项目参考综述论文 [*Agent Harness Engineering: A Survey*](https://picrew.github.io/LLM-Harness/) 提出的 **ETCLOVG 七层架构体系**（Execution, Tool, Context, Lifecycle, Observability, Verification, Governance）构建，采用 **Notebook-first** 理念，用最小可运行、真实 API 驱动、可观测的代码带你逐层拆解现代 Agent 执行机制。

**pure-harness** is a minimal educational Python repository for building LLM Agent execution harnesses. Regarding current practice and production, "**Agent reliability is often governed by its execution harness rather than the model itself**". Built upon the **ETCLOVG 7-layer architecture** (Execution, Tool, Context, Lifecycle, Observability, Verification, Governance) proposed in [*Agent Harness Engineering: A Survey*](https://picrew.github.io/LLM-Harness/), it provides self-contained, real-API-driven, and highly observable code to unpack modern agent infrastructure step-by-step.

<img width="1233" height="609" alt="taxonomy" src="https://github.com/user-attachments/assets/bc281bb0-3a08-4e73-93d3-e6b086f9bc53" />

Image source: [*Agent Harness Engineering: A Survey*](https://picrew.github.io/LLM-Harness/) 

---

## ✨ 核心特色 / Key Features

- 📖 **单文件自包含 / Notebook-first**  
  每个核心机制均独立封装在一个可直接运行的 `.ipynb` 中，无需跨文件跳转。  
  Each core mechanism is independently encapsulated in a runnable `.ipynb` file, eliminating the overhead of navigating across files.
  
- 💻 **极简轻量 / CPU-Only & Lightweight**  
  全代码仅涉及 Harness 执行逻辑与 API 交互，无需 GPU 显卡，普通本地电脑/笔记本即可秒级运行。  
  Pure Python harness logic using remote APIs—NO GPU required; runs seamlessly on standard laptops.

- 🔑 **真实 API 驱动 / Real API Driven**  
  拒绝静态 Mock 数据，所有运行与输出均由统一 `.env` 配置的真实 LLM Backend 产生。  
  Eliminates static mock data; all executions and outputs are driven by real LLM Backends configured via a unified `.env` file.

- 🔍 **运行时可观测 / Runtime Observability**  
  如同在 PyTorch 中打印 Tensor Shape，全程可视化输出输入上下文、工具调用决策、权限控制与 Trace 树。  
  Just like printing tensor shapes in PyTorch, it visually logs input contexts, tool-calling decisions, permission controls, and trace trees.

---

## 📁 项目结构 / Project Structure

核心教学 Notebooks 按 ETCLOVG 七层架构模块化存放在仓库根目录的各子目录中：  
*Core educational notebooks are organized into module-based subdirectories at the repository root, following the ETCLOVG 7-layer architecture:*

```text
pure-harness/
├── 00_core/                                                # [Core] 核心基础模块
│   ├── 00_core_nanoProviderAdapter.ipynb                   # [Core] 统一 LLM Provider 接口与配置校验
│   ├── 00_core_nanoMessageProtocol.ipynb                   # [Core] 结构化消息协议与状态 Diff
│   ├── 00_core_nanoToyEnv.ipynb                            # [Core] 可重置隔离的玩具执行环境
│   └── 00_core_nanoAgentLoop.ipynb                         # [Core] 极简 Agent 核心执行循环
├── 01_Execution Environment and Sandbox (E)/               # [E] 执行环境与沙箱层
│   ├── 01_E_nanoSandbox.ipynb                              # [E] 沙箱化代码执行环境
│   ├── 01_E_nanoResetReplay.ipynb                          # [E] 状态重置与执行回放
│   └── 01_E_nanoSandboxAbstraction.ipynb                   # [E] 沙箱抽象层
├── 02_Tool Interface and Protocol Layer (T)/               # [T] 工具接口与协议层
│   ├── 02_T_nanoToolCalling.ipynb                          # [T] 工具调用机制
│   ├── 02_T_nanoToolRegistry.ipynb                         # [T] 工具注册表
│   └── 02_T_nanoMCPMiniProtocol.ipynb                      # [T] MCP 迷你协议
├── 03_Context and Memory Management (C)/                   # [C] 上下文与记忆管理层
│   ├── 03_C_nanoContextWindow.ipynb                        # [C] 上下文窗口管理
│   ├── 03_C_nanoMemory.ipynb                               # [C] 记忆系统
│   └── 03_C_nanoLongHorizonCompaction.ipynb                # [C] 长时程上下文压缩
├── 04_Lifecycle and Orchestration (L)/                     # [L] 生命周期与编排层
│   ├── 04_L_nanoReActLoop.ipynb                            # [L] ReAct 推理-执行循环
│   ├── 04_L_nanoMultiAgent.ipynb                           # [L] 多 Agent 协作
│   └── 04_L_nanoTaskRunnerLifecycle.ipynb                  # [L] 任务运行器生命周期
├── 05_Observability and Operations (O)/                    # [O] 可观测性与运维层
│   ├── 05_O_nanoCostTelemetry.ipynb                        # [O] 成本遥测
│   ├── 05_O_nanoReliabilityOps.ipynb                       # [O] 可靠性运维
│   └── 05_O_nanoTraceOps.ipynb                             # [O] Trace 运维
├── 06_Verification and Evaluation (V)/                     # [V] 验证与评测层
│   ├── 06_V_nanoEvalHarness.ipynb                          # [V] 评测基础设施
│   ├── 06_V_nanoFailureAttribution.ipynb                   # [V] 失败归因
│   └── 06_V_nanoRegressionSuite.ipynb                      # [V] 回归测试套件
├── 07_Governance and Security (G)/                         # [G] 治理与安全层
│   ├── 07_G_nanoGovernance.ipynb                           # [G] 治理框架
│   ├── 07_G_nanoPromptInjectionDefense.ipynb               # [G] 提示注入防御
│   └── 07_G_nanoAuditConstitution.ipynb                    # [G] 审计宪章
├── 08_Cross-Layer Synthesis (X)/                           # [X] 跨层综合层
│   ├── 08_X_nanoFullHarness.ipynb                          # [X] 完整 Harness 集成
│   ├── 08_X_nanoCostQualitySpeed.ipynb                     # [X] 成本-质量-速度权衡
│   └── 08_X_nanoHarnessCoupling.ipynb                      # [X] Harness 耦合分析
├── .env                                                    # API 密钥配置
├── LICENSE                                                 # MIT 开源协议
└── README.md                                               # 项目说明文档
```
```text
pure-harness/
├── 00_core/                                                # [Core] Core Foundation Modules
│   ├── 00_core_nanoProviderAdapter.ipynb                   # [Core] Unified LLM Provider Interface & Config Validation
│   ├── 00_core_nanoMessageProtocol.ipynb                   # [Core] Structured Message Protocol & State Diff
│   ├── 00_core_nanoToyEnv.ipynb                            # [Core] Isolated & Resettable Toy Execution Environment
│   └── 00_core_nanoAgentLoop.ipynb                         # [Core] Minimal Agent Core Execution Loop
├── 01_Execution Environment and Sandbox (E)/               # [E] Execution Environment & Sandbox Layer
│   ├── 01_E_nanoSandbox.ipynb                              # [E] Sandboxed Code Execution Environment
│   ├── 01_E_nanoResetReplay.ipynb                          # [E] State Reset & Execution Replay
│   └── 01_E_nanoSandboxAbstraction.ipynb                   # [E] Sandbox Abstraction Layer
├── 02_Tool Interface and Protocol Layer (T)/               # [T] Tool Interface & Protocol Layer
│   ├── 02_T_nanoToolCalling.ipynb                          # [T] Tool Calling Mechanism
│   ├── 02_T_nanoToolRegistry.ipynb                         # [T] Tool Registry
│   └── 02_T_nanoMCPMiniProtocol.ipynb                      # [T] MCP Mini Protocol
├── 03_Context and Memory Management (C)/                   # [C] Context & Memory Management Layer
│   ├── 03_C_nanoContextWindow.ipynb                        # [C] Context Window Management
│   ├── 03_C_nanoMemory.ipynb                               # [C] Memory System
│   └── 03_C_nanoLongHorizonCompaction.ipynb                # [C] Long-Horizon Context Compaction
├── 04_Lifecycle and Orchestration (L)/                     # [L] Lifecycle & Orchestration Layer
│   ├── 04_L_nanoReActLoop.ipynb                            # [L] ReAct Reasoning-Action Loop
│   ├── 04_L_nanoMultiAgent.ipynb                           # [L] Multi-Agent Collaboration
│   └── 04_L_nanoTaskRunnerLifecycle.ipynb                  # [L] Task Runner Lifecycle
├── 05_Observability and Operations (O)/                    # [O] Observability & Operations Layer
│   ├── 05_O_nanoCostTelemetry.ipynb                        # [O] Cost Telemetry
│   ├── 05_O_nanoReliabilityOps.ipynb                       # [O] Reliability Operations
│   └── 05_O_nanoTraceOps.ipynb                             # [O] Trace Operations
├── 06_Verification and Evaluation (V)/                     # [V] Verification & Evaluation Layer
│   ├── 06_V_nanoEvalHarness.ipynb                          # [V] Evaluation Harness
│   ├── 06_V_nanoFailureAttribution.ipynb                   # [V] Failure Attribution
│   └── 06_V_nanoRegressionSuite.ipynb                      # [V] Regression Test Suite
├── 07_Governance and Security (G)/                         # [G] Governance & Security Layer
│   ├── 07_G_nanoGovernance.ipynb                           # [G] Governance Framework
│   ├── 07_G_nanoPromptInjectionDefense.ipynb               # [G] Prompt Injection Defense
│   └── 07_G_nanoAuditConstitution.ipynb                    # [G] Audit Constitution
├── 08_Cross-Layer Synthesis (X)/                           # [X] Cross-Layer Synthesis Layer
│   ├── 08_X_nanoFullHarness.ipynb                          # [X] Full Harness Integration
│   ├── 08_X_nanoCostQualitySpeed.ipynb                     # [X] Cost-Quality-Speed Trade-off
│   └── 08_X_nanoHarnessCoupling.ipynb                      # [X] Harness Coupling Analysis
├── .env                                                    # API Key Configuration
├── LICENSE                                                 # MIT License
└── README.md                                               # Project Documentation
```
---

## 🚀 快速开始 / Quick Start

### 1. 环境准备 / Environment Setup
克隆仓库并创建 Conda 环境：  
Clone the repository and set up a Conda environment:
```bash
git clone https://github.com/kaixinjiuxing666/pure-harness.git
cd pure-harness
conda create -n pure-harness python=3.11 -y
conda activate pure-harness
pip install -r requirements.txt
```

### 2. 配置密钥 / Configure API Key
在 `.env` 填入真实的 API 密钥  
Fill in your real API backend credentials in `.env` file

### 3. 打开并运行 / Launch & Run
在 IDE (如 VS Code / Cursor / PyCharm) 或 Jupyter Lab 中打开 `notebooks/` 目录下的目标 `.ipynb` 文件，选择配置好的 Python 内核即可按顺序运行代码单元格。  
Open any `.ipynb` file in the `notebooks/` directory using your IDE (e.g., VS Code, Cursor, PyCharm) or Jupyter Lab, select the configured Python kernel, and execute the cells step-by-step.

---

## TODO

> 注：带 `opt` 标识的为可选与进阶模块，不带 `opt` 的为基础必修模块。  
> Note: Notebooks with the `opt` prefix are optional & advanced modules, while those without `opt` are core foundation modules.

### 00_core
- [x] ~~`00_core_nanoProviderAdapter.ipynb`~~
- [x] ~~`00_core_nanoMessageProtocol.ipynb`~~
- [x] ~~`00_core_nanoToyEnv.ipynb`~~
- [x] ~~`00_core_nanoAgentLoop.ipynb`~~

### 01_E
- [x] ~~`01_E_nanoSandbox.ipynb`~~
- [x] ~~`01_E_nanoResetReplay.ipynb`~~
- [x] ~~`01_E_nanoSandboxAbstraction.ipynb`~~
- [ ] `01_E_opt_nanoBrowserEnv.ipynb`
- [ ] `01_E_opt_nanoPermissionSandbox.ipynb`
- [ ] `01_E_opt_nanoSandboxEscapeBench.ipynb`
- [ ] `01_E_opt_nanoWasmSandbox.ipynb`

### 02_T
- [x] ~~`02_T_nanoToolCalling.ipynb`~~
- [x] ~~`02_T_nanoToolRegistry.ipynb`~~
- [x] ~~`02_T_nanoMCPMiniProtocol.ipynb`~~
- [ ] `02_T_opt_nanoOpenAPIAdapter.ipynb`
- [ ] `02_T_opt_nanoSkillLibrary.ipynb`
- [ ] `02_T_opt_nanoTokenEfficientTools.ipynb`
- [ ] `02_T_opt_nanoToolLearningToy.ipynb`
- [ ] `02_T_opt_nanoToolSessionScaling.ipynb`

### 03_C
- [x] ~~`03_C_nanoContextWindow.ipynb`~~
- [x] ~~`03_C_nanoMemory.ipynb`~~
- [x] ~~`03_C_nanoLongHorizonCompaction.ipynb`~~
- [ ] `03_C_opt_nanoContextDriftBenchmark.ipynb`
- [ ] `03_C_opt_nanoGraphMemory.ipynb`
- [ ] `03_C_opt_nanoKVCacheAwareContext.ipynb`
- [ ] `03_C_opt_nanoProgressiveDisclosure.ipynb`
- [ ] `03_C_opt_nanoSubAgentContextIsolation.ipynb`

### 04_L
- [x] ~~`04_L_nanoReActLoop.ipynb`~~
- [x] ~~`04_L_nanoMultiAgent.ipynb`~~
- [x] ~~`04_L_nanoTaskRunnerLifecycle.ipynb`~~
- [ ] `04_L_opt_nanoCheckpointResume.ipynb`
- [ ] `04_L_opt_nanoGraphWorkflow.ipynb`
- [ ] `04_L_opt_nanoHumanHandoff.ipynb`
- [ ] `04_L_opt_nanoPlannerGeneratorEvaluator.ipynb`
- [ ] `04_L_opt_nanoStateModels.ipynb`

### 05_O
- [x] ~~`05_O_nanoCostTelemetry.ipynb`~~
- [x] ~~`05_O_nanoReliabilityOps.ipynb`~~
- [x] ~~`05_O_nanoTraceOps.ipynb`~~
- [ ] `05_O_opt_nanoCognitiveObservability.ipynb`
- [ ] `05_O_opt_nanoOpenTelemetryMini.ipynb`
- [ ] `05_O_opt_nanoOpsDashboard.ipynb`

### 06_V
- [x] ~~`06_V_nanoEvalHarness.ipynb`~~
- [x] ~~`06_V_nanoFailureAttribution.ipynb`~~
- [x] ~~`06_V_nanoRegressionSuite.ipynb`~~
- [ ] `06_V_opt_nanoHarnessAblationEval.ipynb`
- [ ] `06_V_opt_nanoInfraNoise.ipynb`
- [ ] `06_V_opt_nanoLLMJudgeCalibration.ipynb`
- [ ] `06_V_opt_nanoReadinessValidation.ipynb`

### 07_G
- [x] ~~`07_G_nanoGovernance.ipynb`~~
- [x] ~~`07_G_nanoPromptInjectionDefense.ipynb`~~
- [x] ~~`07_G_nanoAuditConstitution.ipynb`~~
- [ ] `07_G_opt_nanoComponentHardening.ipynb`
- [ ] `07_G_opt_nanoCredentialVault.ipynb`
- [ ] `07_G_opt_nanoFormalPolicyDSL.ipynb`
- [ ] `07_G_opt_nanoIdentityDelegation.ipynb`
- [ ] `07_G_opt_nanoInfoFlowControl.ipynb`

### 08_X
- [x] ~~`08_X_nanoFullHarness.ipynb`~~
- [x] ~~`08_X_nanoCostQualitySpeed.ipynb`~~
- [x] ~~`08_X_nanoHarnessCoupling.ipynb`~~
- [ ] `08_X_opt_nanoCapabilityControl.ipynb`
- [ ] `08_X_opt_nanoHarnessAsAssumption.ipynb`
- [ ] `08_X_opt_nanoLongRunStability.ipynb`
- [ ] `08_X_opt_nanoMetaHarnessSearch.ipynb`
- [ ] `08_X_opt_nanoSelfEvolution.ipynb`

### 09_capstone
- [ ] `09_capstone_nanoAgentPlatform.ipynb`

---

## 📄 开源协议 / License

本项目采用 [MIT License](LICENSE) 开源协议。  
This project is licensed under the [MIT License](LICENSE).
