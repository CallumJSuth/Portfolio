# Project work 2

In week 9, you are continuing with the team project. Your portfolio entry should 
demonstrate how your software engineering practice is improving. It should include
much the same content as last week's:

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

In the reflective sections, try to identify things that you have done better this week. 
This could include, for example,

* Better application of the principles of clean code.
* Avoiding the repetition of previous mistakes.
* More comprehensive test coverage.
* Adoption of a more systematic personal workflow.
* Improved identification of problems in other people's code.
* etc.


## Summary of Issue 

The aim of this task is to allow users to easily see the health, location, and current assignment of team vehicles and equipment for mission objectives. The objective is to offer a  summary of mission vehicles and guarantee their accessibility for both support and operational tasks. The most important aspect of this program is to have a free-text search function which allows user's to search for data in each individual field. 

## Code and Commentary 

```
            <!-- Changed Horizontal StackLayout for search bars -->
            <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand">
                
                <!-- Entries for each individual search bar (VehicleReg, Health, Location,Deployment-->
                <Entry Placeholder="Search Vehicle Registration" x:Name="VehicleRegSearch" TextChanged="OnSearchTextChanged"/>

                <Entry Placeholder="Search Health" x:Name="HealthSearch" TextChanged="OnSearchTextChanged"/>

                <Entry Placeholder="Search Location" x:Name="LocationSearch" TextChanged="OnSearchTextChanged"/>

                <Entry Placeholder="Search Deployment" x:Name="DeploymentSearch" TextChanged="OnSearchTextChanged"/>
                
            </StackLayout>
```

This is the frontend code for each search bar this is required. This has two good examples of good coding practice, more specfically good UI design. The first of which is the addition of placeholder text. This placeholder text allows the user to clearly see what each search bar does in a simple and easy to understand way without the need for any extra unnecessary formatting. 

Secondly, is the appropriate naming of each entry. Giving each individual entry it's own name allows for good code readabilty. This means that when any future changes are needed, it will be a lot easier to make those changes now it is clear what all of elements are. 

```
        private void OnSearchTextChanged(object sender, TextChangedEventArgs e)
        {
            // Convert the search text to lowercase
            var searchText = e.NewTextValue.ToLower();

            // Filter the data based on search criteria 
            FilteredVehicleDescription = new ObservableCollection<VehicleInfo>(
                VehicleDescription.Where(v =>
                    v.VehicleReg.ToLower().Contains(searchText) ||
                    v.Health.ToString().Contains(searchText) ||
                    v.VehicleLocation.ToLower().Contains(searchText) ||
                    v.CurrentDeployment.ToLower().Contains(searchText))
            );

            // Update the ListView's ItemsSource with the filtered data
            ListView.ItemsSource = FilteredVehicleDescription;
        }
```

This is the backend code for the above frontend code.  Firstly, the search text is immediately converted to lowercase and also converted relevant properties to lowercase during comparison, ensuring a case-insensitive search, which is a good practice for user-friendly search functionality and preemptively avoids any user-input errors.

Another easy to point out example of good pratice is the clear and descriptive name of the method. From a glance it is easy to understand the purpose and subsequent function of this method.  

Finally, the use of "ObservableCollection" allows the fields shown to the user to be updated instantly as they are searching. This allows the UI to have real-time updates as the user is searching, meaning a good response between the elements and the user's needs. User experience is greatly improved by this level of responsiveness. 

## Summary of Test Code

```
    public void CollectionInit()
    {
        // Setting Page variable
        var page = new MainPage(); // Constructor will be tested

        // Checking correct initalization 
        Assert.NotNull(page.VehicleDescription);
        Assert.NotNull(page.FilteredVehicleDescription);


    }
```

This test makes sure that the MainPage class constructor properly initializes the VehicleDescription and FilteredVehicleDescription collections. It confirms that these collections are not null once the constructor is called. This is crucial to extremly important that the constructor sets up the MainPage object's initial state as intended and that the collections can be used for future data changes.

```
    public void SuccessfulCopying()
    {
        // Arrange
        var page = new MainPage();

        // Act

        // Assert
        Assert.Equal(page.VehicleDescription.Count, page.FilteredVehicleDescription.Count);

        // You can add more assertions to compare the data in both collections if needed
    }
```
This test checks if the constructor accurately duplicates the data from the VehicleDescription collection to the FilteredVehicleDescription collection. It compares the counts of both collections to show they have the same number of elements, meaning that the data has been successfully copied. This is crucial because it guarantees that the two collections are  identical, enabling later data manipulation of one collection without impacting the other.

## Review Changes 

During my review this week, I received feedback regarding my data binding. The primary change that was suggested was to address the issues arising from the design of my code, which were getting in the way of the data displaying properly. 

I dealt with this by simply adding one line of code to my backend .cs file. 
```
...
BindingContext = this;
...
```
This allowed my data on my Main .xaml page to properly access the data in the backend and display it properly. 

It was also suggested that I made my search bars more readable. I acomplished this by changing their orientation from horizontal to vertical (Allowing the search bars to be more easily read) and adding a label above each search box in order explain its purpose more clearly. 

## Issues That Arose

The code I reviewed this week for checking stock levels of existing mission resources. It seems to meet the user and business goals, but there are a couple of things that need attention.

Adding a sorting option: The code allows for filtering resources by type and storage location, but it doesn't have a way to sort them. It would be great to add a sorting feature so that the resource list can be organized by quantity, location, or other relevant criteria. This will give a more detailed overview.

UI : The code should prioritize creating a user-friendly interface to make it easy for users to understand the mission resources' overview. The current UI that is being used isn't tailered towards someone who didn't have a good understanding of the code itself. Changing the layout and adding temporary text to the search boxes in order to show what they do. 



## Reflection of Weekly Work 

This wweeks work has been a great reflections of the skills I learned last week. After having a lot of problems with VS and my code in general, I decided to take a slower approch to coding this porgram in order to give myself a better strucutre and understanding of the code I was creating. As I mentioned last week, modularity was my main focus as it had caused me problems last week. I was successful in creating code which was better structured and more understandable. 
