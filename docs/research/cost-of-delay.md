# How can cost of delay be estimated in a way that survives scrutiny?

Research for issue #4. Cost of delay is the value lost because a ticket reached production later than it could have. It rests on an assumption about what the ticket is worth.

## Answer in brief

- Every published method turns a ticket's assumed value into a cost per unit of delay. None of them measures it. The estimate is only as good as the value assumption, and the sources agree the assumption is uncertain.
- Evidence strength is thin. The strongest peer-reviewed item found is a time-to-market model, not an estimation method. The only published case data found is one practitioner-written paper about one company. Most of what is repeated about cost of delay is folklore until traced to a source.
- What a sceptic can accept: state the cost of delay as a range with the assumption written next to it, built from the ticket's own benefit (revenue gained, cost removed), and always report it separately from elapsed time and labour cost. This matches the practice the Maersk paper describes (visible assumptions) and the project's standing preference for never summing the three measures.
- Internal and maintenance work is the weakest case. The practitioners say it can be estimated, usually by technical staff, but the sources read give no worked figures for it.

## Evidence tiers

Each claim below is tagged. "Read" means I read the page text. Nothing here comes from reading Reinertsen's books directly.

| Tier | Meaning in this note |
| --- | --- |
| Peer-reviewed | Journal or conference paper with review |
| Practitioner book | Book by a practitioner, not independently checked |
| Consultancy case study | Written by the consultants who ran the engagement |
| Folklore | Repeated widely, original not found or checked |

## What cost of delay is

