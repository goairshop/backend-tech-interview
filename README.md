# Problem Statement

There is a feature on the airshop website that allows users with loyalty accounts to claim a free sample box up
to once every 30 days. In order for the provide this feature, the backend needs to provide a record of the user's
free sample box usages for the year, and a list of what they are entitled to claim in future. The output on the frontend will be a list of sample boxes, with their status, along with the date they were claimed on or the date they will be unlockable.

The goal of the problem is not necessarily to produce a perfect solution during the interview, but to work through making sense of the requirements and starting to code a good solution.

## Input
Input is a list of committed free sample boxes (already used), a list of active free sample box (unlocked but not used yet), along with the number of free sample boxes the user is entitled to this year. (Users in different tiers will be able to claim different numbers of boxes)
```
calcFreeSampleBoxes(committedFreeSamplesBoxes: FreeSampleBoxInput[], activeFreeSampleBox: FreeSampleBoxInput, numBoxes: number): FreeSampleBox[]

export class FreeSampleBoxInput {
  updated_at: Date
}
```

## Output
Output is a list of free sample boxes, both the used ones and the ones claimable in the future, sorted by date
```
export class FreeSampleBox {
  status: FreeSampleBoxStatus;
  claimed_at?: Date;
  claimable_at?: Date;
}
```

## Example Inputs
```
Example inputs:
Single box claimed, none active, 2 boxes offered

[{"updated_at": "1-1-2023"}], null, 2

Two boxes claimed, one unlocked, 5 boxes offered
[{'updated_at": "1-1-2023"}, {"updated_at": "2-1-2023"}], {updated_at": "3-1-2023"}, 5
```

## Rules:
1. A user should only be able to use a free sample box once every 30 days
2. Bonus: If a user's next box is already unlocked, the box available after that should show as unlockable 30 days from today

