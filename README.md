# <p id="routes">Routes</p>

<ul>
<li><a href="#init">Initialization (Get current position)</a></li>
<li><a href="#move">Move Player</a></li>
<li><a href="#take">Take Treasure</a></li>
<li><a href="#drop">Drop Treasure</a></li>
<li><a href="#sell">Sell Treasure</a></li>
<li><a href="#status">Check Status or Inventory</a></li>
<li><a href="#examine">Examine (Item or Room)</a></li>
<li><a href="#equip">Wear Equipment</a></li>
<li><a href="#unequip">Remove Equipment</a></li>
<li><a href="#name">Name Changer</a></li>
<li><a href="#shrine">Pray at Shrine</a></li>
<li><a href="#flight">Flight</a></li>
<li><a href="#dash">Dash</a></li>
<li><a href="#carry">Ghost Companion Carry</a></li>
<li><a href="#receive">Receive From Ghost Companion</a></li>
<li><a href="#warp">Warp</a></li>
<li><a href="#recall">Recall</a></li>
<li><a href="#mine">Mine Lambda Coin</a></li>
<li><a href="#proof">Get Last Proof</a></li>
<li><a href="#balance">Lambda Coin Balance</a></li>
<li><a href="#transmogrify">Transmogrify Item</a></li>
</ul>

## <div style="display: flex; justify-content: space-between"><p id="init">Init</p><a href="#routes">(TOP)</a></div>

---

#### GET

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/init/
```

##### Header:

```javascript
'Authorization: Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607';
```

##### Response:

```json
{
  "room_id": 507,
  "title": "Darkness",
  "description": "You are standing on grass and surrounded by darkness.",
  "coordinates": "(60,63)",
  "elevation": 0,
  "terrain": "NORMAL",
  "players": ["Phil Smith", "Dr Cooldown"],
  "items": ["shiny treasure", "shiny treasure", "nice jacket", "poor boots"],
  "exits": ["n", "s", "e", "w"],
  "cooldown": 1.0,
  "errors": [],
  "messages": []
}
```

## <div style="display: flex; justify-content: space-between"><p id="move">Move</p>

## <a href="#routes">(TOP)</a></div>

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/move/
```

##### Header:

```javascript
'Authorization: Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607';
'Content-Type: application/json';
```

##### Body:

```json
{ "direction": "n" }
```

##### ** OPTIONAL ** - REDUCED COOLDOWN IF YOU KNOW THE NEXT_ROOM_ID

```json
{ "direction": "s", "next_room_id": "0" }
```

##### Response:

```json
{
  "room_id": 506,
  "title": "Darkness",
  "description": "You are standing on grass and surrounded by darkness.",
  "coordinates": "(60,62)",
  "elevation": 0,
  "terrain": "NORMAL",
  "players": [],
  "items": [],
  "exits": ["n", "s", "e", "w"],
  "cooldown": 3.0,
  "errors": [],
  "messages": ["You have walked south.", "Wise Explorer: -50% CD"]
}
```

## <div style="display: flex; justify-content: space-between"><p id="take">Take Treasure</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/take/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "name": "treasure" }
```

##### Response:

```json
{
  "room_id": 507,
  "title": "Darkness",
  "description": "You are standing on grass and surrounded by darkness.",
  "coordinates": "(60,63)",
  "elevation": 0,
  "terrain": "NORMAL",
  "players": ["Phil Smith", "Dr Cooldown"],
  "items": ["shiny treasure", "nice jacket", "poor boots"],
  "exits": ["n", "s", "e", "w"],
  "cooldown": 1.0,
  "errors": [],
  "messages": ["You have picked up shiny treasure"]
}
```

## <div style="display: flex; justify-content: space-between"><p id="drop">Drop Treasure</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/drop/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "name": "treasure" }
```

##### Response:

```json
{
  "room_id": 507,
  "title": "Darkness",
  "description": "You are standing on grass and surrounded by darkness.",
  "coordinates": "(60,63)",
  "elevation": 0,
  "terrain": "NORMAL",
  "players": ["Phil Smith", "Dr Cooldown"],
  "items": ["poor boots"],
  "exits": ["n", "s", "e", "w"],
  "cooldown": 1.0,
  "errors": [],
  "messages": ["You have dropped poor boots"]
}
```

