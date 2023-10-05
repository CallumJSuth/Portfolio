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

# Clean Code Rules

## Rules used 

1. Descriptive and Meaningful Names

2. Single Responsibility Principle (SRP)

3. Don't Repeat Yourself (DRY)

4. Keep Functions/Methods Small

5. Consistent Formatting and Indentation

6. Comments for Clarity, Not Explanation

## Examples in my code

1. A good example of this in my code is the method names for my buttons and other processes for my UI. newValueButton_Clicked, UpdateValueButton_Clicked, deleteValueButton_Clicked and UpdateValueList all show this rule as they are clearly named based on their purpose.

2. Again, the best example of this is my button methods(newValueButton_Clicked, UpdateValueButton_Clicked, deleteValueButton_Clicked). Each method has clear code which only pretains to it's associated use and nothing else.

3. UndacDatabaseSTRV.cs shows an avoidance of repeated code. This because of the methods GetItemsAsync, SaveItemAsync and DeleteItemAsync. These methods are called whenever data needs to be manipulated or read from the backend database. This means code doesn't have to be repeated everytime the database is accessed.

4. GetItemsAsync, SaveItemAsync and DeleteItemAsync are good examples of this as they only have a few lines of code each and successfully preform database manipulation.

5. All formatting throughout my code is consistant throughout. Code is spaced and organised in a way that is easy to read and understand.

6. Comments are used but not overused in my code, they provided descriptions of elements of my code without being too indepth or overexplaning things.

## How code implements the rule

1. By appropriately naming variables and methods based on what they pretain to.

2. By making sure each method sticks to it's required use and doesn't have code which could cause confusion.

3. By creating methods that are specific to each required use and not adding in code that could be used again.

4. All though my code has bigger methods, most of them are small and compact in order to increase readability. Even for the bigger functions, there is no filler code or code that could be removed (As far as I can tell ).

5. By keeping a consistent indention pattern throughout all of my files and code.

6. By adding comments that simply explain aspects of my code wihtout being confusing or overexplaining.

# Doxygen Comments 

## Constants Class

```
/// <summary>
/// Provides constants used in the application.
/// </summary>
public static class Constants
{
    // ...
}

```

<summary>: This comment provides a summary of the purpose of the Constants class. It describes that the class is used for storing constants used in the application.

## UndacDatabaseSTRV Class

```
/// <summary>
/// Provides database operations for the 'structureSTRV' table.
/// </summary>
public class UndacDatabaseSTRV
{
    // ...
}

```

<summary>: This comment provides a summary of the purpose of the UndacDatabaseSTRV class. It states that the class is responsible for performing database operations related to the 'structureSTRV' table.
InitDatabase Method

## InitDatabase Method

```
/// <summary>
/// Initializes the SQLite database connection.
/// </summary>
/// <returns>An asynchronous task.</returns>
async Task InitDatabase()
{
    // ...
}

```

<summary>: This comment explains the purpose of the InitDatabase method. It mentions that the method is responsible for initializing the SQLite database connection.
<returns>: This tag describes the return value of the method, which is an asynchronous task.

## GetItemsAsync Method

```
/// <summary>
/// Gets all items from the 'structureSTRV' table.
/// </summary>
/// <returns>A list of 'structureSTRV' items.</returns>
public async Task<List<structureSTRV>> GetItemsAsync()
{
    // ...
}

```

<summary>: This comment describes the purpose of the GetItemsAsync method, which is to retrieve all items from the 'structureSTRV' table.
<returns>: This tag specifies that the method returns a list of 'structureSTRV' items.

## structureSTRV Class

```
/// <summary>
/// Represents a structure stored in the 'values' table.
/// </summary>
[Table("values")]
public class structureSTRV
{
    // ...
}

```

<summary>: This comment provides an overview of the purpose of the structureSTRV class. It mentions that the class represents a structure stored in the 'values' table.
[Table("values")]: This tag is a C# attribute, but it is included in the comment to explain that the class is mapped to a table named "values" in the database.


