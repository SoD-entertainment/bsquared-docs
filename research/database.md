# SQLite Database

## NOW 👈👈👈👈

1. Define a basic schema
2. Figure out how to handle all the OBS stuff
   - ❓ How will I handle the json objects from the GUI

## NOWish

---

## Schema

1. Table: access_levels

   - access_level_id (PK)
   - access_level_name

2. Table: command_responses

   - command_response_id (PK)
   - command_response

3. Table: action_types

   - action_type_id (PK)
   - action_type

4. Table: inputs
   - input_id (PK)
   - input_name
   - input_setting_id (FK -> input_settings.input_setting_id)

<!-- # TODO: update fields -->

5. Table: input_settings

   - input_setting_id (PK)
   - input_name
   - muted
   - volume_db

6. Table: scenes

   - scene_id (PK)
   - scene_name

7. Table: transform_positions

   - transform_position_id (PK)
   - position_x
   - position_y

8. Table: transform_scales

   - transform_scale_id (PK)
   - scale_x
   - scale_y

9. Table: transform_crops

   - transform_crop_id (PK)
   - crop_top
   - crop_right
   - crop_bottom
   - crop_left

10. Table: transform_datas

    - transform_data_id (PK)
    - rotation
    - transform_position_id (FK -> transform_positions.transform_position_id)
    - transform_scale_id (FK -> transform_scales.transform_scale_id)
    - transform_crop_id (FK -> transform_crops.transform_crop_id)

11. Table: scene_items

    - scene_item_id (PK)
    - item_name
    - scene_id (FK -> scenes.scene_id)
    - transform_data_id (FK -> transform_datas.transform_data_id)

12. Table: actions

    - action_id (PK)
    - action_params
    - action_type_id (FK -> action_types.action_type_id)
    - input_id (FK -> inputs.input_id)
    - scene_id (FK -> scenes.scene_id)

13. Table: users

    - user_id (PK)
    - username
    - followed_on
    - last_seen
    - access_level_id (FK -> access_levels.access_level_id)

14. Table: commands

    - command_id (PK)
    - command_name
    - access_level_id (FK -> access_levels.access_level_id)
    - command_response_id (FK -> command_responses.command_response_id)
    - action_id (FK -> actions.action_id)

15. Table: user_commands

    - user_command_id (PK)
    - command_id (FK -> commands.command_id)
    - user_id (FK -> users.user_id)

16. Table: streamelements_donations
    - donation_id (PK)
    - user_id (FK -> users.user_id)
    - amount
    - message
    - timestamp
