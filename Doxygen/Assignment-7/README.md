# Assignment 7: Doxygen Code Documentation

## Objective
Learn to create comprehensive source code documentation using Doxygen, including automatic generation of API documentation, class diagrams, and professional technical documentation from annotated code.

## What I Learned

### Introduction to Doxygen

Doxygen is a documentation generator that creates documentation from annotated source code. It extracts:
- Class hierarchies and relationships
- Function and method signatures
- Parameter and return value descriptions
- Code structure and dependencies
- Visual diagrams of code organization

### Setting Up Doxygen

**Installation:**
```bash
# Linux/Ubuntu
sudo apt-get install doxygen graphviz

# macOS
brew install doxygen graphviz

# Windows
# Download from www.doxygen.nl
```

**Creating Configuration File:**
```bash
doxygen -g Doxyfile
```

This creates `Doxyfile` with default settings.

### Documentation Comment Styles

**JavaDoc Style:**
```cpp
/**
 * @brief Brief description of function
 * @param name Parameter description
 * @return Return value description
 */
int myFunction(string name);
```

**Qt Style:**
```cpp
/*!
 * \brief Brief description
 * \param name Parameter description
 * \return Return value description
 */
```

**Triple-Slash Style:**
```cpp
/// @brief Brief description
/// @param name Parameter description
/// @return Return value description
```

### File Documentation

**Header File:**
```cpp
/**
 * @file calculator.h
 * @brief Calculator class declaration
 * @author Your Name
 * @date 2024-11-12
 * @version 1.0
 * 
 * This file contains the Calculator class which provides
 * basic arithmetic operations.
 */

#ifndef CALCULATOR_H
#define CALCULATOR_H

// Class definition...

#endif // CALCULATOR_H
```

### Class Documentation

**Documenting Classes:**
```cpp
/**
 * @class Calculator
 * @brief Performs arithmetic calculations
 * 
 * The Calculator class provides methods for basic
 * arithmetic operations including addition, subtraction,
 * multiplication, and division.
 * 
 * @author Your Name
 * @date 2024-11-12
 * 
 * Example usage:
 * @code
 * Calculator calc;
 * double result = calc.add(5.0, 3.0);
 * cout << "Result: " << result << endl;
 * @endcode
 */
class Calculator {
private:
    double result;  ///< Stores the last calculation result
    
public:
    /**
     * @brief Default constructor
     * Initializes result to 0.0
     */
    Calculator();
    
    /**
     * @brief Destructor
     */
    ~Calculator();
    
    /**
     * @brief Adds two numbers
     * 
     * This function performs addition of two double values
     * and stores the result internally.
     * 
     * @param a First operand
     * @param b Second operand
     * @return Sum of a and b
     * 
     * @note This is a simple addition operation
     * @see subtract(), multiply(), divide()
     */
    double add(double a, double b);
    
    /**
     * @brief Subtracts second number from first
     * @param a Minuend
     * @param b Subtrahend
     * @return Difference a - b
     */
    double subtract(double a, double b);
    
    /**
     * @brief Multiplies two numbers
     * @param a First factor
     * @param b Second factor
     * @return Product a × b
     */
    double multiply(double a, double b);
    
    /**
     * @brief Divides first number by second
     * 
     * @param a Dividend
     * @param b Divisor
     * @return Quotient a ÷ b
     * @throws std::invalid_argument if b is zero
     * 
     * @warning Division by zero will throw an exception
     * 
     * Example:
     * @code
     * Calculator calc;
     * try {
     *     double result = calc.divide(10.0, 2.0);
     * } catch (std::invalid_argument& e) {
     *     cerr << "Error: " << e.what() << endl;
     * }
     * @endcode
     */
    double divide(double a, double b);
    
    /**
     * @brief Gets the last computed result
     * @return Last calculation result
     */
    double getResult() const;
    
    /**
     * @brief Resets the result to zero
     */
    void reset();
};
```

### Implementation Documentation

**Source File:**
```cpp
/**
 * @file calculator.cpp
 * @brief Implementation of Calculator class
 */

#include "calculator.h"
#include <stdexcept>

Calculator::Calculator() : result(0.0) {
    // Initialize with zero
}

Calculator::~Calculator() {
    // Cleanup if needed
}

double Calculator::add(double a, double b) {
    result = a + b;
    return result;
}

double Calculator::subtract(double a, double b) {
    result = a - b;
    return result;
}

double Calculator::multiply(double a, double b) {
    result = a * b;
    return result;
}

double Calculator::divide(double a, double b) {
    if (b == 0.0) {
        throw std::invalid_argument("Division by zero");
    }
    result = a / b;
    return result;
}

double Calculator::getResult() const {
    return result;
}

void Calculator::reset() {
    result = 0.0;
}
```

