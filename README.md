# vertical-scroll-world-id345

A **vertical scroll-world**: scrolling scrubs one continuous, cut-free camera descent
down a colossal beanstalk — from low orbit, through the jet layer and a cloud-canyon
workshop, to a golden-hour valley where it roots. All narrative text is baked *into*
the world (a hanging name-sign, a biplane banner, signposts, a painted barn roof) —
zero text overlays. A tiny red-hatted gnome hides in every layer.

**Live demo:** open `index.html` over any static server (`python3 -m http.server`),
or enable GitHub Pages on this repo.

## How it was made

1. **Storyboard stills** — one designed keyframe per altitude layer, generated with
   nano-banana-pro on [fal.ai](https://fal.ai) (it renders legible in-world text),
   art-directed and approved before any video spend.
2. **Keyframe-bridged video legs** — each leg is a Seedance 2.0 image-to-video
   generation whose **start frame and end frame are consecutive storyboard stills**,
   so every seam is a designed frame and the legs generate in parallel.
   Motion prompts describe the *evidence* of descent ("features attached to the
   stalk drift steadily upward through the frame") rather than the intention.
3. **Scrub encoding** — `libx264 crf 20`, small GOP (`-g 8`), faststart, audio
   stripped; posters extracted from the encoded clips' first frames.
4. **Scroll engine** — `scrub-engine.js` from the
   [scroll-world](https://github.com/cth9191/scroll-world) Claude Code skill
   (fork of oso95/scroll-world, MIT): blob-loaded fully-seekable video, scroll →
   `currentTime` scrubbing with rAF smoothing, seam crossfades, lazy prefetch,
   reduced-motion and mobile fallbacks. Engine chrome is hidden via CSS for a
   fully cinematic frame; the only UI is an invisible mailto hotspot that fades
   in at the bottom of the descent.

Total generation cost for this build: **≈ $9** (7 stills + 4 × 6s 1080p clips).

## Credits

- Scroll engine: [cth9191/scroll-world](https://github.com/cth9191/scroll-world)
  (MIT), itself a fork of oso95/scroll-world.
- Imagery: nano-banana-pro (stills) + Seedance 2.0 (video) via fal.ai.
- Concept & art direction: Ryan Shuken. Build: Claude Code.
