🧪 Ultimate Get Next Line Tester
A complete hardcore testing suite for the 42 project get_next_line
<p align="center"> <img src="https://img.shields.io/badge/42%20Project-Get%20Next%20Line-2ea44f?style=for-the-badge" /> <img src="https://img.shields.io/badge/Language-Python%203-blue?style=for-the-badge" /> <img src="https://img.shields.io/badge/Memory%20Check-Valgrind-critical?style=for-the-badge" /> <img src="https://img.shields.io/badge/Linux-Compatible-lightgrey?style=for-the-badge" /> </p>
📌 Overview

This repository contains the most advanced, complete, and brutal tester ever created for the 42 School project get_next_line.

It is designed to help you:

Validate your mandatory part

Stress-test your bonus part

Catch memory leaks, crashes, undefined behavior

Identify edge cases that normal testers never catch

Simulate real-world usage (stdin, pipes, binary files)

If your GNL passes this tester, moulinette is guaranteed to pass.
If your GNL fails this tester… well, it saved you from a moulinette disaster 😄

✨ Features
✅ Mandatory Tests

Multi-line file reading

No trailing newline

Empty file

BUFFER_SIZE=1 behavior

Large BUFFER_SIZE support

Standard input (stdin) reading

Pipe reading

EOF correctness

🟪 Bonus Tests

Multi-file-descriptor support

Switching between several FDs (2 → 30)

Ensures correct usage of a single static variable

Detects FD mixing, leakage, buffer pollution

🔥 Hardcore Stress Tests

These tests push your implementation to the absolute limit:

🔸 Huge Line Test

Reads a line of 1,000,000 characters.
Many implementations crash here — if yours survives, you’re elite.

🔸 Huge File Test

Reads 100,000 lines at high speed.

🔸 Binary File Test

Ensures your implementation does not segfault on binary data.

🔸 Random Fuzzer Test

Generates 5000 random lines with random lengths & random newline placement.

🔸 FD Storm Test

Opens 30 file descriptors at once and alternates calls to GNL.

🔸 PIPE Test

Simulates real shell behavior using OS pipes.

🔸 STDIN Test

Simulates input from keyboard and terminal streams.

🫧 Memory Leak Detection (Valgrind mode)

Detects:

Leaks

Invalid reads/writes

Double free

Use-after-free

Uninitialized memory access

Run with:

python3 gnl_autotester.py --valgrind

🌈 Beautiful Colored Output

Readable and moulinette-like for fast debugging.

📸 Preview
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

📦 Installation

Clone the repository:

git clone https://github.com/YOUR_USERNAME/gnl_autotester.git
cd gnl_autotester


Place your Get Next Line files in the same folder.

Mandatory files:
get_next_line.c
get_next_line_utils.c
get_next_line.h

Bonus files:
get_next_line_bonus.c
get_next_line_utils_bonus.c
get_next_line_bonus.h

▶️ Usage
🔵 Run mandatory tests
python3 gnl_autotester.py

🟣 Run bonus tests
python3 gnl_autotester.py bonus

🔥 Enable valgrind
python3 gnl_autotester.py --valgrind

🔧 Test with custom BUFFER_SIZE values
python3 gnl_autotester.py --buffers 1,10,42,10000

python3 gnl_autotester.py bonus --buffers 1,42,4096,100000

🧬 How It Works

This tester automatically:

Generates all necessary test files

Creates huge & binary files

Fuzzes random inputs

Compiles your GNL with multiple BUFFER_SIZE values

Runs all mandatory + bonus tests (depending on mode)

Executes additional hardcore stress tests

Scans memory operations (optional valgrind)

Prints a full summary

No configuration required.

🏆 Why This Tester?

Other testers stop at basic stuff.
This one simulates EVERYTHING that breaks GNL in real codebases, including:

heavy IO

buffers of all sizes

pipe-based input

simultaneous reading from multiple file descriptors

huge memory allocations

corrupted binary data

fuzzing random inputs

long-term stability with enormous files

If your GNL passes this, it is rock solid.

🤝 Contributing

Pull requests and suggestions are welcome!

You can contribute by adding:

more fuzzing strategies

new stress conditions

Windows/macOS portability

ASCII banners

CI pipelines

📄 License

MIT License.
Feel free to use, modify, and share.
