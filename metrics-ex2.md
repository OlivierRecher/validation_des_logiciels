# Metric Analysis: BankAccount.java

## Method Analysis

**Chosen Method:** `withdrawMoney(double withdrawAmount)`

I choose this method because CK Metrics indicates it has a high Cyclomatic Complexity of 5, which suggests it contains multiple decision points. This complexity can lead to challenges in understanding, testing, and maintaining the method. Analyzing this method will help identify potential areas for refactoring to improve code quality.

```` bash
 ~ public boolean withdrawMoney(double arg0): 5
````

**Cyclomatic Complexity:** 5

## Decision Points

```java
public boolean withdrawMoney(double withdrawAmount) {
    // Decision Point 1: The 'if' statement content involves multiple checks
    if (withdrawAmount >= 0 
        && balance >= withdrawAmount // Decision Point 2: checking sufficient balance
        && withdrawAmount < withdrawLimit // Decision Point 3: checking against withdraw limit
        && withdrawAmount + amountWithdrawn <= withdrawLimit) { // Decision Point 4: limit cumulative withdrawals
        
        balance = balance - withdrawAmount;
        success = true;
        amountWithdrawn += withdrawAmount;
    } else { // Decision Point 5: else branch
        success = false;
    }
    return success;
}
```

## Refactoring Proposal

The `withdrawMoney()` method currently mixes validation logic with state modification, which contributes to its complexity. I propose extracting the validation logic into a helper method named `isWithdrawalValid(double amount)`. This separate boolean method would encapsulate all the rules for allowing a withdrawal (positive amount, sufficient balance, and limit checks), reducing the main method's responsibility to just orchestrating the transaction.

## Bonus: Implementation of Refactoring

```java
    public boolean withdrawMoney(double withdrawAmount) {
		if (!isWithdrawalValid(withdrawAmount)) {
			return false;
		}

		balance -= withdrawAmount;
		amountWithdrawn += withdrawAmount;
		return true;
	}

	private boolean isWithdrawalValid(double withdrawAmount) {
		return withdrawAmount >= 0 && balance >= withdrawAmount && withdrawAmount <     withdrawLimit && withdrawAmount + amountWithdrawn <= withdrawLimit;
	}
```

```` bash
 ~ public boolean withdrawMoney(double arg0): 2
````