# Dart Overview – Study Notes

These notes summarize the official Dart overview and add links at the exact places where each idea appears so you can jump back later.  
Source page: https://dart.dev/overview

---

## 1. What is Dart?

- Dart is a **client-optimized** language for building fast apps on any platform (web, mobile, desktop, server).[file:1]  
  - Docs: https://dart.dev/overview#dart-the-language
- Dart’s goal is to be the most productive language for **multi‑platform development**, with:
  - Sub‑second **hot reload**.
  - High‑quality production experiences across web, mobile, and desktop.[file:1]
- Dart is the language that powers **Flutter**:
  - Flutter uses Dart for UI, logic, and tooling (formatting, analyzing, testing).[file:1]  
  - Flutter docs: https://docs.flutter.dev

---

## 2. Dart: The Language

### 2.1 Type safety and static types

- Dart is **type safe**: it uses static type checking + runtime checks to ensure a variable’s **value always matches its static type**.[file:1]  
  - Overview: https://dart.dev/overview#dart-the-language  
  - Deep dive: https://dart.dev/language/type-system
- **Static type** = the type the compiler/analyzer knows for a variable (e.g. `int`, `String`, `List<int>`).  
  - If something is statically typed as `String`, at runtime it will always be a `String` (sound typing).[file:1]  
  - More: https://dart.dev/language/type-system#what-is-soundness

### 2.2 Type annotations and type inference

- Types are **mandatory** in the language but **annotations are optional**.[file:1]  
  - Dart can **infer** types from initial values or expressions.  
  - Example pattern:
    - `var x = 3;` → inferred as `int`
    - `final names = ['a', 'b'];` → inferred as `List<String>`  
  - Inference details: https://dart.dev/language/type-system#type-inference

### 2.3 `dynamic` type

- Dart’s type system is **flexible** and allows `dynamic`.[file:1]  
  - `dynamic` disables some static checking for that variable and relies on runtime checks.  
  - Useful for:
    - Quick experiments.
    - Very dynamic code (e.g. JSON‑like structures, loosely typed APIs).  
  - More about `dynamic`: https://dart.dev/language/type-system#implicit-downcasts-from-dynamic

### 2.4 Sound null safety

- Dart has **built‑in sound null safety**.[file:1]  
  - Non‑nullable types (e.g. `String`) **cannot be null**.
  - Nullable types are written with `?` (e.g. `String?`), and only these can hold `null`.
- “Sound” means:
  - If the analyzer decides something is **non‑null**, the runtime also guarantees it will never be `null`.[file:1]  
  - This prevents a whole class of **null reference exceptions**.  
- Null safety guide: https://dart.dev/null-safety  
- Understanding null safety: https://dart.dev/null-safety/understanding-null-safety

---

## 3. Example Program – Language Features

The overview shows a **Monte Carlo π** example to demonstrate many Dart features in one place.[file:1]  
Code: https://dart.dev/overview#dart-the-language

Key features shown:

- **Imports and libraries**:
  - `import 'dart:math' show Random;`  
  - Library docs: https://api.dart.dev/stable/dart-math/dart-math-library.html
- **Async / await** and **Streams**:
  - `void main() async { ... await for (final estimate in computePi().take(100)) { ... } }`
  - `Stream<double> computePi(...) async* { ... }`  
  - Async docs: https://dart.dev/libraries/dart-async
- **Generators**:
  - `async*` (async generator) returning `Stream<T>`.
  - `sync*` (sync generator) returning `Iterable<T>`.
  - Uses `yield` in a loop to lazily produce values.[file:1]  
  - Generators: https://dart.dev/language/async#generators
- **Nullable / non‑nullable** types:
  - Use of `int`, `double`, `int?` etc. reflects null safety rules.[file:1]  
  - Null safety tour: https://dart.dev/null-safety
- **Arrow syntax**:
  - Short methods or getters use `=>` instead of full `{}` body:
    - `bool get isInsideUnitCircle => x * x + y * y <= 1;`[file:1]  
  - Arrow syntax: https://dart.dev/language/functions#arrow-syntax
- **Classes and getters**:
  - `class Point { final double x; final double y; const Point(this.x, this.y); bool get isInsideUnitCircle => ... }`  
  - Classes: https://dart.dev/language/classes  
  - Getters/setters: https://dart.dev/language/classes#getters-and-setters

---

## 4. Dart: The Libraries

Dart ships with many **core libraries** for everyday tasks.[file:1]  
Library index: https://dart.dev/libraries

### 4.1 Core and collections

- `dart:core` – always imported; includes:
  - `int`, `double`, `num`, `String`, `bool`, `List`, `Map`, `Set`, `DateTime`, etc.[file:1]  
  - Docs: https://api.dart.dev/stable/dart-core/dart-core-library.html
- `dart:collection` – additional collections:
  - Queues, linked lists, hash maps, trees, etc.[file:1]  
  - Docs: https://api.dart.dev/stable/dart-collection/dart-collection-library.html

### 4.2 Data conversion and math

- `dart:convert` – encoding/decoding:
  - JSON, UTF‑8, and other formats.[file:1]  
  - Docs: https://api.dart.dev/stable/dart-convert/dart-convert-library.html
- `dart:math` – math utilities:
  - Constants (e.g. `pi`), random numbers (`Random`), math functions.[file:1]  
  - Docs: https://api.dart.dev/stable/dart-math/dart-math-library.html

### 4.3 Async, typed data, and IO

