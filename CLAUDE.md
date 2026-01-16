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

## Phaser Version

The project loads Phaser 3.11.0 from CDN, though package.json references ^3.90.0 (not currently used since Phaser is loaded via script tag).
