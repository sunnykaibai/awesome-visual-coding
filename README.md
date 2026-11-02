# Awesome Visual Coding

A curated reading list for Visual Coding and Multimodal Code Intelligence: models that understand visual artifacts, generate executable programs, and improve through rendering, execution, and environment feedback.

The list is organized by the technical layer a paper contributes to, rather than by application domain. Web, UI, charts, SVG, CAD, 3D, documents, and animation appear throughout the same seven-layer framework.

## Contents

- [Latest Technical Reports and Releases](#latest-technical-reports-and-releases)
- [1. Tasks and Representations](#1-tasks-and-representations)
- [2. Data](#2-data)
- [3. Foundation Architectures and Pretraining](#3-foundation-architectures-and-pretraining)
- [4. Post-training](#4-post-training)
- [5. Feedback, Verifiers, and Reward Models](#5-feedback-verifiers-and-reward-models)
- [6. Execution Environments and Agents](#6-execution-environments-and-agents)
- [7. Evaluation](#7-evaluation)
- [Open Datasets and Resources](#open-datasets-and-resources)
- [Tools and Frameworks](#tools-and-frameworks)
- [Related Lists](#related-lists)
- [Contributing](#contributing)

## Latest Technical Reports and Releases

- [PrismaCoder: Pushing the Boundaries of Open Multimodal Code Intelligence through Decomposed Rubric Synthesis](https://arxiv.org/abs/2610.20538) — 2026. PrismaForge uses decomposed rubrics for both data filtering and RL; releases 9B/35B models and the PrismaCoder-2M dataset. [Data](https://huggingface.co/datasets/QiushiSun/PrismaCoder-2M)
- [MiMo-V2.6: Scaling Reinforcement Learning Towards Self-Improvement](https://arxiv.org/abs/2610.11959) — 2026. Covers multimodal mid-training, mixed agent environments, agentic grading, asynchronous RL, and reward-hacking defenses. The report releases RL training dynamics, environments, and framework; MiMo Visual Coding itself is an internal benchmark.
- [GLM-5V-Turbo: Toward a Native Foundation Model for Multimodal Agents](https://arxiv.org/abs/2604.26752) — 2026. Covers model design, multimodal training, hierarchical optimization, tool use, and end-to-end verification for multimodal coding and agents.
- [Seed2.1](https://seed.bytedance.com/zh/seed2_1) — 2026. Official model card covering visual inputs, interactive frontend generation, code engineering, debugging, and result verification. It is a model card rather than a detailed training report.
- [RAP: A Dataset for Paper-to-Poster Generation via Declarative Markup from Human-Crafted Exemplars](https://arxiv.org/abs/2610.23230) — 2026. Provides 25K+ verified paper–poster–HTML/CSS triplets, a held-out benchmark, PosterRAG, and an SFT+RL recipe. [Code](https://github.com/VincentHancoder/RAP) · [Data](https://huggingface.co/datasets/VincentHancoder/RAP)
- [Widget2Code: From Visual Widgets to UI Code via Multimodal LLMs](https://github.com/Djanghao/widget2code) — CVPR 2026 Highlight. Combines component decomposition, layout detection, icon retrieval, WidgetDSL, schema validation, compilation, and headless-browser rendering. The repository includes generation and evaluation tools and a link to the benchmark.

## 1. Tasks and Representations

How visual content becomes a program: direct code generation, DOM and layout trees, DSLs, component hierarchies, scene graphs, and executable intermediate representations.

- [Beyond NL2Code: A Structured Survey of Multimodal Code Intelligence](https://arxiv.org/abs/2606.15932) — TMLR 2026. A task map for visual reconstruction, editable structures, code-assisted reasoning, and tool use.
- [pix2code: Generating Code from a Graphical User Interface Screenshot](https://arxiv.org/abs/1705.07962) — EICS 2018. Early CNN+RNN screenshot-to-DSL generation for web and mobile interfaces. [Code](https://github.com/tonybeltramelli/pix2code)
- [StarVector: Generating Scalable Vector Graphics Code from Images and Text](https://arxiv.org/abs/2312.11556) — CVPR 2025. Direct SVG generation with SVG-Stack and SVG-Bench. [Code](https://github.com/joanrod/star-vector)
- [DeepCAD: A Deep Generative Network for Computer-Aided Design Models](https://arxiv.org/abs/2105.09492) — ICCV 2021. Represents CAD modeling histories as learnable command sequences. [Code/Data](https://github.com/rundiwu/DeepCAD)
- [CAD-Recode: Reverse Engineering CAD Code from Point Clouds](https://arxiv.org/abs/2412.14042) — ICCV 2025. Generates executable and editable CadQuery programs from point clouds. [Code](https://github.com/filaPro/cad-recode)
- [Chart Specification: Structural Representations for Incentivizing VLM Reasoning in Chart-to-Code Generation](https://arxiv.org/abs/2602.10880) — Neurocomputing 2026. Uses a structured chart representation for supervision, filtering, and fine-grained feedback.
- [What You See Is What You Get: Observation-Aligned Supervision for Chart-to-Code Generation](https://arxiv.org/abs/2607.04726) — 2026. Studies supervision targets that cannot actually be recovered from the rendered image.

Further reading: [Visual Programming](https://arxiv.org/abs/2211.11559), [ShapeCoder](https://arxiv.org/abs/2305.05661), [SceneScript](https://arxiv.org/abs/2403.13064).

## 2. Data

Real and synthetic image–code pairs, rendering verification, multi-object alignment, data filtering, multi-turn correction, diversity, and data mixtures.

- [WebSight: Unlocking the Conversion of Web Screenshots into HTML Code](https://arxiv.org/abs/2403.09029) — 2024. Approximately two million synthetic screenshot–HTML pairs. [Data](https://huggingface.co/datasets/HuggingFaceM4/WebSight)
- [WebCode2M: A Real-World Dataset for Code Generation from Webpage Designs](https://arxiv.org/abs/2404.06369) — WWW 2025. 2.56 million real-world design, code, and layout triplets. [Data](https://huggingface.co/datasets/xcodemind/webcode2m)
- [Web2Code: A Large-scale Webpage-to-Code Dataset and Evaluation Framework for Multimodal LLMs](https://arxiv.org/abs/2406.20098) — NeurIPS 2024 Datasets and Benchmarks. Joint webpage understanding, webpage-to-code training, and evaluation. [Code](https://github.com/MBZUAI-LLM/web2code)
- [PrismaCoder-2M](https://arxiv.org/abs/2610.20538) — 2026. A two-million-sample multimodal code corpus curated with per-instruction decomposed rubrics. The dataset page listed active uploading when checked; full availability should be rechecked before use. [Data](https://huggingface.co/datasets/QiushiSun/PrismaCoder-2M)
- [VisCoder2: Building Multi-Language Visualization Coding Agents](https://arxiv.org/abs/2510.23642) — ICLR 2026. VisCode-Multi-679K covers 12 programming languages and includes multi-turn self-debugging dialogues. [Code/Data](https://github.com/TIGER-AI-Lab/VisCoder2)
- [ChartNet: A Million-Scale, High-Quality Multimodal Dataset for Robust Chart Understanding](https://arxiv.org/abs/2603.27064) — CVPR 2026. Aligns plotting code, rendered charts, data tables, summaries, and reasoning QA across 1.5 million samples.
- [OmniSVG: A Unified Scalable Vector Graphics Generation Model](https://arxiv.org/abs/2504.06263) — NeurIPS 2025. Introduces MMSVG-2M and standardized SVG representations and evaluation. [Code/Data](https://github.com/OmniSVG/OmniSVG)
- [MathCoder-VL: Bridging Vision and Code for Enhanced Multimodal Mathematical Reasoning](https://arxiv.org/abs/2505.10557) — ACL 2025 Findings. Uses model-in-the-loop construction for ImgCode-8.6M and MM-MathInstruct-3M. [Code](https://github.com/mathllm/MathCoder)
- [CoSyn: Scaling Text-Rich Image Understanding via Code-Guided Synthetic Multimodal Data Generation](https://arxiv.org/abs/2502.14846) — ACL 2025. Generates 400K images and 2.7M instructions from executable code. [Code](https://github.com/allenai/pixmo-docs)

Further reading: [ChartGen](https://arxiv.org/abs/2507.19492), [CADFS](https://arxiv.org/abs/2605.01925), [RAP](https://arxiv.org/abs/2610.23230).

## 3. Foundation Architectures and Pretraining

Vision–language–code fusion, Code LLM initialization, high-resolution interfaces, spatial grounding, long programs, repository context, unified generation and editing, and general-capability retention.

- [VisCodex: Unified Multimodal Code Generation via Merging Vision and Coding Models](https://arxiv.org/abs/2508.09945) — ICLR 2026. Merges a Code LLM into a VLM using task vectors, followed by training on a 598K multimodal coding dataset. [Code](https://github.com/JackLingjie/VisCodex)
- [JanusCoder: Towards a Foundational Visual-Programmatic Interface for Code Intelligence](https://arxiv.org/abs/2510.23538) — ICLR 2026. A unified 7B–14B coder trained with the JanusCode-800K synthesis pipeline. [Code](https://github.com/InternLM/JanusCoder)
- [Qwen3-VL Technical Report](https://arxiv.org/abs/2511.21631) — 2025. Describes multimodal coding data and evaluates on Design2Code, ChartMimic, and UniSVG. [Code/Models](https://github.com/QwenLM/Qwen3-VL)
- [Kimi K2.5: Visual Agentic Intelligence](https://arxiv.org/abs/2602.02276) — 2026. Uses HTML, React, SVG, and rendered-image pairs in pretraining to align code structure with visual layout. [Code/Models](https://github.com/MoonshotAI/Kimi-K2.5)
- [GLM-4.5V and GLM-4.1V-Thinking: Towards Versatile Multimodal Reasoning with Scalable Reinforcement Learning](https://arxiv.org/abs/2507.01006) — 2025. Includes UI coding in instruction tuning and coding in RL. [Code/Models](https://github.com/zai-org/GLM-V)
- [GLM-5V-Turbo](https://arxiv.org/abs/2604.26752) — 2026. Integrates multimodal perception into reasoning, planning, tool use, and execution rather than treating vision as an auxiliary interface.
- [Seed2.1](https://seed.bytedance.com/zh/seed2_1) — 2026. Official model card connecting multimodal inputs, frontend generation, repository-scale engineering, and verification; detailed training data and mixtures are not disclosed.
- [MiMo-V2.6](https://arxiv.org/abs/2610.11959) — 2026. Uses multimodal mid-training to provide exploration space for subsequent large-scale, mixed-environment RL.

Further reading: [ChartCoder](https://arxiv.org/abs/2501.06598), [M2-Coder](https://arxiv.org/abs/2507.08719), [LLM4SVG](https://arxiv.org/abs/2412.11102).

## 4. Post-training

SFT, rejection and filtering strategies, preference optimization, online RL, multi-turn correction, and internalizing external feedback into the model.

- [UICoder: Finetuning Large Language Models to Generate User Interface Code through Automated Feedback](https://arxiv.org/abs/2406.07739) — NAACL 2024. Iteratively fine-tunes on model-generated UI code filtered by compilers and multimodal models.
- [Learning Only with Images: Visual Reinforcement Learning with Reasoning, Rendering, and Visual Feedback](https://arxiv.org/abs/2507.20766) — 2025. Uses rendering and visual comparison as rewards without reference-code supervision.
- [Breaking the SFT Plateau: Multimodal Structured Reinforcement Learning for Chart-to-Code Generation](https://arxiv.org/abs/2508.13587) — ICLR 2026. Uses three million chart–code pairs to study SFT saturation and combines code-level and rendering rewards.
- [UI2Code^N: UI-to-Code Generation as Interactive Visual Optimization](https://arxiv.org/abs/2511.08195) — ICML 2026. Combines continued pretraining, SFT, and RL with relative visual preference optimization for generation, editing, and refinement. [Code](https://github.com/zai-org/UI2Code_N)
- [VinciCoder: Unifying Multimodal Code Generation via Coarse-to-fine Visual Reinforcement Learning](https://arxiv.org/abs/2511.00391) — EMNLP 2026. Trains on 1.3M direct-generation and 300K visual-feedback editing samples before visual RL. [Code](https://github.com/DocTron-hub/VinciCoder)
- [ChartMaster: Advancing Chart-to-Code Generation with Real-World Charts and Chart Similarity Reinforcement Learning](https://arxiv.org/abs/2508.17608) — 2025. Combines chart-attribute and visual-feature similarity as rewards. [Code](https://github.com/WentaoTan/ChartMaster)
- [cadrille: Multi-modal CAD Reconstruction with Reinforcement Learning](https://arxiv.org/abs/2505.22914) — ICLR 2026 Oral. Applies SFT followed by online programmatic feedback across point-cloud, image, and text inputs. [Code](https://github.com/col14m/cadrille)

Further reading: [Text-to-CAD Generation Through Infusing Visual Feedback](https://arxiv.org/abs/2501.19054), [Thyme](https://arxiv.org/abs/2508.11630), [PrismaCoder](https://arxiv.org/abs/2610.20538).

## 5. Feedback, Verifiers, and Reward Models

Executable and structural rewards, visual similarity, functional tests, VLM critics, learned reward models, process supervision, and evaluation of the graders themselves.

- [Visual-ERM: Reward Modeling for Visual Equivalence](https://arxiv.org/abs/2603.13224) — 2026. Trains a fine-grained visual-equivalence reward model and introduces VC-RewardBench. [Code](https://github.com/InternLM/Visual-ERM)
- [UniCoder: Unified Visual-to-Code Generation via Symbolic Rewards and Reference-Guided Code Optimization](https://arxiv.org/abs/2606.31732) — 2026. Parses generated code into symbolic visual attributes for element-level rewards and uses reference-guided exploration.
- [WebGen-Agent: Enhancing Interactive Website Generation with Multi-Level Feedback and Step-Level Reinforcement Learning](https://arxiv.org/abs/2509.22644) — ICLR 2026. Combines VLM screenshot scores and GUI-agent functional tests for step-level RL. [Code](https://github.com/mnluzimu/WebGen-Agent)
- [ReLook: Vision-Grounded RL with a Multimodal LLM Critic for Agentic Web Coding](https://arxiv.org/abs/2510.11498) — ACL 2026. Uses an MLLM critic for generation, diagnosis, and revision, with explicit handling of rendering failures and non-improving edits.
- [PrismaCoder](https://arxiv.org/abs/2610.20538) — 2026. Uses the same decomposed rubric to filter supervised data and reward RL candidates.
- [ChartJudgeBench: Evaluating LMM Judges for Chart-to-Code Generation](https://arxiv.org/abs/2609.24210) — 2026. Measures position bias, over-acceptance, and other failure modes of LMM judges.
- [SVG-Score: Human-Aligned Evaluation of Text-to-SVG Generation](https://arxiv.org/abs/2609.03806) — 2026. Uses controlled perturbations to test whether CLIPScore and VLM judges notice color, count, and spatial errors.

Further reading: [MoVer](https://arxiv.org/abs/2502.13372), [SimuScene](https://arxiv.org/abs/2602.10840), [CodeV](https://arxiv.org/abs/2511.19661).

## 6. Execution Environments and Agents

Compilers, interpreters, renderers, browsers, IDEs, and design software; execution, observation, search, repair, tool generation, and trajectory collection.

- [MatPlotAgent: Method and Evaluation for LLM-Based Agentic Scientific Data Visualization](https://arxiv.org/abs/2402.11453) — ACL 2024 Findings. Combines query understanding, iterative debugging, and rendered-image feedback. [Code/Data](https://github.com/thunlp/MatPlotAgent)
- [DeTikZify: Synthesizing Graphics Programs for Scientific Figures and Sketches with TikZ](https://arxiv.org/abs/2405.15306) — NeurIPS 2024. Uses MCTS to search for and refine TikZ programs at inference time. [Code/Data](https://github.com/potamides/DeTikZify)
- [SceneCraft: An LLM Agent for Synthesizing 3D Scenes as Blender Code](https://arxiv.org/abs/2403.01248) — ICML 2024. Combines scene graphs, layout constraints, rendering checks, and a reusable function library.
- [ScreenCoder: Advancing Visual-to-Code Generation for Front-End Automation via Modular Multimodal Agents](https://arxiv.org/abs/2507.22827) — 2025. Uses grounding, planning, and generation agents as both a coding system and a data engine, followed by SFT and GRPO. [Code/Data](https://github.com/leigest519/ScreenCoder)
- [WebVIA: A Web-based Vision-Language Agentic Framework for Interactive and Verifiable UI-to-Code Generation](https://arxiv.org/abs/2511.06251) — 2025. Explores multiple UI states before generating and verifying interactive code. [Code](https://github.com/zheny2751-dotcom/WebVIA)
- [Rendering-in-the-Loop: An Execution-Driven Agent for Interactive Web Development](https://arxiv.org/abs/2609.02088) — 2026. Replays browser interactions, combines functional and visual feedback, and reuses execution-verified results for training.
- [Programming with Pixels: Can Computer-Use Agents do Software Engineering?](https://arxiv.org/abs/2502.18525) — ICLR 2026. Evaluates agents that operate VSCode using only screenshots, keyboard, and mouse input. [Project/Data](https://programmingwithpixels.com)
- [PlayCoder: Making LLM-Generated GUI Code Playable](https://arxiv.org/abs/2604.19742) — FSE 2026. Uses an automated playtester and Play@k to evaluate functional correctness rather than compilation alone. [Code](https://github.com/Tencent/PlayCoder)

Further reading: [GUIRepair](https://arxiv.org/abs/2506.16136), [HTMLCure](https://arxiv.org/abs/2605.26807), [PyVision](https://arxiv.org/abs/2507.07998).

## 7. Evaluation

Visual necessity, perception, structure, code correctness, visual fidelity, functionality, temporal behavior, repository-level performance, leakage, and metric reliability.

- [Design2Code: Benchmarking Multimodal Code Generation for Automated Front-End Engineering](https://arxiv.org/abs/2403.03163) — NAACL 2025. Provides 484 real webpages and Design2Code-HARD, with text, position, color, layout, and visual metrics. [Code/Data](https://github.com/NoviScl/Design2Code)
- [ChartMimic: Evaluating LMM's Cross-Modal Reasoning Capability via Chart-to-Code Generation](https://arxiv.org/abs/2406.09961) — ICLR 2025. Separates direct and customized reproduction and evaluates both code and rendering. [Code/Data](https://github.com/ChartMimic/ChartMimic)
- [HumanEval-V: Benchmarking High-Level Visual Reasoning with Complex Diagrams in Coding Tasks](https://arxiv.org/abs/2410.12381) — 2024. Uses image removal and human-written image descriptions to separate visual understanding from coding ability. [Code/Data](https://github.com/HumanEval-V/HumanEval-V-Benchmark)
- [Image2Struct: Benchmarking Structure Extraction for Vision-Language Models](https://arxiv.org/abs/2410.22456) — NeurIPS 2024 Datasets and Benchmarks. Re-renders HTML/CSS, LaTeX, and LilyPond outputs and uses newly uploaded content to reduce leakage. [Code/Data](https://github.com/stanford-crfm/image2struct)
- [SWE-bench Multimodal: Do AI Systems Generalize to Visual Software Domains?](https://arxiv.org/abs/2410.03859) — ICLR 2025. Contains 617 visual issue-resolution instances from 17 JavaScript repositories. [Code/Data](https://github.com/SWE-bench/SWE-bench)
- [WebGen-Bench: Evaluating LLMs on Generating Interactive and Functional Websites from Scratch](https://arxiv.org/abs/2505.03733) — NeurIPS 2025. Uses a web-navigation agent to execute 647 tests on multi-file websites; its inputs are textual requirements rather than visual references. [Code/Data](https://github.com/mnluzimu/WebGen-Bench)
- [IWR-Bench: Can LVLMs Reconstruct Interactive Webpages from a User Interaction Video?](https://arxiv.org/abs/2509.24709) — ICLR 2026. Separates visual fidelity and functional correctness across 113 tasks and 1,001 actions. [Code/Data](https://github.com/SIGMME/IWR-Bench)
- [Pattern over Pixels: Measuring Pattern Completion Bias in Multimodal Code Generation](https://arxiv.org/abs/2608.03691) — ASE 2026. Uses controlled screenshot perturbations to detect models that infer repeated patterns instead of reading pixels.
- [ArtifactsBench: Bridging the Visual-Interactive Gap in LLM Code Generation Evaluation](https://arxiv.org/abs/2507.04952) — 2025. Evaluates 1,825 interactive artifacts using multi-time screenshots, source code, rubrics, and human-preference comparisons. [Code/Data](https://github.com/Tencent-Hunyuan/ArtifactsBenchmark)

Further reading: [Vision2Code](https://arxiv.org/abs/2605.11307), [Animation2Code](https://arxiv.org/abs/2606.28593), [ChartJudgeBench](https://arxiv.org/abs/2609.24210), [SVG-Score](https://arxiv.org/abs/2609.03806).

## Open Datasets and Resources

This section distinguishes direct dataset links from papers that merely report constructing a dataset. A code repository or open model does not imply that training data is available.

| Resource | Contents | Availability note |
|---|---|---|
| [WebSight](https://huggingface.co/datasets/HuggingFaceM4/WebSight) | Approximately 2M screenshot–HTML pairs | Direct Hugging Face dataset |
| [WebCode2M](https://huggingface.co/datasets/xcodemind/webcode2m) | 2.56M real-web design, code, and layout triplets | Direct Hugging Face dataset |
| [PrismaCoder-2M](https://huggingface.co/datasets/QiushiSun/PrismaCoder-2M) | Multimodal code data reported at 2M scale | Dataset page and subsets exist; active uploading was noted when checked on 2026-11-02 |
| [RAP-25K](https://huggingface.co/datasets/VincentHancoder/RAP) | 25K+ paper–poster–HTML/CSS triplets | Public dataset entry; full download was not verified here |
| [Widget2Code](https://github.com/Djanghao/widget2code) | Widget benchmark, generation, rendering, and evaluation tools | Repository records the benchmark release on Hugging Face |
| [VisCoder2](https://github.com/TIGER-AI-Lab/VisCoder2) | VisCode-Multi-679K and multi-turn correction data | Project release; inspect repository files and licenses before training |
| [OmniSVG](https://github.com/OmniSVG/OmniSVG) | MMSVG-2M | Project release; inspect repository files and licenses before training |
| [ChartNet](https://arxiv.org/abs/2603.27064) | 1.5M chart, code, table, summary, and QA samples | Reported as released; a direct dataset page was not present in the source list |
| [ScreenCoder / ScreenBench](https://github.com/leigest519/ScreenCoder) | Agent data engine and a 1,000-website benchmark | ScreenBench is an evaluation set, not the full training corpus |
| [WebGen-Instruct](https://github.com/mnluzimu/WebGen-Bench) | 6,667 training instructions and 647 tests | Text instructions rather than image–code pairs |
| [MiMo-V2.6](https://arxiv.org/abs/2610.11959) | RL dynamics, environments, and framework | Released training resources; MiMo Visual Coding remains an internal benchmark |

## Tools and Frameworks

- [screenshot-to-code](https://github.com/abi/screenshot-to-code) — Generates HTML/Tailwind, React, Vue, and other frontend code from screenshots, mockups, designs, and recordings.
- [make-real](https://github.com/tldraw/make-real) — Turns tldraw sketches into interactive web prototypes using multimodal models.
- [OpenUI](https://github.com/wandb/openui) — Describes, renders, and iterates on UI code with support for multiple model providers.
- [bolt.diy](https://github.com/stackblitz-labs/bolt.diy) — Generates, runs, edits, and deploys full-stack web applications in a browser-based agent environment.

## Related Lists

- [Awesome Multimodal LLM for Code](https://github.com/xjywhu/Awesome-Multimodal-LLM-for-Code) — A broader companion list for multimodal code intelligence.

## Contributing

Suggestions are welcome. Open an issue or a pull request, and keep each entry concise. Include a primary paper or project link, the relevant technical layer, and direct code or data links when available. Clearly distinguish open weights, open code, open training data, evaluation-only data, and internal benchmarks.
