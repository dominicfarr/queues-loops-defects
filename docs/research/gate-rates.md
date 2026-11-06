# Published rates for defects, detection and rejection at each gate

Research for issue #2. Evidence grades used here:

- **Peer-reviewed**: published in a refereed venue.
- **Vendor / consultancy**: a commercial firm's own report; method and data not open to inspection.
- **Folklore**: widely repeated, no source found that I could read.

"Read" means I read the quoted text on the linked page. Where I could only see a figure quoted by a later paper, it is marked **secondary**. Several publisher PDFs could not be read here, so only abstracts or author summaries were checked; this is stated per item.

## Summary

| Gate | Defect rate per ticket | Detection rate | Rejection rate (all causes) | Rejection with no defect |
| --- | --- | --- | --- | --- |
| Code review | No credible figure | Median 30% of defects (mean 34%, range 8.5% to 92.7%), mostly inspection studies | 16% of pull requests not merged (open source, 2014) | Most review findings are not functional defects (about 75%, evolvability) |
| Merge | No credible figure | Not applicable | 10% to 20% of merges conflict (cited by Ghiotto et al.; original source not read) | All merge conflicts are no-defect rejections |
| Testing | No credible figure per ticket; per function point only from a vendor | Mean about 50% per technique (range 7% to 89%) | No credible figure | No credible figure |
| Security testing | No credible figure | One static analysis tool warned in vulnerable functions for 52% of vulnerability-contributing commits | No credible figure | No credible figure |
| Performance testing | No credible figure | No credible figure | No credible figure | No credible figure |

The headline finding is negative: published figures exist for detection effectiveness of techniques, and for pull request merge outcomes in open source, but none that map a ticket to "carries a defect", "gate rejects it" at each gate of the article's process. The model will need to treat most of its defaults as assumptions and show them as such.

## Code review

### Detection

**Median 30% of defects found by inspection and review techniques (peer-reviewed survey, aggregating older studies).**
Wagner's survey of empirical studies reports the effectiveness of inspection techniques as lowest 8.5%, mean 34.14%, median 30%, highest 92.7%. The author notes the range is huge and "an inspection is dependent on other factors to be effective." Population: pooled experiments and case studies from several decades, mostly formal inspections, not modern pull-request review. Read the arXiv HTML version in full text for this table. Strength: moderate for the central figure, weak for transfer to modern review.
Source: Wagner, "A literature survey of the quality economics of defect-detection techniques", https://arxiv.org/abs/1612.04590 (table 7 at https://arxiv.org/html/1612.04590v1).

**Most defects found in review are not functional (peer-reviewed).**
Mäntylä and Lassenius (IEEE TSE 2009) classified issues found in code reviews. The author's own summary page says 75% of defects found in code reviews affect software evolvability rather than functionality, from over 700 issues. A search summary described the data as nine industrial C/C++ reviews and 23 student Java reviews (388 and 371 defects); I did not read that breakdown in the paper itself. The same summary said Beller et al. (2014) found a similar 75:25 split in two open-source projects; **secondary, not verified**. Strength: peer-reviewed, small and partly student-based; direction is consistent across replications.
Source: https://mmantyla.github.io/wiki/What+Types+of+Defects+Are+Really+Discovered+in+Code+Reviews%253F.html

**Review often does not find functional problems that block a change (Microsoft, peer-reviewed practitioner paper).**
Czerwonka and Greiler (ICSE 2015) argue from Microsoft data that code reviews often do not find functionality issues that should block a submission. I read only the abstract; it gives no rate. The PDF could not be read here.
Source: https://www.microsoft.com/en-us/research/publication/code-reviews-do-not-find-bugs-how-the-current-code-review-best-practice-slows-us-down/

**About 34.5% of Microsoft review comments were "not useful" (peer-reviewed, secondary).**
Bosu, Greiler and Bird (MSR 2015) analysed review comments at Microsoft. The 34.5% figure was quoted via a 2023 survey by Ahmed et al., found through search; I did not read the original text or confirm the survey's wording. "Not useful" is not the same as "no defect". Treat as **unverified** until the original is checked.
Related: https://ar5iv.labs.arxiv.org/html/2307.00692

### Rejection

**84% of pull requests merged, 16% not merged (peer-reviewed, open source, 2014).**
Gousios, Pinzger and van Deursen (ICSE 2014) studied pull-based development on GitHub. The 84%/16% split is on the author's own presentation slide (slide 21), alongside time to merge: 34% within an hour, 35% within a day, 31% longer. Population: GHTorrent corpus and 291 selected projects. The slide's rejection-reason chart lists categories (done by others better, project heading elsewhere, incorrect process, incorrect implementation, tests failed, and others) but the extracted text does not tie each percentage to its category, so I do not report the individual reason shares. The abstract, as summarised in a search result, says technical reasons are a small minority of rejections; **secondary**. The ACM and TU Delft paper text could not be read.
Sources: https://speakerdeck.com/player/2c6de050ce430131e1db2aa9d004a740 ; paper listing https://bibtex.github.io/ICSE-2014-GousiosPD.html
Caveat: open-source pull requests from outside contributors are a poor proxy for tickets reviewed inside a company team.

