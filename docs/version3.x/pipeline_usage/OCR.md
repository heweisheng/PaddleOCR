---
comments: true
---

# 通用OCR产线使用教程

## 1. OCR产线介绍

OCR（光学字符识别，Optical Character Recognition）是一种将图像中的文字转换为可编辑文本的技术。它广泛应用于文档数字化、信息提取和数据处理等领域。OCR 可以识别印刷文本、手写文本，甚至某些类型的字体和符号。

通用 OCR 产线用于解决文字识别任务，提取图片中的文字信息以文本形式输出，本产线支持PP-OCRv3、PP-OCRv4、PP-OCRv5模型的使用，其中默认模型为 PaddleOCR3.0 发布的 PP-OCRv5_server 模型，其在多个场景中较 PP-OCRv4_server 提升 13 个百分点。

<img src="https://raw.githubusercontent.com/cuicheng01/PaddleX_doc_images/main/images/pipelines/ocr/01.png"/>

<b>通用OCR产线中包含以下5个模块。每个模块均可独立进行训练和推理，并包含多个模型。有关详细信息，请点击相应模块以查看文档。</b>

- [文档图像方向分类模块](../module_usage/doc_img_orientation_classification.md) （可选）
- [文本图像矫正模块](../module_usage/text_image_unwarping.md) （可选）
- [文本行方向分类模块](../module_usage/textline_orientation_classification.md) （可选）
- [文本检测模块](../module_usage/text_detection.md)
- [文本识别模块](../module_usage/text_recognition.md)

在本产线中，您可以根据下方的基准测试数据选择使用的模型。

<details>
<summary><b>文档图像方向分类模块（可选）：</b></summary>
<table>
<thead>
<tr>
<th>模型</th><th>模型下载链接</th>
<th>Top-1 Acc（%）</th>
<th>GPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>CPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
</thead>
<tbody>
<tr>
<td>PP-LCNet_x1_0_doc_ori</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-LCNet_x1_0_doc_ori_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-LCNet_x1_0_doc_ori_pretrained.pdparams">训练模型</a></td>
<td>99.06</td>
<td>2.62 / 0.59</td>
<td>3.24 / 1.19</td>
<td>7</td>
<td>基于PP-LCNet_x1_0的文档图像分类模型，含有四个类别，即0度，90度，180度，270度</td>
</tr>
</tbody>
</table>
</details>

<details>
<summary><b>文本图像矫正模块（可选）：</b></summary>
<table>
<thead>
<tr>
<th>模型</th><th>模型下载链接</th>
<th>CER </th>
<th>GPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>CPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
</thead>
<tbody>
<tr>
<td>UVDoc</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/UVDoc_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/UVDoc_pretrained.pdparams">训练模型</a></td>
<td>0.179</td>
<td>19.05 / 19.05</td>
<td>- / 869.82</td>
<td>30.3</td>
<td>高精度文本图像矫正模型</td>
</tr>
</tbody>
</table>
</details>

<details>
<summary><b>文本行方向分类模块（可选）：</b></summary>
<table>
<thead>
<tr>
<th>模型</th>
<th>模型下载链接</th>
<th>Top-1 Acc（%）</th>
<th>GPU推理耗时（ms）</th>
<th>CPU推理耗时 (ms)</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
</thead>
<tbody>
<tr>
<td>PP-LCNet_x0_25_textline_ori</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-LCNet_x0_25_textline_ori_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-LCNet_x0_25_textline_ori_pretrained.pdparams">训练模型</a></td>
<td>98.85</td>
<td>2.16 / 0.41</td>
<td>2.37 / 0.73</td>
<td>0.96</td>
<td>基于PP-LCNet_x0_25的文本行分类模型，含有两个类别，即0度，180度</td>
</tr>
<tr>
<td>PP-LCNet_x1_0_textline_ori</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-LCNet_x1_0_textline_ori_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-LCNet_x1_0_textline_ori_pretrained.pdparams">训练模型</a></td>
<td>99.42</td>
<td>- / -</td>
<td>2.98 / 2.98</td>
<td>6.5</td>
<td>基于PP-LCNet_x1_0的文本行分类模型，含有两个类别，即0度，180度</td>
</tr>
</tbody>
</table>
</details>

<details>
<summary><b>文本检测模块：</b></summary>
<table>
<thead>
<tr>
<th>模型</th><th>模型下载链接</th>
<th>检测Hmean（%）</th>
<th>GPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>CPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
</thead>
<tbody>
<tr>
<td>PP-OCRv5_server_det</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-OCRv5_server_det_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv5_server_det_pretrained.pdparams">训练模型</a></td>
<td>83.8</td>
<td>89.55 / 70.19</td>
<td>383.15 / 383.15</td>
<td>84.3</td>
<td>PP-OCRv5 的服务端文本检测模型，精度更高，适合在性能较好的服务器上部署</td>
</tr>
<tr>
<td>PP-OCRv5_mobile_det</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-OCRv5_mobile_det_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv5_mobile_det_pretrained.pdparams">训练模型</a></td>
<td>79.0</td>
<td>10.67 / 6.36</td>
<td>57.77 / 28.15</td>
<td>4.7</td>
<td>PP-OCRv5 的移动端文本检测模型，效率更高，适合在端侧设备部署</td>
</tr>
<tr>
<td>PP-OCRv4_server_det</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-OCRv4_server_det_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv4_server_det_pretrained.pdparams">训练模型</a></td>
<td>69.2</td>
<td>127.82 / 98.87</td>
<td>585.95 / 489.77</td>
<td>109</td>
<td>PP-OCRv4 的服务端文本检测模型，精度更高，适合在性能较好的服务器上部署</td>
</tr>
<tr>
<td>PP-OCRv4_mobile_det</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-OCRv4_mobile_det_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv4_mobile_det_pretrained.pdparams">训练模型</a></td>
<td>63.8</td>
<td>9.87 / 4.17</td>
<td>56.60 / 20.79</td>
<td>4.7</td>
<td>PP-OCRv4 的移动端文本检测模型，效率更高，适合在端侧设备部署</td>
</tr>
</tbody>
</table>
</details>

<details>
<summary><b>文本识别模块：</b></summary>
<table>
<tr>
<th>模型</th><th>模型下载链接</th>
<th>识别 Avg Accuracy(%)</th>
<th>GPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>CPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
<tr>
<td>PP-OCRv5_server_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
PP-OCRv5_server_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv5_server_rec_pretrained.pdparams">训练模型</a></td>
<td>86.38</td>
<td>8.46 / 2.36</td>
<td>31.21 / 31.21</td>
<td>81</td>
<td rowspan="2">PP-OCRv5_rec 是新一代文本识别模型。该模型致力于以单一模型高效、精准地支持简体中文、繁体中文、英文、日文四种主要语言，以及手写、竖版、拼音、生僻字等复杂文本场景的识别。在保持识别效果的同时，兼顾推理速度和模型鲁棒性，为各种场景下的文档理解提供高效、精准的技术支撑。</td>
</tr>
<tr>
<td>PP-OCRv5_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
PP-OCRv5_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv5_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>81.29</td>
<td>5.43 / 1.46</td>
<td>21.20 / 5.32</td>
<td>16</td>
</tr>
<tr>
<td>PP-OCRv4_server_rec_doc</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
PP-OCRv4_server_rec_doc_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv4_server_rec_doc_pretrained.pdparams">训练模型</a></td>
<td>86.58</td>
<td>8.69 / 2.78</td>
<td>37.93 / 37.93</td>
<td>182</td>
<td>PP-OCRv4_server_rec_doc是在PP-OCRv4_server_rec的基础上，在更多中文文档数据和PP-OCR训练数据的混合数据训练而成，增加了部分繁体字、日文、特殊字符的识别能力，可支持识别的字符为1.5万+，除文档相关的文字识别能力提升外，也同时提升了通用文字的识别能力</td>
</tr>
<tr>
<td>PP-OCRv4_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-OCRv4_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv4_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>78.74</td>
<td>5.26 / 1.12</td>
<td>17.48 / 3.61</td>
<td>10.5</td>
<td>PP-OCRv4的轻量级识别模型，推理效率高，可以部署在包含端侧设备的多种硬件设备中</td>
</tr>
<tr>
<td>PP-OCRv4_server_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-OCRv4_server_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv4_server_rec_pretrained.pdparams">训练模型</a></td>
<td>85.19</td>
<td>8.75 / 2.49</td>
<td>36.93 / 36.93</td>
<td>173</td>
<td>PP-OCRv4的服务器端模型，推理精度高，可以部署在多种不同的服务器上</td>
</tr>
<tr>
<td>en_PP-OCRv4_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
en_PP-OCRv4_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/en_PP-OCRv4_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>70.39</td>
<td>4.81 / 1.23</td>
<td>17.20 / 4.18</td>
<td>7.5</td>
<td>基于PP-OCRv4识别模型训练得到的超轻量英文识别模型，支持英文、数字识别</td>
</tr>
</table>

> ❗ 以上列出的是文本识别模块重点支持的<b>6个核心模型</b>，该模块总共支持<b>20个全量模型</b>，包含多个多语言文本识别模型，完整的模型列表如下：

<details><summary> 👉模型列表详情</summary>

* <b>PP-OCRv5 多场景模型</b>

<table>
<tr>
<th>模型</th><th>模型下载链接</th>
<th>中文识别 Avg Accuracy(%)</th>
<th>英文识别 Avg Accuracy(%)</th>
<th>繁体中文识别 Avg Accuracy(%)</th>
<th>日文识别 Avg Accuracy(%)</th>
<th>GPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>CPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
<tr>
<td>PP-OCRv5_server_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
PP-OCRv5_server_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv5_server_rec_pretrained.pdparams">训练模型</a></td>
<td>86.38</td>
<td>64.70</td>
<td>93.29</td>
<td>60.35</td>
<td>8.46 / 2.36</td>
<td>31.21 / 31.21</td>
<td>81</td>
<td rowspan="2">PP-OCRv5_rec 是新一代文本识别模型。该模型致力于以单一模型高效、精准地支持简体中文、繁体中文、英文、日文四种主要语言，以及手写、竖版、拼音、生僻字等复杂文本场景的识别。在保持识别效果的同时，兼顾推理速度和模型鲁棒性，为各种场景下的文档理解提供高效、精准的技术支撑。</td>
</tr>
<tr>
<td>PP-OCRv5_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
PP-OCRv5_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv5_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>81.29</td>
<td>66.00</td>
<td>83.55</td>
<td>54.65</td>
<td>5.43 / 1.46</td>
<td>21.20 / 5.32</td>
<td>16</td>
</tr>
</table>

* <b>中文识别模型</b>
<table>
<tr>
<th>模型</th><th>模型下载链接</th>
<th>识别 Avg Accuracy(%)</th>
<th>GPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>CPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
<tr>
<td>PP-OCRv4_server_rec_doc</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
PP-OCRv4_server_rec_doc_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv4_server_rec_doc_pretrained.pdparams">训练模型</a></td>
<td>86.58</td>
<td>8.69 / 2.78</td>
<td>37.93 / 37.93</td>
<td>182</td>
<td>PP-OCRv4_server_rec_doc是在PP-OCRv4_server_rec的基础上，在更多中文文档数据和PP-OCR训练数据的混合数据训练而成，增加了部分繁体字、日文、特殊字符的识别能力，可支持识别的字符为1.5万+，除文档相关的文字识别能力提升外，也同时提升了通用文字的识别能力</td>
</tr>
<tr>
<td>PP-OCRv4_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-OCRv4_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv4_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>78.74</td>
<td>5.26 / 1.12</td>
<td>17.48 / 3.61</td>
<td>10.5</td>
<td>PP-OCRv4的轻量级识别模型，推理效率高，可以部署在包含端侧设备的多种硬件设备中</td>
</tr>
<tr>
<td>PP-OCRv4_server_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/PP-OCRv4_server_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv4_server_rec_pretrained.pdparams">训练模型</a></td>
<td>85.19</td>
<td>8.75 / 2.49</td>
<td>36.93 / 36.93</td>
<td>173</td>
<td>PP-OCRv4的服务器端模型，推理精度高，可以部署在多种不同的服务器上</td>
</tr>
<tr>
<td>PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>72.96</td>
<td>3.89 / 1.16</td>
<td>8.72 / 3.56</td>
<td>10.3</td>
<td>PP-OCRv3的轻量级识别模型，推理效率高，可以部署在包含端侧设备的多种硬件设备中</td>
</tr>
</table>

