# SonarQube: Static Analysis & Quick Fixes

## Issues

### Issue 1

Name: Try-with-resources should be used
File: BankAccount.java
Line: 166
Explanation: When you open files or connections in Java, you need to close them after you're done. If you don't, they stay open and waste memory. Try-with-resources automatically closes them for you.

### Issue 2

Name: Unused "private" fields should be removed
File: BankAccount.java
Line: 22
Explanation: Having private fields that are never used clutters the code and can confuse readers. It's best to remove them to keep the code clean and maintainable.

### Issue 3

Name: Local variables should not be declared and then immediately returned or thrown
File: BankAccount.java
Line: 211
Explanation: Declaring a local variable just to return or throw it right away adds unnecessary lines to the code. It's cleaner and more efficient to return or throw the value directly without the extra variable.


## Fix issues

### Fix for Issue 2

Before:
```java
private double withdrawLimit = 0;
private boolean success;
private double initMoneyAmount = 0;
```

After:
```java
private double withdrawLimit = 0;
private double initMoneyAmount = 0;
```

### Fix for Issue 3

Before:
```java
public String toString() {

		String bankInfo = "Your Account number is " + accountNumber + " " + "Your Balance is: " + balance + " "
				+ "Date account created is: " + dateCreated + " " + "Withdraw limit is: " + withdrawLimit + " "
				+ "Your account holder info is: " + accountHolder;

		return bankInfo;
	}
```

After:
```java
public String toString() {

		return "Your Account number is " + accountNumber + " " + "Your Balance is: " + balance + " "
				+ "Date account created is: " + dateCreated + " " + "Withdraw limit is: " + withdrawLimit + " "
				+ "Your account holder info is: " + accountHolder;
	}
```

I confirm SonarQube issues have been fixed.

**Do SonarLint issues appear more often in classes with higher WMC/CBO?**

Not really. BankAccount has more SonarQube issues than Person.java, even though Person has a higher WMC (23 vs 20). This shows that code quality issues and metrics don't always correlate—BankAccount's problems are more about code smells and best practices, while Person's issues are more about design complexity and poor cohesion.