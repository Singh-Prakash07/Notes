## Introduction 
  - In C++, strings are sequences of characters treated as a single data type. 
  - There are two primary ways to handle strings:
### 1. C-style Strings
  - Essentially character arrays terminated by a null character ('\0').
  - Less convenient to use compared to std::string.
  - Example: `char str[] = "Hello, world!";`
### 2. std::string
Part of the C++ Standard Template Library (STL).
Provides a more robust and flexible way to handle strings.
Offers numerous built-in functions for manipulation.
Example:
C++
#include <string>
using namespace std;

string str = "Hello, world!";
