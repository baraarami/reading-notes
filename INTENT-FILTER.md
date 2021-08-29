# Intent Filters
![](https://google-developer-training.github.io/android-developer-fundamentals-course-concepts-v2/images/2-3-c-implicit-intents/implicit-intent.png)
## Allowing Other Apps to Start Your Activity

### What is the purpose of using intent-filter?
Allow other apps to start an another activity.

### How intent-filter works?

* When the app is installed on a device, the system identifies an intent filters and adds the information to an internal catalog of intents, which supported by all installed apps.
* When an app calls `startActivity()` or `startActivityForResult()`the system finds which activity can respond to the intent and then add an Intent Filter.
* The system may send a given Intent to an activity if that activity has an intent filter.


- How I allow other apps to start an another  activity ?
  -  add an `<intent-filter>` element in your manifest file for the corresponding <activity> element.
- How it works?
  - When the app is installed on a device, the system identifies an intent filters and adds the information to an internal catalog of intents.
  - Wich supported by all installed apps.
  - When an app calls `startActivity()` or `startActivityForResult()`, with an `implicit intent`, the system finds which activity (or activities) can respond to the intent.
1. Add an Intent Filter 
  - The system may send a given `Intent` to an activity if that activity has an intent filter fulfills the following criteria of the `Intent` object:
    - Action
      - A string naming the action to perform. Usually one of the platform-defined values such as ACTION_SEND or ACTION_VIEW.
    - Data
      - A description of the data associated with the intent.
    - Category
      - Provides an additional way to characterize the activity handling the intent, usually related to the user gesture or location from which it's started.
- Example: 
```
   <activity android:name="ShareActivity">
     <intent-filter>
        <action android:name="android.intent.action.SEND"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:mimeType="text/plain"/>
        <data android:mimeType="image/*"/>
     </intent-filter>
  </activity>
```
## Handle the Intent in Your Activity
```
  @Override
 protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    setContentView(R.layout.main);

    // Get the intent that started this activity
    Intent intent = getIntent();
    Uri data = intent.getData();

    // Figure out what to do based on the intent type
    if (intent.getType().indexOf("image/") != -1) {
        // Handle intents with image data ...
    } else if (intent.getType().equals("text/plain")) {
        // Handle intents with text ...
    }
  }
```
## Return a Result
```
  // Create intent to deliver some kind of result data
 Intent result = new Intent("com.example.RESULT_ACTION", Uri.parse("content://result_uri"));
 setResult(Activity.RESULT_OK, result);
 finish();
```
#
