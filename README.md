This repository has codes for the implementation of the EigenValue Analysis (EVANS) QSPR methodology. The repository consists of Amber scripts for molecular simulations of small molecules, a VMD script for distance calculation, Excel macros for matrix manipulation, an R script for computing eigenvalues and python codes for ML model building. Detailed instructions on how to implement EVANS may be found in the user manual.

## GitHub Actions Workflow

A GitHub Actions workflow has been created to automate and document the EVANS pipeline. The workflow (`evans-pipeline.yml`) implements all 5 steps from the EVANS manual:

- **Step 1**: Molecular Simulations (AMBER scripts)
- **Step 2**: Distance Calculation (VMD script)
- **Step 3**: Matrix Generation and Processing
- **Step 4**: Eigenvalue Calculation (R script)
- **Step 5**: ML Model Building (Python scripts)

The workflow can be triggered manually from the GitHub Actions tab or automatically on push/pull requests. For more information, see `.github/workflows/README.md`.
