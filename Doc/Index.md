# Stable Diffusion 文字酷炫新玩法，艺术，光影字体生成教程

## 项目目录

1. [<font color="LightSlateGray">前期准备</font>](#ready_start)
	1. [<font color="DodgerBlue">文字底图</font>](#ready_font)
	2. [<font color="DodgerBlue">大模型</font>](#ready_large_model)
	3. [<font color="DodgerBlue">控制模型</font>](#ready_model)
2. [<font color="LightSlateGray">控制综述</font>](#admin_desc)
	1. [<font color="DodgerBlue">简明步骤</font>](#admin_step)
    2. [<font color="DodgerBlue">控制逻辑</font>](#admin_logic)
3. [<font color="LightSlateGray">艺术文字</font>](#art_word)
    1. [<font color="DodgerBlue">面包</font>](#word_bread)
    2. [<font color="DodgerBlue">奶油</font>](#word_cream)
    3. [<font color="DodgerBlue">蛋糕</font>](#word_cake)
    4. [<font color="DodgerBlue">雨水</font>](#word_rain)
4. [<font color="LightSlateGray">嵌入文字</font>]()
    1. [<font color="DodgerBlue">春天</font>]()
5. [<font color="LightSlateGray">光影文字</font>]()
    1. [<font color="DodgerBlue">数字/字符</font>]()
    2. [<font color="DodgerBlue">牛逼/晚安</font>]()
    3. [<font color="DodgerBlue">大本营</font>]()
6. [<font color="LightSlateGray">扩展内容</font>]()
    1. [<font color="DodgerBlue">符号/建筑设计</font>]()
    2. [<font color="DodgerBlue">产品设计</font>]()
    3. [<font color="DodgerBlue">图生图: 图片+文字融合</font>]()
7. [<font color="LightSlateGray">实现</font>]()
8. [<font color="LightSlateGray">FAQ问题</font>]()
    1. [<font color="DodgerBlue">文字过于明显</font>]()
    2. [<font color="DodgerBlue">字体不好看</font>]()
    3. [<font color="DodgerBlue">看不到文字</font>]()
    4. [<font color="DodgerBlue">文字挤到一起</font>]()
    5. [<font color="DodgerBlue">光影文字不美观</font>]()
    6. [<font color="DodgerBlue">提示词怎么写</font>]()
9. [<font color="LightSlateGray">相关链接</font>](#about_links)
10. [<font color="LightSlateGray">参考</font>]()

![效果展示图片](files/output.png)

### <span id="ready_start">1. 前期准备</span>

#### <span id="ready_font">1.1 文字底图</span>

工具推荐 美图秀秀 或者 Photoshop

1. 创建 **<font color="DodgerBlue">"白底黑字的文字图，根据情况使用invert进行反色处理."</font>**
2. 分辨率设置建议 512*768 (同生成图比例一致)
3. 保存为PNG文件

#### <span id="ready_large_model">1.2 大模型</span>

真实系大模型即可，没有特别需求。

推荐 revAnimated, deliberate, majicmixRealistic

不同大模型生成效果有差别，建议 **<font color="DodgerBlue">控制变量</font>** 后多对比测试。
![大模型展示图片](files/modal01.png)
![大模型展示图片](files/modal02.png)

#### <span id="ready_model">1.4 控制模型</span>

本文中用到第三方控制模型需要手动下载

##### Brightness 亮度控制

[<font color="DodgerBlue">下载地址</font>](https://huggingface.co/ViscoseBean/control_v1p_sd15_brightness/tree/main)
 
##### Controlnet QR Code Monster v1 For SD-1.5 

[<font color="DodgerBlue">下载地址</font>](https://huggingface.co/monster-labs/control_v1p_sd15_qrcode_monster)

### <span id="admin_desc">2. 控制综述</span>

#### <span id="admin_step">2.1 简明步骤</span>

1. 安装 Stable Diffusion 和 ControlNet。
2. 在Stable Diffusion 中进行文生图+ControlNet 或者 图生图+ControlNet，图生图更简单。
3. 重点调整控制权重和控制起始时机。

#### <span id="admin_logic">2.2 控制逻辑</span>

<font color="red">所有模型和参数仅供参考，可以继续优化！</font>

本文主要介绍基本实现方法，想更加美观建议在<font color="red">控制变量</font>的同时微调参数和提示词。

1. 推荐预处理器： invert (白底黑线反色）+ Depth/Tile/Canny/Lineart/Softedge/Scribble的搭配。
2. <font color="SeaGreen">想文字更显眼就加大控制权重。</font>
3. <font color="SeaGreen">想画面更美丽就减小控制权重。</font>
4. 引导介入时机越早，对画面破坏程度越高，画面越不美观。
5. 引导结束时机越大，留给模型融合图片的时间就越少，文字融合度效果变差。
6. 白底反色预处理器可以最大程度保留字体，其他预处理器会给画面增加更多元素，导致文字不容易识别。
7. 字体粗细不同会影响预览图和最终结果，为了字体更明显建议粗体字。
8. 场景上融合的字体可以大一些，人物上融合的字体建议小一些，光线打到人物脸上不美观，可以调整底图文字位置。

### <span id="art_word">3. 艺术文字</span>

#### <span id="word_bread">3.1 面包</span>

效果A | 效果B
:---: | :---:
![效果展示图片](files/plugins01.png) | ![效果展示图片](files/plugins02.png)

描述 | 案例
:---: | :---
正向提示词 | bread lay on wood kitchen table
备选提示词 | bread,Air pockets in the dough,Realistic texture,Golden brown crust,soft and fluffy
反向提示词 | human,person,girl,boy,(worst quality:2), (low quality:2), (normal quality:2), lowres, monochrome, grayscale, watermark

**注意：如果觉得背景复杂影响构图，加入simple background 或者 white background 之类提示词即可。**

![效果展示图片](files/plugins03.png)

步数和采样方法仅供参考，可以更换。

![效果展示图片](files/plugins04.png)

使用Depth模型，反色和midas处理底图，实现不一样效果。

效果A | 效果B


更多参数与效果图参考下面图表：

ID | 大模型 | 预处理器 | 控制模型 | <div style="width:400px">原图</div> | <div style="width:400px">预处理</div>-预览图 | <div style="width:400px">生成图1</div> | <div style="width:400px">生成图2</div> | <div style="width:400px">生成图3</div> | <div style="width:400px">生成图4</div> 
:---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: 
1 | deliberate_v2 | invert (白底黑线反色其他默认) | depth 默认配置 | ![效果展示图片](files/bread01.png) | ![效果展示图片](files/bread02.png)bread lay on wood kitchen table | ![效果展示图片](files/bread3.png)bread lay on wood kitchen table | ![效果展示图片](files/bread04.png)bread lay on wood kitchen table | ![效果展示图片](files/bread05.png)bread lay on wood kitchen table | ![效果展示图片](files/bread06.png)bread lay on wood kitchen table
2 | deliberate_v2 | depth_midas 其他默认 | depth 默认配置 | ![效果展示图片](files/bread11.png) | ![效果展示图片](files/bread12.png)bread lay on wood kitchen table | ![效果展示图片](files/bread13.png)bread lay on wood kitchen table | ![效果展示图片](files/bread14.png)bread lay on wood kitchen table | ![效果展示图片](files/bread15.png)bread lay on wood kitchen table | ![效果展示图片](files/bread16.png)bread lay on wood kitchen table
3 | revAnimated_v122 | depth_midas 其他默认 | depth 默认配置 | ![效果展示图片](files/bread21.png) | ![效果展示图片](files/bread22.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread23.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread24.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread25.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread26.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread
4 | deliberate_v2 | Canny 其他默认 | Canny 默认配置 | ![效果展示图片](files/bread31.png) | ![效果展示图片](files/bread32.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread33.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread34.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread35.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread36.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread
5 | deliberate_v2 | Canny invert 白底黑线反色其他默认 | Canny 默认配置 | ![效果展示图片](files/bread41.png) | ![效果展示图片](files/bread42.png) bread lay on wood kitchen table | ![效果展示图片](files/bread43.png) bread lay on wood kitchen table | ![效果展示图片](files/bread44.png) bread lay on wood kitchen table | ![效果展示图片](files/bread45.png) bread lay on wood kitchen table | ![效果展示图片](files/bread46.png) bread lay on wood kitchen table
6 | deliberate_v2 | lineart standard (标准线稿提取-白底黑线反色) | Lineart 默认配置 | ![效果展示图片](files/bread51.png) | ![效果展示图片](files/bread52.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread53.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread54.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread55.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread | ![效果展示图片](files/bread56.png) (Best quality,masterpiece,ultra high res,raw photo,official art), bread
7 | deliberate_v2 | lineart (白底黑线反色) | Lineart 默认配置 | ![效果展示图片](files/bread61.png) | ![效果展示图片](files/bread62.png) bread lay on wood kitchen table | ![效果展示图片](files/bread63.png) bread lay on wood kitchen table | ![效果展示图片](files/bread64.png) bread lay on wood kitchen table | ![效果展示图片](files/bread65.png) bread lay on wood kitchen table | ![效果展示图片](files/bread66.png) bread lay on wood kitchen table
8 | deliberate_v2 | lineart (白底黑线反色) | Lineart 默认配置 | ![效果展示图片](files/bread71.png) | ![效果展示图片](files/bread72.png) make it bread | ![效果展示图片](files/bread73.png) make it bread | ![效果展示图片](files/bread74.png) make it bread | ![效果展示图片](files/bread75.png) make it bread | ![效果展示图片](files/bread76.png) make it bread
9 | deliberate_v2 | None | IP2P 引导终止时机0.8 + Canny 权重0.5 介入0.3 终止0.8| ![效果展示图片](files/bread81.png) | ![效果展示图片](files/bread82.png) make it bread | ![效果展示图片](files/bread83.png) make it bread | ![效果展示图片](files/bread84.png) make it bread | ![效果展示图片](files/bread85.png) make it bread | ![效果展示图片](files/bread86.png) make it bread

#### <span id="word_cream">3.2 面包</span>

效果A | 效果B
:---: | :---:
![效果展示图片](files/modal03.png) | ![效果展示图片](files/modal04.png)


### <span id="about_links">相关链接</span>

[<font color="DodgerBlue">2023 年人工智能 AIGC 学习手册</font>](https://ks48jupoux.feishu.cn/docx/J85pdGX5josTuwx5AVxc6LHJnVc)  
