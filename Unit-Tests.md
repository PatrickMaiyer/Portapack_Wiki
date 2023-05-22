## TL;DR;
`cmake --build . --target build_tests && ctest --output-on-failure`

## Tests

* Unit tests are written using the [doctest](https://github.com/doctest/doctest/tree/master) framework.
* Tests are separated into application and baseband depending on which core is targeted.
* Test source is found under `firmware/test/`.
* Tests are not currently integrated with the PR pipeline.
* Tests are not currently built as part of a normal build and must be built manually.

## Building Tests
In your CMake build directory run `cmake --build . --target build_tests` which will build both application and baseband test hosts.

## Running Tests
Once tests are built, from your CMake build directory run `ctest --output-on-failure`.