# GRUB-Themes

* [GRUB-Themes](#grub-themes)
  * [分辨率选择建议](#分辨率选择建议)
  * [主题列表](#主题列表)
    * [Frieren-GRUB-Theme](#frieren-grub-theme)
  * [使用方法](#使用方法)
    * [自动安装](#自动安装)
    * [手动安装](#手动安装)
    * [安装作为Ventoy主题](#安装作为ventoy主题)
  * [修改指南](#修改指南)
    * [修改背景](#修改背景)
  * [特别感谢](#特别感谢)

## 分辨率选择建议

* 16:9/16:10
  * 1920x1080 ➡ 1080p
  * 2560x1440 ➡ 2k
  * 3840x2160 ➡ 4k

* 21:9
  > TODO

## 主题列表

> 目前仅有1个主题，但...也许以后会有更多？

### Frieren-GRUB-Theme

## 使用方法

### 自动安装

> 这是最推荐的方式，简单，且相对稳定。但请注意，这种方式会覆盖您原有的 GRUB 主题。

1. 在[Release](https://github.com/Steven-Zhl/GRUB-Themes/releases)中，根据您的显示器分辨率，下载合适的`frieren-grub-theme.tar.gz`压缩包。
2. 解压，进入解压后的项目文件夹
3. 执行文件夹内的安装脚本(`install.sh`)

### 手动安装

### 安装作为Ventoy主题

## 修改指南

> 作为一个开源项目，您可以在遵循开源协议条款的基础上随意修改、分发本项目。本节介绍一些修改的操作方法和注意事项。

### 修改背景

* 如需修改背景，直接使用新的背景图片替换掉`background.jpg`即可。
* 但请注意，请确保背景图片的编码方式为`mjpeg (Baseline)`，色彩格式为`yuvj420p`，若不满足这些条件，Ventoy可能无法以GUI模式启动。
    > 会提示："alloc magic is broken at 0xXXXXXXXX: XXXXXXXX Aborted. Press any key to exit."
* 若您不确定这些信息，您可以使用`ffprobe`进行查看：

  ```bash
  ffprobe -v error -select_streams v:0 -show_entries stream=codec_name,pix_fmt -of default=noprint_wrappers=1 "background.jpg"
  ```

* 您可以使用`ffmpeg`将图片转换为符合的格式：

  ```bash
  ffmpeg -i "input.jpg" -vf "format=yuvj420p" -c:v mjpeg -q:v 2 -huffman optimal -acodec copy "output.jpg"
  ```

## 特别感谢

* [Ventoy文档](https://www.ventoy.net/cn/doc_news.html)
* [grub2-themes](https://github.com/vinceliuice/grub2-themes): 安装脚本(`install.sh`)参考自该项目
