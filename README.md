# Software Metrics Analysis

This repository contains an analysis of the software metrics for the Bank Application, generated using CK Metrics and SonarQube.

## Analysis Documents

### 1. [Metrics Overview](./metrics-ex1.md)
**File:** `metrics-ex1.md`
General overview of Chidamber & Kemerer (CK) metrics for the `Bank`, `BankAccount`, `Person`, and `BankAccountApp` classes. It includes the raw output from the CKJM plugin and an initial assessment of responsibilities.

### 2. [Method Complexity Analysis](./metrics-ex2.md)
**File:** `metrics-ex2.md`
Focused analysis of the `withdrawMoney` method in the `BankAccount` class. Identifies Cyclomatic Complexity and proposes a refactoring strategy to separate validation logic from execution.

### 3. [Cross-Class Comparison](./metrics-ex3.md)
**File:** `metrics-ex3.md`
A comparative table of metrics (LOC, WMC, CBO, LCOM) across all classes. It identifies "smelly" classes, highlighting `Person` and `BankAccount` as candidates for refactoring due to high cohesion (LCOM) and complexity scores.

### 4. [SonarQube & Static Analysis](./metrics-ex4.md)
**File:** `metrics-ex4.md`
Reports on issues found by SonarQube static analysis, such as unused private fields and `try-with-resources` suggestions. Includes "Before" and "After" code snippets for applied fixes and discusses the correlation between static analysis issues and CK metrics.