# Antimicrobial activity prediction against Enterococcus faecium from public ChEMBL data

Bioactivity prediction of growth inhibition in Enterococcus faecium, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL. Independent models are trained on multiple bioactivity datasets, corresponding to dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.

This model was incorporated on 2026-05-19.Last packaged on 2026-05-21.

## Information
### Identifiers
- **Ersilia Identifier:** `eos81zy`
- **Slug:** `antimicrobial-activity-efaecium`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Activity prediction`
- **Biomedical Area:** `Antimicrobial resistance`
- **Target Organism:** `Enterococcus faecium`
- **Tags:** `Gram-positive bacteria`, `ESKAPE`, `Antimicrobial activity`, `ChEMBL`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `6`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Enterococcus faecium from 5 ChEMBL-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 5 sub-models. Recommended threshold: 0.834. |
| merged_mic_decoys_a | float | high | Probability from sub-model trained on MIC measurements merged across 8 ChEMBL assays (cutoff 10 uM; n=1360 incl. decoys). Recommended threshold: 0.790. |
| merged_mic_decoys_b | float | high | Probability from sub-model trained on MIC measurements merged across 4 ChEMBL assays (cutoff 10 uM; n=830 incl. decoys). Recommended threshold: 0.842. |
| general_mic | float | high | Probability from sub-model trained on MIC measurements aggregated across 1258 ChEMBL assays (cutoff 10 uM; n=6801). Recommended threshold: 0.523. |
| general_ic50_decoys | float | high | Probability from sub-model trained on IC50 measurements aggregated across 41 ChEMBL assays (cutoff 10 uM; n=880 incl. decoys). Recommended threshold: 0.874. |
| general_mic90 | float | high | Probability from sub-model trained on MIC90 measurements aggregated across 103 ChEMBL assays (cutoff 10 uM; n=228). Recommended threshold: 0.584. |


### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos81zy](https://hub.docker.com/r/ersiliaos/eos81zy)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos81zy.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos81zy.zip)

### Resource Consumption
- **Model Size (Mb):** `29`
- **Environment Size (Mb):** `1888`
- **Image Size (Mb):** `2069.71`

**Computational Performance (seconds):**
- 10 inputs: `36.55`
- 100 inputs: `34.27`
- 10000 inputs: `536.76`

### References
- **Source Code**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication Type:** `Other`
- **Publication Year:** `2026`
- **Ersilia Contributor:** [arnaucoma24](https://github.com/arnaucoma24)

### License
This package is licensed under a [GPL-3.0](https://github.com/ersilia-os/ersilia/blob/master/LICENSE) license. The model contained within this package is licensed under a [GPL-3.0-or-later](LICENSE) license.

**Notice**: Ersilia grants access to models _as is_, directly from the original authors, please refer to the original code repository and/or publication if you use the model in your research.


## Use
To use this model locally, you need to have the [Ersilia CLI](https://github.com/ersilia-os/ersilia) installed.
The model can be **fetched** using the following command:
```bash
# fetch model from the Ersilia Model Hub
ersilia fetch eos81zy
```
Then, you can **serve**, **run** and **close** the model as follows:
```bash
# serve the model
ersilia serve eos81zy
# generate an example file
ersilia example -n 3 -f my_input.csv
# run the model
ersilia run -i my_input.csv -o my_output.csv
# close the model
ersilia close
```

## About Ersilia
The [Ersilia Open Source Initiative](https://ersilia.io) is a tech non-profit organization fueling sustainable research in the Global South.
Please [cite](https://github.com/ersilia-os/ersilia/blob/master/CITATION.cff) the Ersilia Model Hub if you've found this model to be useful. Always [let us know](https://github.com/ersilia-os/ersilia/issues) if you experience any issues while trying to run it.
If you want to contribute to our mission, consider [donating](https://www.ersilia.io/donate) to Ersilia!
