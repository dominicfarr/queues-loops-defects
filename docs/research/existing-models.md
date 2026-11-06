# Has someone already modelled this, and what can we reuse?

Research for issue #5, a child of the map (#1). Researched 2026-11-05. Everything below was read at the linked source unless it is marked **unverified**.

## Short answer

No tool or paper found models what the map's destination describes: simulated tickets that cross policy waits and load waits, pass gates that can miss defects, loop back on rejection, and report elapsed time, labour cost and cost of delay as separate measures. Three kinds of work each cover part of it.

- **Software process simulation research** is the nearest academic match, but I could only read abstracts and bibliographic records, not the papers.
- **Flow forecasting tools** replay historical throughput. They do not simulate queues, gates or loops from capacity.
- **Queueing results** (Little's law, Kingman's formula) give a way to sanity-check the simulation. They are not a model of the process.

The best things to reuse are a general-purpose discrete-event library, SimPy, and the two formulas as credibility checks. "No existing model found" is a statement about my search, which was narrow (see Limits).

## The article's own model (the target to reproduce)

Source: [Faster and More Predictable](https://www.industriallogic.com/blog/faster-and-more-predictable/), read in full.

- Totals: a bit over 10 working days with a 5-day start wait, 2 days of work, a 3-day review wait and an hour of inspection. About 25 days once security and performance testing add 4 days each. These match the map's 10, 17 and 25.
- Twice-as-fast developer gives 24 days and twice-as-slow gives 27, as the map says.
- Loops: returned work re-enters the development queue, waits for prioritisation, then rejoins the review queue (another 3 days on average). The article says rework may itself be rejected, and that loops nest through review, merge and testing. It gives no rates.
- The article describes waits as averages. It contains no simulation, no formulas and no cost figures.

## Candidates

| Candidate | What it models | Time and money? | Reuse or learn | Leaves out versus the destination |
|---|---|---|---|---|
| Software process simulation research (Kellner, Madachy and Raffo 1999; Zhang, Kitchenham and Pfahl 2008 and 2010) | Simulation of software processes for strategic management, process improvement and training. Paradigms include system dynamics, discrete event and hybrid. | Unverified. I read only abstracts. | Learn from. Use the 2010 review's 156 studies as a map of prior work. Unverified whether any covers review queues with rejection loops. | Unverified from abstracts alone. |
| SimPy | A process-based discrete-event simulation framework in Python, with shared resources for capacity-limited points. | No. It is a library with no domain model. | Reuse. Capacity and queueing come built in. | Every domain element: gates, defects, loops, cost. |
| Lighthouse (LetPeopleWork) | Flow metrics and Monte Carlo "how many" and "when" forecasts, applied to a team's historical throughput. | Time only. No labour cost or cost of delay found in the README. | Learn from. Do not reuse code (licence, below). | It resamples past throughput. It does not model queues, capacity, gates or defects. |
| Focused Objective resources (Troy Magennis) | A repository of spreadsheets, a "SimML Reference" and forecasting material for software projects. | Unverified. I read only the file listing and README. | Learn from. | Unverified. Not read in depth. |
| Little's law | L = λW for a stationary system. | n/a | Reuse as a check. | A relation between averages. It says nothing about gates or loops. |
| Kingman's formula | Approximates mean wait in a G/G/1 queue from utilisation, variability and service time. | n/a | Reuse as a check on load waits. | One queue only. No loops, no defects. |

### Software process simulation research

- [Reflections on 10 Years of Software Process Simulation Modeling: a Systematic Review](https://www.simula.no/research/reflections-10-years-software-process-simulation-modeling-systematic-review) (Zhang, Kitchenham and Pfahl, ICSP 2008). The search snippet says it found the 1999 classification needed refinement and that hybrid models, built mainly on system dynamics and discrete event simulation, attracted interest.
- [Software Process Simulation Modeling: An Extended Systematic Review](https://researchrepository.ul.ie/articles/conference_contribution/Software_process_simulation_modeling_an_extended_systematic_review/19848253) (ICSP 2010, LNCS 6195, pp. 309-320). Its abstract reports 156 relevant studies in four categories and says the work was dominated by the ProSim/ICSP community.
- Kellner, Madachy and Raffo, "Software process simulation modeling: Why? What? How?", Journal of Systems and Software 46, 1999, DOI 10.1016/s0164-1212(99)00003-5. The publisher page refused my fetch (HTTP 403), so I know it only through search records: it covers strategic management, process improvement and training, and ends with advice on choosing an approach and open research questions.
- Licence and maintenance: these are papers, so neither applies. Whether any associated models are published is **unverified**.
- Not done: I did not read any paper body, so I cannot say whether any study models review queues, rejection loops, capacity-driven waits or cost of delay. A later pass should open the 2010 review's full text and its list of studies.

### SimPy

- Source: [SimPy documentation](https://simpy.readthedocs.io/en/latest/). It is a process-based discrete-event framework in standard Python. Processes are generator functions and can model customers or agents. Shared resources model "limited capacity congestion points". Runs can go as fast as possible, in real time, or step by step.
- Licence: MIT, per the [PyPI metadata](https://pypi.org/pypi/simpy/json) (version 4.1.2, uploaded 2026-05-24).
- Maintained: a 4.1.2 release in May 2026 is the only evidence I read. I did not check the issue tracker.
- Caveat: this only matters if the project picks Python. The stack ticket decides that. The same capacity-and-queue pattern is simple in any language, so the transferable value is the approach.

### Lighthouse

- Source: [README](https://raw.githubusercontent.com/LetPeopleWork/Lighthouse/main/README.md). It applies Monte Carlo simulation to historical throughput to predict delivery dates. It offers WIP, throughput, cycle time and work-item-age views, plus Jira, Azure DevOps, CSV and Linear (preview) integrations.
- **Licence: not open source.** A web-search summary called it MIT, and that is wrong for current code. The [LICENSE file](https://raw.githubusercontent.com/LetPeopleWork/Lighthouse/main/LICENSE) says releases up to v26.9.9.9 (9 September 2026) stay MIT, and later source is under a "source available" licence built from additional terms plus Elastic License 2.0. I did not read the terms in full, so I cannot say what use is allowed. Treat the current code as not reusable without legal review.
- Maintained: GitHub shows a push on 2026-11-05, so yes.
- Relevance: it supports the map's idea of calibrating from tracker history later. It does not serve the simulation itself.

### Focused Objective resources

- Source: [repository README](https://github.com/FocusedObjective/FocusedObjective.Resources). It describes "various resources related to forecasting and modelling software projects", mostly spreadsheets, and includes a "Skill and Dependency Planner" for finding constraints from over-allocated skills.
- Licence: none found. The repository root lists no LICENSE file (GitHub API contents listing), so treat the contents as all rights reserved.
- Maintained: last push 2022-04-26, so dormant.
- I did not open the spreadsheets or the SimML reference.

### Queueing results

- [Little's law](https://en.wikipedia.org/wiki/Little%27s_law): the long-term average number in a stationary system equals the average effective arrival rate times the average time in the system. The page says the relation does not depend on the arrival process, service distribution or service order.
- [Kingman's formula](https://en.wikipedia.org/wiki/Kingman%27s_formula): E(Wq) ≈ (ρ/(1−ρ)) · ((ca² + cs²)/2) · τ for a G/G/1 queue, first published by Kingman in 1961. The page calls it generally very accurate close to saturation.
- Both citations are to Wikipedia, a secondary source. The original papers (Little 1961, Operations Research 9(3); Kingman 1961) were behind publisher blocks (HTTP 403) and I did not read them.
- Use in the model, as my inference rather than a source claim: Little's law can check that simulated work in progress, throughput and elapsed time agree. Kingman's formula predicts that load waits rise steeply as utilisation approaches 1 and grow with variability. The simulation's load waits should show that shape. The formula holds for a single queue and does not describe loops.

## What is left for this project to build

Based on what I found, nothing read covers these, so the spec must define them itself:

1. Policy waits and load waits together on one ticket.
2. Gates with a miss rate, and rejection loops that follow from defect and detection rates.
3. Rejections without a defect (style, merge conflicts).
4. Elapsed time, labour cost and cost of delay reported separately.
5. Reproducing the article's 10, 17 and 25 days with loops off.

## Limits of this research

- Search was narrow: two web searches for academic work and one for flow tools, plus GitHub searches for "kanban simulation". Names such as Reinertsen's work, agent-based software process studies, commercial simulators and GitHub kanban simulators were not examined. A GitHub search returned several small kanban-simulation repositories (for example `seize-the-dave/get-kanban-simulation`, Apache-2.0, last pushed 2021). These are board-game or teaching simulators. I did not open them.
- No academic paper was read beyond an abstract or record.
- Wikipedia stood in for the primary queueing papers.