No credible figure found for: the share of tickets that a company team's reviewers send back, the share of sent-back tickets with no defect (style objections), or reviewer miss rates on real modern review.

## Merge

**10% to 20% of merge attempts produce a conflict (peer-reviewed, cited).**
Ghiotto et al. (IEEE TSE 2020) study 2,731 open-source Java projects. Their abstract says "it has been reported that as much as 10 to 20 percent of all merge attempts result in a merge conflict", with some projects almost 50% in the introduction as quoted by the reviewer. That range is quoted from earlier work I did not read; the paper's own measured rate was not found in what I read. I could not confirm a specific 19.3% figure that appeared in one query and do not use it. Strength: weak-to-moderate; the rate is for textual conflicts in open source and varies widely by project.
Same paper: of 616 conflicting chunks studied manually, 19% needed new code to resolve and 81% were resolved from existing chunk content.
Source: https://neverworkintheory.org/2021/08/12/on-the-nature-of-merge-conflicts.html (quotes the paper; DOI 10.1109/TSE.2018.2871083)

A merge conflict carries no defect, so each is a rejection with no defect in the project's terms. No credible figure found for conflict rate against ticket age or work in progress, which is what the model needs to make this emerge from load.

## Testing

**Mean about 50% detection per test technique (peer-reviewed survey).**
Wagner's survey, effectiveness of test techniques in percent: functional lowest 33, mean 53.26, median 48.85, highest 88; structural 17, 54.78, 56.85, 89; all techniques 7.2, 49.85, 47, 89. The definition is the share of seeded or known defects a technique finds in the study's setup, so it overstates what a real test suite finds in real tickets. Source: https://arxiv.org/html/1612.04590v1

**Defect potential about 4.95 defects per function point, US average circa 2015 (vendor / consultancy).**
Capers Jones (Namcook Analytics): requirements 1.00, architecture 0.30, design 1.15, code 1.35, security code flaws 0.25, documents 0.50, bad fixes 0.40. Range from under 2 for top teams to over 6 for inexperienced teams. These are per function point, not per ticket, and include non-code defects; the method and data are not open. The same article says a typical US sequence (static analysis then six kinds of testing, including performance test) reaches about 95% cumulative removal, and that inspections can lift it past 99%. A per-stage removal table is in the article but I could not extract it, so no per-stage figure is quoted from it. Strength: vendor report, widely repeated, treat as folklore-grade for tickets.
Source: https://www.cioreview.com/leadership-perspectives/high-efficiency-defect-removal-for-software-projects-nid-21702-cid-121.html

No credible figure found for: the share of tickets that carry a defect on entering test, or the rate at which testing sends back tickets in a team's flow (test failure with no real defect, such as environment or flaky tests, included).

## Security testing

**One static analysis tool warned in vulnerable functions for 52% of vulnerability-contributing commits (peer-reviewed, ISSTA 2024).**
Charoenwet et al.: 319 real vulnerabilities from 815 vulnerability-contributing commits in 92 C/C++ projects. At least 76% of warnings in vulnerable functions were irrelevant to the vulnerability, and 22% of commits remained undetected due to rule limitations. Read from the abstract. Population: C/C++ open source, static analysis only, not penetration testing. Strength: good for its population. Source: https://arxiv.org/abs/2407.12241

No credible figure found for: the share of tickets that carry a security flaw, detection by dynamic or manual security testing, or rejection rate of security gates.

## Performance testing

No credible figure found for defect rate, detection rate or rejection rate. The only quantity found is Jones's inclusion of performance test in a typical test sequence (above), with no separate rate.

## Implications for the model

1. Use the figures above only as named, graded defaults, with ranges: review detection 30% (range 8.5% to 92.7%), test detection about 50% (range 7% to 89%), pull request non-merge 16%, merge conflict 10% to 20%.
2. Per-ticket defect probability, performance-test detection and every no-defect rejection rate other than merge conflicts have no credible published figure. Mark them as assumptions and make them the first parameters a team replaces from its tracker history.
3. The 75% non-functional share of review findings supports counting review rejections mostly as no-defect, which the map already expects.

## Not verified

- Beller et al. 2014 75:25 split, the Bosu 34.5% figure, and the Gousios abstract's "technical reasons are a small minority" are known only through secondary summaries.
- Publisher PDFs (Czerwonka, Gousios, Beller, Bosu) could not be opened; only abstracts or author pages were read.
