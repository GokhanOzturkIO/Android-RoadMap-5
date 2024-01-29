# Android-RoadMap-5 `v1.0.0-alpha01`

**Androidv14 - Level34**

## CORE AREAS - 1

### 1. Services

#### 1.1 Services overview

- Types of Services
- Choosing between a service and a thread
- The basics
    - Declaring a service in the manifest
- Creating a started service
    - Extending the Service class
    - Starting a service
    - Stopping a service
- Creating a bound service
- Sending notifications to the user
- Managing the lifecycle of a service
    - Implementing the lifecycle callbacks

#### 1.2 Foreground services

##### 1.2.1 Foreground services overview

- User can dismiss notification by default
- Services that show a notification immediately
- Declare foreground services in your manifest
- Request the foreground service permissions
- Foreground service prerequisites
- Start a foreground service
- Remove a service from the foreground
- Handle user-initiated stopping of apps running foreground services
    - Exemptions
- Use purpose-built APIs instead of foreground services
- Restrictions on starting a foreground service from the background

##### 1.2.2 Foreground service types

- Camera
- Connected device
- Data sync
- Health
- Location
- Media
- Media projection
- Microphone
- Phone call
- Remote messaging
- Short service
- Special use
- System exempted
- Google Play policy enforcement for using foreground service types

#### 1.3 Bound services overview

- The basics
    - Bind to a started service
- Create a bound service
    - Extend the Binder class
    - Use a Messenger
- Bind to a service
    - Additional notes
- Manage the lifecycle of a bound service

#### 1.4 Android Interface Definition Language (AIDL)

- Defining an AIDL interface
    - Create the .aidl file
    - Implement the interface
    - Expose the interface to clients
- Passing objects over IPC
- Methods with Bundle arguments containing Parcelables
- Calling an IPC method

---

### 2. Background Work

#### 2.1 Background work overview

- Terminology
- Choose the right option
- Asynchronous work
- Background work
- Foreground services
- Alternative APIs
- Tasks initiated by the user
    - Does the task need to continue running while the app is in the background?
    - Will there be a bad user experience if the task is deferred or interrupted?
    - Is it a short, critical task?
    - Is there an alternative API just for this purpose?
- Tasks in response to an event

#### 2.2 Background optimizations

- User-initiated restrictions
- Restrictions on receiving network activity broadcasts
    - Schedule work on unmetered connections
    - Monitor network connectivity while the app is running
- Restrictions on receiving image and video broadcasts
    - Determine which content authorities triggered work
- Further optimize your app

#### 2.3 Keep the device awake

- Alternatives to using wake locks
- Keep the screen on
    - Ambient Mode for TV
- Keep the CPU on

#### 2.4 Asynchronous work

##### 2.4.1 Asynchronous background processing

- Java and Kotlin

##### 2.4.2 Asynchronous work with Java threads

- Concurrency libraries
- Examples overview
- Create multiple threads
- Execute in a background thread
    - Make the request
    - Trigger the request
    - Handle dependency injection
    - Execute in a background thread
    - Considerations
- Communicate with the main thread
- Use handlers
- Configure a thread pool

##### 2.4.3 Coroutine in Android

###### **2.4.3.1 Kotlin coroutines on Android**

- Features
- Examples overview
- Dependency info
- Executing in a background thread
- Use coroutines for main-safety
- Handling exceptions

###### **2.4.3.2 Improve app performance with Kotlin coroutines**

- Manage long-running tasks
- Use coroutines for main-safety
    - Performance of withContext()
- Start a coroutine
    - Parallel decomposition
- Coroutines concepts
    - CoroutineScope
    - Job
    - CoroutineContext

###### **2.4.3.3 Testing Kotlin coroutines on Android**

- Invoking suspending functions in tests
- TestDispatchers
    - StandardTestDispatcher
    - UnconfinedTestDispatcher
- Injecting test dispatchers
- Setting the Main dispatcher
- Creating dispatchers outside a test
- Creating your own TestScope
- Injecting a scope

###### **2.4.3.4 Best practices for coroutines in Android**

- Inject Dispatchers
- Suspend functions should be safe to call from the main thread
- The ViewModel should create coroutines
- Don't expose mutable types
- The data and business layer should expose suspend functions and Flows
    - Creating coroutines in the business and data layer
- Inject TestDispatchers in tests
- Avoid GlobalScope
- Make your coroutine cancellable
- Watch out for exceptions

###### **2.4.3.5 Additional resources for Kotlin coroutines and flow**

- Basics
- Cancellation
- Exceptions
- Scopes
- Flow
- Testing
- Libraries, Jetpack, and Coroutines
- Coroutines in the view layer
- Under the hood

##### 2.4.4 Flow in Android

###### **2.4.4.1 Kotlin flows on Android**

- Creating a flow
- Modifying the stream
- Collecting from a flow
- Catching unexpected exceptions
- Executing in a different CoroutineContext
- Flows in Jetpack libraries
- Convert callback-based APIs to flows

###### **2.4.4.2 Testing Kotlin flows on Android**

- Creating a fake producer
- Asserting flow emissions in a test
    - Continuous collection during a test
- Testing StateFlows
    - Working with StateFlows created by stateIn

###### **2.4.4.3 StateFlow and SharedFlow**

- `StateFlow`
    - StateFlow, Flow, and LiveData
