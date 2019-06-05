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
  audio: {
    contentType: 'video/mp4; codecs=mp4a.40.2',
    channels: 2,
    bitrate: 128000,
    samplerate: 44100,
  },
};
navigator.mediaCapabilities.decodingInfo(videoConfig);
</code></pre>

---

## `contentType` generation

For MP4, use [mp4info](https://www.bento4.com/)

---

CLI:

```bash
$ mp4info video.mp4 | grep Codec
    Codecs String: avc1.4D4020
    Codecs String: mp4a.40.2
```

JavaScript:

```js
const videoContentType = 'video/mp4; codecs=avc1.4D4020';
const audioContentType = 'audio/mp4; codecs=mp4a.40.2';
```

Note:
Only for MP4.
Not sure how to do it for webm containers.

---

The other properties can be generated with mp4info too.

---

## Browser support

- ✅ Chrome 66 (desktop + mobile) April 2018 <!-- .element: class="fragment" -->
- ✅ Firefox 63 (desktop + mobile) October 2018 <!-- .element: class="fragment" -->
- ✅ Opera 55 (desktop + mobile) July 2018 <!-- .element: class="fragment faded" -->
- ☑️ Safari Technology Preview Release 66 September 2018 <!-- .element: class="fragment faded" -->
- ☑️ Edge <!-- .element: class="fragment faded" -->

---

## Polyfill?

⚠️ Not polyfillable

Note:
But can be mimicked by capturing data about playback of various media profiles.
Use the Media Playback Quality with media.getVideoPlaybackQuality() and collect metrics (https://developer.mozilla.org/en-US/docs/Web/API/VideoPlaybackQuality).
Then use these metrics to inform the result of the polyfill.

---

## What now?

- Write such a polyfill?
- Add support to caniuse.com? <!-- .element: class="fragment" -->
- Pester other browsers for implementation? <!-- .element: class="fragment" -->
- CLI to generate a video/audio profile given a file? <!-- .element: class="fragment" -->
- Or simply use it! <!-- .element: class="fragment" -->

---

## Demo time

---

## Questions?

---

## Spec

https://wicg.github.io/media-capabilities/

---

## Links

- https://developer.mozilla.org/en-US/docs/Web/API/Media_Capabilities_API
- https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats
- https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/canPlayType
- https://developer.mozilla.org/en-US/docs/Web/API/MediaSource/isTypeSupported
- https://developers.google.com/web/updates/2017/12/chrome-63-64-media-updates#media-capabilities-decoding-info-api

---

## Misc

- https://www.chromestatus.com/feature/5869632707624960
- https://bugzilla.mozilla.org/show_bug.cgi?id=1409664
- https://bugs.webkit.org/show_bug.cgi?id=181064
