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

## Review Changes 

## Issues That Arose

## Reflection of Weekly Work 

## Issue in Team Repo

![Image](https://github.com/CallumJSuth/Portfolio/blob/main/images/ss6-1.png)
