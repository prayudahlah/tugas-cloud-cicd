# tugas-cloud-cicd

Pipeline ingestion data hidrologi USGS dan meteorologi Open-Meteo ke Azure Blob
Storage, dijalankan oleh GitHub Actions setiap 6 jam.

## Lokal

```bash
uv venv --python 3.12 .venv
source .venv/bin/activate
uv pip install -r requirements-dev.txt
pytest -q
ruff check src tests
python -m src.pipeline --out-dir out --lookback-days 2
```

## Azure

Isi environment berikut, lalu login dengan `az login`:

```bash
set -x AZURE_STORAGE_ACCOUNT satugascicd
python -m src.pipeline --lookback-days 2
```
