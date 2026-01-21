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




Ah! Perfect 😎 Let’s make **type conversions in C** super simple, so you can **remember it for GATE** without confusion. I’ll break it into **automatic (implicit) and manual (explicit) conversions** with clear rules.

---

# **1. Automatic Type Conversion (Implicit / Type Promotion)**

C automatically converts a smaller type to a larger type **when needed**. This is also called **type promotion**.

### Rules:

1. **Integer promotions**

   * `char`, `short`, `signed char`, `unsigned char` → promoted to `int` if `int` can hold all values of the original type; otherwise `unsigned int`.
   * Example:

```c
char a = 100;
int b = a; // char promoted to int automatically
```

2. **Usual arithmetic conversions**

   * In expressions, **smaller types are converted to larger types** before calculation.
   * Order (lowest → highest):

```
char, short → int → long → long long → float → double → long double
```

* Example:

```c
int a = 5;
float b = 2.5;
float c = a + b;  // int promoted to float automatically
```

3. **Signed/Unsigned Rules**

* If you mix **signed and unsigned of the same size**, signed is converted to unsigned.
* Example:

```c
int a = -1;
unsigned int b = 1;
printf("%u", a + b); // a converted to unsigned → very large number
```

---

# **2. Explicit Type Conversion (Casting)**

* When C **does NOT convert automatically**, you can force it with a **cast**.
* Syntax:

```c
(type) expression
```

* Example:

```c
double x = 5.7;
int y = (int)x;  // 5, fractional part discarded
```

* Common uses:

  1. `float` → `int` (fraction lost)
  2. `double` → `float` (precision may reduce)
  3. `long` → `int` (may overflow)
  4. Mixed arithmetic where you want **specific type**

---

# **3. Easy-to-Remember Summary Table**

| Conversion Type           | Automatic?             | Example                          | Notes                           |
| ------------------------- | ---------------------- | -------------------------------- | ------------------------------- |
| `char` → `int`            | Yes                    | `char c; int x = c;`             | Small integer promotion         |
| `short` → `int`           | Yes                    | `short s; int x = s;`            | Same as above                   |
| `int` → `float`           | Yes                    | `int a; float b = a;`            | Precision may increase          |
| `float` → `double`        | Yes                    | `float f; double d = f;`         | Standard promotion              |
| `int` ↔ `unsigned int`    | Usually Yes (careful!) | `int a=-1; unsigned int b; a+b`  | Can cause surprises             |
| `int` → `char`            | No                     | `int a = 300; char c = (char)a;` | Must cast, may overflow         |
| `double` → `int`          | No                     | `int x = (int)3.9;`              | Fraction lost                   |
| Any type → long/long long | Yes                    | `int a; long b = a;`             | Safe                            |
| Any type → pointer        | No                     | Must cast                        | Only allowed with explicit cast |

---

# **4. Rules You Can Memorize Easily**

1. **Small → large automatically**

   * `char → short → int → long → long long → float → double → long double`
2. **Unsigned may “surprise” you** if mixed with signed
3. **Large → small** or **float → int** → **needs explicit cast**

✅ Easy memory trick:

* **“Upwards, it’s automatic. Downwards, you need a cast.”**
* “Upwards” = smaller → bigger in size or precision
* “Downwards” = bigger → smaller → risk of data loss

---

If you want, I can also make a **diagram showing all types in a ladder with arrows for automatic conversions** — it’s **super easy to visualize for GATE**.

Do you want me to make that ladder diagram?

