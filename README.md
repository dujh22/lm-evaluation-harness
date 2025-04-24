
# 语言模型评估框架

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.10256836.svg)](https://doi.org/10.5281/zenodo.10256836)

---

## 最新动态 📣

- [2025/03] 新增支持对 HF 模型进行引导(steering)!
- [2025/02] 新增支持 [SGLang](https://docs.sglang.ai/)!
- [2024/09] 我们正在开发原型功能,允许用户创建和评估文本+图像的多模态输入、文本输出任务。我们刚刚添加了 `hf-multimodal` 和 `vllm-vlm` 模型类型以及 `mmmu` 任务作为原型特性。欢迎用户试用这个正在开发的功能并进行压力测试,同时建议查看 [`lmms-eval`](https://github.com/EvolvingLMMs-Lab/lmms-eval),这是一个从 lm-evaluation-harness 分支出来的优秀项目,提供更广泛的多模态任务、模型和功能支持。
- [2024/07] [API 模型](docs/API_guide.md)支持已更新和重构,引入了批处理和异步请求支持,使其更容易定制和使用。**对于运行 Llama 405B,我们建议使用 VLLM 的 OpenAI 兼容 API 来托管模型,并使用 `local-completions` 模型类型来评估模型。**
- [2024/07] 新增了 Open LLM Leaderboard 任务! 您可以在 [leaderboard](lm_eval/tasks/leaderboard/README.md) 任务组中找到它们。

---

## 公告

**lm-evaluation-harness 的新版本 v0.4.0 已发布!**

新的更新和功能包括:

- **新增了 Open LLM Leaderboard 任务! 您可以在 [leaderboard](lm_eval/tasks/leaderboard/README.md) 任务组中找到它们。**
- 内部重构
- 基于配置的任务创建和配置
- 更容易导入和共享外部定义的任务配置 YAML
- 支持 Jinja2 提示设计,易于修改提示和从 Promptsource 导入提示
- 更多高级配置选项,包括输出后处理、答案提取、每个文档的多个 LM 生成、可配置的少样本设置等
- 加速和支持新的建模库,包括:更快的数据并行 HF 模型使用、vLLM 支持、HuggingFace 的 MPS 支持等
- 日志记录和可用性改进
- 新任务包括 CoT BIG-Bench-Hard、Belebele、用户定义的任务分组等

请查看 `docs/` 中的更新文档了解更多详情。

我们将继续在 `main` 分支上进行开发,我们鼓励您通过 GitHub 上的 issues 或 PRs,或在 [EleutherAI discord](https://discord.gg/eleutherai) 中提供反馈,告诉我们需要哪些功能以及如何进一步改进库,或提出问题。

---

## 概述

该项目提供了一个统一的框架,用于在大量不同的评估任务上测试生成式语言模型。

**特点:**

- 实现了超过 60 个标准学术基准测试,包含数百个子任务和变体
- 支持通过 [transformers](https://github.com/huggingface/transformers/) 加载的模型(包括通过 [GPTQModel](https://github.com/ModelCloud/GPTQModel) 和 [AutoGPTQ](https://github.com/PanQiWei/AutoGPTQ) 进行量化)、[GPT-NeoX](https://github.com/EleutherAI/gpt-neox) 和 [Megatron-DeepSpeed](https://github.com/microsoft/Megatron-DeepSpeed/) 模型,具有灵活的分词器无关接口
- 支持使用 [vLLM](https://github.com/vllm-project/vllm) 进行快速和内存高效的推理
- 支持商业 API,包括 [OpenAI](https://openai.com) 和 [TextSynth](https://textsynth.com/)
- 支持评估 [HuggingFace PEFT 库](https://github.com/huggingface/peft) 支持的适配器(如 LoRA)
- 支持本地模型和基准测试
- 使用公开可用的提示确保论文之间的可重复性和可比性
- 易于支持自定义提示和评估指标

Language Model Evaluation Harness 是 🤗 Hugging Face 流行的 [Open LLM Leaderboard](https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard) 的后端,已在[数百篇论文](https://scholar.google.com/scholar?oi=bibs&hl=en&authuser=2&cites=15052937328817631261,4097184744846514103,1520777361382155671,17476825572045927382,18443729326628441434,14801318227356878622,7890865700763267262,12854182577605049984,15641002901115500560,5104500764547628290)中使用,并被 NVIDIA、Cohere、BigScience、BigCode、Nous Research 和 Mosaic ML 等数十个组织内部使用。

[接下来是安装和使用说明部分,需要继续翻译吗?]