### Common Doxygen Tags

**Function/Method Tags:**
- `@brief` - Short description
- `@param` - Parameter description
- `@return` - Return value description
- `@throws/@exception` - Exception thrown
- `@retval` - Specific return value

**Code Structure Tags:**
- `@file` - File description
- `@class` - Class description
- `@struct` - Structure description
- `@enum` - Enumeration description

**Cross-Reference Tags:**
- `@see` - See also reference
- `@ref` - Reference to entity
- `@link` - Hyperlink to entity

**Annotation Tags:**
- `@note` - Important note
- `@warning` - Warning message
- `@todo` - To-do item
- `@bug` - Bug description
- `@deprecated` - Deprecated feature

**Code Example Tags:**
- `@code` ... `@endcode` - Code block
- `@example` - Example file

**Author/Version Tags:**
- `@author` - Author name
- `@date` - Date
- `@version` - Version number
- `@copyright` - Copyright notice

### Configuring Doxyfile

**Important Settings:**
```
# Project Information
PROJECT_NAME           = "Calculator Library"
PROJECT_NUMBER         = "1.0"
PROJECT_BRIEF          = "A simple calculator library"

# Input Settings
INPUT                  = src include
RECURSIVE              = YES
FILE_PATTERNS          = *.cpp *.h *.hpp

# Output Settings
OUTPUT_DIRECTORY       = docs
GENERATE_HTML          = YES
HTML_OUTPUT            = html
GENERATE_LATEX         = YES
LATEX_OUTPUT           = latex

# Extraction Settings
EXTRACT_ALL            = YES
EXTRACT_PRIVATE        = YES
EXTRACT_STATIC         = YES
EXTRACT_LOCAL_CLASSES  = YES

# Diagram Settings
HAVE_DOT               = YES
CLASS_DIAGRAMS         = YES
COLLABORATION_GRAPH    = YES
INCLUDE_GRAPH          = YES
INCLUDED_BY_GRAPH      = YES
CALL_GRAPH             = YES
CALLER_GRAPH           = YES
GRAPHICAL_HIERARCHY    = YES
DIRECTORY_GRAPH        = YES
```

### Generating Documentation

**Basic Generation:**
```bash
doxygen Doxyfile
```

**Output Directory Structure:**
```
docs/
├── html/
│   ├── index.html      # Main page
│   ├── classes.html    # Class list
│   ├── files.html      # File list
│   ├── functions.html  # Function list
│   └── ...
└── latex/
    ├── refman.tex      # LaTeX source
    ├── Makefile        # Build file
    └── ...
```

### Creating Main Page

**Mainpage Documentation:**
```cpp
/**
 * @mainpage Calculator Library Documentation
 * 
 * @section intro_sec Introduction
 * 
 * Welcome to the Calculator Library documentation.
 * This library provides a simple Calculator class for
 * performing basic arithmetic operations.
 * 
 * @section features_sec Features
 * 
 * - Addition
 * - Subtraction
 * - Multiplication
 * - Division with error handling
 * - Result storage
 * 
 * @section install_sec Installation
 * 
 * @subsection step1 Step 1: Clone Repository
 * @code
 * git clone https://github.com/user/calculator.git
 * @endcode
 * 
 * @subsection step2 Step 2: Compile
 * @code
 * make
 * @endcode
 * 
 * @section usage_sec Usage Example
 * 
 * @code
 * #include "calculator.h"
 * 
 * int main() {
 *     Calculator calc;
 *     double sum = calc.add(10.0, 5.0);
 *     double product = calc.multiply(sum, 2.0);
 *     cout << "Result: " << product << endl;
 *     return 0;
 * }
 * @endcode
 */
```

### Custom Pages

