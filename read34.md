# Monetization
## Publish your app

* publishing : makes your Android applications available to users
* perform two main tasks publish an Android application:
    * prepare the application for release
    * release the application to users

### Preparing app for release:
*  is a multi-step process that involves the following tasks:
    * Configuring your application for release
        * remove Log calls and remove the android:debuggable attribute from your manifest file.
        * provide values for the android:versionCode and android:versionName attributes, which are located in the <manifest> element. 
        * configure several other settings to meet Google Play requirements or accommodate whatever method you're using to release your application.

    * Building and signing a release version of your application
        * use the Gradle build files with the release build type to build and sign a release version of your application.

    * Testing the release version of your application.

    * Updating application resources for release
        * be sure that all application resources such as multimedia files and graphics are updated and included with your application

    * Preparing remote servers and services that your application depends on

    * you will need to get a private key for signing your application
    * You will also need to create an icon for your application
    * you may want to prepare an End User License Agreement (EULA) to protect your person, organization, and intellectual property.

### Releasing app to users
   #### through an application marketplace such as Google Play
    * you can distribute your apps through any app marketplace you want or you can use multiple marketplaces, Google Play is the premier marketplace 
    * Releasing your application on Google Play is a simple process that involves three basic steps:
        * Preparing promotional materials
        * Configuring options and uploading assets
        * Publishing the release version of your application.


   #### on your own website
   * by sending an application directly to a user.
   * prepare your application for release in the normal way
   * need host the release-ready APK file on your website and provide a download link to users.
   *  it is relatively easy to release your application on your own website, it can be inefficient

### User opt-in for unknown apps and sources
  * Android protects users from inadvertent download and install of apps from locations other than a first-party app store, such as Google Play, which is trusted.
  * The opt-in process depends on the version of Android running on the user's device:
    * On devices running Android 8.0 (API level 26) and higher, users must navigate to the Install unknown apps system settings screen to enable app installations from a particular source.
        * users must grant permission to install apps from a source that isn't a first-party app store
        * they must enable the Allow app installs setting for that source

    * On devices running Android 7.1.1 (API level 25) and lower, users must either enable the Unknown sources system setting or allow a single installation of an unknown app.
        * should enable the Unknown sources setting in Settings > Security,


