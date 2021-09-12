# ffmpeg Cheatsheet

> 最近发现这个真的很好用。小丸主要是太久没更新了，那不如自己写一个更新版的？（其实替换小丸的组件也可以吧）


## ffmpeg 常用

- 裁剪, Trim

```bash
ffmpeg -i input.mp4 -ss "hh:mm:ss" -to "hh:mm:ss" -c copy output.mp4
```

- 转码x264，不过我现在一般都不加`crf`参数了...（你是完全不懂这个默认参数吧）

```bash
ffmpeg -i input.mp4 -c:v libx264 -crf 17 -c:a copy output.mp4
```


- 查看视频信息

```
ffprobe input.mp4
```

- 转视频为gif

```bash
ffmpeg -ss 30 -t 3 -i input.mp4 -vf "fps=10,scale=320:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" -loop 0 output.gif
```

- This example will skip the first 30 seconds (-ss 30) of the input and create a 3 second output (-t 3).
- fps filter sets the frame rate. A rate of 10 frames per second is used in the example.
- scale filter will resize the output to 320 pixels wide and automatically determine the height while preserving the aspect ratio. The lanczos scaling algorithm is used in this example.
- palettegen and paletteuse filters will generate and use a custom palette generated from your input. These filters have many options, so refer to the links for a list of all available options and values. Also see the Advanced options section below.
- split filter will allow everything to be done in one command and avoids having to create a temporary PNG file of the palette.
- Control looping with -loop output option but the values are confusing. A value of 0 is infinite looping, -1 is no looping, and 1 will loop once meaning it will play twice. So a value of 10 will cause the GIF to play 11 times.

### 提取音频流

```bash
ffmpeg -i input-video.avi -vn -c:a  output-audio.aac

```


## youtube-dl

> 可用范围：Youtube & Nico & Bilibili 。注意这里一些选项需要`PATH`里有`ffmpeg`


- 查看某个特定流

```bash
youtube-dl URL --proxy 127.0.0.1:1080 -F
youtube-dl URL --proxy 127.0.0.1:1080 -f 521 # 单独抽取video
youtube-dl URL --proxy 127.0.0.1:1080 -f 177 # 单独抽取audio
```

- 合并音轨流和视频流（在提取出特定流后）

```bash
ffmpeg -i audio.webm -i video.mp4 -c:a copy -c:v copy output.mp4
# YouTube的音频流 opus，需要转成适用性更广的aac（B站偶尔转码失败）
ffmpeg -i audio.webm -i video.mp4 -c:a aac -c:v copy output.mp4
```


### 获取YouTube封面

> 资料来源：[s.o.f.](https://stackoverflow.com/questions/2068344/how-do-i-get-a-youtube-video-thumbnail-from-the-youtube-api)

```bash
https://img.youtube.com/vi/T0QDm7kq05A/maxresdefault.jpg
https://img.youtube.com/vi/gX6ENYK4oLU/sddefault.jpg 
https://img.youtube.com/vi/gX6ENYK4oLU/hqdefault.jpg
# 低于1080P的没有maxresdefault
```

### 遍历播放列表（常用）

目前其实最常用应该是这个。注意`-f bestvideo+bestaudio`参数对单一视频也可以使用，这个参数会调用`ffmpeg`然后将两个流塞进`mkv`中，如果要上传的话需要转码

```bash
youtube-dl URL --proxy 127.0.0.1:10809 -f bestvideo+bestaudio
# 单个视频
youtube-dl -o '%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s' https://www.youtube.com/playlist?list=PLBXCln5NVIW4NnNaZR6GZnwTkwyXfnuS1 --proxy 127.0.0.1:10809 -f bestvideo+bestaudio
# 播放列表
```

## 参考链接

1. [小丸工具箱](https://maruko.appinn.me/index.html)
2. [ffmpeg-gif](https://superuser.com/questions/556029/how-do-i-convert-a-video-to-gif-using-ffmpeg-with-reasonable-quality)