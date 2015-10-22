# hrm-level-data
Human Resource Machine level data

## Usage

Install with: `npm install hrm-level-data`

Then:

```
var levels = require('hrm-level-data');
```

`levels` will be an array of level objects.

An excerpt:

```
[{
    number: 1,
    name: "Mail Room",
    floor: {},
    expect: [{
        inbox: [ 1, 9, 4 ],
        outbox: [ 1, 9, 4 ]
    }],
    challenge: {
        size: 6,
        speed: 6
    }
}, {
    ...
}, {
    number: 20,
    name: "Multiplication Workshop",
    floor: { "9": 0 },
    expect: [{
        inbox: [ 9, 4, 1, 7, 7, 0, 0, 8, 4, 2 ],
        outbox: [ 36, 7, 0, 0, 8 ]
    }],
    challenge: {
        size: 15,
        speed: 109
    }
}, {
    ...
}, {
    number: 34,
    name: "Vowel Incinerator",
    floor: [ "A", "E", "I", "O", "U", 0 ],
    expect: [{
        inbox: [ "C", "O", "D", "E", "U", "P", "L", "A", "K", "E" ],
        outbox: [ "C", "D", "P", "L", "K" ]
    }],
    challenge: {
        size: 13,
        speed: 323
    }
}, {
    ...
}]
```

## Data Schema

The data is in the form of an array of level objects. Each level object has the following properties:

### number
_Number_. The level number, as it appears in the game. Note that the level numbers are not sequential because there are cutscenes that take up level numbers. The first level is 1. The first cutscene, Coffee Time, takes up level 5, and so on.

### name
_String_. The level name.

### floor
_Object_/_Array_. The floor setup. Tiles values can either be numbers (e.g. 5) or strings for letters (e.g. "E"). Numbers are never represented as strings (e.g. "3" won't appear).

For sparse setups, this can be an object with keys as floor tile indices:

```
floor: { "0": "A", "10": 4 } // "A" is on tile 0, 4 is on tile 10
```

For setups where every tile is occupied, this can be an array where indices are directly mapped to floor tiles:

```
floor: [ "A", "E", "I", "O", "U", 0 ] // "A" is on tile 0, "E" is on tile 1, etc.
```

### expect
_Array_. The expected input/output combinations for different runs. Each is object with the following properties:

#### inbox
_Array_. The program input as it appears in the "IN" conveyor belt. The first item appears as the first item that will be picked up from the conveyor belt. In other words, it's [FIFO](https://en.wikipedia.org/wiki/FIFO_(computing_and_electronics)).

#### outbox
_Array_. The expected program output as it will appear in the "OUT" conveyor belt. The first item needs to match what will be first placed on the conveyor belt. In other words, this is also FIFO.

### challenge
_Object. The criteria used for the game's size/speed challenges. Each is an object with the following properties:

#### size
_Number_. The maximum program size to meet the size challenge.

#### speed
_Number_. The maximum program run steps to meet the speed challenge.

## Maintainers

* [@atesgoral](https://github.com/atesgoral) (Ates Goral)
* [@nrkn](https://github.com/nrkn) (Nik Coughlin)

## License

MIT
