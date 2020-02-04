# Routes

## Init

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

## Move

---

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

## Take Treasure

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

## Drop Treasure

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

## Selling Treasure

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

## Status/Inventory

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

## Examine (Item, Player, or Room)

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

## Wear Equipment

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

## Remove Equipment

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

## Name Changer - Requires 1000 gold

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
{ "name": "[NEW NAME]" }
```

##### Response:

```json
TBD
```

## Pray at Shrine

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

## Flight - Avoid Penalties on Elevated Terrain

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

## Dash - Move Multiple Room in One Direction

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

## Carry (Ghost Companion)

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

## Receive From (Ghost Companion)

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

## Warp - Need Bodywear and Footwear

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

## Mine Lambda Coin - Need to Be in the Correct Room

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

## Last Valid Proof

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

## Lambda Coin Balance

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

## Transmogrify Items - Need Lambda Coins

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
