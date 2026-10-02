# defineiocc02 · 模拟与混合信号设计

关注 SAR ADC、数字校准、硬件验证，以及深度学习与计算机体系结构。

[技术博客](https://github.com/defineiocc02/Blog) · [仓库阅读与复现规范](REPOSITORY_GUIDE.md) · [本轮审查与后续路线](REVIEW_20261002.md)

## 研究与工程

| 项目 | 内容 | 证据状态 |
|---|---|---|
| [20 位 SAR 行为与数字实现](https://github.com/defineiocc02/20bit_SAR_ADC_Behaviour_Verification) | 两级残差架构、来源分级、定点与 RTL | 行为/数字证据；芯片参数仍含假设 |
| [12 位失配校准模型](https://github.com/defineiocc02/Behavioral-modeling-of-12bit-calibrated-sar-adc) | 失配、前景校准、Python 与 RTL | 通过率受模型和阈值限定；正常转换零噪声 |
| [16 位数字后端审计](https://github.com/defineiocc02/SAR16_Digital_Backend_Signoff) | 网表、版图、时序与交付证据 | LVS、hold、DRC 仍有未闭合项 |
| [SAR 数字处理与验证](https://github.com/defineiocc02/Digital_process.srcs) | 校准控制、重构、历史 RTL 归档 | 频谱口径已修复；历史报告需重算 |
| [MATLAB 残差算法比较](https://github.com/defineiocc02/SAR_ADC_Verification) | MLE、BE 等算法与频谱分析 | 数值检查已通过；完整实验待重跑 |

项目按规格、接口和证据层级独立维护。阅读成果时请同时查看配置、原始数据、复现步骤和未闭合项；输出位数、仿真通过和芯片实测是不同证据。

## 使用的开源工具

| 工具 | 上游 |
|---|---|
| [ADCToolbox](https://github.com/defineiocc02/ADCToolbox) | [Arcadia-1/ADCToolbox](https://github.com/Arcadia-1/ADCToolbox) |
| [virtuoso-bridge-lite](https://github.com/defineiocc02/virtuoso-bridge-lite) | [Arcadia-1/virtuoso-bridge-lite](https://github.com/Arcadia-1/virtuoso-bridge-lite) |

这些仓库保留上游身份，个人改动以提交记录为准。

<details>
<summary>学习资源与书籍配套代码</summary>

- [d2l-zh](https://github.com/defineiocc02/d2l-zh) — fork 自 [d2l-ai/d2l-zh](https://github.com/d2l-ai/d2l-zh)。
- [Deep_Learning_Foundation_and_Concepts-Springer](https://github.com/defineiocc02/Deep_Learning_Foundation_and_Concepts-Springer) — fork 自 [BreCaspian/Deep_Learning_Foundation_and_Concepts-Springer](https://github.com/BreCaspian/Deep_Learning_Foundation_and_Concepts-Springer)。
- [goossens-book-ip-projects](https://github.com/defineiocc02/goossens-book-ip-projects) — fork 自 [goossens-springer/goossens-book-ip-projects](https://github.com/goossens-springer/goossens-book-ip-projects)。
- [Hands-On-Large-Language-Models](https://github.com/defineiocc02/Hands-On-Large-Language-Models) — fork 自 [HandsOnLLM/Hands-On-Large-Language-Models](https://github.com/HandsOnLLM/Hands-On-Large-Language-Models)。

</details>

---

**Research in progress.** Behavioral models, digital verification, physical signoff and silicon measurements are reported separately. Upstream tools and learning materials remain credited to their authors.
