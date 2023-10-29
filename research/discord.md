# Discord Integration

## TODO

- Handle events
  - twitchio requires public facing IP and domain
    - Use local tunnelling?
      - [ngrok](https://ngrok.com/)
      - provides public HTTPS URL to use with EventSub subscription
- Custom rewards/channel point redemptions
  - Relay redemption ✔ (relays reward id - how to get reward name?)

## Requirements

1. Connect to server specific by the user
2. Join channel specific by the user
3. Post to that channel
4. Relay Twitch chat to #twitch-chat

## Technology

- [discord.py (readthedocs)](https://discordpy.readthedocs.io/en/stable/) or [discord.py (github)](https://github.com/Rapptz/discord.py)

## References

- [discord.py - intents](https://discordpy.readthedocs.io/en/stable/intents.html)
- [discord.py - Quickstart](https://discordpy.readthedocs.io/en/stable/quickstart.html)
- [discord.com - Dev Portal](https://discord.com/developers/applications)
