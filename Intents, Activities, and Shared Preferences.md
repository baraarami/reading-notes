# Intents, Activities, and SharedPreferences
## Understand Tasks and Back Stack
- What is a task ?
  - It is a collection of activities that users interact with when performing a certain job.
  - When starting a new activity in is adding to the stack works, and if you start another one then want to go back to the previoce one, you cane do that be back which will let the user get back to the previous task in the stack works.
  
- How the back stack works ?
  - When the user presses the Back button, that new activity is finished and popped off the stack .
  - the current activity is popped from the top of the stack (the activity is destroyed) and the previous activity resumes (the previous state of its UI is restored).
  - As such, the back stack operates as a **`last in, first out`** object structure.
  - check [this](https://youtu.be/MvIlVsXxXmY)
  - ![](https://img-blog.csdnimg.cn/20210130153857479.png)
##### **NOTES :**
- while some task is received by user interaction in the foreground,other tasks is in the background, waiting to be resumed.

- Multiple tasks can be held in the background at once.
- Activities in the back stack are never rearranged, if your app allows users to start a particular activity from more than one activity, a new instance of that activity is created and pushed onto the stack .
 ## Managing Tasks
- How can  you start an activity whitout creating a new instance on top of the back stack?
  - with attributes in the `<activity>` manifest element and with flags in the intent that you pass to `startActivity()`.
  - principal `<activity>` attributes  can be used.
    - `taskAffinity`
    - `launchMode`
    - `allowTaskReparenting`
    - `clearTaskOnLaunch`
    - `alwaysRetainTaskState`
    - `finishOnTaskLaunch`
  - principal intent flags you can use are:
    - `FLAG_ACTIVITY_NEW_TASK`
    - `FLAG_ACTIVITY_CLEAR_TOP`
    - `FLAG_ACTIVITY_SINGLE_TOP`
## Defining launch modes
- `launchMode` attribute specifies an instruction on how the activity should be launched into a task.
  - launchMode attribute:
    - `standard` : The system creates a new instance of the activity in the task from which it was started and routes the intent to it .
    - `singleTop`: If an instance of the activity already exists at the top of the current task, the system routes the intent to that instance through a call to its onNewIntent() method .
    - `singleTask` : The system creates a new task and instantiates the activity at the root of the new task.
    - `singleInstance` : Same as "singleTask", except that the system doesn't launch any other activities into the task holding the instance.
  ##### **NOTE :** `FLAG_ACTIVITY_CLEAR_TOP` is most often used in conjunction with `FLAG_ACTIVITY_NEW_TASK.` When used together, these flags are a way of locating an existing activity in another task and putting it in a position where it can respond to the intent.
  - Handling affinities
    - You can modify the affinity for any given activity with the `taskAffinity` attribute of the `<activity>` element.
    - The `taskAffinity` attribute takes a string value, which must be unique from the default package name declared in the `<manifest>` element
  - Clearing the back stack
    - `alwaysRetainTaskState` : If this attribute is set to `true` in the root activity of a task, the default behavior just described does not happen.
    - `clearTaskOnLaunch` : If this attribute is set to "true" in the root activity of a task, the task is cleared down to the root activity whenever the user leaves the task and returns to it. 
    - `finishOnTaskLaunch` : This attribute is like clearTaskOnLaunch, but it operates on a single activity, not an entire task.
  ##### Example : OF Starting a task
```
  <activity ... >
    <intent-filter ... >
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
    ...
</activity>
```
#
# Save key-value data
![](https://i.ytimg.com/vi/fJEFZ6EOM9o/sddefault.jpg)
- Get a handle to shared preferences
- Use the SharedPreferences APIs when you have a relatively small collection of key-values that you'd like to save.
SharedPreferences object - points to a file containing key-value pairs and provides simple methods to read and write them. Each SharedPreferences file is managed by the framework and can be private or shared.
Can create a new shared preference file or access an existing one by calling one of these methods:
getSharedPreferences() — use this if you need multiple shared preference files identified by name, which you specify with the first parameter. You can call this from any Context in your app.
getPreferences() — use this from an Activity if you need to use only one shared preference file for the activity. Because this retrieves a default shared preference file that belongs to the activity, you don't need to supply a name.
To write to a shared preferences file, create a SharedPreferences.Editor by calling edit() on your SharedPreferences. Pass the keys and values you want to write with methods such as putInt() and putString(). Then call apply() or commit() to save the changes.
To retrieve values from a shared preferences file, call methods such as getInt() and getString(), providing the key for the value you want, and optionally a default value to return if the key isn't present.

 ##### Example Code :
```
Context context = getActivity();
SharedPreferences sharedPref = context.getSharedPreferences(
        getString(R.string.preference_file_key), Context.MODE_PRIVATE);
```
##### to share preferences...
```
SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
```
- Write to shared preferences
 ##### Example Code :

```
SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
SharedPreferences.Editor editor = sharedPref.edit();
editor.putInt(getString(R.string.saved_high_score_key), newHighScore);
editor.apply();
```
- Read from shared preferences
##### Example Code :

```
SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
int defaultValue = getResources().getInteger(R.integer.saved_high_score_default_key);
int highScore = sharedPref.getInt(getString(R.string.saved_high_score_key), defaultValue);
```
