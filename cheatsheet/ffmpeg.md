# ffmpeg Cheatsheet

> 最近发现这个真的很好用。小丸主要是太久没更新了，那不如自己写一个更新版的？（其实替换小丸的组件也可以吧）

## 前言

## Args

裁剪, Trim

```bash
ffmpeg -i input.mp4 -ss "hh:mm:ss" -to "hh:mm:ss" -c copy output.mp4
```

转码x264

```bash
ffmpeg -i input.mp4 -c:v libx264 -crf 17 -c:a copy output.mp4
```

查看视频信息

```
ffprobe input.mp4
```

## youtube-dl

> Usage: Youtube & Nico & Bilibili videos

```
youtube-dl URL --proxy 127.0.0.1:1080 -F
youtube-dl URL --proxy 127.0.0.1:1080 -f 521(video)
youtube-dl URL --proxy 127.0.0.1:1080 -f 177(audio)
```

合并音轨流和视频流

```
ffmpeg -i audio.webm -i video.mp4 -c:a copy -c:v copy output.mp4
```

## refs

[小丸工具箱](https://maruko.appinn.me/index.html)