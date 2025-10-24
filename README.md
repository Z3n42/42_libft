<div align="center">

# 📚 Libft

### Your very first own library

<p>
  <img src="https://img.shields.io/badge/Score-114%2F100-success?style=for-the-badge&logo=42" alt="42 Score"/>
  <img src="https://img.shields.io/badge/Language-C-00599C?style=for-the-badge&logo=c&logoColor=white" alt="Language"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License"/>
  <img src="https://img.shields.io/badge/42-Urduliz-000000?style=for-the-badge&logo=42&logoColor=white" alt="42 Urduliz"/>
</p>

*A complete reimplementation of essential C standard library functions, plus additional utilities and bonus linked list functions.*

[Installation](#%EF%B8%8F-installation) • [Usage](#-usage) • [Function Reference](#-function-reference) • [Testing](#-testing)

</div>

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Installation](#%EF%B8%8F-installation)
- [Usage](#-usage)
- [Function Reference](#-function-reference)
  - [Part 1: Libc Functions](#part-1-libc-functions)
  - [Part 2: Additional Functions](#part-2-additional-functions)
  - [Bonus: Linked List Functions](#bonus-linked-list-functions)
- [Project Structure](#-project-structure)
- [Testing](#-testing)
- [What I Learned](#-what-i-learned)
- [License](#-license)

---

## 🎯 About the Project

**Libft** is the first project in the 42 cursus, where we recreate a subset of the C standard library functions from scratch. This library serves as a foundation for all future C projects at 42, providing a deeper understanding of how these fundamental functions work under the hood.

### Why Libft?

C programming without access to standard library functions can be challenging. This project teaches:
- **Memory management** and pointer manipulation
- **String and character handling** operations
- **Linked list** data structures and algorithms
- **Low-level programming** concepts
- **Code organization** and library creation with Makefiles

The completed library becomes a personal toolkit that can be expanded and reused throughout the 42 curriculum.

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 🔧 Standard Library Functions
- String manipulation (`strlen`, `strcpy`, `strdup`, etc.)
- Memory operations (`memset`, `memcpy`, `memmove`, etc.)
- Character checks (`isalpha`, `isdigit`, `isascii`, etc.)
- Type conversions (`atoi`)

</td>
<td width="50%">

### 🚀 Additional Utilities
- String operations (`substr`, `strjoin`, `strtrim`, `split`)
- File descriptor output functions
- Memory allocation with `calloc`
- Function mapping (`strmapi`)

</td>
</tr>
<tr>
<td width="50%">

### 🔗 Bonus: Linked Lists
- Node creation and deletion
- List traversal and manipulation
- Iteration and mapping functions
- Dynamic list management

</td>
<td width="50%">

### 📦 Compiled Library
- Static library `libft.a`
- Makefile with standard rules
- Clean compilation (no relink)
- Header file with all prototypes

</td>
</tr>
</table>

---

## 🛠️ Installation

### Prerequisites

- **GCC** or **Clang** compiler
- **Make**
- Unix-based system (Linux, macOS)

### Clone and Compile

```bash
# Clone the repository
git clone https://github.com/Z3n42/42_libft.git
cd 42_libft

# Compile the library (mandatory part)
make

# Compile with bonus functions
make bonus

# Clean object files
make clean

# Clean everything (including libft.a)
make fclean

# Recompile from scratch
make re
```

After running `make`, you'll have a `libft.a` static library ready to use.

---

## 🚀 Usage

### Including in Your Project

1. **Copy libft to your project directory:**
```bash
cp libft.a libft.h your_project/
```

2. **Include the header in your C files:**
```c
#include "libft.h"
```

3. **Compile your project with libft:**
```bash
gcc -Wall -Wextra -Werror your_file.c -L. -lft -o your_program
```

### Example Program

```c
#include "libft.h"

int main(void)
{
    char    *str;
    char    **split;
    int     i;

    // Using ft_strdup and ft_split
    str = ft_strdup("Hello from libft!");
    split = ft_split(str, ' ');

    i = 0;
    while (split[i])
    {
        ft_putendl_fd(split[i], 1);
        free(split[i]);
        i++;
    }
    free(split);
    free(str);

    return (0);
}
```

**Compile and run:**
```bash
gcc -Wall -Wextra -Werror example.c -L. -lft -o example
./example
```

---

## 📖 Function Reference

### Part 1: Libc Functions

Functions that replicate standard C library behavior (34 functions):

<details>
<summary><b>Character Classification & Conversion (7 functions)</b></summary>

| Function | Description | Prototype |
|----------|-------------|-----------|
| `ft_isalpha` | Checks if character is alphabetic | `int ft_isalpha(int c)` |
| `ft_isdigit` | Checks if character is a digit | `int ft_isdigit(int c)` |
| `ft_isalnum` | Checks if character is alphanumeric | `int ft_isalnum(int c)` |
| `ft_isascii` | Checks if character is ASCII (0-127) | `int ft_isascii(int c)` |
| `ft_isprint` | Checks if character is printable | `int ft_isprint(int c)` |
| `ft_toupper` | Converts character to uppercase | `int ft_toupper(int c)` |
| `ft_tolower` | Converts character to lowercase | `int ft_tolower(int c)` |

</details>

<details>
<summary><b>String Functions (11 functions)</b></summary>

| Function | Description | Prototype |
|----------|-------------|-----------|
| `ft_strlen` | Calculates string length | `size_t ft_strlen(const char *s)` |
| `ft_strlcpy` | Size-bounded string copy | `size_t ft_strlcpy(char *dst, const char *src, size_t size)` |
| `ft_strlcat` | Size-bounded string concatenation | `size_t ft_strlcat(char *dst, const char *src, size_t size)` |
| `ft_strchr` | Locates first occurrence of character | `char *ft_strchr(const char *s, int c)` |
| `ft_strrchr` | Locates last occurrence of character | `char *ft_strrchr(const char *s, int c)` |
| `ft_strncmp` | Compares strings up to n bytes | `int ft_strncmp(const char *s1, const char *s2, size_t n)` |
| `ft_strnstr` | Locates substring in string | `char *ft_strnstr(const char *big, const char *little, size_t len)` |
| `ft_strdup` | Duplicates a string | `char *ft_strdup(const char *s)` |
| `ft_atoi` | Converts string to integer | `int ft_atoi(const char *nptr)` |

</details>

<details>
<summary><b>Memory Functions (8 functions)</b></summary>

| Function | Description | Prototype |
|----------|-------------|-----------|
| `ft_memset` | Fills memory with a constant byte | `void *ft_memset(void *s, int c, size_t n)` |
| `ft_bzero` | Zeroes a byte string | `void ft_bzero(void *s, size_t n)` |
| `ft_memcpy` | Copies memory area | `void *ft_memcpy(void *dest, const void *src, size_t n)` |
| `ft_memccpy` | Copies memory until character found | `void *ft_memccpy(void *dest, const void *src, int c, size_t n)` |
| `ft_memmove` | Copies memory area (handles overlap) | `void *ft_memmove(void *dest, const void *src, size_t n)` |
| `ft_memchr` | Scans memory for a character | `void *ft_memchr(const void *s, int c, size_t n)` |
| `ft_memcmp` | Compares memory areas | `int ft_memcmp(const void *s1, const void *s2, size_t n)` |
| `ft_calloc` | Allocates and zeroes memory | `void *ft_calloc(size_t nmemb, size_t size)` |

</details>

### Part 2: Additional Functions

Custom functions not present in the standard library (11 functions):

<details>
<summary><b>String Utilities & Conversions (7 functions)</b></summary>

| Function | Description | Prototype |
|----------|-------------|-----------|
| `ft_substr` | Extracts substring from string | `char *ft_substr(char const *s, unsigned int start, size_t len)` |
| `ft_strjoin` | Concatenates two strings into new string | `char *ft_strjoin(char const *s1, char const *s2)` |
| `ft_strtrim` | Trims characters from string edges | `char *ft_strtrim(char const *s1, char const *set)` |
| `ft_split` | Splits string by delimiter into array | `char **ft_split(char const *s, char c)` |
| `ft_itoa` | Converts integer to string | `char *ft_itoa(int n)` |
| `ft_strmapi` | Applies function to each character (indexed) | `char *ft_strmapi(char const *s, char (*f)(unsigned int, char))` |
| `ft_striteri` | Applies function to each character (in-place) | `void ft_striteri(char *s, void (*f)(unsigned int, char*))` |

</details>

<details>
<summary><b>File Descriptor Output Functions (4 functions)</b></summary>

| Function | Description | Prototype |
|----------|-------------|-----------|
| `ft_putchar_fd` | Outputs character to file descriptor | `void ft_putchar_fd(char c, int fd)` |
| `ft_putstr_fd` | Outputs string to file descriptor | `void ft_putstr_fd(char *s, int fd)` |
| `ft_putendl_fd` | Outputs string + newline to FD | `void ft_putendl_fd(char *s, int fd)` |
| `ft_putnbr_fd` | Outputs integer to file descriptor | `void ft_putnbr_fd(int n, int fd)` |

</details>

### Bonus: Linked List Functions

<details>
<summary><b>List Manipulation (9 functions)</b></summary>

**List structure defined in `libft.h`:**
```c
typedef struct s_list
{
    void            *content;
    struct s_list   *next;
}   t_list;
```

| Function | Description | Prototype |
|----------|-------------|-----------|
| `ft_lstnew` | Creates new list node | `t_list *ft_lstnew(void *content)` |
| `ft_lstadd_front` | Adds node at beginning of list | `void ft_lstadd_front(t_list **lst, t_list *new)` |
| `ft_lstsize` | Counts number of nodes | `int ft_lstsize(t_list *lst)` |
| `ft_lstlast` | Returns last node of list | `t_list *ft_lstlast(t_list *lst)` |
| `ft_lstadd_back` | Adds node at end of list | `void ft_lstadd_back(t_list **lst, t_list *new)` |
| `ft_lstdelone` | Deletes single node | `void ft_lstdelone(t_list *lst, void (*del)(void*))` |
| `ft_lstclear` | Deletes and frees entire list | `void ft_lstclear(t_list **lst, void (*del)(void*))` |
| `ft_lstiter` | Iterates list applying function | `void ft_lstiter(t_list *lst, void (*f)(void *))` |
| `ft_lstmap` | Creates new list from function mapping | `t_list *ft_lstmap(t_list *lst, void *(*f)(void *), void (*del)(void *))` |

</details>

---

## 📁 Project Structure

```
42_libft/
├── 📄 LICENSE                # MIT License
├── 📄 Makefile               # Build configuration
├── 📄 libft.h                # Header with prototypes and t_list struct
├── 📄 README.md              # This file
│
├── 📂 Mandatory Part (34 .c files)
│   ├── ft_isalpha.c         # Character checks
│   ├── ft_isdigit.c
│   ├── ft_isalnum.c
│   ├── ft_isascii.c
│   ├── ft_isprint.c
│   ├── ft_toupper.c
│   ├── ft_tolower.c
│   ├── ft_strlen.c          # String operations
│   ├── ft_strlcpy.c
│   ├── ft_strlcat.c
│   ├── ft_strchr.c
│   ├── ft_strrchr.c
│   ├── ft_strncmp.c
│   ├── ft_strnstr.c
│   ├── ft_strdup.c
│   ├── ft_atoi.c
│   ├── ft_memset.c          # Memory operations
│   ├── ft_bzero.c
│   ├── ft_memcpy.c
│   ├── ft_memccpy.c
│   ├── ft_memmove.c
│   ├── ft_memchr.c
│   ├── ft_memcmp.c
│   ├── ft_calloc.c
│   ├── ft_substr.c          # Additional utilities
│   ├── ft_strjoin.c
│   ├── ft_strtrim.c
│   ├── ft_split.c
│   ├── ft_itoa.c
│   ├── ft_strmapi.c
│   ├── ft_striteri.c
│   ├── ft_putchar_fd.c      # File descriptor output
│   ├── ft_putstr_fd.c
│   ├── ft_putendl_fd.c
│   └── ft_putnbr_fd.c
│
├── 📂 Bonus Part (9 .c files)
│   ├── ft_lstnew.c
│   ├── ft_lstadd_front.c
│   ├── ft_lstsize.c
│   ├── ft_lstlast.c
│   ├── ft_lstadd_back.c
│   ├── ft_lstdelone.c
│   ├── ft_lstclear.c
│   ├── ft_lstiter.c
│   └── ft_lstmap.c
│
├── 📂 Tests/                 # Testing utilities (not graded)
│   ├── 📂 Libtests/         # Custom test suite
│   │   ├── README.md
│   │   ├── grademe.sh       # Automated test runner
│   │   ├── deepthought      # Test checker
│   │   └── tests/           # Individual test files
│   └── 📂 libft-unit-test/  # External unit tests (alelievr)
│       ├── Makefile
│       ├── libft_test.c
│       └── tests/
│
└── 📂 libftmain/            # Individual test mains for each function
    ├── atoimain.c
    ├── bzero main.c
    ├── memchrmain.c
    ├── splitmain.c
    └── ...                  # 40+ test programs
```

### Makefile Details

The Makefile implements the following structure:

```makefile
NAME = libft.a
CC = gcc
CFLAGS = -Wall -Wextra -Werror
AR = ar rcs

# Mandatory functions (34 files)
FILES = ft_memset ft_bzero ft_memcpy ft_memccpy ft_memmove ft_memchr ft_memcmp \
        ft_strlen ft_strlcpy ft_strlcat ft_strchr ft_strrchr ft_strncmp ft_strnstr \
        ft_atoi ft_isalpha ft_isdigit ft_isalnum ft_isascii ft_isprint \
        ft_toupper ft_tolower ft_calloc ft_strdup ft_substr ft_strjoin ft_strtrim \
        ft_split ft_itoa ft_strmapi ft_striteri ft_putchar_fd ft_putstr_fd \
        ft_putendl_fd ft_putnbr_fd

# Bonus functions (9 files)
FILES_B = ft_lstnew ft_lstadd_front ft_lstsize ft_lstlast ft_lstadd_back \
          ft_lstdelone ft_lstclear ft_lstiter ft_lstmap

OBJS = $(FILES:=.o)
OBJS_B = $(FILES_B:=.o)
```

### Make Rules

| Rule | Action |
|------|--------|
| `make` / `make all` | Compiles 34 mandatory functions → `libft.a` |
| `make bonus` | Compiles 9 bonus functions and adds to `libft.a` |
| `make clean` | Removes all `.o` object files |
| `make fclean` | Removes `.o` files and `libft.a` |
| `make re` | Equivalent to `make fclean` + `make all` |

**Compilation flags:** `-Wall -Wextra -Werror` (all warnings as errors)  
**Archiver:** `ar rcs libft.a *.o` (creates static library)

---

## 🧪 Testing

### Included Test Suites

The repository includes **two comprehensive testing frameworks** in the `Tests/` directory:

#### 1. Libtests (Custom Test Suite)
```bash
cd Tests/Libtests
./grademe.sh
```

Features:
- Automated test runner with `grademe.sh`
- `deepthought` checker for validation
- Individual test files for each function
- README with usage instructions

#### 2. libft-unit-test (alelievr)
```bash
cd Tests/libft-unit-test
make
```

Features:
- Comprehensive unit tests
- Makefile integration
- Detailed error reporting

### Individual Function Tests

The `libftmain/` directory contains **40+ individual test programs** for manual testing:

```bash
# Example: Test ft_atoi
gcc -Wall -Wextra -Werror libftmain/atoimain.c ft_atoi.c -o test_atoi
./test_atoi

# Example: Test ft_split
gcc -Wall -Wextra -Werror libftmain/splitmain.c ft_split.c libft.a -o test_split
./test_split

# Example: Test ft_memchr
gcc -Wall -Wextra -Werror libftmain/memchrmain.c ft_memchr.c -o test_memchr
./test_memchr
```

### Recommended External Testers

- **[Francinette](https://github.com/xicodomingues/francinette)** - Comprehensive 42 tester
- **[libftTester](https://github.com/Tripouille/libftTester)** - Popular libft validator

```bash
# Using Francinette
bash -c "$(curl -fsSL https://raw.github.com/xicodomingues/francinette/master/bin/install.sh)"
cd ~/42_libft && francinette

# Using Tripouille's tester
git clone https://github.com/Tripouille/libftTester.git
cd libftTester && make
```

### Quick Manual Test

```c
// test_libft.c
#include "libft.h"
#include <stdio.h>

int main(void)
{
    // Test string functions
    printf("ft_strlen(\"Hello\"): %zu\n", ft_strlen("Hello"));

    // Test memory functions
    char str[20];
    ft_memset(str, 'A', 10);
    str[10] = '\0';
    printf("ft_memset result: %s\n", str);

    // Test split
    char **words = ft_split("one,two,three", ',');
    int i = 0;
    while (words[i])
    {
        printf("Word %d: %s\n", i, words[i]);
        free(words[i++]);
    }
    free(words);

    // Test linked list (bonus)
    t_list *node = ft_lstnew("Hello");
    printf("List node content: %s\n", (char *)node->content);
    free(node);

    return (0);
}
```

**Compile and run:**
```bash
make bonus  # Include bonus functions
gcc -Wall -Wextra -Werror test_libft.c -L. -lft -o test
./test
```

---

## 💡 What I Learned

Through this project, deep understanding was gained in:

- ✅ **Memory Management**: Dynamic allocation with `malloc`, proper freeing, leak prevention
- ✅ **Pointer Arithmetic**: Navigating memory addresses and dereferencing
- ✅ **String Manipulation**: Buffer handling, null termination, edge cases
- ✅ **Data Structures**: Implementing and manipulating singly linked lists
- ✅ **Makefile Creation**: Automated compilation, static library generation with `ar`
- ✅ **Function Pointers**: Used in `ft_lstmap`, `ft_lstiter`, `ft_strmapi`, `ft_striteri`
- ✅ **Edge Case Handling**: NULL pointers, empty strings, integer overflow (INT_MIN)
- ✅ **The Norm**: Writing clean, standardized code following 42's strict coding style
- ✅ **Testing Strategies**: Creating comprehensive test mains for each function

### Key Implementation Challenges

1. **`ft_split`**: Managing dynamic 2D arrays with proper memory allocation and error handling
2. **`ft_memmove`**: Handling overlapping memory regions correctly (forward vs backward copy)
3. **`ft_strlcpy` / `ft_strlcat`**: Understanding BSD-style size-bounded functions
4. **`ft_lstmap`**: Implementing list mapping with error handling and cleanup using `del` function
5. **`ft_itoa`**: Converting negative numbers (including INT_MIN: -2147483648)
6. **`ft_memccpy`**: Copying until character found, returning correct pointer

### Bonus Functions - Linked Lists

The bonus introduces **singly linked lists** with 9 manipulation functions:

**Key concepts learned:**
- Dynamic node creation with `malloc`
- Pointer-to-pointer manipulation (`t_list **`)
- Function pointers for generic operations (`void (*f)(void *)`)
- Memory cleanup with custom deleter functions
- List traversal and transformation

**Example: Creating a list**
```c
t_list *head = ft_lstnew("First");
ft_lstadd_back(&head, ft_lstnew("Second"));
ft_lstadd_back(&head, ft_lstnew("Third"));

printf("List size: %d\n", ft_lstsize(head));  // Output: 3

// Clean up
ft_lstclear(&head, free);
```

---

## 📏 Norm Compliance

This project strictly follows the **42 Norm** (Norminette v3):
- ✅ Maximum 25 lines per function
- ✅ Maximum 5 functions per file
- ✅ No forbidden functions (only `write`, `malloc`, `free`)
- ✅ Proper variable declarations at function start
- ✅ No memory leaks (tested with valgrind)
- ✅ No segmentation faults or undefined behavior

---

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details.

This project is part of the 42 School curriculum. Feel free to use and learn from this code, but please don't copy it for your own 42 projects. Understanding comes from doing it yourself! 🚀

---

## 🔗 Related Projects

This library is used extensively in other 42 projects:

- **[get_next_line](https://github.com/Z3n42/get_next_line)** - Line reading (doesn't use libft as per subject)
- **[ft_printf](https://github.com/Z3n42/ft_printf)** - Formatted output (can integrate libft)
- **[fdf](https://github.com/Z3n42/fdf)** - 3D wireframe (uses libft for utilities)
- **pipex** - Unix pipes
- **push_swap** - Sorting algorithm
- **minishell** - Shell implementation

---

<div align="center">

**Made with ☕ by [Z3n42](https://github.com/Z3n42)**

*42 Urduliz | Circle 0*

[![42 Profile](https://img.shields.io/badge/42_Intra-ingonzal-000000?style=flat&logo=42&logoColor=white)](https://profile.intra.42.fr/users/ingonzal)

</div>
