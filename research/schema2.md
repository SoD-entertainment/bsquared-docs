# Figuring out the schema

1. one command can be linked to many obs_actions
2. one obs_action can be linked to many commands
3. one command can be linked to one chat_message
4. one chat_message can be linked to one command
5. one command can be linked to both one obs_action and one chat_message
6. one command can be linked to many obs_actions and one chat message
7. one command can be linked to many access_levels
8. one access_level can be linked to many commands
9. one dollarydoo can be linked to many obs_actions
10. one dollarydoo can be linked to one obs_action
11. one dollarydoo can be linked to one chat_message
12. one channel_reward can be linked to many obs_actions
13. one channel_reward can be linked to one obs_action
14. one channel_reward can be linked to one chat_message
15. one event can be linked to many obs_actions
16. one event can be linked to one obs_action
17. one event can be linked to one chat_message
18. one user can be linked to one access_level
19. one user can be linked to one user_command
20. one access_level can be linked to many users
21. one user_command can be linked to many obs_actions
22. one user_command can be linked to one obs_action
23. one user_command can be linked to one chat_message
24. one user can be linked to many stream_elements
25. one stream_element can be linked to one user
26. one scene_item can be linked to one scene
27. one scene can be linked to many scene_items
28. one special_input can be linked to one input_setting
29. one special_input can be linked to one input_filter

## users

| user_id PK | username | access_level_id FK | followed_on | last_seen  | streams_watched |
| ---------- | -------- | ------------------ | ----------- | ---------- | --------------- |
| 1          | sarah    | 2                  | 2023-01-02  | 2023-04-02 | 2               |
| 2          | helena   | 4                  | 2023-01-03  | 2023-05-02 | 21              |
| 3          | cosima   | 3                  | 2023-01-04  | 2023-06-02 | 453             |

## access_levels

| access_level_id PK | level_name  |
| ------------------ | ----------- |
| 1                  | banned      |
| 2                  | viewer      |
| 3                  | sub         |
| 4                  | vip         |
| 5                  | mod         |
| 6                  | broadcaster |

## access_commands

| access_command_id PK | access_level_id FK | command_id FK |
| -------------------- | ------------------ | ------------- |
| 1                    | 2                  | 3             |
| 2                    | 2                  | 1             |
| 3                    | 2                  | 2             |

## commands

| command_id PK | command_name |
| ------------- | ------------ |
| 1             | !rage        |
| 2             | !hi          |
| 3             | !points      |

## user_commands

| user_command_id PK | command_name | chat_message_id FK | obs_action_id FK | user_id FK |
| ------------------ | ------------ | ------------------ | ---------------- | ---------- |
| 1                  | !pinky       |                    | 1                | 3          |
| 2                  | !special     | 1                  | 1                | 3          |
| 3                  | !something   | 3                  |                  | 3          |

## chat_messages

| chat_message_id PK | message                   |
| ------------------ | ------------------------- |
| 1                  | Hi, {user}                |
| 2                  | You have {points} points. |
| 3                  | rawr                      |

## commands_actions

| command_action_id PK | command_id FK | chat_message_id FK | obs_action_id FK | params                                 |
| -------------------- | ------------- | ------------------ | ---------------- | -------------------------------------- |
| 1                    | 1             | 1                  | 1                | {sceneName: "STREAM", sceneItemId: 32} |
| 2                    | 1             |                    | 3                | "1mic"                                 |

## dollarydoos_actions

| dollarydoo_action_id PK | dollarydoo_id FK | chat_message_id FK | obs_action_id FK | params                                 |
| ----------------------- | ---------------- | ------------------ | ---------------- | -------------------------------------- |
| 1                       | 1                | 1                  |                  | {sceneName: "STREAM", sceneItemId: 32} |
| 2                       | 3                |                    | 1                | {sceneName: "STREAM", sceneItemId: 5}  |
| 3                       | 2                | 1                  | 1                | {sceneName: "STREAM", sceneItemId: 21} |

