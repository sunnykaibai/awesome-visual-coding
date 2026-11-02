# Awesome Visual Coding

[English](README.md) | **简体中文**

一份面向 Visual Coding 与多模态代码智能的精选阅读清单，关注能够理解视觉内容、生成可执行程序，并通过渲染、执行和环境反馈持续改进的模型。

清单按照论文贡献所属的技术层面组织，而不是按照应用领域划分。Web、UI、图表、SVG、CAD、3D、文档和动画都纳入同一个七层框架。

## 目录

- [最新技术报告与发布](#最新技术报告与发布)
- [WebDev 与 Coding Agent 研究](#webdev-与-coding-agent-研究)
- [1. 任务与表示](#1-任务与表示)
- [2. 数据](#2-数据)
- [3. 基座架构与预训练](#3-基座架构与预训练)
- [4. 后训练](#4-后训练)
- [5. 反馈、验证器与奖励模型](#5-反馈验证器与奖励模型)
- [6. 执行环境与 Agent](#6-执行环境与-agent)
- [7. 评测](#7-评测)
- [开放数据集与资源](#开放数据集与资源)
- [工具与框架](#工具与框架)
- [相关清单](#相关清单)
- [贡献指南](#贡献指南)

## 最新技术报告与发布

- [PrismaCoder: Pushing the Boundaries of Open Multimodal Code Intelligence through Decomposed Rubric Synthesis](https://arxiv.org/abs/2610.20538) — 2026。PrismaForge 将分解式评分细则同时用于数据过滤和强化学习；发布了 9B/35B 模型和 PrismaCoder-2M 数据集。[数据](https://huggingface.co/datasets/QiushiSun/PrismaCoder-2M)
- [MiMo-V2.6: Scaling Reinforcement Learning Towards Self-Improvement](https://arxiv.org/abs/2610.11959) — 2026。涵盖多模态中期训练、混合 Agent 环境、Agent 式评分、异步强化学习和奖励作弊防御。报告开放了强化学习训练动态、环境和框架；MiMo Visual Coding 本身是内部基准。
- [GLM-5V-Turbo: Toward a Native Foundation Model for Multimodal Agents](https://arxiv.org/abs/2604.26752) — 2026。涵盖模型设计、多模态训练、分层优化、工具使用，以及面向多模态 Coding 和 Agent 的端到端验证。
- [Seed2.1](https://seed.bytedance.com/zh/seed2_1) — 2026。官方模型卡，涵盖视觉输入、交互式前端生成、代码工程、调试和结果验证。它是模型卡，不是详细的训练报告。
- [RAP: A Dataset for Paper-to-Poster Generation via Declarative Markup from Human-Crafted Exemplars](https://arxiv.org/abs/2610.23230) — 2026。提供超过 25K 组经过验证的论文—海报—HTML/CSS 三元组、 held-out 基准、PosterRAG，以及 SFT+RL 训练方案。[代码](https://github.com/VincentHancoder/RAP) · [数据](https://huggingface.co/datasets/VincentHancoder/RAP)
- [Widget2Code: From Visual Widgets to UI Code via Multimodal LLMs](https://github.com/Djanghao/widget2code) — CVPR 2026 Highlight。结合组件分解、布局检测、图标检索、WidgetDSL、模式校验、编译和无头浏览器渲染。仓库包含生成与评测工具，并提供基准链接。

## WebDev 与 Coding Agent 研究

WebDev 的范围不止于截图转代码，还包括需求理解、全栈与多文件应用、仓库编辑、工具调用、长期项目状态、可执行测试、视觉反馈、调试和回归检查。以下论文按照这些能力组织，并明确区分纯文本输入、视觉反馈和视觉参考输入。

### 完整应用与持续演进的项目

- [WebCoder: Scaling General Frontend Development with Artifact-Grounded Agentic Reinforcement Learning](https://arxiv.org/abs/2610.23104) — 2026。Webdev-World 在编辑、执行、浏览器检查和技能调用之间保留项目状态；以产物进展为长时程强化学习分配信用。
- [EvoWeb: A Benchmark for Coding Agents on Evolving Web Applications](https://arxiv.org/abs/2610.16402) — 2026。包含 32 个应用上的 320 个累积需求，并在真实浏览器中评测新功能、跨需求集成和回归问题。
- [SWE-WebDevBench: Evaluating Coding Agent Application Platforms as Virtual Software Agencies](https://arxiv.org/abs/2605.04637) — 2026。从产品、工程和运维角色出发，评测应用的创建与修改，包括复杂 SaaS 和 AI 原生任务。
- [WebGen-Bench](https://arxiv.org/abs/2505.03733) — NeurIPS 2025。根据文本需求生成多文件网站，并执行 647 项测试。它是文本输入基准，不是视觉输入任务。[代码/数据](https://github.com/mnluzimu/WebGen-Bench)

### 视觉参考、交互与迭代修改

- [RefCraft: Benchmarking Visual-Reference-Conditioned Agentic Generation through Web Development](https://arxiv.org/abs/2610.26826) — 2026。结合自然语言指令与一至五个参考页面的截图，要求模型有选择地理解视觉信息，并进行渲染、检查和改进。
- [InterWebCoder: Learning Interactive Webpage Generation from Executable Tests via Reinforcement Learning](https://arxiv.org/abs/2610.28610) — 2026。从真实交互轨迹合成自包含页面和可执行测试，再通过 SFT 和 GRPO 优化测试通过率与状态级视觉相似度。
- [MT-Web2Code: Benchmarking Coding Agents on Multi-Turn Regional Reconstruction and Localized Modification](https://arxiv.org/abs/2608.03474) — 2026。测试区域重建和局部修改，同时要求保持未受影响的内容。论文称代码和数据将很快发布，因此这里不将其标记为已经开放。
- [Video2Code: Generating Interactive Webpages from UI Videos via Action-Aware Revisit](https://arxiv.org/abs/2606.20711) — 2026。重新查看与动作相关的视频片段，以恢复“状态—动作—状态”转换并生成交互式网页。
- [WebGen-Agent](https://arxiv.org/abs/2509.22644) — ICLR 2026。结合 VLM 截图评分、GUI Agent 功能测试和 Step-GRPO。初始输入是文本需求，截图用于提供反馈。
- [Rendering-in-the-Loop: An Execution-Driven Agent for Interactive Web Development](https://arxiv.org/abs/2609.02088) — 2026。重放浏览器交互，使用功能和视觉评分进行修复，并构建经过执行验证的训练数据。

### 验证、RLVR 与评测

- [WebGrader: Training LLMs for Web Development with Self-Evolving Programmatic Grader](https://arxiv.org/abs/2608.06474) — 2026。从需求中推导可执行的 Flow Contracts，并沿真实浏览器轨迹收集视觉、DOM、响应和持久状态证据。
- [WebUIProof: Benchmarking WebUI Code Generators with UI-Agent Execution Harness](https://arxiv.org/abs/2610.02617) — 2026。通过“规划—行动—观察”的 UI Agent 执行框架，提供 219 个任务和约 3,000 项可执行交互测试。
- [WebCraftBench: Evaluating Web Application Generation from a Software Testing Perspective](https://arxiv.org/abs/2609.15387) — 2026。使用插桩、覆盖率引导探索、状态抽象和独立评分，覆盖 369 项需求和 5,088 条验收标准。
- [The Verification Horizon: No Silver Bullet for Coding Agent Rewards](https://arxiv.org/abs/2606.26300) — 2026。从可扩展性、真实性和稳健性比较测试、评分细则、用户和 Agent 验证器，并主张验证机制必须与生成器共同演进。
- [Vision2Web: A Hierarchical Benchmark for Visual Website Development with Agent Verification](https://arxiv.org/abs/2603.26648) — 2026。涵盖静态 UI、交互式多页面前端和长时程全栈开发，包含 193 个任务和 1,255 项测试。[代码/数据](https://github.com/zai-org/Vision2Web)

### 仓库级视觉工程

- [SWE-bench Multimodal](https://arxiv.org/abs/2410.03859) — ICLR 2025。通过补丁和测试，解决真实 JavaScript 仓库中附带截图的 GitHub Issue。[代码/数据](https://github.com/SWE-bench/SWE-bench)
- [GUIRepair](https://arxiv.org/abs/2506.16136) — ASE 2025。在代码中复现视觉故障，并重新渲染修复后的应用，验证故障是否消失。
- [MM-IssueLoc](https://arxiv.org/abs/2607.15205) — 2026。在评测多模态仓库中的文件和函数定位时控制图像相关性；仅完成定位并不代表完成完整修复。
- [1D-Bench](https://arxiv.org/abs/2602.18548) — 2026。使用真实电商设计工作流、含噪中间表示、组件化 React 项目和迭代执行反馈。

## 1. 任务与表示

研究视觉内容如何转化为程序，包括直接代码生成、DOM 与布局树、DSL、组件层级、场景图和可执行中间表示。

- [Beyond NL2Code: A Structured Survey of Multimodal Code Intelligence](https://arxiv.org/abs/2606.15932) — TMLR 2026。梳理视觉重建、可编辑结构、代码辅助推理和工具使用的任务图谱。
- [pix2code: Generating Code from a Graphical User Interface Screenshot](https://arxiv.org/abs/1705.07962) — EICS 2018。早期使用 CNN+RNN 将 GUI 截图生成 DSL，面向 Web 和移动界面。[代码](https://github.com/tonybeltramelli/pix2code)
- [StarVector: Generating Scalable Vector Graphics Code from Images and Text](https://arxiv.org/abs/2312.11556) — CVPR 2025。直接生成 SVG，并提出 SVG-Stack 和 SVG-Bench。[代码](https://github.com/joanrod/star-vector)
- [DeepCAD: A Deep Generative Network for Computer-Aided Design Models](https://arxiv.org/abs/2105.09492) — ICCV 2021。将 CAD 建模历史表示为可学习的命令序列。[代码/数据](https://github.com/rundiwu/DeepCAD)
- [CAD-Recode: Reverse Engineering CAD Code from Point Clouds](https://arxiv.org/abs/2412.14042) — ICCV 2025。从点云生成可执行、可编辑的 CadQuery 程序。[代码](https://github.com/filaPro/cad-recode)
- [Chart Specification: Structural Representations for Incentivizing VLM Reasoning in Chart-to-Code Generation](https://arxiv.org/abs/2602.10880) — Neurocomputing 2026。使用结构化图表表示进行监督、过滤和细粒度反馈。
- [What You See Is What You Get: Observation-Aligned Supervision for Chart-to-Code Generation](https://arxiv.org/abs/2607.04726) — 2026。研究无法从渲染图像中实际恢复的监督目标。

延伸阅读：[Visual Programming](https://arxiv.org/abs/2211.11559)、[ShapeCoder](https://arxiv.org/abs/2305.05661)、[SceneScript](https://arxiv.org/abs/2403.13064)。

## 2. 数据

涵盖真实与合成的图像—代码对、渲染验证、多对象对齐、数据过滤、多轮纠错、多样性和数据配比。

- [WebSight: Unlocking the Conversion of Web Screenshots into HTML Code](https://arxiv.org/abs/2403.09029) — 2024。约 200 万组合成的截图—HTML 对。[数据](https://huggingface.co/datasets/HuggingFaceM4/WebSight)
- [WebCode2M: A Real-World Dataset for Code Generation from Webpage Designs](https://arxiv.org/abs/2404.06369) — WWW 2025。256 万组真实网页设计、代码和布局三元组。[数据](https://huggingface.co/datasets/xcodemind/webcode2m)
- [Web2Code: A Large-scale Webpage-to-Code Dataset and Evaluation Framework for Multimodal LLMs](https://arxiv.org/abs/2406.20098) — NeurIPS 2024 Datasets and Benchmarks。联合开展网页理解、网页转代码训练和评测。[代码](https://github.com/MBZUAI-LLM/web2code)
- [PrismaCoder-2M](https://arxiv.org/abs/2610.20538) — 2026。使用逐指令分解式评分细则筛选的 200 万条多模态代码语料。检查时数据集页面仍显示正在上传；使用前应重新确认完整数据是否可用。[数据](https://huggingface.co/datasets/QiushiSun/PrismaCoder-2M)
- [VisCoder2: Building Multi-Language Visualization Coding Agents](https://arxiv.org/abs/2510.23642) — ICLR 2026。VisCode-Multi-679K 覆盖 12 种编程语言，并包含多轮自我调试对话。[代码/数据](https://github.com/TIGER-AI-Lab/VisCoder2)
- [ChartNet: A Million-Scale, High-Quality Multimodal Dataset for Robust Chart Understanding](https://arxiv.org/abs/2603.27064) — CVPR 2026。在 150 万条样本中对齐绘图代码、渲染图表、数据表、摘要和推理问答。
- [OmniSVG: A Unified Scalable Vector Graphics Generation Model](https://arxiv.org/abs/2504.06263) — NeurIPS 2025。提出 MMSVG-2M，以及标准化的 SVG 表示和评测。[代码/数据](https://github.com/OmniSVG/OmniSVG)
- [MathCoder-VL: Bridging Vision and Code for Enhanced Multimodal Mathematical Reasoning](https://arxiv.org/abs/2505.10557) — ACL 2025 Findings。通过模型参与构建的方式生成 ImgCode-8.6M 和 MM-MathInstruct-3M。[代码](https://github.com/mathllm/MathCoder)
- [CoSyn: Scaling Text-Rich Image Understanding via Code-Guided Synthetic Multimodal Data Generation](https://arxiv.org/abs/2502.14846) — ACL 2025。从可执行代码生成 40 万张图像和 270 万条指令。[代码](https://github.com/allenai/pixmo-docs)

延伸阅读：[ChartGen](https://arxiv.org/abs/2507.19492)、[CADFS](https://arxiv.org/abs/2605.01925)、[RAP](https://arxiv.org/abs/2610.23230)。

## 3. 基座架构与预训练

涵盖视觉—语言—代码融合、Code LLM 初始化、高分辨率界面、空间定位、长程序、仓库上下文、统一生成与编辑，以及通用能力保持。

- [VisCodex: Unified Multimodal Code Generation via Merging Vision and Coding Models](https://arxiv.org/abs/2508.09945) — ICLR 2026。使用任务向量将 Code LLM 合并进 VLM，随后在 59.8 万条多模态 Coding 数据上训练。[代码](https://github.com/JackLingjie/VisCodex)
- [JanusCoder: Towards a Foundational Visual-Programmatic Interface for Code Intelligence](https://arxiv.org/abs/2510.23538) — ICLR 2026。通过 JanusCode-800K 合成流程训练统一的 7B–14B 代码模型。[代码](https://github.com/InternLM/JanusCoder)
- [Qwen3-VL Technical Report](https://arxiv.org/abs/2511.21631) — 2025。介绍多模态 Coding 数据，并在 Design2Code、ChartMimic 和 UniSVG 上评测。[代码/模型](https://github.com/QwenLM/Qwen3-VL)
- [Kimi K2.5: Visual Agentic Intelligence](https://arxiv.org/abs/2602.02276) — 2026。在预训练中使用 HTML、React、SVG 和渲染图像对，使代码结构与视觉布局对齐。[代码/模型](https://github.com/MoonshotAI/Kimi-K2.5)
- [GLM-4.5V and GLM-4.1V-Thinking: Towards Versatile Multimodal Reasoning with Scalable Reinforcement Learning](https://arxiv.org/abs/2507.01006) — 2025。在指令微调中加入 UI Coding，并在强化学习中加入 Coding。[代码/模型](https://github.com/zai-org/GLM-V)
- [GLM-5V-Turbo](https://arxiv.org/abs/2604.26752) — 2026。将多模态感知融入推理、规划、工具使用和执行，而不是把视觉仅作为辅助接口。
- [Seed2.1](https://seed.bytedance.com/zh/seed2_1) — 2026。官方模型卡将多模态输入、前端生成、仓库级工程和验证联系起来；未披露详细训练数据和配比。
- [MiMo-V2.6](https://arxiv.org/abs/2610.11959) — 2026。通过多模态中期训练，为后续大规模混合环境强化学习提供探索空间。

延伸阅读：[ChartCoder](https://arxiv.org/abs/2501.06598)、[M2-Coder](https://arxiv.org/abs/2507.08719)、[LLM4SVG](https://arxiv.org/abs/2412.11102)。

## 4. 后训练

涵盖 SFT、拒绝采样与过滤策略、偏好优化、在线强化学习、多轮纠错，以及将外部反馈内化到模型中。

- [UICoder: Finetuning Large Language Models to Generate User Interface Code through Automated Feedback](https://arxiv.org/abs/2406.07739) — NAACL 2024。通过编译器和多模态模型过滤模型生成的 UI 代码，并进行迭代微调。
- [Learning Only with Images: Visual Reinforcement Learning with Reasoning, Rendering, and Visual Feedback](https://arxiv.org/abs/2507.20766) — 2025。在没有参考代码监督的情况下，将渲染和视觉比较作为奖励。
- [Breaking the SFT Plateau: Multimodal Structured Reinforcement Learning for Chart-to-Code Generation](https://arxiv.org/abs/2508.13587) — ICLR 2026。使用 300 万组图表—代码对研究 SFT 饱和，并结合代码级奖励和渲染奖励。
- [UI2Code^N: UI-to-Code Generation as Interactive Visual Optimization](https://arxiv.org/abs/2511.08195) — ICML 2026。结合持续预训练、SFT 和强化学习，通过相对视觉偏好优化完成生成、编辑和改进。[代码](https://github.com/zai-org/UI2Code_N)
- [VinciCoder: Unifying Multimodal Code Generation via Coarse-to-fine Visual Reinforcement Learning](https://arxiv.org/abs/2511.00391) — EMNLP 2026。在视觉强化学习之前，使用 130 万条直接生成样本和 30 万条视觉反馈编辑样本进行训练。[代码](https://github.com/DocTron-hub/VinciCoder)
- [ChartMaster: Advancing Chart-to-Code Generation with Real-World Charts and Chart Similarity Reinforcement Learning](https://arxiv.org/abs/2508.17608) — 2025。将图表属性和视觉特征相似度结合为奖励。[代码](https://github.com/WentaoTan/ChartMaster)
- [cadrille: Multi-modal CAD Reconstruction with Reinforcement Learning](https://arxiv.org/abs/2505.22914) — ICLR 2026 Oral。先进行 SFT，再在点云、图像和文本输入上应用在线程序化反馈。[代码](https://github.com/col14m/cadrille)

延伸阅读：[Text-to-CAD Generation Through Infusing Visual Feedback](https://arxiv.org/abs/2501.19054)、[Thyme](https://arxiv.org/abs/2508.11630)、[PrismaCoder](https://arxiv.org/abs/2610.20538)。

## 5. 反馈、验证器与奖励模型

涵盖可执行与结构化奖励、视觉相似度、功能测试、VLM 评价模型、学习型奖励模型、过程监督，以及对评分器自身的评测。

- [Visual-ERM: Reward Modeling for Visual Equivalence](https://arxiv.org/abs/2603.13224) — 2026。训练细粒度视觉等价奖励模型，并提出 VC-RewardBench。[代码](https://github.com/InternLM/Visual-ERM)
- [UniCoder: Unified Visual-to-Code Generation via Symbolic Rewards and Reference-Guided Code Optimization](https://arxiv.org/abs/2606.31732) — 2026。将生成代码解析为符号化视觉属性，用于元素级奖励，并采用参考引导探索。
- [WebGen-Agent: Enhancing Interactive Website Generation with Multi-Level Feedback and Step-Level Reinforcement Learning](https://arxiv.org/abs/2509.22644) — ICLR 2026。结合 VLM 截图评分和 GUI Agent 功能测试进行步骤级强化学习。[代码](https://github.com/mnluzimu/WebGen-Agent)
- [ReLook: Vision-Grounded RL with a Multimodal LLM Critic for Agentic Web Coding](https://arxiv.org/abs/2510.11498) — ACL 2026。使用多模态 LLM 评价模型进行生成、诊断和修改，并显式处理渲染失败和没有改进的编辑。
- [PrismaCoder](https://arxiv.org/abs/2610.20538) — 2026。使用同一套分解式评分细则过滤监督数据，并为强化学习候选结果提供奖励。
- [ChartJudgeBench: Evaluating LMM Judges for Chart-to-Code Generation](https://arxiv.org/abs/2609.24210) — 2026。衡量 LMM 评价模型的位置偏差、过度接受和其他失效模式。
- [SVG-Score: Human-Aligned Evaluation of Text-to-SVG Generation](https://arxiv.org/abs/2609.03806) — 2026。使用受控扰动，检验 CLIPScore 和 VLM 评价模型能否发现颜色、数量和空间错误。

延伸阅读：[MoVer](https://arxiv.org/abs/2502.13372)、[SimuScene](https://arxiv.org/abs/2602.10840)、[CodeV](https://arxiv.org/abs/2511.19661)。

## 6. 执行环境与 Agent

涵盖编译器、解释器、渲染器、浏览器、IDE 和设计软件，以及执行、观察、搜索、修复、工具生成和轨迹采集。

- [MatPlotAgent: Method and Evaluation for LLM-Based Agentic Scientific Data Visualization](https://arxiv.org/abs/2402.11453) — ACL 2024 Findings。结合查询理解、迭代调试和渲染图像反馈。[代码/数据](https://github.com/thunlp/MatPlotAgent)
- [DeTikZify: Synthesizing Graphics Programs for Scientific Figures and Sketches with TikZ](https://arxiv.org/abs/2405.15306) — NeurIPS 2024。在推理时使用 MCTS 搜索并改进 TikZ 程序。[代码/数据](https://github.com/potamides/DeTikZify)
- [SceneCraft: An LLM Agent for Synthesizing 3D Scenes as Blender Code](https://arxiv.org/abs/2403.01248) — ICML 2024。结合场景图、布局约束、渲染检查和可复用函数库。
- [ScreenCoder: Advancing Visual-to-Code Generation for Front-End Automation via Modular Multimodal Agents](https://arxiv.org/abs/2507.22827) — 2025。将定位、规划和生成 Agent 同时用作 Coding 系统和数据引擎，随后进行 SFT 和 GRPO。[代码/数据](https://github.com/leigest519/ScreenCoder)
- [WebVIA: A Web-based Vision-Language Agentic Framework for Interactive and Verifiable UI-to-Code Generation](https://arxiv.org/abs/2511.06251) — 2025。在生成和验证交互代码之前探索多个 UI 状态。[代码](https://github.com/zheny2751-dotcom/WebVIA)
- [Rendering-in-the-Loop: An Execution-Driven Agent for Interactive Web Development](https://arxiv.org/abs/2609.02088) — 2026。重放浏览器交互，结合功能与视觉反馈，并将经过执行验证的结果复用于训练。
- [Programming with Pixels: Can Computer-Use Agents do Software Engineering?](https://arxiv.org/abs/2502.18525) — ICLR 2026。评测仅使用截图、键盘和鼠标操作 VSCode 的 Agent。[项目/数据](https://programmingwithpixels.com)
- [PlayCoder: Making LLM-Generated GUI Code Playable](https://arxiv.org/abs/2604.19742) — FSE 2026。使用自动试玩器和 Play@k 评测功能正确性，而不只检查能否编译。[代码](https://github.com/Tencent/PlayCoder)

延伸阅读：[GUIRepair](https://arxiv.org/abs/2506.16136)、[HTMLCure](https://arxiv.org/abs/2605.26807)、[PyVision](https://arxiv.org/abs/2507.07998)。

## 7. 评测

涵盖视觉必要性、感知、结构、代码正确性、视觉还原度、功能性、时序行为、仓库级表现、数据泄漏和指标可靠性。

- [Design2Code: Benchmarking Multimodal Code Generation for Automated Front-End Engineering](https://arxiv.org/abs/2403.03163) — NAACL 2025。提供 484 个真实网页和 Design2Code-HARD，并使用文本、位置、颜色、布局和视觉指标。[代码/数据](https://github.com/NoviScl/Design2Code)
- [ChartMimic: Evaluating LMM's Cross-Modal Reasoning Capability via Chart-to-Code Generation](https://arxiv.org/abs/2406.09961) — ICLR 2025。区分直接复现和定制复现，同时评测代码和渲染结果。[代码/数据](https://github.com/ChartMimic/ChartMimic)
- [HumanEval-V: Benchmarking High-Level Visual Reasoning with Complex Diagrams in Coding Tasks](https://arxiv.org/abs/2410.12381) — 2024。通过移除图像和使用人工撰写的图像描述，区分视觉理解能力与 Coding 能力。[代码/数据](https://github.com/HumanEval-V/HumanEval-V-Benchmark)
- [Image2Struct: Benchmarking Structure Extraction for Vision-Language Models](https://arxiv.org/abs/2410.22456) — NeurIPS 2024 Datasets and Benchmarks。重新渲染 HTML/CSS、LaTeX 和 LilyPond 输出，并使用新上传内容减少数据泄漏。[代码/数据](https://github.com/stanford-crfm/image2struct)
- [SWE-bench Multimodal: Do AI Systems Generalize to Visual Software Domains?](https://arxiv.org/abs/2410.03859) — ICLR 2025。包含来自 17 个 JavaScript 仓库的 617 个视觉 Issue 修复实例。[代码/数据](https://github.com/SWE-bench/SWE-bench)
- [WebGen-Bench: Evaluating LLMs on Generating Interactive and Functional Websites from Scratch](https://arxiv.org/abs/2505.03733) — NeurIPS 2025。使用 Web 导航 Agent 对多文件网站执行 647 项测试；输入是文本需求，不是视觉参考。[代码/数据](https://github.com/mnluzimu/WebGen-Bench)
- [IWR-Bench: Can LVLMs Reconstruct Interactive Webpages from a User Interaction Video?](https://arxiv.org/abs/2509.24709) — ICLR 2026。在 113 个任务和 1,001 个动作上分别评测视觉还原度和功能正确性。[代码/数据](https://github.com/SIGMME/IWR-Bench)
- [Pattern over Pixels: Measuring Pattern Completion Bias in Multimodal Code Generation](https://arxiv.org/abs/2608.03691) — ASE 2026。使用受控截图扰动，检测模型是否依赖重复模式推断而非读取像素。
- [ArtifactsBench: Bridging the Visual-Interactive Gap in LLM Code Generation Evaluation](https://arxiv.org/abs/2507.04952) — 2025。使用多时间点截图、源代码、评分细则和人类偏好比较，评测 1,825 个交互式产物。[代码/数据](https://github.com/Tencent-Hunyuan/ArtifactsBenchmark)

延伸阅读：[Vision2Code](https://arxiv.org/abs/2605.11307)、[Animation2Code](https://arxiv.org/abs/2606.28593)、[ChartJudgeBench](https://arxiv.org/abs/2609.24210)、[SVG-Score](https://arxiv.org/abs/2609.03806)。

## 开放数据集与资源

本节区分可直接访问的数据集链接与仅在论文中报告构建了数据集的工作。开放代码仓库或模型并不意味着训练数据也已开放。

| 资源 | 内容 | 可用性说明 |
|---|---|---|
| [WebSight](https://huggingface.co/datasets/HuggingFaceM4/WebSight) | 约 200 万组截图—HTML 对 | Hugging Face 数据集直链 |
| [WebCode2M](https://huggingface.co/datasets/xcodemind/webcode2m) | 256 万组真实网页设计、代码和布局三元组 | Hugging Face 数据集直链 |
| [PrismaCoder-2M](https://huggingface.co/datasets/QiushiSun/PrismaCoder-2M) | 报告规模为 200 万条的多模态代码数据 | 数据集页面和子集已存在；2026-11-02 检查时仍显示正在上传 |
| [RAP-25K](https://huggingface.co/datasets/VincentHancoder/RAP) | 超过 25K 组论文—海报—HTML/CSS 三元组 | 公开数据集入口；此处未验证完整下载 |
| [Widget2Code](https://github.com/Djanghao/widget2code) | Widget 基准、生成、渲染和评测工具 | 仓库记录了 Hugging Face 上的基准发布 |
| [VisCoder2](https://github.com/TIGER-AI-Lab/VisCoder2) | VisCode-Multi-679K 和多轮纠错数据 | 项目发布；训练前检查仓库文件和许可证 |
| [OmniSVG](https://github.com/OmniSVG/OmniSVG) | MMSVG-2M | 项目发布；训练前检查仓库文件和许可证 |
| [ChartNet](https://arxiv.org/abs/2603.27064) | 150 万条图表、代码、表格、摘要和问答样本 | 论文报告已经发布；来源清单中没有数据集直链 |
| [ScreenCoder / ScreenBench](https://github.com/leigest519/ScreenCoder) | Agent 数据引擎和包含 1,000 个网站的基准 | ScreenBench 是评测集，不是完整训练语料 |
| [WebGen-Instruct](https://github.com/mnluzimu/WebGen-Bench) | 6,667 条训练指令和 647 项测试 | 文本指令，不是图像—代码对 |
| [MiMo-V2.6](https://arxiv.org/abs/2610.11959) | 强化学习动态、环境和框架 | 已发布训练资源；MiMo Visual Coding 仍是内部基准 |

## 工具与框架

- [screenshot-to-code](https://github.com/abi/screenshot-to-code) — 从截图、线框图、设计稿和录屏生成 HTML/Tailwind、React、Vue 等前端代码。
- [make-real](https://github.com/tldraw/make-real) — 使用多模态模型将 tldraw 草图转化为交互式 Web 原型。
- [OpenUI](https://github.com/wandb/openui) — 描述、渲染和迭代 UI 代码，支持多个模型提供商。
- [bolt.diy](https://github.com/stackblitz-labs/bolt.diy) — 在浏览器 Agent 环境中生成、运行、编辑和部署全栈 Web 应用。

## 相关清单

- [Awesome Multimodal LLM for Code](https://github.com/xjywhu/Awesome-Multimodal-LLM-for-Code) — 覆盖范围更广的多模态代码智能配套清单。

## 贡献指南

欢迎通过 Issue 或 Pull Request 提出建议，并保持每个条目简洁。请附上主要论文或项目链接、相关技术层面，以及可用时的代码或数据直链。明确区分开放权重、开放代码、开放训练数据、仅用于评测的数据和内部基准。
