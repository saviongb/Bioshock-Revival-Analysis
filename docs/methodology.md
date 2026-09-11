# Methodology

## Data collection

Reviews were collected from the Steam review API on 15 July 2026 for three titles:
BioShock Remastered (app ID 409710), BioShock 2 Remastered (app ID 409720), and BioShock Infinite (app ID 8870). The endpoint returns up to 100 reviews per
request along with a cursor marking the position reached, which is passed on the
following request to advance a page. Collection continues until the API returns an empty result.

## Corpus

| Title | Reviews | Positive |
| BioShock Remastered | 26,155 | 82.0% |
| BioShock 2 Remastered | 12,008 | 71.0% |
| BioShock Infinite | 47,232 | 91.1% |
| **Total** | **85,395** | |

All figures in this analysis describe reviewers and the content of their reviews. They do not necessarily describe the player base.

## Processing

Raw API responses were stored unmodified before any filtering, so later stages can be
run without a second collection. Reviewer fields were flattened into
individual columns.

Three fields were derived:

- **Era** 
- **Playtime segment** - playtime at time of review, banded as brief (under 2h),
  moderate (2–12h), and extended (12h and above). Playtime at review is used rather
  than lifetime playtime, which can continue to increase after a review is posted.
- **Recent window** - reviews posted on or after 26 July 2025. This window ends at the
  15 July 2026 pull date and therefore spans slightly under twelve months.

## Theme detection

Nine themes were defined as keyword dictionaries: narrative, setting, atmosphere,
characters, combat, ideology, visual_audio, technical, and pacing. Each review is
matched against each dictionary and recorded as either mentioning or not mentioning
each theme.

Matching is case-insensitive and bounded to whole words and phrases. Detection records presence only, not frequency: a review mentioning a theme
once and a review mentioning it repeatedly are recorded identically.

Salience is the share of a given group's reviews that mention a theme. Figures are
read within their group - "of BioShock 2's reviews, 40.3% mention technical" - and
the denominator changes with the grouping. Verdict, era, and playtime tables report
shares of that subgroup, not of the full corpus.

## Dictionary validation

A sample of 72 randomly selected reviews was hand coded against all nine themes to
measure how accurately the dictionaries identify keywords within reviews. Precision is
the share of flagged reviews that discuss the theme. Recall is the share of discussions the dictionary flags.

| Theme | Terms | Precision | Recall |
| narrative | 25 | .87 | .93 |
| technical | 21 | .91 | .58 |
| combat | 19 | 1.00 | .57 |
| setting | 23 | .80 | .50 |
| pacing | 10 | .50 | .40 |
| visual_audio | 8 | .75 | .25 |
| characters | 36 | .80 | .67 |
| atmosphere | 12 | 1.0 | .33 |
| ideology | 24 | .50 | .50 |

## Theme limitations

**Narrative** is the best validated theme, with high precision and the highest recall
recorded. Findings resting on narrative salience are the most consistent in the analysis.

**Technical** shows high precision at .91 but recall of .58, meaning roughly four in
ten technical discussions go uncounted. This undercount strengthens rather than
weakens the finding that negative reviews of the remasters are largely a performance
problem.

**Combat** records perfect precision across the sample, with no observed contamination
from ambiguous terms. Recall of .57 means the dictionary
undercounts.

**Pacing** is the weakest validated theme, at .50 precision and .40 recall on only five
positive cases. The sample is too small to characterize performance with confidence.

**Setting** and **visual_audio** undercount substantially, at .50 and .25 recall. Ultimately not used in the analysis

**Ideology** appeared in two reviews in the sample, not enough to measure precision or
recall. No claim is made about instrument performance for this theme. The low
validation count is consistent with the low salience recorded in the full corpus.

## Consequences for reported figures

**All salience figures are floors.** Detection records presence rather than frequency,
and only listed terms can be found, so true discussion rates are higher than reported
in every case.

**Same-theme comparisons are robust.** Comparing one theme across titles, eras, or
verdict groups uses an identical instrument in each case. Whatever a dictionary misses,
it misses consistently.

**Cross theme comparisons are weak.** A 36-term dictionary and an 8-term dictionary do
not measure well alongside eachother.

**Grouped figures describe different populations.** Playtime bands and era groups are
not the same reviewers observed over time. Differences between them describe who
reviews under each condition, not change within individuals.
