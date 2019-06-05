## Video configuration

---

### Video ` `

<pre><code class="hljs language-js javascript" data-line-numbers data-trim>
const videoConfig = {
  type: 'file',
  video: {
    contentType: 'video/mp4; codecs=av1',
    width: 640,
    height: 480,
    bitrate: 1200000,
    framerate: 30,
  },
};
navigator.mediaCapabilities.decodingInfo(videoConfig);
</code></pre>

Note:
decodingInfo also exists, but not going to talk about it.
Works on audio files too, but I will focus on video.

---

### `type` property

<pre><code class="hljs language-js javascript" data-line-numbers="2" data-trim>
const videoConfig = {
  type: 'file', // 'file' | 'media-source'
  video: {
    contentType: 'video/mp4; codecs=av1',
    width: 640,
    height: 480,
    bitrate: 1200000,
    framerate: 30,
  },
};
navigator.mediaCapabilities.decodingInfo(videoConfig);
</code></pre>

Note:
Can be 'file' or 'media-source'. Unified API for files and media sources.
Remember media.canPlayType and MediaSource.isTypeSupported. More consistency!

---

### `video.contentType` property

<pre><code class="hljs language-js javascript" data-line-numbers="3-4,9" data-trim>
const videoConfig = {
  type: 'file',
  video: {
    contentType: 'video/mp4; codecs=av1',
    width: 640,
    height: 480,
    bitrate: 1200000,
    framerate: 30,
  },
};
navigator.mediaCapabilities.decodingInfo(videoConfig);
</code></pre>

Note:
Same codec strings than for the existing APIs.

---

### `video.width` & `video.height` property

<pre><code class="hljs language-js javascript" data-line-numbers="3,5-6,9" data-trim>
const videoConfig = {
  type: 'file',
  video: {
    contentType: 'video/mp4; codecs=av1',
    width: 640,
    height: 480,
    bitrate: 1200000,
    framerate: 30,
  },
};
navigator.mediaCapabilities.decodingInfo(videoConfig);
</code></pre>

Note:
Dimensions in pixels.

---

### `video.bitrate` property

<pre><code class="hljs language-js javascript" data-line-numbers="3,7,9" data-trim>
const videoConfig = {
  type: 'file',
  video: {
    contentType: 'video/mp4; codecs=av1',
    width: 640,
    height: 480,
    bitrate: 1200000,
    framerate: 30,
  },
};
navigator.mediaCapabilities.decodingInfo(videoConfig);
</code></pre>

Note:
Video bitrate in bps. This is for the video only, audio is on another property.
Max bitrate for VBR ; average bitrate for CBR.

---

### `video.framerate` property

<pre><code class="hljs language-js javascript" data-line-numbers="3,8,9" data-trim>
const videoConfig = {
  type: 'file',
  video: {
    contentType: 'video/mp4; codecs=av1',
    width: 640,
    height: 480,
    bitrate: 1200000,
    framerate: 30,
  },
};
navigator.mediaCapabilities.decodingInfo(videoConfig);
</code></pre>

Note:
Frame rate in fps.
