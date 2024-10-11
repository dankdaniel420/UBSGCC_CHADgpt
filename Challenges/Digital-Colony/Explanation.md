---
layout: default
title: Digital Colony
description: "Key takeaway : Pattern recognition to reduce repeated computations"
permalink: /Challenges/Digital-Colony/
---

# Digital Colony

[Problem statement](/Challenges/Digital-Colony/Problem-statement.html)

## Initial Thoughts

Convert the String to a list of integers and get the child weight from parent weights.
Create an initial weight variable and add the total weight of children created in each generation.

## Approach

- **Step 1**: Create a helper function to take in the list of parent weights and last digit of total weight (one's place), returns next generation of parent weights and total additional weight from children created
- **Step 2**: Optimize the solution
- **Step 3**: Modify helper function to take a string of one parent pair and last digit of total weight, returns list of next generation parent pairs. Back in main, use count of inital parent pair to add new parent pairs into new generation dictionary

## Challenges Faced

Latency increased exponentially after 20 generations, resulting in runtime error for test cases with large generations of 50.

## Optimization

Explored potential solutions to improve runtime: threading, saving to csv/txt using numpy.

Final strategy was to collate the number of similar parents pairs in a dictionary `parent1_parent2 : count` for each generation and multiply their child weight with the total count of similar parent pairs. Also create/add `parent1_child : count, child_parent2 : count` into dictionary of next generation.

This combines similar parent pairs into **one** calculation instead of `count` calculations (which can be extremely large after 20 generations).

## Key Takeaways

Pattern recognition to reduce repeated computations.

## Code

``` python

import json
import logging

from flask import request
from routes import app

def get_pairs(pair:str,weight) -> list:
    num = int(pair[0]) - int(pair[1])
    if num < 0:
        num += 10
    
    num += weight
    num %= 10

    return [pair[0]+str(num), str(num)+pair[1]]

@app.route('/digital-colony', methods=['POST'])
def evaluate():
    data = request.get_json()
    logging.info("data received: {}".format(data))
    weight = 0

    result = []

    colony = data[0]["colony"]

    for num in colony:
        weight += int(num)

    pair_dict = {}

    for pair in [colony[:2], colony[1:3], colony[2:]]:
        if pair in pair_dict:
            pair_dict[pair] += 1
        else:
            pair_dict[pair] = 1

    logging.info("current dict: {}".format(pair_dict))

    for i in range(10):
        modulo_weight = weight % 10
        new_pair_dict = {}
        for pair, count in pair_dict.items():
            new_pairs = get_pairs(pair,modulo_weight)
            weight += count * int(new_pairs[0][1])
            
            for newpair in new_pairs:
                if newpair in new_pair_dict:
                    new_pair_dict[newpair] += count
                else:
                    new_pair_dict[newpair] = count

        pair_dict = new_pair_dict.copy()
        logging.info("current colony: {}".format(i))

    result.append(str(weight))

    colony = data[1]["colony"]

    weight = 0

    for num in colony:
        weight += int(num)

    pair_dict = {}

    for pair in [colony[:2], colony[1:3], colony[2:]]:
        if pair in pair_dict:
            pair_dict[pair] += 1
        else:
            pair_dict[pair] = 1

    logging.info("current dict: {}".format(pair_dict))

    for i in range(50):
        modulo_weight = weight % 10
        new_pair_dict = {}
        for pair, count in pair_dict.items():
            new_pairs = get_pairs(pair,modulo_weight)
            weight += count * int(new_pairs[0][1])
            
            for newpair in new_pairs:
                if newpair in new_pair_dict:
                    new_pair_dict[newpair] += count
                else:
                    new_pair_dict[newpair] = count

        pair_dict = new_pair_dict.copy()
        logging.info("current colony: {}".format(i))

    result.append(str(weight))

    logging.info("My result :{}".format(result))
    return json.dumps(result)
```
