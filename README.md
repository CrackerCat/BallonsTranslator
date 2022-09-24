# BallonTranslator
简体中文 | [English](README_EN.md) | [Русский](README_RU.md) | [日本語](README_JA.md)

深度学习辅助漫画翻译工具, 支持一键机翻和简单的图像/文本编辑  

<img src="doc/src/ui0.jpg" div align=center>

<p align=center>
界面预览
</p>

# Features
* 一键机翻  
  - 译文回填参考对原文排版的估计, 包括颜色, 轮廓, 角度, 朝向, 对齐方式等
  - 最后效果取决于文本检测, 识别, 抹字, 机翻四个模块的整体表现  
  - 支持日漫和美漫
  - 英译中, 日译英排版已优化, 文本布局以提取到的背景泡为参考, 中文基于pkuseg进行断句, 日译中竖排待改善
  
* 图像编辑  
  支持掩膜编辑和修复画笔
  
* 文本编辑  
  支持富文本编辑和一些基础排版格式调整


# 使用说明

### 发布版

Windows用户可从[腾讯云](https://share.weiyun.com/xoRhz9i4) 或 [Google Drive](https://drive.google.com/drive/folders/1uElIYRLNakJj-YS0Kd3r3HE-wzeEvrWd?usp=sharing)下载发布包Ballonstranslator-x.x.x-core.7z, 如果分享文件夹内存在更高版本的Ballonstranslator-x.x.x-patch.7z, 下载patch并覆盖core即可.  

### 运行源码

```bash
# 确保python<=3.9
$ python --version

# 克隆仓库
$ git clone https://github.com/dmMaze/BallonsTranslator.git ; cd BallonsTranslator

# 安装依赖, macOS安装requirements_macOS.txt
$ pip install -r requirements.txt
```

如果有N卡可以安装torch-cuda启用GPU加速: 

```bash
pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu116
```

从 https://drive.google.com/drive/folders/1uElIYRLNakJj-YS0Kd3r3HE-wzeEvrWd?usp=sharing 下载**data**文件夹并移动到 ```BallonsTranslator/ballontranslator```目录, 最后运行
```bash
python ballontranslator
```

如果要使用Sugoi翻译器(仅英译日), 下载[离线模型](https://drive.google.com/drive/folders/1KnDlfUM9zbnYFTo6iCbnBaBKabXfnVJm), 将 "sugoi_translator" 移入BallonsTranslator/ballontranslator/data/models.  

## 一键翻译
**建议在命令行终端下运行程序**, 首次运行请先配置好源语言/目标语言, 打开一个带图片的文件夹, 点击Run等待翻译完成  
<img src="doc/src/run.gif">  

一键机翻嵌字格式如大小、颜色等默认是由程序决定的, 可以在设置面板->嵌字菜单中改用全局设置. 全局字体格式就是未编辑任何文本块时右侧字体面板显示的格式:  
<img src="doc/src/global_font_format.png"> 

## 画板

## 修复画笔
<img src="doc/src/imgedit_inpaint.gif">
<p align = "center">
修复画笔
</p>

### 矩形工具
<img src="doc/src/rect_tool.gif">
<p align = "center">
矩形工具
</p>

按下鼠标左键拖动矩形框抹除框内文字, 按下右键拉框清除框内修复结果.  
抹除结果取决于算法(gif中的"方法1"和"方法2")对文字区域估算的准确程度, 一般拉的框最好稍大于需要抹除的文本块. 两种方法都比较玄学, 能够应付绝大多数简单文字简单背景, 部分复杂背景简单文字/简单背景复杂文字, 少数复杂背景复杂文字, 可以多拉几次试试.  
勾选"自动"拉完框立即修复, 否则需要按下"修复"或者空格键才进行修复, 或"Ctrl+D"删除矩形选框.  

## 文本编辑
<img src="doc/src/textedit.gif">


<p align = "center">
文本编辑
</p>

<img src="doc/src/multisel_autolayout.gif" div align=center>
<p align=center>
批量文本格式调整及自动排版
</p>

## 界面说明及快捷键
* Ctrl+Z, Ctrl+Y可以撤销重做大部分操作，注意翻页后撤消重做栈会清空
* A/D或pageUp/Down翻页, 如果当前页面未保存会自动保存
* "T"切换到文本编辑模式下(底部最右"T"图标), W激活文本块创建模式后在画布右键拉文本框
* "P"切换到画板模式, 右下角滑条改原图透明度
* 底部左侧"OCR"和"A"按钮控制启用/禁用OCR翻译功能, 禁用后再Run程序就只做文本检测和抹字  
* 设置面板配置各自动化模块参数
* Ctrl++/-或滚轮缩放画布
* Ctrl+A可选中界面中所有文本块
* Ctrl+F查找当前页, Ctrl+G全局查找

<img src="doc/src/configpanel.png">  

# 自动化模块
本项目重度依赖[manga-image-translator](https://github.com/zyddnys/manga-image-translator), 在线服务器和模型训练需要费用, 有条件请考虑支持一下
- Ko-fi: <https://ko-fi.com/voilelabs>
- Patreon: <https://www.patreon.com/voilelabs>
- 爱发电: <https://afdian.net/@voilelabs>

Sugoi翻译器作者: [mingshiba](https://www.patreon.com/mingshiba).
  
### 文本检测
暂时仅支持日文(方块字都差不多)和英文检测, 训练代码和说明见https://github.com/dmMaze/comic-text-detector

### OCR
 * mit_32px模型来自manga-image-translator, 支持日英汉识别和颜色提取
 * mit48px_ctc模型来自manga-image-translator, 支持日英汉韩语识别和颜色提取
 * [manga_ocr](https://github.com/kha-white/manga-ocr)来自[kha-white](https://github.com/kha-white), 支持日语识别, 注意选用该模型程序不会提取颜色

### 图像修复
  * AOT修复模型来自manga-image-translator
  * patchmatch是非深度学习算法, 也是PS修复画笔背后的算法, 实现来自[PyPatchMatch](https://github.com/vacancy/PyPatchMatch), 本程序用的是我的[修改版](https://github.com/dmMaze/PyPatchMatchInpaint)
  

### 翻译器

 * 谷歌翻译能挂代理建议把url从cn改成com
 * 彩云, 需要申请[token](https://dashboard.caiyunapp.com/)
 * papago  
 * DeepL 和 Sugoi(及它的CT2 Translation转换)翻译器, 感谢[Snowad14](https://github.com/Snowad14)  

 如需添加新的翻译器请参考[加别的翻译器](doc/加别的翻译器.md), 本程序添加新翻译器只需要继承基类实现两个接口即可不需要理会代码其他部分, 欢迎大佬提pr

## 杂
* 如果电脑带N卡, 程序默认对所有模型启用GPU加速, 默认配置下显存占用在6G左右. 4G显存调小修复器inpaint_size即可.  
* 感谢[bropines](https://github.com/bropines)提供俄语翻译

## 一键翻译结果预览
|            Original            |         Translated (CHS)         |         Translated (ENG)         |
| :-----------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------: |
|![Original](ballontranslator/data/testpacks/manga/original2.jpg 'https://twitter.com/mmd_96yuki/status/1320122899005460481')| ![Translated (CHS)](doc/src/result2.png) | ![Translated (ENG)](doc/src/original2_eng.png) |
|![Original](ballontranslator/data/testpacks/manga/original3.jpg 'https://twitter.com/_taroshin_/status/1231099378779082754')| ![Translated (CHS)](doc/src/original3.png) | ![Translated (ENG)](doc/src/original3_eng.png) |
| ![Original](ballontranslator/data//testpacks/manga/AisazuNihaIrarenai-003.jpg) | ![Translated (CHS)](doc/src/AisazuNihaIrarenai-003.png) | ![Translated (ENG)](doc/src/AisazuNihaIrarenai-003_eng.png) |
|           ![Original](ballontranslator/data//testpacks/comics/006049.jpg)           | ![Translated (CHS)](doc/src/006049.png) | |
