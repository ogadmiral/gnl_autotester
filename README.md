# Ultimate Get Next Line Tester

<p align="center">
  <img alt="42 Project - Get Next Line" src="https://img.shields.io/badge/42%20Project-Get%20Next%20Line-2ea44f?style=for-the-badge" />
  <img alt="Language - Python 3" src="https://img.shields.io/badge/Language-Python%203-blue?style=for-the-badge" />
  <img alt="Memory Check - Valgrind" src="https://img.shields.io/badge/Memory%20Check-Valgrind-critical?style=for-the-badge" />
  <img alt="Linux Compatible" src="https://img.shields.io/badge/Linux-Compatible-lightgrey?style=for-the-badge" />
</p>

# Ultimate Get Next Line Tester

A complete, brutal testing suite for the 42 School get_next_line project. This tester validates mandatory requirements, stress-tests bonus behavior, and catches leaks, crashes, and edge cases that typical testers miss.

If your GNL passes this tester, moulinette is far more likely to pass. If it fails — you’ve been spared a moulinette disaster.

## Highlights

- Comprehensive mandatory tests (multi-line files, EOF behavior, BUFFER_SIZE edge cases)
- Bonus tests (multi-FD switching, FD leakage detection)
- Hardcore stress tests:
  - Huge line (1,000,000 characters)
  - Huge file (100,000 lines)
  - Binary file handling
  - Random fuzzing (thousands of randomized lines)
  - FD storm (open 30 FDs and alternate reads)
  - PIPE and STDIN behavior
- Optional Valgrind integration to detect:
  - Memory leaks
  - Invalid reads/writes
  - Double frees and use-after-free
  - Uninitialized memory access
- Readable, colored output that mimics moulinette for fast debugging

## Preview

Example output:

```
===== GNL TESTER =====

[OK]   test1: line1
[OK]   test1: line2
[OK]   test1: EOF
[OK]   fuzzing test passed
[OK]   huge line test passed
[OK]   binary file handled
[OK]   multi-FD switching works

===== RESULT =====
Score: 100%
🎉 PERFECT — Your GNL is clean!
```

## What this tester validates

Mandatory:
- Multi-line file reading
- Files without trailing newline
- Empty files
- BUFFER_SIZE = 1 behavior
- Large BUFFER_SIZE behavior
- STDIN reading
- PIPE reading
- EOF correctness

Bonus:
- Multi-file-descriptor support
- Switching between several FDs (2 → 30)
- Single-static-variable correctness
- FD mixing, leakage and buffer pollution detection

Stress & robustness:
- Huge line & huge file tests
- Binary file handling
- Random fuzzer (thousands of cases)
- FD storm and PIPE simulations

## Installation

Clone the repository and change into it:

```bash
git clone https://github.com/ogadmiral/gnl_autotester.git
cd gnl_autotester
```

Place your Get Next Line sources in the tester directory. Files expected:

Mandatory:
- get_next_line.c
- get_next_line_utils.c
- get_next_line.h

Bonus (optional):
- get_next_line_bonus.c
- get_next_line_utils_bonus.c
- get_next_line_bonus.h

## Usage

Run mandatory tests:

```bash
python3 gnl_autotester.py
```

Run bonus tests:

```bash
python3 gnl_autotester.py bonus
```

Enable Valgrind memory checks:

```bash
python3 gnl_autotester.py --valgrind
```

Test with custom BUFFER_SIZE values (comma-separated):

```bash
python3 gnl_autotester.py --buffers 1,10,42,10000
python3 gnl_autotester.py bonus --buffers 1,42,4096,100000
```

## How it works

- Generates required test input files (including huge and binary files)
- Fuzzes randomized inputs to expose edge cases
- Compiles your GNL using multiple BUFFER_SIZE values
- Runs mandatory and/or bonus test suites
- Executes hardcore stress tests designed to break fragile implementations
- Optionally runs Valgrind and parses results
- Produces an easy-to-scan summary and score

No configuration required — drop your GNL files in the folder and run the script.

## Running on CI

- The tester is designed for Linux environments (Valgrind requires Linux).
- You can add a CI workflow that installs Python 3 and Valgrind, places your GNL files in the repository root, runs the tester, and fails the job if score < 100%.

## Troubleshooting & Tips

- If a test crashes, examine the generated log and Valgrind output to locate invalid memory access or leak traces.
- Start by running small subsets (use --buffers and non-valgrind runs) to iterate faster.
- If your implementation uses dynamic buffers, make sure to handle very long lines and binary data safely.

## Contributing

Contributions are welcome! Ideas:
- Add more fuzzing strategies
- New stress conditions or heuristics
- Windows/macOS portability
- CI workflow examples
- ASCII banners and improved test reporting

Please open PRs or issues with detailed reproducers.

## License

MIT License — feel free to use, modify, and share.