- Making cold flows hot using `shareIn`****
- SharedFlow

##### 2.4.5 Using a ListenableFuture

- Required libraries
- Getting the result of a `ListenableFuture`****
    - Adding a callback
    - Suspending in Kotlin
    - Interop with RxJava
- Creating a `ListenableFuture`****
    - Creating an immediate future
    - Using a coroutine
    - Converting a callback
    - Converting from RxJava `Single`****

##### 2.4.6 Parcelable implementation generator

- Supported types
- Custom `Parcelers`

##### 2.4.7 Kotlin Multiplatform

- Multiplatform Jetpack libraries
- Tooling support

##### 2.4.8 Associate Android Developer certification in Kotlin

#### 2.5 Persistent work

##### 2.5.1 About Persistent work

- Types of persistent work
- WorkManager Features
    - Work constraints
    - Robust scheduling
    - Expedited work
    - Flexible retry policy
    - Work chaining
    - Built-In threading interoperability
- Use WorkManager for reliable work
- Relationship to other APIs
- Replace deprecated APIs

##### 2.5.2 Getting started

###### **2.5.2.1 Getting started with WorkManager**

- Define the work
- Create a WorkRequest
- Submit the WorkRequest to the system

###### **2.5.2.2 Define work requests**

- Overview
- Schedule one-time work
- Schedule expedited work
    - Quotas
- Schedule expedited work
    - Backwards compatibility and foreground services
    - Worker
    - CoroutineWorker
    - Sample app
    - Deferred expedited work
- Schedule periodic work
    - Flexible run intervals
    - Effect of Constraints on Periodic Work
- Work constraints
- Delayed Work
- Retry and backoff policy
- Tag work
- Assign input data

##### 2.5.3 How to

###### **2.5.3.1 Work states**

- One-time work states
- Periodic work states
- Blocked state

###### **2.5.3.2 Managing work**

- Unique Work
    - Conflict resolution policy
- Observing your work
    - Complex work queries
- Cancelling and stopping work
- Stop a running Worker
    - onStopped() callback

###### **2.5.3.3 Chaining work**

- Input Mergers
    - OverwritingInputMerger
    - ArrayCreatingInputMerger
- Chaining and Work Statuses

###### **2.5.3.4 Support for long-running workers**

- Creating and managing long-running workers
    - Kotlin
    - Java
- Add a foreground service type to a long-running worker
    - Declare foreground service types in app manifest
    - Specify foreground service types at runtime

###### **2.5.3.5 Observe intermediate worker progress**

- Update Progress
- Observing Progress

###### **2.5.3.6 Update work that is already enqueued**

- Avoid canceling work
    - When to cancel work
    - When to update work
- How to update work
    - Update work example
    - Handle the result
- Track work with generations
    - Track generation example
- Policies for updating work

##### 2.5.4 Threading

###### **2.5.4.1 Threading in WorkManager**

###### **2.5.4.2 Threading in Worker**

###### **2.5.4.3 Threading in CoroutineWorker**

- Running a CoroutineWorker in a different process

###### **2.5.4.4 Threading in RxWorker**

###### **2.5.4.5 Threading in ListenableWorker**

- Running a ListenableWorker in a different process

##### 2.5.5 Configuration

###### **2.5.5.1 Custom WorkManager Configuration and Initialization**

- On-Demand Initialization
    - Remove the default initializer
    - Implement Configuration.Provider
- Custom initialization before WorkManager 2.1.0
    - Default initialization
    - Custom initialization

##### 2.5.6 Migrate from legacy solutions

###### **2.5.6.1 Migrating from Firebase JobDispatcher to WorkManager**

- Gradle setup
- From JobService to workers
    - JobService maps to a ListenableWorker
    - SimpleJobService maps to a Worker
- JobBuilder maps to WorkRequest
    - Setting up inputs for the Worker
    - Setting up Constraints for the Worker
    - Creating the WorkRequest (OneTime or Periodic)
- Scheduling work
- Cancelling work
- Initializing WorkManager

###### **2.5.6.2 Migrating from GCMNetworkManager to WorkManager**

- Migrate to WorkManager
    - Include the WorkManager libraries
    - Modify your manifest
    - Define the Worker
    - Schedule the work request
- API mappings
    - Constraint mappings
    - Other mappings

##### 2.5.7 Testing

###### **2.5.7.1 Persistent work**

###### **2.5.7.1.1 Debug WorkManager**

- Enable logging
- Use adb shell dumpsys jobscheduler
- Request diagnostic information from WorkManager 2.4.0+

###### **2.5.7.1.2 Integration tests with WorkManager**

- Setup
- Concepts
- Structuring Tests
    - Basic Tests
- Simulate constraints, delays, and periodic work
    - Test Initial Delays
    - Testing Constraints
    - Testing Periodic Work

###### **2.5.7.1.3 Testing Worker implementation**

- Testing Workers
- Testing ListenableWorker and its variants

##### 2.5.8 Broadcasts

###### **2.5.8.1 Broadcasts overview**

- About system broadcasts
    - Changes to system broadcasts
- Receiving broadcasts
    - Manifest-declared receivers
    - Context-registered receivers
    - Effects on process state
- Sending broadcasts
- Restricting broadcasts with permissions
    - Sending with permissions
    - Receiving with permissions
- Security considerations and best practices

###### **2.5.8.1 Implicit broadcast exceptions**