## <div style="display: flex; justify-content: space-between"><p id="sell">Selling Treasure</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/sell/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "name": "treasure" }
```

##### ** IMPORTANT ** - TO ACTUALLY SELL

```json
{ "name": "treasure", "confirm": "yes" }
```

##### Response:

```json
{
  "room_id": "?",
  "title": "Shop",
  "description": "You are standing in a shop. You can sell your treasure here.",
  "coordinates": "?",
  "players": [],
  "items": [],
  "exits": ["e"],
  "cooldown": 2.0,
  "errors": [],
  "messages": [
    "I'll give you 100 gold for that Small Treasure.",
    "(include 'confirm':'yes' to sell Small Treasure)"
  ]
}
```

## <div style="display: flex; justify-content: space-between"><p id="status">Status/Inventory</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/status/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
No body
```

##### Response:

```json
{
  "name": "[DONUTS]",
  "cooldown": 1.0,
  "encumbrance": 8,
  "strength": 21,
  "speed": 101,
  "gold": 700,
  "bodywear": "well-crafted jacket",
  "footwear": "well-crafted boots",
  "inventory": [
    "poor boots",
    "nice jacket",
    "shiny treasure",
    "shiny treasure"
  ],
  "abilities": ["pray", "mine", "fly", "dash", "carry", "warp", "recall"],
  "status": [],
  "has_mined": true,
  "errors": [],
  "messages": [],
  "snitches": 768
}
```

## <div style="display: flex; justify-content: space-between"><p id="examine">Examine (Item or Room)</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/examine/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "name": "[NAME OF ITEM OR ROOM]" }
```

##### Response:

```json
// WISHING WELL
{
    "name": "Wishing Well",
    "description": "You see a faint pattern in the water...\n\n10000010\n00000001\n01000110\n01001000\n00000001\n10000010\n00000001\n01101001\n01001000\n00000001\n10000010\n00000001\n01101110\n01001000\n00000001\n10000010\n00000001\n01100100\n01001000\n00000001\n10000010\n00000001\n00100000\n01001000\n00000001\n10000010\n00000001\n01110100\n01001000\n00000001\n10000010\n00000001\n01101000\n01001000\n00000001\n10000010\n00000001\n01100101\n01001000\n00000001\n10000010\n00000001\n00100000\n01001000\n00000001\n10000010\n00000001\n01110011\n01001000\n00000001\n10000010\n00000001\n01101110\n01001000\n00000001\n10000010\n00000001\n01101001\n01001000\n00000001\n10000010\n00000001\n01110100\n01001000\n00000001\n10000010\n00000001\n01100011\n01001000\n00000001\n10000010\n00000001\n01101000\n01001000\n00000001\n10000010\n00000001\n00100000\n01001000\n00000001\n10000010\n00000001\n01101001\n01001000\n00000001\n10000010\n00000001\n01101110\n01001000\n00000001\n10000010\n00000001\n00100000\n01001000\n00000001\n10000010\n00000001\n01110010\n01001000\n00000001\n10000010\n00000001\n01101111\n01001000\n00000001\n10000010\n00000001\n01101111\n01001000\n00000001\n10000010\n00000001\n01101101\n01001000\n00000001\n10000010\n00000001\n00100000\n01001000\n00000001\n10000010\n00000001\n11000101\n10000010\n00000010\n00111011\n10101000\n00000001\n00000010\n10000010\n00000010\n00110100\n10101011\n00000001\n00000010\n01001000\n00000001\n10000010\n00000001\n11000011\n10000010\n00000010\n10110110\n10101000\n00000001\n00000010\n10000010\n00000010\n10111011\n10101011\n00000001\n00000010\n01001000\n00000001\n10000010\n00000001\n01001001\n10000010\n00000010\n00001010\n10101000\n00000001\n00000010\n10000010\n00000010\n00111100\n10101011\n00000001\n00000010\n01001000\n00000001\n00000001",
    "cooldown": 1.0,
    "errors": [],
    "messages": []
}

// ITEM
{
    "name": "poor boots",
    "description": "These are transmogrified boots.",
    "weight": 1,
    "itemtype": "FOOTWEAR",
    "level": 1,
    "exp": 0,
    "attributes": "{\"STRENGTH\": 1, \"SPEED\": 33}",
    "cooldown": 1.0,
    "errors": [],
    "messages": []
}

