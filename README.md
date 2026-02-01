# DevSocial

DevSocial is a lightweight MERN social network for developers. Create a profile, showcase experience, link GitHub repos, and share posts with comments and likes.

**Live demo:** https://devsocial.herokuapp.com/ (wait 30s to boot up. If offline, run locally—see below).

## Features
- Email/password signup/login with JWT.
- Editable developer profile (bio, location, skills, experience, education, social links).
- GitHub integration to display public repos on your profile.
- Community feed with posts, comments, likes/unlikes, and post deletion by owner.
- Directory of all developers with quick profile cards.

## Tech stack
- **Frontend:** React 17, Redux + Thunk, React Router, CRA build.
- **Backend:** Node.js, Express, JWT auth middleware, validation with `express-validator`.
- **Database:** MongoDB via Mongoose.
- **Dev tooling:** Concurrent dev runner (`npm run dev`), Nodemon, Heroku build hooks.

## Environment
Create a `.env` in the project root with:
```
MONGO_URI=mongodb+srv://...
JWT_SECRET=super-secret-key
GITHUB_TOKEN=ghp_xxx              # optional, for higher-rate GitHub API calls
PORT=8000                         # optional
NODE_ENV=development
```

## Getting started
1. Install dependencies (root + client):
   ```bash
   npm install
   ```
2. Run in development (API + React client):
   ```bash
   npm run dev
   ```
   - API on http://localhost:8000  
   - Client on http://localhost:3000 (proxied to the API)
3. Production build:
   ```bash
   npm run start           # serves the API
   # build client assets
   cd client && npm run build
   ```
   The Heroku deploy hook (`heroku-postbuild`) installs and builds the client automatically.

## Project layout
```
server/           # API routes, models, middleware
client/           # React app
config/db.js      # Mongo connection helper
server.js         # Express entry point
```

## Notes
- GitHub repo cards use an optional token to avoid low rate limits; omit it if you don't need repo previews.
- No images are bundled; run locally or hit the live demo to view the UI.
