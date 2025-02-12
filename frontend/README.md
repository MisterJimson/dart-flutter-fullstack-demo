# frontend

This is a Flutter desktop app that provides the frontend for the Dart full-stack
demo.

> NOTE: The desktop app currently has only been tested on macOS. Testing on
> Linux or Windows and help with updating docs is appreciated!

## Environment

Configuration for `dev` and `prod` environments is stored under `assets/config`.

By default running `flutter run` will use `dev`:
```shell
flutter run -d macos
```

To use `prod` specify your environment when running `flutter run`:
```shell
flutter run -d macos --dart-define=ENV=prod
```

### Calling the backend API

The `Greeting` class for invoking the backend API is in `lib/services/api.dart`.

This class is instantiated and used by the model in `lib/models/app_model.dart`.

The JSON serializer / deserializer types are in `lib/services/api_types.dart`.
The serializer part (`lib/services/api_types.g.dart`) is built with the
following command:

```shell
flutter pub run build_runner build
```

Output:
```shell
[INFO] Generating build script...
[INFO] Generating build script completed, took 337ms

[INFO] Initializing inputs
[INFO] Reading cached asset graph...
[INFO] Reading cached asset graph completed, took 50ms

[INFO] Checking for updates since last build...
[INFO] Checking for updates since last build completed, took 423ms

[INFO] Running build...
[INFO] 1.0s elapsed, 8/9 actions completed.
[INFO] Running build completed, took 1.1s

[INFO] Caching finalized dependency graph...
[INFO] Caching finalized dependency graph completed, took 27ms

[INFO] Succeeded after 1.1s with 2 outputs (18 actions)
```

> Note: the JSON serializer code is maintained separately from the code in the
> backend. Tightly coupling client and server code through shared libraries
> (packages) is considered an anti-pattern with microservice architecture.
