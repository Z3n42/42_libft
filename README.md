<div align="center">

# 📚 Libft

### Your very first own library

<p>
  <img src="https://img.shields.io/badge/Score-125%2F100-success?style=for-the-badge&logo=42" alt="42 Score"/>
  <img src="https://img.shields.io/badge/Language-C-00599C?style=for-the-badge&logo=c&logoColor=white" alt="Language"/>
  <img src="https://img.shields.io/github/license/Z3n42/42_libft?style=for-the-badge" alt="License"/>
  <img src="https://img.shields.io/badge/42-Urduliz-000000?style=for-the-badge&logo=42&logoColor=white" alt="42 Urduliz"/>
</p>

*A complete reimplementation of essential C standard library functions, plus additional utilities for future 42 projects.*

[Features](#-features) • [Installation](#-installation) • [Usage](#-usage) • [Functions](#-functions) • [Testing](#-testing)

</div>

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Installation](#-installation)
- [Usage](#-usage)
- [Function Reference](#-function-reference)
  - [Part 1: Libc Functions](#part-1-libc-functions)
  - [Part 2: Additional Functions](#part-2-additional-functions)
  - [Bonus: Linked List Functions](#bonus-linked-list-functions)
- [Project Structure](#-project-structure)
- [Testing](#-testing)
- [What I Learned](#-what-i-learned)
- [Norm Compliance](#-norm-compliance)
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
- **Code organization** and library creation

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
- Type conversions (`atoi`, `itoa`)

</td>
<td width="50%">

### 🚀 Additional Utilities
- String operations (`substr`, `strjoin`, `strtrim`, `split`)
- File descriptor output functions
- Memory allocation with `calloc`
- Function mapping and iteration

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
cp -r libft/ your_project/
```

2. **Include the header in your C files:**
```c
#include "libft.h"
```

3. **Compile your project with libft:**
```bash
gcc -Wall -Wextra -Werror your_file.c -L./libft -lft -o your_program
```

### Example Program

```c
#include "libft.h"
#include <stdio.h>

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
gcc example.c -L. -lft -o example
./example
```

---

## 📖 Function Reference

### Part 1: Libc Functions

Functions that replicate standard C library behavior:

<details>
<summary><b>Character Classification (7 functions)</b></summary>

| Function | Description | Prototype |
|----------|-------------|-----------|
| `ft_isalpha` | Checks if character is alphabetic | `int ft_isalpha(int c)` |
| `ft_isdigit` | Checks if character is a digit | `int ft_isdigit(int c)` |
| `ft_isalnum` | Checks if character is alphanumeric | `int ft_isalnum(int c)` |
| `ft_isascii` | Checks if character is ASCII | `int ft_isascii(int c)` |
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
<summary><b>Memory Functions (9 functions)</b></summary>

| Function | Description | Prototype |
|----------|-------------|-----------|
| `ft_memset` | Fills memory with a constant byte | `void *ft_memset(void *s, int c, size_t n)` |
| `ft_bzero` | Zeroes a byte string | `void ft_bzero(void *s, size_t n)` |
| `ft_memcpy` | Copies memory area | `void *ft_memcpy(void *dest, const void *src, size_t n)` |
| `ft_memmove` | Copies memory area (handles overlap) | `void *ft_memmove(void *dest, const void *src, size_t n)` |
| `ft_memchr` | Scans memory for a character | `void *ft_memchr(const void *s, int c, size_t n)` |
| `ft_memcmp` | Compares memory areas | `int ft_memcmp(const void *s1, const void *s2, size_t n)` |
| `ft_calloc` | Allocates and zeroes memory | `void *ft_calloc(size_t nmemb, size_t size)` |

</details>

### Part 2: Additional Functions

Custom functions not present in the standard library:

<details>
<summary><b>String Utilities (9 functions)</b></summary>

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
<summary><b>Output Functions (4 functions)</b></summary>

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

**List structure:**
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
├── 📄 Makefile              # Compilation rules
├── 📄 libft.h               # Header file with function prototypes
├── 📂 src/                  # Source files (if organized)
│   ├── ft_isalpha.c
│   ├── ft_strlen.c
│   ├── ft_memcpy.c
│   └── ...
├── 📂 bonus/                # Bonus linked list functions
│   ├── ft_lstnew_bonus.c
│   ├── ft_lstadd_front_bonus.c
│   └── ...
└── 📄 README.md             # This file
```

### Makefile Rules

| Rule | Description |
|------|-------------|
| `make` or `make all` | Compiles mandatory functions into `libft.a` |
| `make bonus` | Compiles mandatory + bonus functions |
| `make clean` | Removes object files (`.o`) |
| `make fclean` | Removes object files and `libft.a` |
| `make re` | Cleans and recompiles everything |

---

## 🧪 Testing

### Recommended Testers

I tested my libft thoroughly with several popular testers from the 42 community:

- **[libft-unit-test](https://github.com/alelievr/libft-unit-test)** by alelievr
- **[libftTester](https://github.com/Tripouille/libftTester)** by Tripouille
- **[Francinette](https://github.com/xicodomingues/francinette)** (comprehensive tester)

### Running Tests

```bash
# Clone a tester (example: Tripouille)
git clone https://github.com/Tripouille/libftTester.git
cd libftTester

# Run tests
make
```

### Manual Testing Example

```c
// test.c
#include "libft.h"
#include <stdio.h>

int main(void)
{
    // Test ft_strlen
    printf("ft_strlen(\"Hello\"): %zu\n", ft_strlen("Hello"));

    // Test ft_strjoin
    char *joined = ft_strjoin("Hello", " World");
    printf("ft_strjoin: %s\n", joined);
    free(joined);

    // Test ft_split
    char **words = ft_split("one,two,three", ',');
    int i = 0;
    while (words[i])
    {
        printf("Word %d: %s\n", i, words[i]);
        free(words[i++]);
    }
    free(words);

    return (0);
}
```

---

## 💡 What I Learned

Through this project, I gained deep understanding of:

- ✅ **Memory Management**: Dynamic allocation with `malloc`, proper freeing, leak prevention
- ✅ **Pointer Arithmetic**: Navigating memory addresses and dereferencing
- ✅ **String Manipulation**: Buffer handling, null termination, edge cases
- ✅ **Data Structures**: Implementing and manipulating linked lists
- ✅ **Code Organization**: Creating reusable libraries with proper headers
- ✅ **Makefile Creation**: Automated compilation with dependency management
- ✅ **Edge Case Handling**: NULL pointers, empty strings, integer overflow
- ✅ **The Norm**: Writing clean, standardized code following 42's coding style

### Key Challenges

1. **Understanding `strlcpy` and `strlcat`**: These BSD functions have unique size-bounded behavior
2. **Handling Overlapping Memory**: `ft_memmove` required careful implementation
3. **Split Function**: Managing dynamic 2D arrays and proper memory allocation
4. **Linked List Mapping**: Understanding function pointers and memory cleanup in `ft_lstmap`

---

## 📏 Norm Compliance

This project strictly follows the **42 Norm** (Norminette v3):
- ✅ Maximum 25 lines per function
- ✅ Maximum 5 functions per file
- ✅ No forbidden functions used
- ✅ Proper variable declarations
- ✅ No memory leaks
- ✅ No segmentation faults or unexpected behavior

---

## 📄 License

This project is part of the 42 School curriculum. Feel free to use and learn from this code, but please don't copy it for your own 42 projects. Understanding comes from doing it yourself! 🚀

---

## 🔗 Related Projects

This library is used extensively in my other 42 projects:

- [get_next_line](https://github.com/Z3n42/get_next_line) - Reading from file descriptors
- [ft_printf](https://github.com/Z3n42/ft_printf) - Recreating printf
- [pipex](https://github.com/Z3n42/pipex) - Unix pipes implementation

---

<div align="center">

**Made with ☕ by [Z3n42](https://github.com/Z3n42)**

*42 Urduliz | Circle 0*

[![42 Profile](https://img.shields.io/badge/42_Intra-ingonzal-000000?style=flat&logo=42&logoColor=white)](https://profile.intra.42.fr/users/ingonzal)

</div>
