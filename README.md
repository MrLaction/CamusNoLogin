# CamusNoLogin

A web app for viewing TikTok and Instagram videos without needing an account. Built as a protest against mandatory logins.

## Why This Exists

Social media platforms force you to create accounts just to view content your friends share. This tool extracts and displays videos directly in your browser using a shared database that everyone can access.

## Features

- View TikTok and Instagram videos without accounts
- Shared real-time database across all users
- Direct video playback when possible
- Download button for extracted videos
- No tracking or data collection
- Works on mobile and desktop

## How It Works

1. User pastes a video link
2. App extracts the direct video URL using public APIs
3. Video is stored in Firebase and appears for all users instantly
4. Videos play in a clean HTML5 player without platform UI

For Instagram videos that cannot be extracted, the app falls back to Instagram's official embed.

## Tech Stack

- Pure HTML/CSS/JavaScript (no frameworks)
- Firebase Realtime Database
- TikWM API for TikTok
- Multiple APIs for Instagram extraction

## Deployment

**Requirements:**
- GitHub Pages for hosting
- Firebase project for database

**Setup:**
1. Create Firebase Realtime Database
2. Update Firebase config in HTML
3. Set database rules to public read/write
4. Deploy to GitHub Pages

**Firebase Rules:**
```json
{
  "rules": {
    "videos": {
      ".read": true,
      ".write": true,
      "$videoId": {
        ".validate": "newData.hasChildren(['url', 'addedAt']) && newData.child('url').isString()"
      }
    }
  }
}
```

## Limitations

- Instagram private accounts cannot be accessed
- Some videos may only work via embed
- API availability affects success rate
- No authentication (public access)

## Privacy

No tracking or analytics. Firebase API keys are public by design (security comes from database rules, not hidden keys). All users share the same video collection.

## License

MIT License - Use freely, modify as needed, share widely.
