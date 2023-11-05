# The Process

## OBS requirements

The largest part of this project was determining how the logic and database would handle storing, retrieving, and manipulating all of the OBS scenes, sources/scene items, and (audio) inputs/outputs. This proved quite challenging, as it depended not only on writing re-usable methods that were 'future feature' proof, but also looking forward to how the database may need to handle new OBS features later down the track. Given the significant changes in OBS v28 as compared to previous versions, it was imperative to consider how the bot would handle future OBS updates.
