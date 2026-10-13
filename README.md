[Русская версия](README.ru.md)

# Employee Records and Reporting (C++)

A small Windows-oriented C++ coursework project demonstrating binary employee records, separate command-line utilities, process creation, and report generation.

## Components

| File | Role |
|---|---|
| `Main.cpp` | Main program that coordinates the workflow and launches the helper executables. |
| `Creator.cpp` | Helper intended to create a binary file of employee records. |
| `Reporter.cpp` | Reads the binary records and writes a report with hours and calculated pay. |
| `employee.h`, `employee.cpp` | Employee record structure and file-reading/report helpers. |
| `test.cpp` | GoogleTest-based tests for report generation and error cases. |

## Build and test

Requirements: Windows, a C++20-capable compiler, CMake, and internet access for the current CMake configuration to fetch GoogleTest.

```powershell
cmake -S . -B build
cmake --build build --config Debug
ctest --test-dir build -C Debug --output-on-failure
```

The commands are based on the checked-in CMake configuration; they have not been run in this review. The project uses the Windows process API (`CreateProcessA`) and is not currently a portable cross-platform example.

## Known review notes

- `Creator.cpp` prints a prompt for employee fields, but the current source should be checked to ensure it actually reads and validates those fields before writing records.
- The CMake configuration downloads GoogleTest from its `main` branch rather than pinning a version, so dependency resolution is not fully reproducible.
- Treat this as coursework, not production-ready record-processing software. Review input validation and binary-file error handling before relying on it.
