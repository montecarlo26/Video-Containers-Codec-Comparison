# Why

I want to know the best Video format to read and write video with audio.

## High Level Overview

* A codec is an algorithm that compresses and decompresses audio and / or video.
* A video file is typically a container with multiple codecs. For example, a .mp4 file may use the H264 codec for video and MP2 codec for audio.

Codecs are pretty much mandatory, as storing raw video and audio files would take up too much space. The 34 second 1920x1080 60fps video used in the test would be over 12GB if uncompressed.

## The Test

A source video was converted to various formats. The source video is 1920x1080 60fps RGB-8 bit, 48K 16bit stereo, 34 seconds.
The video is a highlight from Marvel Rivals with a decent amount of action and movement in the scene. Too big to upload.
Shotcut was used to save the video in the various formats.
* source video size: 1920x1080 pixels * 3 channels * 8 bits per channel * 60 frames per second * 34 seconds = 12.7 GigaBytes
* source audio size: 48000 samples per second * 2 channels * 16 bits per channel * 34 seconds = 6.53MegaBytes

<br>

<p align="center" width="100%">
<img src="/codecs compared.png?raw=true" width="90%" height="90%">
</p>

<br>

## Results

All videos are able to play instantly, decoding time is not a variable. Audio has a much smaller impact than video and its compression is more trivial, being a 1-dimensional array of samples, so I didn't bother to benchmark it. The various codecs can be tweaked but I didn't mess with them for simplicity. A video with different dimensions and duration may affect the results.

* .mp4 is the best middleground. License mess with extensions despite initial release in 1999
* .mpg / .avi MPEG-1 is underrated despite its age. Its simple format, fast encoding time, expired patents and decent quality make it desirable. Main drawback is file size
* .mpg MPEG-2 video quality is unacceptable
* .webm VP8 is okay. It is inferior to VP9
* .webm VP9 is the second best middleground and boasts the smallest file size. It is half the size of VP8 with a shorter encoding time and is only ~5% worse quality
* .webm AV1 encoding time is unacceptable
* <b>Bonus:</b> HEVC H265 is proprietary and would have required me to pay to play it. Encoding time was 33 seconds and file size is 26,670KB

I added the VP9 Video result to the repository for reference since it was the only file under 25MB that can be uploaded to github, if you're curious about the video that was used.

## Conclusion

.mp4, .mpg (MPEG-1), and .webm (VP9) are the best contenders. Use base .mp4 as of ~2028 or later to avoid licensing issues. Use .mpg if file size isn't too big of an issue. 

My overall pick is .webm with VP9. VP9's encoding time leaves a bit to be desired but overall its extremely small file size, video quality, and free license paired with .webm which is also free and open (and specific compared to .mkv which is a bit too generalized) makes it the best option imo.