<table>
<tr>
<th>模型</th><th>模型下载链接</th>
<th>识别 Avg Accuracy(%)</th>
<th>GPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>CPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
<tr>
<td>ch_SVTRv2_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/ch_SVTRv2_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/ch_SVTRv2_rec_pretrained.pdparams">训练模型</a></td>
<td>68.81</td>
<td>10.38 / 8.31</td>
<td>66.52 / 30.83</td>
<td>80.5</td>
<td rowspan="1">
SVTRv2 是一种由复旦大学视觉与学习实验室（FVL）的OpenOCR团队研发的服务端文本识别模型，其在PaddleOCR算法模型挑战赛 - 赛题一：OCR端到端识别任务中荣获一等奖，A榜端到端识别精度相比PP-OCRv4提升6%。
</td>
</tr>
</table>

<table>
<tr>
<th>模型</th><th>模型下载链接</th>
<th>识别 Avg Accuracy(%)</th>
<th>GPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>CPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
<tr>
<td>ch_RepSVTR_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/ch_RepSVTR_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/ch_RepSVTR_rec_pretrained.pdparams">训练模型</a></td>
<td>65.07</td>
<td>6.29 / 1.57</td>
<td>20.64 / 5.40</td>
<td>48.8</td>
<td rowspan="1">    RepSVTR 文本识别模型是一种基于SVTRv2 的移动端文本识别模型，其在PaddleOCR算法模型挑战赛 - 赛题一：OCR端到端识别任务中荣获一等奖，B榜端到端识别精度相比PP-OCRv4提升2.5%，推理速度持平。</td>
</tr>
</table>

* <b>英文识别模型</b>
<table>
<tr>
<th>模型</th><th>模型下载链接</th>
<th>识别 Avg Accuracy(%)</th>
<th>GPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>CPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
<tr>
<td>en_PP-OCRv4_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
en_PP-OCRv4_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/en_PP-OCRv4_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td> 70.39</td>
<td>4.81 / 1.23</td>
<td>17.20 / 4.18</td>
<td>7.5</td>
<td>基于PP-OCRv4识别模型训练得到的超轻量英文识别模型，支持英文、数字识别</td>
</tr>
<tr>
<td>en_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
en_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/en_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>70.69</td>
<td>3.56 / 0.78</td>
<td>8.44 / 5.78</td>
<td>17.3</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量英文识别模型，支持英文、数字识别</td>
</tr>
</table>


* <b>多语言识别模型</b>
<table>
<tr>
<th>模型</th><th>模型下载链接</th>
<th>识别 Avg Accuracy(%)</th>
<th>GPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>CPU推理耗时（ms）<br/>[常规模式 / 高性能模式]</th>
<th>模型存储大小（MB）</th>
<th>介绍</th>
</tr>
<tr>
<td>korean_PP-OCRv5_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
korean_PP-OCRv5_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/korean_PP-OCRv5_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>88.0</td>
<td>5.43 / 1.46</td>
<td>21.20 / 5.32</td>
<td>14</td>
<td>基于PP-OCRv5识别模型训练得到的超轻量韩文识别模型，支持韩文、英文和数字识别</td>
</tr>
<tr>
<td>latin_PP-OCRv5_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
latin_PP-OCRv5_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/latin_PP-OCRv5_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>84.7</td>
<td>5.43 / 1.46</td>
<td>21.20 / 5.32</td>
<td>14</td>
<td>基于PP-OCRv5识别模型训练得到的拉丁文识别模型，支持大部分拉丁字母语言、数字识别</td>
</tr>
<tr>
<td>eslav_PP-OCRv5_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
eslav_PP-OCRv5_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/eslav_PP-OCRv5_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>81.6</td>
<td>5.43 / 1.46</td>
<td>21.20 / 5.32</td>
<td>14</td>
<td>基于PP-OCRv5识别模型训练得到的东斯拉夫语言识别模型， 支持东斯拉夫语言、英文和数字识别</td>
</tr>
<tr>
<td>korean_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
korean_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/korean_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>60.21</td>
<td>3.73 / 0.98</td>
<td>8.76 / 2.91</td>
<td>9.6</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量韩文识别模型，支持韩文、数字识别</td>
</tr>
<tr>
<td>japan_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
japan_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/japan_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>45.69</td>
<td>3.86 / 1.01</td>
<td>8.62 / 2.92</td>
<td>9.8</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量日文识别模型，支持日文、数字识别</td>
</tr>
<tr>
<td>chinese_cht_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
chinese_cht_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/chinese_cht_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>82.06</td>
<td>3.90 / 1.16</td>
<td>9.24 / 3.18</td>
<td>10.8</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量繁体中文识别模型，支持繁体中文、数字识别</td>
</tr>
<tr>
<td>te_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
te_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/te_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>95.88</td>
<td>3.59 / 0.81</td>
<td>8.28 / 6.21</td>
<td>8.7</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量泰卢固文识别模型，支持泰卢固文、数字识别</td>
</tr>
<tr>
<td>ka_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
ka_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/ka_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>96.96</td>
<td>3.49 / 0.89</td>
<td>8.63 / 2.77</td>
<td>17.4</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量卡纳达文识别模型，支持卡纳达文、数字识别</td>
</tr>
<tr>
<td>ta_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
ta_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/ta_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>76.83</td>
<td>3.49 / 0.86</td>
<td>8.35 / 3.41</td>
<td>8.7</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量泰米尔文识别模型，支持泰米尔文、数字识别</td>
</tr>
<tr>
<td>latin_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
latin_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/latin_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>76.93</td>
<td>3.53 / 0.78</td>
<td>8.50 / 6.83</td>
<td>8.7</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量拉丁文识别模型，支持拉丁文、数字识别</td>
</tr>
<tr>
<td>arabic_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
arabic_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/arabic_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>73.55</td>
<td>3.60 / 0.83</td>
<td>8.44 / 4.69</td>
<td>17.3</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量阿拉伯字母识别模型，支持阿拉伯字母、数字识别</td>
</tr>
<tr>
<td>cyrillic_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
cyrillic_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/cyrillic_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>94.28</td>
<td>3.56 / 0.79</td>
<td>8.22 / 2.76</td>
<td>8.7</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量斯拉夫字母识别模型，支持斯拉夫字母、数字识别</td>
</tr>
<tr>
<td>devanagari_PP-OCRv3_mobile_rec</td>
<td><a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_inference_model/paddle3.0.0/\
devanagari_PP-OCRv3_mobile_rec_infer.tar">推理模型</a>/<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/official_pretrained_model/devanagari_PP-OCRv3_mobile_rec_pretrained.pdparams">训练模型</a></td>
<td>96.44</td>
<td>3.60 / 0.78</td>
<td>6.95 / 2.87</td>
<td>8.7</td>
<td>基于PP-OCRv3识别模型训练得到的超轻量梵文字母识别模型，支持梵文字母、数字识别</td>
</tr>
</table>
</details>
</details>

<details>
<summary><strong>测试环境说明:</strong></summary>

  <ul>
      <li><b>性能测试环境</b>
          <ul>
            <li><strong>测试数据集：
             </strong>
                <ul>
                  <li>文档图像方向分类模型：PaddleOCR 自建的数据集，覆盖证件和文档等多个场景，包含 1000 张图片。</li>
                  <li>文本图像矫正模型：<a href="https://www3.cs.stonybrook.edu/~cvl/docunet.html">DocUNet</a>。</li>
                  <li>文本检测模型：PaddleOCR 自建的中文数据集，覆盖街景、网图、文档、手写多个场景，其中检测包含 500 张图片。</li>
                  <li>中文识别模型： PaddleOCR 自建的中文数据集，覆盖街景、网图、文档、手写多个场景，其中文本识别包含 1.1w 张图片。</li>
                  <li>ch_SVTRv2_rec：<a href="https://aistudio.baidu.com/competition/detail/1131/0/introduction">PaddleOCR算法模型挑战赛 - 赛题一：OCR端到端识别任务</a>A榜评估集。</li>
                  <li>ch_RepSVTR_rec：<a href="https://aistudio.baidu.com/competition/detail/1131/0/introduction">PaddleOCR算法模型挑战赛 - 赛题一：OCR端到端识别任务</a>B榜评估集。</li>
                  <li>英文识别模型：PaddleOCR 自建的英文数据集。</li>
                  <li>多语言识别模型：PaddleOCR 自建的多语种数据集。</li>
                  <li>文本行方向分类模型：PaddleOCR 自建的数据集，覆盖证件和文档等多个场景，包含 1000 张图片。</li>
                </ul>
             </li>
              <li><strong>硬件配置：</strong>
                  <ul>
                      <li>GPU：NVIDIA Tesla T4</li>
                      <li>CPU：Intel Xeon Gold 6271C @ 2.60GHz</li>
                  </ul>
              </li>
              <li><strong>软件环境：</strong>
                  <ul>
                      <li>Ubuntu 20.04 / CUDA 11.8 / cuDNN 8.9 / TensorRT 8.6.1.6</li>
                      <li>paddlepaddle 3.0.0 / paddleocr 3.0.3</li>
                  </ul>
              </li>
          </ul>
      </li>
      <li><b>推理模式说明</b></li>
  </ul>

<table border="1">
    <thead>
        <tr>
            <th>模式</th>
            <th>GPU配置</th>
            <th>CPU配置</th>
            <th>加速技术组合</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>常规模式</td>
            <td>FP32精度 / 无TRT加速</td>
            <td>FP32精度 / 8线程</td>
            <td>PaddleInference</td>
        </tr>
        <tr>
            <td>高性能模式</td>
            <td>选择先验精度类型和加速策略的最优组合</td>
            <td>FP32精度 / 8线程</td>
            <td>选择先验最优后端（Paddle/OpenVINO/TRT等）</td>
        </tr>
    </tbody>
</table>

</details>

<br />
<b>如果您更注重模型的精度，请选择精度较高的模型；如果您更在意模型的推理速度，请选择推理速度较快的模型；如果您关注模型的存储大小，请选择存储体积较小的模型。</b>

## 2. 快速开始

在本地使用通用OCR产线前，请确保您已经按照[安装教程](../installation.md)完成了wheel包安装。安装完成后，可以在本地使用命令行体验或 Python 集成。

**请注意，如果在执行过程中遇到程序失去响应、程序异常退出、内存资源耗尽、推理速度极慢等问题，请尝试参考文档调整配置，例如关闭不需要使用的功能或使用更轻量的模型。**

### 2.1 命令行方式

