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
---

## 🚀 快速开始 / Quick Start

### 1. 环境准备 / Environment Setup
**[CN]** 克隆仓库并创建 Conda 环境：  
**[EN]** Clone the repository and set up a Conda environment:
```bash
git clone https://github.com/your-username/nano-Harness.git
cd nano-Harness
conda create -n nano-harness python=3.11 -y
conda activate nano-harness
pip install -r requirements.txt
```

### 2. 配置密钥 / Configure API Key
**[CN]** 在 `.env` 填入真实的 API 密钥  
**[EN]** Fill in your real API backend credentials in `.env` file

### 3. 打开并运行 / Launch & Run
**[CN]** 在 IDE (如 VS Code / Cursor / PyCharm) 或 Jupyter Lab 中打开 `notebooks/` 目录下的目标 `.ipynb` 文件，选择配置好的 Python 内核即可按顺序运行代码单元格。  
**[EN]** Open any `.ipynb` file in the `notebooks/` directory using your IDE (e.g., VS Code, Cursor, PyCharm) or Jupyter Lab, select the configured Python kernel, and execute the cells step-by-step.

---

## TODO

> **[CN]** 注：带 `opt` 标识的为可选与进阶模块，不带 `opt` 的为基础必修模块。  
> **[EN]** Note: Notebooks with the `opt` prefix are optional & advanced modules, while those without `opt` are core foundation modules.

### 00_core
- [x] `00_core_nanoProviderAdapter_minimal.ipynb`
- [x] `00_core_nanoMessageProtocol_minimal.ipynb`
- [x] `00_core_nanoToyEnv_minimal.ipynb`
- [x] `00_core_nanoAgentLoop_minimal.ipynb`

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

**[CN]** 本项目采用 [MIT License](LICENSE) 开源协议。  
**[EN]** This project is licensed under the [MIT License](LICENSE).
