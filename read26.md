# Android fundamentals

## Application Fundamentals

* we can write a code in several language : java, cotlin and C++
* The code is compiled into an APK or Android package,(an archive file with an `.apk` suffix).
* An Android App Bundle, (an archive file with an `.aab` suffix) contains the contents of an Android app project including additional metadata that is not required at runtime.

* Each Android app protected by the following Android security features:
    * The Android operating system is a multi-user Linux system in which each app is a different user.

    * By default, the system assigns each app a unique Linux user ID (the ID is used only by the system and is unknown to the app). The system sets permissions for all the files in an app so that only the user ID assigned to that app can access them.

    * Each process has its own virtual machine (VM), so an app's code runs in isolation from other apps.

    * every app runs in its own Linux process. The Android system starts the process when any of the app's components need to be executed, and then shuts down the process when it's no longer needed or when the system must recover memory for other apps.

* The Android system implements the privilege, each app has access only to the components that it requires to do its work and no more.

* ways for an app to share data with other apps: 
    * It's possible to arrange for two apps to share the same Linux user ID, in which case they are able to access each other's files.
    * An app can request permission to access device data such as the device's location, camera, and Bluetooth connection. 

## App components

### different types of app components:

#### Activities

* the entry point for interacting with the user
* represents a single screen with a user interface

#### Services

* a general-purpose entry point for keeping an app running in the background for all kinds of reasons.
* runs in the background to perform long-running operations or to perform work for remote processes. 
* does not provide a user interface.

#### Broadcast receivers
* a component that enables the system to deliver events to the app outside of a regular user flow, allowing the app to respond to system-wide broadcast announcements. 
*  the system can deliver broadcasts even to apps that aren't currently running because broadcast receivers are another well-defined entry into the app

#### Content providers
* it manages a shared set of app data that can stored in the file system, apps can query or modify the data if the content provider allows it

## Activating components
* An intent is created with an `Intent` object, which defines a message to activate either a specific component (explicit intent) or a specific type of component (implicit intent).
* methods for activating each type of component:
    * `startActivity()` or `startActivityForResult()`, can activated by passing an `Intent`
    * You can bind to the service by passing an `Intent` to `bindService()`
    * `sendBroadcast()`, `sendOrderedBroadcast()`, or `sendStickyBroadcast()` can  initiate a broadcast by passing an `Intent` to them 
    * You can perform a query to a content provider by calling `query()` on a `ContentResolver`

## The manifest file
* it does a number of things:
    * declaring the app's components
    * Identifies any user permissions the app requires
    * Declares the minimum API Level required by the app
    * Declares hardware and software features used or required by the app
    * Declares API libraries the app needs to be linked against (other than the Android framework APIs)

## App resources
                    
* Android app requires resources other than source code (pictures, audio files,...)
    * SDK build tools define a unique integer ID, which you can use to reference the resource from your app code or from other resources defined in XML
    * One of the most important aspects of providing resources separate from your source code is the ability to provide alternative resources for different device configurations
    * Android supports many different qualifiers for your alternative resources
    * qualifier is a short string that you include in the name of your resource directories in order to define the device configuration for which those resources should be used
