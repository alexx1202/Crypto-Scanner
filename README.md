# Bybit Crypto Scanner

This project scans Bybit USDT perpetual markets.
Results are written to multiple spreadsheets:

* ``Crypto_Volume.xlsx`` containing volume change statistics
* ``Funding_Rates.xlsx`` with the latest funding rate for each pair
* ``Open_Interest.xlsx`` showing percent changes in open interest across several timeframes, now including 1 day, 1 week and 1 month intervals
* ``Price_Change.xlsx`` listing the percentage price change over common intraday periods

The funding and open interest sheets omit the ``24h USD Volume`` column, but rows remain sorted using this metric.

All rows in every sheet are ordered by ``24h USD Volume`` in descending order.

## Installation

Install the required Python packages using `pip`:

```bash
pip install -r requirements.txt
```

## Running Tests

After installing the dependencies, run `run_checks.py` to execute
both pylint and pytest with progress bars:

```bash
python run_checks.py
```

## Running the Scan

Once the lint checks and tests pass, execute the scanner directly to fetch
market data and export `Crypto_Volume.xlsx`:

```bash
python scan.py
```

## Grouping Debug Logs

Use `group_logs.py` to organise `scanlog.txt` entries so that all lines for
each symbol appear together:

```bash
python group_logs.py /path/to/scanlog.txt
```

The script writes a new file with `_grouped` appended to the original name.

## Log Files

All logs are written to the `logs` directory in the project root:

```
<project_root>/logs
```

`scan.py` writes `scanlog.txt` here, while `run_checks.py` creates
`pylint.log` and `pytest.log` in the same directory.

## Windows Notifications

If the optional `win10toast` package is installed and the script is run on
Windows, a toast notification is shown when scans finish. No additional
configuration is required. On other platforms the notification step is skipped.

