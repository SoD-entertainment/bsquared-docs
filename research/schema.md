# Users

"""
CREATE TABLE users (
user_id INTEGER PRIMARY KEY,
username TEXT NOT NULL,
access_level_id INTEGER,
followed_on DATE,
last_seen DATE,
streams_watched INTEGER,
FOREIGN KEY (access_level_id) REFERENCES access_levels(access_level_id)
);
""",

# Access Levels

"""
CREATE TABLE access_levels (
access_level_id INTEGER PRIMARY KEY,
level_name TEXT NOT NULL
);
""",

# Access Commands ( many-to-many relationship between access_levels and commands)

"""
CREATE TABLE access_commands (
access_command_id INTEGER PRIMARY KEY,
access_level_id INTEGER,
command_id INTEGER,
FOREIGN KEY (access_level_id) REFERENCES access_levels(access_level_id),
FOREIGN KEY (command_id) REFERENCES commands(command_id)
);
""",

# Commands

"""
CREATE TABLE commands (
command_id INTEGER PRIMARY KEY,
command_name TEXT NOT NULL
);
""",

# User Commands

"""
CREATE TABLE user_commands (
user_command_id INTEGER PRIMARY KEY,
command_name TEXT NOT NULL,
user_id INTEGER,
FOREIGN KEY (user_id) REFERENCES users(user_id)
);
""",

# Chat Messages

"""
CREATE TABLE chat_messages (
chat_message_id INTEGER PRIMARY KEY,
message TEXT NOT NULL
);
""",

# OBS Actions

"""
CREATE TABLE obs_actions (
obs_action_id INTEGER PRIMARY KEY,
method TEXT NOT NULL
);
""",

# Commands Actions (many-to-many relationship between commands and obs_actions)

"""
CREATE TABLE commands_actions (
command_action_id INTEGER PRIMARY KEY,
command_id INTEGER,
obs_action_id INTEGER,
chat_message_id INTEGER,
params TEXT,
FOREIGN KEY (command_id) REFERENCES commands(command_id),
FOREIGN KEY (obs_action_id) REFERENCES obs_actions(obs_action_id),
FOREIGN KEY (chat_message_id) REFERENCES chat_messages(chat_message_id)
);
""",

# Dollarydoos

"""
CREATE TABLE dollarydoos (
dollarydoo_id INTEGER PRIMARY KEY,
amount INTEGER,
name TEXT,
description TEXT
);
""",

# Dollarydoos Actions (many-to-many relationship between dollarydoos and obs_actions)

"""
CREATE TABLE dollarydoos_actions (
dollarydoo_action_id INTEGER PRIMARY KEY,
dollarydoo_id INTEGER,
obs_action_id INTEGER,
chat_message_id INTEGER,
params TEXT,
FOREIGN KEY (dollarydoo_id) REFERENCES dollarydoos(dollarydoo_id),
FOREIGN KEY (obs_action_id) REFERENCES obs_actions(obs_action_id),
FOREIGN KEY (chat_message_id) REFERENCES chat_messages(chat_message_id)
);
""",

# Channel Rewards

"""
CREATE TABLE channel_rewards (
channel_reward_id INTEGER PRIMARY KEY,
twitch_id TEXT
);
""",

# Rewards Actions (many-to-many relationship between channel_rewards and obs_actions)

"""
CREATE TABLE rewards_actions (
reward_action_id INTEGER PRIMARY KEY,
channel_reward_id INTEGER,
obs_action_id INTEGER,
params TEXT,
FOREIGN KEY (channel_reward_id) REFERENCES channel_rewards(channel_reward_id),
FOREIGN KEY (obs_action_id) REFERENCES obs_actions(obs_action_id)
);
""",

# Events

"""
CREATE TABLE events (
event_id INTEGER PRIMARY KEY,
event_type TEXT NOT NULL
);
""",

# Events Actions (many-to-many relationship between events and obs_actions)

"""
CREATE TABLE events_actions (
event_action_id INTEGER PRIMARY KEY,
event_id INTEGER,
obs_action_id INTEGER,
params TEXT,
FOREIGN KEY (event_id) REFERENCES events(event_id),
FOREIGN KEY (obs_action_id) REFERENCES obs_actions(obs_action_id)
);
""",

# Scenes

"""
CREATE TABLE scenes (
scene_id INTEGER PRIMARY KEY,
scene_name TEXT NOT NULL
);
""",

# Scene Items

"""
CREATE TABLE scene_items (
item_id INTEGER PRIMARY KEY,
scene_id INTEGER,
obs_scene_item_id INTEGER,
item_name TEXT,
duration REAL,
FOREIGN KEY (scene_id) REFERENCES scenes(scene_id)
);
""",

# Special Inputs

"""
CREATE TABLE special_inputs (
input_id INTEGER PRIMARY KEY,
input_name TEXT NOT NULL
);
""",

# Input Filters

"""
CREATE TABLE inputs_filters (
input_id INTEGER,
filter_id INTEGER,
FOREIGN KEY (input_id) REFERENCES special_inputs(input_id),
FOREIGN KEY (filter_id) REFERENCES filters(filter_id)
);
""",

# Filters

"""
CREATE TABLE filters (
filter_id INTEGER PRIMARY KEY,
filter_name TEXT
);
""",

# Stream Elements

"""
CREATE TABLE stream_elements (
stream_elements_id INTEGER PRIMARY KEY,
user_id INTEGER,
amount REAL,
message TEXT,
FOREIGN KEY (user_id) REFERENCES users(user_id)
);
""",
