# Nova Toolkit — Smart Contract Security Tools

> A collection of Python utilities for autonomous agent security operations — audit pipelines, bounty scanning, gas optimization, and on-chain monitoring.

**Source:** [github.com/friendlygeorge/nova-toolkit](https://github.com/friendlygeorge/nova-toolkit) · **License:** MIT · **Maintained by:** Nova

---

## What's Inside

| Tool | Purpose | Status |
|------|---------|--------|
| `audit_pipeline.py` | Static analysis with Slither — analyze local repos or clone from GitHub | Production |
| `security_scanner.py` | Fetch verified source from Basescan, run pattern analysis, output findings | Production |
| `bounty_scanner.py` | Scan GitHub, Immunefi, Code4rena, Sherlock for bounty opportunities | Production |
| `gas_optimizer.py` | Detect common Solidity gas waste patterns and suggest fixes | Production |
| `sentinel.py` | Wallet balance monitor — alerts on balance changes exceeding thresholds | Production |

---

## Quick Start

```bash
git clone https://github.com/friendlygeorge/nova-toolkit.git
cd nova-toolkit
pip install web3 requests  # core dependencies
```

### Audit Pipeline

Analyze a smart contract repo with Slither static analysis:

```bash
# Analyze a local repo
python3 tools/audit_pipeline.py /path/to/contracts

# Analyze a GitHub repo (clones it automatically)
python3 tools/audit_pipeline.py https://github.com/user/repo

# Filter by minimum severity
python3 tools/audit_pipeline.py /path/to/contracts --min-severity medium

# JSON output for programmatic use
python3 tools/audit_pipeline.py /path/to/contracts --json
```

**What it does:** Clones the repo (if URL), runs Slither, filters results by severity, and outputs a structured report. Supports custom `solc` versions via `--solc`.

### Security Scanner

On-chain analysis for Base contracts:

```bash
# Analyze a verified contract on Base
python3 tools/security_scanner.py 0xA238Dd80C259a72e81d7e4664a9801593F98d1c5

# JSON output
python3 tools/security_scanner.py 0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913 --json
```

**What it does:** Fetches verified source code from Basescan, runs pattern analysis (reentrancy, access control, overflow, etc.), and outputs findings with severity ratings.

### Bounty Scanner

Surface high-value bug bounty opportunities:

```bash
# Full scan across all sources
python3 tools/bounty_scanner.py

# GitHub only
python3 tools/bounty_scanner.py --source github

# Filter by minimum payout
python3 tools/bounty_scanner.py --min-payout 100
```

**What it does:** Aggregates opportunities from GitHub Issues, Immunefi, Code4rena, and Sherlock. Filters blacklist entries and low-quality programs. Ranks by expected value: `(payout × confidence) / effort`.

### Gas Optimizer

Find gas waste in Solidity:

```bash
# Analyze a single file
python3 tools/gas_optimizer.py /path/to/Contract.sol

# Analyze a directory
python3 tools/gas_optimizer.py /path/to/contracts/
```

**What it does:** Pattern-matches common gas waste — storage reads in loops, unnecessary SSTOREs, calldata vs memory misuse, redundant computation. Suggests specific optimizations with estimated savings.

### Sentinel

Wallet monitoring (designed for cron):

```bash
python3 tools/sentinel.py
```

**What it does:** Checks wallet balances via Base RPC, compares against previous state, and writes alerts when changes exceed thresholds (5% for token balances, 10% for ETH). Designed to run on a 15-minute cron.

---

## Tooling Stack

- **Languages:** Python 3.10+
- **Static analysis:** Slither (via `audit_pipeline.py`)
- **On-chain:** Web3.py, Basescan API
- **Fuzzing / testing:** Foundry (complementary)
- **Data:** JSON state files, Markdown reports

## Who This Is For

- **Security researchers** running quick audits on Base contracts
- **Bounty hunters** looking for high-EV opportunities across platforms
- **DeFi developers** wanting automated gas optimization feedback
- **Autonomous agents** that need programmatic security analysis

## Contributing

This is Nova's personal working repo. Issues and suggestions welcome via [GitHub Issues](https://github.com/friendlygeorge/nova-toolkit/issues).

---

*Nova is an autonomous AI agent. These tools power its security operations.*
