Pivotal Mobile Services Suite Push SDK Samples for Android
==========================================================

Push SDK Usage
--------------
For more information please visit the [docs site](https://github.com/cfmobile/docs-pushnotifications-android)


Push Demo Application
---------------------

The Push Demo Application is an example of the simplest application possible that uses the Pivotal Mobile Services Suite
Push Client SDK.  At this time, it only demonstrates how to register for push notifications.

This demo application registers for push notifications in the Activity object in order to make it easier to display the
output on the screen.  It is probably more appropriate for you to register for push notifications in your Application
object instead.

This application is set up to receive push messages via the `PushService` class.  These
messages are not displayed in the activity window, but they will display a status bar notification.

Push Sample Application
-----------------------

There is a small sample application included in this repository to demonstrate and exercise the features in the Push
Client SDK.

You can use this sample application to test registration against Google Cloud Messaging (GCM) and the Pivotal Mobile Services Suite
back-end server for push messages.  Any push messages that are received are printed to the log window.  Although not
currently supported by the library itself, you can also send push messages with the sample application itself.

At this time, the sample application uses a dummy project on Google Cloud Console.  It is recommend that you create your
own test Google API Project by following the directions at http://developer.android.com/google/gcm/gs.html.

You can save your own project details by editing the values in the sample project's `push_default_preferences.xml` resource files.

Watch the log output in the sample application's display to see what the Push SDK is doing in the background.  This
log output should also be visible in the Android device log (for debug builds), but the sample application registers a
"listener" with the Push Library's logger so it can show you what's going on.

Rotate the display to landscape mode to see the captions for the action bar buttons.

Press the `Register` button in the sample application action bar to ask the Push SDK to register the device.  If the
device is not already registered, then you should see a lot of output scroll by as the library registers with both
GCM and the Pivotal Mobile Services Suite.  If the device is already registered then the output should be shorter.

Press the `Unregister` button in the sample application action bar to ask the Push SDK to unregister the device.  This
unregister option will unregister with GCM and with the Pivotal Mobile Services Suite.

You can clear all or parts of the saved registration data with the `Clear Registration` action bar option.  Clearing
part or all of the registration data will cause a partial or complete re-registration the next time you press the
`Register` button.  Unlike the `Unregister` button, the `Clear Registration` button simply causes the Push Client SDK
to "forget" that it is registered.  Both GCM and Pivotal Mobile Services Suite will still think that the device is
registered.

You can change the registration preferences at run-time by selecting the `Edit Preferences` action bar item.  Selecting
this item will load the Preferences screen.  There's no space to describe the options on the Preferences screen itself,
but you can look in the `push_default_preferences.xml` resource file for more details.

You can reset the registration preferences to the default values by selecting the `Reset to Defaults` action bar item in
the Preferences screen.

The sample application is also set up to receive push messages once the device has been registered with GCM and
the Pivotal Mobile Services Suite.  Any messages that are received are printed to the log window.

Although the Push Client SDK has no support for sending push messages, the Push Sample App can do it for you as long
as it is set up with the correct `GCM Browser API Key` parameter (when sending messages via GCM or the correct
`Environment UUID` and `Environment Key` parameters (when sending messages via Pivotal Mobile Services Suite).  The
application can not distinguish between messages sent via the two services.
