# CB2330-KICKASS-PROJECT

Authors: Laura Filkova, Lisa Verena Neuschitzer and Juan Andres Toro Delgado . 

Course project for CB2330, autumn 2026.

## What this is
We model data from Ginell et al. (2025), *Sequence-based prediction of intermolecular interactions driven by disordered regions*, Science 388, eadq8381. The paper uses FINCHES to predict the self-interaction parameter ε of 19,702 human disordered regions (IDRs) before and after their phosphosites are replaced by glutamic acid. Our random variable is the change Δε for one IDR.

Our model: each phosphosite changes ε by its own random amount, drawn from a normal with mean μ and spread s, and the amounts add up. For an IDR with n phosphosites this gives Δε | n ~ Normal(nμ, ns²).

## What we found
- Fitted on Table S3A by maximum likelihood (**´grid search**): μ = 0.927 ε units per phosphosite and s = 1.34. The uncertainty on μ is about ±0.005 (likelihood interval, curvature and bootstrap).
- Simulated data from the model reproduce the straight rise through zero and the widening spread seen in the real data. Fitting simulated data recovers the parameters it was generated with.
- The model predicts that IDRs with more phosphosites are less likely to become stickier after phosphorylation, and the data follow this trend.
- Where it breaks: the spread grows faster than the model allows, so phosphosites in the same IDR are probably not independent. With the second force field (Table S3B), μ is about four times smaller, so μ depends on how FINCHES is run.

## How to run it
In Google Colab: upload `project.ipynb`, create a folder called `data` in the Files panel, and upload the Excel file into it before running.