## rewards_actions

| reward_action_id PK | channel_reward_id | obs_action_id FK | params                                 |
| ------------------- | ----------------- | ---------------- | -------------------------------------- |
| 1                   | 1                 | 1                | {sceneName: "STREAM", sceneItemId: 32} |
| 2                   | 2                 | 1                | {sceneName: "STREAM", sceneItemId: 43} |

## events_actions

| event_action_id PK | event_id FK | obs_action_id FK | params                                                                                                                   |
| ------------------ | ----------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------ |
| 1                  | 1           | 4                | [{sceneName: "STREAM", sceneItemId: 32}, {sceneName: "STREAM", sceneItemId: 32}, {sceneName: "STREAM", sceneItemId: 32}] |
| 2                  | 2           | 4                | [{sceneName: "STREAM", sceneItemId: 21}, {sceneName: "STREAM", sceneItemId: 21}, {sceneName: "STREAM", sceneItemId: 21}] |

## obs_action

| obs_action_id PK | method                            |
| ---------------- | --------------------------------- |
| 1                | toggle_scene_item_enabled         |
| 2                | delayed_toggle_scene_item_enabled |
| 3                | toggle_mute                       |
| 4                | slide_multiple_items              |

## channel_rewards

| channel_reward_id PK | twitch_id            | chat_message_id FK | obs_action_id FK |
| -------------------- | -------------------- | ------------------ | ---------------- |
| 1                    | asd8f70as98d7f9asdf7 |                    |                  |
| 2                    | kj213h4lk123hlk1j234 |                    |                  |

## events

| event_id PK | event_type | chat_message_id FK | obs_action_id FK |
| ----------- | ---------- | ------------------ | ---------------- |
| 1           | sub        |                    |                  |
| 2           | resub      |                    |                  |
| 3           | raid       |                    |                  |
| 4           | host       |                    |                  |

## dollarydoos

| dollarydoo_id PK | amount | name  | description                  | chat_message_id FK | obs_action_id FK |
| ---------------- | ------ | ----- | ---------------------------- | ------------------ | ---------------- |
| 1                | 666    | one   | This is what it does.        |                    |                  |
| 2                | 101    | two   | This is what is might do.    |                    |                  |
| 3                | 42     | three | This is what is surely does. |                    |                  |

## stream_elements

| stream_elements_id | user_id FK | amount | message   |
| ------------------ | ---------- | ------ | --------- |
| 1                  | 2          | 1.00   | Hi        |
| 2                  | 2          | 2.00   | You suck  |
| 3                  | 1          | 3.00   | Get bent! |

## scenes

| scene_id PK | scene_name |
| ----------- | ---------- |
| 1           | STREAM     |
| 2           | AFK        |
| 3           | end stream |

## scene_items

| item_id PK | scene_id FK | obs_scene_item_id | item_name  | is_enabled | duration |
| ---------- | ----------- | ----------------- | ---------- | ---------- | -------- |
| 1          | 1           | 32                | test       | 1          |          |
| 2          | 1           | 20                | test2      | 0          |          |
| 3          | 2           | 32                | end_stream | 1          |          |
| 4          | 1           | 65                | soccer     | 0          | 30       |

## special_inputs

| input_id PK | input_name |
| ----------- | ---------- |
| 1           | 1mic       |
| 2           | 2stream    |
| 3           | 3music     |

## input_settings

| setting_id PK | input_id FK | is_muted | volume_db |
| ------------- | ----------- | -------- | --------- |
| 1             | 1           | 0        | 30        |
| 2             | 2           | 0        | 60        |
| 3             | 3           | 1        | 72        |

## input_filters

| filter_id PK | input_id FK | filter_name | is_enabled |
| ------------ | ----------- | ----------- | ---------- |
| 1            | 1           | compressor  | 1          |
| 2            | 2           | noise gate  | 1          |
| 3            | 3           | chipmunk    | 0          |
