# Fuzzing the desktop calculator

This repo implements a custom fuzzer to find memory-error vulnerabilities in a C program specified in the src/original directory.  

## Directory structure
```
├── Makefile: building the project
├── build.sh
├── fuzzer: Fuzzing tool
│   ├── Fuzzer.java
│   ├── Instruction.java
│   └── OperandType.java
├── get_coverage.sh: generates coverage report
├── poc: contains input which triggers vulnerabilities
│   ├── vuln-1.poc
│   ├── ...
├── run_fuzzer.sh: running the fuzzer
├── run_tests.sh: running generated test cases
├── src
│   ├── include
│   │   └── debug.h
│   ├── original: original application code
│   │   └── dc.c
│   ├── vuln-1: contains code with security vulnerability that can be triggered with poc
│   ├── ...
└── state.properties
```

## Setup of fuzzer

1. Install Clang and LLVM 6.0 and run make

```
sudo apt-get install libfuzzer-6.0-dev llvm-6.0
make
```

2. AdressSanitiser enabled, for detecting memory errors

```
./bin/vuln-1/dc-san poc/vuln-1.poc
```

3. Get coverage of fuzzer

```
./get_coverage.sh <directory>/
```
