# Chat App

A real-time, room-based chat application built with Node.js, Express, and Socket.IO.

## What it does
- Serves a lightweight web UI for joining named chat rooms.
- Broadcasts real-time messages and user join/leave events per room.
- Shares a user's current location as a Google Maps link.

## Key features
- Realtime messaging
  - Socket.IO events for join, message, location, and disconnect flows.
  - Room-scoped broadcasts so messages stay within a room.
- User experience
  - In-room user list rendered in the sidebar.
  - Auto-scroll behavior to keep the latest messages in view.
- Safety and validation
  - Profanity filtering on messages via `bad-words`.
  - Duplicate usernames prevented per room.

## Tech stack
- Backend: Node.js, Express, Socket.IO
- Client: HTML, CSS, vanilla JS, Mustache.js, Moment.js
- Utilities: `bad-words`, `qs`

## Architecture overview
The server serves static files from `public/` and attaches a Socket.IO server to an HTTP server. Room membership and users are kept in memory for the life of the process.

```
Browser (public/)
  |  Socket.IO client
  v
HTTP + Socket.IO server (src/index.js)
  |-- serves static assets
  |-- manages rooms + users (src/utils/users.js)
  `-- formats messages (src/utils/messages.js)
```

## Getting started (local)

### Prerequisites
- Node.js and npm installed

### Install
```bash
npm install
```

### Environment variables
- `PORT` (optional): port for the HTTP server (defaults to 3000)

### Run
```bash
npm start
```

For auto-reload during development:
```bash
npm run dev
```
Note: the `dev` script uses `nodemon`, which must be available in your environment.

## Usage
1) Start the server and open `http://localhost:3000` in a browser.  
2) Enter a display name and room, then join.  
3) Open a second browser window, join the same room, and exchange messages.  
4) Click "Send Location" to share your current location (browser permission required).  

## Testing / Quality
No automated tests or lint/format/typecheck scripts are defined in this repository.

## Deployment
No deployment configuration is included; this project is intended to run locally.
