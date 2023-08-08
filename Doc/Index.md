# Stable Diffusion 文字酷炫新玩法，艺术，光影字体生成教程

## 项目目录

1. [<font color="DarkTurquoise">前期准备</font>](#ready_start)
	1. [<font color="DeepSkyBlue">文字底图</font>](#ready_font)
	2. [<font color="DeepSkyBlue">大模型</font>]()
	3. [<font color="DeepSkyBlue">控制模型</font>]()
2. [<font color="DarkTurquoise">控制描述</font>]()
	1. [<font color="DeepSkyBlue">简明步骤</font>]()
    2. [<font color="DeepSkyBlue">控制逻辑</font>]()
3. [<font color="DarkTurquoise">艺术文字</font>]()
    1. [<font color="DeepSkyBlue">面包</font>]()
    2. [<font color="DeepSkyBlue">奶油</font>]()
    3. [<font color="DeepSkyBlue">蛋糕</font>]()
    4. [<font color="DeepSkyBlue">雨水</font>]()
4. [<font color="DarkTurquoise">嵌入文字</font>]()
    1. [<font color="DeepSkyBlue">春天</font>]()
5. [<font color="DarkTurquoise">光影文字</font>]()
    1. [<font color="DeepSkyBlue">数字/字符</font>]()
    2. [<font color="DeepSkyBlue">牛逼/晚安</font>]()
    3. [<font color="DeepSkyBlue">大本营</font>]()
6. [<font color="DarkTurquoise">扩展内容</font>]()
    1. [<font color="DeepSkyBlue">符号/建筑设计</font>]()
    2. [<font color="DeepSkyBlue">产品设计</font>]()
    3. [<font color="DeepSkyBlue">图生图: 图片+文字融合</font>]()
7. [<font color="DarkTurquoise">实现</font>]()
8. [<font color="DarkTurquoise">FAQ问题</font>]()
    1. [<font color="DeepSkyBlue">文字过于明显</font>]()
    2. [<font color="DeepSkyBlue">字体不好看</font>]()
    3. [<font color="DeepSkyBlue">看不到文字</font>]()
    4. [<font color="DeepSkyBlue">文字挤到一起</font>]()
    5. [<font color="DeepSkyBlue">光影文字不美观</font>]()
    6. [<font color="DeepSkyBlue">提示词怎么写</font>]()
9. [<font color="DarkTurquoise">相关链接</font>](#about_links)
10. [<font color="DarkTurquoise">参考</font>]()

![效果展示图片](files/output.png)

## <span id="ready_start">1. 前期准备</span>


#### <span id="ready_font">1.1 文字底图</span>

工具推荐 美图秀秀 或者 Photoshop

1. 创建 **<font color="DeepSkyBlue">"白底黑字的文字图，根据情况使用invert进行反色处理."</font>**
2. 分辨率设置建议 512*768 (同生成图比例一致)
3. 保存为PNG文件

#### <span id="ready_model">1.2 大模型</span>

真实系大模型即可，没有特别需求。

推荐 revAnimated, deliberate, majicmixRealistic

不同大模型生成效果有差别，建议 **<font color="DeepSkyBlue">控制变量</font>** 后多对比测试。
![大模型展示图片](files/modal01.png)
![大模型展示图片](files/modal02.png)

### <span id="about_links">相关链接</span>

[<font color="DeepSkyBlue">2023 年人工智能 AIGC 学习手册</font>](https://ks48jupoux.feishu.cn/docx/J85pdGX5josTuwx5AVxc6LHJnVc)  
