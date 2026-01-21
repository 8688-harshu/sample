Preprocessor directives in C, such as #define, #if, and #ifdef, operate on text and integer constant expressions rather than directly on variable data types. The preprocessor treats all data as raw text or tokens. 
However, when creating constants or evaluating conditions, the preprocessor supports the following types of values:
1. Integer Constant Expressions (for #if, #elif) 
In conditional directives, the expression must evaluate to a constant integer value. 
Integer Literals: 10, 0x1F, 077
Character Constants: 'a', '\n'
Boolean Results: defined(MACRO) or boolean operators like && (AND), || (OR), and ! (NOT).
Arithmetic Results: +, -, *, /, %. 
2. Basic Text/Token Types (for #define)
When using #define to create macros, the preprocessor treats the replacement text as a string of tokens. Supported text types include: 
Numeric Literals: 10, 3.14159f, 2.998e+8.
String Literals: "hello", "SYSTEM_PATH".
Identifiers/Tokens: Variable names, function names, or keywords (e.g., #define MAX_SIZE 100).
Multi-line Codes: Using the line continuation operator \. 
3. User-Defined Type Aliases (via #define) 
Although the preprocessor doesn't understand types, it can replace a text token with a type name: 
#define DWORD unsigned long
#define PI_PTR float* 
4. Data Type Limitations
No Runtime Type Awareness: The preprocessor does not know about variable types (e.g., int, float, char) at compile time.
No Function Type Safety: Parameterized macros like #define SQUARE(x) (x*x) do not check if x is an integer or float. 
5. Type-Related Directives
#pragma pack(n): Used to specify structure alignment in bytes, which implicitly uses integer values. 
Note: For type-safe operations in modern C (C11 and later), _Generic is preferred over preprocessor macros to handle different data types. 
