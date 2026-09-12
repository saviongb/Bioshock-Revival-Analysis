# BioShock: What Players Value

A data-driven analysis of how the BioShock trilogy was received, and what it suggests
the next entry should protect.

## What this is

Analyzed 85,395 English language Steam reviews across BioShock Remastered,
BioShock 2 Remastered, and BioShock Infinite to find out which themes were leading discussion, verdicts and if reception had changed over time.

Before sourcing the data or performing analysis, I wrote six predictions based on my personal playthroughs, then committed them to the GitHub under Impressions_and_Hypothesis. The predictions were then graded against the results: one confirmed, four partially confirmed, one not confirmed.

The deliverable is a slide deck summarizing key findings. The analysis behind it is in the GitHub.

**[Read the deck (PDF)](deck/BioShock%20Final%20Deck.pdf)**

## What I found

- **Narrative is the only theme mentioned in at least 20% of reviews across the franchise** - 24.6% for BioShock 1 Remastered, 23.5% for BioShock 2 Remastered, 40.4% for Infinite.

- **Negative reviews of BioShock 1 Remastered and BioShock 2 Remastered are largely about technical performance, not
  design** - technical is mentioned in 60.5% of BioShock 1's negative reviews and 75.3%
  of BioShock 2's, against 12.0% for Infinite.

- **Positive review rates rose over time and with hours played** for all three games,
  with the exception of a small decline for Infinite in the later era.

- **Nearly 1/4 of the negative reviews of Infinite mentioned the combat theme** — combat appears in
  23.6% of them, against 8.0% and 7.9% for the other two games' negative reviews.

Full write up: [`outputs/findings/findings_memo.md`](outputs/findings/findings_memo.md)

## Method

Reviews were pulled from Steam's public review API in July 2026. Nine theme dictionaries
were written after playthroughs and committed analysis. Each review was
matched against every dictionary, producing one flag per theme
per review.

Four measures were computed for each theme: overall salience, the split between positive
and negative reviews, review era, and playtime groups.

The instrument was tested against 72 hand coded reviews. Precision and recall are
reported for every theme, including the weak ones - narrative scored best at 87%
precision and 93% recall, visual/audio recall was 25%.

## Structure

- `notebooks/` — analysis, in order
- `src/` — data collection and cleaning code
- `docs/` — predictions, theme dictionaries, methodology log, comparison sources
- `outputs/` — figures and findings
- `deck/` — the deck as a PDF
- `data/raw/` and `data/processed/` are gitignored

## Reproducing

    conda env create -f environment.yml
    conda activate bioshock

Then run the notebooks in order. Notebooks 01 through 03 rebuild `data/raw` and
`data/processed`; notebooks 04 and 05 depend on those outputs and will fail until 01 through 03 have been run.

## Limitations

The instrument counts how often a theme is mentioned, not whether reviews approved of
it. Recall varies by theme, so comparing the same theme across games is sound but
comparing different themes to each other is not. BioShock 1 and 2 are the 2016
remasters, not the original releases. Era and playtime groups are different populations
of reviewers, not the same people tracked over time. Nothing here establishes cause.

## AI use

Claude was used as a programming guide and methodology tool; all analytical decisions,
hand-coding, and findings are my own.
