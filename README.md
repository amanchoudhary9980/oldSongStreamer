# Vibe Radio

An illustrated, scene-based radio for Kishore Kumar–era and 90s Bollywood songs. Pick a scene and you get a full-screen retro-modern Indian illustration under frosted-glass panels, with a Spotify playlist that fits its mood.

Live: https://aman-vibe-radio.netlify.app

## Stack

- [Astro](https://astro.build/): static site generation, one route per scene, View Transitions between scenes
- Spotify playlist embeds for playback
- No backend, no database: scenes and stations live in two JSON files

## Getting started

```bash
npm install
npm run dev
```

Runs at `localhost:4321`. The root redirects to the first scene. Use ← and → to flip between scenes.

## Project structure

```
src/
  data/scenes.json       # scene definitions: title, subtitle, caption, art, focus point, tint, station, credit
  data/station.json      # Spotify playlists the scenes can play
  components/
    SceneStage.astro     # background art + loop, top bar, scene card, live clock + listener counter
    Player.astro         # Spotify player; scenes on the same station keep playing across switches
    SceneSwitcher.astro  # scene chips + arrow-key navigation
  pages/
    [scene].astro        # dynamic route, one page per scene
    index.astro          # redirects to the first scene
  styles/global.css      # glass panels, layout, motion
public/
  media/                 # scene artwork (WebP)
```

## Adding a new scene

1. Drop the artwork into `public/media/`
2. Add an entry to `src/data/scenes.json` with a unique `slug`, `title`, `subtitle`, `caption`, `bg` path, `tint`, a `station` id from `station.json`, and a `credit`
3. It's live at `/your-slug`, no other code changes needed

## Credits

- ट्रक वाला artwork: Aman Choudhary
- बरसात, बम्बई की सड़क and बाज़ार illustrations: [Freepik](https://www.freepik.com) (free license, attribution on each scene)
