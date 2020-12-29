# flutter_notifications

A cross platform plugin for displaying local notifications. 


## Supported platforms
* **Android**


## Android Setup

```xml
<activity
    android:showWhenLocked="true"
    android:turnScreenOn="true">
```

### Example app
The `example` directory has a sample application that demo the features of this plugin.


## Initialisation

```dart
FlutterLocalNotificationsPlugin flutterLocalNotificationsPlugin =
    FlutterLocalNotificationsPlugin();
// initialise the plugin. app_icon needs to be a added as a drawable resource to the Android head project
const AndroidInitializationSettings initializationSettingsAndroid =
    AndroidInitializationSettings('app_icon');
final IOSInitializationSettings initializationSettingsIOS =
    IOSInitializationSettings(
        onDidReceiveLocalNotification: onDidReceiveLocalNotification);
final MacOSInitializationSettings initializationSettingsMacOS =
    MacOSInitializationSettings();
final InitializationSettings initializationSettings = InitializationSettings(
    android: initializationSettingsAndroid,
    iOS: initializationSettingsIOS,
    macOS: initializationSettingsMacOS);
await flutterLocalNotificationsPlugin.initialize(initializationSettings,
    onSelectNotification: selectNotification);
```

```dart
Future selectNotification(String payload) async {
    if (payload != null) {
      debugPrint('payload: $payload');
    }
    await Navigator.push(
      context,
      MaterialPageRoute<void>(builder: (context) => SecondScreen(payload)),
    );
}
```
