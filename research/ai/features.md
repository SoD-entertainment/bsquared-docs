# AI Components

## Conversations

### 1. Word limit

- limit of 25 words
  - prompt: "Condense your response to no more than 20 words"
  - Python's NLTK (Natural Language Toolkit) and spaCy libraries are popular choices for word tokenization.
    - steps in natural language processing pipeline
      - tokenization
      - perform sentiment analysis
        - positive, negative, or neutral
      - named entity recognition (NER)
        - classify named entities into predefined categories
          - people, organisations, locations, times, quantities, monetary values, percentages etc
      - Part-of-Speech Tagging (POS)
        - for grammatical structure
      - Text classification
        - assign predefined labels/categories
          - topic, intent
      - Intent recognition
        - map user's message to predefined intents or actions the bot can perform
          - greeting, question, comment, positive comment, spam
        - Labeled dataset where each user message is annotated with the corresponding intent
        - Trained with a classifier, using techniques like supervised learning or deep learning
        - Predicts the intent associated with the message then determines appropriate response
      - Question answering
        - Models for QA systems user transformer-based models like BERT, GPT or T5
      - Language translation
      - Summarization
      - Entity linking
        - 1. NER (identify peopel, organisations, locations, monetary values, times etc)
        - 2. Linking to Knowledge Base
          - provides more details, descriptions, or context about that entity
        - 3. Enhanced Information
          - enrich's bot's understanding of user's message
      - Dependency parsing
        - analyze grammatical structure/relationship between words
        - uses a "dependency tree"
      - other NLP tasks to extract meaningful info from user's message

### 2. Rate limit

- 1 post every 5 seconds
  - set 5 second timer whenever a post is sent
  - check if difference between current time and last message time is less than 5 seconds
    - if true, delay
    - if false, send message and update last message time

### 3. Combine @user replies

- combine short-answer questions from different users into one reply

  - don't exceed character limit (includes usernames)
  - only do this when there are more than 3 short-answer questions in the last 5 seconds

- combine users when their questions/comments share a topic

  - purpose is to draw in users to a conversation that they can have with each other

  #### EXAMPLE (multiple users within 5 seconds):

  ```
    usera:      hi @bot!
    userb:      that was sushi
    userc:      @bot what is your favourite colour?
    userd:      @bot what's the weather today?
    usere:      where's the streamer @bot
    userb:      where are you from @bot?
    userf:      nah sushi was on Monday
    userg:      chair stream means @bot stream! I welcome our AI overlords!
    BOT:        Bloody hell! One at a time, people, one at a time!
                [*explanation of bot message: bot alerts to too many mentions*]

    usera:      lol sorry
    userc:      haha nevar
    userd:      @bot what's the weather today?
    BOT:        @userc Violet, @userd sunny & 31 degrees, @userb Earth
                [*explanation of bot message: bot combines short-answer questions from multiple users*]

    userb:      Are you sure? Coulda sworn sushi was yesterday...
    usere:      wot about my question sadge
    userd:      yesterday was pizza
    usera:      where's mah helloooooo @bot
    BOT:        @usere No idea ... but IT'S MY STREAM NOW! Right, @userg?!
                [*explanation of bot message: bot combines users with similar topics*]

    userx:      @bot @bot @bot @bot @bot @bot
    userx:      @bot @bot @bot @bot @bot @bot
    userx:      @bot @bot @bot @bot @bot @bot
    usery:      @bot
    userz:      @bot @bot @bot
                [*bot ignores obvious spam messages from userx, usery and userz*]
  ```

- handle greetings from one ore more users

  - if 3 or fewer users, @ each of them
  - if more than 3 users, don't @ any of them - just a general response

  #### EXAMPLE (1 user):

  ```
    usera:        hi, @bot!
    userb:        that was sushi
    BOT:          Hiya, @usera! How goes it?
                  [*explanation of bot message: bot replies to greeting from 1 user*]
  ```

  #### EXAMPLE (<3 users):

  ```
    usera:        hi, @bot!
    userb:        that was sushi
    userc:        hello @bot
    BOT:          Hey hey @usera, @userb. How are you guys today?
                  [*explanation of bot message: bot replies to greetings from 2-3 users*]
  ```

  #### EXAMPLE (3+ users):

  ```
    usera:        hi, @bot!
    userb:        that was sushi
    userc:        hello @bot
    userd:        no, sushi was monday. last night was pizza
    usere:        no it was pizza. you cray cray
    userf:        hola @bot
    userb:        hey @bot
    BOT:          Quite the greeting! Hey hey everyone <3
                  [*explanation of bot message: bot replies to greetings from >3 users*]
  ```

### 4. Spam control

- ignore attempts at making bot spam the chat

### 5. Toggle modes

- ability to toggle bot convo mode !chairstream !chairmode
  - or just leave it on perma for people to use like ChatGPT, but without all the long-winded replies

## Dead air detection

- monitor microphone input and post a conversation starter to chat

## Clippable moment detection

**Manual mode:**

- 'hey siri' style speech command to clip something

**Auto mode:**

- influx of chat messages like "lol" and associated emojis
  - delete clip if hate raid is enabled (perhaps delete ALL clips made during a hate raid?)
