# Changelogs

### 2022-09-24
[v1.3.12](https://github.com/dmMaze/BallonsTranslator/releases/tag/v1.3.12)发布

1. 支持全局(Ctrl+G)/当前页(Ctrl+F)查找替换
2. 原来的文本编辑器局部撤销重做并入全局文本编辑撤销重做栈, 画板撤销重做现在和文本编辑分离
3. Word文档导入导出bug修复
4. 基于https://github.com/zhiyiYo/PyQt-Frameless-Window重写无边框窗口

### 2022-09-13
[v1.3.8](https://github.com/dmMaze/BallonsTranslator/releases/tag/v1.3.8)发布

1. 画笔工具修复及优化
2. 修正界面缩放
3. 支持添加自定义字体样式预设, 支持调整文字透明度和阴影, 详见https://github.com/dmMaze/BallonsTranslator/pull/38
4. 支持导入导出word文档, 支持打开*.json项目文件, 详见https://github.com/dmMaze/BallonsTranslator/pull/40

### 2022-08-31
[v1.3.4](https://github.com/dmMaze/BallonsTranslator/releases/tag/v1.3.4)发布

1. 添加离线日译英模型Sugoi Translator(仅日译英, 作者[mingshiba](https://www.patreon.com/mingshiba), 已获得集成授权), 感谢[@Snowad14](https://github.com/Snowad14)提供CT2转换模型
2. 来自[bropines](https://github.com/bropines)的俄语本地化支持
3. 文本编辑支持字距调节
4. 调整竖排符号及半角字符位置规则, 详见https://github.com/dmMaze/BallonsTranslator/pull/30

### 2022-08-17
[v1.3.0](https://github.com/dmMaze/BallonsTranslator/releases/tag/v1.3.0)发布

1. 修复DeepL翻译器的bug, 感谢[@Snowad14](https://github.com/Snowad14)
2. 修复部分字体偏小+轮廓导致看不清的问题
3. 支持**全局字体格式**(一键机翻字体格式): 在控制面板->嵌字菜单里将相应项从"由程序决定"改为"使用全局设置"后启用. 注意全局设置就是未编辑任何文本块时右侧字体格式面板的那些设置.  
4. 添加**新的修复模型**: lama-mpe (默认启用)
5. 文本块支持多选和**批量调整格式** (ctrl+鼠标左键或者按下右键拉框框选)
6. 支持日译英, 英译中的**自动排版**, 基于提取出的背景气泡, 目标语言为中文时会自动断句(基于pkuseg). 勾选设置面板->常规->嵌字->自动排版后将对一键机翻生效(默认启用). 

<img src="doc/src/multisel_autolayout.gif" div align=center>
<p align=center>
批量格式调整, 英译中自动断句分行
</p>

### 2022-05-19
[v1.2.0](https://github.com/dmMaze/BallonsTranslator/releases/tag/v1.2.0)发布

1. 支持DeepL翻译器, 感谢[@Snowad14](https://github.com/Snowad14)
2. 增加来自manga-image-translator的新OCR模型, 支持韩语识别
3. 修bug


### 2022-04-17
[v1.1.0](https://github.com/dmMaze/BallonsTranslator/releases/tag/v1.1.0)发布

1. 用qthread存编辑图片, 避免翻页卡顿
2. 图像修复策略优化: 
   - 修复算法和**CPU模式**下的修复模型输入由整张图片改为文本块
   - 可选由程序自动评估当前块是否有必要调用开销大的修复方法, 在设置-图像修复启用/禁用, 启用后纯色背景对话泡将会由计算出的背景色直接填充  
  
    优化后图像修复阶段速度提升至原来的2x-5x不等

3. 添加矩形工具
4. 更多快捷键
5. 修bug

### 2022-04-09
v1.0.0发布