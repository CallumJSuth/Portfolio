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

```

## Summary of Test Code

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

The code I reviewed this week for checking stock levels of existing mission resources. It seems to meet the user and business goals, but there are a couple of things that need attention:

Sorting Option: The code allows for filtering resources by type and storage location, but it doesn't have a way to sort them. It would be great to add a sorting feature so that the resource list can be organized by quantity, location, or other relevant criteria. This will give a more detailed overview.

User-Friendly Interface: The code should prioritize creating a user-friendly interface to make it easy for users to understand the mission resources' overview. The current UI that is being used isn't tailered towards someone who didn't have a good understanding of the code itself. Changing the layout and adding temporary text to the search boxes in order to show what they do. 



## Reflection of Weekly Work 

This wweeks work has been a great reflections of the skills I learned last week. After having a lot of problems with VS and my code in general, I decided to take a slower approch to coding this porgram in order to give myself a better strucutre and understanding of the code I was creating. As I mentioned last week, modularity was my main focus as it had caused me problems last week. I was successful in creating code which was better structured and more understandable. 
