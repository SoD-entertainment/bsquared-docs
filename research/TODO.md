# TODO

1. PHASE 1: Figure out the basics
2. PHASE 2: Determine what functionality is required
3. PHASE 3: Design the GUI
4. PHASE 4: Code and Error Handling
5. PHASE 5: Testing
6. PHASE 6: Documentation

---

## Progress ✅

| Ph  | Task           | Status  | Notes                                                  |
| --- | -------------- | ------- | ------------------------------------------------------ |
| 1   | Twitch         | Init    | !hello works.                                          |
| 1   |                |         | Need to modularise commands & OBS/db/SE integration    |
| 1   | DB             | Init    | sqlite3 works fine for 'small streamer' purposes.      |
| 1   |                | 👨‍💻      | Schema                                                 |
| 1   |                | 👨‍💻      | Populating OBS tables                                  |
| 1   | Connect to OBS | Init    | Numerous source manipulations work.                    |
| 1   |                |         | Move sources, slide sources, slide multiple sources.   |
| 1   |                |         | See [doc](obs.md) for required requests.               |
| 1   | Connect to SE  | Init    | Tips event list works.                                 |
| 1   |                |         | Need to id other required endpoints.                   |
| 1   | PyQt           | Init    | New to this, so will need to allocate more time        |
| 1   | OpenAI         | 🔴Nixed | Hit instant rate limit with free account.              |
| 1   | GPT4All        | 🟢v1.0  | !bot {message} - restricted to subs due to load on PC. |
| 1   | Discord        | Init    | $hello works.                                          |
| 1   | Discord        | Init    | Twitch chat relay to #twitch-chat works.               |

---

## NOW 👈👈👈👈👈👈👈👈👈👈👈👈

> MAKE SURE TO RUN MODULES AS SCRIPTS: `python -m scripts.init_db`

**database schema**

❓❓❓❓❓❓
Do we write indiv functions for each websocket request/event?
Or ... just have a "slide source from A to B then hide" 👈👈 SlideAB as db param
❓❓❓❓❓❓

- handle !commands that require obs-websocket
- logic to determine the length of time a scene item needs to be enabled

  - e.g. user triggers a dancing bear that remains on screen for x seconds
  - e.g. user triggers a sound file, which is enabled for the duration of the file itself
    - requires logic to determine how long the file is

- look into data validation to enforce schema rules and ensure data is valid before being inserted into the db

  - [Pydantic](https://docs.pydantic.dev/latest/)
  - [SQLAlchemy](https://docs.sqlalchemy.org/en/20/orm/mapped_attributes.html#simple-validators)

- look into Object-Relational Mapping (ORM) to define tables using Python classes (instead of hardcoding statements)
  - [SQLAlchemy](https://www.sqlalchemy.org/)
    - [quickstart](https://docs.sqlalchemy.org/en/20/orm/quickstart.html)
    - [tutorial](https://docs.sqlalchemy.org/en/20/tutorial/index.html)

## NOWish-ish

1. What other integrations do we need?
   - Soundcloud
   - Spotify
   - Social media (e.g. posting when stream is live)
   - Game integration (e.g. chat interactions influence the game in real time)
   - polls (i.e. prompt, collate, report voting results)
   - analytics (e.g. no. of viewers)
   - ML for moderation
   - newsletter integration? RSS feed of headlines worth talking about while streaming?
2. Basic bot requirements
   - customise the GUI to show only what you want to see
3. All integration requirements
   - **Twitch**
     - Create !command from GUI
       - ❓ how to handle OBS integration
         - scrape OBS for scenes and sources and 'click' the ones required
         - additional options to show/hide/mute/scale/move source etc
     - View db in GUI
     - Moderate chat from GUI
     - View chat in GUI
     - Display chat in OBS overlay
       - customise via GUI?
4. Modularise functions
5. Connect individual components (i.e. twitch to obs)
6. GUI design
   - Twitch section:
     - tabs to switch between control modules: user list, event list, start poll button, (de)activate AFK button

## NOWish-ish

- [venv](https://docs.python.org/3/library/venv.html)

---

## PHASE TRACKER

### PHASE 1: Figure out the basics

1. Connect to twitch
   - cheers
     - domt: remove pulled card from user's personal deck
       - offers bad luck protection
       - tracks' get out jail free' cards (Fates)
         - alert user if they have a FATES card available
     - change channel: mute music input in OBS
2. Connect to db
3. Connect to OBS
   - mute audio inputs
4. Connect to StreamElements
5. GUI
6. Connect to OpenAI
   - free tier limited to 3 requests
     - 🛑 getting RateLimitError on very first request with new API key

### PHASE 2: Determine what functionality is required

- Basic bot functions
- Integration functions
  - DOMT hooks into DB to store Fate card etc
- Accessibility
  - Visual gags/scares as text
  - OBS overlay stuff as text?
  - ❓ Are OBS closed captions accessible by screen readers
    - Maybe bot can manipulate CC to add descriptions for audio
- Twitch functions
  - OBS hook
  - DB hook
  - Maybe SE hook to announce tip in chat????
  - Clips
    - [Twitch API - Clips](https://dev.twitch.tv/docs/api/clips/)
    - Create, delete, list clips from current broadcast
    - POST to YouTube
  - Analytics
    - [Twitch API - Insights & Analytics](https://dev.twitch.tv/docs/insights/#game-developer-analytics)
- OBS functions
  - Twitch hook
  - StreamElements hook
  - Db hook (!duel?)
  - Twitch alert popups
    - handle dollarydoos separately
    - display regular alert for all other amounts
  - StreamElements alert popups
    - display alert for donos
- DB functions
  - Twitch hook
  - StreamElements hook
    - Do something with the CSV file? wget
  - OBS hook
- Discord integration
  - Channel messages and DMs get posted to a 'discord chat' window
  - Live transcription of stream to channel for non-twitch people to use?
    - python library to live transcribe?
- YouTube integration (NOT streaming)
  - Upload clips

### PHASE 3: Design the GUI

### PHASE 4: Code and Error Handling

### PHASE 5: Testing

### PHASE 6: Documentation
