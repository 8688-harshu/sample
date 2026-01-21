| Type                          | Typical Size                         | Range (Signed)                                 | Range (Unsigned)              |
| ----------------------------- | ------------------------------------ | ---------------------------------------------- | ----------------------------- |
| `char`                        | 1 byte (8 bits)                      | -2⁷ … 2⁷-1 → -128 … 127                        | 0 … 2⁸-1 → 0 … 255            |
| `unsigned char`               | 1 byte                               | N/A                                            | 0 … 255                       |
| `signed char`                 | 1 byte                               | -128 … 127                                     | N/A                           |
| `short` / `short int`         | 2 bytes (16 bits)                    | -2¹⁵ … 2¹⁵-1 → -32,768 … 32,767                | 0 … 2¹⁶-1 → 0 … 65,535        |
| `unsigned short`              | 2 bytes                              | N/A                                            | 0 … 65,535                    |
| `int` / `signed int`          | 4 bytes (32 bits)                    | -2³¹ … 2³¹-1 → -2,147,483,648 … 2,147,483,647  | 0 … 2³²-1 → 0 … 4,294,967,295 |
| `unsigned int`                | 4 bytes                              | N/A                                            | 0 … 4,294,967,295             |
| `long` / `long int`           | 4 bytes (32-bit) or 8 bytes (64-bit) | -2³¹ … 2³¹-1 (32-bit) or -2⁶³ … 2⁶³-1 (64-bit) | 0 … 2³²-1 or 0 … 2⁶⁴-1        |
| `unsigned long`               | 4 bytes (32-bit) or 8 bytes (64-bit) | N/A                                            | 0 … 2³²-1 or 0 … 2⁶⁴-1        |
| `long long` / `long long int` | 8 bytes (64-bit)                     | -2⁶³ … 2⁶³-1                                   | 0 … 2⁶⁴-1                     |
| `unsigned long long`          | 8 bytes                              | N/A                                            | 0 … 2⁶⁴-1                     |



| C Type                           | `printf` Specifier             | `scanf` Specifier | Notes                                              |
| -------------------------------- | ------------------------------ | ----------------- | -------------------------------------------------- |
| `int` / `signed int`             | `%d`                           | `%d`              | Standard signed int                                |
| `unsigned int`                   | `%u`                           | `%u`              | Unsigned int                                       |
| `short` / `signed short`         | `%hd`                          | `%hd`             | 16-bit signed                                      |
| `unsigned short`                 | `%hu`                          | `%hu`             | 16-bit unsigned                                    |
| `long` / `signed long`           | `%ld`                          | `%ld`             | Usually 32-bit (Linux/Windows)                     |
| `unsigned long`                  | `%lu`                          | `%lu`             | Unsigned long                                      |
| `long long` / `signed long long` | `%lld`                         | `%lld`            | 64-bit                                             |
| `unsigned long long`             | `%llu`                         | `%llu`            | 64-bit unsigned                                    |
| `char` / `signed char`           | `%c` (char) / `%hhd` (numeric) | `%c` / `%hhd`     | `%c` prints character, `%hhd` prints numeric value |
| `unsigned char`                  | `%hhu`                         | `%hhu`            | Numeric only                                       |






| C Type        | `printf` Specifier | `scanf` Specifier | Notes              |
| ------------- | ------------------ | ----------------- | ------------------ |
| `float`       | `%f`               | `%f`              | Single precision   |
| `double`      | `%lf`              | `%lf`             | Double precision   |
| `long double` | `%Lf`              | `%Lf`             | Extended precision |



| Type    | `printf` / `scanf` Specifier | Notes             |
| ------- | ---------------------------- | ----------------- |
| `_Bool` | `%d`                         | Prints 0 or 1     |
| `void`  | N/A                          | No value to print |
