# <p id="routes">Routes</p>

<ul>
<li><a href="#init">Initialization (Get current position)</a></li>
<li><a href="#move">Move Player</a></li>
<li><a href="#take">Take Treasure</a></li>
<li><a href="#drop">Drop Treasure</a></li>
<li><a href="#sell">Sell Treasure</a></li>
<li><a href="#status">Check Status or Inventory</a></li>
<li><a href="#examine">Examine (Player, Item, or Room)</a></li>
<li><a href="#equip">Wear Equipment</a></li>
<li><a href="#unequip">Remove Equipment</a></li>
<li><a href="#name">Name Changer</a></li>
<li><a href="#shrine">Pray at Shrine</a></li>
<li><a href="#flight">Flight</a></li>
<li><a href="#dash">Dash</a></li>
<li><a href="#carry">Ghost Companion Carry</a></li>
<li><a href="#receive">Receive From Ghost Companion</a></li>
<li><a href="#warp">Warp</a></li>
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
  "room_id": 0,
  "title": "A Dark Room",
  "description": "You cannot see anything.",
  "coordinates": "(60,60)",
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
  "room_id": 10,
  "title": "A Dark Room",
  "description": "You cannot see anything.",
  "coordinates": "(60,61)",
  "exits": ["n", "s", "w"],
  "cooldown": 100.0,
  "errors": [],
  "messages": ["You have walked north."]
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
TBD
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
TBD
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
  "name": "br80",
  "cooldown": 2.0,
  "encumbrance": 2, // How much are you carrying?
  "strength": 10, // How much can you carry?
  "speed": 10, // How fast do you travel?
  "gold": 400,
  "bodywear": "None",
  "footwear": "None",
  "inventory": ["Small Treasure"],
  "status": [],
  "errors": [],
  "messages": []
}
```

## <div style="display: flex; justify-content: space-between"><p id="examine">Examine (Item, Player, or Room)</p><a href="#routes">(TOP)</a></div>

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
{ "name": "[NAME OF ITEM OR PLAYER]" }
```

##### Response:

```json
TBD
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
TBD
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
TBD
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
TBD
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

## <div style="display: flex; justify-content: space-between"><p id="carry">Carry (Ghost Companion)</p><a href="#routes">(TOP)</a></div>

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
TBD
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
No Body
```

##### Response:

```json
TBD
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
TBD
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
TBD
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
TBD
```
