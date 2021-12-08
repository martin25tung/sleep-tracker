# Room - SleepQualityTracker app

This is the toy app for Lesson 6 of the [Android App Development in Kotlin course on Udacity](https://www.udacity.com/course/???).

## SleepQualityTracker

The SleepQualityTracker app is a demo app that helps you collect information about your sleep. 
* Start time
* End time
* Quality
* Time slept

This app demonstrates the following views and techniques:
* Room database
* DAO
* Coroutines

It also uses and builds on the following techniques from previous lessons:
* Transformation map
* Data Binding in XML files
* ViewModel Factory
* Using Backing Properties to protect MutableLiveData
* Observable state LiveData variables to trigger navigation

## Screenshots

![Screenshot1](screenshots/sleep_quality_tracker_start.png)
![Screenshot2](screenshots/sleep_quality_tracker_stop.png)
![Screenshot3](screenshots/sleep_quality_tracker_quality.png)

## How to use this repo while taking the course


Each code repository in this class has a chain of commits that looks like this:

![listofcommits](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58befe2e_listofcommits/listofcommits.png)

These commits show every step you'll take to create the app. Each commit contains instructions for completing the that step.

Each commit also has a **branch** associated with it of the same name as the commit message, as seen below:

![branches](https://d17h27t6h515a5.cloudfront.net/topher/2017/April/590390fe_branches-ud855/branches-ud855.png
)
Access all branches from this tab.

![listofbranches](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58befe76_listofbranches/listofbranches.png
)


![branchesdropdown](https://d17h27t6h515a5.cloudfront.net/topher/2017/April/590391a3_branches-dropdown-ud855/branches-dropdown-ud855.png
)

The branches are also accessible from the drop-down in the "Code" tab.


## Working with the Course Code

Here are the basic steps for working with and completing exercises in the repo.

The basic steps are:

1. Clone the repo.
2. Check out the branch corresponding to the step you want to attempt.
3. Find and complete the TODOs.
4. Optionally commit your code changes.
5. Compare your code with the solution.
6. Repeat steps 2-5 until you've gone trough all the steps to complete the toy app.


**Step 1: Clone the repo**

As you go through the course, you'll be instructed to clone the different exercise repositories, so you don't need to set these up now. You can clone a repository from github in a folder of your choice with the command:

```bash
git clone https://github.com/udacity/REPOSITORY_NAME.git
```

**Step 2: Check out the step branch**

As you go through different steps in the code, you'll be told which step you're on, as well as a link to the corresponding branch.

You'll want to check out the branch associated with that step. The command to check out a branch would be:

```bash
git checkout BRANCH_NAME
```

**Step 3: Find and complete the TODOs**

Once you've checked out the branch, you'll have the code in the exact state you need. You'll even have TODOs, which are special comments that tell you all the steps you need to complete the exercise. You can easily navigate to all the TODOs using Android Studio's TODO tool. To open the TODO tool, click the button at the bottom of the screen that says TODO. This will display a list of all comments with TODO in the project. 

We've numbered the TODO steps so you can do them in order:
![todos](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58bf00e7_todos/todos.png
)

**Step 4: Commit your code changes**

After You've completed the TODOs, you can optionally commit your changes. This will allow you to see the code you wrote whenever you return to the branch. The following git code will add and save **all** your changes.

```bash
git add .
git commit -m "Your commit message"
```

**Step 5: Compare with the solution**

Most exercises will have a list of steps for you to check off in the classroom. Once you've checked these off, you'll see a pop up window with a link to the solution code. Note the **Diff** link:

![solutionwindow](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58bf00f9_solutionwindow/solutionwindow.png
)

The **Diff** link will take you to a Github diff as seen below:
![diff](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58bf0108_diffsceenshot/diffsceenshot.png
)

All of the code that was added in the solution is in green, and the removed code (which will usually be the TODO comments) is in red. 

You can also compare your code locally with the branch of the following step.

## Report Issues
Notice any issues with a repository? Please file a github issue in the repository.


## Creating the SleepNight Entity
1. In the database package, find and open the SleepNight.kt file.
2. Create the SleepNight data class with parameters for an ID, start time and end time in milliseconds, and a numerical sleep quality rating
3. Annotate the data class with @Entity, and name the table daily_sleep_quality_table
4. Identify the nightId as the primary key by annotating it with @PrimaryKey, and set the autoGenerate parameter to true:
5. Annotate the remaining properties with @ColumnInfo and customize their names as shown below.
6. Build and run your code to make sure it has no errors.


## DAO - SleepDatabaseDao
1. Create an interface SleepDatabaseDao and annotate it with @Dao
2. Add an @Insert annotation, and an insert() function that takes one SleepNight.
3. In the same way, add an @Update annotation with an update() function for one SleepNight
4. Add a @Query annotation with a function get() that takes a Long key argument and returns a nullable SleepNight
5. Add a parameter to @Query.
6. Add another @Query with a clear() function and a SQLite query to delete everything from the daily_sleep_quality_table
7. Add a @Query to getAllNights()
8. Add a @Query to getTonight(). Make the returned SleepNight nullable, so that it can handle if the table is empty.
9. Run your app to make sure it has no errors.


## Creating a Room Database
1. In SleepDatabase.kt, create an abstract class that extends RoomDatabase.
2. Declare an abstract value that returns the SleepDatabaseDao
3. Below, define a companion object
4. Inside the companion object, declare a private nullable variable INSTANCE for the database.
5. Below, still inside the companion object, define the getInstance()method with a Context parameter, which will return a reference to the SleepDatabase:
6. Inside getInstance() add a synchronized{} block, and pass in this
7. Inside the synchronized block, copy the current value of INSTANCE to a local variable, instance
8. At the end of the synchronized block, still inside the block, return instance
9. Above the return statement, check if there is already a database stored in instance.
10. Invoke Room’s databaseBuilder and supply the context that we passed in, the database class, and a name for the database
11. Add the required migration strategy to the builder
12. And call .build():
13. Assign INSTANCE = instance as the final step inside the if statement
14. Your final code should look like this
15. Build and run your code to make sure there are no basic errors.


## Testing the Room Database
1. Use the solution code from the previous exercise, which you can download here: Step.03-Solution-Create-RoomDatabase. Work from that code, or copy the test file to your code.
2. In the androidTest folder, open the SleepDatabaseTest file.
3. Uncomment the code.
4. Right-click on the test file in the Project view and choose Run.
5. After the app builds and runs, verify in the SleepDatabaseTest pane that all the tests have passed.


## Adding a ViewModel
1. In the sleeptracker package, open SleepTrackerViewModel.kt.
2. Inspect the provided SleepTrackerViewModel class definition that extends AndroidViewModel().
3. In the sleeptracker package, open SleepTrackerViewModelFactory.kt
4. In the body of create(), we check that there is a SleepTrackerViewModel class available, and if there is, return an instance of it. Otherwise, we throw an exception.
5. In the SleepTrackerFragment, in onCreateView(), get a reference to the application context
6. Define a dataSource.
7. Create an instance of the viewModelFactory.
8. Get a reference to the SleepTrackerViewModel
9. Your finished code in the SleepTrackerFragment should look like this
10. In SleepTrackerFragment inside onCreateView()
11. In fragment_sleep_tracker.xml
12. In SleepTrackerFragment inside onCreateView()
13. Finally, as always, make sure your code builds and runs without errors.


## Coroutines for Long-running Operations
1. Open the SleepTrackerViewModel.kt file.
2. Define viewModelJob and assign it an instance of Job
3. Override onCleared() and cancel all coroutines.
4. Define a uiScope for the coroutines
5. Define a variable, tonight, to hold the current night, and make it MutableLiveData
6. Define a variable, nights. Then getAllNights() from the database and assign to the nights variable
7. To initialize the tonight variable, create an init block and call initializeTonight(), which you'll define in the next step
8. Implement initializeTonight(). In the uiScope, launch a coroutine.
9. Implement getTonightFromDatabase(). Define is as a private suspend function that returns a nullable SleepNight, if there is no current started sleepNight.
10. Inside the function body, return the result from a coroutine that runs in the Dispatchers.IO context:
11. Let the coroutine get tonight from the database. If the start and end times are the not the same, meaning, the night has already been completed, return null. Otherwise, return night
12. Implement onStartTracking(), the click handler for the Start button
13. Inside onStartTracking(), launch a coroutine in uiScope
14. Inside the coroutine, create a new SleepNight, which captures the current time as the start time
15. Call insert() to insert it into the database. You will define insert() shortly
16. Set tonight to the new night
17. Define insert() as a private suspend function that takes a SleepNight as its argument
18. For the body of insert(), launch a coroutine in the IO context and insert the night into the database

### Add Click Handlers for the Buttons
1. Add onStopTracking() to the view model. Launch a coroutine in the uiScope.
2. Implement update() using the same pattern as insert()
3. Analogously, implement onClear() and clear()
4. Open fragment_sleep_tracker.xml and add click handlers to the three buttons

### Display the data
1. Add code to transform nights into a nightsString using the formatNights() function from Util.kt:
2. In fragment_sleep_tracker.xml, in the TextView, in the android:text property, replace the resource string with a reference to nightsString
3. In Util.kt and uncomment the commented code.
4. Rebuild and run your code.

## Recording Sleep Quality
1. Inspect the provided SleepQualityFragment.kt.
2. Inspect the provided fragment_sleep_quality.xml.
3. Open navigation.xml and inspect the code.
4. Open SleepTrackerViewModel.kt.
5. In SleepTrackerViewModel.kt, in onStopTracking() set a LiveData that changes when you want to navigate.
6. Add a doneNavigating() function that resets the event.
7. In the click handler for the STOP button, onStopTracking(), trigger this navigation
8. In the SleepTrackerFragment, in onCreateView(), add an observer for navigateToSleepQuality.
9. Inside the observer block, navigate and pass along the ID of the current night, and then call doneNavigating()
10. Build and run your app. Click START, then click STOP, which should take you to the SleepQualityFragment screen.

### Record the Sleep Quality
1. In the sleepquality package, open SleepQualityViewModel.kt.
2. Create a SleepQualityViewModel that takes sleepNightKey and database as arguments
3. Define a Job, uiScope, and override onCleared(), as previously
4. To navigate back to the SleepTrackerFragment, analogously implement navigateToSleepTracker and _navigateToSleepTracker, as well as doneNavigating()
5. Now, create one click handler that you will use for all the smiley sleep quality images, onSetSleepQuality().
6. Create a SleepQualityViewModelFactory.
7. Open SleepQualityFragment.
8. Get the arguments
9. Get the dataSource
10. And create a factory passing in the dataSource and sleepNightKey
11. Get a SleepQualityViewModel reference:
12. Add the sleepQualityViewModel to the binding object
13. And add the observer, as before
14. Open fragment_sleep_quality.xml and add a variable for the SleepQualityViewModel to the <data> block
15. Add a click handler like the one below to each image
16. Clear cache, rebuild your app, and make sure it runs without errors.


## Button States and SnackBar
1. Open fragment_sleep_tracker.xml.
2. Add the enabled property to each button, and give it the value of a state variable
3. Open SleepTrackerViewModel.kt and create three corresponding variables.
4. Run your app, and that's all there is to it!

### Snackbar
1. In the SleepTrackerViewModel, create the encapsulated event
2. Then implement doneShowingSnackbar()
3. In the SleepTrackerFragment, add an observer
4. Display the snackbar and immediately reset the event
5. To trigger the event, in onClear(), set the event value to true
6. Build and run your app!
