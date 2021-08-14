# Espresso
![](https://riis.com/wp-content/uploads/2015/09/android-espresso-code-testing-1536x864.jpg)
###  What is Espresso
- Espresso is a testing framework for Android to make it easy to write reliable user interface tests.
- Espresso has basically three components:
* ViewMatchers - allows to find view in the current view hierarchy.
* ViewActions - allows to perform actions on the views.
* ViewAssertions - allows to assert state of a view.

- Espresso Test Recorder tool - lets you create UI tests for your app without writing any test code. Takes the saved recording and automatically generates a corresponding UI test that you can run to test your app. Writes tests based on the Espresso Testing framework, an API in AndroidX Test.
- Espresso automatically synchronizes your test actions with the user interface of your application. The framework also ensures that your activity is started before the tests run. - It also lets the test wait until all observed background activities have finished.
- It is intended to test a single application but can also be used to test across applications. If used for testing outside your application, you can only perform black box testing, as you cannot access the classes outside of your application.
### Synchronization capabilities
Each time your test invokes onView(), Espresso waits to perform the corresponding UI action or assertion until passing these checks:
- Checks
  - The message queue is empty.
  - There are no instances of `AsyncTask` currently executing a task.
  - All developer-defined `idling resources` are idle.
### What are the Espresso basically components? 

`ViewMatchers` : allows inding view in the current view hierarchy

`ViewActions` : allows performing actions on the views

`ViewAssertions` : allows asserting state of a view
### Packages
|Package|Component|
|-------|---------|
|`espresso-core`|core and basic `View` matchers, actions, and assertions.|
|`espresso-web`|resources for `WebView` support|
|`espresso-idling-resource`|Espresso's mechanism for synchronization with background jobs|
|`espresso-contrib`|External contributions that contain `DatePicker`, `RecyclerView` and Drawer actions, accessibility checks, and `CountingIdlingResource`.|
|`espresso-intents`|Extension to validate and stub intents for hermetic testing.|
|`espresso-remote`|Location of Espresso's `multi-process`functionality|
#

### What are the basic components on Espresso?
- `ViewMatchers` : allows inding view in the current view hierarchy.
- `ViewActions` : allows performing actions on the views.
- `ViewAssertions` : allows asserting state of a view.

## Espresso basics:

### What are the main components of Espresso include?
- Espresso : `onView()` and `onData()`. exposes APIs that are not tied to any view, such as `pressBack()`.
- ViewMatchers – A collection of objects that implement the Matcher<? super View> interface.
- ViewActions – ViewAction objects that can be passed to the ViewInteraction.perform() method.
- ViewAssertions – ViewAssertion objects that can be passed the ViewInteraction.check() method.

## Espresso basics
### API components
- What are the main components of Espresso include?
  - Espresso :  `onView() and onData()`. exposes APIs that are not tied to any view, such as `pressBack()`.
  - ViewMatchers – A collection of objects that implement the Matcher<? super View> interface.
  - ViewActions – ViewAction objects that can be passed to the ViewInteraction.perform() method.
  - ViewAssertions – ViewAssertion objects that can be passed the ViewInteraction.check() method.
- ***Code Example*** :
```
onView(withId(R.id.my_view))
    .perform(click())
    .check(matches(isDisplayed()));
```

- ***NOTE***: Continue introducing types and Code examples tests in [this section](https://developer.android.com/training/testing/espresso/basics#finding-view).
#

## Create UI tests with Espresso Test Recorder:
- Record UI interactions
  - Click Run > Record Espresso Test.
  - In the Select Deployment Target window, choose the device on which you want to record the test. If necessary, create a new Android Virtual Device. Click OK.
  - Espresso Test Recorder triggers a build of your project, and the app must install and launch before Espresso Test Recorder allows you to interact with it. 
 - Add assertions to verify UI elements
   - text is: Checks the text content of the selected View element
   - exists: Checks that the View element is present in the current View hierarchy visible on the screen
   - does not exist: Checks that the View element is not present in the current View hierarchy
 - Save a recording
   - Click Complete Recording. The Pick a test class name for your test window appears.
   - Espresso Test Recorder gives your test a unique name within its package based on the name of the launched activity.
   - The file automatically opens after Espresso Test Recorder generates it, and Android Studio shows the test class as selected in the Project window of the IDE
 - Run an Espresso test locally:
  - chick these steps ay [this section](https://developer.android.com/studio/test/espresso-test-recorder#run-an-espresso-test-locally)

















