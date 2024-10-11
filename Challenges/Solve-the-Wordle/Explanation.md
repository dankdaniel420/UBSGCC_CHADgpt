---
layout: default
title: Solve the Wordle
description: "Key takeaways : Apply code adaptation on open source resources to help solve challenges"
permalink: /Challenges/Solve-the-Wordle/
---

# Solve the Wordle

[Problem statement](/Challenges/Solve-the-Wordle/Problem-statement.html)

## Initial Thoughts

This challenge belonged to the easier category. Hence I'm pretty sure we are not tested to create our own wordle solver but rather improve on an existing solver to accomodate for the masking of results.

Since we are always given the full history of guesses and evaluation, we can input all past words and evaluations before asking for the next suggested word to guess.

## Approach

- **Step 1**: Found an existing solver on this [Github repo by jason-chao](https://github.com/jason-chao/wordle-solver)
- **Step 2**: Run the progranne with the example output to test it's efficiency
- **Step 3**: Modify the programme's symbols to replace masked symbols `?` if seen before, else ignore it
- **Step 4**: Analyze the solver to work with arguments instead of system inputs
- **Step 5**: Input all past guesses and evaluations before returning the next suggested word as our next guess
- **Step 6**: Testing

## Challenges Faced

It took awhile to understand how Jason's code worked, and even longer to adapt it to this challenge requirements.

## Optimization

If a letter's analysis is masked in the output, search through `right_spot_pattern_list`, `wrong_spot_pattern`, and `excluded_letters` to replace the mask with a known evaluation for the letter.

## Key Takeaways

Apply code adaptation on open source resources to help solve challenges.

## Code

``` python
import json
import logging
import sys


from wordlesolver import wordle_solver

from flask import request

from routes import app

logger = logging.getLogger(__name__)


@app.route('/wordle-game', methods=['POST'])
def evaluate():
    data = request.get_json()
    logging.info("data received: {}".format(data))

    guesses = data.get("guessHistory")
    eval = data.get("evaluationHistory")

    word_list_file_paths = ["english_words_opener.txt", "english_words_full.txt"]
    solver_multi = wordle_solver.WorldSolverMultiList(word_list_file_paths, 5, False)
    solver_multi.max_try_indexes_for_lists = [2, sys.maxsize]

    for i in range(0, len(guesses)):
        if eval[i] == "OOOOO":
            break
        
        solver_multi.input_guess_result(guesses[i], eval[i].lower())
    
    suggested_words = solver_multi.get_suggested_words()

    result = {"guess":suggested_words.words[0]}

    logging.info("My result :{}".format(result))
    return json.dumps(result)
```
