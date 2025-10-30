Lab 5: Static Code Analysis - Inventory System
Overview

This repository contains the solution for Lab 5: Static Code Analysis. The project demonstrates the use of Pylint, Bandit, and Flake8 to enhance Python code quality, improve security, and ensure adherence to style conventions.

Repository Contents

inventory_system.py – Original version containing issues

clean_inventory_system.py – Corrected and optimized version

pylint_report.txt – Pylint analysis report (clean version)

bandit_report.txt – Bandit security analysis report (clean version)

flake8_report.txt – Flake8 style analysis report (clean version)

README.md – This documentation file

Known Issues Table
Issue Type	Tool	Line(s)	Severity	Description	Fix Approach
Mutable default argument	Pylint	8	High	Function used mutable default logs=[], shared across calls	Changed default to None and initialized inside the function
Bare except	Pylint/Flake8	19	High	Catch-all exception handler used	Replaced with specific exceptions (KeyError, TypeError)
Security - eval()	Bandit	59	Medium	Use of eval() enables arbitrary code execution	Removed eval() entirely
Unused import	Pylint/Flake8	2	Low	Unused logging import	Removed unused import
Missing module docstring	Pylint	1	Low	No top-level documentation	Added a descriptive module docstring
Missing function docstrings	Pylint	Multiple	Low	Functions lacked documentation	Added clear docstrings for each function
Non-snake_case names	Pylint	Multiple	Low	Function names not PEP 8 compliant	Renamed functions (e.g., addItem → add_item)
String formatting	Pylint	12	Low	Old % formatting used	Replaced with f-strings
Missing encoding	Pylint	26, 32	Low	open() used without specifying encoding	Added encoding="utf-8"
Context manager	Pylint	26, 32	Low	Files not opened using context manager	Used with statement for file handling
PEP 8 blank lines	Flake8	Multiple	Low	Missing blank lines between functions	Added two blank lines between top-level functions
Missing final newline	Pylint/Flake8	61	Low	No newline at end of file	Added final newline
Input validation	Custom	8, 50	Medium	Functions accepted invalid data types	Added type checking and input validation
Error handling	Custom	14–20	Medium	Poor or missing error messages	Added detailed and informative error messages

Total Issues Fixed: 14

Improvements Made
1. Security Enhancements

Removed the unsafe eval() call

Introduced specific exception handling

Added input validation to prevent invalid types

2. Code Quality Improvements

Added descriptive docstrings for all functions

Adopted snake_case naming convention

Updated string formatting to f-strings

Removed unused imports

Added type validation for parameters

3. Style and PEP 8 Compliance

Added proper spacing between functions

Ensured file ends with a newline

Used with statements for safe file operations

Specified file encoding (utf-8)

Included a comprehensive module docstring

4. Robustness and Reliability

Fixed mutable default argument issue

Implemented handling for missing files

Improved clarity of error messages

Used .get() for safe dictionary access

Added the if __name__ == "__main__": guard

Analysis Results
Pylint Score

Original: 4.60/10

Clean Version: 10.00/10

Bandit Security Issues

Original: 2 issues (1 Medium, 1 Low)

Clean Version: 0 issues

Flake8 Style Issues

Original: 12 issues

Clean Version: 0 issues

Reflection
1. Which issues were easiest and hardest to fix?

Easiest:

Style-related issues like spacing, naming conventions, and final newlines were simple formatting changes.

Removing unused imports and updating string formatting to f-strings were quick fixes.

Hardest:

Fixing the mutable default argument required understanding how Python handles default parameters and memory.

Refining exception handling involved identifying specific error types.

Implementing input validation required considering all potential invalid inputs.

2. Were there any false positives?

One minor example was the global-statement warning from Pylint (line 27). While using global variables is generally discouraged, it was acceptable for this small demo program. The warning was suppressed intentionally with a comment.
All other warnings represented valid improvements.

3. How would static analysis tools be integrated into a development workflow?

Pre-commit Hooks:

Run Flake8 and Pylint automatically before each commit.

Prevent commits if major issues are detected.

CI/CD Integration:

Add Pylint, Bandit, and Flake8 checks in GitHub Actions or Jenkins.

Enforce thresholds (e.g., Pylint score > 8.0).

Block merges with unresolved security issues.

IDE Integration:

Use Pylint and Flake8 extensions in VS Code for real-time linting.

Configure auto-formatting using Black or autopep8.

Code Review Routine:

Review static analysis reports weekly.

Incrementally reduce technical debt.

Track code quality over time.

4. What improvements were observed after applying the fixes?

Readability:

F-strings improved clarity of output.

Snake_case naming and spacing made the code more Pythonic.

Docstrings provided clear context and purpose.

Robustness:

Input validation prevented runtime crashes.

Specific exception handling avoided silent failures.

Context managers ensured proper file closure.

Mutable default argument issue eliminated shared-state bugs.

Maintainability:

Consistent style and documentation simplify future updates.

Clear error messages assist in debugging.

Security:

Removing eval() closed a critical vulnerability.

Better error handling prevented information leakage.

Overall, the refactored code improved from 4.60/10 to a perfect 10/10 on Pylint, achieved zero security warnings, and became fully PEP 8 compliant — illustrating the practical value of static analysis in producing professional, maintainable, and secure code.

How to Run

Install required dependencies:

pip install pylint bandit flake8


Run the cleaned inventory system:

python clean_inventory_system.py


Perform static analysis:

pylint clean_inventory_system.py
bandit clean_inventory_system.py
flake8 clean_inventory_system.py

Author

T Aniruddha (PES1UG23AM332)
