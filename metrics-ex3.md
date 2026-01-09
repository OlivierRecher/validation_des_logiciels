# Exercice 3 - CK Metrics Across Classes: Who Looks “Smelly”?
## Metrics Comparison Table

| Class | LOC | WMC | CBO | LCOM |
|-------|-----|-----|-----|------|
| Bank | 393 | 14 | 4 | 0 |
| BankAccount | 405 | 20 | 3 | 44 |
| Person | 294 | 23 | 1 | 79 |
| BankAccountApp | 447 | 2 | 4 | 1 |

## Questions & Answers

### Which class has the highest WMC?

**Person** with WMC = 23

### Which class has the highest CBO?

**Bank and BankAccountApp** (tied) with CBO = 4

### Looking at WMC + CBO + LCOM together, which class would you worry about most for future maintenance, and why?

I would worry about **Person** the most. Here's why:

- **Highest WMC (23)**: It has the most methods, suggesting multiple responsibilities
- **Highest LCOM (79)**: This is the worst cohesion score. High LCOM means the methods in the class are poorly related and don't work well together
- **Combined impact**: The high WMC + very high LCOM suggests the class is doing many unrelated things. It's likely violating the Single Responsibility Principle

**BankAccount** would be my second concern:
- WMC = 20 (second highest)
- LCOM = 44 (also poor cohesion)
- This suggests it's also mixing too many responsibilities

**Bank** is in the best shape despite moderate WMC and CBO, with good cohesion (LCOM = 0), indicating its methods work well together. **Person** needs refactoring urgently to split its responsibilities and improve cohesion.

## Do SonarLint issues appear more often in classes with higher WMC/CBO?

Not really. BankAccount has more SonarQube issues (3 issues) than Person.java, even though Person has a higher WMC (23 vs 20). This shows that code quality issues and metrics don't always correlate—BankAccount's problems are more about code smells and best practices, while Person's issues are more about design complexity and poor cohesion.
