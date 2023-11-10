# Project work 2

Week 10 is the third and last week in a series in which the goal is to improve your 
personal software engineering practice. Your portfolio entry has the same general content
as last week's, including:

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

In the reflective sections this week, you should highlight ways that you persona practice
has improved as before. It would also be good to reflect on any improvements that have
been made to the agreed team workflow and related procedures. Are things working
better than they were? What further improvements could be made in the future?

## Summary of Issue 

The main point of this issue is to efficiently find and invite the right partner agencies to join their team, while the business aims to give their teams access to external resources . To achieve this, the system needs to meet a set of criteria, like showing partner agencies with their current association status (requested, denied, confirmed, pending, N/A, etc), providing easy access to specfic agency details, allowing for a text search to filter the agency list and allowing that text search to be cleared. In essence, the system should make it easier to identify, engage, and view partner agencies.This allows for improved efficiency and access to external resources and support for the UN.


## Code and Commentary 

```
    public partial class MainPage : ContentPage
    {
        // Define two ObservableCollections to store PartnersInfo objects
        public ObservableCollection<PartnersInfo> PartnersDescription { get; set; }
        public ObservableCollection<PartnersInfo> FilteredPartnersDescription { get; set; }

        // Constructor for the MainPage class
        public MainPage()
        {
            // Initialize the PartnersDescription ObservableCollection with PartnersInfo objects
            PartnersDescription = new ObservableCollection<PartnersInfo>
        {
            // Adding PartnersInfo objects with defined properies (Placeholder Data) 
            new PartnersInfo
            {
                agencyName = "Savers LTD",
                agencyType = "National",
                associationStatus = "Requested",
                Location = "Syria"
            },
        ...
```
The code I've provided this week reflects my prior commitment to maintain clean and modular code. As you can see from the given example, I've chosen to use meaningful variable and class names, such as PartnersDescription and PartnersInfo, which make the code more readable and self-explanatory. By utilizing ObservableCollection, I've ensured efficient data management and responsiveness which is not only good for pratical application but also makes it really easy to manually test all values stored. This way of coding shows how I have been attempting to optimise application performance and improve end user satisfaction.

Additionally, this code shows my ablity initializing data structures, as shown in the constructor within the MainPage class. I've included comments to explain the purpose of various code sections, aiding in code readability and making it accessible to others. By following these coding conventions, I've created a baseline for scalable and easily maintainable code, which would undoubtedly appeal to any further developers looking to work on my code. My commitment to good coding practices has enabled me to create a robust and well-structured application which I am proud of.

```
                    <DataTemplate>
                        <ViewCell>
                            <!-- This is used to customize the appearance of a cell in the ListView -->
                            <Grid>

                                <!-- Defining the four columns in the grid with identical widths-->
                                <Grid.ColumnDefinitions>
                                    <ColumnDefinition Width="2*"/>
                                    <ColumnDefinition Width="2*"/>
                                    <ColumnDefinition Width="2*"/>
                                    <ColumnDefinition Width="2*"/>
                                </Grid.ColumnDefinitions>

                                <!-- Labels in each column to display data from the bound properties -->
                                <Label Grid.Column="0" Text="{Binding agencyName}"/>
                                <Label Grid.Column="1" Text="{Binding agencyType}"/>
                                <Label Grid.Column="2" Text="{Binding associationStatus}"/>
                                <Label Grid.Column="3" Text="{Binding Location}"/>

                            </Grid>
                        </ViewCell>
                    </DataTemplate>
                </ListView.ItemTemplate>
```

In this section of code, I've adopted a consistent and organized approach by using a Grid to lay out the visual elements within the ViewCell. By specifying identical widths for the four columns, I've created a balanced and visually appealing layout. This adherence to uniformity and structure demonstrates how I can create user-friendly interfaces.

In my coding process, I've used the power of data binding, allowing the labels in each column to display data from specific properties in the supplementing data source. This approach not only encourages clean code architecture but also simplifies the process of activily modifying and maintaining the user interface. These practices align with software development design princables for developing data-driven applications.

## Summary of Test Code

