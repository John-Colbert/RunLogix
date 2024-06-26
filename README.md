# Run Logix

# General Description

Run Logix is a simple and free app that allows for planning and tracking of running workouts with detailed performance metrics down to the segment level. The reporting includes a Summary with a distance chart and a running diary, and a Performance Document with the detailed segment metrics.   

The app allows for running routes to be pre-planned including multiple intervals, to which the subsequent running results are compared to provide performance data on each segment. Currently the app allows for time-based run planning and parses running data from ".gpx" files exported from Apple Health Data. Future versions will support other planned routines (i.e. distance-based, pace-based, or maybe even heart-rate-based workouts), and other ".gpx" files from other sources. This app is still under development, but is available now with the mentioned basic functionality.

# Why Run Logix

I developed this app originally as running apps generally do not provide performance information at the interval level (called segments in the app), so I was not informed by my running app at how well I performed on each interval during a multiple interval run. I developed a process to use my iWatch workout app to program the time-based interval runs, and then import the data for detailed reporting. I was still able to use my running app, but this gave me the additional information I wanted.

# Intended Audience

At this time, Run Logix is currently intended to be used by developers, who are runners themselves, as the app is not yet well documented and requires code manipulation to use. Eventually, better instructions will be available to non-developers with instructive matarial. The goal is to allow anybody free access to full running analysis and reporting without the need to fully understand software programming. Just a copy / paste and changing a few pieces of info will create a new run workout.

# Contributions

We would be happy to add contributing developers to the effort.  If you would like to contribution please contact us via Git Hub.

# Why Nytril

Nytril provides immediate output which makes it suitable for this app and very easy to use for non-developers. Nytril also has built-in unit conversion capabilities, which makes running performance tasks simpler to develop. Nytril is a full-featured programming language and IDE with immediate output that displays in the right pane. It is designed for professional documentation development and hosting, but is useful for purposes such as this as the output requires no special knowledge or extra effort. 

# How to Use

1. Download and Install Nytril Desktop IDE. Go to [Nytril.com](https://www.nytril.com) and select the platfrom (Windows or Mac), then download and install.
2. Clone or download this code from GitHub and place in the folder of your choice.
3. Open Nytril and select the menu option "Repo", then "New Repository."
    a. Under "Local Folder", click the browse button and navigate to the "Run Logix" folder where you placed it in the previous step.
    b. The "Repository Name" will be changed to the folder name.  Adjust it if you would like. 
    c. Leave "Language Files" as is. 
    d. Click "OK".
4. The "Starting Project" dialog will appear.
    a. Under "Main File" the path and filename should already be correct. If not, browse to the "Run Logix" folder and select "Main.nytril."
    b. Under "Name" change the name to something useful, such as "Run Logix." This is the friendly name of the project within the local repository. 
    c. Click "OK".
5. The project will load, build and run. The code will be on the left and the output on the right.
6. Select the "Documents" menu option
    a. Click on a document to view the output. At this time, there are two choices "Summary" and "Performance to Target."

# How to add or modify a run workout

The "Main" document will be loaded by default. Place the cursor on the word "Workouts" in the includes section and press "F12". That will open the "Workouts" file.

With the "Workouts" file open:
1. Take note of the samples
    a. The first section establishes an array of workoutClasses.  These are the workouts discussed in step b. 
        i. The constructor takes a date and notes. When creating a new future run, add the date and leave the notes out -- you can add notes after you performed the run.
    b. Note the repeating classes that start with Interval1HR_5x, all inhereting WorkoutClass.
        i. In the constructor, the date is sent the WorkoutClass, and then the metrics for the run are established. 
        ii. A segement is a running interval that has a friendly name, a time to run, and a target pace.
        iii. Repeating intervals are also shown in the examples, where an interval is instatiated with the number of times to repeat, for which segments are added.  Those segments will be repeated in order for the number of times established.
2. Create a workout
    a. Copy one of the sample classes, such as the "Interval1HR_5x" class and paste it at the bottom or onto a new line.
    b. Change the class name to whatever you want, and change the run metrics to whatever configuration you want.
3. Add workout to list
    a. Add the workout to the workouts array in the top section of code "readonly WorkoutClass[] RunningWorkouts..." following the way the examples were created. Add the date that you will do the workout in the constructor.
4. Clear the examples.
    a. Now that you have your own workout, either clear out the examples, or comment them out if you want to keep them for reference.
5. Note the output.
    a. Take note that the output will now show the run in the list with the target data.  It is now waiting for the performance data to come in.

# How to add the performance data

1. Use your iWatch or iPhone to record your run. This process may also work if a different device is synced with an iPhone, but that has not been tested.
    a. Notably, it does not matter whether you use a programmed "Workout" run on the iWatch or iPhone, as the app reads the ".gpx" file data that contains the same basic information regardless of whether a programmed run was used (such as pacer workout).
2. After the run, use your iPhone to export your health data. Transfer the output to your computer.
3. Either copy the entire "apple_health_export" to the "Run Logix" folder -- replacing the existing one -- or find your ".gpx" file under "apple_health_export/workout_routes/" and copy it. The filename will include the date with the ending time of the workout. Paste the file into the "Run Logix/apple_health_export/workout_routes" folder.
4. Press "F5." The app will find the file by the date in the name and use it to compute the performance values.


