# Evidence for how practices change the model's parameters

Research for issue #3. Retrieved 2026-11-05.

**Question.** For pair programming, ensemble programming, code review, test-driven development, static analysis and types, shift-left testing, test automation and work-in-progress limits, what does credible evidence say about their effect on duration, effort, defects added, detection and wait time?

## Short answer

- Only pair programming has a quantified, replicated body of evidence, and it is mixed: more effort, sometimes shorter duration, sometimes better correctness, depending on task complexity and expertise.
- For every other practice the published figures are weak (industrial case studies, surveys, one bug-injection study) or absent. Treat those parameters in the model as assumptions, show the range, and label them.
- Nothing found measures **wait time** for any practice, except a qualitative DORA claim about WIP limits.
- The "later fixes cost 100 times more" rule is not supported by the one large study that tested it, and the model should not use it as a default.
- There is no strong head-to-head comparison of pairing and code review. One small student experiment exists.

## How the evidence is graded

| Grade | Meaning |
| --- | --- |
| A | Meta-analysis or several controlled experiments |
| B | One controlled experiment with professionals |
| C | Controlled experiment with students, or large observational data |
| D | Industrial case study or survey |
| E | Experience report, vendor or practitioner claim |
| none | No figure found |

"Read" means I read the abstract or page text of the source in this session. Full texts were not readable for several papers (paywalled, or PDFs that would not convert), so figures below come from abstracts only. Anything I could not confirm is marked **unverified**.

## Findings by practice

### Pair programming

| Effect | Evidence | Grade | Who was studied |
| --- | --- | --- | --- |
| Quality (defects added) | Small significant positive effect overall. | A | Published pair-versus-solo experiments, mostly students |
| Duration | Medium significant positive effect (pairs finish sooner) overall. | A | As above |
| Effort | Medium significant negative effect (pairs use more person-hours). | A | As above |
| Moderators | Faster when task complexity is low, but with noticeably lower quality. Higher quality when complexity is high, at considerably greater effort. | A | As above |

