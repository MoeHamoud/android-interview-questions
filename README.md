<p align="center">
<img alt="AndroidInterviewQuestions" src="https://raw.githubusercontent.com/MindorksOpenSource/android-interview-questions/master/assets/banner-android-interview-questions.jpg">
</p>

# Android Interview Questions
[![MindOrks](https://img.shields.io/badge/mindorks-opensource-blue.svg)](https://mindorks.com/open-source-projects)
[![MindOrks Community](https://img.shields.io/badge/join-community-blue.svg)](https://mindorks.com/join-community)
[![MindOrks Android Store](https://img.shields.io/badge/Mindorks%20Android%20Store-Android%20Interview%20Questions-blue.svg?style=flat)](https://mindorks.com/android/store)

> Android Interview Questions - Your Cheat Sheet For Android Interview

## Prepared and maintained by [Amit Shekhar](https://github.com/amitshekhariitbhu) who is having experience of taking interviews of many Android developers and cracking interviews of top companies.

<p align="center">
<a href="https://mindorks.com/android-app-development-online-course" target="_blank">
  <img alt="Android Roadmap" src="https://raw.githubusercontent.com/MindorksOpenSource/android-interview-questions/master/assets/roadmap.png">
</a>	
</p>

## A complete guide for learning Android Development - [Check here](https://mindorks.com/android-app-development-online-course)

## Contents

* [Core Android](#core-android)
* [Android Libraries](#android-libraries)
* [Android Architecture](#android-architecture)
* [Android Design Problem](#android-design-problem)
* [Android Unit Testing](#android-unit-testing)
* [Android Tools And Technologies](#android-tools-and-technologies)
* [Java and Kotlin](#java-and-kotlin)
* [Data Structures And Algorithms](#data-structures-and-algorithms)
* [Other Topics](#other-topics)

### Core Android

#### Base

* **Tell all the Android application components.** - [Learn from here](https://developer.android.com/guide/components/fundamentals.html#Components)

    The Android application components are:

    - __Activities__: This is the entry point for interacting with the user and it also facilitates some key interactions between the system and the app.
    - __Services__: Is a general-purpose entry point for keeping an app running in the background. It is a component that runs in the background to perform long-running operations. It does not provide a UI.
    - __Broadcast Receivers__: Is a component that enables the system to deliver events to the app outside of a regular user flow, thus allowing the app to respond to system-wide broadcast events. This component is mainly a gateway to other components and is intended to do a very minimal amount of work.
    - __Content Providers__: Is a component that manages a shared st of app data that you can store in the file system, in a SQLite database, on the web, or on any other persistent storage location that your app can access. Content providers are useful for reading and writing data that is private to your app and not shared, however, they can allow other apps to (if allowed) query or modify the data.

* **What is `Context`? How is it used?** - [Learn from here](https://blog.mindorks.com/understanding-context-in-android-application-330913e32514)

    Context is:

    - It is the context of the current state of the application.
    - It can be used to get information regarding the activity and application.
    - It can be used to get access to resources, databases, shared preferences and more.
    - Both the Activity and Application classes extend the Context class.

    Two types of context are:

    - Application Context: is an instance of the Application we are running in and is tied to the lifecycle of the application.
    - Activity Context: is an instance of the Activity we are running in and is tied to the lifecycle of the activity.


* **What is `AndroidManifest.xml`?** - [Learn from here](https://developer.android.com/guide/topics/manifest/manifest-intro)

    AndroidManifest.xml (App Manifest) is a file that describes essential information about your app to the Android build tools, the Android operating system, and Google Play. 

    Among many things, the manifest file is required to declare the following:

    - The app's package name.
    - The components of the app (activities, services, broadcast receivers, and content providers).
    - The permissions that the app needs.
    - The hardware and software features the app requires.

* **What is `Application` class?**
    - The Application class in Android is the base class within an Android app that contains all other components such as activities and services. The Application class, or any subclass of the Application class, is instantiated before any other class when the process for your application/package is created.

#### Activity and Fragment

* **What is `Activity` and its lifecycle?** - [Learn from here](https://www.youtube.com/watch?v=RiFui-i-s-o)

    This is the entry point for interacting with the user and it also facilitates some key interactions between the system and the app.

    The lifecycle is:

    - onCreate: called when activity is first created.
    - onStart: called when activity is becoming visible to the user.
    - onResume: called when activity will start interacting with the user.
    - onPause: called when activity is not visible to the user.
    - onStop: called when activity is no longer visible to the user.
    - onRestart: called after your activity is stopped, prior to start.
    - onDestroy: called before the activity is destroyed.

* **What is the difference between onCreate() and onStart()** - [Learn from here](https://www.youtube.com/watch?v=RiFui-i-s-o)

    As long as your device does not kill the activity (for example due to low system resources) then any time you leave your app and go back, `onStart()` is called. If however the application process is killed, then when you return `onCreate()` will be called again, because all of your resources will have been released.


* **When only onDestroy is called for an activity without onPause() and onStop()?** - [Learn from here](https://www.youtube.com/watch?v=QSxcLnZ1-RU)

    `onPause()` and `onStop()` will not be invoked if `finish()` is called from within the `onCreate()` method. This might occur, for example, if you detect an error during `onCreate()` and call `finish()` as a result. In such a case, though, any cleanup you expected to be done in `onPause()` and `onStop()` will not be executed.

* **Why do we need to call setContentView() in onCreate() of Activity class?** - [Learn from here](https://www.youtube.com/watch?v=zeYK8JdMOi8)

    As `onCreate()` of an Activity is called only once, this is the point where most initialization should go such as calling `setContentView()`. It is inefficient to set the content in `onResume()` or `onStart()` (which are called multiple times) as the `setContentView()` is a heavy operation.


* **What is onSavedInstanceState() and onRestoreInstanceState() in activity?**
    - onSavedInstanceState() - This method is used to store data before pausing the activity.
    - onRestoreInstanceState() - This method is used to recover the saved state of an activity when the activity is recreated after destruction. So, the onRestoreInstanceState() receive the bundle that contains the instance state information.

    These are usually used to restore the state of the UI for example when doing a configuration change.

* **What is `Fragment` and its lifecycle.** - [Learn from here](https://blog.mindorks.com/android-fragments-and-its-lifecycle)

    Fragments are like child activities and provide us with modularity and adaptability. They allow us to use them as an entire screen or as different components of a screen or activity, each with their own functions. Fragments take on their Activity's lifecycle.

    The lifecycle is:

    - onAttach: called first when the fragment is attached to an activity (host).
    - onCreate: called when the fragment instance is attached and initializes.
    - onCreateView(): called when it's time for the fragment to draw it's UI. However, a fragment does not need to provide a UI.
    - onActivityCreated(): called when the host Activity completes its onCreate() method.
    - onStart: called when the fragment is becoming visible to the user.
    - onResume: called when the fragment is visible and allows user interaction.
    - onPause: called when the fragment is about to go off screen and will not allow user interaction.
    - onStop: called when the fragment is no longer visible.
    - onDestroyView(): called when the view and related resources created in onCreateView() are removed and destroyed. 
    - onDestroy: called when the fragment does its final clean up.
    - onDetach(): called when the fragment is detached from its host activity.


* **What are "launch modes"?** - [Learn from here](https://blog.mindorks.com/android-activity-launchmode-explained-cbc6cf996802)

    Launch modes allow you to define how a new instance of an activity is associated with the current task. These can be defined using the manifest file or by using intent flags (when calling `startActivity()`)

* **What is the difference between a `Fragment` and an `Activity`? Explain the relationship between the two.** - [Learn from here](https://stackoverflow.com/questions/10478233/why-fragments-and-when-to-use-fragments-instead-of-activities)

    A fragment lives inside an activity, while an activity lives by itself.

* **When should you use a Fragment rather than an Activity?**
    - When you have some UI components to be used across various activities
    - When multiple view can be displayed side by side just like viewPager

* **What is the difference between FragmentPagerAdapter vs FragmentStatePagerAdapter?**
    - FragmentPagerAdapter: Each fragment visited by the user will be stored in the memory but the view will be destroyed. When the page is revisited, then the view will be created not the instance of the fragment.
    - FragmentStatePagerAdapter: Here, the fragment instance will be destroyed when it is not visible to the user, except the saved state of the fragment.

* **What is the difference between adding/replacing fragment in backstack?** - [Learn from here](https://stackoverflow.com/questions/24466302/basic-difference-between-add-and-replace-method-of-fragment/24466345)

    The important difference is:

    - `replace` removes the existing fragment and adds a new fragment.
    - `add` retains the existing fragments and adds a new fragment that means existing fragment will be active and they wont be in 'paused' state hence when a back button is pressed onCreateView() is not called for the existing fragment(the fragment which was there before new fragment was added).

* **Why is it recommended to use only the default constructor to create a `Fragment`?** - [Learn from here](https://www.youtube.com/watch?v=9EdvcycKP9A)

    It is used in the case when device has to restore the state of a fragment. No data will be passed and a default fragment will be created and then the state will be restored. Since the system has no way to know what you passed in your constructor or your newInstance, default constructor will be used and saved bundle should be passed via onCreate after the fragment is actually instantiated with the default constructor.

* **How would you communicate between two Fragments?** - [Learn from here](https://blog.mindorks.com/how-to-communicate-between-fragments)

    - using a shared ViewModel
    - using an Interface; by instantiating the interface in the first fragment then implementing the interface in your Activity and calling the action of the second fragment when an interface method is invoked.

* **What is retained `Fragment`?**
    - By default, Fragments are destroyed and recreated along with their parent Activity’s when a configuration change occurs. Calling setRetainInstance(true) allows us to bypass this destroy-and-recreate cycle, signaling the system to retain the current instance of the fragment when the activity is recreated.

#### Views and ViewGroups

* **What is `View` in Android?** - [Learn from here](https://blog.mindorks.com/android-user-interface-view-components)

    A View is a superclass for all the UI components.

    The view is the component which Android provides us to design the layouts of the app. So, we can understand view as a rectangular area which is going to contain some element inside it.

* **Difference between `View.GONE` and `View.INVISIBLE`?** - [Learn from here](https://stackoverflow.com/questions/11556607/android-difference-between-invisible-and-gone)

    - `View.INVISIBLE`: This view is invisible, but it still takes up space for layout purposes.
    - `View.GONE`: This view is invisible, and it doesn't take any space for layout purposes.

* **Can you a create custom view? How?** - [Learn from here](https://blog.mindorks.com/create-your-own-custom-view)

We use custom views to make the UI component re-usable and to add new interaction which is not provided by the Android ecosystem.

- Custom Views: Where we draw everything
- Custom View Groups: Where we use existing widgets to form an inflatable xml file

* **What are ViewGroups and how they are different from the Views?**
    - View: View objects are the basic building blocks of User Interface(UI) elements in Android. View is a simple rectangle box which responds to the user’s actions. Examples are EditText, Button, CheckBox etc. View refers to the android.view.View class, which is the base class of all UI classes.
    - ViewGroup: ViewGroup is the invisible container. It holds View and ViewGroup. For example, LinearLayout is the ViewGroup that contains Button(View), and other Layouts also. ViewGroup is the base class for Layouts.

* **What is a Canvas?** - [Learn from here](https://blog.mindorks.com/understanding-canvas-api-in-android)

* **What is a `SurfaceView`?** - [Learn from here](https://developer.android.com/reference/android/view/SurfaceView)

* **Relative Layout vs Linear Layout.** - [Learn from here](https://blog.mindorks.com/android-layout-relative-linear-frame)

    - Relative means concerning another, or we can understand this as a relative to one another. In this layout, all the components are arranged concerning with each other. 
    - Linear means in a line, either horizontal or vertical. As in all the elements inside the linear layout get arranged linearly, one after the other. If you are using horizontal orientation, then all the views inside the LinearLayout will be arranged horizontally one after the other.

* **Tell about Constraint Layout** - [Learn from here](https://blog.mindorks.com/using-constraint-layout-in-android-531e68019cd)

    ConstraintLayout combines a simple, expressive and flexible layout system with the powerful features built into the Android Studio Designer tool. It makes it easier to create responsive user interface layouts that adapt automatically to different screen sizes and changing device orientations.

* **Do you know what is the view tree? How can you optimize its depth?** - [Learn from here](https://developer.android.com/reference/android/view/ViewTreeObserver)

    A view tree observer is used to register listeners that can be notified of global changes in the view tree. Such global events include, but are not limited to, layout of the whole tree, beginning of the drawing pass, touch mode change, etc.

* **How does the Touch Control and Events work in Android?** - [Learn from here](https://blog.mindorks.com/touch-control-and-events-in-android) and [here](https://www.youtube.com/watch?v=tKeYr7iV5xE)

#### Displaying Lists of Content

* **What is the difference between `ListView` and `RecyclerView`?** - [Learn from here](https://stackoverflow.com/questions/26728651/recyclerview-vs-listview)

    RecyclerView is better and more efficient as it:

    - Reuses cells while scrolling up/down by forcing implementation of a ViewHolder.
    - Decouples list from its container - so you can put list items easily at run time in the different containers (linearLayout, gridLayout) with setting LayoutManager.

    RecyclerView is a more flexible control for handling "list data" that follows patterns of delegation of concerns and leaves for itself only one task - recycling items.

* **How does RecyclerView work internally?** - [Learn from here](https://blog.mindorks.com/how-does-recyclerview-work-internally) and [here](https://www.youtube.com/watch?v=60IYWdnHsZI)

* **What is the ViewHolder pattern? Why should we use it?** - [Learn from here](https://stackoverflow.com/questions/21501316/what-is-the-benefit-of-viewholder-pattern-in-android)

    ViewHolder design pattern is used to speed up rendering of your RecyclerView as `findViewById` is quite an expensive call (it does DOM parsing) when used each time a list item is rendered because it must traverse your layout hierarchy and possibly instantiate objects. Since lists can redraw its items quite frequently during scrolling such overhead might be substantial.

* **RecyclerView Optimization - Scrolling Performance Improvement** - [Learn from here](https://blog.mindorks.com/recyclerview-optimization)

    Some ways to optimize:
    - Use an image loading library.
    - Set fixed width and heights for dynamically loaded content.
    - Do less in `onBindViewHolder()`
    - Avoid deeply nested item views.
    - Use `setHasFixedSize()` if the height of all items is equal.

* **What is `SnapHelper`?** - [Learn from here](https://blog.mindorks.com/using-snaphelper-in-recyclerview-fc616b6833e8)

#### Dialogs and Toasts

* **What is `Dialog` in Android?** - [Learn from here](https://developer.android.com/guide/topics/ui/dialogs)

    A dialog is a small window that prompts the user to make a decision or enter additional information. A dialog does not fill the screen and is normally used for modal events that require users to take an action before they can proceed.

* **What is `Toast` in Android?** - [Learn from here](https://developer.android.com/guide/topics/ui/notifiers/toasts)

    A toast provides simple feedback about an operation in a small popup. It only fills the amount of space required for the message and the current activity remains visible and interactive. Toasts automatically disappear after a timeout.

* **What the difference between `Dialog` and `Dialog Fragment`?** - [Learn from here](https://stackoverflow.com/questions/7977392/android-dialogfragment-vs-dialog)

    Use Dialog for simple yes or no dialogs.

    Use a DialogFragment when you need more complex views in which you need get hold of the lifecycle such as onCreate, request permissions, any life cycle override. Thus you separate the permissions and any other code the dialog needs to operate without having to communicate with the calling activity.

#### Intents and Broadcasting

* **What is `Intent`?** - [Learn from here](https://blog.mindorks.com/what-are-intents-in-android)

    An Intent is a messaging object you can use to request an action from another app component.

* **What is an Implicit `Intent`?** - [Learn from here](https://blog.mindorks.com/what-are-intents-in-android)

    Implicit Intents don't need to specify the fully-qualified address. All you need to do is just specify the action that is to be performed by an Intent. By using the Implicit Intents you can communicate between various applications present on the mobile device (such as Share sheet).
        
* **What is an Explicit `Intent`?** - [Learn from here](https://blog.mindorks.com/what-are-intents-in-android)

    Explicit Intents are used to communicate with a particular component of the same application.

* **What is a `BroadcastReceiver`?** - [Learn from here](https://developer.android.com/guide/components/broadcasts)

    Android apps can send or receive broadcast messages from the Android system and other Android apps, similar to the publish-subscribe design pattern. These broadcasts are sent when an event of interest occurs.

    Apps can register to receive specific broadcasts. When a broadcast is sent, the system automatically routes broadcasts to apps that have subscribed to receive that particular type of broadcast.

* **What is a `LocalBroadcastManager`?** - [Learn from here](https://blog.mindorks.com/using-localbroadcastmanager-in-android)

    LocalBroadcastManager is used to register and send a broadcast of intents to local objects in your process. The broadcasted data will be contained within your app and cannot be accessed by other apps.

* **What is the function of an `IntentFilter`?** - [Learn from here](https://developer.android.com/reference/android/content/IntentFilter)

    An intent filter is an expression in an app's manifest file that specifies the type of intents that the component would like to receive.

    When you create an implicit intent, the Android system finds the appropriate component to start by comparing the contents of the intent to the intent filters declared in the manifest file of other apps on the device. If the intent matches an intent filter, the system starts that component and delivers it the Intent object.

* **What is a Sticky `Intent`?**
    - Sticky Intents allows communication between a function and a service. `sendStickyBroadcast()` performs a sendBroadcast(Intent) known as sticky, i.e. the Intent you are sending stays around after the broadcast is complete, so that others can quickly retrieve that data through the return value of `registerReceiver(BroadcastReceiver, IntentFilter)`. For example, if you take an intent for `ACTION_BATTERY_CHANGED` to get battery change events: When you call `registerReceiver()` for that action — even with a null BroadcastReceiver — you get the Intent that was last Broadcast for that action. Hence, you can use this to find the state of the battery without necessarily registering for all future state changes in the battery.

* **Describe how broadcasts and intents work to be able to pass messages around your app?** - [Learn from here](https://stackoverflow.com/questions/7276537/using-a-broadcast-intent-broadcast-receiver-to-send-messages-from-a-service-to-a)

    An intent can be broadcasted and a BroadcastReceiver can be used to intercept the broadcasted intent. Think of this as similar to Observer pattern and an Event Bus.

* **What is a `PendingIntent`?**
    - If you want someone to perform any Intent operation at future point of time on behalf of you, then Pending Intent is used.

* **What are the different types of Broadcasts?** - [Learn from here](https://developer.android.com/guide/components/broadcasts)

#### Services

* **What is `Service`?** - [Learn from here](https://developer.android.com/guide/components/services)

    A Service is an application component that can perform long-running operations in the background. It does not provide a user interface. Once started, a service might continue running for some time, even after the user switches to another application. Additionally, a component can bind to a service to interact with it and even perform interprocess communication (IPC). For example, a service can handle network transactions, play music, perform file I/O, or interact with a content provider, all from the background.

    There are three ways of using Service:

    - A foreground service is a Service that will let the user know about what is happening in the background.
    - A background service will not inform the user of what is happening in the background.
    - A Bound Service is used when one or more than one application component binds the Service by using the `bindService()` method. If the applications unbind the Service, then the Service will be destroyed.

* **`Service` vs `IntentService`.** - [Learn from here](https://blog.mindorks.com/service-vs-intentservice-in-android)

    A Service is an application component representing either an application's desire to perform a longer-running operation while not interacting with the user or to supply functionality for other applications to use.

    IntentService is a base class for IntentService Services that handle asynchronous requests (expressed as Intents) on demand. Clients send requests through startService(Intent) calls; the service is started as needed, handles each Intent in turn using a worker thread, and stops itself when it runs out of work.

* **What is a `JobScheduler`?** - [Learn from here](https://developer.android.com/reference/android/app/job/JobScheduler)

    This is an API for scheduling various types of jobs against the framework that will be executed in your application's own process.

    The framework will be intelligent about when it executes jobs, and attempt to batch and defer them as much as possible. Typically if you don't specify a deadline on a job, it can be run at any moment depending on the current state of the JobScheduler's internal queue.

#### Inter-process Communication

* **How can two distinct Android apps interact?** - [Learn from here](https://developer.android.com/training/basics/intents)

    An Intent is used to perform some basic interactions with other apps, such as start another app, receive a result from that app, and make your app able to respond to intents from other apps.

    An Intent can be explicit in order to start a specific component (a specific Activity instance) or implicit in order to start any component that can handle the intended action (such as "capture a photo").

* **Is it possible to run an Android app in multiple processes? How?** - [Learn from here](https://stackoverflow.com/questions/6567768/how-can-an-android-application-have-more-than-one-process)

    You can specify android:process=":remote" in your manifest to have an activity/service run in a seperate process.

    The "remote" is just the name of the remote process, and you can call it whatever you want. If you want several activities/services to run in the same process, just give it the same name.

* **What is AIDL? Enumerate the steps in creating a bounded service through AIDL.** - [Learn from here](https://developer.android.com/guide/components/aidl)

    The Android Interface Definition Language (AIDL) is similar to other IDLs you might have worked with. It allows you to define the programming interface that both the client and service agree upon in order to communicate with each other using interprocess communication (IPC). On Android, one process cannot normally access the memory of another process. So to talk, they need to decompose their objects into primitives that the operating system can understand, and marshall the objects across that boundary for you. The code to do that marshalling is tedious to write, so Android handles it for you with AIDL.

* **What can you use for background processing in Android?** - [Learn from here](https://developer.android.com/guide/background)

    Background tasks fall into one of the following main categories:

    - Immediate
    - Deferred
    - Exact

    Immediate tasks can be done using Kotlin `coroutines`. For tasks that should be executed immediately and need continued processing, even if the user puts the app in the background or the device restarts then a `WorkManager` should be used. For deferred tasks, `WorkManager` should also be used to schedule them.

    A task that needs to be executed at an exact point in time can use `AlarmManager`.

* **What is a `ContentProvider` and what is it typically used for?** - [Learn from here](https://developer.android.com/guide/topics/providers/content-provider-basics) and [here](https://developer.android.com/guide/topics/providers/content-providers)

    A content provider manages access to a central repository of data.

    Typically you work with content providers in one of two scenarios; you may want to implement code to access an existing content provider in another application, or you may want to create a new content provider in your application to share data with other applications.

#### Long-running Operations

* **How to run parallel tasks in Java or Android, and get callback when all complete?** - [Learn from here](https://www.youtube.com/watch?v=v0ZSnISeyKE)

* **Why should you avoid to run non-ui code on the main thread?** - [Learn from here](https://developer.android.com/training/multiple-threads/communicate-ui)

    In order not to lock up the UI and keep performance and framerate of your app high. 
    
    In general, any task that takes more than a few milliseconds should be delegated to a background thread. Common long-running tasks include things like decoding a bitmap, accessing storage, working on a machine learning (ML) model, or performing network requests.

* **What is ANR? How can the ANR be prevented?** - [Learn from here](https://developer.android.com/topic/performance/vitals/anr.html)

    When the UI thread of an Android app is blocked for too long, an "Application Not Responding" (ANR) error is triggered.

    An ANR will be triggered for your app when one of the following conditions occur:

    - While your activity is in the foreground, your app has not responded to an input event or BroadcastReceiver (such as key press or screen touch events) within 5 seconds.
    - While you do not have an activity in the foreground, your BroadcastReceiver hasn't finished executing within a considerable amount of time.

* **What is an `AsyncTask`?** - [Learn from here](https://www.youtube.com/watch?v=ZZ-6nGbfVdA)

    AsyncTask allows you to perform background operations on a worker thread and publish results on the UI thread without needing to directly manipulate threads or handlers.

* **What are the problems in AsyncTask?** - [Learn from here](https://www.youtube.com/watch?v=ZZ-6nGbfVdA)

    - When the Activity is restarted, your AsyncTask’s reference to the Activity is invalid, so onPostExecute() will have no effect on the new Activity.
    - A common usage of AsyncTask is to declare it as an anonymous inner class of the host Activity, which creates an implicit reference to the Activity and an even bigger memory leak.
    - The only way that an AsyncTask finishes early is if it is canceled via `AsyncTask.cancel()`. This means that you have to manage the cancellation of AsyncTasks yourself.
    - It’s up to you to check whether the AsyncTask has been canceled so that you can halt your operation.

* **When would you use java thread instead of an AsyncTask?** - [Learn from here](https://stackoverflow.com/questions/18480206/asynctask-vs-thread-in-android)

    Use AsyncTask for:

    - Simple network operations which do not require downloading a lot of data
    - Disk-bound tasks that might take more than a few milliseconds
    
    Use Java threads for:

    - Network operations which involve moderate to large amounts of data (either uploading or downloading)
    - High-CPU tasks which need to be run in the background
    - Any task where you want to control the CPU usage relative to the GUI thread

* **What is the relationship between the life cycle of an `AsyncTask` and an `Activity`? What problems can this result in? How can these problems be avoided?**
    - An AsyncTask is not tied to the life cycle of the Activity that contains it. So, for example, if you start an AsyncTask inside an Activity and the user rotates the device, the Activity will be destroyed (and a new Activity instance will be created) but the AsyncTask will not die but instead goes on living until it completes.
    
    - Then, when the AsyncTask does complete, rather than updating the UI of the new Activity, it updates the former instance of the Activity (i.e., the one in which it was created but that is not displayed anymore!). This can lead to an Exception (of the type java.lang.IllegalArgumentException: View not attached to window manager if you use, for instance, findViewById to retrieve a view inside the Activity).
    
    - There’s also the potential for this to result in a memory leak since the AsyncTask maintains a reference to the Activity, which prevents the Activity from being garbage collected as long as the AsyncTask remains alive.

    - For these reasons, using AsyncTasks for long-running background tasks is generally a bad idea . Rather, for long-running background tasks, a different mechanism (such as a service) should be employed.
    
    - Note: AsyncTasks by default run on a single thread using a serial executor, meaning it has only 1 thread and each task runs one after the other.

* **Explain `Looper`, `Handler` and `HandlerThread`.** - [Learn from here](https://blog.mindorks.com/android-core-looper-handler-and-handlerthread-bd54d69fe91a) and [from video](https://www.youtube.com/watch?v=rfLMwbOKLRk&list=PL6nth5sRD25hVezlyqlBO9dafKMc5fAU2)

    - MessageQueue: It is a low-level class holding the list of messages to be dispatched by a Looper. Messages are not added directly to a MessageQueue, but rather through Handler objects associated with the Looper.
    - Looper: It loops over a MessageQueue which contains the messages to be dispatched. The actual task of managing the queue is done by the Handler which is responsible for handling (adding, removing, dispatching) messages in the message queue.
    - Handler: It allows you to send and process Message and Runnable objects associated with a thread's MessageQueue. Each Handler instance is associated with a single thread and that thread's message queue.

* **How does the threading work in Android?** - [Learn from here](https://www.youtube.com/watch?v=zfDYK-xB1Uo)

    When an application is launched, the system creates a thread of execution for the application, called "main." This thread is very important because it is in charge of dispatching events to the appropriate user interface widgets, including drawing events.

    Because of the single threaded model described above, it's vital to the responsiveness of your application's UI that you do not block the UI thread. If you have operations to perform that are not instantaneous, you should make sure to do them in separate threads ("background" or "worker" threads).

    However, note that you cannot update the UI from any thread other than the UI thread or the "main" thread.

* **Android Memory Leak and Garbage Collection** - [Learn from here](https://www.youtube.com/watch?v=zCSSFRRIreo)

    A memory leak happens when your code allocates memory for an object, but never deallocates it. This can happen for many reasons.

    No matter the cause, when a memory leak occurs the Garbage Collector thinks an object is still needed because it’s still referenced by other objects. But those references should have cleared.

    If the app continues to leak memory, it’ll eventually run out of it and crash.

#### Working With Multimedia Content

* **How do you handle bitmaps in Android as it takes too much memory?** - [Learn from here](https://developer.android.com/topic/performance/graphics/load-bitmap) and [here](https://developer.android.com/topic/performance/graphics/manage-memory)

* **What is the difference between a regular `Bitmap` and a nine-patch image?**
    - In general, a Nine-patch image allows resizing that can be used as background or other image size requirements for the target device. The Nine-patch refers to the way you can resize the image: 4 corners that are unscaled, 4 edges that are scaled in 1 axis, and the middle one that can be scaled into both axes.

* **Tell about the `Bitmap` pool.** - [Learn from here](https://blog.mindorks.com/how-to-use-bitmap-pool-in-android-56c71a55533c)

    Bitmap pooling is a simple technique (though fairly complex to implement), that aims to reuse bitmaps instead of creating new ones every time. To put it simply, when you need a bitmap, you check a bitmap stack to see if there are any bitmaps available. If there are not bitmaps available you create a new bitmap otherwise you pop a bitmap from the stack and reuse it. Then when you are done with the bitmap, you can put it on a stack.

* **How to play sounds in Android?** - [Learn from here](https://blog.mindorks.com/using-mediaplayer-to-play-an-audio-file-in-android)

    You can use ExoPlayer or MediaPlayer to Play Audio Files in Android applications.

#### Data Saving

* **How to persist data in an Android app?** - [Learn from here](https://blog.mindorks.com/android-shared-preferences-in-kotlin)

    You can use SharedPreferences or a dedicated SQLite database with Room.

* **What is ORM? How does it work?** - [Learn from here](https://www.youtube.com/watch?v=9OHzXUo3Ymk)

    Object-Relational Mapping (ORM) is a technique that lets you query and manipulate data from a database using an object-oriented paradigm. When talking about ORM, most people are referring to a library that implements the Object-Relational Mapping technique, hence the phrase "an ORM".

    An ORM database is something like Room or Realm.

* **How would you preserve `Activity` state during a screen rotation?** - [Learn from here](https://stackoverflow.com/questions/3915952/how-to-save-state-during-orientation-change-in-android-if-the-state-is-made-of-m)

    For simple/small data, you can use `onSaveInstanceState()` and restore the data using the bundle.

    On newer versions of Android and with the compatibility library, retained fragments are usually the best way to handle keeping expensive-to-recreate data alive across activity destruction/creation.

    As well, the ViewModel class allows data to survive configuration changes such as screen rotations.

* **What are different ways to store data in your Android app?** - [Learn from here](https://blog.mindorks.com/understanding-storage-system-to-store-data-in-android)

    - Internal Storage
    - External Storage
    - Shared Preferences
    - Database

* **Explain Scoped Storage in Android.** - [Learn from here](https://blog.mindorks.com/understanding-the-scoped-storage-in-android)

    - Scoped Storage was introduced in Android 10 and the idea behind it is to compartmentalize the storage into specified collections to limit the access to broad storage. 

* **How to encrypt data in Android?** - [Learn from here](https://blog.mindorks.com/how-to-encrypt-data-safely-on-device-and-use-the-androidkeystore)

    Use the JetPack Security Library or Tink Cryptography library as this stuff should not be manually implemented as its very easy to mess up the implementation. EncryptedSharedPreferences can also be used to store encrypt data.

* **What is commit() and apply() in SharedPreferences?**
    - commit() returns a boolean value of success or failure immediately by writing data synchronously.
    - apply() is asynchronous and it won't return any boolean response. If you have an apply() outstanding and you are performing commit(), then the commit() will be blocked until the apply() is not completed.

#### Look and Feel

* **What is a `Spannable`?** - [Learn from here](https://medium.com/androiddevelopers/underspanding-spans-1b91008b97e4)

    Spans are powerful concepts that allow styling text at character or paragraph levels by providing access to components like TextPaint and Canvas.

* **What is a `SpannableString`?**
   - A SpannableString has immutable text, but its span information is mutable. Use a SpannableString when your text doesn't need to be changed but the styling does. Spans are ranges over the text that include styling information like color, highlighting, italics, links, etc

* **What are the best practices for using text in Android?** - [Learn from here](https://blog.mindorks.com/best-practices-for-using-text-in-android)

* **How to implement Dark mode in any application?** - [Learn from here](https://blog.mindorks.com/implementing-dark-mode-theme-in-android)

    Update your AppTheme (styles.xml) to inherit from a theme that supports DayNight.

* **How to generate dynamic colors based in image?** - [Learn from here](https://blog.mindorks.com/color-palette-in-android)

    Use the Color Palette API.

* **Explain about Density Independence Pixel** - [Learn from here](https://blog.mindorks.com/understanding-density-independent-pixel-sp-dp-dip-in-android)

    The number of pixels that fit into an inch is referred to as pixel density.

#### Memory Optimizations

* **What is the `onTrimMemory()` method?** - [Learn from here](https://developer.android.com/topic/performance/memory)

    The provided `onTrimMemory()` callback method allows your app to listen for memory related events when your app is in either the foreground or the background, and then release objects in response to app lifecycle or system events that indicate the system needs to reclaim memory.

* **How does the OutOfMemory happens?** - [Learn from here](https://blog.mindorks.com/practical-guide-to-solve-out-of-memory-error-in-android-application)

    There are various reasons that can lead to OutOfMemoryError in Android. Some of the common reason for Memory Leaks that results in OutOfMemoryError are:

    - Loading large bitmaps 
    - Use of Static view/context/activity
    - Register and unregister listeners
    - Non-Static inner class
    - Wrong use of getContext() and getApplicationContext()

* **How do you find memory leaks in Android applications?** - [Learn from here](https://blog.mindorks.com/practical-guide-to-solve-out-of-memory-error-in-android-application) and [here](https://mindorks.com/blog/detecting-and-fixing-memory-leaks-in-android)

    You can use the memory profiler of Android Studio to find the classes responsible for OutOfMemoryError. Or you can use a library called LeakCanary.

#### Battery Life Optimizations

* **How to reduce battery usage in an android application?** - [Learn from here](https://blog.mindorks.com/battery-optimization-for-android-apps-f4ef6170ff70)

    - Reduce network calls as much as you can by caching data and retrieve it from the cache when required.
    - Avoid wake locks as much as possible.
    - Use AlarmManager carefully.
    - Batch the network calls to prevent the device from waking up frequently.
    - Keep tabs on all background processes.
    - Use GPS carefully.
    - Use WorkManager for long-running async tasks.

* **What is Doze? What about App Standby?** - [Learn from here](https://developer.android.com/training/monitoring-device-state/doze-standby)

    - Doze reduces battery consumption by deferring background CPU and network activity for apps when the device is unused for long periods of time. 
    -  App Standby defers background network activity for apps with which the user has not recently interacted.

* **What is `overdraw`?** - [Learn from here](https://developer.android.com/topic/performance/rendering/overdraw.html)

    An app may draw the same pixel more than once within a single frame, an event called __overdraw__. Overdraw is usually unnecessary, and best eliminated. It manifests itself as a performance problem by wasting GPU time to render pixels that don't contribute to what the user sees on the screen.

    To help you determine if overdraw is affecting your app's performance you can use these tools: Debug GPU overdraw tool and Profile GPU rendering tool.

    There are several strategies you can pursue to reduce or eliminate overdraw:

    - Removing unneeded backgrounds in layouts.
    - Flattening the view hierarchy.
    - Reducing transparency.


#### Supporting Different Screen Sizes

* **How do you support different types of resolutions?** - [Learn from here](https://developer.android.com/training/multiscreen/screensizes)

    - Use view dimensions that allow the layout to resize
    - Create alternative UI layouts according to the screen configuration
    - Provide bitmaps that can stretch with the views
    - Use ConstraintLayout
    - Avoid hard-coded layout sizes
    - Create alternative layouts (landscape, portrait, tablets, etc.)

#### Permissions

* **What are the different protection levels in permission?** - [Learn from here](https://blog.mindorks.com/what-are-the-different-protection-levels-in-android-permission)

    Following are the three protection levels of permissions in Android:

    - Normal Permissions: These are automatically granted to the app as there is very little or no risk of user privacy exposure.
    - Signature Permissions: The android system grants these permissions at the installation time but there is one condition. The app that is asking for some permission must be signed with the same signature as that of the app that defines the required permission.
    - Dangerous Permissions: These are permissions that involve user data in some way. To use these permissions you have to explicitly ask the user for the permission before using it.

#### Native Programming

* **What is the NDK and why is it useful?** - [Learn from here](https://www.youtube.com/watch?v=iljxHVt7Arc) and [here](https://blog.mindorks.com/getting-started-with-android-ndk-android-tutorial) and [here](https://www.youtube.com/watch?v=iljxHVt7Arc)

    The Native Development Kit (NDK) is a set of tools that allow you to leverage C and C++ code in your Android app. You can use it to build from your own source code or to take advantage of existing prebuilt libraries.

    It can be useful in cases in which you need to:

    - Get the extra performance out of a device for computationally intensive applications like games or physics simulations.
    - Reuse your C or C++ libraries.

* **What is renderscript?** - [Learn from here](https://blog.mindorks.com/comparing-android-ndk-and-renderscript-1a718c01f6fe)

#### Android System Internal

* **What is the Dalvik Virtual Machine?** - [Learn from here](https://blog.mindorks.com/what-are-the-differences-between-dalvik-and-art)

    Dalvik is a Just In Time (JIT) compiler. By the term JIT, we mean to say that whenever you run your app in your mobile device then that part of your code that is needed for execution of your app will only be compiled at that moment and rest of the code will be compiled in the future when needed. 

* **What is the difference JVM, DVM and ART?** - [Learn from here](https://android.jlelse.eu/closer-look-at-android-runtime-dvm-vs-art-1dc5240c3924)

* **What are the differences between Dalvik and ART?** - [Learn from here](https://blog.mindorks.com/what-are-the-differences-between-dalvik-and-art)

    ART or Android Runtime is an Android runtime that uses Ahead Of Time(AOT). By using AOT, what is does is it converts or compiles the whole High-level language code into Machine level code and at the time of installation of the app and not dynamically as the application runs(like in case of Dalvik).

* **What is DEX?** - [Learn from here](https://developer.android.com/reference/dalvik/system/DexFile)

    Compiled Android application code file on Dalvik VM.

    Android programs are compiled into .dex (Dalvik Executable) files, which are in turn zipped into a single .apk file on the device. .dex files can be created automatically by Android, by translating the compiled applications written in the Java programming language.

* **Can you manually call the Garbage collector?** - [Learn from here](https://stackoverflow.com/questions/15632734/can-we-call-the-garbage-collector-explicitly)

    You can call Garbage collector using `System.gc()` but this does not mean that it'll be executed immediately. The JVM decides when to execute it.

#### Android Jetpack

* **What is Android Jetpack and why to use this?** - [Learn from here](https://blog.mindorks.com/what-is-android-jetpack-and-why-should-we-use-it)

    Android Jetpack is a collection of Android libraries meant to help and alleviate common problems when building Android apps. This suite of libraries is now considered the "modern" way to build Android apps.

* **What are Android Architecture Components?** - [Learn from here](https://blog.mindorks.com/what-are-android-architecture-components)

    Android architecture components are a collection of libraries that help us in the following:

    - Build robust Android application.
    - Build testable Android application.
    - Build maintainable Android Apps.

    Architecture components also help in managing our UI component lifecycle and handling data persistence.

* **What is LiveData in Android?** - [Learn from here](https://blog.mindorks.com/understanding-livedata-in-android)

    LiveData is an observable data holder class. Unlike a regular observable, LiveData is lifecycle-aware, meaning it respects the lifecycle of other app components, such as activities, fragments, or services. This awareness ensures LiveData only updates app component observers that are in an active lifecycle state.

    - You can use LiveData with libraries like Room Persistent Library, Coroutines, etc.
    - Once a data is modified/changed, the observers will be notified about the change
    - But before notifying the observers, LiveData will check if the observer is live or not. If it is live, then the notification will be sent otherwise not. In this way, the crash due to stopped activities will be stopped.
    - While using LiveData, you need not worry about unsubscribing any observers.
    - If the inactive observer will be resumed in future, then the latest data will be sent to that observer.
    - No need to worry about activity recreation due to screen rotation because only the updated data will be sent.

* **How LiveData is different from ObservableField?** - [Learn from here](https://blog.mindorks.com/livedata-vs-observable-in-android)

    - ObservableField <T> is not Lifecycle aware but LiveData is. That means LiveData will only update app component observers that are in an active lifecycle state and not which are inactive.
    - We have to do manual handling of Lifecycle awareness in ObservableField

* **What is the difference between setValue and postValue in LiveData?** - [Learn from here](https://blog.mindorks.com/livedata-setvalue-vs-postvalue-in-android)

    Both `setValue` and `postValue` can be used in the same manner when working on the main thread.

    If working in a background thread, then you can't use `setValue`. You have to use `postValue` here and the value will be changed immediately however the notification that is to be sent to observers will be scheduled to execute on the main thread via the event loop with the handler.

* **How to share ViewModel between Fragments in Android?** - [Learn from here](https://blog.mindorks.com/shared-viewmodel-in-android-shared-between-fragments)

    In both fragments, when you instantiate the `SharedViewModel` you must provide the same single activity as the owner. This is how to create a shared ViewModel.

* **Explain Work Manager in Android.** - [Learn from here](https://blog.mindorks.com/integrating-work-manager-in-android)

    Work Manager is a library that is part of Android Jetpack which makes it easy to schedule deferrable, asynchronous tasks that are expected to run even if the app exits or device restarts. Work Manager makes sure the scheduled task executes again.

* **Use-cases of WorkManager in Android.** - [Learn from here](https://www.youtube.com/watch?v=4LTpYXFMnJw)

    - run a task
    - run a task periodically
    - cancelling tasks
    - listening to task results

* **How ViewModel work internally?** - [Learn from here](https://blog.mindorks.com/android-viewmodels-under-the-hood)

#### Others

* **Why Bundle class is used for data passing and why cannot we use simple Map data structure?** - [Learn from here](https://developer.android.com/guide/components/activities/parcelables-and-bundles)

* **How do you troubleshoot a crashing application?** - [Learn from here](https://developer.android.com/topic/performance/vitals/crash)

    - stack trace
    - logcat
    - debugging and profiling tools

* **Explain Android notification system?** - [Learn from here](https://blog.mindorks.com/how-to-increase-push-notification-delivery-rate-in-android)

* **What is the difference between Serializable and Parcelable? Which is the best approach in Android?** - [Learn from here](https://android.jlelse.eu/parcelable-vs-serializable-6a2556d51538)

    - Serializable is a standard Java interface. It is not a part of the Android SDK. It’s simplicity is it’s beauty. Just by implementing this interface your POJO will be ready to jump from one Activity to another. Reflection is used during the process and lots of additional objects are created along the way. This can cause lot’s of garbage collection. The result is poor performance and battery drain.
    - Parcelable is another interface. Despite it’s rival (Serializable in case you forgot), it is a part of the Android SDK. Now, Parcelable was specifically designed in such a way that there is no reflection when using it. That is because, we are being really explicit for the serialization process.

* **What is AAPT?** - [Learn from here](https://developer.android.com/studio/command-line/aapt2)

* **What is the best way to update the screen periodically?** - [Learn from here](https://stackoverflow.com/questions/5452394/best-way-to-perform-an-action-periodically-while-an-app-is-running-handler)

    Using a handler to schedule a `Runnable` that does work.

* **FlatBuffers vs JSON.** - [Learn from here](https://blog.mindorks.com/why-consider-flatbuffer-over-json-2e4aa8d4ed07)

* **`HashMap`, `ArrayMap` and `SparseArray`** - [Learn from here](https://blog.mindorks.com/android-app-optimization-using-arraymap-and-sparsearray-f2b4e2e3dc47)

* **What are Annotations?** - [Learn from here](https://blog.mindorks.com/creating-custom-annotations-in-android-a855c5b43ed9), [Link](https://blog.mindorks.com/improve-your-android-coding-through-annotations-26b3273c137a), [and from video](https://www.youtube.com/watch?v=LEb9if2HHSw)

    Annotations are essentially just information about your code.

    For example, `@Override` annotation tells the compiler that this method is an overridden method (metadata about the method) and whether any such method exists in its parent class. Then it throws a compiler error (the method does not override a method from its super class).

* **How to create custom Annotation?** - [Learn from here](https://blog.mindorks.com/creating-custom-annotations-in-android-a855c5b43ed9) and [here](https://www.youtube.com/watch?v=LEb9if2HHSw)

    You create custom Annotations by creating an interface and marking it with `@interface`.

    ```
    @Target(ElementType.METHOD)
    @Retention(RetentionPolicy.RUNTIME)
    @interface Status {
        public enum Priority {LOW, MEDIUM, HIGH}
        Priority priority() default Priority.LOW;
        String author() default “Amit”;
        int completion() default 0;
    }
    ```

    - `@Target` specifies where an annotation can be placed. 
    - `@Retention` defines how long the annotation should be kept around.

* **How to handle multi-touch in android?** - [Learn from here](https://developer.android.com/training/gestures/multi)

    By overriding `onTouchEvent()`.

* **What is the support library? Why was it introduced?** - [Learn from here](https://developer.android.com/topic/libraries/support-library)

    The support library was created to provide newer features on earlier versions of Android or gracefully fall back to equivalent functionality. Rather than building code to handle earlier versions of the platform, you can leverage these libraries to provide that compatibility layer.

    - Backward Compatibility for newer APIs
    - Convenience and Helper Classes
    - Debugging and Utilities

* **What is Android Data Binding?** - [Learn from here](https://developer.android.com/topic/libraries/data-binding/index.html)

    The Data Binding Library is a support library that allows you to bind UI components in your layouts to data sources in your app using a declarative format rather than programmatically.

### Android Libraries

* **Explain OkHttp Interceptor** - [Learn from here](https://blog.mindorks.com/okhttp-interceptor-making-the-most-of-it)

     Interceptors are a powerful mechanism that can monitor, rewrite, and retry API calls. So basically, when we do some API call, we can monitor the call or perform some tasks.

* **OkHttp - HTTP Caching - How caching work in Android** - [Learn from here](https://www.youtube.com/watch?v=D6dQn6pUQD0)

    It automatically parses the cache-related header from the server and stores the response into the cache dir. Next time, when we send the request, it will automatically append the corresponding header for us.

    Ofcourse, you'd want your server to have the proper headers sent to you.

* **Tell me something about RxJava.** - [Learn from here](https://blog.mindorks.com/a-complete-guide-to-learn-rxjava-b55c0cea3631)

    RxJava is used for reactive programming. In reactive programming, the consumer reacts to the data as it comes in. Reactive programming allows for event changes to propagate to registered observers.

* **How will you handle error in RxJava?** - [Learn from here](https://blog.mindorks.com/error-handling-in-rxjava)

* **FlatMap Vs Map Operator** - [Learn from here](https://medium.com/mindorks/rxjava-operator-map-vs-flatmap-427c09678784)

    - Map transforms the items emitted by an Observable by applying a function to each item.
    - FlatMap transforms the items emitted by an Observable into Observables.
    
* **When to use `Create` operator and when to use `fromCallable` operator of RxJava?** - [Learn from here](https://blog.mindorks.com/understanding-rxjava-create-and-fromcallable-operator)
    
* **When to use `defer` operator of RxJava?** - [Learn from here](https://blog.mindorks.com/understanding-rxjava-defer-operator)
    
* **How are Timer, Delay, and Interval operators used in RxJava?** - [Learn from here](https://blog.mindorks.com/understanding-rxjava-timer-delay-and-interval-operators)

* **How to make two network calls in parallel using RxJava?** - [Learn from here](https://blog.mindorks.com/understanding-rxjava-zip-operator-with-example)

    Using the Zip operator you can:
    - Run all the tasks in parallel when Schedulers are correctly provided to each observable.
    - Return the results of all the tasks in a single callback when all the tasks are completed.
    
* **Tell the difference between Concat and Merge.** - [Learn from here](https://blog.mindorks.com/rxjava-operator-concat-vs-merge)

    - Concat emits the emissions from two or more Observables without interleaving them. It will maintain the order of the observables while emitting the items. It means that it will emit all the items of the first observable and then it will emit all the items of the second observable and so on.
    - Merge combines multiple Observables into one by merging their emissions. It will not maintain the order while emitting the items.

* **Explain Subject in RxJava?** - [Learn from here](https://blog.mindorks.com/understanding-rxjava-subject-publish-replay-behavior-and-async-subject-224d663d452f)

    A Subject is a sort of bridge or proxy that is available in some implementations of ReactiveX that acts both as an observer and as an Observable. Because it is an observer, it can subscribe to one or more Observables, and because it is an Observable, it can pass through the items it observes by re-emitting them, and it can also emit new items.

    This is similar to a MediatorLiveData. 

* **What are the types of Observables in RxJava?** - [Learn from here](https://blog.mindorks.com/understanding-types-of-observables-in-rxjava-6c3a2d0819c8)

* **How to implement EventBus with RxJava?** - [Learn from here](https://blog.mindorks.com/implementing-eventbus-with-rxjava-rxbus-e6c940a94bd8)

* **How to implement search feature using RxJava in your application?** - [Learn from here](https://blog.mindorks.com/implement-search-using-rxjava-operators-c8882b64fe1d)

* **How The Android Image Loading Library Glide and Fresco Works?** - [Learn from here](https://blog.mindorks.com/how-the-android-image-loading-library-glide-and-fresco-works-962bc9d1cc40)

    - Checks if the image with that URL key is available in the memory cache or not.
    - If present in the memory cache, it just shows the bitmap by taking it from the memory cache.
    - If not present in the memory cache, it checks in the disk cache.
    - If present in the disk cache, it loads the bitmap from the disk, also puts it in the memory cache and load the bitmap into the view.
    - If not present in the disk cache, it downloads the image from the network, puts it in the disk cache, also puts it in the memory cache and load the bitmap into the view.

* **Difference between Schedulers.io() and Schedulers.computation() in RxJava.**

    - Schedulers.computation() – This schedular can be used to perform CPU-intensive operations like processing huge data, bitmap processing etc., The number of threads created using this scheduler completely depends on number CPU cores available.
    - Schedulers.io() – This is used to perform non-CPU-intensive operations like making network calls, reading disc/files, database operations, etc., This maintains a pool of threads.

* **Why do we use the Dependency Injection Framework like Dagger in Android?** - [Learn from here](https://blog.mindorks.com/why-do-we-use-the-dependency-injection-framework-in-android)

    Consider, that when we have to create a lot of objects which are dependent on many other objects in our project, it becomes tough when the project becomes bigger. With the code base increasing, we might need some good external support to manage it all. That is one of the use-cases for that we use a dependency framework.

* **How does the Dagger work?** - [Learn from here](https://blog.mindorks.com/android-annotation-processing-tutorial-part-1-a-practical-approach) and [here]((https://www.youtube.com/watch?v=Grzqz-B3NWU))

* **What is Component in Dagger?** - [Learn from here](https://www.youtube.com/watch?v=Grzqz-B3NWU)

    Components are essentially the glue that holds everything together. They are a way of telling Dagger 2 what dependencies should be bundled together and made available to a given instance so they can be used. They provide a way for a class to request dependencies being injected through their @Inject annotation.

* **What is Module in Dagger?** - [Learn from here](https://www.youtube.com/watch?v=Grzqz-B3NWU)

    @Module annotated class defines a class that contributes to the dagger object graph.

* **How does the custom scope work in Dagger?**

* **When to call dispose and clear on CompositeDisposable in RxJava?** - [Learn from here](https://stackoverflow.com/questions/47057885/when-to-call-dispose-and-clear-on-compositedisposable)

* **What is Multipart Request in Networking?** - [Learn from here](https://www.youtube.com/watch?v=p7SiNT0q1I8)

    Multipart requests combine one or more sets of data into a single body, separated by boundaries. You typically use these requests for file uploads and for transferring data of several types in a single request (for example, a file along with a JSON object).

* **What is Flow in Kotlin?** - [Learn from here](https://blog.mindorks.com/what-is-flow-in-kotlin-and-how-to-use-it-in-android-project)

    Flow API in Kotlin is a better way to handle a stream of data asynchronously that executes sequentially. The code inside a flow builder does not run until the flow is collected (similar to RxJava observables).

### Android Architecture

* **Describe the architecture of your last app.**

    The architecture of my last app was influenced by Architecture Components and MVVM. 

    The UI layer will contain a fragment as a screen, a ViewModel as the controller for the screen where calls from the fragment are routed through to the ViewModel to operate on. The ViewModel will have a reference to a data source such as a repository which will be used to fetch data from either local storage or network. When the data is retrieved by the repository the ViewModel can either observe or wait directly on the data using coroutines and when the data is received it can push that data to the screen/fragment using LiveData.

    The repository may utilize it's own mapper or helper classes to handle some transformations. 

    The repository will have a data source such as a DB that it can make calls to and an API service using Retrofit to handle any network requests that are required. 

    Why are architectures important? They are important in order to provide clear data flow which will increase robustness, scalability, bug resistant, increase readability, easy to modify and increase productivity and provide a quality app. Using an architecture also creates natural separation of concerns.

* **Describe MVP.** - [Learn from here](https://mindorks.com/course/android-mvp-introduction)

    MVP is an architecture that provides code reusability and testability. MVP usually has direct references to each component. 

    `Model <---> Presenter <---> View`
    
    MVP core components:
    - Model: represents the data and business logic part of the app. It does not interact directly with the view. It provides data to the Presenter, and the presenter forwards that data to the view. The model is usually a repository that interacts with multiple data sources such as a local database or remote API.
    - View: handles the presentation of the data and UI. It's responsibility is to draw the UI with the data provided by the Presenter. A view can be an activity, fragment, dialog, or any user facing component.
    - Presenter: Is the gateway between the model and the view as they do not interact or know about each other. Data is retrieved from the Model by the Presenter and passed on to the View.


* **Describe MVVM.** - [Learn from here](https://blog.mindorks.com/mvvm-architecture-android-tutorial-for-beginners-step-by-step-guide) and [here](https://www.youtube.com/watch?v=HJMZNF-tG-4)

    MVVM architecture is a Model-View-ViewModel architecture that removes the tight coupling between each component. Most importantly, in this architecture, the children don't have the direct reference to the parent, they only have the reference by observables.

    MVVM core components:
    - Model: it represents the data and the business logic. The model is usually a repository that interacts with multiple data sources such as a local database or remote API. The data from these sources is received by the repository and then delivered back to the ViewModel using some form of observing.
    - View: handles the presentation of the data and UI. A view can be an activity, fragment, dialog, or any user facing component. The View sends user actions to the ViewModel but does not get the response back directly. To get the response, it has to subscribe to observables which ViewModel exposes to it.
    - ViewModel: It is a bridge between the View and Model(business logic). It does not have any clue which View has to use it as it does not have a direct reference to the View and is not aware of it. It interacts with the Model, updates it's observables and exposes those observables to be observed by the View.


* **MVC vs MVP vs MVVM architecture.** - [Learn from here](https://blog.mindorks.com/mvc-mvp-mvvm-architecture-in-android)

    ### MVC
    Advantages:
    - It keeps business logic separate in the model
    - Support asynchronous techniques
    - The modification does not affect the entire model
    - Faster development process
    
    Disadvantages:
    - Due to large code in controller it becomes unmanageable
    - Hinders Unit testing
    - Increased Complexity

    ### MVP
    Advantages:
    - It makes view dumb so that you can swap the view easily
    - Reusable View and Presenter
    - Code is more readable and maintainable
    - Easy testing as business logic separated from UI

    Disadvantages:
    - Tight coupling between View and Presenter
    - Huge amount of interfaces for interaction between layers
    - The code size can be quite excessive

    ### MVVM
    Advantages:
    - No tight coupling between the View and ViewModel
    - No interfaces required between View and ViewModel
    - Easy to unit test and code is event-driven

    Disadvantages:
    - You have to create observables for each UI component
    - The code size can be quite excessive


* **What is presenter?** - [Learn from here](https://mindorks.com/course/android-mvp-introduction)

    Presenter: Is the gateway between the model and the view as they do not interact or know about each other. Data is retrieved from the Model by the Presenter and passed on to the View.

* **What is model?** - [Learn from here](https://mindorks.com/course/android-mvp-introduction)

    Model: it represents the data and the business logic. The model is usually a repository that interacts with multiple data sources such as a local database or remote API.

* **Describe MVC.** - [Learn from here](https://blog.mindorks.com/mvc-mvp-mvvm-architecture-in-android)

    - Model: It is business logic and Data State. Getting and manipulating the data, communicates with the controller, interacts with the database, sometimes update the views.
    - View: What we see. User Interface consists of HTML/CSS/XML. It communicates with the controller and sometimes interacts with the model. It is passed some dynamic views through the controller.
    - Controller: It is the Activity/Fragment. It communicates with the view and model. It takes the user input from view/REST services. Process request data from the model and passes to the view.

* **Describe MVI** - [Learn from here](https://github.com/MindorksOpenSource/MVI-Architecture-Android-Beginners)

    MVI stands for Model-View-Intent. 

    MVI works in a very different way compared to its distant relatives, MVC, MVP or MVVM. The role of each MVI components is as follows:

    - Model: represents a state. Models in MVI should be immutable to ensure a unidirectional data flow between them and the other layers in your architecture.
    - View: corresponds to the UI layer. Like in MVP, Interfaces in MVI represent Views, which are then implemented in one or more Activities or Fragments.
    - Intent represents an intention or a desire to perform an action, either by the user or the app itself. For every action, a View receives an Intent. The Presenter observes the Intent, and Models translate it into a new state.

    For this architecture, we use models (data class) to represent the state of a screen or requested data. For example, using this approach, the model would indicate to your app when it should display a progress bar, an error message, or a list of items. 

    For example, the User pushes a button in the View layer where then the User action is routed to the Presenter which will then invoke some action to the repository/data source. The repository/data source would then create a new Model with a different state (for example, error state) and return that back to the Presenter. The Presenter will then pass the Model state onto the View so that it can render it.

* **Describe the repository pattern** - [Learn from here](https://blog.mindorks.com/android-mvp-architecture-extension-with-interactors-and-repositories-bd4b51972339)

    Repositories are classes or components that encapsulate the logic required to access data sources. They centralize common data access functionality, providing better maintainability and decoupling. They are use to abstract the core data source logic and to just deal with retrieving and persisting data from/to the data sources.

* **What is controller?** - [Learn from here](https://blog.mindorks.com/mvc-mvp-mvvm-architecture-in-android)

    In simple terms, the controller translates interactions with the view into actions to be performed by the model.

* **Tell me something about clean code** - [Learn from here](https://blog.mindorks.com/every-programmer-should-read-this-book-6755dedec78d)

    Clean Code usually refers to a set of guiding principles for writing elegant, readable, and maintainable code. 

    Some of these are:
    - Single Responsibility Principle: It states that every module or class should have responsibility over a single part of the functionality provided by the software, and that responsibility should be entirely encapsulated by the class.
    - Open Closed Principle: It states that the software entities (classes, modules, functions, etc) should be open for extension, but closed for modification. That is, such an entity can allow its behaviour to be extended without modifying its source code.
    - Use Descriptive Names
    - DRY (Don't Repeat Yourself): It states that duplicating code will create bloat in the codebase and will require much more work if the code needs to be changed in multiple places where it is exactly the same. 

### Android Design Problem

* **Design Uber App.** - [Learn from here](https://github.com/MindorksOpenSource/ridesharing-uber-lyft-app)

* **Design Facebook App.**

* **Design Facebook Near-By Friends App.**

* **Design WhatsApp.**

* **Design SnapChat.**

* **Design problems based on location based app.**

    - Persuading your Users to opt-in to geolocation. Perhaps when they use a feature of your app that requires it. Say they tap on the search bar to look for a restaurant or location, that is a good spot as contextually it makes sense.
    - Mitigate privacy concerns as Users may feel like Big Brother is watching them. We must be transparent in how the data is used.
    - Protect location data by making security a priority from the start. By assessing potential vulnerabilities in third-party libraries and components. By using authorization best practices and secure communication practices. By securing the local data storage.
    - Try to reduce battery drain due to location tracking.


* **How to build offline-first app? Explain the architecture.**

    An offline-first app will depend on the local storage as a primary soruce of data and changes are made to this storage. 

    The most common approach is to cache data locally. Caching stores data for read access which gives users access to data on their device, renders the UI, and provides a predictable user experience based on a snapshot in time. Caching can provide a smooth offline experience and faster performance but may require a whole component dedicated to handling cached data and determining when to update that cached data.

    Another approach is to modify data locally and then sync it online when the device gets a network connection. 

* **Design LRU Cache.**

    LRU cache manages an object list. Each time a value is accessed, it is moved to the head of the list. When a value is put into the cache, the value at the end of the list may be evicted.

    The LRU cache on Android typically uses a LinkedHashmap. 

    A scenario that a LruCache can be used is to manager the quota of disk cache and memory cache when loading a network image.

* **Design File Downloader** - [Lear from here](https://github.com/MindorksOpenSource/PRDownloader)

* **HTTP Request vs HTTP Long-Polling vs WebSockets** - [Learn from here](https://www.youtube.com/watch?v=k56H0DHqu5Y)

### Android Unit Testing
* **What is Espresso?** - [Learn from here](https://developer.android.com/training/testing/ui-testing/espresso-testing.html)

    The Espresso testing framework, provided by AndroidX Test, provides APIs for writing UI tests to simulate user interactions within a single target app. 

* **What is Robolectric?** - [Learn from here](http://robolectric.org/)

    Robolectric is a framework that brings fast and reliable unit tests to Android. Tests run inside the JVM on your workstation in seconds.

    Robolectric allows a test style that is closer to black box testing, making the tests more effective for refactoring and allowing the tests to focus on the behavior of the application instead of the implementation of Android.

* **What are the disadvantages of using Robolectric?** - [Learn from here](https://stackoverflow.com/questions/18271474/robolectric-vs-android-test-framework) 

    Robolectric excels at aiding Unit testing, but does not cover all the functionality a real device or emulator can offer. For example sensors, gps, open-gl etc etc.

* **What is UI-Automator?** - [Learn from here](https://developer.android.com/training/testing/ui-testing/uiautomator-testing.html)

    The UI Automator APIs let you interact with visible elements on a device, regardless of which Activity is in focus. Your test can look up a UI component by using convenient descriptors such as the text displayed in that component or its content description. 

    The uiautomatorviewer tool provides a convenient visual interface to inspect the layout hierarchy and view the properties of UI components that are visible on the foreground of the device. This information lets you create more fine-grained tests using UI Automator.

* **Explain unit test.** - [Learn from here](https://developer.android.com/training/testing/unit-testing/local-unit-tests)

    To evaluate and test your app's logic you can use local unit tests when you need to run tests more quickly and don't need the fidelity and confidence associated with running tests on a real device.

    In short, Unit testing simply verifies that individual units of code (mostly functions) work as expected.

* **Explain instrumented test.** - [Learn from here](https://developer.android.com/training/testing/unit-testing/instrumented-unit-tests)

    Instrumented unit tests are tests that run on physical devices and emulators, and they can take advantage of the Android framework APIs and supporting APIs. Instrumented tests provide more fidelity than local unit tests, but they run much more slowly.

* **Have you done unit testing or automatic testing?**

* **Why Mockito is used?** - [Learn from here](http://site.mockito.org/)

     Mockito allows you to create and configure mock objects. Using Mockito greatly simplifies the development of tests for classes with external dependencies.

    If you use Mockito in tests you typically:
    - Mock away external dependencies and insert the mocks into the code under test
    - Execute the code under test
    - Validate that the code executed correctly

* **Describe JUnit test.** - [Learn from here](https://en.wikipedia.org/wiki/JUnit)

    JUnit is a unit testing framework for the Java programming language. JUnit promotes the idea of "first testing then coding", which emphasizes on setting up the test data for a piece of code that can be tested first and then implemented

* **Describe code coverage.** - [Learn from here](https://blog.mindorks.com/generate-global-code-coverage-report-in-android-development-using-jacoco-plugin)

    Test coverage is a measure used to describe the degree to which the source code of a program is executed when a particular test suite runs. A program with high test coverage, measured as a percentage, has had more of its source code executed during testing, which suggests it has a lower chance of containing undetected software bugs compared to a program with low test coverage.

### Android Tools And Technologies

* **What is ADB?** - [Learn from here](https://developer.android.com/studio/command-line/adb)

    Android Debug Bridge (adb) is a versatile command-line tool that lets you communicate with a device. The adb command facilitates a variety of device actions, such as installing and debugging apps, and it provides access to a Unix shell that you can use to run a variety of commands on a device. It is a client-server program that includes three components:

    - A client, which sends commands. The client runs on your development machine. You can invoke a client from a command-line terminal by issuing an adb command.
    - A daemon (adbd), which runs commands on a device. The daemon runs as a background process on each device.
    - A server, which manages communication between the client and the daemon. The server runs as a background process on your development machine.

* **What is DDMS and what can you do with it?** - [Learn from here](https://developer.android.com/studio/profile/monitor)

* **What is the StrictMode?** - [Learn from here](https://blog.mindorks.com/use-strictmode-to-find-things-you-did-by-accident-in-android-development-4cf0e7c8d997)

    StrictMode is a developer tool which detects things you might be doing by accident and brings them to your attention so you can fix them.

    StrictMode is most commonly used to catch accidental disk or network access on the application’s main thread, where UI operations are received and animations take place.

* **What is Lint? What is it used for?** - [Learn from here](https://blog.mindorks.com/what-is-lint-what-is-it-used-for)

    Lint is a code scanning tool provided by the Android Studio to identify, suggest and correct wrong, risky, or smelly code present in the project.

* **Git.** - [Learn from here](https://www.youtube.com/watch?v=D4h8Dbrjt4M&list=PL6nth5sRD25itbyNVUULAebzL-VLrLfkK)

    Git is a distributed version-control system for tracking changes in source code during software development. It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows

* **Android Development Useful Tools.** - [Learn from here](https://blog.mindorks.com/android-development-useful-tools-fd73283e82e3)

* **Firebase.** - [Learn from here](https://firebase.google.com/)

    Firebase is Google’s mobile application development platform that helps you build, improve, and grow your app.

    It contains components such as:
    - Authentication — user login and identity
    - Realtime Database — realtime, cloud hosted, NoSQL database
    - Cloud Firestore — realtime, cloud hosted, NoSQL database
    - Cloud Storage — massively scalable file storage
    - Cloud Functions — “serverless”, event driven backend
    - Firebase Hosting — global web hosting

* **How to measure method execution time in Android?** - [Learn from here](https://blog.mindorks.com/measure-method-execution-time-in-android-debug-build)

    You can use a 3rd party library or the traditional way is to use `System.currentTimeMillis()` at the beginning of a method to keep track of the start time and then the same thing at the end of the method to track the end time. Then you can substract the end time from the start time to get your total method run time.

* **Can you access your database of SQLite Database for debugging?** - [Learn from here](https://blog.mindorks.com/how-to-access-sqlite-database-in-android-for-debugging)

    Yes, on a device with Developer Options on and a debuggable app. You can extract the database and open it locally on your computer. 

    In the newest Android Studio update there is a database viewer feature.

* **What are things that we need to take care while using Proguard?** - [Learn from here](https://blog.mindorks.com/things-to-care-while-using-proguard-in-android-application)

* **What is Multidex in Android?** - [Learn from here](https://blog.mindorks.com/understanding-multidex-in-android)

    Dex stands for Dalvik Executable, which is what Google's virtual machine processor (Dalvik) uses to handle Android Applications. Android was built with small and simple apps in mind and the constraints on one single Dalvik Executable pinned the roof of code references at 65,536 methods. Because of this issue and the way the Dalvik machine handles code execution there were some compiling and invocation issues, until the Monkey Patch or MultiDex integration. 

    MultiDex integration in Android Studio allows Android Developers the ability to compile and execute a code-base with over 65,536 methods!

* **How to use Android Studio Memory Profiler?** - [Learn from here](https://www.youtube.com/watch?v=FxDa2td6Ej8)

    The Memory Profiler is a component in the Android Profiler that helps you identify memory leaks and memory churn that can lead to stutter, freezes, and even app crashes. It shows a realtime graph of your app's memory use and lets you capture a heap dump, force garbage collections, and track memory allocations.

* **How to use Firebase realtime database in your app?** - [Learn from here](https://blog.mindorks.com/firebase-realtime-database-android-tutorial)

* **What is Gradle?** - [Learn from here](https://blog.mindorks.com/gradle-for-android-developers-getting-the-most-of-it)

    By definition, Gradle is an open-source build automation tool focused on flexibility and performance.

* **APK Size Reduction.** - [Learn from here](https://blog.mindorks.com/how-to-reduce-apk-size-in-android-2f3713d2d662) and [here](https://blog.mindorks.com/using-r8-to-reduce-apk-size-in-android)

    - Use Android App Bundles
    - Use Android Size Analyzer to understand which files are taking up space
    - Remove unused resources
    - Pay attention to Lint in order to detect unused resources and code
    - Evaluate the use of 3rd party libraries and whether you can get away without needing one
    - Compress image files
    - Use proguard or better yet R8, minification, and shrink resources

* **How can you speed up the Gradle build?** - [Learn from here](https://blog.mindorks.com/speed-up-gradle-build-for-android-to-save-your-time)

* **About gradle build system.** - [Learn from here](https://blog.mindorks.com/gradle-for-android-developers-getting-the-most-of-it)

* **About multiple apk for android application.** - [Learn from here](https://mindorks.com/blog/how-to-create-multiple-apk-files-for-android-application)

* **What is proguard used for?** - [Learn from here](https://blog.mindorks.com/applying-proguard-in-an-android-application)

    Proguard is a tool that helps with:
    - Shrink(Minify) the code: Remove unused code in the project.
    - Obfuscate the code: Rename the names of class, fields, etc.
    - Optimize the code: Do things like inlining the functions.

    In summary, Proguard helps with:
    - It reduces the size of the application.
    - It removes unused classes and methods that contribute to the 64K method counts limit of an Android application.
    - It makes the application difficult to reverse engineer by obfuscating the code.

* **What is obfuscation? What is it used for? What about minification?** - [Learn from here](https://www.youtube.com/watch?v=yduedsaxfDw)

    - Code shrinking (or tree-shaking): detects and safely removes unused classes, fields, methods, and attributes from your app and its library dependencies (making it a valuable tool for working around the 64k reference limit). For example, if you use only a few APIs of a library dependency, shrinking can identify library code that your app is not using and remove only that code from your app. To learn more, go to the section about how to shrink your code.
    - Resource shrinking: removes unused resources from your packaged app, including unused resources in your app’s library dependencies. It works in conjunction with code shrinking such that once unused code has been removed, any resources no longer referenced can be safely removed as well.
    - Obfuscation: shortens the name of classes and members, which results in reduced DEX file sizes.
    - Optimization: inspects and rewrites your code to further reduce the size of your app’s DEX files. For example, if R8 detects that the else {} branch for a given if/else statement is never taken, R8 removes the code for the else {} branch.

* **How to change some parameters in an app without app update?** - [Learn from here](https://blog.mindorks.com/getting-started-with-firebase-remote-config-in-android)

    You can use Firebase RemoteConfig which allows you to deliver some updates in the App like text changes and color changes without publishing any update of the app on the Play Store.

### Java and Kotlin

#### OOP

* **Explain OOP Concepts.**
    - Object-Oriented Programming is a methodology of designing a program using classes, objects, 
    [inheritance](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming)),
    [polymorphism](https://en.wikipedia.org/wiki/Polymorphism_(computer_science)),
    [abstraction](https://en.wikipedia.org/wiki/Abstraction_(software_engineering)), and
    [encapsulation](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming)).

    - __Inheritance__: Inheritance is a mechanism in which one class acquires the property of another class. For example, a child inherits the traits of his/her parents. With inheritance, we can reuse the fields and methods of the existing class.
    - __Polymorphism__: Polymorphism allows us to perform a single action in different ways. In other words, polymorphism allows you to define one interface and have multiple implementations. Real life example of polymorphism: A person at the same time can have different characteristic. Like a man at the same time is a father, a husband, an employee.
    - __Abstraction__: Abstraction is the process of removing physical, spatial, or temporal details or attributes in the study of objects or systems to focus attention on details of greater importance. Through the process of abstraction, a programmer hides all but the relevant data about an object in order to reduce complexity and increase efficiency.
    - __Encapsulation__: Encapsulation refers to the bundling of data, along with the methods that operate on that data, into a single unit. Encapsulation can be used to hide both data members and data functions or methods associated with an instantiated class or object.

* **What is the difference between a constructor and a method?**
    - The name of the constructor is same as that of the class name, whereas the name of the method can be anything. (not necessarily, see Kotlin language)
    - There is no return type of a constructor.
    - When you make an object of a class, then the constructor of that class will be called automatically. But for methods, we need to call it explicitely.
    - Constructors can't be inherited but you can call the constructor of the parent class by calling `super()`.
    - Constructors and methods both run a block of code but the difference is in calling them.
    - We can call a method directly using their name.
    - Constructor Syntax -
        ```java
        public class SomeClassName{
            SomeClassName(parameter_list){ 
                ...
            } 
            ...
        }
        ```
    - Method Syntax 
        ```java
        public class SomeClassName{
            public void someMethodName(parameter_list){
                ...
            }
            // call method
            someMethodName(parameter_list)
        }
        ```
* **Differences between abstract classes and interfaces?** 
    - An abstract class, is a class that contains both concrete and abstract methods (methods without implementations). An abstract method must be implemented by the abstract class sub-classes. Abstract classes cannot be instantiated and need to be extended to be used.
    - An interface is like a blueprint/contract of a class (or it may be thought of as a class with methods, but without their implementation). It contains empty methods that represent what all of its subclasses should have in common. The subclasses provide the implementation for each of these methods. 
    - Interfaces are implemented.

* **What is the difference between iterator and enumeration in java?**
    - In Enumeration we have remove() method and we can only read and traverse through a collection.
    - Iterators can be applied to any collection. In an Iterator, we can read and remove items from a collection.

* **Do you agree with "composition over inheritance"?** [Learn from here](https://www.journaldev.com/12086/composition-vs-inheritance)

    Inheritance brings out IS-A relation. Composition brings out HAS-A relation.
    
    Prefer composition over inheritance as it is more malleable / easy to modify later, but do not use a compose-always approach. With composition, it's easy to change behavior on the fly with Dependency Injection / Setters. Inheritance is more rigid as most languages do not allow you to derive from more than one type.

* **Difference between method overloading and overriding.**
        <p align="center"><img alt="Overloading and Overriding" src="assets/overloading-vs-overriding.png"></p>
    - Overloading happens at compile-time while Overriding happens at runtime: The binding of overloaded method call to its definition happens at compile-time however binding of overridden method call to its definition happens at runtime.
    More info on static vs. dynamic binding: [StackOverflow](https://stackoverflow.com/questions/19017258/static-vs-dynamic-binding-in-java).
    - Static methods can be overloaded which means a class can have more than one static method of same name. Static methods cannot be overridden, even if you declare a same static method in a child class it has nothing to do with the same method of parent class as overridden static methods are chosen by the reference class and not by the class of the object.

        So, for example:
        ```java
        public class Animal {
            public static void testClassMethod() {
                System.out.println("The static method in Animal");
            }

            public void testInstanceMethod() {
                System.out.println("The instance method in Animal");
            }
        }

        public class Cat extends Animal {
            public static void testClassMethod() {
                System.out.println("The static method in Cat");
            }

            public void testInstanceMethod() {
                System.out.println("The instance method in Cat");
            }

            public static void main(String[] args) {
                Cat myCat = new Cat();
                myCat.testClassMethod();
                Animal myAnimal = myCat;
                myAnimal.testClassMethod();
                myAnimal.testInstanceMethod();
            }
        }
        ```
        Will output:
        ```java
        The static method in Cat    // testClassMethod() is called from "Cat" reference

        The static method in Animal // testClassMethod() is called from "Animal" reference,
                                    // ignoring actual object inside it (Cat)

        The instance method in Cat  // testInstanceMethod() is called from "Animal" reference,
                                    // but from "Cat" object underneath
        ```

        The most basic difference is that overloading is being done in the same class while for overriding, base and child classes are required. Overriding is all about giving a specific implementation to the inherited method of parent class.

        Static binding is being used for overloaded methods and dynamic binding is being used for overridden/overriding methods.
        Performance: Overloading gives better performance compared to overriding. The reason is that the binding of overridden methods is being done at runtime.

        Private and final methods can be overloaded but they cannot be overridden. It means a class can have more than one private/final methods of same name but a child class cannot override the private/final methods of their base class.

        Return type of method does not matter in case of method overloading, it can be same or different. However in case of method overriding the overriding method can have more specific return type (meaning if, for example, base method returns an instance of Number class, all overriding methods can return any class that is extended from Number, but not a class that is higher in the hierarchy, like, for example, Object is in this particular case).

        Argument list should be different while doing method overloading. Argument list should be same in method Overriding.
        It is also a good practice to annotate overridden methods with `@Override` to make the compiler be able to notify you if child is, indeed, overriding parent's class method during compile-time.

* **What are the access modifiers you know? What does each one do?** <br>
   - There are four access modifiers in Java language (from strictest to the most lenient):
        1. `private` *variables*, *methods*, *constructors* or *inner classes* are only visible to its' containing class and its' methods. This modifier is most commonly used, for example, to allow variable access only through getters and setters or to hide underlying implementation of classes that should not be used by user and therefore maintain encapsulation. Singleton constructor is also marked `private` to avoid unwanted instantiation from outside.
        2. `Default` (no keyword is used) this modifier can be applied to *classes*, *variables*, *constructors* and *methods* and allows access from classes and methods inside the same package.
        3. `protected` can be used on *variables*, *methods* and *constructors* therefore allowing access only to subclasses and classes that are inside the same package as protected members' class.
        4. `public` modifier is widely-used on *classes*, *variables*, *constructors* and *methods* to grant access from any class and method anywhere. It should not be used everywhere as it implies that data marked with `public` is not sensitive and can not be used to harm the program.

* **Can an Interface implement another Interface?**
  - Yes, an interface can implement another interface (and more than one), but it needs to use `extends`, rather than `implements` keyword. And while you can not remove methods from parent interface, you can add new ones freely to your sub-interface.

* **What is Polymorphism? What about Inheritance?**
  - Polymorphism in Java has two types: Compile time polymorphism (static binding) and Runtime polymorphism (dynamic binding). Method overloading is an example of static polymorphism, while method overriding is an example of dynamic polymorphism.

    An important example of polymorphism is how a parent class refers to a child class object.  In fact, any object that satisfies more than one IS-A relationship is polymorphic in nature.

    For instance, let’s consider a class `Animal` and let `Cat` be a subclass of `Animal`. So, any cat IS animal. Here, Cat satisfies the IS-A relationship for its own type as well as its super class Animal.
  - Inheritance can be defined as the process where one class acquires the properties (methods and fields) of another. With the use of inheritance the information is made manageable in a hierarchical order.

    The class which inherits the properties of other is known as subclass (derived class, child class) and the class whose properties are inherited is known as superclass (base class, parent class).

    Inheritance uses the keyword `extends` to inherit the properties of a class. Following is the syntax of extends keyword.
    ```java
    class Super {
       .....
       .....
    }
    class Sub extends Super {
       .....
       .....
    }
    ```

* **What are the design patterns?** [Learn from here](https://blog.mindorks.com/mastering-design-patterns-in-android-with-kotlin)
    - Creational patterns
        - Builder ([Wikipedia](https://en.wikipedia.org/wiki/Builder_pattern?oldformat=true)): The Builder pattern is a design pattern designed to provide a flexbile solution to various object creation problems in object-oriented programming. The intent of the Builder design pattern is to separate the construction of a complex object from its representation.
        - Factory ([Wikipedia](https://en.wikipedia.org/wiki/Factory_method_pattern?oldformat=true)): The Factory pattern is a creational pattern that uses factory methods to deal with the problem of creating objects without having to specify the exact class of the object that will be created. This is done by creating objects by calling a factory method -- either specified in an interface and implemented by child casses, or implemented in a base class and optionally overriden by derived classes -- rather than by calling a constructor.
        - Singleton ([Wikipedia](https://en.wikipedia.org/wiki/Singleton_pattern)): The Singleton pattern is a software design pattern that restricts the instantiation of a class to one "single" instance. This is useful when exactly one object is needed to coordinate actions across the system.
        - Monostate ([Wikipedia](http://wiki.c2.com/?MonostatePattern)): The Monostate pattern is usually referred to as syntactic sugar over the Singleton pattern or as a conceptual Singleton . It avoids all the complications of having a single instance of a class, but all the instances use the same data. This is accomplished mostly by using static data members.
        - Fluent Interface Pattern ([Wikipedia](https://martinfowler.com/bliki/FluentInterface.html)): A Fluent interface is an object-oriented API whose design relies extensively on method chaining. Its goal is to increase code legibility by creating a domain-specific language (DSL). An example of where this is used is in database queries when using an ORM.
    - Structural patterns
        - Adapter ([Wikipedia](https://en.wikipedia.org/wiki/Adapter_pattern?oldformat=true)): The Adapter pattern is a structural design pattern that allows objects with incompatible interfaces to collaborate. This is a special object that converts the interface of one object so that another object can understand it. (Think of this like an object mapper, for example, from JSON to Data Class object)
        - Decorator ([Wikipedia](https://en.wikipedia.org/wiki/Decorator_pattern?oldformat=true)): Decorator pattern allows a user to add new functionality to an existing object without altering its structure. This type of design pattern comes under structural pattern as this pattern acts as a wrapper to existing class.
        - Facade ([Wikipedia](https://en.wikipedia.org/wiki/Facade_pattern?oldformat=true)): The Facade pattern hides the complexities of the system and provides an interface to a client. This type of design pattern comes under structural pattern as this pattern adds an interface to existing system to hide its complexities. This pattern involves a single class which provides simplified methods required by client and delegates calls to methods of existing system classes.
    - Behavioural patterns
        - Chain of responsibility ([Wikipedia](https://en.wikipedia.org/wiki/Chain-of-responsibility_pattern?oldformat=true)): The chain-of-responsibility pattern is a design pattern consisting of a source of command objects and a series of processing objects. Each processing object contains logic that defines the types of command objects that it can handle; the rest are passed to the next processing object in the chain. A mechanism also exists for adding new processing objects to the end of this chain. Thus, the chain of responsibility is an object oriented version of the `if...else if...else if...else...endif` idiom, with the benefit that the condition–action blocks can be dynamically rearranged and reconfigured at runtime.
        - Iterator ([Wikipedia](https://en.wikipedia.org/wiki/Iterator_pattern?oldformat=true)): The iterator pattern is a design pattern in which an iterator is used to traverse a container and access the container's elements. The iterator pattern decouples algorithms from containers; in some cases, algorithms are necessarily container-specific and thus cannot be decoupled.
        - Strategy ([Wikipedia](https://en.wikipedia.org/wiki/Strategy_pattern?oldformat=true)): The strategy pattern (also known as the policy pattern) is a behavioral software design pattern that enables selecting an algorithm at runtime. Instead of implementing a single algorithm directly, code receives run-time instructions as to which in a family of algorithms to use.

#### Collections and Generics

* **Arrays Vs ArrayLists** - [Learn from here](https://stackoverflow.com/questions/32020000/what-is-the-difference-between-an-array-arraylist-and-a-list/32020072) and [here](https://www.youtube.com/watch?v=SMtSW3Zke_k)

    - An `Array` (System.Array) is fixed in size once it is allocated. You can't add items to it or remove items from it. Also, all the elements must be the same type. As a result, it is type safe, and is also the most efficient of the three, both in terms of memory and performance. 
    - An `ArrayList` is a flexible array which contains a list of objects. You can add and remove items from it and it automatically deals with allocating space. If you store value types in it, they are boxed and unboxed, which can be a bit inefficient. Also, it is not type-safe.
    - A `List<>` leverages generics; it is essentially a type-safe version of ArrayList. This means there is no boxing or unboxing (which improves performance) and if you attempt to add an item of the wrong type it'll generate a compile-time error.

* **HashSet Vs TreeSet** - [Learn from here](https://stackoverflow.com/questions/25602382/java-hashset-vs-treeset-when-should-i-use-over-other)

    - `HashSet` is implemented using a hash table. Elements are not ordered. The add, remove, and contains methods have constant time complexity O(1). HashSet does not maintain ordering.
    - `TreeSet` is implemented using a tree structure(red-black tree in algorithm book). The elements in a set are sorted, but the add, remove, and contains methods has time complexity O(log (n)). It offers several methods to deal with the ordered set like first(), last(), headSet(), tailSet(), etc. TreeSet does maintain ordering.

* **HashMap Vs Set** - [Learn from here](https://stackoverflow.com/questions/2773824/difference-between-hashset-and-hashmap)

    - `HashMap` is a Map (a collection with keyed access) implementation, allowing duplicate values but not duplicate keys. For adding an object a Key/Value pair is required. Null Keys and Null values are allowed. 
    - `HashSet` is a Set (an unordered non-duplicate collection) implementation, which does not allow duplicates. If you tried to add a duplicate object, a call to public boolean add(Object o) method, then the set remains unchanged and returns false.

* **Stack Vs Queue** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/stack-and-queue)

    - `Stack` is a data structure that allows elements to be inserted and deleted only from one side of the list, called the top. The insertion of an element is called push operation and the deletion of an element is called pop operation.
    - `Queue` is a datastructure that allows elements to be inserted only from one side of the list called Rear, and the elements can be deleted only from the other side called the Front. It’s the insertion of an element in a queue is called an Enqueue operation and the deletion of an element is called a Dequeue operation.

* **Explain Generics in Java?**
    - Generics were included in Java language to provide stronger type checks, by allowing the programmer to define which classes can be used with other classes
        > In a nutshell, generics enable types (classes and interfaces) to be parameters when defining classes, interfaces and methods. Much like the more familiar formal parameters used in method declarations, type parameters provide a way for you to re-use the same code with different inputs. The difference is that the inputs to formal parameters are values, while the inputs to type parameters are types. ([Official Java Documentation](https://docs.oracle.com/javase/tutorial/java/generics/why.html))

    - This means that, for example, you can define:
        ```java
        List<Integer> list = new ArrayList<>();
        ```
        And let the compiler take care of noticing, if you put some object, of type other than `Integer` into this list and warn you.
    - It should be noted that standard class hierarchy *does not* apply to generic types. It means that `Integer` in `List<Integer>` is not inherited from `<Number>` - it is actually inherited directly from `<Object>`. You can still put some constraints on what classes can be passed as a parameter into a generic by using [wildcards](https://docs.oracle.com/javase/tutorial/extra/generics/wildcards.html) like `<?>`, `<? extends MyCustomClass>` or `<? super Number>`.
    - While generics are very useful, late inclusion into Java language has put some restraints on their implementation - backward compatibility required them to remain just "syntactic sugar" - they are erased ([type erasure](https://docs.oracle.com/javase/tutorial/java/generics/erasure.html)) during compile-time and replaced with `object` class.

* **What is Java PriorityQueue?**
        - In Priority Queue, each element is having some priority and all the elements are present in a queue. The operations are performed based on the priority.

#### Objects and Primitives

* **How is `String` class implemented? Why was it made immutable?**
  - There is no primitive variant of `String` class in Java language - all strings are just wrappers around underlying array of characters, which is declared `final`. This means that, once a `String` object is instantiated, it cannot be changed through normal tools of the language (Reflection still can mess things up horribly, because in Java no object is truly immutable). This is why `String` variables in classes are the first candidates to be used, when you want to override `hashCode()` and `equals()` of your class - you can be sure, that all their required contracts will be satisfied.
    > Note: The String class is immutable, so that once it is created a String object cannot be changed. The String class  has a number of methods, some of which will be discussed below, that appear to modify strings. Since strings are  immutable, what these methods really do is create and return a new string that contains the result of the operation. ([Official Java Documentation](https://docs.oracle.com/javase/tutorial/java/data/strings.html))

    This class is also unique in a sense, that, when you create an instance like this:
    ```java
    String helloWorld = "Hello, World!";
    ```
    `"Hello, World!"` is called a *literal* and compiler creates a `String` object with its' value. So
    ```java
    String capital = "Hello, World!".toUpperCase();
    ```
    is a valid statement, that, firstly, will create an object with literal value "Hello, World!" and then will create and return another object with value "HELLO, WORLD!"
  - `String` was made immutable to prevent malicious manipulation of data, when, for example, user login or other sensitive data is being send to a server.

* **What does it means to say that a `String` is immutable?**
    - It means that once created, `String` object's `char[]` (its' containing value) is declared `final` and, therefore, it can not be changed during runtime.

* **What is `String.intern()`? When and why should it be used?**
    - `String.intern()` is used to manage memory in Java code. It is used when we have duplicate values in different strings. When you call the `String.intern()`, then if in the String pool that string is present then the `equals()` method will return true and it will return that string only.

* **Can you list 8 primitive types in java?**
    - `byte`
    - `short`
    - `int`
    - `long`
    - `float`
    - `double`
    - `char`
    - `String`
    - `boolean`

* **What is the difference between an Integer and int?**
  - `int` is a primitive data type (with `boolean`, `byte`, `char`, `short`, `long`, `float`, and `double`), while `Integer` (with `Boolean`, `Byte`, `Character`, `Short`, `Long`, `Float`, and `Double`) is a [wrapper](https://docs.oracle.com/javase/tutorial/java/data/numberclasses.html) class that encapsulates primitive data type, while providing useful methods to perform different tasks with it.

* **What is Autoboxing and Unboxing?**
  - Autoboxing and Unboxing is the process of automatic wrapping (putting in a box) and unwrapping (getting the value out) of primitive data types, that have "wrapper" classes. So `int` and `Integer` can (almost always) be used interchangeably in Java language, meaning a method `void giveMeInt(int i) { ... }` can take `int` as well as `Integer` as a parameter.

* **Typecast in Java**
    - In Java, you can use casts to polymorph one class into another compatible one. For example:
        ```java
            long i = 10l;
            int j = (int) i;
            long k = j;
        ```
        Here we see, that, while narrowing (`long i` -> `int j`) requires an explicit cast to make sure the programmer realizes that there may be some data or precision loss whereas widening (`int j` -> `long k`) does not require an explicit cast, because there can be no data loss (`long` can take larger numbers than `int` allows).

* **Do objects get passed by reference or value in Java? Elaborate on that.**
    - In Java all primitives and objects are passed by value, meaning that their copy will be manipulated in the receiving method. But there is a caveat - when you pass an object reference into a method, a *copy of this reference* is made, so it still points to the same object. This means, that any changes that you make to the insides of this object are retained, when the method exits.
        ```java
        public class Pointer {

            int innerField;

            public Pointer(int a) {
                this.innerField = a;
            }
        }
        ```
        ```java
        public class ValueAndReference {

            public static void main(String[] args) {

                Pointer a = new Pointer(0);
                int b = 1;

                print("Before:");
                print("b = " + b);
                print("a.innerField = " + a.innerField);
                exampleMethod(a, b);
                print("After:");
                print("b = " + b);
                print("a.innerField = " + a.innerField);
            }

            static void exampleMethod(Pointer a, int b) {
                a.innerField = 2;
                b = 10;
            }

            static void print(String text) {
                System.out.println(text);
            }
        }
        ```
        Will output:
        ```java
            Before:

            b = 1

            a.innerField = 0

            After:

            b = 1        // a new local int variable was created and operated on, so "b" didn't change

            a.innerField = 2 // Pointer a got its' innerField variable changed
                             //  from 0 to 2, because method was operating on
                             //  the same reference to an instance
        ```

* **What is the difference between instantiation and initialization of an object?** - [Learn from here](https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html)

    - Instantiation: is when you create an instance of a class. That instance is then an object, and you can set its properties, or call methods on it (tell it to do things).
    - Initialization: is when you set up a set of initial conditions for something. That something might be an object, where you tell it to initiate itself, or just a variable to which you assign a value.

* **What the difference between local, instance and class variables?**
  - Local variables exist only in methods that created them, they are stored separately in their respected Thread Stack (for more information, see question about Java Memory Model) and cannot have their reference passed outside of the method scope. That also means that they cannot be assigned any access modifier or made `static` - because they only exist during enclosing method's execution and those modifiers just do not make sense, since no other outside method can get them anyway.
  - Instance variables are the ones, that are declared in classes and their value can be different from one instance of the class to another, but they always require that class' instance to exist.
  - Class variables are those, that are marked with `static` keyword in their class' body. They can only have one value across all instances of that class (changing it in one place will change it in their class and, therefore, in all instances) and can even be retrieved without that class' instance (if their access modifier allows it).

#### Java Memory Model and Garbage Collector

* **What is garbage collector? How does it work?**
  - All objects are allocated on the heap area managed by the JVM.
  As long as an object is being referenced, the JVM considers it alive.
  Once an object is no longer referenced and therefore is not reachable by the application code, the garbage collector removes it and reclaims the unused memory.

* **What is Java Memory Model? What contracts does it guarantee? How are its' Heap and Stack organized?** - [Learn from here](http://tutorials.jenkov.com/java-concurrency/java-memory-model.html)

* **What is memory leak and how does Java handle it?** - [Learn from here](https://developers.redhat.com/blog/2014/08/14/find-fix-memory-leaks-java-application/)

    - A memory leak in Java can occur if you forget to close a resource, or a reference to an object is not released.

* **What are strong, soft, weak and phantom references in Java?** - [Learn from here](https://dzone.com/articles/weak-soft-and-phantom-references-in-java-and-why-they-matter)

    - `SoftReference`: Soft reference objects are cleared at the discretion of the garbage collector in response to memory demand. Soft references are most often used to implement memory-sensitive caches. All soft references to softly reachable objects are guaranteed to have been cleared before the virtual machine throws an OutOfMemoryError.
    - `WeakReference`: Weak reference objects do not prevent their referents from being made finalizable, finalized, and then reclaimed. Weak references are most often used to implement canonicalizing mappings.
    - `PhantomReference`: Phantom reference objects are enqueued after the collector determines that their referents may otherwise be reclaimed. Phantom references are most often used for scheduling pre-mortem cleanup actions in a more flexible way than is possible with the Java finalization mechanism. Unlike soft and weak references, phantom references are not automatically cleared by the garbage collector as they are enqueued. An object that is reachable via phantom references will remain so until all such references are cleared or themselves become unreachable.


#### Concurrency

* **What does the keyword `synchronized` mean?** [Learn from here](https://stackoverflow.com/a/1085745/2621950)

    - `synchronized` methods enable a simple strategy for preventing thread interference and memory consistency errors: if an object is visible to more than one thread, all reads or writes to that object's variables are done through synchronized methods. In a nutshell, the synchronized keyword makes methods thread-safe.

* **What is a `ThreadPoolExecutor`?** [Learn from here](https://blog.mindorks.com/threadpoolexecutor-in-android-8e9d22330ee3)

    - The ThreadPoolExecutor executes a given task using one of its threads from the thread pool.
    - It’s a powerful task execution framework as it supports task addition in a queue, task cancellation, and task prioritization.
    - It reduces the overhead associated with thread creation, as it manages a required number of threads in its thread pool.

* **What is `volatile` modifier?** [Learn from here](http://tutorials.jenkov.com/java-concurrency/volatile.html)

    Volatile keyword is used to modify the value of a variable by different threads. It is also used to make classes thread safe. It means that multiple threads can use a method and instance of the classes at the same time without any problem. The volatile keyword can be used either with primitive type or objects. It does not cache the value of the variable and always reads the variable from the main memory. It cannot be used with classes or methods. However, it is used with variables.

* **The classes in the atomic package expose a common set of methods: `get`, `set,`, `lazyset`, `compareAndSet`, and `weakCompareAndSet`. Please describe them.**

#### Exceptions

* **How does the `try{}`, `catch{}`, `finally` works?** - [Learn from here](https://www.youtube.com/watch?v=Z_5e8MjRWnc&list=PL6nth5sRD25g_M_OgsMQgYIrESzzkGLME&index=13)

    - If an exception is thrown during a sequence of statements inside a try-catch block, the sequence of statements is interrupted and the flow of control will skip directly to the catch-block.
    - You can attach a finally-clause to a try-catch block. The code inside the finally clause will always be executed, even if an exception is thrown from within the try or catch block.

* **What is the difference between a `Checked Exception` and an `Un-Checked Exception`?** - [Learn from here](https://www.w3schools.in/java-questions-answers/difference-between-checked-and-unchecked-exceptions-in-java/)

    - Checked exceptions occur at compile time.
    - Checked exceptions are a sub-class of the exception class.

    - Unchecked exceptions occur at runtime.
    - Unchecked exceptions are runtime exceptions and hence are not a part of the Exception class.

#### Others

* **What is serialization? How do you implement it?**
    - Serialization is the process of converting an object into a stream of bytes in order to store
    an object into memory, so that it can be recreated at a later time, while still keeping the
    object's original state and data. In Android you may use either the Serializable, Externalizable (implements Serializable) or Parcelable interfaces.
    - While Serializable is the easiest to implement, Externalizable may be used if you need to insert custom logic into the process of serialization (although it is almost never used nowadays as it is considered a relic from early versions of Java). But it is highly recommended to use Parcelable in Android instead, as Parcelable was created exclusively for Android and it performs about 10x faster than Serializable, because Serializable uses reflection, which is a slow process and tends to create a lot of temporary objects and it may cause garbage collection to occur more often.
    - To use Serializable all you have to do is implement the interface:

        ```java
        /**
        *  Implementing the Serializable interface is all that is required
        */
        public class User implements Serializable {

            private String name;
            private String email;

                public User() {
                }

                public String getName() {
                    return name;
                }

                public void setName(final String name) {
                    this.name = name;
                }

                public String getEmail() {
                    return email;
                }

                public void setEmail(final String email) {
                    this.email = email;
                }
            }
        ```
    - Parcelable requires a bit more work:
        ```java
            public class User implements Parcelable {

                private String name;
                private String email;

                /**
                 * Interface that must be implemented and provided as a public CREATOR field
                 * that generates instances of your Parcelable class from a Parcel.
                 */
                public static final Creator<User> CREATOR = new Creator<User>() {

                    /**
                     * Creates a new USer object from the Parcel. This is the reason why
                     * the constructor that takes a Parcel is needed.
                     */
                    @Override
                    public User createFromParcel(Parcel in) {
                        return new User(in);
                    }

                    /**
                     * Create a new array of the Parcelable class.
                     * @return an array of the Parcelable class,
                     * with every entry initialized to null.
                     */
                    @Override
                    public User[] newArray(int size) {
                        return new User[size];
                    }
                };

                public User() {
                }

                /**
                 * Parcel overloaded constructor required for
                 * Parcelable implementation used in the CREATOR
                 */
                private User(Parcel in) {
                    name = in.readString();
                    email = in.readString();
                }

                public String getName() {
                    return name;
                }

                public void setName(final String name) {
                    this.name = name;
                }

                public String getEmail() {
                    return email;
                }

                public void setEmail(final String email) {
                    this.email = email;
                }

                @Override
                public int describeContents() {
                    return 0;
                }

                /**
                 * This is where the parcel is performed.
                 */
                @Override
                public void writeToParcel(final Parcel parcel, final int i) {
                    parcel.writeString(name);
                    parcel.writeString(email);
                }
            }
        ```
        Note: For a full explanation of the <b>describeContents()</b> method see [StackOverflow](https://stackoverflow.com/questions/4076946/parcelable-where-when-is-describecontents-used/4914799#4914799).
        In Android Studio, you can have all of the parcelable code auto generated for you, but like with everything else, it is always a good thing to try and understand everything that is happening.

* **What is `transient` modifier?** [Learn from here](https://www.javatpoint.com/transient-keyword)

    - The `transient` keyword is used in serialization. If you define any data member as transient, it will not be serialized.

* **What are anonymous classes?** [Learn from here](https://docs.oracle.com/javase/tutorial/java/javaOO/anonymousclasses.html)

    - Anonymous classes enable you to declare and instantiate a class at the same time. They are like local classes except that they do not have a name. Use them if you need to use a local class only once.

    ```
    HelloWorld frenchGreeting = new HelloWorld() {
        String name = "tout le monde";
        public void greet() {
            greetSomeone("tout le monde");
        }
        public void greetSomeone(String someone) {
            name = someone;
            System.out.println("Salut " + name);
        }
    };
    ```

* **What is the difference between using `==` and `.equals` on an object?** - [Learn from here](https://www.youtube.com/watch?v=aVjnX1MIHB8)

    - `object1 == object2` compares if the objects referenced by object1 and object2 refer to the same memory location in Heap.
    - `object1.equals(object2)` compares the values of object1 and object2 regardless of where they are located in memory.

* **What is the `hashCode()` and `equals()` used for?** - [Learn from here](https://www.geeksforgeeks.org/equals-hashcode-methods-java/)

    - `equals()` method is used to compare equality of two Objects.
    - `hashCode()` returns the hashcode value as an Integer. Hashcode value is mostly used in hashing based collections like HashMap, HashSet, HashTable, etc. This method must be overridden in every class which overrides equals() method.

* **Why would you not call abstract method in constructor?** - [Learn from here](https://stackoverflow.com/questions/15327417/is-it-ok-to-call-abstract-method-from-constructor-in-java)

* **When would you make an object value `final`?**

    - `final` simply makes the object reference unchangeable. The object it points to is not immutable by doing this. INSTANCE can never refer to another object, but the object it refers to may change state.

* **What are these `final`, `finally` and `finalize` keywords?**
  - `final` is a keyword in the java language. It is used to apply restrictions on class, method and variable. Final class can't be inherited, final method can't be overridden and final variable value can't be changed.
    ```java
    class FinalExample {
        public static void main(String[] args) {
            final int x=100;
            x=200;//Compile Time Error because x is final
        }
    }
    ```
  - `finally` is a code block and is used to place important code, it will be executed whether exception is handled or not.
    ```java
    class FinallyExample {
        public static void main(String[] args) {
            try {
                int x=300;
            }catch(Exception e) {
                System.out.println(e.getMessage());            }
            finally {
                System.out.println("finally block is executed");
            }
        }
    }
    ```
  - `Finalize` is a method used to perform clean up processing just before object is garbage collected.
    ```java
    class FinalizeExample {
        public void finalize() {
            System.out.println("finalize called");
        }

        public static void main(String[] args) {
            FinalizeExample f1=new FinalizeExample();
            FinalizeExample f2=new FinalizeExample();
            f1=null;
            f2=null;
            System.gc();
        }
    }
    ```

* **What is the difference between "throw" and "throws" keyword in Java?**

    - `throws` is just used to indicated which exception is to be thrown.
    - `throw` keyword is used to throw some exception from any static block or any method.

* **What does the `static` word mean in Java?**
    - In case of `static` variable it means that this variable (its' value or the object it references) spans across all instances of enclosing class (changing it in one instance affects all others), while in case of `static` methods it means that these methods can be invoked without an instance of their enclosing class. It is useful, for example, when you create util classes that need not be instantiated every time you want to use them.

* **Can a `static` method be overridden in Java?**
    - While child class can override a static method with another static method with the same signature (return type can be down-casted), it is not truly overridden - it becomes "hidden", but both methods can still be accessed under right circumstances (see question about overloading/overriding above).

* **When is a `static` block run?**
    - Code inside static block is executed only once: the first time you make an object of that class or the first time you access a static member of that class (even if you never make an object of that class).

* **What is reflection?**
    - You can inspect classes, interfaces, fields, and method at runtime with the help of reflection and the best part is that you need not know the names of these classes, methods, etc.

* **What is Dependency Injection?** [Learn from here](https://www.youtube.com/watch?v=Grzqz-B3NWU)

    - Dependency Injection is a technique in which an object receives other objects that it depends on. These other objects are called dependencies.

* **How is a `StringBuilder` implemented to avoid the immutable string allocation problem?** - [Learn from here](https://stackoverflow.com/questions/54023816/how-is-a-stringbuilder-implemented-to-avoid-the-immutable-string-allocation-prob)

    - Behind the scene it uses a `char[]` (or `byte[]` in JDK 9 or newer) to store the characters. New String object is created only after calling `StringBuilder.toString()`.

* **Difference between `StringBuffer` and `StringBuilder`?** - [Learn from here](https://www.journaldev.com/538/string-vs-stringbuffer-vs-stringbuilder)

    - StringBuffer is Thread-Safe.
    - StringBuffer is synchronized.
    - StringBuffer is slower.
    - StringBuilder is not Thread-Safe.
    - StringBuilder is not synchronized.
    - StringBuilder is faster.

* **What is the difference between fail-fast and fail-safe iterators in Java?**
    - Fail-fast iterator will not throw any exception even if the collection is modified while iterating over it. But in fail-safe iterator, it throws a `ConcurrentModificationException` when you try to modify the collection while using it.

* **What is Java NIO?** - [Learn from here](https://en.wikipedia.org/wiki/Non-blocking_I/O_(Java))

    - Non-blocking I/O is a collection of Java programming language APIs that offer features for intensive I/O operations.

* **Monitor and Synchronization** - [Learn from here](https://www.youtube.com/watch?v=oLTw1aJpSho)

* **Tell some advantages of Kotlin.** - [Learn from here](https://www.youtube.com/watch?v=kRhivT-jKzY&t=16s)

    Kotlin advantages:
    - concise
    - null-safe
    - interoperable
    - data classes
    - coroutines
    - extension functions

* **What is the difference between `val` and `var`?** - [Learn from here](https://stackoverflow.com/questions/44200075/val-and-var-in-kotlin)

    - `val` is a read-only property and it can only be accessed by a getter. `val` is immutable.
    - `var` is a read-and-write property, so it can be accessed not only by a getter but a setter as well. `var` is mutable.

* **What is the difference between `const` and `val`?** - [Learn from here](https://blog.mindorks.com/what-is-the-difference-between-const-and-val)

    - `consts` are compile time constants. Meaning that their value has to be assigned during compile time, unlike `val`s, where it can be done at runtime.
    - `consts` can never be assigned to a function or any class constructor, but only to a String or primitive.

* **How to ensure `null` safety in Kotlin?** - [Learn from here](https://blog.mindorks.com/safecalls-vs-nullchecks-in-kotlin)

    By using the safe call operator, written as `?.`

    ```
    val b: String? = null
    println(b?.length)
    ```

* **When to use `lateint` keyword used in Kotlin?** - [Learn from here](https://blog.mindorks.com/learn-kotlin-lateinit-vs-lazy)

    `lateinit` means late initialization.

    `lateinit var questionTextView: TextView`

    Using `lateinit`, the initial value does not need to be assigned. Furthermore, at the use sites the questionTextView is not a nullable type, so `?.` and `!!` are not used. However, we have to be careful to assign our lateinit var a value before we use it. Otherwise, a lateinit property acts as if we performed `!!`: it will crash the app on a null value.

* **How to check if a `lateinit` variable has been initialized?** - [Learn from here](https://blog.mindorks.com/how-to-check-if-a-lateinit-variable-has-been-initialized)

    You can use `isInitialized` on the variable.

    `if (myVariable.isInitialized) // do work `

* **How to do lazy initialization of variables in Kotlin?** - [Learn from here](https://blog.mindorks.com/learn-kotlin-lateinit-vs-lazy) and [here](https://www.youtube.com/watch?v=yEX9_PeNRy4)

    `lazy` is lazy initialization.

    `lazy()` is a function that takes a lambda and returns an instance of lazy which can serve as a delegate for implementing a lazy property: the first call to `get()` executes the lambda passed to `lazy()` and remembers the result, subsequent calls to `get()` simply return the remembered result.

* **What are `companion objects` in Kotlin?** - [Learn from here](https://blog.mindorks.com/companion-object-in-kotlin)

    In Kotlin, if you want to write a function or any member of the class that can be called without having the instance of the class then you can write the same as a member of a companion object inside the class.

    ```
    class ToBeCalled {
        companion object Test {
            fun callMe() = println("You are calling me :)")
        }
    }

    fun main(args: Array<String>) {
        ToBeCalled.callMe()
    }
    ```

* **What are the visibility modifiers in Kotlin?** - [Learn from here](https://blog.mindorks.com/learn-kotlin-visibility-modifiers-private-protected-internal-public)

    There are 4 visibility modifiers:
    - `private`: visible inside that particular class or file containing the declaration.
    - `protected`: visible inside that particular file containing the declaration and also in the subclass of that particular class.
    - `internal`: visible everywhere in that particular module. The internal modifier is beneficial only when we have more than one module in a project.
    - `public`: visible to everyone. By default, the visibility modifier in Kotlin is set to public.

* **What is the equivalent of Java static methods in Kotlin?** - [Learn from here](https://blog.mindorks.com/what-is-the-equivalent-of-java-static-methods-in-kotlin)

    - Using a `companion object`.
    - Using `object`.
    - Using a package-level function (think extension functions).

* **What is a data class in Kotlin?** - [Learn from here](https://blog.mindorks.com/learn-kotlin-data-class)

    Fundamentally, Data Class is a simple class that is used to hold data or state, and includes standard functionality. 

    Requirements for data classes:
    - The primary constructor of a Data Class needs to have at least one parameter.
    - Each parameter of the primary constructor must be val or var.
    - Data classes cannot be marked as abstract, sealed, open, or inner.
    - This type of class can inherit another class, and it can implement an interface.

    The compiler automatically derives the following members from all properties declared in the primary constructor:

    - equals()/hashCode() pair;
    - toString() of the form "User(name=John, age=42)";
    - componentN() functions corresponding to the properties in their order of declaration;
    - copy() function (see below).

* **How to create a Singleton class in Kotlin?** - [Learn from here](https://blog.mindorks.com/how-to-create-a-singleton-class-in-kotlin)

    By marking a class with the `object` keyword.

    ```
    object SingletonClass {

    }
    ```

* **What is the difference between `open` and `public` in Kotlin?** - [Learn from here](https://blog.mindorks.com/understanding-open-keyword-in-kotlin)

    - `open` is opposite to `Final` in Java. You use this to mark a class as inheritable. If the class is not 'open', it can't be inherited.
    - `public` is a visibility modifier and everything without access modifiers is by default public in Kotlin.

* **Explain the use-case of `let`, `run`, `also`, `apply`, and `with` in Kotlin.** - [Learn from here](https://blog.mindorks.com/using-scoped-functions-in-kotlin-let-run-with-also-apply) and [here](https://www.youtube.com/watch?v=AiFBEH54Xpw)

    - `let` takes the object it is invoked upon as the parameter and returns the result of the lambda expression. It can be chained or nested and is great for null checks such as `myObj?.let { // do something }`
    ```
    var str = "Hello World"
    str.let { println("$it!!") } 
    ```
    - `run` expression can change the outer property. Similar to the `let` function, the `run` function also returns the last statement. However, unlike `let`, the `run` function doesn’t support the `it` keyword.
    - `also` expressions does some additional processing on the object it was invoked. Unlike `let`, it returns the original object instead of any new return data. Hence the return data has always the same type.
    - `apply` is an extension function on a type. It runs on the object reference (also known as receiver) into the expression and returns the object reference on completion. Such as `person.apply { this.tutorial = "Swift" }`
    - `with` is used to change instance properties without the need to call dot operator over the reference every time.
    ```
    with(person)
    {
        name = "No Name"
        tutorial = "Kotlin tutorials"
    }
    ```

* **Difference between List and Array types in Kotlin** - [Learn from here](https://blog.mindorks.com/difference-between-list-and-array-types-in-kotlin)

    The major difference from usage side is that `Arrays` have a fixed size while (Mutable) `List` can adjust their size dynamically. Moreover Array is mutable whereas List is not.

* **What are `Labels` in Kotlin?** - [Learn from here](https://blog.mindorks.com/learn-kotlin-returns-jumps-labels)

    Any expression in Kotlin may be marked with a `label`. Labels have the form of an identifier followed by the @ sign, for example: abc@, fooBar@ are valid labels.

    For example, below allows you to reference the labeled loop (first loop) and break out of it.
    ```
    loop@ for (i in 1..100) {
        for (j in 1..100) {
            if (...) break@loop
        }
    }
    ```

* **What is an `Init` block in Kotlin?** - [Learn from here](https://blog.mindorks.com/understanding-init-block-in-kotlin)

    Code inside an `init` block is the first to be executed when the class is instantiated and the `init` block is run every time the class is instantiated.

    ```
    MyClass {
        init {
            // some code
        }
    }
    ```

* **Explain `pair` and `triple` in Kotlin.** - [Learn from here](https://blog.mindorks.com/pair-and-triple-in-kotlin)

    - `Pair` is a predefined class in Kotlin that is used to store and return two variables at a time. The two variables can be of different type.
    - `Triple` is a predefined class in Kotlin that is used to store and return 3 variables of same or different type. 

* **How to choose between `apply` and `with`?** - [Learn from here](https://blog.mindorks.com/learn-kotlin-apply-vs-with)

    There are mainly two differences between them:
    - `apply` accepts an instance as the receiver while `with` requires an instance to be passed as an argument. In both cases the instance will become `this` within a block.
    - `apply` returns the receiver and `with` returns a result of the last expression within its block.

    ```
    // apply
    fun getDeveloper(): Developer {
        return Developer().apply {
            developerName = "Amit Shekhar"
            developerAge = 22
        }
    } 

    // with
    fun getPersonFromDeveloper(developer: Developer): Person {
        return with(developer) {
            Person(developerName, developerAge)
        }
    }     
    ```

* **How to choose between `switch` with `when`?** - [Learn from here](https://blog.mindorks.com/replace-switch-with-when-in-kotlin)

    - `switch` doesn't exist in Kotlin.
    - `when` can be used as a `switch` replacement and can be used without an argument. In such case it acts as a nicer `if-else` chain. The key thing to remember with `when` is that the first branch that matches is chosen and it does not cascade.

* **What are Coroutines in Kotlin?** - [Learn from here](https://blog.mindorks.com/mastering-kotlin-coroutines-in-android-step-by-step-guide)

    Coroutines allow you to write asynchronous code in a sequential fashion.

* **What is Coroutine Scope?** - [Learn from here](https://blog.mindorks.com/mastering-kotlin-coroutines-in-android-step-by-step-guide)

    CoroutineScope is the interface that define the concept of Scope with Coroutines, to execute a coroutine using `launch` or `async` you need a scope.

    - a coroutine must run in a scope
    - it is a way to keep track of all coroutines that run in it
    - all (cooperative) coroutines can be cancelled via their scope
    - scopes get uncaught exceptions
    - they are a way to bind coroutines to an application specific lifecycle (e.g. viewModelScope in Android) to avoid leaking

* **What is Coroutine Context?** - [Learn from here](https://blog.mindorks.com/mastering-kotlin-coroutines-in-android-step-by-step-guide)

    The context determines on which thread the coroutines will run. There are four options:
    - Dispatchers.Default - for CPU intense work (e.g. sorting a big list)
    - Dispatchers.Main - what this will be depends on what you've added to your programs runtime dependencies (e.g. kotlinx-coroutines-android, for the UI thread in Android)
    - Dispatchers.Unconfined - runs coroutines unconfined on no specific thread
    - Dispatchers.IO - for heavy IO work (e.g. long-running database queries)

* **Launch vs Async in Kotlin Coroutines** - [Learn from here](https://www.youtube.com/watch?v=nC30UiDv8Xc)

    - `launch` starts a background thread, does something, and returns a token immediately as `Job` (think fire and forget). You can call `join` on this `Job` to block until this `launch` thread completes.
    - `async` starts a background thread, does something, and returns a token immediately as `Deferred` (think fire and wait for result). You can use `.await()` on a deferred value to get its eventual result, but `Deferred` is also a `Job`, so you can cancel it if needed.

* **What is inline function in Kotlin?** - [Learn from here](https://blog.mindorks.com/understanding-inline-noinline-and-crossinline-in-kotlin)

    Inline function instructs the compiler to insert the complete body of the function wherever that function got called in the code.

* **When to use Kotlin sealed classes?** - [Learn from here](https://blog.mindorks.com/learn-kotlin-sealed-classes)

    Sealed classes are used for representing restricted class hierarchies, when a value can have one of the types from a limited set, but cannot have any other type. They are, in a sense, an extension of enum classes.

    - Sealed classes are abstract and can have abstract members.
    - Sealed classes cannot be instantiated directly.
    - Sealed classes cannot have public constructors (the constructors are private by default).
    - Sealed classes can have subclasses, but they must either be in the same file or nested inside of the sealed class declaration.
    - Sealed classes subclass can have subclasses outside of the sealed class file.

    An example use case for sealed classes is representing a UI state.

    ```
    sealed class UiState()
    class Loading() : UiState()
    class Display() : UiState()
    ```
    
    Usage:
    ```
    when (uiState) {
        is UiState.Loading -> showLoadingProgressView()
        is UiState.Display -> showContent()
    }
    ```

* **Explain function literals with receiver in Kotlin?** - [Learn from here](https://blog.mindorks.com/function-literals-with-receiver-in-kotlin)

    Closely related to the extension function is the function literal with receiver. There are two types of function literals:
    - lambda
    - anonymous function

    Where with extension functions you can add a new member function to an existing class, with a function literal with receiver you can access the member functions of an existing class inside the lambda block (inside the curly braces {}).

    For example:
    ```
    val lambdaAppendMonkey: StringBuilder.() -> StringBuilder = { this.append("monkey") }
    ```

* **Tell about Kotlin DSL.** - [Learn from here](https://blog.mindorks.com/mastering-kotlin-dsl-in-android-step-by-step-guide)

* **What are higher-order functions in Kotlin?** - [Learn from here](https://blog.mindorks.com/understanding-higher-order-functions-and-lambdas-in-kotlin)

* **What are Lambdas in Kotlin** - [Learn from here](https://blog.mindorks.com/understanding-higher-order-functions-and-lambdas-in-kotlin)

* **Tell about the Collections in Kotlin** - [Learn from here](https://www.youtube.com/watch?v=XeRt2ZZ-jkA)

### Data Structures And Algorithms

> The level of questions asked on the topic of Data Structures And Algorithms totally depends on the company for which you are applying.

#### Whiteboard Interview Series - Data Structures and Algorithms on Youtube - [Check here](https://www.youtube.com/playlist?list=PLqOiaH9id5qt_lZl2bFi8q9RQoV1JJUpf)

#### Tech Interview Preparation Kit - [Check here](https://afteracademy.com/tech-interview)

#### Android Developer should know these Data Structures for Next Interview - [Check here](https://blog.mindorks.com/android-developer-should-know-these-data-structures-for-next-interview)

* **Complexity Analysis** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/complexity-analysis)
    - What is Input, Output, Correctness, Efficiency of Algorithms?
    - What is Input Size and Running Time of Algorithms?
    - Explain the Worst, Best, and Average case analysis of Algorithms.
    - What is Big-O Notation with respect to Time and Space Complexity?

*  **Iteration and Two Pointer Approach** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/iteration-and-two-pointer-approach)
    - Explain Initialization, Maintenance, and Termination used in iteration.
    - Explain the use-case of Two Pointer approach

* **Recursion and Divide & Conquer Approach** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/recursion-and-divide-and-conquer-approach)
    - Explain Recursion with the help of an example and also draw the recursion call stack for the same.
    - How will you analyse the recursive solution of some problem?
    - Is there any difference between Recursion and Iteration?
    - Explain the Divide and Conquer technique with the help of a real-world example.

* **Arrays and Linked List** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/array-and-linked-list)
    - What do you mean by Linear Data Structures?
    - Explain the basic operations that can be performed on Arrays? Also, tell about Amortized analysis of array.
    - What is a Linked List? Explain with an example by performing some operations on Linked List.
    - What are the types of Linked List?
    - Can you tell the difference between an Array and a Linked List?

* **Stack and Queue** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/stack-and-queue)
    - What is a Stack? Explain various operations that can be performed on a Stack.
    - Can you implement Stack using an Array or using a Linked List? How?
    - What is a Queue? Explain various operations that can be performed on a Queue.
    - Can you implement Queue using an Array or using a Linked List? How?
    - Is there any difference between a Stack and a Queue?

* **Sorting Algorithms** - [Wikipedia](https://en.wikipedia.org/wiki/Sorting_algorithm?oldformat=true)
    - Using the most efficient sorting algorithm (and correct data structures that implement it) is vital for any program, because data manipulation can be one of the most significant bottlenecks in case of performance and the main purpose of spending time, determining the best algorithm for the job, is to drastically improve said performance. The efficiency of an algorithm is measured in its' "Big O" ([StackOverflow](https://stackoverflow.com/questions/487258/what-is-a-plain-english-explanation-of-big-o-notation)) score. Really good algorithms perform important actions in O(n log n) or even O(log n) time and some of them can even perform certain actions in O(1) time (HashTable insertion, for example). But there is always a trade-off - if some algorithm is really good at adding a new element to a data structure, it is, most certainly, much worse at data access than some other algorithm. If you are proficient with math, you may notice that "Big O" notation has many similarities with "limits", and you would be right - it measures best, worst and average performances of an algorithm in question, by looking at its' function limit. It should be noted that, when we are speaking about O(1) - constant time - we are not saying that this algorithm performs an action in one operation, rather that it can perform this action with the same number of operations (roughly), regrardless of the amount of elements it has to take into account. Thankfully, a lot of "Big O" scores have been already calculated, so you don't have to guess, which algorithm or data structure will perform better in your project. ["Big O" cheat sheet](http://bigocheatsheet.com/)
    - Bubble sort [Wikipedia](https://en.wikipedia.org/wiki/Bubble_sort?oldformat=true) 
        - Bubble sort is one of the simplest sorting algorithms. It just compares neighbouring elements and if the one that precedes the other is smaller - it changes their places. So over one iteration over the data list, it is guaranteed that **at least** one element will be in its' correct place (the biggest/smallest one - depending on the direction of sorting). This is not a very efficient algorithm, as highly unordered arrays will require a lot of reordering (upto O(n^2)), but one of the advantages of this algorithm is its' space complexity - only two elements are compared at once and there is no need to allocate more memory, than those two will occupy. 
            <table>
                <tr>
                    <th colspan="3" align="center">Time Complexity</th>
                    <th align="center">Space Complexity</th>
                </tr>
                <tr>
                    <th align="center">Best</th>
                    <th align="center">Average</th>
                    <th align="center">Worst</th>
                    <th align="center">Worst</th>
                </tr>
                <tr>
                    <td align="center">Ω(n)</td>
                    <td align="center">Θ(n^2)</td>
                    <td align="center">O(n^2)</td>
                    <td align="center">O(1)</td>
                </tr>
            </table>
    - Selection sort [Wikipedia](https://www.wikiwand.com/en/Selection_sort) 
        - Firstly, selection sort assumes that the first element of the array to be sorted is the smallest, but to confirm this, it iterates over all other elements to check, and if it finds one, it gets defined as the smallest one. When the data ends, the element, that is currently found to be the smallest, is put in the beginning of the array. This sorting algorithm is quite straightforward, but still not that efficient on larger data sets, because to assign just one element to its' place, it needs to go over all data.
            <table>
                <tr>
                    <th colspan="3" align="center">Time Complexity</th>
                    <th align="center">Space Complexity</th>
                </tr>
                <tr>
                    <th align="center">Best</th>
                    <th align="center">Average</th>
                    <th align="center">Worst</th>
                    <th align="center">Worst</th>
                </tr>
                <tr>
                    <td align="center">Ω(n^2)</td>
                    <td align="center">Θ(n^2)</td>
                    <td align="center">O(n^2)</td>
                    <td align="center">O(1)</td>
                </tr>
            </table>
    - Insertion sort [Wikipedia](https://en.wikipedia.org/wiki/Insertion_sort?oldformat=true)
        - Insertion sort is another example of an algorithm, that is not that difficult to implement, but is also not that efficient. To do its' job, it "grows" sorted portion of data, by "inserting" new encountered elements into already (innerly) sorted part of the array, which consists of previously encountered elements. This means that in best case (data is already sorted) it can confirm that its' job is done in Ω(n) operations, while, if all encountered elements are not in their required order as many as O(n^2) operations may be needed.
            <table>
            <tr>
                <th colspan="3" align="center">Time Complexity</th>
                <th align="center">Space Complexity</th>
            </tr>
            <tr>
                <th align="center">Best</th>
                <th align="center">Average</th>
                <th align="center">Worst</th>
                <th align="center">Worst</th>
            </tr>
            <tr>
                <td align="center">Ω(n)</td>
                <td align="center">Θ(n^2)</td>
                <td align="center">O(n^2)</td>
                <td align="center">O(1)</td>
            </tr>
            </table>
    - Merge sort [Wikipedia](https://en.wikipedia.org/wiki/Merge_sort?oldformat=true)
        - This is a "divide and conquer" algorithm, meaning it recursively "divides" given array in to smaller parts (up to 1 element) and then sorts those parts, combining them with each other. This approach allows merge sort to achieve very high speed, while  doubling required space, of course, but today memory space is more available than it was a couple of years ago, so this trade-off is considered acceptable.   
            <table>
            <tr>
                <th colspan="3" align="center">Time Complexity</th>
                <th align="center">Space Complexity</th>
            </tr>
            <tr>
                <th align="center">Best</th>
                <th align="center">Average</th>
                <th align="center">Worst</th>
                <th align="center">Worst</th>
            </tr>
            <tr>
                <td align="center">Ω(n log(n))</td>
                <td align="center">Θ(n log(n))</td>
                <td align="center">O(n log(n))</td>
                <td align="center">O(n)</td>
            </tr>
            </table>
    - Quicksort [Wikipedia](https://en.wikipedia.org/wiki/Quicksort?oldformat=true)
        - Quicksort is considered, well, quite quick. When implemented correctly, it can be a significant number of times faster than its' main competitors. This algorithm is also of "divide and conquer" family and its' first step is to choose a "pivot" element (choosing it randomly, statistically, minimizes the chance to get the worst performance), then by comparing elements to this pivot, moving it closer and closer to its' final place. During this process, the elements that are bigger are moved to the right side of it and smaller elements to the left. After this is done, quicksort repeats this process for subarrays on each side of placed pivot (does first step recursively), until the array is sorted.
                <table>
                <tr>
                    <th colspan="3" align="center">Time Complexity</th>
                    <th align="center">Space Complexity</th>
                </tr>
                <tr>
                    <th align="center">Best</th>
                    <th align="center">Average</th>
                    <th align="center">Worst</th>
                    <th align="center">Worst</th>
                </tr>
                <tr>
                    <td align="center">Ω(n log(n))</td>
                    <td align="center">Θ(n log(n))</td>
                    <td align="center">O(n^2)</td>
                    <td align="center">O(n)</td>
                </tr>
                </table>  
    - There are, of course, more sorting algorithms and their modifications. We strongly recommend all readers to familiarize themselves with a couple more, because knowing algorithms is very important quality of a candidate, applying for a job and it shows understanding of what is happening "under the hood".

* **Binary Tree** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/binary-tree)
    - What are non-linear data structures? Give example.
    - What is a Tree Data Structure? Explain the properties of tree with an example.
    - How is Binary Tree different from a normal Tree?
    - What is inorder, pre-order, post-order, and level-order traversal of a tree? Explain with an example.
    - Can you find the inorder, pre-order, and post-order of a tree using Stack? How?
    - Explain how searching, insertion, and deletion operations are performed on a Tree?

* **Binary Search Tree** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/binary-search-tree)
    - What is a Binary Search Tree? Explain its properties also.
    - Explain how searching, insertion, and deletion operations are performed on a Binary Search Tree?
    - How is Binary Search Tree different from Binary Tree?

* **Heap and Priority Queue** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/heap-and-priority-queue)
    - What is a Heap data structure and when it is used?
    - Explain the operations that can be performed on a Heap.
    - What is the difference between a min-heap and a max-heap? How to implement these two?
    - What do you mean by Priority Queue? How to implement Priority Queue?
    - What are the real-life applications of Priority Queue?

* **Hash Table** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/hash-table)
    - What do you mean by Direct Address Table?
    - Can you perform search, insert, and delete in O(1)? How?
    - Explain Hash Table and its properties.
    - How to remove collision in Hash Table by Chaining and Open Addressing?
    - What are the real-life applications of Hash Table?

* **Dynamic Programming** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/dynamic-programming)
    - What is Dynamic Programming and how to find if a problem can be solved using DP or not?
    - What are two approaches of solving a Dynamic Programming problem?
    - Explain Optimization and Combinatorial problems?

* **Greedy Algorithms** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/greedy-algorithms)
    - What do you mean by Greedy algorithms? How to find if a problem can be solved by Greedy approach or not?
    - Is there any difference between Dynamic Programming and Greedy Algorithms?

* **Backtracking** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/backtracking)
    - What is Backtracking?
    - How to find if a problem can be solved with Backtracking or not?
    - What is Exhaustive Searching?

* **Graph** - [Learn from here](https://afteracademy.com/tech-interview/ds-algo-concepts/graph)
    - What is Graph and how to represent a Graph?
    - Explain Depth First Search and Breadth First Search.
    - How to represent a Graph? 
    - What are the real-life applications of Graph?
    - What do you mean by Topological Sorting?
    - Explain Dijkstra algorithm with an example.
    - What is a Minimum Spanning Tree?

### Other Topics

* **Describe how REST APIs work. What is REST?** - [Learn from here](https://www.youtube.com/watch?v=1wSEI6_SzMU) and [here](https://www.youtube.com/watch?v=HgXAoBomGcA)

* **Describe SQLite.** - [Learn from here](https://blog.mindorks.com/android-sqlite-database-in-kotlin) and [here](https://www.youtube.com/watch?v=9OHzXUo3Ymk)

* **Describe database.** - [Learn from here](https://afteracademy.com/blog/what-is-a-database-and-dbms)

* **How do you control the application version update to specific number of users?**

* **Can we identify users who have uninstalled our application?**

* **Android Development Best Practices.** - [Learn from here](https://blog.mindorks.com/android-development-best-practices-83c94b027fd3)

* **Android Code Style And Guidelines.** - [Learn from here](https://blog.mindorks.com/android-code-style-and-guidelines-d5f80453d5c7)

* **Have you tried Kotlin?** - [Learn from here](https://blog.mindorks.com/why-you-must-try-kotlin-for-android-development-e14d00c8084b)

* **What are the metrics that you should measure continuously while android application development?** - [Learn from here](https://blog.mindorks.com/android-app-performance-metrics-a1176334186e)

* **What is Chrome Custom Tabs? How to display web content in your app?** - [Learn from here](https://blog.mindorks.com/android-browser-lets-launch-chrome-custom-tabs-with-kotlin)

* **How to avoid API keys from check-in into VCS?** - [Learn from here](https://blog.mindorks.com/using-local-properties-file-to-avoid-api-keys-check-in-into-version-control-system)

* **How does the Kotlin Multiplatform work?** - [Learn from here](https://blog.mindorks.com/how-does-the-kotlin-multiplatform-work)

* **How to use Memory Heap Dumps data?** - [Learn from here](https://blog.mindorks.com/how-to-use-memory-heap-dumps-data)

* **How to implement Dark Theme in your app?** - [Learn from here](https://blog.mindorks.com/build-material-and-dark-themes-apps-using-style-in-android)

* **Have you tried Jetpack compose?** - [Learn from here](https://blog.mindorks.com/using-jetpack-compose-to-build-ui-in-android)

* **How to secure the API keys used in an app?** - [Learn from here](https://blog.mindorks.com/securing-api-keys-using-android-ndk)

* **How to convert check Java equivalent code of Kotlin?** - [Learn from here](https://blog.mindorks.com/how-to-convert-a-kotlin-source-file-to-a-java-source-file)

* **Tell something about memory usage in Android.** - [Learn from here](https://blog.mindorks.com/understanding-memory-usage-in-android)

* **What is Benchmarking?** - [Learn from here](https://blog.mindorks.com/improving-android-app-performance-with-benchmarking)

* **Can you create transparent activity in Android?** - [Learn from here](https://blog.mindorks.com/how-to-create-a-transparent-activity-in-android)

* **How to use Android Sensors?** - [Learn from here](https://blog.mindorks.com/using-android-sensors-android-tutorial)

* **Explain Annotation processing.**  - [Learn from here](https://blog.mindorks.com/android-annotation-processing-tutorial-part-1-a-practical-approach)

* **How to increase the Notification delivery rate?** [Learn from here](https://blog.mindorks.com/how-to-increase-push-notification-delivery-rate-in-android)

* **How does the notification system work?** [Learn from here](https://blog.mindorks.com/how-to-increase-push-notification-delivery-rate-in-android)

* **How to show local Notification at an exact time?** [Learn from here](https://blog.mindorks.com/how-to-increase-push-notification-delivery-rate-in-android)

### Found this project useful :heart:

* Support by clicking the :star: button on the upper right of this page. :v:

[Check out MindOrks awesome open source projects here](https://mindorks.com/open-source-projects)

### License
```
   Copyright (C) 2020 MINDORKS NEXTGEN PRIVATE LIMITED

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```

### Contributing to Android Interview Questions
Just make pull request. You are in!
