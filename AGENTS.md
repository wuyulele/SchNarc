# Repository Guidelines

## Project Structure & Modules
- `src/schnarc/`: core library (drivers in `schnarc.py`, models in `model.py`/`nn.py`, metrics, data utilities, trainers, calculators).
- `src/scripts/`: CLI tools for data prep, training, and MD runs (e.g., `setup_schnarc.py`, `run_schnarc.py`, `train_sharc_potential.py`, transforms).
- `examples/`: reference systems (CH2NH2+, SO2) with sample inputs/outputs.
- Tutorials: `SchNarc_Tutorial.pdf` and `20220907_CECAMSchool_PS5.ipynb` for walkthroughs.

## Build, Test, and Development Commands
- `python -m venv .venv; .\.venv\Scripts\activate`: create/activate a virtual env on Windows.
- `python -m pip install -e .`: editable install; pulls torch, ase, h5py.
- `python src/scripts/setup_schnarc.py --help`: inspect dataset/setup options.
- `python src/scripts/run_schnarc.py input.yml`: run dynamics with a config file.
- `python src/scripts/train_sharc_potential.py config.yml`: train a potential from a YAML config.
- `python src/scripts/transform_dataset.py --help`: see dataset transformation helpers.

## Coding Style & Naming Conventions
- Follow PEP 8 with 4-space indents; keep lines ?99 chars when practical.
- Use snake_case for functions/variables, CapWords for classes, UPPER_SNAKE for constants.
- Add type hints on new/changed APIs; prefer clear argument names over comments.
- Reuse helpers in `utils.py`/`metrics.py` before adding new utilities.

## Testing Guidelines
- No automated suite yet; prefer `pytest` for new tests.
- Place tests in `tests/` mirroring `src/schnarc` paths; name files `test_*.py`.
- For scripts, test entry-point functions with small fixture configs; mock heavy I/O.
- Validate numerical routines with tight tolerances and document assumptions.

## Commit & Pull Request Guidelines
- History is informal; use imperative English subjects (e.g., "Add MD config parser").
- Keep commits scoped; note rationale when changing scientific defaults or units.
- PRs should state motivation, key changes, and runtime impact; link issues/papers/configs.
- Include sample commands or configs used to validate changes; attach short logs or screenshots when UX changes.

## Security & Configuration Tips
- Keep credentials/proprietary datasets out of git; use env vars or gitignored files.
- Document SHARC/SchNetPack install paths via configs, not hard-coded constants.
- When sharing examples, strip large trajectory outputs and keep minimal inputs.
