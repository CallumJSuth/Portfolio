# Testing

The practical exercise in week 6 involved competitive testing. For your portfolio entry,
select two pieces of test code that you wrote that best illustrate your skills in this
area.

For each example

* Summarise the purpose of the code you were testing
* Include the test code
* Provide a brief explanation of the test(s) that are performed
* Explain why this is an important aspect of the code to test
* Identify any limitations of your tests (this may be something that you realised after
  the evaluation).

Did you manage to write a test which failed during the final evaluation? If so, that would
make an excellent example. You should briefly discuss why the writer of the code might 
have overlooked the particular test case that failed

# Week 6  - Code Battles 

## Purpose of Tested Code

I wrote my tests on two pieces of code. The first of which being the initialization of the game page which is responsable for stating and setting up a new game.

Secondly, my other tests were run on the method required for chosing the game difficulty. More specficailly, the process responsable for creating a game on the medium difficulty. 

## Test Code Itself

### Page Setup Test

```
    public class PageTest
    {

        [Fact]
        public void Test_CreateNewChallengeEasy_SetWordProperty()
        {
            // Initialize a GamePage instance for "Easy" difficulty
            GamePage gamePage = new GamePage("Easy");

            // Create a new challenge
            gamePage.CreateNewChallenge();

            // Check that the 'Word' property is not null after challenge creation
            Assert.NotNull(gamePage.Word);
        }
    }
```

### Medium Code Test

```
        public class GamePageTests
        {
            // Using Theory attribute for parameterized testing
            [Theory]
            [InlineData(9)]  // Expected maximum length for the "Medium" difficulty(9a)

            // The test method
            public void Test_SelectWord_ReturnValidWordForMedium(int expectedMaxLength)
            {
                // Setting up the test scenario
                GamePage gamePage = new GamePage("Medium");

                // Calling the method in order for it to be tested
                string selectedWord = gamePage.SelectWord("Medium");

                // Verifying whether the chosen word length falls within the limit
                Assert.True(selectedWord.Length >= expectedMaxLength);
            }
        }
```

## Explanation of Test Code

### Setup Test 

The test method, "Test_CreateNewChallengeEasy_SetWordProperty()", checks how a new game challenge is created with the "Easy" difficulty setting on a "GamePage" object. This method is public and confirms that the "Word" property is correctly set after creating the challenge.

When "gamePage.CreateNewChallenge();" is called, it triggers the "CreateNewChallenge" method in the "gamePage" object. This method is responsible for starting a new game challenge and is the first step in loading the game itself.

Finally, the code "Assert.NotNull(gamePage.Word);" checks if the "Word" property in the "gamePage" object is null or not. This allows the program to know that "Word" has been set correctly as well as making sure that the "Easy" level challenge is working properly.

### Medium Code Test

The purpose of the test method “Test_SelectWord_ReturnValidWordForMedium(int expectedMaxLength)“ is to check if the SelectWord method behaves correctly in the "Medium" difficulty level. It verifies if the length of the word selected by the GamePage object is within the expected maximum length.

Next, the line “GamePage gamePage = new GamePage("Medium")” creates a new instance of the GamePage class and assigns it to the variable gamePage. This object is configured with the "Medium" difficulty level, setting up the initial conditions for the test.

By executing “gamePage.SelectWord("Medium")”, the test calls the SelectWord method within the gamePage object which is the main code that is getting tested. 

Lastly, the line “Assert.True(selectedWord.Length <= expectedMaxLength)” is an assertion using the Assert class. It uses the Assert.True method to confirm that the length of the selectedWord string is less than or equal to the expectedMaxLength. If this is successful, it means that the SelectWord method works correctly for the "Medium" difficulty level, ensuring that the selected word's length is within the limits provided.


## Reason for Test

### Setup Test 

This test method is designed to verify whether the process of creating a new game challenge with the "Easy" difficulty level, as the code in the GamePage class shows, correctly sets the 'Word' property to a non-null value. The primary purpose is to ensure that the game setup for the "Easy" difficulty level is functioning as expected, guaranteeing that a valid 'Word' variable is successfully passed once the code is run. 


### Medium Code Test

Next, this test method is tasked with confirming that the SelectWord method within the GamePage class correctly selects a word with a length that adheres to the maximum expected length for the "Medium" difficulty level. By specifying the maximum length, this test aims to validate that the game logic for word selection in the "Medium" difficulty mode works without flaws, ensuring that the chosen word's length complies with the defined length.


## Limitations of Tests

These tests have some problems. They only look at small parts of the GamePage class and don't consider the program as a whole. They also don't utilize fixed settings, which means they might not work well in a different environment. They don't check for user entry mistakes or any other of the ususal things you would test for . They only look at good results and don't show how the class works in more complicated and realistic situations. Finally, they only test a small part of the class, so more tests might be needed.


