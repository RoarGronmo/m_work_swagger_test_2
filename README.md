# m_work_swagger_test_2

A simple test testing `swagger_dart_code_generator 2.2.5+1`

## Was created like this: 

1. Create an ordinary Flutter project in AS2020.3.1
2. Create a `swaggers` directory in project path (beside lib path)
3. Copy your `.swagger` file into here
4. Add under `dependencies:` in `pubspec.yaml` file:
```
  #---swagger changes---
  chopper: ^4.0.3
  json_annotation: ^4.3.0
```
5. Add under `dev.dependencies:` in `pubspec.yaml` file:
```
  #---swagger changes---
  build_runner: ^2.1.5
  chopper_generator: ^4.0.3
  json_serializable: ^6.0.1
  swagger_dart_code_generator: ^2.2.5+1
```
6. create `build.yaml` in project path (at same level as `pubspec.yaml`) with theese contents:
```
targets:
  $default:
    sources:
      - swaggers/**
      - lib/**
    builders:
      chopper_generator:
        options:
          header: "//Generated code"
      swagger_dart_code_generator:
        options:
          input_folder: "lib/"
          output_folder: "lib/swagger_generated_code"
```
Note: In AS2020.3.1 you will receive a warning/error that the `targets:` section is not allowed here...

7. Do a "pub get" in the pubspec.yaml file (shortcut at the top if you have configured dart right).
8. Open an powershell and navigate to your project path
9. Run following command `flutter pub run build_runner build --delete-conflicting-outputs`
10. The build fails...
