# Week 3 - Workflow 

This week, our group was tasked with choosing an appropriate work flow, implementing it and further developing it by adding tasks that will be individually completed by each member. 

We choose the recommended workflow of Github Flow. 

We were also tasked with individually getting more familiar with Github's workflow tools, allowing us to more easily utilise the resources Github offers. This consisted of showing that we were able to use the following processes : 

![Image](https://github.com/CallumJSuth/Portfolio/blob/main/images/ss2-2.png)



# Proof of Work

## ------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Progressing through project 

As seen below, I decided to go with "Maintain Reference Values For System Types" as the task I would be working on : 
![Image](https://github.com/CallumJSuth/Portfolio/blob/main/images/ss2-3.png)

I first moved this task to the in development list and assigned it to myself before I started in order to ensure no one else in my team was attempting to complete the same task as me : 

![Image](https://github.com/CallumJSuth/Portfolio/blob/main/images/ss2-4.png)

As I progressed on with my task (Further details in section below ) I proceeded to move the task through each appropriate stage. 

Moving the task to the "In Review" section was the next step as by this point in development I had finished my code and was ready to begin testing and optimizations. 

![Image]()

Next was the testing stage once I was done reviewing the code. 

![Image)()

And finally to the done section once everything had been completed and I was ready to submit this portfolio. 

![Image]()


## Completing a Task

While working on this task, I used Github's tools through Visual Studio. This was purely for ease of access and simplicity while working on the given job. 

Firstly, I created a branch in order to deviate my changes from the main code and then later push these changes to the main repository. :

![Image](https://github.com/CallumJSuth/Portfolio/blob/main/images/ss2-5.png)

Once this branch had been created the first thing I did was create the structure of my database and named it "structureSTRV.cs' '. This will outline how data is stored and indexed. I got the template for this structure from the support files already provided from my repo. 

![Image]()

Once this was done, I created the database itself by following the provided tutorial and appropriately editing the fields to match my files. The only real change I made to the provided code was the removal of the line that required a boolean value in order to check if there was a value in the field. 

![Image]()

Next I organised my file structure and created the files I would be using throughout this project as well as the project page. During this stage I created the xaml file that would house the code for my value editing UI as well as the backend for it. These files are called STRV.xaml and STRV.xaml.cs respectively. 

![Image]()   

Due to me pulling this code from our group repository early, I also had to create a constants.cs file. This has been added to our repository since but I thought it was worth mentioning. 

![Image]()

Now I moved onto coding my UI itself. I used many resources and got help from coursemates ( Daniel Miller was exceptionally helpful, big thank you to him) in order to create this code. It follows a basic structure using buttons and the "Picker'' tag in order to display a short list of values to choose from. These values can be interacted with in order to meet the requirements specified in my chosen task. 

![Image]()

![Image]()

I am skipping over a lot of debugging and tinkering however for the purposes of this portfolio talking about every issue I ran into would drag on for far too long. However at this stage my UI and backend database has been completed and I am ready to start testing my program and its functions. Despite being simple, my UI meets all of the requirements of my task and is presented clearly. 

![Image]()

At this stage I am moving onto testing. Further information about this stage can be found in the section below. 


The last thing to cover before moving on is the Definition of Done (DoD). Due to the length of time it has taken me to complete this task(Never working with C# before) all of my code has been rigorously bug tested and analysed as I spend quite a long time on it, so the unit test coverage is easily above 80%. All of the required criteria have been met to my knowledge, I cannot see any defects in my code either and my documentation is up to date. As for functionality testing, I have a section below which covers that. Definition of Done has been met.   


Now my development task has been completed on my branch I can start looking at committing my changes and submitting a pull request with appropriate comments. This will be the last step of my portfolio entry. 

![Image]()



## Testing 

When approaching testing, there is little to actually be tested. The above screenshots already prove that my UI loads correctly so the only thing I really have to test is the functionality of my Database and Ui. 

Below is a link to a Word Document that shows my testing processes : 

![Testing Document](https://1drv.ms/w/s!AvGyrAKUKVKFgpge0wyXF_cgTx1-zA?e=UMpzMa)



