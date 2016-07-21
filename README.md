# Nestlean SDK v1.1.0  

## Android Integration

1. Clone or download aar file

2. Copy aar file to your 'libs' folder

3. Add "libs" folder as a repository by adding 'flatDir' to main project's build.gradle file:

  ```
  allprojects {
  repositories {
    jcenter()
    flatDir {
     dirs 'libs'
    }
  }
  }
  ```
  
4. Add aar file to dependencies(app module build.gradle):

  `compile(name: 'NestleanSDK-1.1.0', ext: 'aar')`
  
5. Add Manifest Permissions

  *INTERNET* is the only mandatory permission. It's already in aar manifest and will be added to your project automatically.
  
  `<uses-permission android:name="android.permission.INTERNET" />`
  
  *READ_EXTERNAL_STORAGE* is optional, it is used to read files from gallery in feedback feature. If you will not add it, you still can use feedback feature, but without screenshots.
  
  `<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>`
  
  *ACCESS_NETWORK_STATE* is optional, it is used to get information about connection type and availability. If you will not add it, you will not see such information in reports.
  
  `<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>`
  
  *ACCESS_FINE_LOCATION* is optional, it is used to get device gps location. If you will not add it, you will not see such information in reports.
  
  `<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>`

6. Initialization
   In order to initialize Nestlean SDK you need to call the following method:
   
   `Nestlean.init(activity, "sdk_token");`
   
   By default all the screens are being submitted automatically but if you want to specify a screen:
   
   `Nestlean.screen("screen_name");`
   
   To populate your app with custom events for advanced tracking, you need to call the method:
   
   `Nestlean.event("event_name");`

   You may know even more about your app with adding custom parameters to the event:
   
   ```
   HashMap<String, String> data = new HashMap<>();
   data.put("key", "value");
   Nestlean.event("event_name", data);
   ```
