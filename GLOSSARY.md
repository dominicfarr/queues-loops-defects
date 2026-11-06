# Queues, Loops, Defects

An arcade game about what happens to each ticket as it moves through a software delivery process, and what the process's queues, loops and defects cost. Its delivery terms come from the article [Faster and More Predictable](https://www.industriallogic.com/blog/faster-and-more-predictable/).

## Language

### Playing

**Run**:
One timed play of the game, from the first hand to the final score.
_Avoid_: Game, session, round

**Scenario**:
The team, demand and code a run starts with.
_Avoid_: Mess, level, variant

**Level**:
A named bundle of scenarios and the moves that can be dealt in them.
_Avoid_: Scenario, stage, world

**Pace**:
How moves arrive during a run, such as a new hand on a timer. Scores are only compared within one pace.
_Avoid_: Mode, difficulty

**Legend**:
A caricature of a well-known figure who arrives at random with a real quote and a power the team can save and use later. The power is the punchline.
_Avoid_: Hero, character, hire

**Move**:
One change to how the team works, such as adopting a practice, dropping one or hiring someone. A card is only how a move is drawn.
_Avoid_: Card, action, upgrade

**Hand**:
The moves on offer at one decision.
_Avoid_: Shop, menu

**Practice**:
A standing way of working that takes up the team's capacity while the team keeps it.
_Avoid_: Upgrade, process

**Score**:
What actually reached users and worked. It is the only number a run is judged by.
_Avoid_: Points, revenue

**Impact**:
What a ticket turns out to be worth when it reaches users. It can't be seen beforehand and falls the longer the ticket was in progress.
_Avoid_: Value, business value

**Dials**:
The quick overall reading of queues, loops and defects. They don't count towards the score.
_Avoid_: Metrics, stats

**Receipt**:
The record of where the days went, showing symptoms and never causes.
_Avoid_: Report, feedback, explanation

### Delivery

**Ticket**:
One unit of work moving through the delivery process, from being handed to a developer to reaching production.
_Avoid_: Work item, change, feature

**Simulated ticket**:
A ticket generated from assumed process parameters, as opposed to one replayed from a real tracker's history.
_Avoid_: Sample, synthetic data

### Waiting

**Policy wait**:
Waiting caused by how work is organised, such as all reviews happening on one day of the week.
_Avoid_: Batching delay

**Load wait**:
Waiting caused by people being busy with other tickets, so it depends on team capacity and the tickets competing for it.
_Avoid_: Queue time

### Defects and loops

**Defect**:
A problem carried by a ticket. A fix can introduce a new one.
_Avoid_: Bug, bad change

**Debt**:
The hidden state of the code that makes work slower, makes defects more likely and makes changing how the team works harder. Players only see its symptoms.
_Avoid_: Mess, cruft

**Gate**:
A stage that may detect a defect in a ticket, and can miss it.
_Avoid_: Check, approval step

**Rejection**:
A gate sending a ticket back. Most follow a detected defect, but some don't, such as a style objection or a merge conflict.
_Avoid_: Return, failure

**Loop**:
The repeat journey a ticket makes after a rejection, back through the intermediate queues and gates.
_Avoid_: Rework, which is only the fixing part

**Escaped defect**:
A defect that passes every gate and reaches production.
_Avoid_: Production bug, leak

### Cost measures

These are always reported separately and never added into one total.

**Elapsed time**:
How long a ticket takes in working days, whether or not anyone is working on it.
_Avoid_: Cost, duration

**Labour cost**:
The money spent on people's time for a ticket. Waiting adds to it only through the extra work that waiting causes.
_Avoid_: Cost, effort

**Cost of delay**:
The value lost because a ticket reached production later than it could have. It rests on an assumption about what the ticket is worth.
_Avoid_: Cost, opportunity cost
