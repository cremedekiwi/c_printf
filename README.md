# libftprintf

ft_printf: A Custom printf Implementation

Welcome to the libftprintf project! This repository contains an implementation of the ft_printf function, a custom version of the standard printf function in C. This project is designed to mimic the behavior of the standard printf, adhering to the 42 School guidelines.

## Overview
The ft_printf function is a variadic function that formats and prints data to the standard output. It supports a subset of the functionality of the standard printf function, focusing on core features necessary for practical use. This project is an excellent exercise in mastering variable argument functions, string manipulation, and memory management.

## Features

    Custom implementation of ft_printf without using the standard library's printf.
    Handles common format specifiers such as integers, strings, characters, and more.
    Supports custom behaviors like precision and width formatting.
    Flexible and efficient implementation.

## Usage
Function Prototype

int ft_printf(const char *format, ...);

Example

#include "ft_printf.h"

int main(void)
{
    ft_printf("Hello, %s! You have %d new messages.\n", "Alice", 5);
    return 0;
}

## Supported Format Specifiers
| Specifier	| Description |
| --- | --- |
| %c	| Prints a single character |
| %s	| Prints a string |
| %d/%i	| Prints a signed decimal integer |
| %u	| Prints an unsigned decimal integer |
| %x	| Prints a number in lowercase hexadecimal |
| %X	| Prints a number in uppercase hexadecimal |
| %p	| Prints a pointer address |
| %%	| Prints a literal % character |

## Error Handling
    The function returns the total number of characters printed.
    If an error occurs (e.g., invalid format specifier), the behavior mimics standard printf to the extent possible.

## Installation
### Clone the repository:
```
git clone https://github.com/cremedekiwi/libftprintf.git libftprintf
```
### Compile the library using make:
```
cd libftprintf
make
```
### Link the library in your project:
```
gcc -L. -lftprintf your_program.c
```
