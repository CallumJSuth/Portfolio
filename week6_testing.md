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

## Reason for Test

## Limitations of Test
