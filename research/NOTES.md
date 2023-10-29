# Stuff 'n Things

## QUESTIONS ❓

> "Twitch requires EventSub targets to have TLS/SSL enabled (https). TwitchIO does not support this, as such you should use a reverse proxy such as nginx to handle TLS/SSL."

### OpenAI

- Made a new API key on free tier - openai.error.RateLimitError on first request
  ❓ Possible to have FREE chatbot ai?????

---

## OBS integration

- obs-websocket-py

---

## Twitch integration

- had probs getting threading to work with twichio and tkinter
  - maybe try PyQt?

### Alternatives

1. [twitch-python](https://pypi.org/project/twitch-python)
2. [Python Twitch API](https://pypi.org/project/twitchAPI)
3. [PyWitch](https://pypi.org/project/pywitch)

---

## StreamElements integration

- [SE API ref](https://dev.streamelements.com/docs/api-docs/bcd899e16ac9a-se-api-docs)
- [SE API ref: GET tips](https://dev.streamelements.com/docs/api-docs/704e5580be2d9-channel)

### Maybe?

Snippets from [StreamElements-Local-Cloudbot](https://github.com/Yazaar/StreamElements-Local-Cloudbot/wiki/Useful-StreamElements-endpoints)???

- [sticky beak](https://github.com/Yazaar/StreamElements-Local-Cloudbot/blob/master/source/dependencies/modules/StreamElements.py)

Use a REST API

```python
import requests

headers = {
    'Authorization': 'Bearer your_streamelements_jwt_token',
}

response = requests.get('https://api.streamelements.com/kappa/v2/points/your_channel_id/user_name', headers=headers)

if response.status_code == 200:
    data = response.json()
    print(data)  # Handle your data here
```

---

## Database integration

- [sqlite3](https://docs.python.org/3/library/sqlite3.html)

---

## GUI (PyQt)

- https://realpython.com/python-pyqt-gui-calculator/#installing-pyqt
