### Get Audio from video
    ┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ ffmpeg -i source.mpg -f s16le -acodec pcm_s16le audio.raw
