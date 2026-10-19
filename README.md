# Starynight / 模拟与混合信号设计

> 我是 Starynight，做 SAR ADC 的行为建模、数字校准与硬件验证，同时记录深度学习与体系结构的学习。

账号下的公开仓库按研究工程、开源工具、学习资源三层索引在下方，另有两个受许可限制的版图与 FPGA 工程未公开。指标与结论的时间条件写在各仓库内部，本页只做入口，不重复陈述证据。

## 方向

- SAR ADC 架构与行为建模：两级残差、冗余与电容失配建模，定点实现与 RTL 对照。
- 数字校准：前景校准与电容阵列校准，Python 模型与 RTL 实现互相验证。
- 数字后端与签核：综合、静态时序、LVS/DRC 证据链与未闭合项记录。
- 验证与指标口径：MATLAB/Octave 算法对照，SNR/SNDR/SFDR/THD 的统一计算口径。
- 深度学习与体系结构：教材与开源实现的学习记录。

## 代表项目

### 研究与工程

| 项目 | 一句话说明 | 状态 |
|---|---|---|
| [20bit_SAR_ADC_Behaviour_Verification](https://github.com/defineiocc02/20bit_SAR_ADC_Behaviour_Verification) | 20 位两级残差 SAR 的行为模型、定点实现与 RTL 对照 | 活跃 |
| [Behavioral-modeling-of-12bit-calibrated-sar-adc](https://github.com/defineiocc02/Behavioral-modeling-of-12bit-calibrated-sar-adc) | 12 位电容失配建模与前景校准，Python 与 RTL 双实现 | 活跃 |
| [SAR16_Digital_Backend_Signoff](https://github.com/defineiocc02/SAR16_Digital_Backend_Signoff) | 16 位 SAR 数字后端的网表、版图、时序与交付证据 | 维护中，LVS、hold、DRC 未闭合 |
| [Digital_process.srcs](https://github.com/defineiocc02/Digital_process.srcs) | 校准控制与码字重构的数字处理，含历史 RTL 归档 | 活跃 |
| [SAR_ADC_Verification](https://github.com/defineiocc02/SAR_ADC_Verification) | MATLAB/Octave 残差算法对照与频谱分析 | 活跃，历史比较图与排名待重新生成 |

### 使用的开源工具（fork）

| 项目 | 一句话说明 | 状态 |
|---|---|---|
| [ADCToolbox](https://github.com/defineiocc02/ADCToolbox) | ADC 建模与分析工具箱，上游 [Arcadia-1/ADCToolbox](https://github.com/Arcadia-1/ADCToolbox) | fork，跟随上游 |
| [virtuoso-bridge-lite](https://github.com/defineiocc02/virtuoso-bridge-lite) | Virtuoso 与外部流程的轻量桥接，上游 [Arcadia-1/virtuoso-bridge-lite](https://github.com/Arcadia-1/virtuoso-bridge-lite) | fork，跟随上游 |

### 学习资源（fork）

| 项目 | 一句话说明 | 状态 |
|---|---|---|
| [d2l-zh](https://github.com/defineiocc02/d2l-zh) | 《动手学深度学习》中文版，上游 [d2l-ai/d2l-zh](https://github.com/d2l-ai/d2l-zh) | fork |
| [Deep_Learning_Foundation_and_Concepts-Springer](https://github.com/defineiocc02/Deep_Learning_Foundation_and_Concepts-Springer) | 深度学习基础与概念教材配套代码，上游 BreCaspian 同名仓库 | fork |
| [goossens-book-ip-projects](https://github.com/defineiocc02/goossens-book-ip-projects) | 数据转换器设计教材的 IP 工程，上游 goossens-springer 同名仓库 | fork |
| [Hands-On-Large-Language-Models](https://github.com/defineiocc02/Hands-On-Large-Language-Models) | 大模型实践教材配套代码，上游 HandsOnLLM 同名仓库 | fork |

### 未公开工程

| 项目 | 一句话说明 | 状态 |
|---|---|---|
| 12bit_CAAZ_SAR_ADC | 12 位 CAAZ 校准 SAR ADC 的设计与验证，与上面的 12 位模型互为上下游 | 私有仓库 |
| candidate-a-acx720-v3-fpga | 12 位 SAR 校准的 FPGA 实现（ACX720-V3 板），含 CDC 与 XPM FIFO 验证 | 私有仓库 |

以上状态核对于 2026-10-19，依据各仓库默认分支的最新提交；未闭合项以各仓库内的签核与验证文档为准。账号另有 4 个私有仓库未在此列出。

阅读与复现规范见 [REPOSITORY_GUIDE.md](REPOSITORY_GUIDE.md)；本轮审查与后续路线见 [REVIEW_20261002.md](REVIEW_20261002.md)，其中「待合入」条目以各仓库的 PR 状态为准。

## 当前在做什么

- 20 位工程：校准综合与核心时序改进在 [PR #4](https://github.com/defineiocc02/20bit_SAR_ADC_Behaviour_Verification/pull/4)（分支 `codex/calibration-closure-20260928`），尚未合入 `main`；另有 [PR #6](https://github.com/defineiocc02/20bit_SAR_ADC_Behaviour_Verification/pull/6)（`feature/ad4080-dsp`）在开。该分支的 40 MHz 核时钟、16 周期/样本对应 2.5 MS/s 属 FPGA 核时序结果，不能读作芯片实测；完整外部 I/O hold 仍有缺口。
- 16 位后端：静态审计与 PPA 对标改进在 [PR #1](https://github.com/defineiocc02/SAR16_Digital_Backend_Signoff/pull/1)（分支 `codex/static-audit-20260930`），尚未合入；`codex/sky130hs-repair-signoff-20261006` 分支尚无 PR。默认分支上的签核资料仍报 LVS、hold、DRC 未闭合，应先关闭这些问题再谈签核完成。
- 数字处理：指标口径修复已合入 `main`；`codex/metric-evidence-guard-20261005` 上的证据校验改动在 [PR #4](https://github.com/defineiocc02/Digital_process.srcs/pull/4)，待评审。
- 12 位失配：保留名义与压力样本、失败尾部与局部回退；验收条件含 calibration-only 扰动，正常转换零噪声，不作为通用噪声性能证明。

## 联系

- 邮箱：<待补充>
- 博客：https://defineiocc02.github.io/Blog/ ，源码在 [Blog](https://github.com/defineiocc02/Blog) 仓库
- 问题反馈：在上述仓库提 Issue
