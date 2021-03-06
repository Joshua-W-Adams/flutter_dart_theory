# Interview Questions

Store of common interview questions for Flutter / Dart.

## 1. What is Flutter?

Flutter is a framework (library of code) for developing cross platform (Andriod, iOS, Web, Windows, Mac, Linux, Google Fuchsia) applications using a single code base.

## 2. What is Dart?

The official description is:

```
Dart is a client-optimized language for fast apps on any platform. 
```

But more generally Dart is simply a general purpose (designed to be used in a wide variety of purposes), garbage-collected, object orientated programming language.

Notes:
- Dart is AOT (Ahead Of Time) compiled to fast, predictable, native code.
- Dart can also be JIT (Just In Time) compiled for exceptionally fast development cycles and game-changing workflow (including Flutter’s popular sub-second stateful hot reload).

## 3. Is Flutter Free?

Yes, Flutter is open source and therefore free.

## 4. What is a Widget?

A Flutter app/user interface is considered a tree data structure of widgets. A widget represents a specific part of the user interface. 

A widget can therefore be thought of as a component in the Composite design pattern.

## 5. What is a Stateful Widget?

A widget that has state. State being anything that needs to be remembered about the view. 

Basically this means that the widget is dynamic and can change its appearance in response to events.

## 6. What is a Stateless Widget?

A widget that has no state.

## 7. What is the pubspec.yaml file?

It contains metadata about the project that the Dart and Flutter tooling needs to know.

It specifies dependancies, dev dependacies, fonts, files (images and videos), Flutter SDK version.

## 8. What are Packages and Plugins?

A "package" contains only Dart code.

A "plugin" contains both Dart and Native code (kotlin/js/swift/...).

A package can use plugins if it wants to. It will still qualify as a package.

A package/plugin is created to make code re-usueable across projects.

DartPub refers to packages and plugins as packages.

## 9. What are some common Flutter architectures? 

ScopedModel - an external flutter packages that allows you to easily pass a data Model from a parent Widget down to its descendants.
 
BLoC - Business Logic Component design pattern.

## 10. What are the advantages of Flutter?

- Create cross platform apps for a single code base
- Native like performance
- Supported by Google
- Open source
- Strong community

## 11. What is the purpose of the andriod/ios/web folders?

These folders holds a complete platform specific project. Flutter compiles to platform specific native code and is then injected into these folders. Resulting in a native application. 

For Andriod, the native application code is injected into the runner folder, then entire andriod folder is then compiled into an .apk file.

For iOS, the native code is injected into the runner folder, then the entire folder is compilied into a .ipa file.

## 12. What is Tween Animation?

Tween short for in-betweening is a linear interpolation between two values. Therefore a tween animation is an animation that animates linearly between two values. The framework itself calculates how to transition the widget to fulfill values.

## 13. What is Hot Reload?

An automatic rebuild of the widget tree persisting state. Allowing you to view the changes to your code in real-time. This only applies to non state related application code.

## 14. What is Hot Restart?

A rebuild of the widget tree destroying state.

## 15. What are some popular apps that use Flutter?

Google AdWords, Google Stadia, Reflectly and Grab.

## 16. What is the "main()" function?

In Dart, main() acts as the entry point for the program.

## 17. What is the "runApp()" function?

In Flutter, runApp() takes the given Widget and attaches it to the screen. Also makes it the root of the widget tree.

## 18. What are the different build modes in Flutter?

Debug - when you are developing your app and want hot reload.
Profile - when you want to analyze performance.
Release - when you are ready to release your app.

## 19. Why do we need mixins?

A mixin, mixes in additional functionality to a class. We need mixins because Dart does not support multiple inheritance.

## 20. How would you execute code only in certain modes?

You would use the kReleaseMode, kProfileMode, or kDebugMode check from the following package:

```dart
import 'package:flutter/foundation.dart' as Foundation;
```

## 21. What is the WidgetsApp?

