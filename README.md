# OPTIC: Optimising Preferences and Time-Dependent Costs

https://nms.kcl.ac.uk/planning/software/optic.html

Modernized OPTIC to build out-of-the-box.
Some small modifications to the build system and source have been done.

## Dependencies & How to Build

Simply build with `CMake`:
```sh
# I recommend the ninja build system
cmake -Bbuild -GNinja .
cmake --build build
```

You will need the following dependencies:
- CMake for building
- Flex/Bison for parsing
- COIN-OR OSI, CLP, CBC, and CoinUtils
- GNU Scientific Library (GSL)
