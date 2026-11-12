# Doxygen Documentation

Doxygen is a documentation generation tool that creates comprehensive documentation from annotated source code. It extracts code structure and specially formatted comments to generate HTML, LaTeX, and other documentation formats.

## What is Doxygen?

Doxygen automatically generates documentation by:
- Parsing source code (C++, C, Java, Python, etc.)
- Extracting structure (classes, functions, variables)
- Processing special comment blocks
- Creating hyperlinked documentation
- Generating class diagrams and call graphs

## Key Concepts Learned

### Documentation Comments

**C++ Style Comments:**
```cpp
/**
 * @brief Short description
 * 
 * Detailed description of the function
 * with multiple lines if needed
 * 
 * @param name Parameter description
 * @param value Another parameter
 * @return Description of return value
 */
int myFunction(string name, int value);
```

**Alternative Style:**
```cpp
/// @brief Short description
/// Detailed description
/// @param x Parameter x
/// @return Return value
int calculate(int x);
```

**JavaDoc Style:**
```cpp
/**
 * Brief description
 * 
 * @param input Input parameter
 * @return Output value
 */
```

### Common Doxygen Tags

**Function Documentation:**
- `@brief` - Short description (one line)
- `@param` - Parameter description
- `@return` - Return value description
- `@throws` - Exception thrown
- `@see` - Cross-reference
- `@note` - Important note
- `@warning` - Warning message

**Class Documentation:**
- `@class` - Class description
- `@author` - Author name
- `@date` - Creation date
- `@version` - Version number

**Code Examples:**
- `@code` ... `@endcode` - Code block
- `@example` - Example file

### File Documentation

```cpp
/**
 * @file myfile.cpp
 * @brief Brief description of file
 * @author Author Name
 * @date Creation date
 * 
 * Detailed description of what
 * this file contains
 */
```

### Class Documentation

```cpp
/**
 * @class Calculator
 * @brief Performs mathematical calculations
 * 
 * This class provides basic arithmetic
 * operations including addition, subtraction,
 * multiplication, and division
 * 
 * @author Your Name
 * @date 2024
 */
class Calculator {
public:
    /**
     * @brief Adds two numbers
     * @param a First number
     * @param b Second number
     * @return Sum of a and b
     */
    int add(int a, int b);
    
    /**
     * @brief Subtracts second from first
     * @param a First number
     * @param b Number to subtract
     * @return Difference a - b
     */
    int subtract(int a, int b);
};
```

### Configuration File

**Doxyfile Creation:**
```bash
doxygen -g Doxyfile
```

**Key Configuration Options:**
```
PROJECT_NAME           = "My Project"
PROJECT_NUMBER         = 1.0
OUTPUT_DIRECTORY       = docs
INPUT                  = src
RECURSIVE              = YES
EXTRACT_ALL            = YES
GENERATE_HTML          = YES
GENERATE_LATEX         = YES
HAVE_DOT               = YES
CALL_GRAPH             = YES
CALLER_GRAPH           = YES
```

### Generating Documentation

**Basic Generation:**
```bash
doxygen Doxyfile
```

**Output:**
- `html/index.html` - HTML documentation
- `latex/` - LaTeX documentation

### Documentation Structure

**Member Groups:**
```cpp
/** @name Getters
 *  Functions for retrieving values
 */
///@{
int getValue();
string getName();
///@}

/** @name Setters
 *  Functions for setting values
 */
///@{
void setValue(int v);
void setName(string n);
///@}
```

### Special Commands

**Lists:**
```cpp
/**
 * Shopping list:
 * - Item 1
 * - Item 2
 * - Item 3
 */
```

**Parameters with Direction:**
```cpp
/**
 * @param[in] input Input parameter (read-only)
 * @param[out] output Output parameter (modified)
 * @param[in,out] data Input and output
 */
```

