项目持续时间：2024年10月-2025年10月。当前此页已停止维护。

# 一、简介
tracking-map用于跟踪pt-ecosystem小组在Ascend NPU适配一些热门生态工具的进展。

****非常感谢这些优秀的生态工具能接受我们的PR**



# 二、项目清单
## 24年Q4
### 1、基于transformers、llama-factory、openMind做的一系列微调指导
- [以huggingface-transformers为例，创建一个可供使用昇腾原生支持三方套件的环境](https://modelers.cn/models/PNP/Start-Create-Env-Transformers)
- [以llama-factory为例，快速使用Qwen2.5-7B-Instruct模型完成一个微调任务](https://modelers.cn/models/PNP/Llama-Factory-Quick-Start)
- [使用昇腾原生支持生态库llama-factory做法律垂域模型微调](https://modelers.cn/models/PNP/Enhance-Llama-Factory-SFT-Law)

### 2、后来，上述文章被整合，并发到了官网公众号宣传
- 文章标题：[基于应用使能套件的行业模型微调实践](https://mp.weixin.qq.com/s/7ocVjwX1k4xF6AaUkj-6vg)

### 3、ModelZoo-PyTorch经典模型库
- 规定[随版本演进模型](https://gitee.com/ascend/ModelZoo-PyTorch/pulls/6964)范围
- 优化[环境变量](https://gitee.com/ascend/ModelZoo-PyTorch/pulls/6943)说明
- 新增代码提交[规范](https://gitee.com/ascend/ModelZoo-PyTorch/pulls/7079)
- 随版本演进模型每季度刷新性能[基线](https://gitee.com/ascend/ModelZoo-PyTorch/pulls/7230)

### 4、ModelZoo-GPL下YOLO系模型
- 以[YOLOv8](https://gitee.com/ascend/modelzoo-GPL/tree/master/built-in/PyTorch/Official/cv/object_detection/Yolov8_for_PyTorch)为例示范迁移模型和调优路径


## 25年Q1
### 1、IntrernLMv3发布后0 day支持xtuner npu

- 在-1 day令xtuner原生支持Ascend NPU: https://github.com/InternLM/xtuner/pull/983
- NPU中使用InternLMv3快速上手指导: https://github.com/InternLM/InternLM/pull/816
  - 贡献基于huggingface-transformers直接推理的脚本
  - 基于已适配的xtuner，在InternLMv3发布当天即完成在xtuner的LoRA微调验证
  - 贡献基于llama-factory的微调脚本，并在发布当天完成InternLMv3精度和性能的验证

### 2、torchtune原生支持

- NPU单卡功能相关: https://github.com/pytorch/torchtune/pull/2234
- NPU多卡分布式相关：https://github.com/pytorch/torchtune/pull/2646
- roadmap: https://github.com/pytorch/torchtune/issues/2288

### 3、OpenRLHF原生支持
- OpenRLHF原生支持NPU: https://github.com/OpenRLHF/OpenRLHF/pull/605
- Q2 RoadMap：https://github.com/OpenRLHF/OpenRLHF/issues/914
- 因OpenRLHF没有支持第三方device计划，后续转为此项目维护：[pt-ecosystem/OpenRLHF-NPU](https://github.com/pt-ecosystem/OpenRLHF-NPU)

### 4、transformers中原生支持sdpa和flash-attention
- 尝试在transformers中开启SDPA：[PR1](https://github.com/huggingface/transformers/pull/35165)、[PR2](https://github.com/huggingface/transformers/pull/36383)
- transformers原生支持npu的flash attention：[PR1](https://github.com/huggingface/transformers/pull/36696)、[PR2](https://github.com/huggingface/transformers/pull/37698)
、[PR3](https://github.com/huggingface/transformers/pull/38278)

## 25年Q2
### 1、NPU支持使用OpenFold
- torch.multinomial在ARM和x86中使用的不同点：https://github.com/pytorch/pytorch/issues/148247
- OpenFold项目：使用[示例脚本](https://gitee.com/ascend/ModelZoo-PyTorch/tree/master/PyTorch/built-in/others/OpenFold_for_PyTorch)

### 2、在RL场景中vllm-ascend需要一些独特的修改
- vllm-ascend支持sleep mode功能：https://github.com/vllm-project/vllm-ascend/issues/320
- 修复RL场景拉起vllm的功能问题：https://github.com/vllm-project/vllm-ascend/pull/884
- 为vllm_ascend_C增加lazy init：https://github.com/vllm-project/vllm-ascend/pull/1234

### 3、veRL原生支持NPU
- 原生支持PR：https://github.com/volcengine/verl/pull/332
- verl Q2 Roadmap：https://github.com/volcengine/verl/discussions/900
- 支持verl profiling：https://github.com/volcengine/verl/pull/2194
- 支持LLM GRPO：https://github.com/volcengine/verl/pull/332
- 支持LLM DAPO：https://github.com/volcengine/verl/pull/1858
- 支持VL GRPO：https://github.com/volcengine/verl/pull/1924
 

### 4、ascend-ring-attention项目
- 提供ascend npu的ring-attention支持：https://github.com/ji-huazhong/ring-attention-ascend/pull/1


## 25年Q3
### 1、在RL场景中vllm-ascend需要一些独特的修改（继承q2，持续）
- 配套torch_npu升级：https://github.com/vllm-project/vllm-ascend/issues/1390
- DFX-澄清报错信息：https://github.com/vllm-project/vllm-ascend/issues/1706
- 修复Qwen2.5-VL场景功能缺失：https://github.com/vllm-project/vllm-ascend/pull/1705

### 2、veRL原生支持NPU（继承q2，持续）
- verl的npu原生支持工作被官方昇腾AI开发者公众号[报道](https://mp.weixin.qq.com/s/0nH7d2LvvBfcUhUvBR4r_A)
- verl Q3 RoadMap：https://github.com/volcengine/verl/discussions/2171
- 支持SFT：https://github.com/volcengine/verl/pull/2240
- 支持Retool SFT：https://github.com/volcengine/verl/pull/3000
- 支持ray actor sharing situation：https://github.com/volcengine/verl/pull/2341
- 增加Profiling指导：https://github.com/volcengine/verl/pull/2514
- profiling discrete模式下支持按阶段采集：https://github.com/volcengine/verl/pull/2750
- 增强CI能力：https://github.com/volcengine/verl/pull/2089
- 添加融合算子：https://github.com/volcengine/verl/pull/3260
- Refactor：https://github.com/volcengine/verl/pull/2542, https://github.com/volcengine/verl/pull/1974
- Fix：https://github.com/volcengine/verl/pull/2459,https://github.com/volcengine/verl/pull/2576, https://github.com/volcengine/verl/pull/2541, https://github.com/volcengine/verl/pull/2477, https://github.com/volcengine/verl/pull/2291, https://github.com/volcengine/verl/pull/3052
- 关于doc：https://github.com/volcengine/verl/pull/3063, https://github.com/volcengine/verl/pull/3127

### 3、transformers中集成其他npu融合算子
- 跟踪issue：https://github.com/huggingface/transformers/issues/39105
- 第1个PR尝试，可作为临时解决方案：https://github.com/huggingface/transformers/pull/39238
- 使用kernels工具重构：kernels现已原生支持NPU-https://github.com/huggingface/kernels/pull/146
- 可以通过kernels + transformers直接使用flash attention和RMSNorm，存放于该组织中https://huggingface.co/kernels-ext-npu

### 4、SGLang + verl工作
- 跟踪issue：https://github.com/volcengine/verl/issues/2916

### 5、ROLL的原生支持
- 第一个PR（合作）：https://github.com/alibaba/ROLL/pull/99


# 三、pt-ecosystem小组成员
24年10月-25年10月，参与pt-ecosystem适配工作的成员包含:
- [@zheliuyu](https://github.com/zheliuyu)
- [@FightingZhen](https://github.com/FightingZhen)
- [@zhuo97](https://github.com/zhuo97)
- [@Nicorgi](https://github.com/Nicorgi)
- [@as12138](https://github.com/as12138)
- [@tongtong0613](https://github.com/tongtong0613)
- [@Tonyztj](https://github.com/Tonyztj)
- [@Keilo001](https://github.com/Keilo001)
- [@Leo-imperial](https://github.com/Leo-imperial)
- [@obj12](https://github.com/obj12)