一行命令即可快速体验OCR产线效果。运行以下代码前，请您下载[示例图片](https://paddle-model-ecology.bj.bcebos.com/paddlex/imgs/demo_image/general_ocr_002.png)到本地：

```bash
# 默认使用 PP-OCRv5 模型
paddleocr ocr -i https://paddle-model-ecology.bj.bcebos.com/paddlex/imgs/demo_image/general_ocr_002.png \
    --use_doc_orientation_classify False \
    --use_doc_unwarping False \
    --use_textline_orientation False \
    --save_path ./output \
    --device gpu:0 

# 通过 --ocr_version 指定 PP-OCR 其他版本
paddleocr ocr -i ./general_ocr_002.png --ocr_version PP-OCRv4
```

<details><summary><b>命令行支持更多参数设置，点击展开以查看命令行参数的详细说明</b></summary>
<table>
<thead>
<tr>
<th>参数</th>
<th>参数说明</th>
<th>参数类型</th>
<th>默认值</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>input</code></td>
<td>待预测数据，必填。如图像文件或者PDF文件的本地路径：<code>/root/data/img.jpg</code>；<b>如URL链接</b>，如图像文件或PDF文件的网络URL：<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/imgs/demo_image/general_ocr_002.png">示例</a>；<b>如本地目录</b>，该目录下需包含待预测图像，如本地路径：<code>/root/data/</code>(当前不支持目录中包含PDF文件的预测，PDF文件需要指定到具体文件路径)。
</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>save_path</code></td>
<td>指定推理结果文件保存的路径。如果不设置，推理结果将不会保存到本地。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>doc_orientation_classify_model_name</code></td>
<td>文档方向分类模型的名称。如果不设置，将会使用产线默认模型。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>doc_orientation_classify_model_dir</code></td>
<td>文档方向分类模型的目录路径。如果不设置，将会下载官方模型。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>doc_unwarping_model_name</code></td>
<td>文本图像矫正模型的名称。如果不设置，将会使用产线默认模型。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>doc_unwarping_model_dir</code></td>
<td>文本图像矫正模型的目录路径。如果不设置，将会下载官方模型。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>text_detection_model_name</code></td>
<td>文本检测模型的名称。如果不设置，将会使用产线默认模型。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>text_detection_model_dir</code></td>
<td>文本检测模型的目录路径。如果不设置，将会下载官方模型。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>textline_orientation_model_name</code></td>
<td>文本行方向模型的名称。如果不设置，将会使用产线默认模型。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>textline_orientation_model_dir</code></td>
<td>文本行方向模型的目录路径。如果不设置，将会下载官方模型。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>textline_orientation_batch_size</code></td>
<td>文本行方向模型的batch size。如果不设置，将默认设置batch size为<code>1</code>。</td>
<td><code>int</code></td>
<td></td>
</tr>
<tr>
<td><code>text_recognition_model_name</code></td>
<td>文本识别模型的名称。如果不设置，将会使用产线默认模型。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>text_recognition_model_dir</code></td>
<td>文本识别模型的目录路径。如果不设置，将会下载官方模型。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>text_recognition_batch_size</code></td>
<td>文本识别模型的batch size。如果不设置，将默认设置batch size为<code>1</code>。</td>
<td><code>int</code></td>
<td></td>
</tr>
<tr>
<td><code>use_doc_orientation_classify</code></td>
<td>是否加载并使用文档方向分类模块。如果不设置，将使用产线初始化的该参数值，默认初始化为<code>True</code>。</td>
<td><code>bool</code></td>
<td></td>
</tr>
<tr>
<td><code>use_doc_unwarping</code></td>
<td>是否加载并使用文本图像矫正模块。如果不设置，将使用产线初始化的该参数值，默认初始化为<code>True</code>。</td>
<td><code>bool</code></td>
<td></td>
</tr>
<tr>
<td><code>use_textline_orientation</code></td>
<td>是否加载并使用文本行方向模块。如果不设置，将使用产线初始化的该参数值，默认初始化为<code>True</code>。</td>
<td><code>bool</code></td>
<td></td>
</tr>
<tr>
<td><code>text_det_limit_side_len</code></td>
<td>文本检测的图像边长限制。
大于 <code>0</code> 的任意整数。如果不设置，将使用产线初始化的该参数值，默认初始化为 <code>64</code>。
</td>
<td><code>int</code></td>
<td></td>
</tr>
<tr>
<td><code>text_det_limit_type</code></td>
<td>文本检测的边长度限制类型。支持 <code>min</code> 和 <code>max</code>，<code>min</code> 表示保证图像最短边不小于 <code>det_limit_side_len</code>，<code>max</code> 表示保证图像最长边不大于 <code>limit_side_len</code>。如果不设置，将使用产线初始化的该参数值，默认初始化为 <code>min</code>。
</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>text_det_thresh</code></td>
<td>文本检测像素阈值，输出的概率图中，得分大于该阈值的像素点才会被认为是文字像素点。
大于<code>0</code>的任意浮点数。如果不设置，将使用产线初始化的该参数值（默认为 <code>0.3</code>）。
</td>
<td><code>float</code></td>
<td></td>
</tr>
<tr>
<td><code>text_det_box_thresh</code></td>
<td>文本检测框阈值，检测结果边框内，所有像素点的平均得分大于该阈值时，该结果会被认为是文字区域。
大于 <code>0</code> 的任意浮点数。如果不设置，将使用产线初始化的该参数值（默认为 <code>0.6</code>）。
</td>
<td><code>float</code></td>
<td></td>
</tr>
<tr>
<td><code>text_det_unclip_ratio</code></td>
<td>文本检测扩张系数，使用该方法对文字区域进行扩张，该值越大，扩张的面积越大。大于 <code>0</code> 的任意浮点数。如果不设置，将使用产线初始化的该参数值（默认为 <code>2.0</code>）。
</td>
<td><code>float</code></td>
<td></td>
</tr>
<tr>
<td><code>text_det_input_shape</code></td>
<td>文本检测的输入形状，您可以设置3个值代表C，H，W。</td>
<td><code>int</code></td>
<td></td>
</tr>
<tr>
<td><code>text_rec_score_thresh</code></td>
<td>文本识别阈值，得分大于该阈值的文本结果会被保留。
大于<code>0</code>的任意浮点数。如果不设置，将使用产线初始化的该参数值（默认为 <code>0.0</code>，即不设阈值）。
</td>
<td><code>float</code></td>
<td></td>
</tr>
<tr>
<td><code>text_rec_input_shape</code></td>
<td>文本识别的输入形状。</td>
<td><code>tuple</code></td>
<td></td>
</tr>
<tr>
<td><code>lang</code></td>
<td>使用指定语言的 OCR 模型。
附录中的表格中列举了全部支持的语言。
</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>ocr_version</code></td>
<td>OCR 模型版本。
<ul>
<li><b>PP-OCRv5</b>：使用PP-OCRv5系列模型；
<li><b>PP-OCRv4</b>：使用PP-OCRv4系列模型；
<li><b>PP-OCRv3</b>：使用PP-OCRv3系列模型。
</ul>
注意不是每个<code>ocr_version</code>都支持所有的<code>lang</code>，请查看附录中的对应关系表。
</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>det_model_dir</code></td>
<td>已废弃，请参考<code>text_detection_model_dir</code>，且与新的参数不能同时指定。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>det_limit_side_len</code></td>
<td>已废弃，请参考<code>text_det_limit_side_len</code>，且与新的参数不能同时指定。</td>
<td><code>int</code></td>
<td></td>
</tr>
<tr>
<td><code>det_limit_type</code></td>
<td>已废弃，请参考<code>text_det_limit_type</code>，且与新的参数不能同时指定。
</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>det_db_thresh</code></td>
<td>已废弃，请参考<code>text_det_thresh</code>，且与新的参数不能同时指定。
</td>
<td><code>float</code></td>
<td></td>
</tr>
<tr>
<td><code>det_db_box_thresh</code></td>
<td>已废弃，请参考<code>text_det_box_thresh</code>，且与新的参数不能同时指定。
</td>
<td><code>float</code></td>
<td></td>
</tr>
<tr>
<td><code>det_db_unclip_ratio</code></td>
<td>已废弃，请参考<code>text_det_unclip_ratio</code>，且与新的参数不能同时指定。
</td>
<td><code>float</code></td>
<td></td>
</tr>
<tr>
<td><code>rec_model_dir</code></td>
<td>已废弃，请参考<code>text_recognition_model_dir</code>，且与新的参数不能同时指定。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>rec_batch_num</code></td>
<td>已废弃，请参考<code>text_recognition_batch_size</code>，且与新的参数不能同时指定。</td>
<td><code>int</code></td>
<td></td>
</tr>
<tr>
<td><code>use_angle_cls</code></td>
<td>已废弃，请参考<code>use_textline_orientation</code>，且与新的参数不能同时指定。</td>
<td><code>bool</code></td>
<td></td>
</tr>
<tr>
<td><code>cls_model_dir</code></td>
<td>已废弃，请参考<code>textline_orientation_model_dir</code>，且与新的参数不能同时指定。</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>cls_batch_num</code></td>
<td>已废弃，请参考<code>textline_orientation_batch_size</code>，且与新的参数不能同时指定。</td>
<td><code>int</code></td>
<td></td>
</tr>
<tr>
<td><code>device</code></td>
<td>用于推理的设备。支持指定具体卡号：
<ul>
<li><b>CPU</b>：如 <code>cpu</code> 表示使用 CPU 进行推理；</li>
<li><b>GPU</b>：如 <code>gpu:0</code> 表示使用第 1 块 GPU 进行推理；</li>
<li><b>NPU</b>：如 <code>npu:0</code> 表示使用第 1 块 NPU 进行推理；</li>
<li><b>XPU</b>：如 <code>xpu:0</code> 表示使用第 1 块 XPU 进行推理；</li>
<li><b>MLU</b>：如 <code>mlu:0</code> 表示使用第 1 块 MLU 进行推理；</li>
<li><b>DCU</b>：如 <code>dcu:0</code> 表示使用第 1 块 DCU 进行推理；</li>
</ul>如果不设置，将默认使用产线初始化的该参数值，初始化时，会优先使用本地的 GPU 0号设备，如果没有，则使用 CPU 设备。
</td>
<td><code>str</code></td>
<td></td>
</tr>
<tr>
<td><code>enable_hpi</code></td>
<td>是否启用高性能推理。</td>
<td><code>bool</code></td>
<td><code>False</code></td>
</tr>
<tr>
<td><code>use_tensorrt</code></td>
<td>是否启用 Paddle Inference 的 TensorRT 子图引擎。如果模型不支持通过 TensorRT 加速，即使设置了此标志，也不会使用加速。<br/>
对于 CUDA 11.8 版本的飞桨，兼容的 TensorRT 版本为 8.x（x>=6），建议安装 TensorRT 8.6.1.6。<br/>
对于 CUDA 12.6 版本的飞桨，兼容的 TensorRT 版本为 10.x（x>=5），建议安装 TensorRT 10.5.0.18。
</td>
<td><code>bool</code></td>
<td><code>False</code></td>
</tr>
<tr>
<td><code>precision</code></td>
<td>计算精度，如 fp32、fp16。</td>
<td><code>str</code></td>
<td><code>fp32</code></td>
</tr>
<tr>
<td><code>enable_mkldnn</code></td>
<td>是否启用 MKL-DNN 加速推理。如果 MKL-DNN 不可用或模型不支持通过 MKL-DNN 加速，即使设置了此标志，也不会使用加速。
</td>
<td><code>bool</code></td>
<td><code>True</code></td>
</tr>
<tr>
<td><code>mkldnn_cache_capacity</code></td>
<td>
MKL-DNN 缓存容量。
</td>
<td><code>int</code></td>
<td><code>10</code></td>
</tr>
<tr>
<td><code>cpu_threads</code></td>
<td>在 CPU 上进行推理时使用的线程数。</td>
<td><code>int</code></td>
<td><code>8</code></td>
</tr>
<tr>
<td><code>paddlex_config</code></td>
<td>PaddleX产线配置文件路径。</td>
<td><code>str</code></td>
<td></td>
</tr>
</tbody>
</table>
</details>
<br />

运行结果会被打印到终端上：

```bash
{'res': {'input_path': './general_ocr_002.png', 'page_index': None, 'model_settings': {'use_doc_preprocessor': True, 'use_textline_orientation': False}, 'doc_preprocessor_res': {'input_path': None, 'page_index': None, 'model_settings': {'use_doc_orientation_classify': False, 'use_doc_unwarping': False}, 'angle': -1}, 'dt_polys': array([[[  3,  10],
        ...,
        [  4,  30]],

       ...,

       [[ 99, 456],
        ...,
        [ 99, 479]]], dtype=int16), 'text_det_params': {'limit_side_len': 736, 'limit_type': 'min', 'thresh': 0.3, 'max_side_limit': 4000, 'box_thresh': 0.6, 'unclip_ratio': 1.5}, 'text_type': 'general', 'textline_orientation_angles': array([-1, ..., -1]), 'text_rec_score_thresh': 0.0, 'rec_texts': ['www.997700', '', 'Cm', '登机牌', 'BOARDING', 'PASS', 'CLASS', '序号SERIAL NO.', '座位号', 'SEAT NO.', '航班FLIGHT', '日期DATE', '舱位', '', 'W', '035', '12F', 'MU2379', '03DEc', '始发地', 'FROM', '登机口', 'GATE', '登机时间BDT', '目的地TO', '福州', 'TAIYUAN', 'G11', 'FUZHOU', '身份识别IDNO.', '姓名NAME', 'ZHANGQIWEI', '票号TKT NO.', '张祺伟', '票价FARE', 'ETKT7813699238489/1', '登机口于起飞前10分钟关闭 GATESCL0SE10MINUTESBEFOREDEPARTURETIME'], 'rec_scores': array([0.67634439, ..., 0.97416091]), 'rec_polys': array([[[  3,  10],
        ...,
        [  4,  30]],

       ...,

       [[ 99, 456],
        ...,
        [ 99, 479]]], dtype=int16), 'rec_boxes': array([[  3, ...,  30],
       ...,
       [ 99, ..., 479]], dtype=int16)}}
```

若指定了`save_path`，则会保存可视化结果在`save_path`下。可视化结果如下：

<img src="https://raw.githubusercontent.com/cuicheng01/PaddleX_doc_images/main/images/pipelines/ocr/03.png"/>


### 2.2 Python脚本方式集成

命令行方式是为了快速体验查看效果，一般来说，在项目中，往往需要通过代码集成，您可以通过几行代码即可完成产线的快速推理，推理代码如下：

```python
from paddleocr import PaddleOCR

ocr = PaddleOCR(
    use_doc_orientation_classify=False, # 通过 use_doc_orientation_classify 参数指定不使用文档方向分类模型
    use_doc_unwarping=False, # 通过 use_doc_unwarping 参数指定不使用文本图像矫正模型
    use_textline_orientation=False, # 通过 use_textline_orientation 参数指定不使用文本行方向分类模型
)
# ocr = PaddleOCR(lang="en") # 通过 lang 参数来使用英文模型
# ocr = PaddleOCR(ocr_version="PP-OCRv4") # 通过 ocr_version 参数来使用 PP-OCR 其他版本
# ocr = PaddleOCR(device="gpu") # 通过 device 参数使得在模型推理时使用 GPU
# ocr = PaddleOCR(
#     text_detection_model_name="PP-OCRv5_server_det",
#     text_recognition_model_name="PP-OCRv5_server_rec",
#     use_doc_orientation_classify=False,
#     use_doc_unwarping=False,
#     use_textline_orientation=False,
# ) # 更换 PP-OCRv5_server 模型
result = ocr.predict("./general_ocr_002.png")
for res in result:
    res.print()
    res.save_to_img("output")
    res.save_to_json("output")
```

在上述 Python 脚本中，执行了如下几个步骤：

<details><summary>（1）通过 <code>PaddleOCR()</code> 实例化 OCR 产线对象，具体参数说明如下：</summary>

<table>
  <thead>
    <tr>
      <th>参数</th>
      <th>参数说明</th>
      <th>参数类型</th>
      <th>默认值</th>
    </tr>
  </thead>
  <tbody>
<tr>
<td><code>doc_orientation_classify_model_name</code></td>
<td>文档方向分类模型的名称。如果设置为<code>None</code>，将会使用产线默认模型。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>doc_orientation_classify_model_dir</code></td>
<td>文档方向分类模型的目录路径。如果设置为<code>None</code>，将会下载官方模型。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>doc_unwarping_model_name</code></td>
<td>文本图像矫正模型的名称。如果设置为<code>None</code>，将会使用产线默认模型。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>doc_unwarping_model_dir</code></td>
<td>文本图像矫正模型的目录路径。如果设置为<code>None</code>，将会下载官方模型。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_detection_model_name</code></td>
<td>文本检测模型的名称。如果设置为<code>None</code>，将会使用产线默认模型。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_detection_model_dir</code></td>
<td>文本检测模型的目录路径。如果设置为<code>None</code>，将会下载官方模型。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>textline_orientation_model_name</code></td>
<td>文本行方向模型的名称。如果设置为<code>None</code>，将会使用产线默认模型。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>textline_orientation_model_dir</code></td>
<td>文本行方向模型的目录路径。如果设置为<code>None</code>，将会下载官方模型。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>textline_orientation_batch_size</code></td>
<td>文本行方向模型的batch size。如果设置为<code>None</code>，将默认设置batch size为<code>1</code>。</td>
<td><code>int|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_recognition_model_name</code></td>
<td>文本识别模型的名称。如果设置为<code>None</code>，将会使用产线默认模型。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_recognition_model_dir</code></td>
<td>文本识别模型的目录路径。如果设置为<code>None</code>，将会下载官方模型。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_recognition_batch_size</code></td>
<td>文本识别模型的batch size。如果设置为<code>None</code>，将默认设置batch size为<code>1</code>。</td>
<td><code>int|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>use_doc_orientation_classify</code></td>
<td>是否加载并使用文档方向分类模块。如果设置为<code>None</code>，将使用产线初始化的该参数值，默认初始化为<code>True</code>。</td>
<td><code>bool|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>use_doc_unwarping</code></td>
<td>是否加载并使用文本图像矫正模块。如果设置为<code>None</code>，将使用产线初始化的该参数值，默认初始化为<code>True</code>。</td>
<td><code>bool|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>use_textline_orientation</code></td>
<td>是否加载并使用文本行方向模块。如果设置为<code>None</code>，将使用产线初始化的该参数值，默认初始化为<code>True</code>。</td>
<td><code>bool|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_det_limit_side_len</code></td>
<td>文本检测的图像边长限制。
<ul>
<li><b>int</b>：大于 <code>0</code> 的任意整数；</li>
<li><b>None</b>：如果设置为<code>None</code>，将使用产线初始化的该参数值，默认初始化为 <code>64</code>。</li>
</ur>
</td>
<td><code>int|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_det_limit_type</code></td>
<td>文本检测的边长度限制类型。
<ul>
<li><b>str</b>：支持 <code>min</code> 和 <code>max</code>，<code>min</code> 表示保证图像最短边不小于 <code>det_limit_side_len</code>，<code>max</code> 表示保证图像最长边不大于 <code>limit_side_len</code>；</li>
<li><b>None</b>：如果设置为<code>None</code>，将使用产线初始化的该参数值，默认初始化为 <code>min</code>。</li>
</ur>
</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_det_thresh</code></td>
<td>文本检测像素阈值，输出的概率图中，得分大于该阈值的像素点才会被认为是文字像素点。
<ul>
<li><b>float</b>：大于<code>0</code>的任意浮点数；
<li><b>None</b>：如果设置为<code>None</code>，将使用产线初始化的该参数值（默认为<code>0.3</code>）。</li>
</td>
<td><code>float|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_det_box_thresh</code></td>
<td>文本检测框阈值，检测结果边框内，所有像素点的平均得分大于该阈值时，该结果会被认为是文字区域。
<ul>
<li><b>float</b>：大于<code>0</code>的任意浮点数；
<li><b>None</b>：如果设置为<code>None</code>，将使用产线初始化的该参数值（默认为<code>0.6</code>）。
</td>
<td><code>float|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_det_unclip_ratio</code></td>
<td>文本检测扩张系数，使用该方法对文字区域进行扩张，该值越大，扩张的面积越大。
<ul>
<li><b>float</b>：大于<code>0</code>的任意浮点数；
<li><b>None</b>：如果设置为<code>None</code>，将使用产线初始化的该参数值（默认为<code>2.0</code>）。
</ur>
</td>
<td><code>float|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_det_input_shape</code></td>
<td>文本检测的输入形状。</td>
<td><code>tuple|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_rec_score_thresh</code></td>
<td>文本识别阈值，得分大于该阈值的文本结果会被保留。
<ul>
<li><b>float</b>：大于<code>0</code>的任意浮点数；
<li><b>None</b>：如果设置为<code>None</code>，将使用产线初始化的该参数值（默认为<code>0.0</code>，即不设阈值）。
</ur>
</td>
<td><code>float|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>text_rec_input_shape</code></td>
<td>文本识别的输入形状。</td>
<td><code>tuple|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>lang</code></td>
<td>使用指定语言的 OCR 模型。
附录中的表格中列举了全部支持的语言。
</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>ocr_version</code></td>
<td>OCR 模型版本。
<ul>
<li><b>PP-OCRv5</b>：使用PP-OCRv5系列模型；
<li><b>PP-OCRv4</b>：使用PP-OCRv4系列模型；
<li><b>PP-OCRv3</b>：使用PP-OCRv3系列模型。
</ul>
注意不是每个<code>ocr_version</code>都支持所有的<code>lang</code>，请查看附录中的对应关系表。
</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>device</code></td>
<td>用于推理的设备。支持指定具体卡号：
<ul>
<li><b>CPU</b>：如 <code>cpu</code> 表示使用 CPU 进行推理；</li>
<li><b>GPU</b>：如 <code>gpu:0</code> 表示使用第 1 块 GPU 进行推理；</li>
<li><b>NPU</b>：如 <code>npu:0</code> 表示使用第 1 块 NPU 进行推理；</li>
<li><b>XPU</b>：如 <code>xpu:0</code> 表示使用第 1 块 XPU 进行推理；</li>
<li><b>MLU</b>：如 <code>mlu:0</code> 表示使用第 1 块 MLU 进行推理；</li>
<li><b>DCU</b>：如 <code>dcu:0</code> 表示使用第 1 块 DCU 进行推理；</li>
<li><b>None</b>：如果设置为<code>None</code>，将默认使用产线初始化的该参数值，初始化时，会优先使用本地的 GPU 0号设备，如果没有，则使用 CPU 设备。
</ur>
</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>enable_hpi</code></td>
<td>是否启用高性能推理。</td>
<td><code>bool</code></td>
<td><code>False</code></td>
</tr>
<tr>
<td><code>use_tensorrt</code></td>
<td>是否启用 Paddle Inference 的 TensorRT 子图引擎。如果模型不支持通过 TensorRT 加速，即使设置了此标志，也不会使用加速。<br/>
对于 CUDA 11.8 版本的飞桨，兼容的 TensorRT 版本为 8.x（x>=6），建议安装 TensorRT 8.6.1.6。<br/>
对于 CUDA 12.6 版本的飞桨，兼容的 TensorRT 版本为 10.x（x>=5），建议安装 TensorRT 10.5.0.18。
</td>
<td><code>bool</code></td>
<td><code>False</code></td>
</tr>
<tr>
<td><code>precision</code></td>
<td>计算精度，如 fp32、fp16。</td>
<td><code>str</code></td>
<td><code>"fp32"</code></td>
</tr>
<tr>
<td><code>enable_mkldnn</code></td>
<td>是否启用 MKL-DNN 加速推理。如果 MKL-DNN 不可用或模型不支持通过 MKL-DNN 加速，即使设置了此标志，也不会使用加速。
<td><code>bool</code></td>
<td><code>True</code></td>
</tr>
<tr>
<td><code>mkldnn_cache_capacity</code></td>
<td>
MKL-DNN 缓存容量。
</td>
<td><code>int</code></td>
<td><code>10</code></td>
</tr>
<tr>
<td><code>cpu_threads</code></td>
<td>在 CPU 上进行推理时使用的线程数。</td>
<td><code>int</code></td>
<td><code>8</code></td>
</tr>
<tr>
<td><code>paddlex_config</code></td>
<td>PaddleX产线配置文件路径。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
</tbody>
</table>
</details>

<details><summary>（2）调用 OCR 产线对象的 <code>predict()</code> 方法进行推理预测，该方法会返回一个结果列表。另外，产线还提供了 <code>predict_iter()</code> 方法。两者在参数接受和结果返回方面是完全一致的，区别在于 <code>predict_iter()</code> 返回的是一个 <code>generator</code>，能够逐步处理和获取预测结果，适合处理大型数据集或希望节省内存的场景。可以根据实际需求选择使用这两种方法中的任意一种。以下是 <code>predict()</code> 方法的参数及其说明：</summary>

<table>
<thead>
<tr>
<th>参数</th>
<th>参数说明</th>
<th>参数类型</th>
<th>默认值</th>
</tr>
</thead>
<tr>
<td><code>input</code></td>
<td>待预测数据，支持多种输入类型，必填。
<ul>
<li><b>Python Var</b>：如 <code>numpy.ndarray</code> 表示的图像数据；</li>
<li><b>str</b>：如图像文件或者PDF文件的本地路径：<code>/root/data/img.jpg</code>；<b>如URL链接</b>，如图像文件或PDF文件的网络URL：<a href="https://paddle-model-ecology.bj.bcebos.com/paddlex/imgs/demo_image/general_ocr_002.png">示例</a>；<b>如本地目录</b>，该目录下需包含待预测图像，如本地路径：<code>/root/data/</code>(当前不支持目录中包含PDF文件的预测，PDF文件需要指定到具体文件路径)；</li>
<li><b>list</b>：列表元素需为上述类型数据，如<code>[numpy.ndarray, numpy.ndarray]</code>，<code>["/root/data/img1.jpg", "/root/data/img2.jpg"]</code>，<code>["/root/data1", "/root/data2"]。</code></li>
</ul>
</td>
<td><code>Python Var|str|list</code></td>
<td></td>
</tr>
<tr>
<td><code>use_doc_orientation_classify</code></td>
<td>是否在推理时使用文档方向分类模块。</td>
<td><code>bool|None</code></td>
<td><code>None</code></td>
</tr>
<tr>
<td><code>use_doc_unwarping</code></td>
<td>是否在推理时使用文本图像矫正模块。</td>
<td><code>bool|None</code></td>
<td><code>None</code></td>
</tr>
<td><code>use_textline_orientation</code></td>
<td>是否在推理时使用文本行方向分类模块。</td>
<td><code>bool|None</code></td>
<td><code>None</code></td>
</tr>
<td><code>text_det_limit_side_len</code></td>
<td>参数含义与实例化参数基本相同。设置为<code>None</code>表示使用实例化参数，否则该参数优先级更高。</td>
<td><code>int|None</code></td>
<td><code>None</code></td>
</tr>
<td><code>text_det_limit_type</code></td>
<td>参数含义与实例化参数基本相同。设置为<code>None</code>表示使用实例化参数，否则该参数优先级更高。</td>
<td><code>str|None</code></td>
<td><code>None</code></td>
</tr>
<td><code>text_det_thresh</code></td>
<td>参数含义与实例化参数基本相同。设置为<code>None</code>表示使用实例化参数，否则该参数优先级更高。</td>
<td><code>float|None</code></td>
<td><code>None</code></td>
</tr>
<td><code>text_det_box_thresh</code></td>
<td>参数含义与实例化参数基本相同。设置为<code>None</code>表示使用实例化参数，否则该参数优先级更高。</td>
<td><code>float|None</code></td>
<td><code>None</code></td>
</tr>
<td><code>text_det_unclip_ratio</code></td>
<td>参数含义与实例化参数基本相同。设置为<code>None</code>表示使用实例化参数，否则该参数优先级更高。</td>
<td><code>float|None</code></td>
<td><code>None</code></td>
</tr>
<td><code>text_rec_score_thresh</code></td>
<td>参数含义与实例化参数基本相同。设置为<code>None</code>表示使用实例化参数，否则该参数优先级更高。</td>
<td><code>float|None</code></td>
<td><code>None</code></td>
</table>
</details>

<details><summary>（3）对预测结果进行处理，每个样本的预测结果均为对应的Result对象，且支持打印、保存为图片、保存为<code>json</code>文件的操作:</summary>

<table>
<thead>
<tr>
<th>方法</th>
<th>方法说明</th>
<th>参数</th>
<th>参数类型</th>
<th>参数说明</th>
<th>默认值</th>
</tr>
</thead>
<tr>
<td rowspan="3"><code>print()</code></td>
<td rowspan="3">打印结果到终端</td>
<td><code>format_json</code></td>
<td><code>bool</code></td>
<td>是否对输出内容进行使用 <code>JSON</code> 缩进格式化。</td>
<td><code>True</code></td>
</tr>
<tr>
<td><code>indent</code></td>
<td><code>int</code></td>
<td>指定缩进级别，以美化输出的 <code>JSON</code> 数据，使其更具可读性，仅当 <code>format_json</code> 为 <code>True</code> 时有效。</td>
<td>4</td>
</tr>
<tr>
<td><code>ensure_ascii</code></td>
<td><code>bool</code></td>
<td>控制是否将非 <code>ASCII</code> 字符转义为 <code>Unicode</code>。设置为 <code>True</code> 时，所有非 <code>ASCII</code> 字符将被转义；<code>False</code> 则保留原始字符，仅当<code>format_json</code>为<code>True</code>时有效。</td>
<td><code>False</code></td>
</tr>
<tr>
<td rowspan="3"><code>save_to_json()</code></td>
<td rowspan="3">将结果保存为json格式的文件</td>
<td><code>save_path</code></td>
<td><code>str</code></td>
<td>保存的文件路径，当为目录时，保存文件命名与输入文件类型命名一致。</td>
<td>无</td>
</tr>
<tr>
<td><code>indent</code></td>
<td><code>int</code></td>
<td>指定缩进级别，以美化输出的 <code>JSON</code> 数据，使其更具可读性，仅当 <code>format_json</code> 为 <code>True</code> 时有效。</td>
<td>4</td>
</tr>
<tr>
<td><code>ensure_ascii</code></td>
<td><code>bool</code></td>
<td>控制是否将非 <code>ASCII</code> 字符转义为 <code>Unicode</code>。设置为 <code>True</code> 时，所有非 <code>ASCII</code> 字符将被转义；<code>False</code> 则保留原始字符，仅当<code>format_json</code>为<code>True</code>时有效。</td>
<td><code>False</code></td>
</tr>
<tr>
<td><code>save_to_img()</code></td>
<td>将结果保存为图像格式的文件</td>
<td><code>save_path</code></td>
<td><code>str</code></td>
<td>保存的文件路径，支持目录或文件路径。</td>
<td>无</td>
</tr>
</table>

<ul>
  <li>调用<code>print()</code> 方法会将结果打印到终端，打印到终端的内容解释如下：
    <ul>
      <li><code>input_path</code>: <code>(str)</code> 待预测图像的输入路径</li>
      <li><code>page_index</code>: <code>(Union[int, None])</code> 如果输入是PDF文件，则表示当前是PDF的第几页，否则为 <code>None</code></li>
      <li><code>model_settings</code>: <code>(Dict[str, bool])</code> 配置产线所需的模型参数
        <ul>
          <li><code>use_doc_preprocessor</code>: <code>(bool)</code> 控制是否启用文档预处理子产线</li>
          <li><code>use_textline_orientation</code>: <code>(bool)</code> 控制是否启用文本行方向分类模块</li>
        </ul>
      </li>
      <li><code>doc_preprocessor_res</code>: <code>(Dict[str, Union[str, Dict[str, bool], int]])</code> 文档预处理子产线的输出结果。仅当<code>use_doc_preprocessor=True</code>时存在
        <ul>
          <li><code>input_path</code>: <code>(Union[str, None])</code> 图像预处理子产线接受的图像路径，当输入为<code>numpy.ndarray</code>时，保存为<code>None</code></li>
          <li><code>model_settings</code>: <code>(Dict)</code> 预处理子产线的模型配置参数
            <ul>
              <li><code>use_doc_orientation_classify</code>: <code>(bool)</code> 控制是否启用文档方向分类</li>
              <li><code>use_doc_unwarping</code>: <code>(bool)</code> 控制是否启用文本图像矫正</li>
            </ul>
          </li>
          <li><code>angle</code>: <code>(int)</code> 文档方向分类的预测结果。启用时取值为[0,1,2,3]，分别对应[0°,90°,180°,270°]；未启用时为-1</li>
        </ul>
      </li>
      <li><code>dt_polys</code>: <code>(List[numpy.ndarray])</code> 文本检测的多边形框列表。每个检测框由4个顶点坐标构成的numpy数组表示，数组shape为(4, 2)，数据类型为int16</li>
      <li><code>dt_scores</code>: <code>(List[float])</code> 文本检测框的置信度列表</li>
      <li><code>text_det_params</code>: <code>(Dict[str, Dict[str, int, float]])</code> 文本检测模块的配置参数
        <ul>
          <li><code>limit_side_len</code>: <code>(int)</code> 图像预处理时的边长限制值</li>
          <li><code>limit_type</code>: <code>(str)</code> 边长限制的处理方式</li>
          <li><code>thresh</code>: <code>(float)</code> 文本像素分类的置信度阈值</li>
          <li><code>box_thresh</code>: <code>(float)</code> 文本检测框的置信度阈值</li>
          <li><code>unclip_ratio</code>: <code>(float)</code> 文本检测框的膨胀系数</li>
          <li><code>text_type</code>: <code>(str)</code> 文本检测的类型，当前固定为"general"</li>
        </ul>
      </li>
      <li><code>textline_orientation_angles</code>: <code>(List[int])</code> 文本行方向分类的预测结果。启用时返回实际角度值（如[0,0,1]），未启用时返回[-1,-1,-1]</li>
      <li><code>text_rec_score_thresh</code>: <code>(float)</code> 文本识别结果的过滤阈值</li>
      <li><code>rec_texts</code>: <code>(List[str])</code> 文本识别结果列表，仅包含置信度超过<code>text_rec_score_thresh</code>的文本</li>
      <li><code>rec_scores</code>: <code>(List[float])</code> 文本识别的置信度列表，已按<code>text_rec_score_thresh</code>过滤</li>
      <li><code>rec_polys</code>: <code>(List[numpy.ndarray])</code> 经过置信度过滤的文本检测框列表，格式同<code>dt_polys</code></li>
      <li><code>rec_boxes</code>: <code>(numpy.ndarray)</code> 检测框的矩形边界框数组，shape为(n, 4)，dtype为int16。每一行表示一个矩形框的[x_min, y_min, x_max, y_max]坐标，其中(x_min, y_min)为左上角坐标，(x_max, y_max)为右下角坐标</li>
    </ul>
  </li>
  <li>调用<code>save_to_json()</code> 方法会将上述内容保存到指定的<code>save_path</code>中，如果指定为目录，则保存的路径为<code>save_path/{your_img_basename}_res.json</code>，如果指定为文件，则直接保存到该文件中。由于json文件不支持保存numpy数组，因此会将其中的<code>numpy.array</code>类型转换为列表形式。</li>
  <li>调用<code>save_to_img()</code> 方法会将可视化结果保存到指定的<code>save_path</code>中，如果指定为目录，则保存的路径为<code>save_path/{your_img_basename}_ocr_res_img.{your_img_extension}</code>，如果指定为文件，则直接保存到该文件中。(产线通常包含较多结果图片，不建议直接指定为具体的文件路径，否则多张图会被覆盖，仅保留最后一张图)</li>
</ul>

<p>此外，也支持通过属性获取带结果的可视化图像和预测结果，具体如下：</p>

<table>
<thead>
<tr>
<th>属性</th>
<th>属性说明</th>
</tr>
</thead>
<tr>
<td rowspan="1"><code>json</code></td>
<td rowspan="1">获取预测的 <code>json</code> 格式的结果</td>
</tr>
<tr>
<td rowspan="2"><code>img</code></td>
<td rowspan="2">获取格式为 <code>dict</code> 的可视化图像</td>
</tr>
</table>

<ul>
  <li><code>json</code> 属性获取的预测结果为dict类型的数据，相关内容与调用 <code>save_to_json()</code> 方法保存的内容一致。</li>
  <li><code>img</code> 属性返回的预测结果是一个dict类型的数据。其中，键分别为 <code>ocr_res_img</code> 和 <code>preprocessed_img</code>，对应的值是两个 <code>Image.Image</code> 对象：一个用于显示 OCR 结果的可视化图像，另一个用于展示图像预处理的可视化图像。如果没有使用图像预处理子模块，则dict中只包含 <code>ocr_res_img</code>。</li>
</ul>

</details>

## 3. 开发集成/部署

如果通用 OCR 产线可以达到您对产线推理速度和精度的要求，您可以直接进行开发集成/部署。

若您需要将通用 OCR 产线直接应用在您的Python项目中，可以参考[2.2 Python脚本方式集成](#22-python脚本方式集成)中的示例代码。

此外，PaddleOCR 也提供了其他两种部署方式，详细说明如下：

🚀 高性能推理：在实际生产环境中，许多应用对部署策略的性能指标（尤其是响应速度）有着较严苛的标准，以确保系统的高效运行与用户体验的流畅性。为此，PaddleOCR 提供高性能推理功能，旨在对模型推理及前后处理进行深度性能优化，实现端到端流程的显著提速，详细的高性能推理流程请参考[高性能推理](../deployment/high_performance_inference.md)。

☁️ 服务化部署：服务化部署是实际生产环境中常见的一种部署形式。通过将推理功能封装为服务，客户端可以通过网络请求来访问这些服务，以获取推理结果。详细的产线服务化部署流程请参考[服务化部署](../deployment/serving.md)。

以下是基础服务化部署的API参考与多语言服务调用示例：

<details><summary>API参考</summary>
<p>对于服务提供的主要操作：</p>
<ul>
<li>HTTP请求方法为POST。</li>
<li>请求体和响应体均为JSON数据（JSON对象）。</li>
<li>当请求处理成功时，响应状态码为<code>200</code>，响应体的属性如下：</li>
</ul>
<table>
<thead>
<tr>
<th>名称</th>
<th>类型</th>
<th>含义</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>logId</code></td>
<td><code>string</code></td>
<td>请求的UUID。</td>
</tr>
<tr>
<td><code>errorCode</code></td>
<td><code>integer</code></td>
<td>错误码。固定为<code>0</code>。</td>
</tr>
<tr>
<td><code>errorMsg</code></td>
<td><code>string</code></td>
<td>错误说明。固定为<code>"Success"</code>。</td>
</tr>
<tr>
<td><code>result</code></td>
<td><code>object</code></td>
<td>操作结果。</td>
</tr>
</tbody>
</table>
<ul>
<li>当请求处理未成功时，响应体的属性如下：</li>
</ul>
<table>
<thead>
<tr>
<th>名称</th>
<th>类型</th>
<th>含义</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>logId</code></td>
<td><code>string</code></td>
<td>请求的UUID。</td>
</tr>
<tr>
<td><code>errorCode</code></td>
<td><code>integer</code></td>
<td>错误码。与响应状态码相同。</td>
</tr>
<tr>
<td><code>errorMsg</code></td>
<td><code>string</code></td>
<td>错误说明。</td>
</tr>
</tbody>
</table>
<p>服务提供的主要操作如下：</p>
<ul>
<li><b><code>infer</code></b></li>
</ul>
<p>获取图像OCR结果。</p>
<p><code>POST /ocr</code></p>
<ul>
<li>请求体的属性如下：</li>
</ul>
<table>
<thead>
<tr>
<th>名称</th>
<th>类型</th>
<th>含义</th>
<th>是否必填</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>file</code></td>
<td><code>string</code></td>
<td>服务器可访问的图像文件或PDF文件的URL，或上述类型文件内容的Base64编码结果。默认对于超过10页的PDF文件，只有前10页的内容会被处理。<br /> 要解除页数限制，请在产线配置文件中添加以下配置：
<pre><code>Serving:
  extra:
    max_num_input_imgs: null
</code></pre>
</td>
<td>是</td>
</tr>
<tr>
<td><code>fileType</code></td>
<td><code>integer</code> | <code>null</code></td>
<td>文件类型。<code>0</code>表示PDF文件，<code>1</code>表示图像文件。若请求体无此属性，则将根据URL推断文件类型。</td>
<td>否</td>
</tr>
<tr>
<td><code>useDocOrientationClassify</code></td>
<td><code>boolean</code> | <code>null</code></td>
<td>请参阅产线对象中 <code>predict</code> 方法的 <code>use_doc_orientation_classify</code> 参数相关说明。</td>
<td>否</td>
</tr>
<tr>
<td><code>useDocUnwarping</code></td>
<td><code>boolean</code> | <code>null</code></td>
<td>请参阅产线对象中 <code>predict</code> 方法的 <code>use_doc_unwarping</code> 参数相关说明。</td>
<td>否</td>
</tr>
<tr>
<tr>
<td><code>useTextlineOrientation</code></td>
<td><code>boolean</code> | <code>null</code></td>
<td>请参阅产线对象中 <code>predict</code> 方法的 <code>use_textline_orientation</code> 参数相关说明。</td>
<td>否</td>
</tr>
<tr>
<td><code>textDetLimitSideLen</code></td>
<td><code>integer</code> | <code>null</code></td>
<td>请参阅产线对象中 <code>predict</code> 方法的 <code>text_det_limit_side_len</code> 参数相关说明。</td>
<td>否</td>
</tr>
<tr>
<td><code>textDetLimitType</code></td>
<td><code>string</code> | <code>null</code></td>
<td>请参阅产线对象中 <code>predict</code> 方法的 <code>text_det_limit_type</code> 参数相关说明。</td>
<td>否</td>
</tr>
<tr>
<td><code>textDetThresh</code></td>
<td><code>number</code> | <code>null</code></td>
<td>请参阅产线对象中 <code>predict</code> 方法的 <code>text_det_thresh</code> 参数相关说明。</td>
<td>否</td>
</tr>
<tr>
<td><code>textDetBoxThresh</code></td>
<td><code>number</code> | <code>null</code></td>
<td>请参阅产线对象中 <code>predict</code> 方法的 <code>text_det_box_thresh</code> 参数相关说明。</td>
<td>否</td>
</tr>
<tr>
<td><code>textDetUnclipRatio</code></td>
<td><code>number</code> | <code>null</code></td>
<td>请参阅产线对象中 <code>predict</code> 方法的 <code>text_det_unclip_ratio</code> 参数相关说明。</td>
<td>否</td>
</tr>
<tr>
<td><code>textRecScoreThresh</code></td>
<td><code>number</code> | <code>null</code></td>
<td>请参阅产线对象中 <code>predict</code> 方法的 <code>text_rec_score_thresh</code> 参数相关说明。</td>
<td>否</td>
</tr>
<tr>
<td><code>visualize</code></td>
<td><code>boolean</code> | <code>null</code></td>
<td>是否返回可视化结果图以及处理过程中的中间图像等。
<ul style="margin: 0 0 0 1em; padding-left: 0em;">
<li>传入 <code>true</code>：返回图像。</li>
<li>传入 <code>false</code>：不返回图像。</li>
<li>若请求体中未提供该参数或传入 <code>null</code>：遵循产线配置文件<code>Serving.visualize</code> 的设置。</li>
</ul>
<br/>例如，在产线配置文件中添加如下字段：<br/>
<pre><code>Serving:
  visualize: False
</code></pre>
将默认不返回图像，通过请求体中的<code>visualize</code>参数可以覆盖默认行为。如果请求体和配置文件中均未设置（或请求体传入<code>null</code>、配置文件中未设置），则默认返回图像。
</td>
<td>否</td>
</tr>
</tbody>
</table>
<ul>
<li>请求处理成功时，响应体的<code>result</code>具有如下属性：</li>
</ul>
<table>
<thead>
<tr>
<th>名称</th>
<th>类型</th>
<th>含义</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>ocrResults</code></td>
<td><code>object</code></td>
<td>OCR结果。数组长度为1（对于图像输入）或实际处理的文档页数（对于PDF输入）。对于PDF输入，数组中的每个元素依次表示PDF文件中实际处理的每一页的结果。</td>
</tr>
<tr>
<td><code>dataInfo</code></td>
<td><code>object</code></td>
<td>输入数据信息。</td>
</tr>
</tbody>
</table>
<p><code>ocrResults</code>中的每个元素为一个<code>object</code>，具有如下属性：</p>
<table>
<thead>
<tr>
<th>名称</th>
<th>类型</th>
<th>含义</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>prunedResult</code></td>
<td><code>object</code></td>
<td>产线对象的 <code>predict</code> 方法生成结果的 JSON 表示中 <code>res</code> 字段的简化版本，其中去除了 <code>input_path</code> 和 <code>page_index</code> 字段。</td>
</tr>
<tr>
<td><code>ocrImage</code></td>
<td><code>string</code> | <code>null</code></td>
<td>OCR结果图，其中标注检测到的文本位置。图像为JPEG格式，使用Base64编码。</td>
</tr>
<tr>
<td><code>docPreprocessingImage</code></td>
<td><code>string</code> | <code>null</code></td>
<td>可视化结果图像。图像为JPEG格式，使用Base64编码。</td>
</tr>
<tr>
<td><code>inputImage</code></td>
<td><code>string</code> | <code>null</code></td>
<td>输入图像。图像为JPEG格式，使用Base64编码。</td>
</tr>
</tbody>
</table>
</details>

<details><summary>多语言调用服务示例</summary>

<details>
<summary>Python</summary>

<pre><code class="language-python">import base64
import requests

API_URL = "http://localhost:8080/ocr"
file_path = "./demo.jpg"

with open(file_path, "rb") as file:
    file_bytes = file.read()
    file_data = base64.b64encode(file_bytes).decode("ascii")

payload = {"file": file_data, "fileType": 1}

response = requests.post(API_URL, json=payload)

assert response.status_code == 200
result = response.json()["result"]
for i, res in enumerate(result["ocrResults"]):
    print(res["prunedResult"])
    ocr_img_path = f"ocr_{i}.jpg"
    with open(ocr_img_path, "wb") as f:
        f.write(base64.b64decode(res["ocrImage"]))
    print(f"Output image saved at {ocr_img_path}")
</code></pre></details>

<details><summary>C++</summary>

<pre><code class="language-cpp">#include &lt;iostream&gt;
#include &lt;fstream&gt;
#include &lt;vector&gt;
#include &lt;string&gt;
#include "cpp-httplib/httplib.h" // https://github.com/Huiyicc/cpp-httplib
#include "nlohmann/json.hpp" // https://github.com/nlohmann/json
#include "base64.hpp" // https://github.com/tobiaslocker/base64

int main() {
    httplib::Client client("localhost", 8080);  
    const std::string filePath = "./demo.jpg"; 

    std::ifstream file(filePath, std::ios::binary | std::ios::ate);
    if (!file) {
        std::cerr << "Error opening file." << std::endl;
        return 1;
    }

    std::streamsize size = file.tellg();
    file.seekg(0, std::ios::beg);
    std::vector<char> buffer(size);

    if (!file.read(buffer.data(), size)) {
        std::cerr << "Error reading file." << std::endl;
        return 1;
    }

    std::string bufferStr(buffer.data(), static_cast<size_t>(size));
    std::string encodedFile = base64::to_base64(bufferStr);


    nlohmann::json jsonObj;
    jsonObj["file"] = encodedFile;
    jsonObj["fileType"] = 1;  

    auto response = client.Post("/ocr", jsonObj.dump(), "application/json");

    if (response && response->status == 200) {
        nlohmann::json jsonResponse = nlohmann::json::parse(response->body);
        auto result = jsonResponse["result"];

        if (!result.is_object() || !result["ocrResults"].is_array()) {
            std::cerr << "Unexpected response structure." << std::endl;
            return 1;
        }

        for (size_t i = 0; i < result["ocrResults"].size(); ++i) {
            auto ocrResult = result["ocrResults"][i];
            std::cout << ocrResult["prunedResult"] << std::endl;

            std::string ocrImgPath = "ocr_" + std::to_string(i) + ".jpg";
            std::string encodedImage = ocrResult["ocrImage"];
            std::string decodedImage = base64::from_base64(encodedImage);

            std::ofstream outputImage(ocrImgPath, std::ios::binary);
            if (outputImage.is_open()) {
                outputImage.write(decodedImage.c_str(), static_cast<std::streamsize>(decodedImage.size()));
                outputImage.close();
                std::cout << "Output image saved at " << ocrImgPath << std::endl;
            } else {
                std::cerr << "Unable to open file for writing: " << ocrImgPath << std::endl;
            }
        }
    } else {
        std::cerr << "Failed to send HTTP request." << std::endl;
        if (response) {
            std::cerr << "HTTP status code: " << response->status << std::endl;
            std::cerr << "Response body: " << response->body << std::endl;
        }
        return 1;
    }

    return 0;
}
</code></pre></details>

<details><summary>Java</summary>

<pre><code class="language-java">import okhttp3.*;
import com.fasterxml.jackson.databind.ObjectMapper;
import com.fasterxml.jackson.databind.JsonNode;
import com.fasterxml.jackson.databind.node.ObjectNode;

import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.util.Base64;

public class Main {
    public static void main(String[] args) throws IOException {
        String API_URL = "http://localhost:8080/ocr"; 
        String imagePath = "./demo.jpg"; 

        File file = new File(imagePath);
        byte[] fileContent = java.nio.file.Files.readAllBytes(file.toPath());
        String base64Image = Base64.getEncoder().encodeToString(fileContent);

        ObjectMapper objectMapper = new ObjectMapper();
        ObjectNode payload = objectMapper.createObjectNode();
        payload.put("file", base64Image); 
        payload.put("fileType", 1); 

        OkHttpClient client = new OkHttpClient();
        MediaType JSON = MediaType.get("application/json; charset=utf-8");
	RequestBody body = RequestBody.create(JSON, payload.toString());

        Request request = new Request.Builder()
                .url(API_URL)
                .post(body)
                .build();

        try (Response response = client.newCall(request).execute()) {
            if (response.isSuccessful()) {
                String responseBody = response.body().string();
                JsonNode root = objectMapper.readTree(responseBody);
                JsonNode result = root.get("result");

                JsonNode ocrResults = result.get("ocrResults");
                for (int i = 0; i < ocrResults.size(); i++) {
                    JsonNode item = ocrResults.get(i);

                    JsonNode prunedResult = item.get("prunedResult");
                    System.out.println("Pruned Result [" + i + "]: " + prunedResult.toString());

                    String ocrImageBase64 = item.get("ocrImage").asText();
                    byte[] ocrImageBytes = Base64.getDecoder().decode(ocrImageBase64);
                    String ocrImgPath = "ocr_result_" + i + ".jpg";
                    try (FileOutputStream fos = new FileOutputStream(ocrImgPath)) {
                        fos.write(ocrImageBytes);
                        System.out.println("Saved OCR image to: " + ocrImgPath);
                    }
                }
            } else {
                System.err.println("Request failed with HTTP code: " + response.code());
            }
        }
    }
}
</code></pre></details>

<details><summary>Go</summary>

<pre><code class="language-go">package main

import (
    "bytes"
    "encoding/base64"
    "encoding/json"
    "fmt"
    "io/ioutil"
    "net/http"
)

func main() {
    API_URL := "http://localhost:8080/ocr"
    filePath := "./demo.jpg"

    fileBytes, err := ioutil.ReadFile(filePath)
    if err != nil {
        fmt.Printf("Error reading file: %v\n", err)
        return
    }
    fileData := base64.StdEncoding.EncodeToString(fileBytes)

    payload := map[string]interface{}{
        "file":     fileData,
        "fileType": 1,
    }
    payloadBytes, err := json.Marshal(payload)
    if err != nil {
        fmt.Printf("Error marshaling payload: %v\n", err)
        return
    }

    client := &http.Client{}
    req, err := http.NewRequest("POST", API_URL, bytes.NewBuffer(payloadBytes))
    if err != nil {
        fmt.Printf("Error creating request: %v\n", err)
        return
    }
    req.Header.Set("Content-Type", "application/json")

    res, err := client.Do(req)
    if err != nil {
        fmt.Printf("Error sending request: %v\n", err)
        return
    }
    defer res.Body.Close()

    if res.StatusCode != http.StatusOK {
        fmt.Printf("Unexpected status code: %d\n", res.StatusCode)
        return
    }

    body, err := ioutil.ReadAll(res.Body)
    if err != nil {
        fmt.Printf("Error reading response body: %v\n", err)
        return
    }

    type OcrResult struct {
        PrunedResult map[string]interface{} `json:"prunedResult"` 
        OcrImage     *string                `json:"ocrImage"`     
    }

    type Response struct {
        Result struct {
            OcrResults []OcrResult `json:"ocrResults"`
            DataInfo   interface{} `json:"dataInfo"` 
        } `json:"result"`
    }

    var respData Response
    if err := json.Unmarshal(body, &respData); err != nil {
        fmt.Printf("Error unmarshaling response: %v\n", err)
        return
    }

    for i, res := range respData.Result.OcrResults {
        
        if res.OcrImage != nil {
            imgBytes, err := base64.StdEncoding.DecodeString(*res.OcrImage)
            if err != nil {
                fmt.Printf("Error decoding image %d: %v\n", i, err)
                continue
            }
            
            filename := fmt.Sprintf("ocr_%d.jpg", i)
            if err := ioutil.WriteFile(filename, imgBytes, 0644); err != nil {
                fmt.Printf("Error saving image %s: %v\n", filename, err)
                continue
            }
            fmt.Printf("Output image saved at %s\n", filename)
        }
    }
}
</code></pre></details>

<details><summary>C#</summary>

<pre><code class="language-csharp">using System;
using System.IO;
using System.Net.Http;
using System.Text;
using System.Threading.Tasks;
using Newtonsoft.Json.Linq;

class Program
{
    static readonly string API_URL = "http://localhost:8080/ocr";
    static readonly string inputFilePath = "./demo.jpg";

    static async Task Main(string[] args)
    {
        var httpClient = new HttpClient();

        byte[] fileBytes = File.ReadAllBytes(inputFilePath);
        string fileData = Convert.ToBase64String(fileBytes);

        var payload = new JObject
        {
            { "file", fileData },
            { "fileType", 1 }
        };
        var content = new StringContent(payload.ToString(), Encoding.UTF8, "application/json");

        HttpResponseMessage response = await httpClient.PostAsync(API_URL, content);
        response.EnsureSuccessStatusCode();

        string responseBody = await response.Content.ReadAsStringAsync();
        JObject jsonResponse = JObject.Parse(responseBody);

        JArray ocrResults = (JArray)jsonResponse["result"]["ocrResults"];
        for (int i = 0; i < ocrResults.Count; i++)
        {
            var res = ocrResults[i];
            Console.WriteLine($"[{i}] prunedResult:\n{res["prunedResult"]}");

            string base64Image = res["ocrImage"]?.ToString();
            if (!string.IsNullOrEmpty(base64Image))
            {
                string outputPath = $"ocr_{i}.jpg";
                byte[] imageBytes = Convert.FromBase64String(base64Image);
                File.WriteAllBytes(outputPath, imageBytes);
                Console.WriteLine($"OCR image saved to {outputPath}");
            }
            else
            {
                Console.WriteLine($"OCR image at index {i} is null.");
            }
        }
    }
}
</code></pre></details>

<details><summary>Node.js</summary>

<pre><code class="language-js">const axios = require('axios');
const fs = require('fs');
const path = require('path');

const API_URL = 'http://localhost:8080/layout-parsing';
const imagePath = './demo.jpg';  
const fileType = 1;             

function encodeImageToBase64(filePath) {
  const bitmap = fs.readFileSync(filePath);
  return Buffer.from(bitmap).toString('base64');
}

const payload = {
  file: encodeImageToBase64(imagePath),
  fileType: fileType
};

axios.post(API_URL, payload)
  .then(response => {
    const results = response.data.result.layoutParsingResults;
    results.forEach((res, index) => {
      console.log(`\n[${index}] prunedResult:`);
      console.log(res.prunedResult);

      const outputImages = res.outputImages;
      if (outputImages) {
        Object.entries(outputImages).forEach(([imgName, base64Img]) => {
          const imgPath = `${imgName}_${index}.jpg`;
          fs.writeFileSync(imgPath, Buffer.from(base64Img, 'base64'));
          console.log(`Output image saved at ${imgPath}`);
        });
      } else {
        console.log(`[${index}] No outputImages.`);
      }
    });
  })
  .catch(error => {
    console.error('Error during API request:', error.message || error);
  });
</code></pre></details>

<details><summary>PHP</summary>

<pre><code class="language-php">&lt;?php

$API_URL = "http://localhost:8080/ocr"; 
$image_path = "./demo.jpg"; 

$image_data = base64_encode(file_get_contents($image_path));
$payload = array(
    "file" => $image_data,
    "fileType" => 1 
);

$ch = curl_init($API_URL);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($payload));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type: application/json'));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
curl_close($ch);

$result = json_decode($response, true)["result"]["ocrResults"];

foreach ($result as $i => $item) {
    echo "[$i] prunedResult:\n";
    print_r($item["prunedResult"]);

    if (!empty($item["ocrImage"])) {
        $output_img_path = "ocr_{$i}.jpg";
        file_put_contents($output_img_path, base64_decode($item["ocrImage"]));
        echo "OCR image saved at $output_img_path\n";
    } else {
        echo "No ocrImage found for item $i\n";
    }
}
?&gt;
</code></pre></details>
</details>

## 4. 二次开发
如果 通用OCR 产线提供的默认模型权重在您的场景中，精度或速度不满意，您可以尝试利用<b>您自己拥有的特定领域或应用场景的数据</b>对现有模型进行进一步的<b>微调</b>，以提升 通用OCR 产线的在您的场景中的识别效果。

### 4.1 模型微调
通用 OCR 产线包含若干模块，模型产线的效果如果不及预期，可能来自于其中任何一个模块。您可以对识别效果差的图片进行分析，进而确定是哪个模块存在问题，并参考以下表格中对应的微调教程链接进行模型微调。

<table>
<thead>
<tr>
<th>情形</th>
<th>微调模块</th>
<th>微调参考链接</th>
</tr>
</thead>
<tbody>
<tr>
<td>整图旋转矫正不准</td>
<td>文档图像方向分类模块</td>
<td><a href="https://paddlepaddle.github.io/PaddleX/latest/module_usage/tutorials/ocr_modules/doc_img_orientation_classification.html#_5">链接</a></td>
</tr>
<tr>
<td>图像扭曲矫正不准</td>
<td>文本图像矫正模块</td>
<td>暂不支持微调</td>
</tr>
<tr>
<td>文本行旋转矫正不准</td>
<td>文本行方向分类模块</td>
<td><a href="https://paddlepaddle.github.io/PaddleX/latest/module_usage/tutorials/ocr_modules/textline_orientation_classification.html#_5">链接</a></td>
</tr>
<tr>
<td>文本漏检</td>
<td>文本检测模块</td>
<td><a href="https://paddlepaddle.github.io/PaddleOCR/main/version3.x/module_usage/text_detection.html#_5">链接</a></td>
</tr>
<tr>
<td>文本内容不准</td>
<td>文本识别模块</td>
<td><a href="https://paddlepaddle.github.io/PaddleOCR/main/version3.x/module_usage/text_recognition.html#_5">链接</a></td>
</tr>
</tbody>
</table>

### 4.2 模型应用

当您使用私有数据集完成微调训练后，可获得本地模型权重文件，然后可以通过参数指定本地模型保存路径的方式，或者通过自定义产线配置文件的方式，使用微调后的模型权重。

#### 4.2.1 通过参数指定本地模型路径

在初始化产线对象时，通过参数指定本地模型路径。以文本检测模型微调后的权重的使用方法为例，示例如下：

命令行方式:

```bash
# 通过 --text_detection_model_dir 指定本地模型路径
paddleocr ocr -i ./general_ocr_002.png --text_detection_model_dir your_det_model_path

# 默认使用 PP-OCRv5_server_det 模型作为默认文本检测模型，如果微调的不是该模型，通过 --text_detection_model_name 修改模型名称
paddleocr ocr -i ./general_ocr_002.png --text_detection_model_name PP-OCRv5_mobile_det --text_detection_model_dir your_v5_mobile_det_model_path
```

脚本方式：

```python

from paddleocr import PaddleOCR

# 通过 text_detection_model_dir 指定本地模型路径
pipeline = PaddleOCR(text_detection_model_dir="./your_det_model_path")

# 默认使用 PP-OCRv5_server_det 模型作为默认文本检测模型，如果微调的不是该模型，通过 text_detection_model_name 修改模型名称
# pipeline = PaddleOCR(text_detection_model_name="PP-OCRv5_mobile_det", text_detection_model_dir="./your_v5_mobile_det_model_path")

```


#### 4.2.2 通过配置文件指定本地模型路径


1.获取产线配置文件

可调用 PaddleOCR 中 通用 OCR 产线对象的 `export_paddlex_config_to_yaml` 方法，将当前产线配置导出为 YAML 文件：

```Python
from paddleocr import PaddleOCR

pipeline = PaddleOCR()
pipeline.export_paddlex_config_to_yaml("PaddleOCR.yaml")
```

2.修改配置文件

在得到默认的产线配置文件后，将微调后模型权重的本地路径替换至产线配置文件中的对应位置即可。例如

```yaml
......
SubModules:
  TextDetection:
    box_thresh: 0.6
    limit_side_len: 64
    limit_type: min
    max_side_limit: 4000
    model_dir: null # 替换为微调后的文本测模型权重路径
    model_name: PP-OCRv5_server_det # 如果微调的模型名称与默认模型名称不同，请一并修改此处
    module_name: text_detection
    thresh: 0.3
    unclip_ratio: 1.5
  TextLineOrientation:
    batch_size: 6
    model_dir: null  # 替换为微调后的文本行方向分类模型权重路径
    model_name: PP-LCNet_x1_0_textline_ori # 如果微调的模型名称与默认模型名称不同，请一并修改此处
    module_name: textline_orientation
  TextRecognition:
    batch_size: 6
    model_dir: null # 替换为微调后的文本识模型权重路径
    model_name: PP-OCRv5_server_rec # 如果微调的模型名称与默认模型名称不同，请一并修改此处
    module_name: text_recognition
    score_thresh: 0.0
......
```

在产线配置文件中，不仅包含 PaddleOCR CLI 和 Python API 支持的参数，还可进行更多高级配置，具体信息可在 [PaddleX模型产线使用概览](https://paddlepaddle.github.io/PaddleX/3.0/pipeline_usage/pipeline_develop_guide.html) 中找到对应的产线使用教程，参考其中的详细说明，根据需求调整各项配置。

3.在 CLI 中加载产线配置文件

在修改完成配置文件后，通过命令行的 `--paddlex_config` 参数指定修改后的产线配置文件的路径，PaddleOCR 会读取其中的内容作为产线配置。示例如下：

```bash
paddleocr ocr --paddlex_config PaddleOCR.yaml ...
```

4.在 Python API 中加载产线配置文件

初始化产线对象时，可通过 `paddlex_config` 参数传入 PaddleX 产线配置文件路径或配置dict，PaddleOCR 会读取其中的内容作为产线配置。示例如下：

```python
from paddleocr import PaddleOCR

pipeline = PaddleOCR(paddlex_config="PaddleOCR.yaml")
```

## 5. 附录

<details><summary><b>Supported Languages</b></summary>

<table border="1" cellspacing="0" cellpadding="4">
  <thead>
    <tr>
      <th><code>lang</code></th>
      <th>Language Name</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><code>abq</code></td><td>Abaza</td></tr>
    <tr><td><code>af</code></td><td>Afrikaans</td></tr>
    <tr><td><code>ang</code></td><td>Old English</td></tr>
    <tr><td><code>ar</code></td><td>Arabic</td></tr>
    <tr><td><code>ava</code></td><td>Avaric</td></tr>
    <tr><td><code>az</code></td><td>Azerbaijani</td></tr>
    <tr><td><code>be</code></td><td>Belarusian</td></tr>
    <tr><td><code>bg</code></td><td>Bulgarian</td></tr>
    <tr><td><code>bgc</code></td><td>Haryanvi</td></tr>
    <tr><td><code>bh</code></td><td>Bihari</td></tr>
    <tr><td><code>bho</code></td><td>Bhojpuri</td></tr>
    <tr><td><code>bs</code></td><td>Bosnian</td></tr>
    <tr><td><code>ch</code></td><td>Chinese (Simplified)</td></tr>
    <tr><td><code>che</code></td><td>Chechen</td></tr>
    <tr><td><code>chinese_cht</code></td><td>Chinese (Traditional)</td></tr>
    <tr><td><code>cs</code></td><td>Czech</td></tr>
    <tr><td><code>cy</code></td><td>Welsh</td></tr>
    <tr><td><code>da</code></td><td>Danish</td></tr>
    <tr><td><code>dar</code></td><td>Dargwa</td></tr>
    <tr><td><code>de</code> or <code>german</code></td><td>German</td></tr>
    <tr><td><code>en</code></td><td>English</td></tr>
    <tr><td><code>es</code></td><td>Spanish</td></tr>
    <tr><td><code>et</code></td><td>Estonian</td></tr>
    <tr><td><code>fa</code></td><td>Persian</td></tr>
    <tr><td><code>fr</code> or <code>french</code></td><td>French</td></tr>
    <tr><td><code>ga</code></td><td>Irish</td></tr>
    <tr><td><code>gom</code></td><td>Konkani</td></tr>
    <tr><td><code>hi</code></td><td>Hindi</td></tr>
    <tr><td><code>hr</code></td><td>Croatian</td></tr>
    <tr><td><code>hu</code></td><td>Hungarian</td></tr>
    <tr><td><code>id</code></td><td>Indonesian</td></tr>
    <tr><td><code>inh</code></td><td>Ingush</td></tr>
    <tr><td><code>is</code></td><td>Icelandic</td></tr>
    <tr><td><code>it</code></td><td>Italian</td></tr>
    <tr><td><code>japan</code></td><td>Japanese</td></tr>
    <tr><td><code>ka</code></td><td>Georgian</td></tr>
    <tr><td><code>kbd</code></td><td>Kabardian</td></tr>
    <tr><td><code>korean</code></td><td>Korean</td></tr>
    <tr><td><code>ku</code></td><td>Kurdish</td></tr>
    <tr><td><code>la</code></td><td>Latin</td></tr>
    <tr><td><code>lbe</code></td><td>Lak</td></tr>
    <tr><td><code>lez</code></td><td>Lezghian</td></tr>
    <tr><td><code>lt</code></td><td>Lithuanian</td></tr>
    <tr><td><code>lv</code></td><td>Latvian</td></tr>
    <tr><td><code>mah</code></td><td>Magahi</td></tr>
    <tr><td><code>mai</code></td><td>Maithili</td></tr>
    <tr><td><code>mi</code></td><td>Maori</td></tr>
    <tr><td><code>mn</code></td><td>Mongolian</td></tr>
    <tr><td><code>mr</code></td><td>Marathi</td></tr>
    <tr><td><code>ms</code></td><td>Malay</td></tr>
    <tr><td><code>mt</code></td><td>Maltese</td></tr>
    <tr><td><code>ne</code></td><td>Nepali</td></tr>
    <tr><td><code>new</code></td><td>Newari</td></tr>
    <tr><td><code>nl</code></td><td>Dutch</td></tr>
    <tr><td><code>no</code></td><td>Norwegian</td></tr>
    <tr><td><code>oc</code></td><td>Occitan</td></tr>
    <tr><td><code>pi</code></td><td>Pali</td></tr>
    <tr><td><code>pl</code></td><td>Polish</td></tr>
    <tr><td><code>pt</code></td><td>Portuguese</td></tr>
    <tr><td><code>ro</code></td><td>Romanian</td></tr>
    <tr><td><code>rs_cyrillic</code></td><td>Serbian (Cyrillic)</td></tr>
    <tr><td><code>rs_latin</code></td><td>Serbian (Latin)</td></tr>
    <tr><td><code>ru</code></td><td>Russian</td></tr>
    <tr><td><code>sa</code></td><td>Sanskrit</td></tr>
    <tr><td><code>sck</code></td><td>Sadri</td></tr>
    <tr><td><code>sk</code></td><td>Slovak</td></tr>
    <tr><td><code>sl</code></td><td>Slovenian</td></tr>
    <tr><td><code>sq</code></td><td>Albanian</td></tr>
    <tr><td><code>sv</code></td><td>Swedish</td></tr>
    <tr><td><code>sw</code></td><td>Swahili</td></tr>
    <tr><td><code>tab</code></td><td>Tabassaran</td></tr>
    <tr><td><code>ta</code></td><td>Tamil</td></tr>
    <tr><td><code>te</code></td><td>Telugu</td></tr>
    <tr><td><code>tl</code></td><td>Tagalog</td></tr>
    <tr><td><code>tr</code></td><td>Turkish</td></tr>
    <tr><td><code>ug</code></td><td>Uyghur</td></tr>
    <tr><td><code>uk</code></td><td>Ukrainian</td></tr>
    <tr><td><code>ur</code></td><td>Urdu</td></tr>
    <tr><td><code>uz</code></td><td>Uzbek</td></tr>
    <tr><td><code>vi</code></td><td>Vietnamese</td></tr>
  </tbody>
</table>

</details>

<details><summary><b>Correspondence Between OCR Model Versions and Supported Languages</b></summary>

<table border="1" cellspacing="0" cellpadding="4">
  <thead>
    <tr>
      <th><code>ocr_version</code></th>
      <th>Supported <code>lang</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>PP-OCRv5</code></td>
      <td><code>ch</code>, <code>en</code>, <code>fr</code>, <code>de</code>, <code>japan</code>, <code>korean</code>, <code>chinese_cht</code>, <code>af</code>, <code>it</code>, <code>es</code>, <code>bs</code>, <code>pt</code>, <code>cs</code>, <code>cy</code>, <code>da</code>, <code>et</code>, <code>ga</code>, <code>hr</code>, <code>hu</code>, <code>rslatin</code>, <code>id</code>, <code>oc</code>, <code>is</code>, <code>lt</code>, <code>mi</code>, <code>ms</code>, <code>nl</code>, <code>no</code>, <code>pl</code>, <code>sk</code>, <code>sl</code>, <code>sq</code>, <code>sv</code>, <code>sw</code>, <code>tl</code>, <code>tr</code>, <code>uz</code>, <code>la</code>, <code>ru</code>, <code>be</code>, <code>uk</code></td>
    </tr>
    <tr>
      <td><code>PP-OCRv4</code></td>
      <td><code>ch</code>, <code>en</code></td>
    </tr>
    <tr>
      <td><code>PP-OCRv3</code></td>
      <td>
        <code>abq</code>, <code>af</code>, <code>ady</code>, <code>ang</code>, <code>ar</code>, <code>ava</code>, <code>az</code>, <code>be</code>,
        <code>bg</code>, <code>bgc</code>, <code>bh</code>, <code>bho</code>, <code>bs</code>, <code>ch</code>, <code>che</code>,
        <code>chinese_cht</code>, <code>cs</code>, <code>cy</code>, <code>da</code>, <code>dar</code>, <code>de</code>, <code>german</code>,
        <code>en</code>, <code>es</code>, <code>et</code>, <code>fa</code>, <code>fr</code>, <code>french</code>, <code>ga</code>, <code>gom</code>,
        <code>hi</code>, <code>hr</code>, <code>hu</code>, <code>id</code>, <code>inh</code>, <code>is</code>, <code>it</code>, <code>japan</code>,
        <code>ka</code>, <code>kbd</code>, <code>korean</code>, <code>ku</code>, <code>la</code>, <code>lbe</code>, <code>lez</code>, <code>lt</code>,
        <code>lv</code>, <code>mah</code>, <code>mai</code>, <code>mi</code>, <code>mn</code>, <code>mr</code>, <code>ms</code>, <code>mt</code>,
        <code>ne</code>, <code>new</code>, <code>nl</code>, <code>no</code>, <code>oc</code>, <code>pi</code>, <code>pl</code>, <code>pt</code>,
        <code>ro</code>, <code>rs_cyrillic</code>, <code>rs_latin</code>, <code>ru</code>, <code>sa</code>, <code>sck</code>, <code>sk</code>,
        <code>sl</code>, <code>sq</code>, <code>sv</code>, <code>sw</code>, <code>ta</code>, <code>tab</code>, <code>te</code>, <code>tl</code>,
        <code>tr</code>, <code>ug</code>, <code>uk</code>, <code>ur</code>, <code>uz</code>, <code>vi</code>
      </td>
    </tr>
  </tbody>
</table>

</details>
