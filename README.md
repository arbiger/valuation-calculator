# Valuation Calculator

Fast stock valuation calculator with instant market valuation metrics.

Inspired by:
- YouTube: [布萊恩穩賺 - Stock valuation screening](https://youtu.be/gVWvhIAtGDE)
- [Day1Global Tech Earnings Deepdive Skill](https://github.com/star23/Day1Global-Skills)

## Features

- **PEG Ratio** - Implied EPS growth calculation
- **EV/EBITDA** + **Rule of 40**
- **DCF** - Discounted Cash Flow with sensitivity analysis
- **Holdings Dashboard** - Portfolio valuation at a glance
- **Index Valuation** - SPY, QQQ, DIA

## Installation

```bash
# Clone the repo
git clone https://github.com/arbiger/valuation-calculator.git
cd valuation-calculator

# Install dependencies
pip install yfinance
```

## Usage

```bash
# Full valuation
python valuation.py value NVDA

# PEG only
python valuation.py value peg NVDA

# EV/EBITDA + Rule 40
python valuation.py value ev NVDA

# DCF (with custom params)
python valuation.py value dcf NVDA --wacc=0.08 --growth=0.15 --terminal=0.03

# All holdings (requires holdings.md)
python valuation.py value

# Major indices
python valuation.py value --index
```

## Commands

| Command | Description |
|---------|-------------|
| `value <ticker>` | Full valuation for a single stock |
| `value peg <ticker>` | PEG + Forward/Trailing P/E + Implied Growth |
| `value ev <ticker>` | EV/EBITDA + Rule of 40 |
| `value dcf <ticker>` | DCF valuation |
| `value` | All holdings valuation |
| `value --index` | Three major indices (SPY, QQQ, DIA) |

## DCF Parameters

| Parameter | Description | Default |
|-----------|-------------|---------|
| `--wacc=N` | Weighted Average Cost of Capital | 10% |
| `--growth=N` | Future growth rate | 5% |
| `--terminal=N` | Terminal growth rate | 2.5% |

## Evaluation Criteria

| PEG | Rating |
|-----|--------|
| < 0.5 | 🔥 Severely Undervalued |
| 0.5 - 1.0 | 👍 Undervalued |
| 1.0 - 1.5 | ✅ Fair Value |
| > 1.5 | ⚠️ Overvalued |

| DCF Upside | Rating |
|------------|--------|
| > 20% | ✅ Undervalued |
| -20% ~ 20% | ⚠️ Fair Value |
| < -20% | ❌ Overvalued |

## Requirements

- Python 3.9+
- yfinance

## License

MIT
