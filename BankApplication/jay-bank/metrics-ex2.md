# Metric Analysis: BankAccount.java

## Method Analysis
**Chosen Method:** `withdrawMoney(double withdrawAmount)`
**Cyclomatic Complexity:** 5

## Decision Points
```java
public boolean withdrawMoney(double withdrawAmount) {
    // Decision Point 1: The 'if' statement content involves multiple checks
    if (withdrawAmount >= 0 
        && balance >= withdrawAmount                       // Decision Point 2: logical AND
        && withdrawAmount < withdrawLimit                  // Decision Point 3: logical AND
        && withdrawAmount + amountWithdrawn <= withdrawLimit) { // Decision Point 4: logical AND
        
        balance = balance - withdrawAmount;
        success = true;
        amountWithdrawn += withdrawAmount;
    } else {
        success = false;
    }
    return success;
}
```

## Refactoring Proposal
The `withdrawMoney` method currently mixes validation logic with state modification, which contributes to its complexity. I propose extracting the validation logic into a helper method named `isWithdrawalValid(double amount)`. This separate boolean method would encapsulate all the rules for allowing a withdrawal (positive amount, sufficient balance, and limit checks), reducing the main method's responsibility to just orchestrating the transaction.