- `dart:async` – asynchronous programming:
  - `Future`, `Stream`, async utilities.[file:1]  
  - Docs: https://api.dart.dev/stable/dart-async/dart-async-library.html
- `dart:typed_data` – typed lists:
  - Efficient fixed‑size numeric lists, bytes, etc.[file:1]  
  - Docs: https://api.dart.dev/stable/dart-typed_data/dart-typed_data-library.html
- `dart:io` – I/O for non‑web apps:
  - Files, sockets, HTTP servers, command‑line I/O.[file:1]  
  - Docs: https://api.dart.dev/stable/dart-io/dart-io-library.html

### 4.4 FFI, isolates, and web

- `dart:ffi` – **Foreign Function Interface**:
  - Call native C APIs and interop with existing C libraries.[file:1]  
  - Docs: https://dart.dev/libraries/dart-ffi
- `dart:isolate` – **isolates** for concurrency:
  - Isolates are like threads with no shared memory; they communicate via messages.[file:1]  
  - Docs: https://api.dart.dev/stable/dart-isolate/dart-isolate-library.html
- **Web / browser interop**:
  - `dart:js_interop` and `package:web` for interacting with the DOM and JS in browsers.[file:1]  
  - Docs: https://dart.dev/web/js-interop

### 4.5 Packages (pub.dev)

- Beyond core libs, **packages** add thousands of features:
  - Official & community packages on https://pub.dev.[file:1]  
  - Common packages list: https://dart.dev/guides/packages

---

## 5. Dart: The Platforms

Dart supports **native** and **web** targets using different compilers.[file:1]  
Section: https://dart.dev/overview#dart-the-platforms

### 5.1 Dart Native (JIT & AOT)

For **mobile, desktop, and backend** apps:

- **JIT (Just‑In‑Time)** with Dart VM:
  - Used during development.
  - Enables fast **hot reload**, rich debugging, and DevTools.[file:1]  
  - Command: `dart run` or `flutter run` (with Flutter).
- **AOT (Ahead‑Of‑Time)** compilation:
  - For production builds.
  - Compiles to native machine code (ARM or x64).[file:1]  
  - Benefits:
    - Fast startup.
    - Consistent performance.  
- AOT apps run in a small **Dart runtime** that:
  - Enforces the type system.
  - Manages memory via garbage collection.[file:1]  
  - Runtime details: https://dart.dev/overview#the-dart-runtime
- Getting started with CLI/server:
  - https://dart.dev/tutorials/server/get-started  
  - `dart` tool: https://dart.dev/tools/dart-tool

### 5.2 Dart Web (JavaScript and WebAssembly)

For **browser** apps:

- Dart Web compiles Dart → **JavaScript** or **WebAssembly (WasmGC)**.[file:1]  
  - Section: https://dart.dev/overview#dart-web-javascript-dev--prod-and-webassembly
- Three main modes:
  1. **Incremental JS dev compiler** (fast dev, hot reload).
  2. **Optimizing JS production compiler** (dead‑code elimination, small & fast bundles).
  3. **Optimizing WebAssembly (WasmGC) production compiler** for super‑fast Wasm code.[file:1]

### 5.3 Flutter on top of Dart

- The **Flutter framework** is a multi‑platform UI toolkit that uses Dart as its language and runtime.[file:1]  
  - Build for:
    - iOS, Android
    - Web
    - Windows, macOS, Linux  
  - Flutter overview: https://flutter.dev

---

## 6. The Dart Runtime

Regardless of platform, all Dart code runs with a **runtime**.[file:1]  
Section: https://dart.dev/overview#the-dart-runtime

Main responsibilities:

- **Memory management**:
  - Dart uses automatic memory management with a **garbage collector (GC)**.[file:1]
- **Type system enforcement**:
  - Static checks (compile time) catch most issues.
  - Dynamic checks (runtime) for casts and type tests (`as`, `is`, `is!`).[file:1]
- **Isolate management**:
  - Controls the main isolate and any extra isolates created by the app.[file:1]

On native platforms, the runtime is bundled into the self‑contained executable produced by AOT compilation.[file:1]

---

## 7. Learning Dart – Recommended Path

The overview page also suggests how to start learning Dart.[file:1]  
Section: https://dart.dev/overview#learning-dart

Recommended resources:

1. **DartPad**  
   - Run Dart in the browser, no installation needed.  
   - https://dartpad.dev  
   - Intro: https://dart.dev/tools/dartpad

2. **Tour of the Dart language**  
   - Explains syntax, types, functions, classes, async, etc.  
   - https://dart.dev/language

3. **Dart tutorials** (e.g., command-line apps)  
   - https://dart.dev/tutorials  
   - Example: https://dart.dev/tutorials/server/cmdline

4. **API documentation**  
   - Core libraries reference: https://api.dart.dev

5. **Books and online training**  
   - Linked from: https://dart.dev/resources

---

## 8. Key Terms To Remember

- **Type safety**: variables’ values always match their static types; enforced by static and runtime checks.  
  - https://dart.dev/language/type-system
- **Static type**: the type known at compile time (`int`, `String`, etc.).
- **Type inference**: Dart infers types when you omit them (e.g. `var`, `final`).  
  - https://dart.dev/language/type-system#type-inference
- **`dynamic`**: opt‑out from static checking for that variable; more runtime checks.  
  - https://dart.dev/language/type-system#implicit-downcasts-from-dynamic
- **Sound null safety**: non‑nullable types can never be null; nullability is explicit with `?`.  
  - https://dart.dev/null-safety

Use these links to jump back to the official explanation whenever you want more depth or examples.
