## Audio configuration

---

### Audio ` `

<pre><code class="hljs language-js javascript" data-line-numbers="3,8" data-trim>
const audioConfig = {
  type: 'file',
  audio: {
    contentType: 'video/mp4; codecs=mp4a.40.2',
    channels: 2,
    bitrate: 128000,
    samplerate: 44100,
  },
};
navigator.mediaCapabilities.decodingInfo(audioConfig);
</code></pre>

Note:
- contentType
- channels
- bitrate
- samplerate

---

### `audio.contentType` property

<pre><code class="hljs language-js javascript" data-line-numbers="3,4,8" data-trim>
const audioConfig = {
  type: 'file',
  audio: {
    contentType: 'video/mp4; codecs=mp4a.40.2',
    channels: 2,
    bitrate: 128000,
    samplerate: 44100,
  },
};
navigator.mediaCapabilities.decodingInfo(audioConfig);
</code></pre>

---

### `audio.channels` property

<pre><code class="hljs language-js javascript" data-line-numbers="3,5,8" data-trim>
const audioConfig = {
  type: 'file',
  audio: {
    contentType: 'video/mp4; codecs=mp4a.40.2',
    channels: 2,
    bitrate: 128000,
    samplerate: 44100,
  },
};
navigator.mediaCapabilities.decodingInfo(audioConfig);
</code></pre>

Note:
Can be defined as a number (e.g. `2` or `5.1`).

---

### `audio.bitrate` property

<pre><code class="hljs language-js javascript" data-line-numbers="3,6,8" data-trim>
const audioConfig = {
  type: 'file',
  audio: {
    contentType: 'video/mp4; codecs=mp4a.40.2',
    channels: 2,
    bitrate: 128000,
    samplerate: 44100,
  },
};
navigator.mediaCapabilities.decodingInfo(audioConfig);
</code></pre>

Note:
Audio bitrate in bps.

---

### `audio.samplerate` property

<pre><code class="hljs language-js javascript" data-line-numbers="3,7,8" data-trim>
const audioConfig = {
  type: 'file',
  audio: {
    contentType: 'video/mp4; codecs=mp4a.40.2',
    channels: 2,
    bitrate: 128000,
    samplerate: 44100,
  },
};
navigator.mediaCapabilities.decodingInfo(audioConfig);
</code></pre>

Note:
Audio samplerate expressed in Hz (i.e. number of samples of audio per second).
