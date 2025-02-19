# 📝 Exercise4 - Self-Evaluation ~ 10 minutes

Self-evaluation involves asking the model to assess itself using specific criteria. In this exercise, we apply this method to TypeScript scenarios.

## 1️⃣ Use Case 1: Create a Prompt for the Model to List Comprehensive Items to Test a Java method

Possible example:

```java
// Ask your AI to give you a list to test this method
// Method that validates an email address
public boolean validateEmail(String email) {
    String emailRegex = "^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$";
    return email.matches(emailRegex);
}
```

Now it's your turn to integrate your prompt below: 👀
```java
can you generate comprhencive items to test this code 
// Ask your AI to give you a list to test this method
// Method that validates an email address
public boolean validateEmail(String email) {
    String emailRegex = "^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$";
    return email.matches(emailRegex);
}
```

What was the response?
```java
✅ Positive Test Cases (Valid Emails)
#	Test Case	Input	Expected Output
1	Valid simple email	test@example.com	true
2	Email with subdomain	user@mail.co.uk	true
3	Email with numbers	john123@example.net	true
4	Email with hyphens and dots	first.last@my-domain.com	true
5	Email with underscores	user_name@domain.com	true
6	Email with capital letters	Test@Example.COM	true
❌ Negative Test Cases (Invalid Emails)
#	Test Case	Input	Expected Output
7	Missing @ symbol	userexample.com	false
8	Missing domain	user@.com	false
9	Missing username	@example.com	false
10	Space in email	user@exa mple.com	false
11	Missing top-level domain (TLD)	user@example	false
12	Multiple @ symbols	user@@example.com	false
13	Special characters not allowed	user!@example.com	false
14	Consecutive dots in domain	user@domain..com	false
15	Empty string	""	false
16	Null input	null	false (Handle NullPointerException)

```

## 2️⃣ Use Case 2: Ask the Model if It Can Provide More Possibilities

Possible example:

```typescript
Ask the model if it can provide more possibilities.
```

Now it's your turn to integrate your prompt below: 👀
```java
Write your prompt here
```

What was the response?
```java
Write AI response here
```

## 3️⃣ Use Case 3: Ask the Model to Self-Evaluate and Improve Its Response

Possible example:

```typescript
Ask the model to self-evaluate and improve its response.
```

Now it's your turn to integrate your prompt below: 👀
```java
Write your prompt here
```

What was the response?
```java
Write AI response here
```
