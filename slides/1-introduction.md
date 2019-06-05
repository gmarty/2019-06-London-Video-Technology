# Can a browser<br>play that?

## The Media Capabilities API<br>to the rescue

---

## Guillaume C. Marty

### @g_marty

<img src="img/g_marty.jpg" alt="@g_marty" title="@g_marty" class="profile" style="width: 320px;"/>

Front-end engineer at <img src="img/twitter-logo.svg" alt="Twitter" title="Twitter" style="width: 60px; vertical-align: middle; padding-left: 10px;"/>

---

#### Previous video projects

<a href="https://github.com/gmarty/DVD.js"><img src="img/dvd.js.svg" alt="dvd.js" title="dvd.js" style="width: 320px;"/></a>

Note:
DVD.js
Into media preservation / archiving
Into video in general

---

<img src="img/video-history.png" alt="Video on the web" title="Video on the web" style="height: 640px;"/>

Note:
Screenshot from caniuse for the support of the video element.
Horizontal axis: IE, Edge, Firefox, Chrome, Safari, Opera
Vertical axis: browsers version aligned on time
Video on the web been around a long time.
Browsers started implementing the video HTML element in mid-2009.
By mid-2011, most browsers supported it.

---

![Playback issue](img/playback-issue.png)

---

## Facts

- Video codecs are complex
- Browsers can't guarantee playback

Note:
Media readability depends on:

- the codec, container, resolution, framerate, bitrate, (encryption scheme)...
- the software, browser, browser version, plugins installed, OS, OS version...
- the hardware, CPU/GPU...
  In other word, determining if a browser can read a media is hard.

---

### Legacy API 1

```js
const mediaEl = document.createElement("video");
const codecString = "video/mp4; codecs=av1";
const support = mediaEl.canPlayType(codecString);

// support can be:
//   '' (definitely can't play)
//   'maybe' (won't know until I try to play it)
//   'probably' (looks like it can be played)
```

---

### Legacy API 2

```js
const codecString = "video/mp4; codecs=av1";
const support = MediaSource.isTypeSupported(codecString);

// support can be:
//   false (definitely can't play)
//   true (looks like it can be played)
```

Note:
Everything OK?
Please note the discrepancy in both the API names and returned value!
One runs on an instance ; the other runs on the object.
There are similar APIs for encoding, but not going to talk about it here.

---

## No granularity

- Smoothness?
- Battery impact?
- Hardware accelerated?
- Encrypted content?

Note:

- What about smoothness (4k video on lowend hardware can be choppy)? 🐌
- What about performance on mobile (hardware accelerated)? 😱
- What about the impact on battery life (think mobile)? 🔋
- How to decide between several formats available? 🎲
- > Do output capabilities (e.g. color gamut, dynamic range, audio channels) match content?
- > Are security requirements (e.g. encryption, HDCP, etc) supported or playback-impacting?
  > But above all, can it be played or not?! 🤷🏽‍♂️

---

<img src="img/shrug.svg" alt="We don't know" title="We don't know" style="width: 320px;"/>

---

## Solution

`navigator.mediaCapabilities`

Note:
This new API reflects a change in perspective:

- Emphasis on mobile
- Modern API
  In the question "can a browser play this media?", this new API answers the how well.

---

* Query based API 🛎
* Returns detailed report 📋 <!-- .element: class="fragment" -->
* Promise-based ⚡️ <!-- .element: class="fragment" -->

Note:
You need to know about your videos.
Good for performance but remember to update your UI accordingly.

---

### `MediaCapabilitiesInfo` object

```js
{
    supported: true | false,
    smooth: true | false,
    powerEfficient: true | false,
}
```

Note:
The promise resolves with a MediaCapabilitiesInfo object.
powerEfficient = can be used with the Battery Status API.
