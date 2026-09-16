# GBP SEO Study Tracker

A standalone six-week Google Business Profile and Local SEO study tracker.

Progress is saved automatically in the browser using `localStorage`, so checkmarks remain available after closing the page and reopening it in the same browser.

## Deploy with Vercel

Import this repository into Vercel. No build command or framework preset is required; `index.html` is the site entry point.

## Firebase setup

In Firestore Database → Rules, use the following rule so each signed-in user can access only their own progress document:

```text
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /progress/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```
