# Queues, Loops, Defects

A model of what happens to each ticket as it moves through a software delivery process, and what the process's queues, loops and defects cost. Its terms come from the article [Faster and More Predictable](https://www.industriallogic.com/blog/faster-and-more-predictable/).

## Language

**Ticket**:
One unit of work moving through the delivery process, from being handed to a developer to reaching production.
_Avoid_: Work item, change, feature

**Simulated ticket**:
A ticket generated from assumed process parameters, as opposed to one replayed from a real tracker's history.
_Avoid_: Sample, synthetic data

**Scenario**:
One version of the delivery process with its own parameters, such as the current process or an improved one. A scenario carries the costs of any change it makes.
_Avoid_: Variant, what-if

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
