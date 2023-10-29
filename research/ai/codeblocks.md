# Code Blocks

```python
# Determine if an answer can be provided in 4 of fewer words:
def short_answer_question(answer, max_words=4):
    # Tokenize the answer by splitting it into words
    tokens = answer.split()

    # Check if the number of tokens is within the limit
    return len(tokens) <= max_words

# Example usage
answer = "Yes, it is possible."
if short_answer_question(answer):
    print("The answer can be provided in 4 or fewer words.")
else:
    print("The answer is longer than 4 words.")
```

```python
# Tokenenize user's message
def tokenize_message(message):
    # Word tokenization
    return message.split()  # Split by spaces

# Example usage
user_message = "Hello, chatbot! How can I help you?"
tokens = tokenize_message(user_message)
print(tokens)  # Output: ['Hello,', 'chatbot!', 'How', 'can', 'I', 'help', 'you?']
```

```python
# Word tokenization
# ! requires nltk import
import nltk
nltk.download('punkt')

sentence = "Hello, how are you?"
tokens = nltk.word_tokenize(sentence)
print(tokens)  # Output: ['Hello', ',', 'how', 'are', 'you', '?']
```
