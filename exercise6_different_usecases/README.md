# 📝 Exercise6 - Different usecases ~ 20 minutes
This file contains several exercises that highlight various use cases for a developer. These exercises will allow you to test multiple scenarios, providing a comprehensive understanding of different situations you may encounter in development.

## Use Case 1: Fix code
Possible example:
```java
// Check why this code is not working whithout IA
// Ask AI to fix it
public static int divide(int a, String b) {
    // Division
    int result = a / b;
    int result = 0;
    return result;
}
```

Now it's yoNow it's your turn to integrate your prompt below: 👀
```java
is it a valid code 
[code]
```

What was the response?
```java
 Syntax & Compilation Errors
Type mismatch:

The method attempts to divide an int by a String (a / b), which is not allowed in Java. Division requires numeric types (int, double, etc.).
Duplicate variable declaration:

int result is declared twice:
java
Copier
Modifier
int result = a / b;
int result = 0;
This causes a "variable is already defined" compilation error.
Unused result of division:

Even if the division were correct, the calculated result is overwritten by int result = 0;, making the division pointless.
✅ Corrected Code
If you intended to parse b as an integer before performing the division, a correct version would be:

java
Copier
Modifier
public static int divide(int a, String b) {
    try {
        int numB = Integer.parseInt(b); // Convert String to int
        return a / numB; // Perform division
    } catch (NumberFormatException e) {
        throw new IllegalArgumentException("Invalid number format: " + b);
    } catch (ArithmeticException e) {
        throw new ArithmeticException("Division by zero is not allowed.");
    }
}
🛠 Fixes & Enhancements
✅ Parses String b safely
✅ Handles invalid number format ("abc" as input)
✅ Prevents division by zero
✅ Returns correct result

Would you like JUnit tests for this method? 🚀
```

## Use Case 2: Optimize code
Possible example:
```java
//ask AI to add some optimization like protecting the denominator from 0
public static int divide(int a, int b) {
    int result = a / b;
    return result;
}

```

Now it's your turn to integrate your prompt below: 👀
```java
can you optimise the code
```

What was the response?
```java
public static int divide(int a, String b) {
    if (b == null || b.isBlank()) {
        throw new IllegalArgumentException("Input cannot be null or empty.");
    }

    int numB;
    try {
        numB = Integer.parseInt(b.trim()); // Trim spaces & parse
    } catch (NumberFormatException e) {
        throw new IllegalArgumentException("Invalid number format: " + b);
    }

    if (numB == 0) {
        throw new ArithmeticException("Division by zero is not allowed.");
    }

    return a / numB;
}

```

## Use Case 3: Reverse engineering
Possible example:
```java
// Ask AI what is the purpose of this code
public static List<Integer> calcul(int limit) {
    List<Integer> primes = new ArrayList<>();
    boolean[] isPrime = new boolean[limit + 1];
    
    for (int i = 0; i <= limit; i++) {
        isPrime[i] = true;
    }
    
    int p = 2;
    while (p * p <= limit) {
        if (isPrime[p]) {
            for (int i = p * p; i <= limit; i += p) {
                isPrime[i] = false;
            }
        }
        p++;
    }
    
    for (p = 2; p <= limit; p++) {
        if (isPrime[p]) {
            primes.add(p);
        }
    }
    
    return primes;
}

```

Now it's your turn to integrate your prompt below: 👀
```java
Write your prompt here
```

What was the response?
```java
Write AI response here
```

## Use Case 4: REGEX
Possible example:
```java
// Try to understand what this regex does without AI
// Ask AI what the regex does and compare
// Modify the regex to match your company

^[\w\.=-]+@[\w\.-]+\.[\w]{2,3}$
```

Now it's your turn to integrate your prompt below: 👀
```java
can you explain the folowing regex dose and compare : 
^[\w\.=-]+@[\w\.-]+\.[\w]{2,3}$
```

What was the response?
```java
Regex Part	Explanation
^	Start of the string
[\w\.=-]+	Matches one or more (+) word characters (\w = [a-zA-Z0-9_]), dots (.), equals (=), and hyphens (-) before @
@	Matches the @ symbol (required in an email)
[\w\.-]+	Matches the domain name: one or more word characters (\w), dots (.), and hyphens (-)
\.	Matches a dot (.) before the domain extension
[\w]{2,3}	Matches 2 to 3 word characters (letters or numbers) for the TLD (e.g., "com", "net", "org")
$	End of the string
```
