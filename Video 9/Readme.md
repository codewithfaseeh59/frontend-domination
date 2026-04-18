# 🎬 HTML Media Tags — Complete Reference

A detailed guide covering `<video>`, `<audio>`, `<source>`, `<track>`, `<picture>`, `<img>`, and `<figure>` tags in HTML5.

---

## Table of Contents

1. [Video Tag](#-video-tag)
2. [Audio Tag](#-audio-tag)
3. [Source Tag](#-source-tag)
4. [Track Tag](#-track-tag)
5. [Picture Tag](#-picture-tag)
6. [Figure & Figcaption](#-figure--figcaption-tags)
7. [Img Tag (Extended)](#-img-tag-extended)
8. [Media Events Reference](#-media-events-reference)
9. [JavaScript Media API](#-javascript-media-api)
10. [Best Practices](#-best-practices)

---

## 🎥 Video Tag

The `<video>` element is used to embed video content directly in the browser without any third-party plugin.

### Basic Syntax

```html
<video src="video.mp4" controls></video>
```

### Full Example

```html
<video
  src="movie.mp4"
  width="800"
  height="450"
  controls
  autoplay
  muted
  loop
  poster="thumbnail.jpg"
  preload="auto"
>
  Your browser does not support the video tag.
</video>
```

### Attributes

| Attribute      | Value / Type      | Description                                                                 |
|----------------|-------------------|-----------------------------------------------------------------------------|
| `src`          | URL               | Path to the video file                                                      |
| `controls`     | Boolean           | Shows native browser playback controls (play, pause, volume, fullscreen)    |
| `autoplay`     | Boolean           | Starts playing the video automatically (requires `muted` in most browsers)  |
| `muted`        | Boolean           | Mutes the audio on load (required for autoplay in Chrome/Firefox)           |
| `loop`         | Boolean           | Replays the video when it ends                                              |
| `poster`       | URL               | Image shown before the video loads or plays                                 |
| `preload`      | `none` / `metadata` / `auto` | Hints the browser how much to preload                          |
| `width`        | px / %            | Width of the video player                                                   |
| `height`       | px / %            | Height of the video player                                                  |
| `playsinline`  | Boolean           | Plays inline on iOS instead of fullscreen                                   |
| `crossorigin`  | `anonymous` / `use-credentials` | Handles CORS for external video sources                  |
| `disablepictureinpicture` | Boolean | Prevents the Picture-in-Picture mode                              |

### Supported Formats

| Format   | Extension  | MIME Type      | Browser Support                         |
|----------|------------|----------------|-----------------------------------------|
| MP4/H.264 | `.mp4`    | `video/mp4`    | All modern browsers ✅                  |
| WebM     | `.webm`    | `video/webm`   | Chrome, Firefox, Edge ✅                |
| Ogg      | `.ogv`     | `video/ogg`    | Firefox, Chrome (limited) ⚠️           |

> **Tip:** Always provide MP4 as a fallback since it has the widest support.

---

## 🔊 Audio Tag

The `<audio>` element embeds sound content like music, podcasts, or sound effects.

### Basic Syntax

```html
<audio src="sound.mp3" controls></audio>
```

### Full Example

```html
<audio
  src="podcast.mp3"
  controls
  autoplay
  muted
  loop
  preload="metadata"
>
  Your browser does not support the audio tag.
</audio>
```

### Attributes

| Attribute  | Value / Type              | Description                                                    |
|------------|---------------------------|----------------------------------------------------------------|
| `src`      | URL                       | Path to the audio file                                         |
| `controls` | Boolean                   | Shows native browser audio controls                            |
| `autoplay` | Boolean                   | Plays audio as soon as it's ready                              |
| `muted`    | Boolean                   | Mutes the audio by default                                     |
| `loop`     | Boolean                   | Loops the audio indefinitely                                   |
| `preload`  | `none` / `metadata` / `auto` | Controls how much audio is preloaded                        |
| `crossorigin` | `anonymous` / `use-credentials` | Handles CORS for external audio                      |

### Supported Formats

| Format | Extension | MIME Type      | Browser Support           |
|--------|-----------|----------------|---------------------------|
| MP3    | `.mp3`    | `audio/mpeg`   | All modern browsers ✅    |
| OGG    | `.ogg`    | `audio/ogg`    | Firefox, Chrome ✅        |
| WAV    | `.wav`    | `audio/wav`    | All modern browsers ✅    |
| AAC    | `.aac`    | `audio/aac`    | Chrome, Edge, Safari ✅   |
| FLAC   | `.flac`   | `audio/flac`   | Chrome, Firefox ✅        |

---

## 🔀 Source Tag

The `<source>` tag is used inside `<video>`, `<audio>`, or `<picture>` to define **multiple media sources**. The browser picks the first one it can play.

### Syntax

```html
<video controls width="800">
  <source src="video.webm" type="video/webm" />
  <source src="video.mp4" type="video/mp4" />
  <p>Your browser doesn't support HTML video.</p>
</video>

<audio controls>
  <source src="audio.ogg" type="audio/ogg" />
  <source src="audio.mp3" type="audio/mpeg" />
</audio>
```

### Attributes

| Attribute | Description                                                              |
|-----------|--------------------------------------------------------------------------|
| `src`     | URL of the media file                                                    |
| `type`    | MIME type of the resource (helps browser skip unsupported formats fast)  |
| `media`   | Media query string (used inside `<picture>`, e.g. `(min-width: 800px)`) |
| `sizes`   | Used in `<picture>` to define display sizes                              |
| `srcset`  | Used in `<picture>` for responsive image sets                            |

> **Why use `<source>` instead of `src`?**
> When you list multiple `<source>` elements, the browser tests each in order and uses the first compatible one — giving you fallback support across all browsers.

---

## 📝 Track Tag

The `<track>` tag adds **timed text tracks** (subtitles, captions, chapters, metadata) to `<video>` or `<audio>`.

### Syntax

```html
<video src="movie.mp4" controls>
  <track
    kind="subtitles"
    src="subtitles-en.vtt"
    srclang="en"
    label="English"
    default
  />
  <track
    kind="subtitles"
    src="subtitles-ur.vtt"
    srclang="ur"
    label="Urdu"
  />
  <track
    kind="chapters"
    src="chapters.vtt"
    srclang="en"
    label="Chapters"
  />
</video>
```

### Attributes

| Attribute  | Description                                                                 |
|------------|-----------------------------------------------------------------------------|
| `kind`     | Type of text track (`subtitles`, `captions`, `descriptions`, `chapters`, `metadata`) |
| `src`      | URL of the `.vtt` (WebVTT) file                                             |
| `srclang`  | Language of the track (e.g. `en`, `ur`, `hi`)                              |
| `label`    | Human-readable label shown in the browser's subtitle menu                   |
| `default`  | Boolean — this track is enabled by default                                  |

### `kind` Values Explained

| Kind           | Description                                                      |
|----------------|------------------------------------------------------------------|
| `subtitles`    | Translates spoken dialog for users who don't know the language   |
| `captions`     | Includes dialog + sound effects (for deaf/hard-of-hearing users) |
| `descriptions` | Text description of visual content for screen readers            |
| `chapters`     | Allows chapter navigation in the video                           |
| `metadata`     | Custom data used by scripts, not visible to users                |

### Sample `.vtt` File

```vtt
WEBVTT

00:00:01.000 --> 00:00:04.000
Welcome to this HTML tutorial.

00:00:05.000 --> 00:00:09.000
Today we'll cover media tags in detail.
```

---

## 🖼️ Picture Tag

The `<picture>` element provides **art direction** and **responsive images** — serving different images based on screen size, resolution, or format support.

### Syntax

```html
<picture>
  <!-- Modern format for supporting browsers -->
  <source srcset="image.avif" type="image/avif" />
  <source srcset="image.webp" type="image/webp" />

  <!-- Responsive breakpoints -->
  <source srcset="image-desktop.jpg" media="(min-width: 1024px)" />
  <source srcset="image-tablet.jpg"  media="(min-width: 600px)" />

  <!-- Fallback <img> is REQUIRED inside <picture> -->
  <img src="image-mobile.jpg" alt="A descriptive alt text" width="400" height="300" />
</picture>
```

### Attributes on `<source>` inside `<picture>`

| Attribute | Description                                                             |
|-----------|-------------------------------------------------------------------------|
| `srcset`  | One or more image URLs, optionally with width (`w`) or density (`x`) descriptors |
| `sizes`   | Hints to browser about display size (e.g. `(max-width: 600px) 100vw, 50vw`) |
| `media`   | CSS media query — source is used only when this condition is true       |
| `type`    | MIME type of the image (e.g. `image/webp`, `image/avif`)               |

> **Important:** The `<img>` tag inside `<picture>` is **mandatory** — it acts as a universal fallback and holds the `alt`, `width`, and `height`.

---

## 📌 Figure & Figcaption Tags

`<figure>` wraps self-contained media content, and `<figcaption>` provides a caption for it.

### Syntax

```html
<figure>
  <video src="demo.mp4" controls width="600"></video>
  <figcaption>Demo: Building a scroll animation with GSAP</figcaption>
</figure>

<figure>
  <img src="portfolio.jpg" alt="Portfolio screenshot" width="800" height="500" />
  <figcaption>Fig 1. — KULT Streetwear Drop Page</figcaption>
</figure>
```

### When to Use

- Wrapping code blocks with captions
- Wrapping images, videos, or diagrams with descriptions
- Any media that has a caption that relates directly to it

---

## 🗂️ Img Tag (Extended)

The `<img>` tag embeds images. It's a void element (self-closing) with powerful attributes for performance and accessibility.

### Full Example

```html
<img
  src="hero.jpg"
  alt="A hero banner for the landing page"
  width="1200"
  height="600"
  loading="lazy"
  decoding="async"
  fetchpriority="high"
  srcset="hero-400.jpg 400w, hero-800.jpg 800w, hero-1200.jpg 1200w"
  sizes="(max-width: 600px) 100vw, (max-width: 1024px) 80vw, 1200px"
/>
```

### Key Attributes

| Attribute       | Description                                                                  |
|-----------------|------------------------------------------------------------------------------|
| `src`           | Path to the image                                                            |
| `alt`           | Alternate text for accessibility & SEO (always include this!)                |
| `width`         | Intrinsic width in pixels — prevents layout shift                            |
| `height`        | Intrinsic height in pixels — prevents layout shift                           |
| `loading`       | `lazy` (defer off-screen) / `eager` (load immediately)                      |
| `decoding`      | `async` / `sync` / `auto` — controls decoding performance                   |
| `fetchpriority` | `high` / `low` / `auto` — hints render priority (great for LCP images)      |
| `srcset`        | Comma-separated list of image sources with size/density descriptors         |
| `sizes`         | Describes image display size at various breakpoints                          |
| `crossorigin`   | Enables CORS for canvas use or external sources                              |
| `referrerpolicy`| Controls referrer header sent with image request                             |
| `ismap`         | Makes the image a server-side image map (rare usage)                        |
| `usemap`        | Links image to a `<map>` element for client-side image maps                  |

---

## ⚡ Media Events Reference

These JavaScript events fire on `<video>` and `<audio>` elements:

| Event              | Fires When...                                                     |
|--------------------|-------------------------------------------------------------------|
| `play`             | Playback begins (or resumes)                                      |
| `pause`            | Playback is paused                                                |
| `ended`            | Playback has finished                                             |
| `timeupdate`       | The `currentTime` property has changed (fires ~4x/sec)           |
| `volumechange`     | Volume or muted state changes                                     |
| `seeking`          | User starts seeking to a new position                             |
| `seeked`           | Seeking has completed                                             |
| `loadstart`        | Browser starts loading the media                                  |
| `loadedmetadata`   | Duration and dimensions are available                             |
| `loadeddata`       | First frame/audio chunk has loaded                                |
| `canplay`          | Browser can start playing (may still buffer)                      |
| `canplaythrough`   | Browser can play all the way without buffering                    |
| `waiting`          | Playback stalled waiting for data                                 |
| `stalled`          | Browser tried to fetch data but couldn't                          |
| `error`            | An error occurred loading the media                               |
| `progress`         | Browser is downloading media                                      |
| `ratechange`       | Playback speed changed                                            |
| `durationchange`   | Duration has changed                                              |

---

## 🧠 JavaScript Media API

Key properties and methods available on `<video>` and `<audio>` DOM elements:

```js
const video = document.querySelector('video');

// --- Properties ---
video.currentTime       // Current playback position in seconds (read/write)
video.duration          // Total duration in seconds (read-only)
video.paused            // true if paused
video.ended             // true if playback has finished
video.muted             // true/false (read/write)
video.volume            // 0.0 to 1.0 (read/write)
video.playbackRate      // 1.0 = normal, 2.0 = 2x speed (read/write)
video.readyState        // 0–4 indicating how much is loaded
video.buffered          // TimeRanges of buffered content
video.loop              // true/false (read/write)
video.src               // Current source URL (read/write)
video.videoWidth        // Intrinsic width of video
video.videoHeight       // Intrinsic height of video

// --- Methods ---
video.play()            // Returns a Promise — plays the video
video.pause()           // Pauses playback
video.load()            // Reloads/resets the media element
video.canPlayType('video/mp4')  // Returns '', 'maybe', or 'probably'
video.requestFullscreen()       // Enters fullscreen (on the element)
video.requestPictureInPicture() // Enters PiP mode

// --- Event Listeners ---
video.addEventListener('timeupdate', () => {
  console.log('Current time:', video.currentTime);
});

video.addEventListener('ended', () => {
  console.log('Video finished!');
});
```

### Custom Video Player Example

```html
<video id="myVideo" src="video.mp4" width="800"></video>
<button id="playBtn">Play</button>
<input type="range" id="seekBar" value="0" />

<script>
  const video = document.getElementById('myVideo');
  const playBtn = document.getElementById('playBtn');
  const seekBar = document.getElementById('seekBar');

  playBtn.addEventListener('click', () => {
    if (video.paused) {
      video.play();
      playBtn.textContent = 'Pause';
    } else {
      video.pause();
      playBtn.textContent = 'Play';
    }
  });

  video.addEventListener('timeupdate', () => {
    seekBar.value = (video.currentTime / video.duration) * 100;
  });

  seekBar.addEventListener('input', () => {
    video.currentTime = (seekBar.value / 100) * video.duration;
  });
</script>
```

---

## ✅ Best Practices

### Performance
- Always specify `width` and `height` on `<img>` and `<video>` to prevent **Cumulative Layout Shift (CLS)**
- Use `loading="lazy"` on off-screen images
- Use `preload="metadata"` for videos (not `auto`) to avoid unnecessary bandwidth
- Serve modern formats: **WebP/AVIF** for images, **WebM/H.265** for video
- Use `fetchpriority="high"` on your LCP (Largest Contentful Paint) image

### Accessibility
- Always add `alt` text on `<img>` — empty `alt=""` for decorative images
- Add `<track kind="captions">` to all videos with dialogue
- Don't rely on `autoplay` without user interaction — it's blocked by most browsers
- Use `<figure>` + `<figcaption>` to associate captions semantically

### Cross-browser
- Provide multiple `<source>` formats for video/audio (WebM + MP4)
- Use `<picture>` for modern image formats with a JPEG/PNG fallback
- Test `muted` + `autoplay` combo — both attributes are required for autoplay to work in Chrome

### SEO
- Use descriptive `alt` attributes (not empty unless purely decorative)
- Add structured data for videos using `schema.org/VideoObject`
- Host video on a CDN for fast global delivery

---

## 📚 Quick Reference Summary

| Tag            | Purpose                                               |
|----------------|-------------------------------------------------------|
| `<video>`      | Embed video files with playback controls              |
| `<audio>`      | Embed audio files with playback controls              |
| `<source>`     | Define multiple media sources inside video/audio/picture |
| `<track>`      | Add subtitles, captions, chapters to video/audio      |
| `<picture>`    | Serve responsive/art-directed images                  |
| `<img>`        | Embed images (also used as fallback inside `<picture>`) |
| `<figure>`     | Wrap self-contained media as a semantic unit          |
| `<figcaption>` | Caption/description for a `<figure>` element          |

---