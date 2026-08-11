# Vibe Radio

An illustrated, scene-based music radio experience. Pick a scene, get a full-screen poster-style visual and a curated soundtrack that autoplays alongside it.

## Stack

- [Astro](https://astro.build/) — static site generation, one route per scene
- Spotify embeds for playback
- No backend, no database — scene data lives in a single JSON file

## Getting started

```bash
npm install
npm run dev
```

Runs at `localhost:4321`. The root redirects to the default scene.

## Project structure

```
src/
  data/scenes.json       # scene definitions: title, caption, art, colors, track, listener count
  components/
    SceneStage.astro     # fullscreen background, title, live clock + listener counter
    Player.astro         # floating Spotify player
    SceneSwitcher.astro  # thumbnail rail to jump between scenes
  pages/
    [scene].astro         # dynamic route, one page per scene
    index.astro           # redirects to the default scene
public/
  media/                 # scene artwork
```

## Adding a new scene

1. Drop the artwork into `public/media/`
2. Add an entry to `src/data/scenes.json` with a unique `slug`, `title`, `caption`, `bg` path, color pair, Spotify embed URL, and starting listener count
3. It's live at `/your-slug` — no other code changes needed

## Build

```bash
npm run build
npm run preview
```

Outputs a static site to `dist/`, deployable anywhere that serves static files (Netlify, Vercel, etc).

## Roadmap

- Swap static scene backgrounds for looping video
- Premium tier: exclusive scenes, no ads
- User accounts for saved favorites
