# Project work 1

In week 8, you are exercising all the principles and techniques that have been discussed 
in the module so far. Your portfolio entry should demonstrate your ability to integrate 
the various dimensions of software engineering into your practice. It should include 

* A descriptive summary of the issue that you worked on.
* Snippets from your code with commentary showing how you have used good software design 
  practice.
* A descriptive summary of the test code that you have written.
* A reflective summary of any changes that were requested during the code review along 
  with your fixes.
* A descriptive summary of any issues you found with the code that you were asked to review.
* A general reflective section that identifies, for example,
  * New things you have realised this week
  * Common problems that can arise in a team development situation
  * How your practice compares to other people's
  * etc.

Be sure to include links to the original items in the team's GitHub repository.


## Summary of Issue 

The UNDAC Deputy Team Leader needs to regularly check the available resources to insure the mission going smoothly. This helps ensure the mission's long-term success. To make this happen, users should be able to easily access and sort the data.  

There will be four values that each resource will have. Name, quantity, resource type and where it is stored. Resource type and storage location will be used to filter the data by the data they contain.


## Code and Commentary 
### Code Example One
```
                <ListView.Header>
                    <!-- Column definitions and labels. -->
                    <Grid>
                        
                        <!-- Define four columns with equal width for displaying data. -->
                        
                        <Grid.ColumnDefinitions>
                            <ColumnDefinition Width="2*" />
                            <ColumnDefinition Width="2*" />
                            <ColumnDefinition Width="2*" />
                            <ColumnDefinition Width="2*" />
                        </Grid.ColumnDefinitions>

                        <!-- Column labels -->
                        <Label Grid.Column="0" Text="Resource Name" FontAttributes="Bold" />
                        
                        <Label Grid.Column="1" Text="Resource Type" FontAttributes="Bold" />
                        
                        <Label Grid.Column="2" Text="Storage Location" FontAttributes="Bold" />

                        <Label Grid.Column="3" Text="Quantity" FontAttributes="Bold" />
                        
                    </Grid>
                </ListView.Header>
```
In this section of code, I make use of a couple of good software desgin practices. Firstly is good code readability. All of the elements are spaced out and easily understandable, allowing for any future changes to be implemented easier and quicker. Comments are used by only where they are needed, having the column widths and lables in their own section means that not every element has to be explained as it is already clear what they do.  


## Summary of Test Code

## Review Changes 

## Issues That Arose

## Reflection of Weekly Work 