// ERROR
{
    "room_id": 555,
    "title": "Wishing Well",
    "description": "You are standing besides a large well. A sign next the well reads 'EXAMINE WELL, FIND WEALTH'.",
    "coordinates": "(58,61)",
    "elevation": 0,
    "terrain": "NORMAL",
    "players": [
        "Labyrinth65",
        "Aaron The Beast",
        "Michael Mangus",
        "Kevin Smith",
        "Chance",
        "Ad-R0ck"
    ],
    "items": [],
    "exits": [
        "n"
    ],
    "cooldown": 6.0,
    "errors": [
        "Item not found: +5s CD"
    ],
    "messages": []
}
```

## <div style="display: flex; justify-content: space-between"><p id="equip">Wear Equipment</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/wear/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "name": "[NAME OF WEARABLE]" }
```

##### Response:

```json
{
  "name": "[DONUTS]",
  "cooldown": 1.0,
  "encumbrance": 8,
  "strength": 21,
  "speed": 101,
  "gold": 700,
  "bodywear": "well-crafted jacket",
  "footwear": "well-crafted boots",
  "inventory": [
    "poor boots",
    "nice jacket",
    "shiny treasure",
    "shiny treasure"
  ],
  "abilities": ["pray", "mine", "fly", "dash", "carry", "warp", "recall"],
  "status": [],
  "has_mined": true,
  "errors": [],
  "messages": ["You wear well-crafted jacket"],
  "snitches": 768
}
```

## <div style="display: flex; justify-content: space-between"><p id="unequip">Remove Equipment</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/undress/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "name": "[NAME OF WEARABLE]" }
```

##### Response:

```json
{
  "name": "[DONUTS]",
  "cooldown": 1.0,
  "encumbrance": 8,
  "strength": 12,
  "speed": 101,
  "gold": 700,
  "bodywear": null,
  "footwear": "well-crafted boots",
  "inventory": [
    "poor boots",
    "nice jacket",
    "shiny treasure",
    "shiny treasure",
    "well-crafted jacket"
  ],
  "abilities": ["pray", "mine", "fly", "dash", "carry", "warp", "recall"],
  "status": [],
  "has_mined": true,
  "errors": [],
  "messages": ["You remove well-crafted jacket"],
  "snitches": 768
}
```

## <div style="display: flex; justify-content: space-between"><p id="name">Name Changer - Requires 1000 gold</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/change_name/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "name": "[NEW NAME]", "confirm": "aye" }
```

##### Response:

```json
TBD
```

## <div style="display: flex; justify-content: space-between"><p id="shrine">Pray at Shrine</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/pray/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
No Body
```

##### Response:

```json
TBD
```

## <div style="display: flex; justify-content: space-between"><p id="flight">Flight - Avoid Penalties on Elevated Terrain</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/fly/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "direction": "n" }
```

##### Response:

```json
{
  "room_id": 528,
  "title": "Darkness",
  "description": "You are standing on grass and surrounded by darkness.",
  "coordinates": "(58,62)",
  "elevation": 0,
  "terrain": "NORMAL",
  "players": [],
  "items": ["nice jacket", "nice boots"],
  "exits": ["n", "s", "w"],
  "cooldown": 8.100000000000001,
  "errors": [],
  "messages": [
    "You have flown north.",
    "Flight Bonus: -10% CD",
    "Foolish Explorer: +50% CD"
  ]
}
```

## <div style="display: flex; justify-content: space-between"><p id="dash">Dash - Move Multiple Room in One Direction</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/dash/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "direction": "n", "num_rooms": "5", "next_room_ids": "10,19,20,63,72" }
```

##### Response:

```json
TBD
```

## <div style="display: flex; justify-content: space-between"><p id="carry">Carry (Ghost Companion - Holds 1 Item)</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/carry/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "name": "[ITEM_NAME]" }
```

##### Response:

```json
{
  "room_id": 555,
  "title": "Wishing Well",
  "description": "You are standing besides a large well. A sign next the well reads 'EXAMINE WELL, FIND WEALTH'.",
  "coordinates": "(58,61)",
  "elevation": 0,
  "terrain": "NORMAL",
  "players": [
    "Labyrinth65",
    "Aaron The Beast",
    "Michael Mangus",
    "Kevin Smith",
    "Chance",
    "Ad-R0ck"
  ],
  "items": [],
  "exits": ["n"],
  "cooldown": 1.0,
  "errors": [],
  "messages": ["You hand shiny treasure to Glasowyn's Ghost"]
}
```