**Additional Documentation Pages:**
```cpp
/**
 * @page installation Installation Guide
 * 
 * @section requirements Requirements
 * 
 * - C++11 compiler or later
 * - CMake 3.10+
 * - Doxygen (for documentation)
 * 
 * @section build Building the Library
 * 
 * @subsection unix Unix/Linux/macOS
 * @code
 * mkdir build
 * cd build
 * cmake ..
 * make
 * @endcode
 * 
 * @subsection windows Windows
 * @code
 * mkdir build
 * cd build
 * cmake ..
 * cmake --build .
 * @endcode
 */

/**
 * @page examples Usage Examples
 * 
 * @section basic_example Basic Usage
 * 
 * @code
 * Calculator calc;
 * double result = calc.add(5, 3);
 * @endcode
 * 
 * @section advanced_example Advanced Usage
 * 
 * @code
 * Calculator calc;
 * calc.add(10, 5);
 * calc.multiply(calc.getResult(), 2);
 * cout << "Final: " << calc.getResult();
 * @endcode
 */
```

### Grouping Documentation

**Creating Groups:**
```cpp
/**
 * @defgroup arithmetic Arithmetic Operations
 * @brief Basic arithmetic functions
 * @{
 */

double add(double a, double b);
double subtract(double a, double b);
double multiply(double a, double b);
double divide(double a, double b);

/** @} */ // end of arithmetic group

/**
 * @defgroup utility Utility Functions
 * @brief Helper and utility functions
 * @{
 */

void reset();
double getResult() const;

/** @} */ // end of utility group
```

### Parameter Documentation Styles

**Direction Specifiers:**
```cpp
/**
 * @param[in] input Input parameter (read-only)
 * @param[out] output Output parameter (will be modified)
 * @param[in,out] data Input/output parameter (read and modified)
 */
void process(const Data& input, Result& output, Cache& data);
```

### Generating PDF

**From LaTeX Output:**
```bash
cd docs/latex
make pdf
# Output: refman.pdf
```

### Diagrams Generated

With Graphviz (HAVE_DOT = YES):

1. **Class Hierarchy** - Inheritance relationships
2. **Collaboration Diagrams** - Class dependencies
3. **Include Graphs** - Header file dependencies
4. **Call Graphs** - Function call relationships
5. **Caller Graphs** - Functions calling this function
6. **Directory Graphs** - Directory structure

## Best Practices

1. **Document Public API**: All public members must be documented
2. **Brief First**: Start with concise @brief description
3. **Detailed After**: Add detailed explanation if needed
4. **Parameter Order**: Document params in declaration order
5. **Return Values**: Always document return values
6. **Examples**: Include @code blocks for complex functions
7. **Cross-References**: Use @see to link related items
8. **Update Regularly**: Keep docs in sync with code changes

## Common Documentation Patterns

**Getter Function:**
```cpp
/**
 * @brief Gets the current value
 * @return Current value
 */
double getValue() const;
```

**Setter Function:**
```cpp
/**
 * @brief Sets the value
 * @param value New value to set
 */
void setValue(double value);
```

**Boolean Query:**
```cpp
/**
 * @brief Checks if value is valid
 * @return true if valid, false otherwise
 */
bool isValid() const;
```

## Key Takeaways

- Doxygen generates documentation automatically
- Special comment syntax triggers extraction
- Supports multiple programming languages
- Generates both HTML and LaTeX/PDF
- Creates visual diagrams with Graphviz
- Cross-referenced and searchable output
- Minimal overhead for developers
- Professional publication-quality documentation

## Common Mistakes to Avoid

1. ❌ Forgetting to document public members
2. ❌ Using plain comments instead of Doxygen syntax
3. ❌ Not updating docs when code changes
4. ❌ Missing @param for all parameters
5. ❌ Incomplete @brief descriptions
6. ❌ No usage examples for complex APIs

## Files

This assignment focused on code documentation with Doxygen documented in this README.

## Compilation Steps

```bash
# 1. Generate Doxyfile
doxygen -g Doxyfile

# 2. Edit Doxyfile (configure settings)

# 3. Generate documentation
doxygen Doxyfile

# 4. View HTML
firefox docs/html/index.html

# 5. Generate PDF (optional)
cd docs/latex
make pdf
```

## Viewing Documentation

**HTML Documentation:**
```bash
# Open in browser
open docs/html/index.html       # macOS
xdg-open docs/html/index.html   # Linux
start docs/html/index.html      # Windows
```

**PDF Documentation:**
```bash
cd docs/latex
make pdf
# Open refman.pdf
```

## Resources

- Doxygen Manual: https://www.doxygen.nl/manual/
- Graphviz: https://graphviz.org/
- Markdown in Doxygen: https://www.doxygen.nl/manual/markdown.html