The Black Swan Farming (Joshua Arnold's consultancy) page defines it as "the partial derivative of the total expected value with respect to time", and as a way of communicating the impact of time on outcomes. Wikipedia gives the units as value per unit of time, with the delay cost found by integrating over the period of delay. Sources: [Black Swan Farming, Cost of Delay](https://blackswanfarming.com/cost-of-delay) and [Wikipedia, Cost of delay](https://en.wikipedia.org/wiki/Cost_of_delay). Tier: consultancy and encyclopedia. Read.

This is the same definition the project uses. Note the shape matters: if value leaks at a constant rate, delay cost is rate times days late. If it does not, it is an integral.

## Reinertsen's work

- Reinertsen is quoted as saying "If you only quantify one thing, quantify the Cost of Delay." The quotation appears on the Scaled Agile page for weighted shortest job first, attributed to *The Principles of Product Development Flow*. Source: [SAFe, WSJF](https://framework.scaledagile.com/wsjf). Tier: practitioner book, second-hand quotation. Read.
- Wikipedia says Reinertsen reports that about 85% of product managers do not know their cost of delay, and that intuitive estimates spread by 50 to 1. Source: [Wikipedia, Cost of delay](https://en.wikipedia.org/wiki/Cost_of_delay). Tier: folklore until the original is found. **Not verified in the book.** Other pages found by search repeat 85%, one review gives 15% knowing, which is the same claim inverted; I did not verify either.
- Thomke and Reinertsen, "Six Myths of Product Development", Harvard Business Review, May 2012, vol. 90 no. 5, pp. 84-94. Bibliographic details come from a search listing ([EconBiz record](https://econbiz.de/Record/six-myths-of-product-development-thomke-stefan/10009549327)); only a preview of the article was readable ([O'Reilly copy](https://www.oreilly.com/library/view/hbrs-10-must/9781422191507/Text/12_Six_Myths_of_Product_Development.html)). I could not confirm what it says about estimating cost of delay. Tier: management journal, not an academic peer-reviewed estimation study.
- Reinertsen, *The Principles of Product Development Flow* (2009) is the main source for the idea. **I did not read it.** The questions of how it weights sensitivity analysis and its worked cost-of-delay tables are therefore unanswered here.

## Estimation methods found

### 1. Dollar benefit divided into urgency profiles (Black Swan Farming)

Arnold and Yüce describe estimating a dollar benefit for each requirement using four benefit "buckets", which the paper says "primarily consider the likely impact on revenue and costs". They then choose an urgency profile for how the value leaks away. Sources: [Arnold and Yüce, Black Swan Farming using Cost of Delay](https://blackswanfarming.com/black-swan-farming-using-cost-of-delay) (IEEE-format paper, 2013; Agile2013), and [Urgency Profiles](https://blackswanfarming.com/urgency-profiles/). Tier: consultancy case study. Read.

Profiles named on those pages: expedite, fixed date, standard (value grows steadily) and intangible. The paper says the most common profile at Maersk Line was "long life-cycle, peak unaffected by delay", typified by automating a process or cutting time or cost, and calls it "the easiest urgency profile for which to calculate the Cost of Delay" because it approximates a parallelogram.

Implication for the model: process-improvement and cost-reduction tickets are the easy case, and the paper says they were the most common.

### 2. Relative scoring (WSJF in SAFe)

SAFe estimates WSJF as "relative cost of delay divided by relative job duration", where cost of delay uses relative user and business value, time criticality, and risk reduction or opportunity enablement. Source: [SAFe, WSJF](https://framework.scaledagile.com/wsjf). Tier: practitioner framework. Read the introduction only; I did not read how the scoring scale is defined.

This ranks tickets. It does not produce a money figure, so it cannot feed a finance reader's cost of delay. It is useful only as a contrast.

### 3. Economic models of the time-to-market trade-off (peer-reviewed)

Cohen, Eliashberg and Ho, "New Product Development: The Performance and Time-to-Market Tradeoff", *Management Science* 42(2), 173-186, 1996. From the abstract as surfaced by search: a multistage model of the trade-off, where optimal timing depends on market size, margins, window of opportunity and competitor performance. Source: [Wharton copy of the paper](https://faculty.wharton.upenn.edu/wp-content/uploads/2013/04/New-Product-Development_1.pdf) (the PDF text would not extract, so I saw only the abstract through search results; the [EconPapers entry](https://econpapers.repec.org/RePEc:inm:ormnsc:v:42:y:1996:i:2:p:173-186) failed to load). Tier: peer-reviewed. **Not read in full.** It shows delay cost depends on market circumstances, which supports reporting ranges. I could not check how it models delay cost.

A search result for an academic paper (probably the NUS-hosted one, not confirmed to be this one) quotes a McKinsey finding that products six months late lose about 33% of after-tax profit, against 3.5% for overspending development by 50%. **Not verified**: I did not read the primary study, and search results gave conflicting versions (five years of profit, and 4% for overspend). Treat as folklore.

## Documented weaknesses

From the practitioners' own pages:

- **Estimates are uncertain.** Black Swan Farming says "we're looking for accuracy NOT precision", and that cost of delay is "a power law distribution, so Order of magnitude accuracy is better than nothing". Source: [CD3 and Cost of Delay puzzles](https://blackswanfarming.com/cd3-and-cost-of-delay-puzzles). Read. This is an admission that figures can be out by large factors.
- **Gaming.** The same page says that without transparency about how a figure was reached, "it becomes an easy thing for the system to game." The Maersk paper says its rule was to make assumptions visible, which "prevented blatant gaming", and that reliability improved over time through reviewing assumptions in weekly sessions. Source: [Arnold and Yüce](https://blackswanfarming.com/black-swan-farming-using-cost-of-delay). The improvement claim is the authors' own and no measurement of it was seen.
- **Who estimates.** Product owners facilitate and draw in finance, marketing and customer service. Source: [CD3 and Cost of Delay puzzles](https://blackswanfarming.com/cd3-and-cost-of-delay-puzzles).
- **Bias in value estimates.** Black Swan Farming cites civil engineering studies that put optimism bias on benefits at about 2%, against about 20% on duration and about 50% on cost, and says that is "difficult to measure". It then expects worse for product development. Source: [Estimation is hard, but worthwhile](https://blackswanfarming.com/why-making-value-estimates-is-hard-but-worthwhile/). Read the page; **I did not read the underlying civil engineering studies** it links. Do not carry the 2% figure into the model.
- **Duration critique.** Critics argue that duration is too uncertain to use, and the author replies that rough sorting is still useful. Source: [Challenges with Cost of Delay and CD3](https://blackswanfarming.com/challenges-with-cost-of-delay-and-cd3-wsjf-duration/). Partly read. The critics' own pages were not found, so their argument is seen only through the reply.
- **Independence.** Every source on estimation methods that I read was written by the people who sell the method. I found no independent critique or replication.

## Tickets with no direct revenue

- Black Swan Farming says value need not be monetary ("number of baby elephants saved"), but that, since people are paid in dollars, dollars are "typically a useful common currency". For tech debt, architecture and delivery-pipeline changes, technical people often estimate the cost of delay. Source: [CD3 and Cost of Delay puzzles](https://blackswanfarming.com/cd3-and-cost-of-delay-puzzles). Read.
- The urgency profiles page describes "intangible" work as the hardest to conceptualise, usually seen as low urgency in the short term, which may later become expedite. Source: [Urgency Profiles](https://blackswanfarming.com/urgency-profiles/), via a search summary of that page; I did not re-read the exact wording on the page.
- The Maersk paper's benefit buckets include cost reductions, for example a feature worth $4,000,000 a year in earlier cash from fewer late-paying customers plus a reduction in calls costing 5 full-time staff. The figures I saw were the inputs only; I did not capture the paper's final per-week result for that example. Source: [Arnold and Yüce](https://blackswanfarming.com/black-swan-farming-using-cost-of-delay).
- The paper also values "information discovery": what you would pay to learn earlier that something fails. Same source.

Gap: I found no published worked example putting a dollar cost of delay on pure maintenance or defect-fix work.

## Published case data

Only one source found: Maersk Line, a $100 million portfolio, described in the 2013 IEEE-format paper by Arnold and Yüce, who ran the engagement ([paper](https://blackswanfarming.com/black-swan-farming-using-cost-of-delay), [experience report](https://blackswanfarming.com/experience-report-maersk-line/)). Tier: consultancy case study. Read in part.

- A feature "spent 38 weeks in queues", had a cost of delay of "more than $200,000 per week", and so "cost the organisation nearly $8m in lost revenue". Source: [Black Swan Farming, Cost of Delay](https://blackswanfarming.com/cost-of-delay). The page gives no method for the $200,000, no audit, and says the estimate took "5 minutes". Treat as an illustration, not evidence. Arithmetic check: 38 x 200,000 = 7.6 million, consistent with "nearly $8m".
- Making changes to the central booking system took 373 days on average, and 1,856 requirements sat between drafting and development start. Source: [Arnold and Yüce](https://blackswanfarming.com/black-swan-farming-using-cost-of-delay). These describe queues, not cost of delay.

I did not find reported outcome data (for example, realised revenue against the estimates). The paper's results section was not retrieved in readable form.

Not found: any peer-reviewed empirical study estimating cost of delay for software tickets. A search for one returned work on schedule slippage (for example an ING case study in IEEE Transactions on Software Engineering, DOI 10.1109/TSE.2021.3101192, per a search summary) and preprints on project overruns, none of which measure the value lost.

## What a sceptical finance reader would accept

This is a judgement drawn from the sources, not a finding from one of them.

1. A figure built from an itemised benefit (revenue, cost saved) with each assumption written beside it, which is the practice described in the Maersk paper.
2. A range, not a point, since the practitioners themselves say order-of-magnitude accuracy is the realistic goal.
3. A label for each ticket's source of value, and a flag where the value is unmeasured, as with internal work.
4. The cost of delay kept separate from labour cost, so a weak value assumption cannot contaminate the two measures that rest on records.
5. No use of the 33%, 85% or 50-to-1 figures as evidence until their originals are found.

## Implications for the spec

- Cost of delay should be an input the user sets per ticket, as a rate with a range, with a default of "not assumed" rather than an invented number.
- The model needs the urgency profile (at least constant rate, fixed date, and no loss) because the shape changes the arithmetic. The "long life, peak unaffected" case reduces to rate times days late.
- Report evidence strength beside every cost-of-delay result, consistent with the map's standing preference.
- Sensitivity to the assumption should be shown, because it may hold most of the model's money.

## Open gaps

- Reinertsen's book was not read; its sensitivity guidance and any weaknesses he states are unchecked.
- The 85%, 50-to-1 and 33% figures are unverified.
- No independent critique or replication was found.
- No worked figures for maintenance or internal work.
- Cohen, Eliashberg and Ho were seen through an abstract only.
