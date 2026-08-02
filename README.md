# nano-Harness

> **从零实现包在大模型外面的 Agent Execution Harness（执行基础设施）**  
> **Building LLM Agent Execution Harnesses from Scratch with Python & Jupyter Notebooks**

---

## 📌 简介 / Overview
 
**nano-Harness** 是一个基于 Python 的微型 Agent 执行基础设施教学与实验库。就现阶段实践与生产而言，“**决定 Agent 可靠性的往往不是模型本身，而是包在它外面的 Harness**”。本项目参考综述论文 [*Agent Harness Engineering: A Survey*](https://picrew.github.io/LLM-Harness/) 提出的 **ETCLOVG 七层架构体系**（Execution, Tool, Context, Lifecycle, Observability, Verification, Governance）构建，采用 **Notebook-first** 理念，用最小可运行、真实 API 驱动、可观测的代码带你逐层拆解现代 Agent 执行机制。

**nano-Harness** is a minimal educational Python repository for building LLM Agent execution harnesses. Regarding current practice and production, "**Agent reliability is often governed by its execution harness rather than the model itself**". Built upon the **ETCLOVG 7-layer architecture** (Execution, Tool, Context, Lifecycle, Observability, Verification, Governance) proposed in [*Agent Harness Engineering: A Survey*](https://picrew.github.io/LLM-Harness/), it provides self-contained, real-API-driven, and highly observable code to unpack modern agent infrastructure step-by-step.

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
---

## 🚀 快速开始 / Quick Start

### 1. 环境准备 / Environment Setup
克隆仓库并创建 Conda 环境：  
Clone the repository and set up a Conda environment:
```bash
git clone https://github.com/your-username/nano-Harness.git
cd nano-Harness
conda create -n nano-harness python=3.11 -y
conda activate nano-harness
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
- [x] ~~`00_core_nanoProviderAdapter_minimal.ipynb`~~
- [x] ~~`00_core_nanoMessageProtocol_minimal.ipynb`~~
- [x] ~~`00_core_nanoToyEnv_minimal.ipynb`~~
- [x] ~~`00_core_nanoAgentLoop_minimal.ipynb`~~

### 01_E
- [ ] `01_E_nanoSandbox_minimal.ipynb`
- [ ] `01_E_nanoResetReplay_minimal.ipynb`
- [ ] `01_E_nanoSandboxAbstraction_minimal.ipynb`
- [ ] `01_E_opt_nanoBrowserEnv_minimal.ipynb`
- [ ] `01_E_opt_nanoPermissionSandbox_minimal.ipynb`
- [ ] `01_E_opt_nanoSandboxEscapeBench_minimal.ipynb`
- [ ] `01_E_opt_nanoWasmSandbox_minimal.ipynb`

### 02_T
- [ ] `02_T_nanoToolCalling_minimal.ipynb`
- [ ] `02_T_nanoToolRegistry_minimal.ipynb`
- [ ] `02_T_nanoMCPMiniProtocol_minimal.ipynb`
- [ ] `02_T_opt_nanoOpenAPIAdapter_minimal.ipynb`
- [ ] `02_T_opt_nanoSkillLibrary_minimal.ipynb`
- [ ] `02_T_opt_nanoTokenEfficientTools_minimal.ipynb`
- [ ] `02_T_opt_nanoToolLearningToy_minimal.ipynb`
- [ ] `02_T_opt_nanoToolSessionScaling_minimal.ipynb`

### 03_C
- [ ] `03_C_nanoContextWindow_minimal.ipynb`
- [ ] `03_C_nanoMemory_minimal.ipynb`
- [ ] `03_C_nanoLongHorizonCompaction_minimal.ipynb`
- [ ] `03_C_opt_nanoContextDriftBenchmark_minimal.ipynb`
- [ ] `03_C_opt_nanoGraphMemory_minimal.ipynb`
- [ ] `03_C_opt_nanoKVCacheAwareContext_minimal.ipynb`
- [ ] `03_C_opt_nanoProgressiveDisclosure_minimal.ipynb`
- [ ] `03_C_opt_nanoSubAgentContextIsolation_minimal.ipynb`

### 04_L
- [ ] `04_L_nanoReActLoop_minimal.ipynb`
- [ ] `04_L_nanoMultiAgent_minimal.ipynb`
- [ ] `04_L_nanoTaskRunnerLifecycle_minimal.ipynb`
- [ ] `04_L_opt_nanoCheckpointResume_minimal.ipynb`
- [ ] `04_L_opt_nanoGraphWorkflow_minimal.ipynb`
- [ ] `04_L_opt_nanoHumanHandoff_minimal.ipynb`
- [ ] `04_L_opt_nanoPlannerGeneratorEvaluator_minimal.ipynb`
- [ ] `04_L_opt_nanoStateModels_minimal.ipynb`

### 05_O
- [ ] `05_O_nanoCostTelemetry_minimal.ipynb`
- [ ] `05_O_nanoReliabilityOps_minimal.ipynb`
- [ ] `05_O_nanoTraceOps_minimal.ipynb`
- [ ] `05_O_opt_nanoCognitiveObservability_minimal.ipynb`
- [ ] `05_O_opt_nanoOpenTelemetryMini_minimal.ipynb`
- [ ] `05_O_opt_nanoOpsDashboard_minimal.ipynb`

### 06_V
- [ ] `06_V_nanoEvalHarness_minimal.ipynb`
- [ ] `06_V_nanoFailureAttribution_minimal.ipynb`
- [ ] `06_V_nanoRegressionSuite_minimal.ipynb`
- [ ] `06_V_opt_nanoHarnessAblationEval_minimal.ipynb`
- [ ] `06_V_opt_nanoInfraNoise_minimal.ipynb`
- [ ] `06_V_opt_nanoLLMJudgeCalibration_minimal.ipynb`
- [ ] `06_V_opt_nanoReadinessValidation_minimal.ipynb`

### 07_G
- [ ] `07_G_nanoGovernance_minimal.ipynb`
- [ ] `07_G_nanoPromptInjectionDefense_minimal.ipynb`
- [ ] `07_G_nanoAuditConstitution_minimal.ipynb`
- [ ] `07_G_opt_nanoComponentHardening_minimal.ipynb`
- [ ] `07_G_opt_nanoCredentialVault_minimal.ipynb`
- [ ] `07_G_opt_nanoFormalPolicyDSL_minimal.ipynb`
- [ ] `07_G_opt_nanoIdentityDelegation_minimal.ipynb`
- [ ] `07_G_opt_nanoInfoFlowControl_minimal.ipynb`

### 08_X
- [ ] `08_X_nanoFullHarness_minimal.ipynb`
- [ ] `08_X_nanoCostQualitySpeed_minimal.ipynb`
- [ ] `08_X_nanoHarnessCoupling_minimal.ipynb`
- [ ] `08_X_opt_nanoCapabilityControl_minimal.ipynb`
- [ ] `08_X_opt_nanoHarnessAsAssumption_minimal.ipynb`
- [ ] `08_X_opt_nanoLongRunStability_minimal.ipynb`
- [ ] `08_X_opt_nanoMetaHarnessSearch_minimal.ipynb`
- [ ] `08_X_opt_nanoSelfEvolution_minimal.ipynb`

### 09_capstone
- [ ] `09_capstone_nanoAgentPlatform_minimal.ipynb`

---

## 📄 开源协议 / License

本项目采用 [MIT License](LICENSE) 开源协议。  
This project is licensed under the [MIT License](LICENSE).
