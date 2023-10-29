# TODO

## Progress ✅

| PHASE | Task                      | Status       | Notes                                                                        |
| ----- | ------------------------- | ------------ | ---------------------------------------------------------------------------- |
| 1     | Twitch                    | Init ✔       | !hello works. Need to modularise commands & OBS/db/SE integration            |
| 1     | DB                        | Init ✔       | sqlite3 works fine for 'small streamer' purposes.                            |
| 1     | Connect to OBS            | Init ✔       | Numerous source manipulations work. See [doc](obs.md) for required requests. |
| 1     | Connect to StreamElements | Init ✔       | Tips event list works. Need to id other required endpoints.                  |
| 1     | PyQt                      | Init ✔       | New to this, so will need to allocate more time                              |
| 1     | OpenAI                    | Postponed 🕔 | Hit instant rate limit with free account. Need to investigate further.       |
| 1     | Discord                   | Init ✔       | $hello works. Twitch chat relay to #twitch-chat works.                       |

## NOW 👈👈👈👈👈👈👈👈👈👈👈👈

1. [venv](https://docs.python.org/3/library/venv.html)
2. Discord integration
3. YouTube integration

## PHASE 2: Determine what functionality is required 👈👈👈👈

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
    - Create, delete, list clips from current broadcast
    - POST to YouTube
- OBS functions
  - Twitch hook
  - StreamElements hook
  - Db hook (!duel?)
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

## PHASE 3: Design the GUI

## PHASE 4: Code and Error Handling

## PHASE 5: Testing

## PHASE 6: Documentation

---

## PHASE 1: Figure out the basics

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
     - getting RateLimitError on very first request with new API key