A convenience class that wraps a numebr of widgets that are commonly required for an application. The MaterialApp or CupertinoApp build upon this widget. 

## 22. What is BuildContext?

Contains the information about where the widget is in the tree data structure.

## 23. What are Null-aware operators?

Operators that can deal with nulls. Some of these operators are as follows

### Null operator (??=) 

returns the expression on its left unless that expression’s value is null.

### Null-aware assignment operator (??= )

Assigns a value to a variable only if that variable is currently null.

### Null-aware access operator (?.)

object?. access object property only if object is not null

### Null-aware spread operator (...?)

The spread operator ... adds an array to another array

Null aware spread operator will only add items to the array if the they are not null.

## 24. What is a Stream?

A series of asynchronous events.

There are two types of streams in dart. A Single stream and a broadcast stream. Single streams allow one listener and gaurantee delivery of events. Boradcast streams allow multiple listeners but will drop events off the stream after they have been delivered.

Streams can be created by using an asynchronous generator function.

```dart
Stream<int> generateStream() async* {
    for (var i = 0; i < 10; i++) {
        /// wait have a second
        await Duration(milliseconds: 500);
        /// release event on the stream
        yield i;
    }
}
```

Streams can be listened to using either the await for loop or the .listen method. The only way to remove the underlying listener in the await for loop is to break or exit the loop.

## 25. Explain async and await?

Asynchronous programming allows you to perform tasks in paralell with other operations. i.e. it allows you to complete work while waiting for other operations to complete. Examples of async operations are fetching data from a REST API or writing to a database.

the async keyword defines a function as asynchronous.

the await keyword can only be used in an async or async* (generator) function. The function will not continue execution until the code defined at the await location has been completed. All code before and after the await keyword is executed synchronously.

## 26. How Does Dart AOT Work?

The compilier compiles native code from dart source code. 

For mobile applications source code is compilied for the underling processor architectures (ARM, ARM64 and x64) for both Android and iOS.

AOT (Ahead of Time) compilies the code before the application is launched.

JOT (Just In Time) compilies the application at runtime. i.e. is already launched.

## 27. What is a Future?

A future represents a single event that will be recieved at some point in the future.

The main components of a Future are shown below:

```dart
Future<int> someFutureValue() async {
    await Duration(milliseconds: 500);
    return 1;
}

void getSomeFutureValue() {
    // await for future to process
    someFutureValue.then((int value) {
        // process sucessful response
        print(value);
    }).catchError((error) {
        // process failed repsonse
        print(error);
    })
}
```

## 28. What is the difference between double.INFINITY and MediaQuery?

MediaQuery gets information about the device you are running on. e.g.
```dart
// get device width
MediaQuery.of(context).size.width
```
double.infinity is a double datatype with an infinite value.

In the context of widget the difference can be summarized into:

- I want to be as big as my parent allows (double.infinity)
- I want to be as big as the screen (MediaQuery).

Some Widgets allow their children to be as big as they want to be (Column, ListView, OverflowBox...). In that situation using double.infinity creates a paradox:

The parent allows any size
The child wants the biggest size allowed by the parent

