# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Phaser 3 game project. The main game is a space invader-style game where a spaceship moves horizontally and drops bombs to destroy stacked stars.

## Running the Game

```bash
npm install
npm run dev
```

Opens a static server at http://localhost:3000. No build step is required.

## Project Structure

- `index.html` - Main game with custom space invader-style gameplay
- `phaser3-tutorial-src/` - Reference files from the official Phaser 3 "Making your first game" tutorial (parts 1-10)
- `assets/` - Game sprites (sky, platform, star, bomb, dude character)

## Architecture

The game uses Phaser 3's Arcade Physics system with a single-scene architecture:

- **preload()** - Loads images and spritesheets
- **create()** - Sets up game objects, physics groups, collision handlers, and input
- **update()** - Game loop handling player movement and input

Key game objects use `this.physics.add.group()` and `this.physics.add.sprite()` for physics-enabled entities. Collisions are handled via `this.physics.add.collider()`.

## Game Scenes

The game uses a multi-scene architecture with two scenes:

- **TitleScene** - Menu screen with difficulty selection (easy/medium/hard) and high score display per difficulty
- **GameScene** - Main gameplay with spaceship movement, bomb dropping, and star destruction

Scene transitions use `this.scene.start('SceneName')`.

## Key Game Systems

**Difficulty System**: Three difficulty levels with different ship speeds and speed increments, configured in `difficultySettings` object.

**High Score System**: Per-difficulty high scores stored in localStorage under key `starBomberHighScores`.

**Audio System**: Web Audio API-based sound effects (no external audio files). Functions include:
- `playStarSound()`, `playMissSound()`, `playExplosionSound()`, `playFanfare()`, `playSelectSound()`
- `startFuelSound()`/`stopFuelSound()` for looping engine sound
- `startOrganMusic()`/`stopOrganMusic()` for background music with tempo that adjusts to ship speed

**Particle System**: Star explosion particles created via `this.add.particles()` with dynamically generated textures.

## Phaser Version

The project loads Phaser 3.11.0 from CDN, though package.json references ^3.90.0 (not currently used since Phaser is loaded via script tag).
