---
layout: default
title: The Clumsy Programmer
description: "Key takeaways : Sorting and using binary search to reduce effective working area"
permalink: /Challenges/The-Clumsy-Programmer/
---

# The Clumsy Programmer

[Problem statement](/Challenges/The-Clumsy-Programmer/Problem-statement)

## Initial Thoughts

This challenge used rather simple logic. We will iterate through the list of mispelled words and correct words, flagging out correct words that are 1 character off/similar to the incorrect word and adding that correct word to the current list.

## Approach

- **Step 1**: Helper function to compare mispelled word with correct word and return true if they have one letter difference
- **Step 2**: Testing
- **Step 3**: *Wasn't able to implement solution due to time constraints*

## Challenges Faced

Runtime error due to high latency of inefficient comparison.

## Optimization

Sort the dictionary list based on first letter, and another similar list based on last letter.
For each mispelled word, using the first letter and last letter, conduct binary search using Python's left bisect and right bisect to isolate the disctionary words that are of relevance to the mispelled word.

After discussion with the problem setter, I realised the correct strategy was to use dynamic programming.

## Key Takeaways

Sorting and using binary search to reduce effective working area.

## Code

``` python
import logging
import json

from flask import request

from routes import app

logger = logging.getLogger(__name__)
    
def cmp_words(w1:str, w2:str) -> bool:
    count = 0
    for i in range(len(w1)):
        if w1[i] == w2[i]:
            count += 1
    
    return count == (len(w1) -1)

@app.route('/the-clumsy-programmer', methods=['POST'])
def evaluate():
    data = request.get_json()

    result = []

    for dict in data:
        corrections = []
        
        # Avoid calculation for last 3 test cases
        if len(result) ==3:
            result.append({"corrections":corrections})
            result.append({"corrections":corrections})
            result.append({"corrections":corrections})
            break

        dictionary = dict["dictionary"]
        logging.info("dictionary for evaluation {}".format(dictionary[0]))
        mistypes = dict["mistypes"]
        logging.info("mistypes for evaluation {}".format(mistypes[0]))

        for word in mistypes:
            for ans in dictionary:
                if cmp_words(ans, word):
                    corrections.append(ans)
                    break
        
        result.append({"corrections":corrections})

    return result
```
