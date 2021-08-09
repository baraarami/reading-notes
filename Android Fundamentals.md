# Android Fundamentals
![](http://1.bp.blogspot.com/-ox9b54FkhHo/UdqduQ0dEaI/AAAAAAAABj4/nGZnO31wu7g/s1600/Android+Application+Fundamentals+and+Components.jpg)

* What is Android security features?
  - The Android operating system is a multi-user Linux system in which each app is a different user.
  - the system assigns each app a unique Linux user ID.
  - Each process has its own virtual machine (VM).
  - every app runs in its own Linux process. 
* Mintion ways for an app to share data with other apps and for an app to access system services:
  - It's possible to arrange for two apps to share the same Linux user ID, in which case they are able to access each other's files. 
  - An app can request permission to access device data such as the device's location, camera, and Bluetooth connection.
## App components
![App](https://user-images.githubusercontent.com/79080942/128704790-f442ee9a-2782-4211-a3a7-3c860bfbe084.png)

 - Activity: It is the the UI of the Android App.
 - Services: We use the services to add logic to our apps.
 - Broadcast receivers: using to deliver events to the app outside of a regular user flow.
 - Content providers: Manages a shared set of app data that you can store in the file system.
### Activities
- An activity is the entry point for interacting with the user. It represents a single screen with a user interface.
- An activity facilitates the following key interactions between system and app:
  - Keeping track of what the user currently cares about (what is on screen).
  - Knowing that previously used processes contain things the user may return to (stopped activities).
  - Helping the app handle having its process killed.
  - Providing a way for apps to implement user flows between each other.
  ### Services
- is a general-purpose entry point for keeping an app running in the background for all kinds of reasons.
- Syncing data in the background or playing music also represent two different types :
  - Music playback is something the user is directly aware of, so the app tells the system this by saying it wants to be foreground with a notification to tell the user about it.
  - A regular background service is not something the user is directly aware as running, so the system has more freedom in managing its process.
 ### Broadcast receivers
- A broadcast receiver is a component that enables the system to deliver events to the app outside of a regular user flow.
- A broadcast receiver is implemented as a subclass of `BroadcastReceiver` and each broadcast is delivered as an `Intent` object.
### Content providers
- A content provider manages a shared set of app data that you can store in the file system, in a SQLite database, on the web, or on any other persistent storage location that your app can access.
-  The Android system provides a content provider that manages the user's contact information. As such, any app with the proper permissions can query the content provider, such as ContactsContract.Data, to read and write information about a particular person.
- What the system can do in managing an app ?
 - Assigning a URI doesn't require that the app remain running, so URIs can persist after their owning apps have exited. The system only needs to make sure that an owning app is still running.
 - These URIs also provide an important fine-grained security model. 
## Activating components
- **There are separate methods for activating each type of component:**
  - You can start an activity or give it something new to do by passing an `Intent` to `startActivity()` or `startActivityForResult()` (when you want the activity to return a result).
  - With `Android 5.0 (API level 21)` and later, you can use the `JobScheduler` class to schedule actions. For earlier `Android` versions, you can start a service (or give new instructions to an ongoing service) by passing an `Intent` to `startService()`. You can bind to the service by passing an Intent to `bindService()`.
  - You can initiate a broadcast by passing an `Intent` to methods such as `sendBroadcast()`, `sendOrderedBroadcast()`, or `sendStickyBroadcast()`.
  - You can perform a query to a content provider by calling `query()` on a `ContentResolver`.
 ## The manifest file
 - What manifest can do ?
   - declare all its app components in this file `AndroidManifest.xml.`.
   - Identifies any user permissions the app requires.
   - Declares the minimum API Level required by the app.
   - Declares hardware and software features used or required by the app.
   - Declares API libraries the app needs to be linked against.

  ## App resources
   - Android app is composed of more than just code—it requires resources that are separate from the source code, such as images, audio files, and anything relating to the visual presentation of the app.
   - For every resource that you include, the SDK build tools define a unique integer ID, which you can use to reference the resource from your app code or from other resources defined in XML.
   - One of the most important aspects of providing resources separate from your source code is the ability to provide alternative resources for different device configurations.
   - Android supports many different qualifiers for your alternative resources.
   - Qualifier - a short string that you include in the name of your resource directories in order to define the device configuration for which those resources should be used.
