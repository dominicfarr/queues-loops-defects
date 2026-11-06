# Prototypes

Throwaway experiments, kept so they can still be played. Each one is a single HTML file with no build step: double-click it to open it. The only thing a page fetches is its Google Fonts, and it falls back to system fonts offline.

| Prototype | What it is | Question it answered |
|---|---|---|
| [Delivery flow](delivery-flow.html) | Maths model with guided walkthroughs | Does a simulation reproduce the article's totals, and can it reach "months"? |
| [Ticket to Prod](ticket-to-prod.html) | Pixel-art game about a delivery pipeline, with legends to hire | Is a game a better direction than a dashboard? |
| [Boxbot Depot](boxbot-depot.html) | Pixel-art game about robots moving boxes along pipes | Can queues, loops and defects be playful? |

Boxbot Depot is unrelated to the other two and may go its own way.

## Reading them

The numbers in these pages are mostly assumptions, and the games' effects are invented. Don't quote them as evidence.

Ticket to Prod is a snapshot, not the design. It plays as a factory and a checklist, which the design has since moved away from, and some of its cards describe a practice wrongly. For example, its TDD card promises half as many bugs, but TDD is a design practice rather than a test gate.

Its legends are parody. Each quote was checked against a source, or the card shows a book title instead, but the powers are made up.

## Adding one

Add one self-contained HTML file with a doctype and charset, and a row in the table above. Delete a prototype or split it out if it stops being one small file.
