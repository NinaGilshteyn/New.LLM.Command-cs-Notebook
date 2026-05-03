# Example: /cs-notebook in action

This example shows the full interaction flow using the raw notes in `raw_input.txt`.

---

## Step 1 — User runs the command

```
/cs-notebook ran kraken2 on the 6 gut samples from cohort B today. samples are HMP_gut_001
through 006. fastq files are on the server at /data/raw/cohortB/. trimmed with trimmomatic
first, output went to /data/trimmed/cohortB/. kraken2 db is the standard db at
/ref/kraken2_standard_db. outputs in /data/kraken2_out/cohortB/. then ran bracken to get
abundance estimates at species level. wrote a python script bracken_summary.py to merge all
6 bracken output files into one table and compute relative abundances. saved the merged table
to /data/results/cohortB_species_abundance.csv. noticed sample HMP_gut_004 has way lower read
counts after trimming, might be a QC issue. committed bracken_summary.py. still need to run
diversity analysis and figure out the HMP_gut_004 problem. also need to run the same pipeline
on cohort A.
```

---

## Step 2 — Claude generates the draft entry

---

## CS Progress Notebook Entry

**Date:** 2026-05-03
**Session Title:** Kraken2 + Bracken Taxonomic Profiling — Cohort B Gut Metagenomes
**Developer:** *(auto-detected from git config)*
**Session Type:** Analysis

---

### Objective
Run taxonomic classification and species-level abundance estimation on 6 gut metagenome samples from Cohort B using Kraken2 and Bracken. Merge outputs into a single abundance table and flag any QC anomalies before proceeding to diversity analysis.

---

### Scripts & Files

| Script / File | Full Path | Language / Type | Notes |
|---------------|-----------|-----------------|-------|
| bracken_summary.py | ❓ UNKNOWN | Python | Merges 6 Bracken output files; computes relative abundances |
| trimmomatic output | /data/trimmed/cohortB/ | FASTQ | Trimmed reads for all 6 samples |
| Kraken2 output | /data/kraken2_out/cohortB/ | Kraken2 report | Raw classification output per sample |
| cohortB_species_abundance.csv | /data/results/cohortB_species_abundance.csv | CSV | Merged species-level relative abundance table |

---

### Major Edits

| File | Change Description | Reason / Context |
|------|--------------------|------------------|
| bracken_summary.py | Created new script | Needed to merge per-sample Bracken outputs and compute relative abundances across Cohort B |

---

### Version Control

**Commits made this session:** Yes

| Commit Message | Repository | Branch | Notes |
|----------------|------------|--------|-------|
| ❓ UNKNOWN | ❓ UNKNOWN | ❓ UNKNOWN | Committed bracken_summary.py |

**Repository URL / path:** ❓ UNKNOWN

---

### Data Storage

| Data / Asset | Location | Format | Notes |
|--------------|----------|--------|-------|
| Raw FASTQ reads | /data/raw/cohortB/ | FASTQ | HMP_gut_001 – HMP_gut_006 |
| Trimmed reads | /data/trimmed/cohortB/ | FASTQ | Trimmomatic output |
| Kraken2 DB | /ref/kraken2_standard_db | Kraken2 DB | Standard database |
| Kraken2 reports | /data/kraken2_out/cohortB/ | Kraken2 report | Per-sample classification results |
| Species abundance table | /data/results/cohortB_species_abundance.csv | CSV | Merged Bracken output, relative abundances |

---

### Issues & Blockers

| Issue | Severity | Status | Notes |
|-------|----------|--------|-------|
| HMP_gut_004 low read count post-trimming | HIGH | Open | May indicate a failed library prep or sample contamination; needs investigation before diversity analysis |

---

### Next Steps

#### Immediate (do next session)
- [ ] Investigate HMP_gut_004 — check raw read count, trimming log, and FastQC report
- [ ] Confirm full path for bracken_summary.py and verify it is in the correct repo

#### Short-term (this week)
- [ ] Run alpha and beta diversity analysis on Cohort B abundance table
- [ ] Run full Trimmomatic → Kraken2 → Bracken pipeline on Cohort A
- [ ] Write tests for bracken_summary.py (edge cases: missing samples, zero-count rows)

#### Research / Figure out
- [ ] Determine threshold for excluding a sample based on read count — is HMP_gut_004 salvageable?
- [ ] Decide whether to use rarefaction or relative abundance normalization for diversity analysis

#### Backlog
- [ ] Wrap full pipeline (Trimmomatic → Kraken2 → Bracken → merge) into a single Snakemake or Nextflow workflow
- [ ] Add visualizations (stacked bar charts of top species per sample) to bracken_summary.py

---

### Additional Notes
*(filled in from user response in Step 3)*
Using Kraken2 v2.1.3 and Bracken v2.8. Trimmomatic settings: LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:36.

---

### Original Input
```
ran kraken2 on the 6 gut samples from cohort B today...
```

---

## Step 3 — Claude asks follow-up questions

After displaying the draft above, Claude sends this message:

---

I have a few gaps to fill in before saving. Please answer what you can:

1. What is the full file path for **bracken_summary.py**? (e.g. `/home/user/projects/metagenomics/bracken_summary.py`)
2. What was your **commit message** for bracken_summary.py?
3. What is the **repository name or URL** where bracken_summary.py was committed?
4. Which **branch** were you working on?
5. Is there anything else you'd like to add to this entry? (Any extra context, observations, or details not covered above — or type 'no' to skip.)

---

## Step 4 — User answers

```
1. /home/researcher/projects/metagenomics/cohortB/bracken_summary.py
2. add bracken summary script for cohort B
3. https://github.com/lab/metagenomics-pipeline
4. main
5. Using Kraken2 v2.1.3 and Bracken v2.8. Trimmomatic settings: LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:36.
```

---

## Step 5 — Claude fills in all unknowns, shows the final revised entry, then saves

All `❓ UNKNOWN` fields are replaced, the Additional Notes section is populated, and the file is saved to:

```
C:\Users\<you>\Documents\CS_Notebook\data_2026-05-03_time_14-22-07.docx
```