**Code Formatting:**
```cpp
/**
 * Use @c variable for inline code
 * or @p parameter for parameter names
 * 
 * Example:
 * @code
 * int x = 5;
 * cout << x;
 * @endcode
 */
```

### Namespaces

```cpp
/**
 * @namespace Math
 * @brief Mathematical operations namespace
 * 
 * Contains utility functions for
 * mathematical calculations
 */
namespace Math {
    /**
     * @brief Calculate factorial
     * @param n Input number
     * @return Factorial of n
     */
    int factorial(int n);
}
```

### Enumerations

```cpp
/**
 * @enum Color
 * @brief Represents color values
 */
enum Color {
    RED,    ///< Red color
    GREEN,  ///< Green color
    BLUE    ///< Blue color
};
```

### Structures

```cpp
/**
 * @struct Point
 * @brief Represents 2D point
 */
struct Point {
    int x;  ///< X coordinate
    int y;  ///< Y coordinate
};
```

## Markdown Support

Doxygen supports Markdown in comments:

```cpp
/**
 * # Main Heading
 * 
 * ## Sub Heading
 * 
 * **Bold text** and *italic text*
 * 
 * - Bullet list
 * - Another item
 * 
 * 1. Numbered list
 * 2. Second item
 */
```

## Graphs and Diagrams

With Graphviz (dot) installed:

**Enable in Doxyfile:**
```
HAVE_DOT = YES
CLASS_DIAGRAMS = YES
CALL_GRAPH = YES
CALLER_GRAPH = YES
COLLABORATION_GRAPH = YES
```

**Generates:**
- Class inheritance diagrams
- Collaboration diagrams
- Include dependency graphs
- Call graphs

## Special Pages

**Main Page:**
```cpp
/**
 * @mainpage Project Documentation
 * 
 * @section intro Introduction
 * This is the introduction
 * 
 * @section usage Usage
 * How to use the library
 */
```

**Custom Pages:**
```cpp
/**
 * @page installation Installation Guide
 * 
 * ## Requirements
 * - Compiler
 * - Libraries
 * 
 * ## Steps
 * 1. Download
 * 2. Compile
 * 3. Install
 */
```

## Best Practices

1. **Consistent Style**: Use same comment style throughout
2. **Brief First**: Start with concise @brief description
3. **Document Public API**: All public members should be documented
4. **Parameter Order**: Document params in same order as code
5. **Return Values**: Always document return values
6. **Examples**: Include usage examples for complex functions
7. **Cross-References**: Use @see to link related functions
8. **Update Regularly**: Keep docs synchronized with code

## Common Doxygen Commands Summary

| Command | Purpose |
|---------|---------|
| @brief | Short description |
| @param | Parameter description |
| @return | Return value |
| @see | Cross-reference |
| @note | Important note |
| @warning | Warning message |
| @code @endcode | Code example |
| @file | File description |
| @class | Class description |
| @author | Author name |
| @date | Date |
| @version | Version number |

## Important Notes

1. **Comment Placement**: Before or after declaration
2. **Triple Slash**: `///` for single-line comments
3. **Double Star**: `/**` for multi-line comments
4. **Extraction**: Use EXTRACT_ALL = YES for all members
5. **Recursive**: Enable RECURSIVE for subdirectories
6. **Output Format**: Can generate HTML, LaTeX, RTF, XML

## Key Takeaways

- Doxygen generates documentation from code
- Special comment syntax triggers documentation
- Supports multiple programming languages
- Automatic class and call graph generation
- HTML and PDF output formats
- Cross-referenced and searchable documentation
- Minimal overhead for developers
- Integration with version control

## Compilation

```bash
# Generate config file
doxygen -g

# Generate documentation
doxygen Doxyfile

# View HTML output
# Open html/index.html in browser

# Generate PDF from LaTeX
cd latex
make pdf
```

## Files

- `Doxyfile` - Configuration file
- `src/` - Source code directory (would contain files to document)
- `html/` - Generated HTML documentation
- `latex/` - Generated LaTeX documentation
