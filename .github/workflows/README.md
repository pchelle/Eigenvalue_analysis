# EVANS GitHub Actions Workflow

This directory contains the GitHub Actions workflow for the EVANS (EigenValue ANalySis) pipeline, following the instructions from the EVANS manual.pdf.

## Workflow: evans-pipeline.yml

The `evans-pipeline.yml` workflow implements the complete EVANS methodology for chirality-sensitive 3D QSPR analysis.

### Workflow Steps

The pipeline follows the 5 main steps outlined in the EVANS manual:

1. **Molecular Simulations (AMBER)**
   - Uses scripts in `molecular simulations/` directory
   - Performs MD simulations to obtain stable starting structures
   - Requires AMBER or AmberTools installation for actual execution

2. **Distance Calculation (VMD)**
   - Uses `dist_CentBond-CentMol.tcl` script
   - Calculates interatomic distances
   - Requires VMD (Visual Molecular Dynamics) for actual execution

3. **Matrix Generation and Processing**
   - Uses `Evans_v2020.1.xlsm` Excel macro
   - Performs canonical numbering, distance matrix generation
   - Integrates physicochemical properties
   - Generates covariance matrices

4. **Eigenvalue Calculation (R)**
   - Uses `newCoVarMats_2_eigen_tab.r` script
   - Computes eigenvalues from covariance matrices
   - Generates descriptors for QSAR/QSPR modeling

5. **ML Model Building (Python)**
   - Uses `classification.py` and `regression.py` scripts
   - Builds machine learning models using scikit-learn and mlxtend
   - Correlates eigenvalue descriptors with biological properties

### Triggering the Workflow

#### Manual Trigger

You can manually trigger the workflow from the GitHub Actions tab with the following options:

- `input_molecules`: Path to input molecules (default: 'test_molecules')
- `run_simulations`: Run molecular simulations step (default: true)
- `run_distance_calc`: Run distance calculation step (default: true)
- `run_eigenvalue_calc`: Run eigenvalue calculation step (default: true)
- `run_ml_model`: Run ML model building step (default: true)

#### Automatic Trigger

The workflow automatically runs on:
- Push to `main` or `master` branch
- Pull requests to `main` or `master` branch

### Prerequisites

For complete execution of the EVANS pipeline, the following software is required:

1. **AMBER/AmberTools**: For molecular dynamics simulations
2. **VMD**: For distance calculations
3. **Microsoft Excel or LibreOffice**: For matrix generation using the Excel macro
4. **R**: For eigenvalue calculations (installed by the workflow)
5. **Python 3.11+**: With required packages (installed by the workflow)

### Python Dependencies

The workflow automatically installs:
- numpy
- pandas
- matplotlib
- scikit-learn
- mlxtend

### Artifacts

The workflow generates the following artifacts:

1. **evans-manual**: The EVANS manual PDF (30-day retention)
2. **pipeline-report**: Execution report (30-day retention)

### Customization

To customize the workflow:

1. Edit `.github/workflows/evans-pipeline.yml`
2. Modify input parameters in the `workflow_dispatch` section
3. Adjust steps based on your specific requirements
4. Update software versions in the `uses` sections

### References

For detailed information about the EVANS methodology, refer to:
- `EVANS manual.pdf` in the repository root
- Publications listed in the manual

### Support

For questions or issues related to the EVANS methodology:
- Refer to the EVANS manual.pdf
- Check the repository README.md
- Review the publications listed in the manual
