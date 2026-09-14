# 机器人上下文学习 — 论文目录

[主页](README.md) · [English](README_EN.md)

按类别整理机器人上下文学习（ICL）、上下文模仿学习（ICIL）及相关适应方法的公开论文。

最后核对：**2026-09-15** · **28 篇论文**。年份采用 arXiv 首次提交年份，可能与会议年份不同；标题采用所链接的 arXiv 记录。各类别内按年份排序。本目录为精选阅读列表，不是穷尽性综述或性能排名。

**范围说明。** 区分固定策略权重下的示范条件执行与基于梯度的适应。元训练发生在部署之前，并不意味着测试时更新参数。“测试时适应与长上下文记忆”单独收录更新权重的方法；通用强化学习及多模态基础工作作为相关文献收录，不视为机器人 ICIL 实验结果。分类依据主要接口，允许交叉：人类视频策略也可能采用 VLA。

每个条目提供原论文，以及已核实的作者项目页或仓库链接。仓库链接不代表已经提供完整可运行版本，请查看其发布状态。未列附加链接表示本目录尚未核实对应资源。

## 目录

- [基于 LLM/VLM 的机器人上下文学习](#llm-icl)
- [机器人原生 ICIL 与元训练策略](#robot-native)
- [基于 VLA/VLM 的 ICL 与多模态提示](#vla-icl)
- [人类视频与跨形态上下文学习](#human-video)
- [测试时适应与长上下文记忆](#adaptation-memory)
- [多模态上下文学习基础](#multimodal-foundations)

<a id="llm-icl"></a>

## 基于 LLM/VLM 的机器人上下文学习

### Code as Policies · 2022

**[Code as Policies: Language Model Programs for Embodied Control](https://arxiv.org/abs/2209.07753)**

通过策略代码示例提示语言模型，将语言指令转为可执行机器人程序；属于程序层面的提示方法，与直接感知运动 ICIL 相关但有所区别。

[项目](https://code-as-policies.github.io/) · [仓库](https://github.com/google-research/google-research/tree/master/code_as_policies)

### KAT · 2024

**[Keypoint Action Tokens Enable In-Context Imitation Learning in Robotics](https://arxiv.org/abs/2403.19578)**

将视觉关键点和动作轨迹转换为文本 token，让冻结的文本预训练 Transformer 根据示范预测机器人运动。

[项目](https://www.robot-learning.uk/keypoint-action-tokens)

### RoboPrompt · 2024

**[In-Context Learning Enables Robot Action Prediction in LLMs](https://arxiv.org/abs/2410.12782)**

将初始物体位姿和关键帧末端动作转换为文本示例，使用现成 LLM 进行机器人动作预测。

[项目](https://davidyyd.github.io/roboprompt/) · [仓库](https://github.com/davidyyd/roboprompt)

### BiCICLe · 2026

**[Bimanual Robot Manipulation via Multi-Agent In-Context Learning](https://arxiv.org/abs/2604.20348)**

以结构化空间示范作为上下文，通过协调的主从 LLM 智能体生成双臂操作轨迹。

<a id="robot-native"></a>

## 机器人原生 ICIL 与元训练策略

### One-Shot Imitation Learning · 2017

**[One-Shot Imitation Learning](https://arxiv.org/abs/1703.07326)**

元训练以示范为条件的策略，使其能够从单个示范执行新任务，实验包括仿真积木堆叠。

[项目](https://openai.com/index/robots-that-learn/)

### MOSAIC · 2021

**[Towards More Generalizable One-shot Visual Imitation Learning](https://arxiv.org/abs/2110.13423)**

结合自注意力与时序对比学习进行多任务单次视觉模仿，分别评估示范条件执行及新任务微调。

[仓库](https://github.com/rll-research/mosaic)

### ICRT · 2024

**[In-Context Imitation Learning via Next-Token Prediction](https://arxiv.org/abs/2408.15980)**

自回归建模图像、状态和动作轨迹，通过遥操作示范提示新行为，无需针对目标任务更新参数。

[项目](https://icrt.dev/) · [仓库](https://github.com/Max-Fu/icrt)

### Instant Policy · 2024

**[Instant Policy: In-Context Imitation Learning via Graph Diffusion](https://arxiv.org/abs/2411.12633)**

将示范、观测和动作表示为图，通过图扩散生成动作，并使用仿真伪示范训练。

[项目](https://www.robot-learning.uk/instant-policy) · [仓库](https://github.com/vv19/instant_policy)

### RoboSSM · 2025

**[RoboSSM: Scalable In-context Imitation Learning via State-Space Models](https://arxiv.org/abs/2509.19658)**

使用状态空间模型进行示范条件模仿，研究长提示及不同示范数量下的泛化。

[仓库](https://github.com/youngjuY/RoboSSM)

### ICLR · 2026

**[ICLR: In-Context Imitation Learning with Visual Reasoning](https://arxiv.org/abs/2603.07530)**

在示范提示中加入图像空间的未来轨迹表示，联合预测视觉推理轨迹与底层动作。

[项目](https://toannguyen1904.github.io/ICLR)

### SynthICL · 2026

**[SynthICL: Scalable In-context Imitation Learning with Synthetic Data](https://arxiv.org/abs/2606.08154)**

使用合成数据和子目标图像预测训练仅输入 RGB 的流匹配 ICIL 策略，在真实任务中以单个示范为条件执行。

[项目](https://synth-icl.github.io/)

### BPP · 2026

**[Behavior Prompting Policy: Demonstrations as Prompts for Manipulation](https://arxiv.org/abs/2606.30457)**

以行为示范和当前观测为条件生成动作，提出 iPhUMI 采集接口及 DrawAnything、LIBERO-Gen 评测。

[项目](https://behavior-prompting.github.io/) · [仓库](https://github.com/real-stanford/behavior_prompting)

<a id="vla-icl"></a>

## 基于 VLA/VLM 的 ICL 与多模态提示

### VIMA · 2022

**[VIMA: General Robot Manipulation with Multimodal Prompts](https://arxiv.org/abs/2210.03094)**

使用视觉与文本交错提示指定操作任务，包括视觉目标和示范，是相关的多模态提示策略。

[项目](https://vimalabs.github.io/) · [仓库](https://github.com/vimalabs/VIMA)

### RICL · 2025

**[RICL: Adding In-Context Adaptability to Pre-Trained Vision-Language-Action Models](https://arxiv.org/abs/2508.02062)**

对预训练 VLA 进行上下文适应后训练，在推理时检索相关示范片段；另行评估目标任务微调设置。

[项目](https://ricl-vla.github.io/) · [仓库](https://github.com/ricl-vla/ricl_openpi)

### SeeTraceAct · 2026

**[SeeTraceAct: Visibility-Aware Latent Planning from Cross-Embodiment Demonstration Videos](https://arxiv.org/abs/2606.02745)**

使用示范视频作为 VLA 的条件，并在训练时预测具有可见性信息的未来末端轨迹，以加强空间定位。

[项目](https://jaehyeon-son.github.io/seetraceact/) · [仓库](https://github.com/jaehyeon-son/SeeTraceAct)

### StellaVLA · 2026

**[StellaVLA: In-Context Structured Demonstration for Generalizable Vision-Language-Action Models](https://arxiv.org/abs/2608.11671)**

将轨迹转换为包含计划、子目标和语言化运动信息的结构化示范，在测试时以检索到的示范作为 VLA 上下文。

[项目](https://www.stelledge.com/blog/stellavla)

<a id="human-video"></a>

## 人类视频与跨形态上下文学习

### Vid2Robot · 2024

**[Vid2Robot: End-to-end Video-conditioned Policy Learning with Cross-Attention Transformers](https://arxiv.org/abs/2403.12943)**

从提示视频与机器人轨迹配对数据中学习视频条件策略，通过交叉注意力和对比学习对齐人类与机器人视频。

[项目](https://vid2robot.github.io/)

### ViVLA · 2025

**[See Once, Then Act: Vision-Language-Action Model with Task Learning from One-Shot Video Demonstrations](https://arxiv.org/abs/2512.07582)**

联合处理单个专家示范视频和当前机器人观测以预测动作，使用包含人类视频合成配对在内的专家—执行者数据训练。

### HOST · 2026

**[HOST:Robots Acquire Manipulation Skills in Seconds from a Single Human Video](https://arxiv.org/abs/2607.20033)**

对齐机器人进度与人类示范，预测机器人视角的未来观测，再生成动作，在推理时从单段视频获取技能。

[项目](https://host-site.host-robotics.workers.dev/) · [仓库](https://github.com/CGuangyan-BIT/HOST)

### Zero-WAM · 2026

**[Zero-WAM: In-Context World-Action Modeling from Human Videos for Open-Ended Task Generalization](https://arxiv.org/abs/2608.26103)**

以人类视频提示作为因果视频动作模型的条件来执行未见任务，提出 HumanGen 配对数据及上下文未来片段预测目标。

[项目](https://robbyant-research.github.io/Zero-WAM/) · [仓库](https://github.com/robbyant-research/Zero-WAM)

<a id="adaptation-memory"></a>

## 测试时适应与长上下文记忆

### Meta-imitation learning · 2017

**[One-Shot Visual Imitation Learning via Meta-Learning](https://arxiv.org/abs/1709.04905)**

元学习视觉运动策略的初始化，使其通过梯度更新从单个示范适应任务；属于少样本适应前驱工作，而非固定权重 ICL。

[项目](https://sites.google.com/view/one-shot-imitation) · [仓库](https://github.com/tianheyu927/mil)

### Domain-adaptive meta-learning · 2018

**[One-Shot Imitation from Observing Humans via Domain-Adaptive Meta-Learning](https://arxiv.org/abs/1802.01557)**

学习适应目标，通过梯度适应将人类视频迁移为机器人策略，处理形态差异。

### Algorithm Distillation · 2022

**[In-context Reinforcement Learning with Algorithm Distillation](https://arxiv.org/abs/2210.14215)**

在强化学习历史上训练因果序列模型，使策略通过上下文改善而无需更新网络参数；属于通用强化学习基础工作。

### TTT layers · 2024

**[Learning to (Learn at Test Time): RNNs with Expressive Hidden States](https://arxiv.org/abs/2407.04620)**

将循环隐状态表示为小型模型，其权重在推理时通过自监督学习更新；为参数化记忆提供序列建模基础。

[仓库](https://github.com/test-time-training/ttt-lm-pytorch)

### RoboTTT · 2026

**[RoboTTT: Context Scaling for Robot Policies](https://arxiv.org/abs/2607.15275)**

在机器人策略中加入测试时训练层，支持长感知运动历史和视频提示；推理期间会对快速权重进行梯度更新。

[项目](https://research.nvidia.com/labs/gear/robottt/)

<a id="multimodal-foundations"></a>

## 多模态上下文学习基础

### Flamingo · 2022

**[Flamingo: a Visual Language Model for Few-Shot Learning](https://arxiv.org/abs/2204.14198)**

通过交错的视觉与文本示例支持少样本图像和视频任务，为多模态上下文学习提供架构基础。

[项目](https://deepmind.google/blog/tackling-multiple-tasks-with-a-single-visual-language-model/)

### OpenFlamingo · 2023

**[OpenFlamingo: An Open-Source Framework for Training Large Autoregressive Vision-Language Models](https://arxiv.org/abs/2308.01390)**

提供开源框架及模型，在交错图文上下文中进行自回归视觉语言学习。

[仓库](https://github.com/mlfoundations/open_flamingo)

### MMICL · 2023

**[MMICL: Empowering Vision-language Model with Multi-Modal In-Context Learning](https://arxiv.org/abs/2309.07915)**

提出多模态上下文格式与 MIC 数据集，提升对多图提示及多模态上下文示例的理解。

[仓库](https://github.com/PKUnlp-icler/MIC)
