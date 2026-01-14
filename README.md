# 目录

2024年10月至2025年10月工作在: [TrackingMap_2410-2510.md](./TrackingMap_2410-2510.md)

这里呈现的是2025年10月之后的工作。


# 项目清单

## 25年11月-12月

### huggingface/kernels 及其衍生工具

- huggingface/kernels原生支持：
    - https://github.com/huggingface/kernels/pull/146
    - https://github.com/huggingface/kernels/pull/155
- huggingface/transformers中支持通过kernels加载算子
    - https://github.com/huggingface/transformers/pull/41542
    - https://github.com/huggingface/transformers/pull/42106
    - https://github.com/huggingface/transformers/pull/42358
    - https://github.com/huggingface/transformers/pull/42800
- kernels在npu中使用所依赖的hub中各kernel的源码：https://github.com/pt-ecosystem/kernels-ext-npu

### Liger-kernel 的原生支持

- Roadmap: https://github.com/linkedin/Liger-Kernel/issues
- Adjust MAX_FUSED_SIZE when using fused_linear_cross_entropy: https://github.com/linkedin/Liger-Kernel/pull/985

### VeOmni 的特性支持

- 升级 transformers 到 v5 版本：https://github.com/ByteDance-Seed/VeOmni/pull/348


## 26年1月

## 开新坑：verl + VeOmni + transformers v5 + Liger-Kernel + kernels 最近的一些工作整合成一个demo

pass

## 顺便把三方库对外呈现的文档重构一下

关注这里的PR：https://github.com/Ascend/docs/pull/94
