---
layout: default
title: Dodge Bullet
description : "Key takeaways : Backtracking to calculate all possible pathways"
permalink: /Challenges/Dodge-Bullet/
---

# Dodge Bullet

[Problem statement](/Challenges/Dodge-Bullet/Problem-statement)

## Initial Thoughts

Identify safe indexes (not in any bullet's path) and move towards it.
Get safe moves by obtaining left right up down indexes and checking their safety. (If any bullets reach them in the next move).
Make the move which reduces the man's Manhatten distance to nearest safe index.

## Approach

- **Step 1**: Create helper functions to identify safe indexes, check move safety, get Manhatten distance
- **Step 2**: Create Map class to keep track of changing map array. Create class functions to reset map and update bullet location after each move
- **Step 3**: Get man's index and keep moving man until his index is on a safe index. For each loop, get man's safe moves, move the man, and update the map/bullets. If safe moves list is 0, return null for unsolvable
- **Step 4**: Testing and optimisation
- **Step 5**: Modify solution to consider all safe moves(not just shortest to a safe index) and update safe index list after every move. Returns if man's last index is on a safe index

## Challenges Faced

This question was more tedious, requiring attention to detail.
New safe indexes can be created after moves and not just at the start.
Choosing the move for shortest Manhatten distance towards a safe point does not always give the correct answer.

## Optimization

Assuming only 1 existant answer for move list.
Explore all safe moves by appending each of them to the position history list.

**Example:**
Man starts on `Map[2][2]`, his position index is (2,2) and position history is `[[(2,2)]]`.
For his first move, the man could only move left or up, so the position history will be :
`[[(2,2), (2,1)], [(2,2), (1,2)]]`
For his second move, on (2,1) and (1,2), he could move left or up again, so the move history will be :
`[[(2,2), (2,1), (2,0)], [(2,2), (2,1), (1,1)], [(2,2), (1,2), (0,2)]]`
`[(2,2), (1,2), (1,1)]` is not in the list as it's last position already exists.

If a position has no safe moves to make, remove it's history from list as it is a wrong pathway.

Recalculate safe indexes after each move and return/break when man's last position index is in the list of safe indexes.

If move history list is empty, return `null` for no possible moves to safety.

## Key Takeaways

Backtracking to calculate all possible pathways.

## Code

``` python
import json
import logging

from flask import request

from routes import app

logger = logging.getLogger(__name__)

class Map:
    def __init__(self, map) -> None:
        self.map = map
        self.rb = []
        self.lb = []
        self.db = []
        self.ub = []
        self.find_bullets()
        pass
    
    def find_bullets(self):
        for i in range(len(self.map)):
            for j in range(len(self.map[i])):
                if "r" in self.map[i][j]:
                    self.rb.append((i,j))
                elif "l" in self.map[i][j]:
                    self.lb.append((i,j))
                elif "d" in self.map[i][j]:
                    self.db.append((i,j))
                elif "u" in self.map[i][j]:
                    self.ub.append((i,j))

    def update_bullets(self):
        new_rb = []
        for right in self.rb:
            x,y = right
            try:
                self.map[x][y+1].append("r")
                new_rb.append((x,y+1))
            except IndexError:
                continue
        self.rb = new_rb
        
        new_lb = []
        for left in self.lb:
            x,y = left
            if y == 0:
                continue
            self.map[x][y-1].append("l")
            new_lb.append((x,y-1))
        self.lb = new_lb

        new_ub = []
        for up in self.ub:
            x,y = up
            if x == 0:
                continue
            self.map[x-1][y].append("u")
            new_ub.append((x-1,y))
        self.ub = new_ub
            
        new_db = []
        for down in self.db:
            x,y = down
            try:
                self.map[x+1][y].append("d")
                new_db.append((x+1,y))
            except IndexError:
                continue
        self.db = new_db

    def update_map(self):
        for i in range(len(self.map)):
            for j in range(len(self.map[i])):
                self.map[i][j] = ["."]

        self.update_bullets()
        return self.map

def find_safe(map:list) -> list:
    safe = []
    unsafe = []
    for i in range(len(map)):
        for j in range(len(map[i])):
            if "r" in map[i][j]:
                for k in range(j,len(map[i])):
                    if (i,k) not in unsafe:
                        unsafe.append((i,k))    
            if "l" in map[i][j]:
                for k in range(0,j+1):
                    if (i,k) not in unsafe:
                        unsafe.append((i,k))    
            if "d" in map[i][j]:
                for k in range(i,len(map)):
                    if (k,j) not in unsafe:
                        unsafe.append((k,j))  
            if "u" in map[i][j]:
                for k in range(0,i+1):
                    if (k,j) not in unsafe:
                        unsafe.append((k,j))  
            else:
                safe.append((i,j))
    
    safe = [x for x in safe if x not in unsafe]

    # logging.info("safe: {}".format(safe))
    # logging.info("unsafe: {}".format(unsafe))

    return safe

def find_man(map:list) -> list:
    for i in range(len(map)):
        for j in range(len(map[i])):
            if "*" in map[i][j]:
                return (i,j)
    
    return (-1,-1)

def is_safe(map:list, location:tuple) -> bool:
    x, y = location
    # logging.info("man safety loc: {}".format(location))
    try:
        # bullet from top
        if x > 0 and "d" in map[x-1][y]:
            return False
        
    except IndexError:
        pass

    try:
        # bullet from bottom
        if "u" in map[x+1][y]:
            return False
    except IndexError:
        pass

    try:
        # bullet from left
        if y > 0 and "r" in map[x][y-1]:
            return False
    except IndexError:
        pass

    try:
        # bullet from right
        if "l" in map[x][y+1]:
            return False
    except IndexError:
        pass
    
    return True

def find_moves(map:list, man:tuple) -> list:
    x, y = man
    moves = []
    try:
        # bullet from top
        if x > 0 and "d" not in map[x-1][y] and is_safe(map, (x-1,y)):
            moves.append((x-1,y))

    except IndexError:
        pass

    try:
        # bullet from bottom
        if "u" not in map[x+1][y] and is_safe(map, (x+1,y)):
            moves.append((x+1,y))

    except IndexError:
        pass

    try:
        # bullet from left
        if y > 0 and "r" not in map[x][y-1] and is_safe(map, (x,y-1)):
            moves.append((x,y-1))

    except IndexError:
        pass

    try:
        # bullet from right
        if "l" not in map[x][y+1] and is_safe(map, (x,y+1)):
            moves.append((x,y+1))

    except IndexError:
        pass

    return moves

def get_direction(man:tuple, dest:tuple) -> list:
    x1, y1 = man
    x2, y2 = dest

    if x1 == x2:
        if y1 + 1 == y2:
            return 'r'
        else:
            return 'l'
    else:
        if x1 + 1 == x2:
            return 'd'
        else:
            return 'u'

@app.route('/dodge', methods=['POST'])
def evaluate():
    data = request.data.decode('utf-8')
    logging.info("initial data received: {}".format(data))
    map = []
    row = []

    for char in data:
        if char == '\r':
            continue
        elif char == '\n':
            map.append(row)
            row = []
        else:    
            row.append(char)

    map.append(row)
  
    logging.info("initial map: {}".format(map))

    map_class = Map(map)

    safe = find_safe(map)
    man = find_man(map)
    move_tracker = [[man]]
    
    # logging.info("safe spot: {}".format(safe))

    while len(move_tracker) > 0:

        for x in move_tracker:
            last = x[-1]
            if last in safe:
                instructions = []
                for i in range(len(x)-1):
                    instructions.append(get_direction(x[i],x[i+1]))
                
                logging.info("return: {}".format(instructions))
                return json.dumps({"instructions":instructions})
            
        new_move_tracker = []
        # new_pos = []
        for prev in move_tracker:
            # logging.info("prev: {}".format(prev))
            pos = prev[-1]
            # logging.info("position: {}".format(pos))
            safe_moves = find_moves(map, pos)
            # logging.info("safe moves: {}".format(safe_moves))
            # new_pos += [x for x in safe_moves if x not in new_pos]
            if len(safe_moves) > 0:
                new_move_tracker += [prev + [x] for x in safe_moves]

        move_tracker = new_move_tracker

        # logging.info("move history: {}".format(move_tracker))
        map = map_class.update_map()
        # logging.info("return: {}".format(map))
        safe = find_safe(map)

    logging.info("return: {}".format(None))
    return json.dumps({"instructions":None})
```
