# ffmpeg基础

> Author: Sylvie233
>
> Date: 23/2/24

[TOC]

## 基础介绍

容器

复用、解复用

码率、帧率

AVC、AAC



视频编解码

<img src="ffmpeg.assets/image-20230224145527138.png" alt="image-20230224145527138" style="zoom:67%;" />



### ffmpeg

```
ffmpeg:
	-ac: 音频的Channel数
	-acodec:
		ac3:
		copy:
		libmp3lame:
	-af: 音频过滤器
	-aframes: 输出的音频帧数
	-an: 不处理音频
	-ar: 音频采样率
	-aspect: 横纵比
	-b: 修改码率
		:a: 音频码率
		:v: 视频码率
			400k:
	-bsfs: 实现可用比特流filter
	-buildconf: 显示编译配置
	-codecs: 显示可用编解码器
	-colors: 显示可用的颜色名称
	-decoders: 显示可用解码器
	-demuxers: 显示可用解复用器
	-devices: 支持设备
	-dshow:
	-encoders: 显示可用编码器
	-f: 指定格式
		concat: 拼接
		f32le:
		gif:
		image2:
	-filter_complex:
		amix:
			inpus:
			duration:
			dropout_transition:
		nullsrc:
	-filters: 显示可用的过滤器
	-formats: 显示可用格式
	-h:
		full:	
		long:
	-i: 输入流
		.txt: 输入文件列表
		audio: 音频
		video: 视频
	-layouts: 显示标准声道名称
	-list_devices:
	-list_options:
	-muxers: 显示可用复用器
	-pix_fmt:
		rgb24:
		yuv420p:
	-pix_fmts: 显示可用的像素格式
	-protocols: 显示可用的协议
	-r: 帧速率
	-re:
	-s: 设定画面宽高
	-sample_fmts: 显示可用的音频采样格式
	-ss: 开始时间
	-t: 时间长度
	-vcodec: 
		copy: 保留
		libx264: h264格式
		libx265:
	-version:
	-vf: 视频过滤器
		crop: 裁剪
			iw:
			ih:
		drawtext: 文字水印
			enable:
			fontsize:
			x:
			y:
			alpha:
			text:
			fontfile:
			box:
		movie: 图片水印
		overlay: 叠加
			x:
			y:
			eof_action:
			shortest:
			format:
	-vframes: 输出的视频帧数
	-vn: 不处理视频
	-y: 
```



### ffplay

```
ffplay:
	-ac:
	-acodec:
	-af: 音频过滤器
		atempo: 变速
	-an: 禁用音频
	-ar:
	-ast: 音频流索引
	-autoexit:
	-bytes: 按字节跳转
	-codec:
		:v:
	-f: 格式
	-fast:
	-framerate:
	-fs: 全屏模式
	-genpts:
	-h:
	-infbuf: 不限制输入缓存区大小
	-loop: 循环次数
	-noborder: 无边框窗口
	-pixel_format:
	-scodec:
	-showmode: 显示模式
	-sn: 禁用字幕
	-ss: 跳转
	-sst: 字幕流索引
	-stats: 统计信息
	-sync: 同步类型
    -t: 设置长度
    -vcodec:
    -vf: 视频过滤器
    	hflip: 视频反转
    	setpts: 变速播放
    	transpose: 视频选择
    	vflip: 视频反转
	-video_size:
	-vn: 禁用视频
	-volume:
	-vst: 视频流索引
	-window_title: 窗口标题
	-x: 宽度
	-y: 高度
```

<img src="ffmpeg.assets/image-20230224151802157.png" alt="image-20230224151802157" style="zoom:67%;" />





### ffprobe

```
ffprobe:
	-h:
```





## 核心内容