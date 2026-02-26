# DAY-2-TASK

A simple command‑line log filtering tool written for the **PL202 Day‑2 exercise**.

The repository contains a Python script that reads a raw `logs.txt` file, ignores
invalid lines, optionally filters entries by log **level** and/or **service**,
and writes the matching records to an output file while printing a brief summary.

---

## 📁 Repository structure

```
pl202 t2 - nv24170/        # working directory containing log files and tool
├── logs.txt               # input data (raw log lines)
├── auth_logs.txt          # example output (level=ERROR, service=auth)
├── db_logs.txt            # example output (not filtered yet)
├── warn_api.txt           # example output (level=WARN, service=api)
├── filtered_logs.txt      # default output file
├── run_proof.txt          # proof of exercise run(s)
└── log_tool.py            # main CLI script
```

> All paths are relative to the project root unless otherwise noted.

## 🛠️ Requirements

* Python 3.7+ (no external dependencies).

## 🚀 Usage

Run `log_tool.py` from the repository root. The default behaviour is to scan
`logs.txt` and write every valid log line to `filtered_logs.txt`.

```bash
# basic invocation (no filters)
python "pl202 t2 - nv24170/log_tool.py"

# filter by level (INFO/WARN/ERROR is case‑insensitive)
python "pl202 t2 - nv24170/log_tool.py" --level ERROR

# filter by service name
python "pl202 t2 - nv24170/log_tool.py" --service auth

# combine filters and specify an output file
python "pl202 t2 - nv24170/log_tool.py" --level WARN --service api --out warn_api.txt
```

Each run prints a summary like:

```
Valid lines scanned: 42
Lines written: 5
Output file: warn_api.txt
```

Filtered results appear one per line in the chosen output file using the
original `timestamp | LEVEL | service | message` format.

## 📋 Log format rules

The script only considers lines that meet **all** of the following criteria:

* Non‑empty content
* Exactly four fields separated by the `|` character
* The second field (level) is one of `INFO`, `WARN`, or `ERROR` (case
  insensitive; stored uppercase internally)

Lines failing any rule are skipped but do not cause an error.

## 📚 Example files

Some example output files are already included (`auth_logs.txt`,
`warn_api.txt`, etc.) demonstrating common filter combinations.

## ✅ Running proofs and tests

`run_proof.txt` contains sample command sequences and their output, useful for
verifying the tool behaves as expected.

---

Feel free to modify the script, extend the filters, or integrate the tool into
larger data‑processing pipelines. Happy filtering! 🎯