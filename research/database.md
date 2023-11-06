# SQLite Database

## NOW 👈👈👈👈

1. Define a basic schema
2. Figure out how to handle all the OBS stuff
   - ❓ How will I handle the json objects from the GUI

## NOWish

---

## Schema

### access_levels

| access_level_id | level_name  |
| --------------- | ----------- |
| 1               | banned      |
| 2               | viewer      |
| 3               | sub         |
| 4               | vip         |
| 5               | mod         |
| 6               | broadcaster |

### users

| user_id | username | access_level_id FK | follow_date | last_seen  | streams_watched | favorite_dollarydoo FK | favourite_reward FK |
| ------- | -------- | ------------------ | ----------- | ---------- | --------------- | ---------------------- | ------------------- |
| 1       | bob      | 2                  | 2023-01-01  | 2023-01-01 | 1               | 1                      | 2                   |
| 2       | sarah    | 2                  | 2023-01-02  | 2023-03-01 | 231             |                        | 6                   |
| 3       | helena   | 4                  | 2023-01-03  | 2023-04-01 | 2034            | 13                     | 3                   |

### user_dollarydoos

| user_dollarydoo_id | user_id FK | dollarydoo_id FK | usage_count |
| ------------------ | ---------- | ---------------- | ----------- |
| 1                  | 23         | 1                | 3           |
| 2                  | 523        | 1                | 43          |
| 3                  | 754        | 3                | 1           |

### dollarydoos

| dollarydoo_id | dollaryamount | dollaryname    | dollarydesc                                                  |
| ------------- | ------------- | -------------- | ------------------------------------------------------------ |
| 1             | 42            | Mindblown      | Someone's mind is blown.                                     |
| 2             | 101           | Change Channel | Surely there's something better to watch right now ...       |
| 3             | 666           | Jumpscare      | Triggers a loud jumpscare after an undefined length of time. |

### user_channel_rewards

| user_channel_rewards_id | user_id FK | reward_id FK | usage_count |
| ----------------------- | ---------- | ------------ | ----------- |
| 1                       | 1          | 2            | 32          |
| 2                       | 1          | 1            | 4           |
| 3                       | 3          | 1            | 1           |

### channel_rewards

| reward_id | twitch_reward_id       | usage_count |
| --------- | ---------------------- | ----------- |
| 1         | jhasdfjkhasd9f8asd9f08 | 1           |
| 2         | kjh43lkj5h234k5h2l34k5 | 32          |
| 3         | asdhflkdjshf34875qy84s | 4           |

### scenes

| scene_id | scene_name |
| -------- | ---------- |
| 1        | STREAM     |
| 2        | AFK        |
| 3        | end stream |

### scene_items

| item_id | scene_id | obs_scene_item_id | item_name  | is_enabled | duration |
| ------- | -------- | ----------------- | ---------- | ---------- | -------- |
| 1       | 1        | 32                | test       | 1          |          |
| 2       | 1        | 20                | test2      | 0          |          |
| 3       | 2        | 32                | end_stream | 1          |          |
| 4       | 1        | 65                | soccer     | 0          | 30       |

### transform_properties

| transform_id | item_id | position_x | position_y | rotation | scale_x | scale_y | crop_bottom | crop_left | crop_right | crop_top |
| ------------ | ------- | ---------- | ---------- | -------- | ------- | ------- | ----------- | --------- | ---------- | -------- |
| 1            | 3       | 200        | 300        | 0.0      | 1.0     | 1.0     | 0           | 0         | 0          | 0        |
| 2            | 4       | 100        | 200        | 0.0      | 1.0     | 1.0     | 0           | 0         | 0          | 0        |
| 3            | 6       | 150        | 250        | 0.0      | 1.5     | 1.5     | 0           | 0         | 0          | 0        |

### special_inputs

| input_id | input_name |
| -------- | ---------- |
| 1        | 1mic       |
| 2        | 2stream    |
| 3        | 3music     |

### input_settings

| setting_id | input_id FK | is_muted | volume_db |
| ---------- | ----------- | -------- | --------- |
| 1          | 1           | 0        | 30        |
| 2          | 2           | 0        | 60        |
| 3          | 3           | 1        | 72        |

### input_filters

| filter_id | input_id FK | filter_name | is_enabled |
| --------- | ----------- | ----------- | ---------- |
| 1         | 1           | compressor  | 1          |
| 2         | 2           | noise gate  | 1          |
| 3         | 3           | chipmunk    | 0          |

### commands

| command_id | command_name | access_level_id FK | user_id FK |
| ---------- | ------------ | ------------------ | ---------- |
| 1          | !boo         | 2                  |            |
| 2          | !shh         | 2                  |            |
| 3          | !points      | 2                  |            |
| 4          | !pinky       |                    | 3          |

### commands_actions

| command_id | action_id |
| ---------- | --------- |
| 1          | 1         |
| 2          | 2         |
| 3          | 4         |

### actions

| action_id | obs_method_name                 | chat_response                      |
| --------- | ------------------------------- | ---------------------------------- |
| 1         | toggle_scene_item_enabled       | Screamer inc!                      |
| 2         | list_special_input_setting_mute |                                    |
| 3         |                                 | hi, {user}.                        |
| 4         |                                 | @{user}, you have {points} points. |