## <div style="display: flex; justify-content: space-between"><p id="receive">Receive From (Ghost Companion)</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/receive/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "name": "[ITEM_NAME]" }
```

##### Response:

```json
{
  "room_id": 555,
  "title": "Wishing Well",
  "description": "You are standing besides a large well. A sign next the well reads 'EXAMINE WELL, FIND WEALTH'.",
  "coordinates": "(58,61)",
  "elevation": 0,
  "terrain": "NORMAL",
  "players": [
    "Labyrinth65",
    "Aaron The Beast",
    "Michael Mangus",
    "Kevin Smith",
    "Chance",
    "Ad-R0ck"
  ],
  "items": [],
  "exits": ["n"],
  "cooldown": 1.0,
  "errors": [],
  "messages": ["You receive shiny treasure from Glasowyn's Ghost"]
}
```

## <div style="display: flex; justify-content: space-between"><p id="warp">Warp - Need Bodywear and Footwear</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/warp/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
No Body
```

##### Response:

```json
{
  "room_id": 55,
  "title": "Wishing Well",
  "description": "You are standing besides a large well. A sign next the well reads 'EXAMINE WELL, FIND WEALTH'.",
  "coordinates": "(63,61)",
  "elevation": 0,
  "terrain": "NORMAL",
  "players": [
    "['Selkirk']",
    "[Nowhere] Arvin",
    "[matthew_harshman]",
    "['Matt']"
  ],
  "items": [],
  "exits": ["w"],
  "cooldown": 6.0,
  "errors": [],
  "messages": ["You have warped to an alternate dimension."]
}
```

## <div style="display: flex; justify-content: space-between"><p id="recall">Recall</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/recall/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
No Body
```

##### Response:

```json
{
  "room_id": 0,
  "title": "A brightly lit room",
  "description": "You are standing in the center of a brightly lit room. You notice a shop to the west and exits to the north, south and east.",
  "coordinates": "(60,60)",
  "elevation": 0,
  "terrain": "NORMAL",
  "players": [],
  "items": [],
  "exits": ["n", "s", "e", "w"],
  "cooldown": 6.0,
  "errors": [],
  "messages": ["You have been recalled to your point of origin."]
}
```

## <div style="display: flex; justify-content: space-between"><p id="mine">Mine Lambda Coin - Need to Be in the Correct Room</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/bc/mine/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "proof": new_proof }
```

##### Response:

```json
{
  "index": 10547,
  "transactions": "adv_blockchain.Transaction.None",
  "proof": 1685616,
  "previous_hash": "91507b40cea651157f2337aae0a1f813b03226eaf6c7643a46ade9c8859f9d75",
  "cooldown": 6,
  "messages": ["New Block Forged"],
  "errors": []
}
```

## <div style="display: flex; justify-content: space-between"><p id="proof">Last Valid Proof</p><a href="#routes">(TOP)</a></div>

---

#### GET

```html
https://lambda-treasure-hunt.herokuapp.com/api/bc/last_proof/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
No Body
```

##### Response:

```json
{
  "proof": 123456,
  "difficulty": 8,
  "cooldown": 1.0,
  "messages": [],
  "errors": []
}
```

## <div style="display: flex; justify-content: space-between"><p id="balance">Lambda Coin Balance</p><a href="#routes">(TOP)</a></div>

---

#### GET

```html
https://lambda-treasure-hunt.herokuapp.com/api/bc/get_balance/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
No Body
```

##### Response:

```json
{
  "cooldown": 1.0,
  "messages": ["You have a balance of 35.0 Lambda Coins"],
  "errors": []
}
```

## <div style="display: flex; justify-content: space-between"><p id="transmogrify">Transmogrify Items - Need Lambda Coins</p><a href="#routes">(TOP)</a></div>

---

#### POST

```html
https://lambda-treasure-hunt.herokuapp.com/api/adv/transmogrify/
```

##### Header:

```javascript
{
  'Authorization': 'Token 7a375b52bdc410eebbc878ed3e58b2e94a8cb607',
  'Content-Type': 'application/json'
}
```

##### Body:

```json
{ "name": "[NAME OF ITEM]" }
```

##### Response:

```json
{
  "room_id": 495,
  "title": "The Transmogriphier",
  "description": "A strange machine stands in this room.  There is a large opening on the top.  A placard reads, \"Test your luck!  One item and one Lambdacoin!\"",
  "coordinates": "(50,58)",
  "elevation": 0,
  "terrain": "NORMAL",
  "players": [],
  "items": [],
  "exits": ["e"],
  "cooldown": 6.0,
  "errors": [],
  "messages": ["Your poor boots transmogrified into nice jacket!"]
}
```