Source: Hannay, Dybå, Arisholm and Sjøberg 2009, ["The effectiveness of pair programming: A meta-analysis"](https://ebse.webspace.durham.ac.uk/ebse-bibliography/the-effectiveness-of-pair-programming-a-meta-analysis/) (Information and Software Technology 51(7); abstract read at the Durham EBSE bibliography, DOI [10.1016/j.infsof.2009.02.001](http://dx.doi.org/10.1016/j.infsof.2009.02.001)). The abstract gives effect-size labels only, not numbers. It also reports significant between-study variance and signs of publication bias.

Professional-developer experiment: Arisholm, Gallis, Dybå and Sjøberg 2007, "Evaluating Pair Programming with Respect to System Complexity and Programmer Expertise" (IEEE TSE 33(2); abstract read via the [Semantic Scholar API record](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1109/TSE.2007.17?fields=title,abstract,year,venue), DOI 10.1109/TSE.2007.17). Grade B. 295 professional Java consultants (99 individuals, 98 pairs) from 29 companies, one day, change tasks on two Java systems. Findings from the abstract:

- No support for pairing reducing the time to solve the tasks correctly, or raising the proportion of correct solutions, in general.
- A significant 84 percent increase in effort to perform the tasks correctly.
- On the more complex system, a 48 percent increase in the proportion of correct solutions, with no significant difference in time.
- On the simpler system, a 20 percent decrease in time, with no significant difference in correctness.
- The correctness benefit applied mainly to juniors; the time reduction mainly to intermediates and seniors.

The authors note that benefits may exceed these results for larger, longer tasks (abstract text, truncated in the copy I read). The tasks lasted at most one day, so the figures say nothing about long-run effects.

Candidate check: both papers are real and correctly attributed. Hannay et al. 2009 and Arisholm et al. 2007 share authors, so they are not independent confirmation of each other, although the meta-analysis is the wider evidence.

Model use: the pairing parameters are moderated by task complexity and developer experience. A scenario that applies one fixed effort multiplier and one fixed defect reduction overstates the evidence. The 84 percent effort figure is one experiment; the meta-analysis only says "medium".

### Ensemble (mob) programming

No quantitative effect on duration, effort, defects or wait time found. Grade E at best.

- Buchan and Pearl, ["Leveraging the Mob Mentality: An Experience Report on Mob Programming"](https://arxiv.org/abs/1907.11352) (arXiv 1907.11352, 2019). One team over 18 months in a financial services product organisation, plus a preliminary survey of 82 mob programming practitioners. The abstract says it is "not clear if these are realized in practice and under what circumstances" for the claimed benefits. No measured effect sizes in the abstract.
- A web search for systematic reviews returned only secondary summaries, which described the literature as experience reports and small case studies. I did not read a review myself. **Unverified.**

Model use: ensemble programming has no credible figure. Any scenario that includes it must mark all its parameters as assumptions.

### Code review

| Effect | Evidence | Grade | Who was studied |
| --- | --- | --- | --- |
| Share of review findings that are functional defects | About 75 percent of defects found in code reviews affect evolvability rather than functionality. | D | Industrial and student code reviews |
| Motivation versus outcome | Finding defects is the main motivation, but reviews are "less about defects than expected"; knowledge transfer, team awareness and alternative solutions are also outcomes. | D | Microsoft teams, interviews, survey and classified comments |
| Scale and process at Google | 12 interviews, a 44-respondent survey and review logs for 9 million reviewed changes were analysed. | D | Google engineers |
| Wait time and duration | No figure verified. | none | |
| Defects added or detection rate | No figure verified for the modern, tool-based practice. | none | |

Sources:

- Mäntylä and Lassenius 2009, "What types of defects are really discovered in code reviews?" (IEEE TSE 35(3)). Read the author's own summary at [mmantyla.github.io](https://mmantyla.github.io/wiki/What+Types+of+Defects+Are+Really+Discovered+in+Code+Reviews%253F.html): "75% of defects found in code reviews affect software evolvability rather than functionality" and "over 700 issues". A web-search summary gave 388 industrial and 371 student defects from nine industrial and 23 student reviews. That split is **unverified** (not read in a source I fetched). The candidate DOI I tried (10.1109/TSE.2009.4) points to a different paper, so cite by title.
- Bacchelli and Bird 2013, ["Expectations, Outcomes, and Challenges of Modern Code Review"](https://www.microsoft.com/en-us/research/publication/expectations-outcomes-and-challenges-of-modern-code-review/) (ICSE 2013). Abstract read. Observation, interviews, a survey, and manual classification of hundreds of review comments at Microsoft.
- Sadowski et al. 2018, ["Modern Code Review: A Case Study at Google"](https://research.google/pubs/modern-code-review-a-case-study-at-google/) (ICSE-SEIP 2018). Abstract read. A secondary source quoted a median review latency under four hours and a median of one approver. I could not confirm these in the paper, so they are **unverified** and not used here.
- Fagan 1976, "Design and code inspections to reduce errors in program development" (IBM Systems Journal 15(3), DOI 10.1147/sj.153.0182). The abstract, as quoted in a bibliographic record found by search, reports "substantial net improvements in programming quality and productivity". I could not read the paper's data tables, and a glossary site's "60 to 90 percent of defects removed" and "23 percent productivity gain" are **unverified**. Fagan inspections are formal, meeting-based inspections from IBM in the 1970s. They differ from today's tool-based review, and the paper is an industrial report (grade D/E).

Candidate check: Mäntylä, Bacchelli and Bird, Sadowski and Fagan are real and correctly attributed. None gives a defect-detection rate or a wait time that can be dropped into the model. The model's review gate detection rate therefore has no credible published default from these sources.

### Pairing versus code review, head to head

One experiment, no more. Müller 2005, ["Two controlled experiments concerning the comparison of pair programming to peer review"](https://ps.ipd.kit.edu/english/399_911.php) (Journal of Systems and Software 78; abstract read on the KIT page). Two controlled experiments in 2002 and 2003 with 38 computer science students at Karlsruhe, comparing pairs with single developers followed by an anonymous peer review phase. Finding: single developers are as costly as pairs "if both ... are forced to produce programs of similar level of correctness", so the two become interchangeable in development cost. The author notes the tasks were small and long-term benefits were not measured.

Grade C, students, small tasks. This is not a strong head-to-head comparison. I found no comparison with professionals and no replication. The model should treat "pairing replaces review" as an assumption.

### Test-driven development

| Effect | Evidence | Grade | Who was studied |
| --- | --- | --- | --- |
| Defects added (pre-release defect density) | Decreased 40 to 90 percent relative to similar non-TDD projects. | D | Three Microsoft teams and one IBM team |
| Duration of initial development | Teams subjectively experienced a 15 to 35 percent increase. | D (subjective) | As above |
| Test-first sequencing itself | No important influence found; granularity and uniformity of steps were associated with better quality and productivity. | C | 82 data points from 39 professionals |

Sources:

- Nagappan, Maximilien, Bhat and Williams 2008, "Realizing quality improvement through test driven development: results and experiences of four industrial teams" (Empirical Software Engineering 13(3), DOI [10.1007/s10664-008-9062-z](https://doi.org/10.1007/s10664-008-9062-z)). The abstract is quoted in the [It Will Never Work in Theory review](https://neverworkintheory.org/2012/01/25/realizing-quality-improvement-through-test-driven-development.html), which I read. Case studies, not controlled experiments, and the comparison projects were "similar", not randomised. The time figure is subjective.
- Fucci et al. 2016, ["A dissection of the test-driven development process"](https://oa.upm.es/50842/) (IEEE TSE; abstract read). The conclusion says the claimed benefits "may not be due to its distinctive test-first dynamic, but rather due to the fact that TDD-like processes encourage fine-grained, steady steps". Quality was measured as functional correctness on a development task.

Candidate check: Nagappan et al. and Fucci et al. are real and correctly cited. The 40 to 90 percent range is a wide, uncontrolled industrial range; the model should carry it as a range with a grade D label, not as a point value. Model use: the TDD effect on duration is a subjective team estimate, so it is weak.

### Static analysis and types

| Effect | Evidence | Grade | Who was studied |
| --- | --- | --- | --- |
| Share of bugs a type checker would catch | About 15 percent of the sampled JavaScript bugs. | D/C | Bugs from public JavaScript projects |
| Value of automated static analysis for fault detection | Described as an "affordable means of software fault detection", effective on assignment and checking faults. No figure read. | D | Three Nortel Networks systems |

Sources:

- Gao, Bird and Barr 2017, "To type or not to type: quantifying detectable bugs in JavaScript" (ICSE 2017). I did not read the abstract. The [It Will Never Work in Theory review](https://neverworkintheory.org/2021/09/08/to-type-or-not-to-type.html) says static typing would have caught the error "in 15% of cases". Search summaries gave 400 sampled bugs, with 59 detected by Flow and 58 by TypeScript, and a confidence interval of 11.5 to 18.5 percent. Those counts are **unverified**. The authors' own point, as relayed by search summaries, is that bugs which survived testing and review make the 15 percent conservative. That is also **unverified**.
- Zheng, Williams, Nagappan, Snipes, Hudepohl and Vouk 2006, "On the value of static analysis for fault detection in software" (IEEE TSE 32(4); abstract partly read in a [library catalogue record](https://manuscript.isc.ac/Inventory/49/926913.htm), truncated). The abstract gives no numbers in the part I read.

Candidate check: Gao et al. 2017 is real, but it measures the share of bugs that were still in committed code, not detection at a gate with a cost. It has no effect on duration, effort or wait time. Note the review's caveat that the study does not tell us whether typing is cost-effective.

### Shift-left testing

No credible figure found. The usual justification is that later fixes cost more, which is addressed next.

**The cost-to-fix claim.** Menzies, Nichols, Shull and Layman 2016, ["Are Delayed Issues Harder to Resolve? Revisiting Cost-to-Fix of Defects throughout the Lifecycle"](https://arxiv.org/abs/1609.04886) (arXiv 1609.04886; Empirical Software Engineering). Abstract read. They tested the "delayed issue effect" in 171 software projects from 2006 to 2014 and "found no evidence for the delayed issue effect; i.e. the effort to resolve issues in a later phase was not consistently or substantially greater than when issues were resolved soon after their introduction." The abstract adds that the effect is not constant across projects. The projects came from the Team Software Process (TSP) at the Software Engineering Institute, whose teams use personal reviews and peer inspections, so the data come from a disciplined process and may not generalise.

Candidate check: the candidate wording, "Menzies et al. 2016 on the claim that later fixes cost 100 times more", is **corrected**. The paper does not give a 100-times figure. It tests the earlier belief, defined by reference to Boehm 1981, and finds it unsupported in its data. I did not read Boehm's original figures, so I make no statement about them. The model should not default to a multiplier for late detection. Make "cost to fix by phase" a scenario parameter, with TSP-like data as one input and a clear label that the data come from TSP teams.

### Test automation

No numeric effect found. DORA's [test automation capability page](https://dora.dev/capabilities/test-automation/) says its research shows automated test suites drive "improved software stability, reduced team burnout, and lower deployment pain". It also recommends test suites that give developer feedback in under ten minutes. The page gives no effect size, population or method. Grade E for the claim as read (DORA's underlying studies are surveys, see below).

### Work-in-progress limits (and wait time)

No figure found. DORA's [WIP limits page](https://dora.dev/capabilities/wip-limits/) says its research "shows that WIP limits help drive improvements in software delivery performance, particularly when they are combined with" other practices (the sentence was truncated in the text I read). No effect size, no wait-time figure, no population. Grade E. The queueing mechanism (fewer items in progress means less waiting) is a property of the model itself, so a WIP scenario should be derived from the simulated queues rather than from a published number.

### DORA and Accelerate

Candidate check: real, but I did not read the book or a DORA report's methods section. Search results described a multi-year, survey-based programme with statistical analysis, which makes it grade D for any single practice. The model should not take DORA's findings as per-practice effect sizes on duration, effort, defects or wait time. I have not verified the survey sizes quoted in vendor blogs, so none are used here.

## Summary table for the model

| Practice | Duration | Effort | Defects added | Detection | Wait time |
| --- | --- | --- | --- | --- | --- |
| Pair programming | A, qualitative; B, -20% simple task | A, qualitative; B, +84% | A, small positive; B, +48% correct on complex task | none | none |
| Ensemble programming | none | none | none | none | none |
| Code review | none | none | none | D, 75% of findings are evolvability | none |
| Test-driven development | D, +15-35% (subjective) | none | D, -40 to -90% | none | none |
| Static analysis and types | none | none | none | D, about 15% of sampled bugs (types) | none |
| Shift-left testing | none | none | none | none | none |
| Test automation | none | none | none | none | none |
| WIP limits | none | none | none | none | E, qualitative only |

Cells say "none" where I found no credible figure.

## Effects with no credible figure

- Any effect of ensemble programming.
- Defect-detection rate or wait time for code review.
- Shift-left testing in any form.
- Numeric effect of test automation, WIP limits or static analysis on duration, effort or wait time.
- Detection rates for any gate from published data. The only "detection" numbers are shares of defects found by a technique (75 percent evolvability, 15 percent type-detectable), which are not rates of detection per defect present.
- Any head-to-head pairing versus review comparison with professionals.

## What I could not verify

- Full texts of Mäntylä and Lassenius, Sadowski et al., Fagan, Gao et al. and Zheng et al.; only abstracts or secondary summaries were read.
- Sadowski et al. latency, reviewer-count and change-size figures.
- Fagan's "60 to 90 percent" and "23 percent" figures.
- Gao et al. bug counts and confidence interval.
- Reviews of ensemble programming evidence.
- Accelerate book methodology and sample sizes.
- Boehm 1981 original data.

## Standing limits on all the figures

Most studies measure small tasks over hours or days, many with students, and few measure wait time, which is the model's main concern. The model's own scenarios should show ranges and the grade beside each parameter.
