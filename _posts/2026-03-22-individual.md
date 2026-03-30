---
layout: post
title: CS111 Blog — Chetan Tiduwar
description: A complete CS111 walkthrough of my final project — a 3-level gauntlet game built with HTML5 Canvas.
author: Chetan Tiduwar
date: 2026-03-23
permalink: /cs111-blog/
---

<style>
@import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Exo+2:wght@400;600;700;900&display=swap');

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

body, .page-content {
  background: #060a0f;
  color: #d0e8ff;
  font-family: 'Exo 2', sans-serif;
}

.blog-wrap {
  max-width: 860px;
  margin: 0 auto;
  padding: 60px 24px 100px;
}

.meta {
  text-align: center;
  color: #4a6a8a;
  font-family: 'Share Tech Mono', monospace;
  font-size: 13px;
  margin-bottom: 10px;
}

.title {
  text-align: center;
  font-size: 38px;
  font-weight: 900;
  color: #e0f2ff;
  margin-bottom: 14px;
}

.subtitle {
  text-align: center;
  color: #6a8fa8;
  margin-bottom: 40px;
}

iframe {
  display: block;
  margin: 0 auto;
  border: 2px solid #1d4ed8;
  border-radius: 10px;
  width: 100%;
  max-width: 800px;
  height: 600px;
}

h2 {
  margin-top: 40px;
  margin-bottom: 10px;
  font-family: 'Share Tech Mono', monospace;
  color: #38bdf8;
}

p {
  margin-bottom: 14px;
  color: #8aaccc;
}
</style>

<div class="blog-wrap">

<div class="meta">Mar 23, 2026 · Chetan Tiduwar · Sprint 6 Final Project</div>

<h1 class="title">CS111 Blog</h1>

<p class="subtitle">
A complete CS111 walkthrough — a 3-level gauntlet game.
</p>

<h2>🎮 Play The Gate Game</h2>

<p>You can play the game right below:</p>

<iframe 
  src="https://phantom-deploy.github.io/portfolio/gamify/gategame"
  allowfullscreen>
</iframe>

<h2>🎮 Game Overview</h2>

<p>
This is a 3-level game where each level has a different challenge. You use WASD or arrow keys to move and try to reach the exit.
</p>

<ul>
  <li><strong>Level 1:</strong> Dodge cannon bullets</li>
  <li><strong>Level 2:</strong> Maze navigation</li>
  <li><strong>Level 3:</strong> Stay in safe zone</li>
</ul>

<h2>📐 OOP (Classes)</h2>

<p>
I used classes like Level1, Level2, and Level3 to organize the game. Each level has its own logic and methods.
</p>

<h2>⚙️ Methods</h2>

<p>
The game uses methods like spawnBullet(), resetPlayer(), and update() to control behavior.
</p>

<h2>🗂️ Data Types</h2>

<p>
The game uses numbers, strings, booleans, arrays, and objects to store game data.
</p>

<h2>🔁 Control Structures</h2>

<p>
Loops and if statements control movement, collisions, and game logic.
</p>

<h2>⌨️ Input / Output</h2>

<p>
Keyboard input moves the player and the canvas shows the output visually.
</p>

<h2>🐛 Debugging</h2>

<p>
I used console logs and Chrome DevTools to debug issues.
</p>

<div style="text-align:center; margin-top: 40px; color:#4a6a8a;">
CS111 Final Project · Chetan Tiduwar
</div>

</div>