```
        public void noTextSearch()
        {
            // Setting example data and arranging test
            var mainPage = new MainPage();
            mainPage.PartnersDescription = new ObservableCollection<PartnersInfo>
            {
                new PartnersInfo
                {
                    agencyName = "TestAgency1",
                    agencyType = "TestType1",
                    associationStatus = "TestStatus1",
                    Location = "TestLocation1"
                },
                new PartnersInfo
                {
                    agencyName = "TestAgency2",
                    agencyType = "TestType2",
                    associationStatus = "TestStatus2",
                    Location = "TestLocation2"
                }
            };

            // Setting variable of blank search 
            var searchText = string.Empty; 

            // Running test code through actual code
            mainPage.OnSearchTextChanged(this, new TextChangedEventArgs("", searchText));

            // Asserting
            Assert.Equal(2, mainPage.FilteredPartnersDescription.Count);
        }
```

In this weeks test , I created a enviroment to test the behavior of the OnSearchTextChanged method when there is no text in the input box. I set up an instance of the MainPage class and added two example PartnersInfo objects to its PartnersDescription "ObservableCollection". Then, I provided an empty search variable for the search function. When I called the OnSearchTextChanged method to trigger the search, I expected the FilteredPartnersDescription to contain all the items from the PartnersDescription since there is no search filter applied. To confirm this, I checked that the count of items in FilteredPartnersDescription is equal to 2, showing that all items are displayed when the search text is empty. This test ensures that the application handles and displays data correctly when there is no search input in the provided box.

## Review Changes 

During the process of code reviews this week, one of the improvements that was suggested was adding more declerations for each of my elements making sure the are named appropriately. This was an easy fix as all that I ended up doing was going through each of my elements and providing names for all of them using the "x:Name..." attribute to unnamed elements. On top of this it was also recommended that I changed my "associationSatus" to Camel case instead of Pascal as I had named it "AssociationStatus" while not really thinking about it. Again, an easy fix and this helped me pay more attention to the naming conventions I used for my future variables. 

Another suggestion was made but for the scope of this project me and the reviewer agreed that it wasn't really required. Changing my grid layout to be based on the screen size rather than pre-set sizes/formatting. The reason we decided it wasn't worth implementing was due to the fact a lot of work would need to be done on the project as a whole to make this section work all different screen sizes / platforms and without the changes it would lead to only the gird scaling correctly and nothing else.  

## Issues That Arose

When looking at the code I had to review this week, the main element of there code was a map feature. The only problem I found with it was it didn't contain any function for zooming in and out of the map. This meant the map was only visable from one point and any indiviudal parts of the map couldn't be isolated. It wasn't a hard problem to deal with and I imagine it was fixed quickly. 

The other issue I found was a lack of error handling. There was no code that would catch any errors relating to the network or data retrival. This is a problem as no matter the size of the program, if run in an enviroment where either of these errors may show up it will immediately crash with no real clear information on why or how. 

## Reflection of Weekly Work 

As this is the final week I will talk about the last three weeks of progress here. When I began this course I had no conception of how to use Visual Studio, C# or .net MAUI but looking back on the past three weeks of work, I can confidently say that my skills not only in these areas have improved but my skills as a program as well. It became aparent during my development time in week eight that I wasn't creating code that was easy for anyone other than me to understand or edit. Now, with the mixture of the team project and completing the weekly tasks I feel like I can confidently say that has changed. My main focus the past week has been on improving my code modulaity and I have met that goal. This week, being the final week of tasks, showed that fact to me the best. The difference in development time between week eight and week ten is massive as well as the overall quailty of my code. 

Being able to actually practice coding has been a massive help these past few weeks and has helped me understand a lot about coding at a higher level. All through there are still problems I run into when I code(Mostly VS not playing nice), I feel like I can more easily handle these problems due to my better understanding of this project and coding in general. Working on this issue was similar to the last one I tackled so I spent extra time attempting to find different ways to code it and looking at different fetures I could add. A lot of these additional features were removed due to me wanting to keep my code simple and to the point but it was still fun to explore different avenues of coding and other proccesses.   

## Issue in Team Repo

![Image](https://github.com/CallumJSuth/Portfolio/blob/main/images/ss6-1.png)
