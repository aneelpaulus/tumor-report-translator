# Tumor Report Translator

Paste or upload a tumor DNA test report and get each finding explained in plain English, along with the FDA-approved drugs and recruiting clinical trials for that change.

**[Try it live](https://aneelpaulus.github.io/tumor-report-translator/)** or **[open a fictional sample report](https://aneelpaulus.github.io/tumor-report-translator/?sample=1)**

Genomic reports from labs like Foundation Medicine, Tempus, and Caris are written for oncologists. Patients and families get a list of gene names and letter codes ("KRAS G12C", "CDKN2A loss", "TMB 12 Muts/Mb") with little explanation. This tool translates them.

## What you get

- **Each gene change in plain English:** what the gene normally does and what this kind of change means (a swapped building block, a cut-short protein, extra copies, a lost gene, a fusion). It recognizes the roughly 780 genes on the Tempus xT, FoundationOne CDx and OmniSeq INSIGHT panels; about 85 common cancer genes have their own plain-English descriptions, and when the lab labels a change gain- or loss-of-function, that's explained too.
- **FDA-approved drugs for that change, split by scope.** The tool reads every FDA drug label that mentions the gene and sorts the drugs into:
  - approved for this change in your cancer
  - approved for this change in any solid tumor
  - approved for this change only in other cancers (off-label for you)
  - "not a match": the label names a different change in the same gene. For example, KRAS G12C drugs are listed as not a match for KRAS G12D, and EGFR exon 19 drugs as not a match for exon 20 insertions or T790M.
- **Strong published evidence the FDA lists miss.** If CIViC, a free expert-curated research database, gives a drug its top grade ("validated") for this change and that drug isn't already listed from FDA labels, it appears in its own section. It's labeled clearly as research evidence, not a guideline or an approval.
- **A note about treatment guidelines.** Oncologists also follow guidelines such as NCCN's, which can recommend drugs not shown here. The page says so and points patients to NCCN's free patient guides.
- **Tumor-wide markers:** TMB, MSI, mismatch repair, HRD, PD-L1, HER2 protein by immunohistochemistry (IHC), and genomic loss of heterozygosity (LOH), with what each one means and any approvals based on it.
- **Blood-cell changes flagged.** When a blood test (liquid biopsy) says a change may come from clonal hematopoiesis, meaning age-related changes in blood cells rather than the tumor, the tool says so on that finding.
- **Recruiting trials** from ClinicalTrials.gov that mention the change, filtered to your cancer type.
- **Inherited changes are flagged, not interpreted.** If the report's germline section lists a change (found in normal blood or saliva DNA), the tool says it was most likely inherited. If a tumor-only change is in a gene such as BRCA1, BRCA2, or ATM, it suggests asking about genetic counseling and germline testing. It doesn't estimate inherited risk.
- **Blood tests (liquid biopsies) are recognized.** For Guardant360, FoundationOne Liquid, or Tempus xF reports, the page explains why percentages are low and why a "not detected" result doesn't rule a change out.
- **Variants of unknown significance** are listed last, and the tool explains why they usually don't change treatment.
- **Questions to ask the doctor,** based on what was found.
- **A clinician view.** "Show technical detail" adds variant allele fraction, CIViC evidence (sensitivity and resistance, levels A and B), and links to CIViC, OncoKB, and the [Drug Target Tracker](https://aneelpaulus.github.io/drug-target-tracker/).
- **A summary for your AI assistant.** One click downloads a text file with the findings and drug information, plus instructions to explain them simply. It leaves out names, dates, and the original report text. Upload or paste it into ChatGPT, Claude, Gemini, or Copilot.

## Privacy

The page has no server. The report is read inside your browser, and PDFs are read with PDF.js on your device. Only the gene names, the changes found (for example "KRAS G12C"), and the cancer type you choose are sent to the public databases below. Names, dates, and the rest of the report never leave the page. Nothing is stored.

## Where the information comes from

| What | Source |
|---|---|
| Approved drugs and their indications | FDA drug labels via [openFDA](https://open.fda.gov) |
| Recruiting trials | [ClinicalTrials.gov](https://clinicaltrials.gov) |
| Graded research evidence | [CIViC](https://civicdb.org), an open knowledge base from Washington University in St. Louis |
| Further reading links | [OncoKB](https://www.oncokb.org) |
| Plain-English gene descriptions | Written for this tool |

## Limitations

- **Findings are read automatically.** The PDF reader rebuilds each page's layout and skips boilerplate (test descriptions, gene lists, drug and literature write-ups, trial titles, and lab interpretation pages), and it was tested on published sample reports from FoundationOne CDx, Tempus xT and xF, Caris MI Profile, Oncomine Dx Target Test, and OmniSeq INSIGHT, plus the example pages in Foundation's FoundationOne Liquid CDx report guide. Other formats may still trip it up, so check the list of findings against the report. Scanned PDFs and photos can't be read; type the findings in instead. When some pages of a PDF are pictures (some labs print the summary page that way), the tool names those pages so you can check them.
- **Some results are graphics.** Tempus shows MSI as a scale with the result highlighted, which text can't capture. The tool says so instead of guessing.
- **No treatment guidelines.** NCCN guidelines are copyrighted and can't be reproduced without NCCN's permission, so they aren't included. Guidelines often recommend drugs for changes the FDA label doesn't name. The CIViC section catches some of these, but a drug missing here may still be standard care.
- **Matching reads label wording.** The tool handles common patterns (exon 19 deletions, exon 20 insertions, resistance mutations, "HRR gene-mutated"), but labels are written for people, not programs. Some matches carry a note asking the doctor whether this specific change qualifies. A few drugs keep an FDA label online after being taken off the US market; the ones known to the tool are marked.
- **It doesn't say which treatment to choose.** That depends on the person's whole situation, prior treatment, and the full report.
- **Inherited risk isn't assessed.** A tumor test usually can't tell whether a change was inherited. Only germline testing and genetic counseling can.

## Run your own copy

The whole tool is one file, `index.html`. To host it free on GitHub:

1. Create a new public repository and upload `index.html`, `README.md`, and `LICENSE`.
2. In the repository, open **Settings**, then **Pages**.
3. Under "Build and deployment", choose **Deploy from a branch**, select `main` and `/ (root)`, and save.

## Part of the Medical AI Toolkit

Drug names link to the [Drug Label Explainer](https://aneelpaulus.github.io/drug-label-explainer/), and genes link to the [Drug Target Tracker](https://aneelpaulus.github.io/drug-target-tracker/). All tools are at [aneelpaulus.github.io](https://aneelpaulus.github.io/).

## Disclaimer

For education only. This is not medical advice, and it doesn't replace a conversation with the oncologist who knows the person's full situation. Not affiliated with the FDA, NIH, any testing lab, or any drug maker.

## License

MIT. See `LICENSE`.

Built by Aneel Paulus, MD, MS.
