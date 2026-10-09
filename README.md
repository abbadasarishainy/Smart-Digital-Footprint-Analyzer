# Smart-Digital-Footprint-Analyzer
Smart Digital Footprint Analyzer

import re
from collections import Counter

def analyze_text(text):
    words = re.findall(r"\b[a-zA-Z]+\b", text.lower())

    if not words:
        print("Please enter some text!")
        return

    word_count = len(words)
    unique_words = set(words)
    common_word = Counter(words).most_common(1)[0]

    positive_words = {"happy", "love", "good", "great", "success"}
    negative_words = {"sad", "bad", "hate", "fail", "angry"}

    positive = sum(word in positive_words for word in words)
    negative = sum(word in negative_words for word in words)

    if positive > negative:
        mood = "Positive 😊"
    elif negative > positive:
        mood = "Negative 😔"
    else:
        mood = "Neutral 😐"

    print("\n===== TEXT ANALYSIS REPORT =====")
    print("Total words:", word_count)
    print("Unique words:", len(unique_words))
    print("Most used word:", common_word[0])
    print("Word frequency:", common_word[1])
    print("Estimated mood:", mood)
    print("================================")

text = input("Enter your text: ")
analyze_text(text)
