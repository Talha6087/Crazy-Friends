# Crazy Friends Battle — 3D multiplayer browser game

A shareable real-time WebSocket battle game with a Three.js 3D arena, 20 real players, 10 per team, 8-minute rounds, cartoon fighters, tomato projectiles, lobby and room invite links.

## Run locally

Install Node.js 18 or newer, then in this directory:

```bash
npm install
npm start
```

Open http://localhost:3000. To test two players locally, use two browser tabs and join the same room. The first player is host. Both teams must contain at least one player before the host can start.

## Deploy to a public website

Push this directory to a GitHub repository. On Render create a **Web Service** from that repository, choose Node, build command `npm install`, start command `npm start`, and deploy. Open your service HTTPS URL, create a room, then share the **Copy Invite Link** URL. Choose a hosting plan that stays awake for matches and supports WebSockets.

## Controls

PC: WASD/arrow keys move, Space/F or click shoot, mouse wheel or +/- zoom. Mobile: virtual joystick and FIRE button. Projectiles auto-aim in the last movement direction; if no direction has been chosen, the server aims at the closest enemy. Share and Exit buttons appear in-game.

## Architecture

`server.js`: authoritative room/team limits, game clock, movement, projectiles, hits and elimination over WebSockets (20 Hz). `public/game.js`: Three.js client using CDN import. `public/index.html`: responsive UI.

## Known limitations

This is an early prototype, not a hardened production game. The 3D engine requires internet access to load Three.js from jsDelivr. Game rooms are held in server memory and disappear on restart. There is no reconnect, persistence, anti-cheat authentication, lag compensation, or server-side obstacle collision yet. Obstacles are decorative in this build; do not assume they provide cover. Test with multiple devices before inviting 20 players. A single server instance is required unless you add shared room state. This package does not deploy itself or supply a live public URL.