To solve this paradox you can:
a) specify a height
b) use LayoutBuilder 
c) use InstrinicHeight (sizes its child to the child's intrinsic height)

## 29. Explain the Stateful Widget Lifecycle in detail?

The lifecycle of a stateful widget can be described as follows:

createState - our widget is comprised of two parts, the stateless widget class and the state. The state is generated by a call to createState() by the underlying framework.

initState() - first method called when creating a stateful class. All state variables are initialised here.

didChangeDependencies() - called immediately after initState.

build() - runs each time the widget tree is rebuilt. This happens as a result of setState, didUpdateWidget or didChangeDependencies.

didUpdateWidget() - called whenever the widget configuration changes. i.e. when the parent updates / passes through parameters.

setState() - called to set the internal widget state and issue a rebuild.

deactivate() - rarely used.

dispose() - when the widget is permanently removed. Typically used to clean up internal state and prevent memory leaks.

<img src="./../img/stateful_widget_lifecycle.png"></img>

## 30. What is the difference between var, const and final?

var declares a property with its data type inferred and its value can change.

Both final and const prevent a property from being changed.

A const property is a compile-time constant, which means that it must be created from constants available in compile-time. 

Compile-time is the time duration in which the programming code is converted to the machine code (i.e binary code).

They are instantiated during compile-time and therefore can be reused over and over again. They are a great way to optimise your application for time (speed) and space (memory).

For Example:

```dart
Column(
    children: [
        // will use the same widget in memory everytime Column is rebuilt
        const Text('first'),
        // will rebuild this widget everytime Column is rebuilt
        Text('second'),
    ]
)
```

A class constructor can be defined as const, which will create what is called a canonicalised instance. i.e. everytime the same parameters are passed through to the constructor the same instance will be retrieved from memory.

## 31. What is a Dart Isolate?

An isolate is what all Dart code runs in. It's like a little space on the machine with its own, private chunk of memory and a single thread running an event loop.

## 32. What are sync*, async*, yield and yield* in Dart?

* indicates a generator function. Generator functions produce a sequence of values. 

Generator functions can be asynchronous or synchronous.

- sync* is a synchronous generator function, returns an Iterable
- async* is a asynchronous generator function
- yield returns single value
- yield* hands over yielding to another function

They generate values on demand. Meaning values are only generated when some tries to iterate over the iterator or listen to the stream.

An iterable is a collection that you can move through sequentially one element at a time. List and set are two types of iterables.

Iterate is the process of moving through items in an iterable.

An iterable doesn't know how to iretate through all it's element. It’s the job of the iterator to move sequentially through all the elements of the iterable.

## 33. Who creates the navigator in Flutter?

The navigator is a Widget responsible for displaying screens(Routes in Flutter) on the top of each other(like in Stack). 

Navigator is included in the MaterialApp, CupertinoApp and WidgetsApp. Separate instances can also be created at any point in the tree data structure.

## 34. Does the State object live after calling dispose()?

Yes, it will live afater calling dispose. Therefore you must ensure you cleanup any relevant state variables to prevent memeory leaks. E.g. a streamController.

## 35. How do you make a class variable private?

prefix it with an _.

## 36. How do you make a variable global?

Move it outside the class. It will then be made available anywhere you import it.

## 37. Provide an answer for the following REST API sample?

GitHub Jobs has an open API for querying software engineering-related job positions. The following URL returns a list of remote jobs:

```
https://jobs.github.com/positions.json?location=remote
```

Given the following simple data class, in which you only care about the company name and job title, write a function that returns a Future with a List of Jobs. You can ignore error checking for this question.

```dart
class Job {
  Job(this.company, this.title);

  final String company;
  final String title;
}
```

Given REST APIs return data in the form of Map<String, dynamic> The first step is to add a fromMap function to the Job class.

```dart
factory Job.fromMap(Map<String,dynamic> json) {
    final company = json['company'];
    final title = json['title'];
    return Job(company, title);
}
```

Next we need a way of sending HTTP requests to an external service. We can do this by using the http package maintained by the Flutter team.

Define as a dependancy.

```yaml
dependancies:
    http: ^0.12.1
```
^ = all compatible version changes (i.e. minor and patches).

Create the method.

```dart
import 'package:http/http.dart' as http;

Future<List<Job>> getJobs() async {
    // define the uri components
    final String host = 'jobs.github.com';
    final String path = 'positions.json';
    final Map<String, dynamic> queryParameters = {'location': 'remote'};
    // build the uri
    final Uri uri = Uri.https(host, path, queryParameters);
    // define the http headers
    final Map<String, String> headers = {'Accept': 'application/json'};
    // perform http get request on uri    
    final results = await http.get(uri, headers: headers);
    final jsonList = json.decode(results.body) as List;
    return jsonList.map((job) => Job.fromJson(job)).toList();
}
```

## 38. What are the limitations of Flutter?

- Larger release size
- Lack of third party libraries
- Is not a native language so it will never have the performance or features of a true
native application

## 39. What makes Flutter unique?

Flutter does not depend on web browser technology nor the set of widgets that each device contains. Instead it uses its own rendering engine to draw widgets. This rendering engine provides very high performance. This concept makes flutter unique.

## 40. In What technology is Flutter built?

C, C++, Skia (2D rendering engine) and Dart.

## 41. What are extensions, and how do we create one?

A way to add additional functionality to any data type.

For example

```dart
extension NumberParsing on String {
    int parseInt() {
        return int.parse(this);
    }
}
```

## 42. What is a dynamic type?

dynamic is a type underlying all Dart objects. Can change TYPE of the variable, & can change VALUE of the variable later in code.

## 43. What is the point of getters and setters?

getters and setters are a way to read and write the values of properties in a class. All classes have Implicit getters and setters for all their properties.

You can explicitly define the getters and setters for you properties to remove or add additional functionality. 
```
Implicit - always to be found in, but not stated in detail.
```
```
Explicit - stated clearly and in detail, leaving no room for confusion or doubt.
```
For example...

```dart
class Car {
    String _model = 'some model';
    // no setter is defined therefore you cannot do...
    // car.model = 'new value'
    String get model {
        return _model;
    }
}

class Car {
    String _model= 'some model';
    
    String get model {
        return _model;
    }

    // internal model property can only be set under specific conditions.
    // i.e. car.model = 'abc' will not work
    set model(String value) {
        if (value.length > 3) {
            _model = value;
        }
    }
}
```

## 44. What is a Sliver?

A sliver is a portion of a scrollable area. 

You can use slivers to achieve custom scrolling effects, such as elastic scrolling.

## 45. What’s a difference between the debug and profile modes?

Debug mode is used for debugging and developing your app. In profile mode only basic
debugging functionality is persisted, just enough to performance profile your app.

## 46. What’s Flutter tree shaking?

All unused code in our application is not included in the final compilation.

This is great because we can use big libraries and all the dead code wont be included in our app.

## 47. How can we run code on a different Isolate? And Why would we do this?

You run dart code on a different isolate by calling the **compute** function.

We want to do this to move expensive code to a separate thread, memory allocation and event loop to prevent blocking our main isolate / blocking our ui.

## 48. How do you talk to native code or libraries from within a Flutter app?

We need to create a bridge between the dart code and native language. We do this by creating a plugin.

**Platform channels**. One type of channel is the **method channel**. Where data is serialized on the Dart side and then sent to the native side. You can write native code to interact with the platform before sending a serialized message back.

The second type of platform channel is the **event channel**, which you use to send a stream of data from the native platform back to Flutter.

## 49. What is ephemeral state?

Ephemeral means lasting for a very short time. In the context of Flutter this means state that only exists within a single widget.

## 50. What is vsync?

Vsync keeps the track of screen. So that Flutter does not render animations when the screen is not being displayed.

## 51. What is the Flutter inspector?

A tool that helps in visualizing and exploring the widget trees.

# HOLD

## AA. How do environment variables work in Flutter?

<!-- The twelve factor app dictates that environment variables must be stored and managed separately to code. These are things that may change between deploys.
flutter_dot_env package to add a .env file to project folder.

flutter_config package

only for non-sensitive data.

It is impossible to keep secrets secure on client side applications. Therefore you should design your applications with this in mind.

```dart
const String.fromEnvironment('CLIENT_ID')
```
```dart
Platform.environment['CLIENT_ID']
```
flutter_secure_storage is a great package for storing api keys -->

## XX. What is the event loop, and what is its relationship to isolates?

## YY. What is an InheritedWidget?

## ZZ. What are Flavours in Flutter?
