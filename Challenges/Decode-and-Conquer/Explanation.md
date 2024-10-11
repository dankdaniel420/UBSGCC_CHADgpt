---
layout: default
title: Decode and Conquer!
description: "Key takeaway : Hunting for flags requires strong inference, resilience, and creativity"
permalink: /Challenges/Decode-and-Conquer/
---

# Decode and Conquer

[Problem statement](./Problem-statement)

## Initial Thoughts

This challenge tested capture-the-flag (ctf) skills. Additionally, each task description was quite verbose in hinting the required decoding for each flag.

Teck Ren found the flag for task 1 and the first flag for task 4, before I hopped in and found the flag for task 2 and the second flag for task 4.

## Approach

### Task 2

- **Step 1**: Interpreting the hint - *shift your thinking like a Roman king to unlock the hidden prefix* - I decided to try different sized shifts of the Caesar Cipher on the key prefix `sk`
- **Step 2**: Found the key due to the presence of {} brackets, in addition to the repo and file name `DefN0tSus/thislooksfishy · thislooksfishier.js`

### Task 4

- **Step 1**: Interpreting the hint - *messages concealed in these pictures* - I used this [image steganography tool](https://incoherency.co.uk/image-steganography/#unhide) to uncover the hidden bits
- **Step 2**: Found the key after checking least significant bits 4 and 5

## Challenges Faced

Dead ends that led to feelings of frustration and the temptation to quit.

## Optimization

Discussed with my team about the methods they have tried and brainstormed toegther for new ideas/approaches.

## Key Takeaways

Hunting for flags requires strong inference, resilience, and creativity.
