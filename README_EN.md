# Robotics In-Context Learning — Paper List

[Home](README.md) · [中文](README_CN.md)

A categorized reading list of public papers on robotic in-context learning (ICL), in-context imitation learning (ICIL), and closely related adaptation methods.

Last checked: **2026-09-15** · **28 papers**. Years refer to the first arXiv submission, which may differ from the conference year; titles follow the linked arXiv record. Entries are ordered by year within each category. This is a curated list, not an exhaustive survey or performance ranking.

**Scope.** Demonstration-conditioned execution with fixed policy weights is distinguished from gradient-based adaptation. Meta-training happens before deployment and does not by itself imply test-time updates. The adaptation/memory section explicitly includes methods that update weights; general RL and multimodal foundations are labeled as related work rather than robot ICIL results. Categories describe the main interface and can overlap: human-video policies may also be VLAs.

Each entry links to its source paper and, where verified, an author project or repository. A repository link does not imply a complete runnable release; consult its release status. Omitted auxiliary links mean none was verified for this list.

## Contents

- [LLM/VLM-based robotic ICL](#llm-icl)
- [Robot-native ICIL and meta-trained policies](#robot-native)
- [VLA/VLM-based ICL and multimodal prompting](#vla-icl)
- [Human-video and cross-embodiment ICL](#human-video)
- [Test-time adaptation and long-context memory](#adaptation-memory)
- [Multimodal ICL foundations](#multimodal-foundations)

<a id="llm-icl"></a>

## LLM/VLM-based robotic ICL

### Code as Policies · 2022

**[Code as Policies: Language Model Programs for Embodied Control](https://arxiv.org/abs/2209.07753)**

Uses examples of policy code to prompt language models to compose executable robot programs from language instructions; related program-level prompting rather than direct sensorimotor ICIL.

[Project](https://code-as-policies.github.io/) · [Repository](https://github.com/google-research/google-research/tree/master/code_as_policies)

### KAT · 2024

**[Keypoint Action Tokens Enable In-Context Imitation Learning in Robotics](https://arxiv.org/abs/2403.19578)**

Tokenizes visual keypoints and action trajectories so a frozen text-pretrained transformer can predict robot motions from demonstrations.

[Project](https://www.robot-learning.uk/keypoint-action-tokens)

### RoboPrompt · 2024

**[In-Context Learning Enables Robot Action Prediction in LLMs](https://arxiv.org/abs/2410.12782)**

Converts initial object poses and keyframe end-effector actions into textual examples for robot action prediction with an off-the-shelf LLM.

[Project](https://davidyyd.github.io/roboprompt/) · [Repository](https://github.com/davidyyd/roboprompt)

### BiCICLe · 2026

**[Bimanual Robot Manipulation via Multi-Agent In-Context Learning](https://arxiv.org/abs/2604.20348)**

Uses structured spatial demonstrations and coordinated leader–follower LLM agents to generate bimanual manipulation trajectories through in-context learning.

<a id="robot-native"></a>

## Robot-native ICIL and meta-trained policies

### One-Shot Imitation Learning · 2017

**[One-Shot Imitation Learning](https://arxiv.org/abs/1703.07326)**

Meta-trains a demonstration-conditioned policy to perform a new task from one demonstration, including simulated block-stacking tasks.

[Project](https://openai.com/index/robots-that-learn/)

### MOSAIC · 2021

**[Towards More Generalizable One-shot Visual Imitation Learning](https://arxiv.org/abs/2110.13423)**

Combines self-attention and temporal contrastive learning for multi-task one-shot visual imitation; evaluates both demonstration conditioning and fine-tuning on new tasks.

[Repository](https://github.com/rll-research/mosaic)

### ICRT · 2024

**[In-Context Imitation Learning via Next-Token Prediction](https://arxiv.org/abs/2408.15980)**

Autoregressively models image, state, and action trajectories; teleoperated demonstrations prompt new robot behaviors without target-task parameter updates.

[Project](https://icrt.dev/) · [Repository](https://github.com/Max-Fu/icrt)

### Instant Policy · 2024

**[Instant Policy: In-Context Imitation Learning via Graph Diffusion](https://arxiv.org/abs/2411.12633)**

Represents demonstrations, observations, and actions as a graph and generates actions through graph diffusion, using simulated pseudo-demonstrations for training.

[Project](https://www.robot-learning.uk/instant-policy) · [Repository](https://github.com/vv19/instant_policy)

### RoboSSM · 2025

**[RoboSSM: Scalable In-context Imitation Learning via State-Space Models](https://arxiv.org/abs/2509.19658)**

Uses a state-space model for demonstration-conditioned imitation, studying longer prompts and generalization to different numbers of demonstrations.

[Repository](https://github.com/youngjuY/RoboSSM)

### ICLR · 2026

**[ICLR: In-Context Imitation Learning with Visual Reasoning](https://arxiv.org/abs/2603.07530)**

Augments demonstration prompts with image-space future trajectory traces and jointly predicts visual reasoning traces and low-level actions.

[Project](https://toannguyen1904.github.io/ICLR)

### SynthICL · 2026

**[SynthICL: Scalable In-context Imitation Learning with Synthetic Data](https://arxiv.org/abs/2606.08154)**

Trains an RGB-only flow-matching ICIL policy with synthetic data and subgoal-image prediction, then conditions on one demonstration for real-world tasks.

[Project](https://synth-icl.github.io/)

### BPP · 2026

**[Behavior Prompting Policy: Demonstrations as Prompts for Manipulation](https://arxiv.org/abs/2606.30457)**

Conditions a visuomotor policy on a behavior demonstration and current observation; introduces the iPhUMI interface and DrawAnything/LIBERO-Gen evaluations.

[Project](https://behavior-prompting.github.io/) · [Repository](https://github.com/real-stanford/behavior_prompting)

<a id="vla-icl"></a>

## VLA/VLM-based ICL and multimodal prompting

### VIMA · 2022

**[VIMA: General Robot Manipulation with Multimodal Prompts](https://arxiv.org/abs/2210.03094)**

Uses interleaved visual and textual prompts to specify manipulation tasks, including visual goals and demonstrations; a related multimodal prompting policy.

[Project](https://vimalabs.github.io/) · [Repository](https://github.com/vimalabs/VIMA)

### RICL · 2025

**[RICL: Adding In-Context Adaptability to Pre-Trained Vision-Language-Action Models](https://arxiv.org/abs/2508.02062)**

Post-trains a pretrained VLA for in-context adaptation and retrieves relevant demonstration segments at inference; also evaluates a separate target-task fine-tuning setting.

[Project](https://ricl-vla.github.io/) · [Repository](https://github.com/ricl-vla/ricl_openpi)

### SeeTraceAct · 2026

**[SeeTraceAct: Visibility-Aware Latent Planning from Cross-Embodiment Demonstration Videos](https://arxiv.org/abs/2606.02745)**

Conditions a VLA on demonstration videos and uses visibility-aware future end-effector trace prediction during training to support spatial grounding.

[Project](https://jaehyeon-son.github.io/seetraceact/) · [Repository](https://github.com/jaehyeon-son/SeeTraceAct)

### StellaVLA · 2026

**[StellaVLA: In-Context Structured Demonstration for Generalizable Vision-Language-Action Models](https://arxiv.org/abs/2608.11671)**

Converts trajectories into structured demonstrations containing plans, subgoals, and verbalized motion; conditions a VLA on a retrieved demonstration at test time.

[Project](https://www.stelledge.com/blog/stellavla)

<a id="human-video"></a>

## Human-video and cross-embodiment ICL

### Vid2Robot · 2024

**[Vid2Robot: End-to-end Video-conditioned Policy Learning with Cross-Attention Transformers](https://arxiv.org/abs/2403.12943)**

Learns a video-conditioned robot policy from prompt-video/robot-trajectory pairs, using cross-attention and contrastive alignment across human and robot videos.

[Project](https://vid2robot.github.io/)

### ViVLA · 2025

**[See Once, Then Act: Vision-Language-Action Model with Task Learning from One-Shot Video Demonstrations](https://arxiv.org/abs/2512.07582)**

Processes one expert demonstration video with current robot observations to predict actions; trains on expert–agent pairs including synthesized human-video pairs.

### HOST · 2026

**[HOST:Robots Acquire Manipulation Skills in Seconds from a Single Human Video](https://arxiv.org/abs/2607.20033)**

Aligns robot progress with a human demonstration, predicts robot-grounded future observations, and derives actions to acquire a skill from one video at inference.

[Project](https://host-site.host-robotics.workers.dev/) · [Repository](https://github.com/CGuangyan-BIT/HOST)

### Zero-WAM · 2026

**[Zero-WAM: In-Context World-Action Modeling from Human Videos for Open-Ended Task Generalization](https://arxiv.org/abs/2608.26103)**

Conditions a causal video-action model on human video prompts for unseen tasks; introduces HumanGen paired data and an in-context future chunk prediction objective.

[Project](https://robbyant-research.github.io/Zero-WAM/) · [Repository](https://github.com/robbyant-research/Zero-WAM)

<a id="adaptation-memory"></a>

## Test-time adaptation and long-context memory

### Meta-imitation learning · 2017

**[One-Shot Visual Imitation Learning via Meta-Learning](https://arxiv.org/abs/1709.04905)**

Meta-learns a visuomotor policy initialization that can adapt from one demonstration through gradient updates; a few-shot adaptation predecessor, not fixed-weight ICL.

[Project](https://sites.google.com/view/one-shot-imitation) · [Repository](https://github.com/tianheyu927/mil)

### Domain-adaptive meta-learning · 2018

**[One-Shot Imitation from Observing Humans via Domain-Adaptive Meta-Learning](https://arxiv.org/abs/1802.01557)**

Learns an adaptation objective that transfers from a human video to a robot policy using gradient-based adaptation across the embodiment gap.

### Algorithm Distillation · 2022

**[In-context Reinforcement Learning with Algorithm Distillation](https://arxiv.org/abs/2210.14215)**

Trains a causal sequence model on reinforcement-learning histories so policy improvement occurs through context without network parameter updates; a general RL foundation.

### TTT layers · 2024

**[Learning to (Learn at Test Time): RNNs with Expressive Hidden States](https://arxiv.org/abs/2407.04620)**

Treats recurrent hidden state as a small model whose weights update through self-supervised learning during inference; a sequence-modeling foundation for parametric memory.

[Repository](https://github.com/test-time-training/ttt-lm-pytorch)

### RoboTTT · 2026

**[RoboTTT: Context Scaling for Robot Policies](https://arxiv.org/abs/2607.15275)**

Adds test-time-training layers to robot policies for long visuomotor histories and video prompting; fast weights receive gradient updates during inference.

[Project](https://research.nvidia.com/labs/gear/robottt/)

<a id="multimodal-foundations"></a>

## Multimodal ICL foundations

### Flamingo · 2022

**[Flamingo: a Visual Language Model for Few-Shot Learning](https://arxiv.org/abs/2204.14198)**

Supports few-shot image and video tasks through interleaved visual–text examples, providing an architectural foundation for multimodal in-context learning.

[Project](https://deepmind.google/blog/tackling-multiple-tasks-with-a-single-visual-language-model/)

### OpenFlamingo · 2023

**[OpenFlamingo: An Open-Source Framework for Training Large Autoregressive Vision-Language Models](https://arxiv.org/abs/2308.01390)**

Provides an open framework and models for autoregressive vision-language learning with interleaved image/text contexts.

[Repository](https://github.com/mlfoundations/open_flamingo)

### MMICL · 2023

**[MMICL: Empowering Vision-language Model with Multi-Modal In-Context Learning](https://arxiv.org/abs/2309.07915)**

Introduces a multimodal context format and the MIC dataset to improve understanding of multi-image prompts and multimodal in-context examples.

[Repository](https://github.com/PKUnlp-icler/MIC)
