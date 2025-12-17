# Python Code Workspace

This directory hosts the runnable Python assets for the glider flight analysis project. Use it as the working tree for notebooks, conversion utilities, and any derived data artifacts.

## Layout
- `Glider_Flight_Data_Analysis.ipynb` – primary analysis notebook; used for detailed data analysis and modelling of thermal regions
- `Raw_data/` – source Larus binaries, trimmed IGC tracks, and other telemetry inputs.
- `Results/` – derived parquet files, QA figures, and validation exports.
- `_internal/`, `__init__.py`, `__pycache__/` – helper utilities and package wiring that support the notebooks.
- `larus_to_df_2025.py` – conversion script that turns Larus dumps into typed pandas DataFrames saved next to the source file.

## Environment Setup
Create a virtual environment from the repo root and install the shared dependency set before running notebooks or scripts:

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r ../01_ENV/requirements.txt
```

(Alternatively, use `conda env create -f ../01_ENV/FSR_ENV3.yml`.)

## Usage Notes
1. Launch Jupyter Lab with the working directory pinned here so relative paths resolve correctly:
   ```bash
   jupyter lab --notebook-dir .
   ```
2. Convert Larus sensor dumps to pandas-ready frames:
   ```bash
   python larus_to_df.py <path-to-larus-bin>
   ```
3. **Filename alignment:** rename every Larus binary so its basename matches the paired IGC filename format `YYYY-MM-DD Pilot Name FlightID`, e.g. `2025-06-09 Alexandre Fierain 603970`. This ensures downstream joins succeed.

## Testing & Validation
- Place unit tests under `tests/` (create if needed) and run `pytest` from this directory for module-level validation.
- For analysis work, rerun `Glider_Flight_Data_Analysis_v7.ipynb` and compare updated plots or CSV exports under `Results/`.

## Data Handling
Keep sensitive flight telemetry under `Raw_data/`. Share hefty artifacts via external storage and reference them in documentation or PRs. Never store credentials in the repo—use local `.env` files instead.
