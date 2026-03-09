# Simple Array Sum

## Objectives

When given an array of integers we need to return sym of its elements.

## Constraints

We're given numbers between 0 and 1000, so in this case we don't have edgecases to handle. However it is always good to think about some edgecases, e.g. what happens if item given is not a number, etc.

## Solution

We're already given setup that reads input:

```
'use strict';

const fs = require('fs');

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();
});

function readLine() {
    return inputString[currentLine++];
}

/*
 * Complete the 'simpleArraySum' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER_ARRAY ar as parameter.
 */

function simpleArraySum(ar) {
    // Write your code here
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);
    const arCount = parseInt(readLine().trim(), 10);
    const ar = readLine().replace(/\s+$/g, '').split(' ').map(arTemp => parseInt(arTemp, 10));
    const result = simpleArraySum(ar);

    ws.write(result + '\n');
    ws.end();
}

```

We need only to add simpleArraySum() function body, like:

```
function simpleArraySum(ar) {
    let sum = 0;
    for (let number of ar) {
        sum += number;
    }

    return sum;
}
```

## what to be cautious of:

- `let sum = 0;` - we need to declare it using let, since sum will change with calculations being part of for loop; we also need to declare initial sum - if we don't in first iteration it would be perceived by JavaScript as "undefined"; you can check it by adding console log in for loop.
- `for (number of ar)` - we still need to declare helper variable number using let or const
- `for (let number in ar)` - it returns indexes of items (since they are sort of "keys" in here, and syntax for...in... is dedicated to objects) - and JavaScript sees them as string type:

```
function simpleArraySum(ar) {
    let sum = 0;
    for (let number in ar) {
        console.log(typeof sum);
        console.log(typeof number);
        sum += number;
    }
    return sum;
}
```

_Output_:

```
number (first iteration - typeof sum)
string (first iteration - typeof number)
string (second iteration - typeof sum)
string (second iteration - typeof number)
string (third iteration - typeof sum)
string (third iteration - typeof number)
string (fourth iteration - typeof sum)
string (fourth iteration - typeof number)
string (fifth iteration - typeof sum)
string (fifth iteration - typeof number)
string (sixth iteration - typeof sum)
string (sixth iteration - typeof number)
```
