# Ola

A personal, non-commercial companion app for TIDAL, built around queue control, low-distraction listening and discovery through Last.fm.

**Ola is not made by, endorsed by or affiliated with TIDAL or Last.fm.** You need your own TIDAL subscription, and your own TIDAL and Last.fm developer credentials, to use it.


[**Live app**](https://NicoDemo-3.github.io/ola/ola.html)
[**Privacy notice**](https://NicoDemo-3.github.io/ola/privacy.html)

---

## Features

### Queue control
- **Swipe to queue:** swipe a song one way to add it to the end of the queue, the other way to play it next. Directions and sensitivity are adjustable.
- **No accidental skips:** tapping a song while something is playing asks "Play now?" first.
- **Drag to reorder** the queue, with a tap menu for play now or play next.
- **Smart shuffle:** no repeats until the whole list has played, and no same artist twice in a row.
- **DJ:** mixes your saved songs with new ones, with a new-vs-saved slider and optional gradual genre drift. It can start from any song.
- **Sleep timer** with fixed times or "end of this song".

### Two modes
- **Spring mode:** the full app, with a Home screen, Updates, Search and Collection laid out like TIDAL's own app.
- **Neap mode:** a low-distraction layout with just your library, the queue, picks and the DJ. Your library shows liked songs first, then songs from your playlists, in random order.

### Search and discovery
- Search sorted by **Relevance**, **Popularity** or **For you**. Song-title matches come before artist-name matches, and originals come before live versions and remixes.
- Popularity uses Last.fm listener counts when available, and fetches well-known matches that TIDAL's search missed.
- **Your genres first:** genre tags for your most-saved artists, from Last.fm, followed by common genres.
- **Picks from Last.fm:** daily, weekly, monthly and yearly playlists of songs by artists similar to what you've been listening to, that you haven't heard yet. Each one can be saved as a playlist.
- Full artist pages with popular tracks, albums, EPs and singles, and similar artists.

### Personalisation
- Six marine themes, each with matched light and dark versions, plus up to six custom themes.
- Light or dark by phone setting, fixed choice, a night-time schedule, or the light sensor where the device supports it.
- Drag-to-reorder Home sections and Collection tabs, a startup screen, and "remember where I left off".

### Last.fm
- Connect your account, see recent scrobbles, and optionally send scrobbles and "now playing" updates.

---

## Current limitation: 30-second previews

Ola plays music through TIDAL's official, unmodified Player module (`@tidal-music/player`). TIDAL currently limits apps registered through its developer portal to **30-second previews**, even for subscribers (`FULL_REQUIRES_HIGHER_ACCESS_TIER`). Full-length playback depends on TIDAL approving the app for Production Mode.

Because of this, **sending scrobbles to Last.fm is off by default.** Settings > Tidal account has a **Test playback** button that reports which kind of playback your app currently gets.

---

## Setup

Ola is a single HTML file with no build step and no server. These steps use only a web browser.

### 1. Host it on GitHub Pages
1. Fork this repository, or create a new public repository and upload `ola.html` and `privacy.html`.
2. Go to **Settings > Pages**, choose **Deploy from a branch**, then **main** and **/ (root)**, and save.
3. After a minute or two your copy is live at `https://github.com/NicoDemo-3/Ola/`.

### 2. Register a TIDAL app
1. Log in at [developer.tidal.com](https://developer.tidal.com) and create an app in the dashboard.
2. Open your Ola address, go to **Settings > Tidal account**, and copy the **redirect URL** shown there. Add it to your app in the TIDAL dashboard exactly as shown.
3. Enable the permissions Ola uses:

   | Permission | Used for |
   | --- | --- |
   | `user.read` | Username and country |
   | `collection.read` | Liked tracks, saved albums, followed artists |
   | `playlists.read` | Your playlists |
   | `search.read` | Search |
   | `playback` | Playback through the official player |
   | `entitlements.read` | Lets the player check your subscription |
   | `recommendations.read` | Optional, reserved for future features |

4. Copy the **client ID** into Ola (Settings > Tidal account) and tap **Sign in with Tidal**. You don't need the client secret.

### 3. Connect Last.fm (optional)
1. Create an API account at [last.fm/api/account/create](https://www.last.fm/api/account/create). You can set the callback URL to your Ola address.
2. In Ola, go to **Settings > Last.fm**, enter the **API key** and **shared secret**, and tap **Connect Last.fm**.

Keys and secrets are entered in the app and stored only on your device. They are never part of the code in this repository. **Never commit them to GitHub.**

### 4. Install on your phone
Open your Ola address in Chrome and choose **Add to Home screen** from the menu.

---

## Privacy

Ola has no server, no analytics and no ads. Everything it keeps is stored in your browser on your own device, and cached TIDAL data expires after 30 days. Settings > Reset > **Delete all my data** removes everything. See the full [privacy notice](privacy.html).

---

## Staying within the platforms' terms

- Playback only through TIDAL's official, unmodified Player module. No downloading, recording or offline storage of audio.
- Non-commercial use only, as TIDAL's developer terms require.
- TIDAL content is never used with AI services. The DJ, picks and search ranking are rule-based and use Last.fm data.
- Only temporary caching of metadata and cover art.

Anyone running their own copy is responsible for following the [TIDAL Developer Terms](https://developer.tidal.com) and [Last.fm API terms](https://www.last.fm/api/tos) with their own credentials.

---

## How it's built

- One self-contained `index.html`: plain HTML, CSS and JavaScript, no framework, no build step.
- [TIDAL API](https://developer.tidal.com) with Authorization Code + PKCE sign-in.
- [@tidal-music/player](https://github.com/tidal-music/tidal-sdk-web), loaded from jsDelivr.
- [Last.fm API](https://www.last.fm/api) for history, genre tags, picks and scrobbling.
- [Figtree](https://fonts.google.com/specimen/Figtree) font from Google Fonts.

## Roadmap

- Sync Ola's queue to a TIDAL playlist, for full-length playback in the official TIDAL app.
- TIDAL Production Mode request for full-length playback inside Ola.
- A native Android app.

## License

The code in this repository is released under the [MIT License](LICENSE). It gives no rights to TIDAL's or Last.fm's content, trademarks or APIs, which remain subject to their own terms.


