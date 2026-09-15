# IPP / Principles of Programming Languages and OOP

Python interpreter for the XML representation of the **IPPcode23** language, created as the second project for the Brno University of Technology course **Principles of Programming Languages and OOP (IPP)** in 2022/2023.

## Project overview

The interpreter reads an IPPcode23 program represented in XML, validates its structure and executes instructions in order. It supports command-line input handling, variable frames, data and call stacks, labels, jumps, arithmetic and logical operations, string operations and basic I/O.

The implementation uses only the Python standard library, including `argparse` for command-line arguments and `xml.etree.ElementTree` for XML parsing.

## Main components

- `Argument` — processes `--source` and `--input` command-line arguments.
- `XML` — parses and validates the XML program representation, sorts instructions and collects labels.
- `Context` — stores interpreter state, including variable frames, stacks, labels and input data.
- `Interpreter` — executes IPPcode23 instructions and performs runtime checks.

## Execution flow

1. Command-line arguments are parsed and the XML source is opened from a file or standard input.
2. The XML structure, instruction attributes and arguments are validated.
3. Instructions are stored and sorted by their `order` value.
4. Labels are collected before execution so jump and call instructions can resolve their destinations.
5. Instructions are executed sequentially while the interpreter maintains variable frames, data stack and call stack state.

Helper methods handle frame lookup, variable access and updates, argument type/value resolution and label-based jumps.

## Supported functionality

The implementation includes:

- global, local and temporary variable frames (`GF`, `LF`, `TF`)
- data stack and call stack handling
- labels and unconditional / conditional jumps
- arithmetic operations such as `ADD`, `SUB`, `MUL` and `IDIV`
- logical and comparison operations
- string operations including `CONCAT`, `STRLEN`, `GETCHAR`, `SETCHAR` and `STRI2INT`
- type conversion and variable type handling
- input/output instructions such as `READ`, `WRITE` and `DPRINT`
- XML structure validation and interpreter error handling

## Running the interpreter

Run the interpreter with a source XML file:

```bash
python3 interpret.py --source program.xml
```

Use a separate input file when the interpreted program requires input:

```bash
python3 interpret.py --source program.xml --input input.txt
```

The implementation also supports reading the XML source from standard input when `--source` is omitted.

## Repository structure

```text
.
├── README.md
└── interpret.py
```

`interpret.py` contains the original interpreter implementation.

## Course context

The IPP course covers programming-language paradigms and approaches to processing and implementing programming languages. This repository contains the interpreter part of the 2022/2023 coursework.

Official course page: https://www.vut.cz/studenti/predmety/detail/231010

## Notes

The original `interpret.py` coursework implementation is preserved unchanged. The relevant implementation details from the original Czech project documentation were consolidated into this README for a cleaner portfolio repository.
