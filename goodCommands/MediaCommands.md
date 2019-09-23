<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Get Audio from video](#get-audio-from-video)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### Get Audio from video
    ┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ ffmpeg -i source.mpg -f s16le -acodec pcm_s16le audio.raw
