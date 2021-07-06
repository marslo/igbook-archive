# media

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [Highly Recommanded](media.md#highly-recommanded)
* [Video](media.md#video)
  * [Get Audio from video](media.md#get-audio-from-video)
  * [Convert flv to mp4](media.md#convert-flv-to-mp4)
  * [Combine video and audio](media.md#combine-video-and-audio)
* [Image](media.md#image)
  * [identity an image](media.md#identity-an-image)
  * [convert svg to png](media.md#convert-svg-to-png)
  * [convert HEIC/HEIF to PNG](media.md#convert-heicheif-to-png)

## Highly Recommanded

[cmd.to](https://cmd.to/fm)

## Video

### Get Audio from video

```bash
$ ffmpeg -i source.mpg -f s16le -acodec pcm_s16le audio.raw
```

### Convert flv to mp4

```bash
$ ffmpeg -i name.flv -qscale 0 name.mp4
```

#### convert to 5 mins \(300 sec\)

```bash
$ ffmpeg -i name.mp4 -ss 0 -t 300 name-5m.mp4
```

#### sequence convert \(every 5 mins ~&gt; 300 secs\)

* first 5 mins \(0 ~&gt; 300\)

```bash
$ ffmpeg -i name.mp4 -ss 0 -t 300 name-5m-1.mp4
```

* second 5 mins \(300\*1 ~&gt; 300\)

```bash
$ ffmpeg -i name.mp4 -ss 300 -t 300 name-5m-2.mp4
```

* third 5 mins \(300\*2 ~&gt; 300\)

```bash
$ ffmpeg -i name.mp4 -ss 600 -t 300 name-5m-3.mp4
```

### Combine video and audio

```bash
$ ffmpeg -i <origin-video> -i <origin-audio> -c copy -map 0:0 -map 1:0 -shortest <new-video>
```

![combine](../.gitbook/assets/ffmpeg-combine%20%282%29.jpg)

## Image

### identity an image

```bash
$ identify arms009.jpg | grep -o "[[:digit:]]*x[[:digit:]]*" | tail -1
1024x768
```

### convert svg to png

```bash
$ qlmanage -t -s 1000 -o . k-1.svg
```

### convert HEIC/HEIF to PNG

![magick](../.gitbook/assets/heic-1%20%282%29.gif)

```bash
$ brew install imagemagick --with-libheif

# for single convert
$ magick convert [-monitor] <name>.HEIC <new-name>.png

# for batch convert
$ magick mogrify [-monitor] -format png *.HEIC.
```

