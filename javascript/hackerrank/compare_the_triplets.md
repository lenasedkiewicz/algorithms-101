# Compare the Triplets

## Objectives

We compare two inputs containing triples with grades from two people. It's like comparing three items, each person use number between 1 and 100 to assess item.

We need to compare assessments for same items from those two different people. We compare first item grading, then second item, then third item.

If person A grades item higer this person gets a point. If grades are equal no one gets the point. If person B grades item higher this person gets the point.

The output expected from us is array with poins gained by person A and then points gained by person B.

## Constraints

- Number given are between 1 and 100.
- The output need to be an array with two items.

## Solution

function compareTriplets(a, b) {
let resultA = 0;
let resultB = 0;

    let array = [];
    for (let i = 0; i < a.length; i++) {
        if (a[i] > b[i]) {
            resultA += 1;
        } else if (a[i] < b[i]) {
            resultB += 1;
        }
    }

    array.push(resultA);
    array.push(resultB);
    return array;

}

## what to be cacutious of:

We don't need to check equal condition since we're not giving points for this.
