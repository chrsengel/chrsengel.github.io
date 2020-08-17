---
title: Stuff I learned today 001
date: 2020-08-17 21:04:00 +0200
categories: [stuff i learned today]
tags: [stild, flutter, deep learning]
---

For a long time now I talked about wanting to start a series where I write down quick notes about everything I learned during the day. And now is finally the time to start this thing! I promise to try my best to stay consistent and keep the stuff concise. So let's start with today:

# Flutter Stuff

I just recently got into Flutter development, so some of these points might be totally dumb for experienced developers. Hit me up on [Twitter](https://twitter.com/chrsengel) if you find something utterly stupid or want to get in touch. I'd appreciate some feedback.

## Stuff that sucks

- Passing data between pages totally sucks and is way more complicated than it should be.
- Unfortunately there is no default hook for `resume` events. In my case, I wanted to update a view once a user came back to it (after it was already built previously) and there's no simple way to do this. I found some ressources online[^flutter-resume] that require you to extend the `WidgetsBindingObserver` class to be able to fire some actions. I couldn't get it to work though, so I decided to change my logic to use only the provider.
  - in React you could simply use the `useEffect` hook to accomplish this in a few lines of code

## Fluro

Today I discovered the [Fluro](https://pub.dev/packages/fluro) package. It brings web-like url parameters to your app and has a super simple configuration. You only need one extra file `router.dart` and you're good to go! Let's build a simple example to pass the parameter `id` via the route `/location/:id`.

Here's the `LocationView` widget:

```dart
// location_view.dart
class LocationView extends StatelessWidget {
  final String id;
  LocationView({this.id});
  // ...
}
```

Next is the `router.dart` file that will set up the route handlers that can be used to pass parameters.

```dart
// router.dart
import 'package:flutter/widgets.dart'; // required for the BuildContext
import 'package:fluro/fluro.dart';

class AppRouter {
  static Router router = Router();

  static Handler _locationHandler = Handler(
    handlerFunc: (BuildContext context, Map<String, dynamic> params) =>
        LocationView(id: params['id'][0])); // id is the parameter

  // your other routes
  // ...

  static void setupRouter() {
    router.define("/location/:id", handler: _locationHandler);
    // ...
  }
}
```

Once that is set up you need to edit your `main.dart` file to use Fluro as router manager.

```dart
// imports
void main() {
  AppRouter.setupRouter(); // 👈 defines your routes
  runApp(MyApp());
}


class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: "Your cool app",
      initialRoute: "/auth/register", // 👈 the initial route
      onGenerateRoute: AppRouter.router.generator, // 👈 use Fluro as route manager
    );
  }
}
```

Once that's done you can easily pass parameters to your routes, like so:

```dart
  // inside some context
  String id = "5f399892e809cbce81f7f9af";
  Navigator.pushReplacementNamed(context, '/location/$id');
```

You'll quickly notice that the default transition will be a `fromBottom` transition. To change that, simply add a `transitionType` to your route definitions.

```dart
  router.define("/location/:id", handler: _locationViewHandler, transitionType: TransitionType.inFromRight);
```

Fluro offers many more features, but I haven't used any of those yet. Check it out on [pub.dev](https://pub.dev/packages/fluro).


# AI stuff

Some of this stuff is from the "[Deep Learning Book](https://www.deeplearningbook.org/)" by Ian Goodfellow[^book].

- There is an AI project called [Cyc](https://en.wikipedia.org/wiki/Cyc) that aims to train a model to understand everyday knowledge. Apparently it works by explaining every object in the world and then relating these objects to each other. People started working on it in 1984 and two years ago the researchers published the latest stable release.
- **Representation Learning** basically describes to let an algorithm decide what features best describe an object. If these were handcrafted by humans it might not be the most optimal design. And evidently, letting algorithms learn features by themselves improves performance in the Image Recognition field. However, it comes with the problem that it can't easily understand the context of these features. This is where Deep Learning comes into play.
- Deep learning solves the problem in representation learning by splitting up complex representations into simpler representations. If I got this correct, an example could be the following: A car has four wheels and a bunch of windows. The representation learning algorithm does not easily understand that the combination of those representations result in the representation of a car. Deep learning on the other hand understands this.
- Deep learning exists since the 1940s but it was called differently throughout the years. The history is quite interesting, so it's worth to check out the book[^book]. According to Goodfellow, the deep learning field was introduced in three waves, each with different names:
  - 1940-1960: cybernetics
  - 1980-1990: connectionism and neural networks
  - since 2006: deep learning
- The MNIST database of handwritten digits is already 22 years old!
- The rule of thumb for superviced deep learning algorithms:
  > a supervised deep learning algorithm will generally achieve acceptable performance with around 5,000 labeled examples per category, and will match or exceed human performance when trained with a dataset containing at least 10 million labeled examples[^book]


# Footnotes

[^flutter-resume]: [https://stackoverflow.com/questions/49869873/flutter-update-widgets-on-resume](https://stackoverflow.com/questions/49869873/flutter-update-widgets-on-resume)
[^book]: [https://www.deeplearningbook.org/](https://www.deeplearningbook.org/)
