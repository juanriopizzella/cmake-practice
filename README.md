# cmake-practice

Working through the official CMake tutorial, one exercise at a time, to build
a solid foundation before using CMake on a larger C++ project.

Source: https://cmake.org/cmake/help/v3.27/guide/tutorial/index.html
(CMake 3.27 docs — matches the version installed here: `cmake --version` → 3.27.1)

Editor: VS Code, with commands run manually in its integrated terminal — no
CMake Tools extension, so nothing is hidden behind IDE integration.

Starter files for each step are pulled from the CMake GitHub mirror, e.g.:
https://github.com/Kitware/CMake/tree/v3.27.9/Help/guide/tutorial/Step1

## Progress

- [ ] Step 1 — A Basic Starting Point
  - [x] Exercise 1 — Building a Basic Project
  - [ ] Exercise 2 — Specifying the C++ Standard
  - [ ] Exercise 3 — Adding a Version Number and Configured Header File
- [ ] Step 3 — Adding Usage Requirements for a Library
- [ ] Step 4 — Adding Generator Expressions

## Notes

Each step's folder starts from the "before" state in the tutorial repo; the
following step's folder is the answer key. Trying it unaided before peeking
is the point.

## Boiled Down Summaries

### Step 1

#### Exercise 1

##### cmake Command

- Create a path-to-build folder, and change to its directory within the terminal
- Run `cmake ../Step1`, Step1 being the path-to-source (contains CMakeLists.txt and tutorial.cxx)

Terminal's Output Timeline (reduction)
1. Before reading CMakeLists.txt
   - Generator is identified (e.g. Visual Studio 17 2022)
2. Configuration: CMakeLists.txt
   - project() → Since you have not specified a language, both C and C++ compilers and their ABI info are identified and tested
3. Generation based on what was configured
   - MSBuild solution and project files

##### CMakeLists.txt Commands

`cmake_minimum_required(VERSION 3.1)`

- Installed version < 3.1 → Error
- Installed version >= 3.1 → Runs, NEW policies till 3.1

`cmake_minimum_required(VERSION 3.1...4.0)`

- Same as before regarding the error
- Installed version >= 3.1 → Runs, NEW policies <= 4.0 (with the installed CMake as the cap)

`project(Tutorial)`

- Sets the project name (and stores it in variables you can use later)
- Build systems were already identified upon CMake startup, before any command from CMakeLists.txt ran. project() just identifies and tests the compiler

`add_executable(Tutorial tutorial.cxx)`

- Based on the source file tutorial.cxx, have Tutorial as the name of the executable being built and also the name CMake will use to target it
