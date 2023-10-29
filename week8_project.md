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

Consistency is shown in the grid definitions being all the same size. This allows the UI to be balanced and appealing to users.I made the decsion to make the column lables bold for the same reason. Labels also have relevent names and can be easily identifed at a glance which helps a lot as code scales. 

### Code Example 2 

```
        public List<string> StorageLocations { get; set; } // Holds storage locations as strings.

        private string SelectedStorageLocation;  // Holds the selected storage location.

        // Getter and setter for SelectedStorageLocation.
        public string SelectedStorageLocation
        {
            get { return SelectedStorageLocation; }
            set
            {
                // Checking if the new value is different from the current value.
                if (SelectedStorageLocation != value)
                {
                    // Update the selected storage location.
                    SelectedStorageLocation = value;

                    // Notify that the SelectedStorageLocation property has changed.
                    OnPropertyChanged(nameof(SelectedStorageLocation));

                    // Call the FilterData method to update the data based on the selected storage location.
                    FilterData();
                }
            }
        }
```
This example of code is more comment heavy but that is due to the fact there are more complicated processes going on here that can't be easily understood. Because of this, I felt like adding more comments makes the code require less knowlage of the program as a whole to understand. Therefore this is a good example of code readabilty. 

Variables are named in a way that makes it easy to understand what there purpose is. StorageLocatiom amd SelectedStorageLocation make it clear that there is a link between them but that they are still easily told apart. 


## Summary of Test Code

### updateValueTest
```
    public void updateValueTest()
    {
        // Creating relevent variables
        var page = new MissionResourcesPage();
        string newValue = "Food";

        // Assigning new value
        page.SelectedResourceType = newValue;

        // Assert
        Assert.Equal(newValue, page.SelectedResourceType);
    }
```
To ensure  SelectedResourceType property update in MissionResourcesPage is working, a test is run. This test works by creating an instance of MissionResourcesPage and the assignment of a new value, such as "Food," for the SelectedResourceType property. The test then verifies if the property accurately reflects the newly assigned value.

### 
```
    public void defaultStates()
    {
        // Creating relevent variables
        var page = new MissionResourcesPage();

        // Assert
        Assert.Equal("All", page.SelectedResourceType);
        Assert.Equal("All", page.SelectedStorageLocation);
    }
```
This test ensures that when MissionResourcesPage is initialized, it sets the SelectedResourceType and SelectedStorageLocation variables to the default values of "All." It verifies that these properties are properly setup with the expected base data, which helps make sure the application's starts reliably.

## Review Changes 

One main issue were flagged when my code got the review stage. This was that due to the order in which I was initializing the elements of my code, only one of the filter boxes were being populated with data. This meant that all through it was able to display and sort the data, it would only work with storage location and not the type of resource. After this issue had been pointed out it was as easy as reorganising my code so it was loading and pulling data correctly. 

This was a simple error to make and an obvious one however I had been more focused on testing and making my code work in the development stage that I skipped right past it. Dispite this, it taught me a good lession about code modularity and the importance of thinking ahead when creating elements in relation to the data or other element it may need access to at some point. 


## Issues That Arose

To the best of my abilty as a program as of right now, I could not find any real issues or code discrepancies. I wish I had something to write here but I do not. The only change I ended up suggesting was that two of their methods serverd very similar purposes and could be combined in order to help future proof the code a bit. But this change isn't applicable on the size of the applications we are working on. 

## Reflection of Weekly Work 

A lot of issues arose when it came to creating this project, unfortunately,  nearly all the result of my Visual Studio not wanting to play nice with NuGet extension. It took days before anything started working again and the only reason I bring this up is it made me change my code a lot to attempt some form of work around. I did not know what was causing problems and ended up troubleshooting my code and making use of a lot of breakpoints to see what was happening individually. As painfully annoying the problems I ran into were, I will admit it gave me a better understanding of the tools Visual Studio has at it's disposal. There is still a lot I have to learn about VS, but I am also learning more everyday. 

Mainly, my biggest takeaway from a coders' perspective that I had this week was the overwhelming importantance of modularity. Having code set up in a way that isolates and specfies each element, the data it uses and any initializations creates an infinitely better block of code to work with. It allows for not only an easier understanding of the code but also makes it easier to edit and test. 


