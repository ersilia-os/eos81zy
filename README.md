# Antimicrobial activity prediction against Enterococcus faecium from public ChEMBL data

Bioactivity prediction of growth inhibition in Enterococcus faecium, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (Inhibition) and dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.

This model was incorporated on 2026-05-19.Last packaged on 2026-06-02.

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
- **Output Dimension:** `9`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Enterococcus faecium from 8 ChEMBL-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 8 sub-models. Recommended threshold: 0.602. |
| chembl_single_point_0 | float | high | Probability from sub-model trained on ChEMBL single-point low-data catch-all pool of 21 assays (135 compounds). Recommended threshold: 0.481. |
| chembl_dose_response_0 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 165 assays (1596 compounds). Recommended threshold: 0.693. |
| chembl_dose_response_1 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 57 assays (911 compounds). Recommended threshold: 0.553. |
| chembl_dose_response_2 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 69 assays (883 compounds). Recommended threshold: 0.524. |
| chembl_dose_response_3 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 56 assays (677 compounds). Recommended threshold: 0.596. |
| chembl_dose_response_4 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 61 assays (672 compounds). Recommended threshold: 0.482. |
| chembl_dose_response_5 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 43 assays (644 compounds; incl. 117 added negatives). Recommended threshold: 0.513. |
| chembl_dose_response_6 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 29 assays (510 compounds; incl. 19 added negatives). Recommended threshold: 0.501. |


### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos81zy](https://hub.docker.com/r/ersiliaos/eos81zy)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos81zy.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos81zy.zip)

### Resource Consumption
- **Model Size (Mb):** `70`
- **Environment Size (Mb):** `1890`
- **Image Size (Mb):** `2115.19`

**Computational Performance (seconds):**
- 10 inputs: `48.27`
- 100 inputs: `37.9`
- 10000 inputs: `832.93`

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
