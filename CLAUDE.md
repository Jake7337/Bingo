# Bingo Caller App

## Project Info
- **Live URL:** https://jake7337.github.io/Bingo/
- **GitHub:** https://github.com/Jake7337/Bingo
- **Creator:** Jake - creates all art/videos/ideas with AI tools

## Current State
- Single HTML file (`index.html`) with embedded CSS/JS
- Uses GIF files for media rotator (1.gif - 6.gif, welcomelogo.gif)
- Built for Bellwood FOE 1859 Aerie (Fraternal Order of Eagles)
- Designed for TV display at club

## Features
- 75-ball bingo board (horizontal B/I/N/G/O rows)
- Random number calling with text-to-speech
- Pattern selector (full card, X, T, L, corners, custom, etc.)
- Media rotator in header for club promotions
- Winner mode with confetti
- Pace delay control
- Row dimming (click letter to dim/enable)
- Fullscreen mode
- Last 5 calls display

## Ideas to Add
- [ ] Intermission button - fullscreen overlay with video playback
- [ ] Convert GIFs to MP4 (smaller files, better quality)
- [ ] Multiple intermission videos to choose from

## Media Manager
- **Secret access**: Type "7337" on the start screen (not in the name field) to open
- **File**: `media-manager.html` — standalone page with dark theme
- **Manifest**: `media-manifest.json` — inventory of all media files with roles
- **Roles**: `rotator`, `winner`, `welcome`, `intermission`
- **Drop folder**: `C:\Users\jrsrl\OneDrive\Desktop\media-drop` — Jake puts new files here
- Jake uses the manager to browse/preview files, mark deletions, and stage additions
- The action queue generates instructions for Claude Code to process

### Claude Code Media Workflow
When Jake asks to process media changes:
1. Run ffmpeg commands as needed (convert, resize, etc.)
2. Use `git rm` for deletions, `git add` for additions
3. **Always regenerate `media-manifest.json`** as the final step — scan for all MP4 files and assign roles based on filename conventions:
   - `winner*.mp4` → role: `winner`
   - `welcomelogo.mp4` → role: `welcome`
   - `intermission*.mp4` → role: `intermission`
   - Everything else → role: `rotator`
4. Also update any references in `index.html` if filenames changed (rotator array, winner array, etc.)

## Notes
- GIFs were used because video autoplay had permission issues on different PCs
- Now hosted online, videos should work fine (user clicks "Start" which unlocks autoplay)
- Jake likes to share code openly to help others
