# Documentation

This section is related to your work on clean code and documentation in week 5.

First, choose six rules of clean code and explain them. For each one,

* Summarise the rule in your own words.
* Provide an example from the code that you wrote in week 2 and then refined in week 4.
* Explain how your code implements the rule. 

Second, copy the doxygen comments from your code into your portfolio and provide some 
descriptive commentary on their purpose and structure. Use screenshots showing the HTML 
content that is generated from your code to illustrate your explanation.

Finally, highlight three examples from your code where you have eliminated the need
for comments by adhering to the principles of clean code.

# Code Referenced  
```
 public void Register(string username, string password)
{
    var (hashedPassword, salt) = HashPasswordWithSalt(password);
    SaveToDatabase(username, hashedPassword, salt);
}

public bool Login(string username, string password)
{
    var user = GetUserFromDatabase(username);
    var hashedPassword = HashPassword(password, user.Salt);
    return user.HashedPassword == hashedPassword;
}

private (string HashedPassword, string Salt) HashPasswordWithSalt(string password)
{
    var salt = CreateSalt();
    var hashedPassword = HashPassword(password, salt);
    return (hashedPassword, salt);
}
```

# Clean Code Rules

## Rules used 

1. Descriptive and Meaningful Names

2. Single Responsibility Principle (SRP)

3. Don't Repeat Yourself (DRY)

4. Keep Functions/Methods Small

5. Consistent Formatting and Indentation

6. Keep Lines of Code Short and Concise

## Examples in my code

1. Good examples of this rule in my code are Register, Login, HashPasswordWithSalt, hashedPassword, salt, and user. These are all clearly named and the purpose is evident at a glance.

2. Looking at my functions shows that they all have a clear purpose and don't stray from their responsibility. Register is responsible for registering a user, Login for user authentication, and HashPasswordWithSalt for password hashing.

3. As pointed out in my prior portfoilo entry, I spend time making sure there was no repeated code. HashPasswordWithSalt removed the need to repeat the password hashing logic.

4. Due to the size of my code, all of my functions are easy to read and understand. This is mostly shown in Register as only two methods are called in order to get the desired outcome.

5. Indentation is used throughout in order to make sure my code is readable and easy to understand. This formatting stays consistent throughout.

6. This is shown throughout my code, as all methods are relatively short and don't leave room for much errors. 

## Implementation of Rule 

1. This is implemented by giving clear names to variables and methods (e.g. HashPasswordWithSalt, hashedPassword, user...)

2. I have used this rule in my code by  
