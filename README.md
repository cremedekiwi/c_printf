# ft_printf

A custom implementation of the printf function in C.

## Overview

ft_printf is a recreation of the standard C library printf function. It handles various format specifiers and returns the number of characters printed, just like the original printf.

## Features

This implementation supports the following format specifiers:

- `%c` - Single character
- `%s` - String
- `%p` - Pointer address (hexadecimal format with "0x" prefix)
- `%d` - Signed decimal integer
- `%i` - Signed decimal integer
- `%u` - Unsigned decimal integer
- `%x` - Hexadecimal (lowercase)
- `%X` - Hexadecimal (uppercase)
- `%%` - Literal percent sign

## Project Structure

```
ft_printf/
├── Makefile
├── includes/
│   └── ft_printf.h
└── src/
    ├── ft_printf.c
    ├── ft_print_char.c
    ├── ft_print_str.c
    ├── ft_print_int.c
    ├── ft_print_int_unsigned.c
    ├── ft_print_ptr.c
    └── ft_print_hex.c
```

## Compilation

The project includes a Makefile with the following rules:

```bash
make        # Compile the library
make clean  # Remove object files
make fclean # Remove object files and library
make re     # Recompile everything
```

This will create `libftprintf.a` static library.

## Usage

### Include the header
```c
#include "ft_printf.h"
```

### Link the library
```bash
gcc your_program.c -L. -lftprintf
```

### Example usage
```c
#include "ft_printf.h"

int main(void)
{
    ft_printf("Hello, %s!\n", "world");
    ft_printf("Number: %d\n", 42);
    ft_printf("Hex: %x\n", 255);
    
    int *ptr = &some_variable;
    ft_printf("Pointer: %p\n", ptr);
    
    return (0);
}
```

## Function Prototypes

```c
int ft_printf(const char *format, ...);
int ft_print_char(char c);
int ft_print_str(char *s);
int ft_print_ptr(void *ptr);
int ft_print_int(int n);
int ft_print_int_unsigned(unsigned int n);
int ft_print_hex(unsigned int n, int uppercase);
```

## Implementation Details

### Error Handling
- Returns -1 if the format string is NULL
- Returns -1 if format string ends with '%' or has '% ' (percent followed by space)
- Handles NULL string pointers by printing "(null)"
- Handles NULL pointers by printing "(nil)"

### Special Cases
- **INT_MIN**: Properly handles the edge case of -2147483648
- **Null pointers**: Displays "(nil)" for null pointer addresses
- **Null strings**: Displays "(null)" for null string pointers

### Memory Management
- Uses stack-allocated buffers for number conversion
- No dynamic memory allocation (malloc/free)
- All functions return the number of characters printed

## Technical Specifications

- **Compiler**: gcc with `-Wall -Wextra -Werror` flags
- **Standard**: C99 compliant
- **Dependencies**: Only uses `write()`, `stdarg.h`, and `unistd.h`
- **No forbidden functions**: Does not use printf, sprintf, or other printf family functions

## Testing

The main function (commented out in ft_printf.c) includes basic tests comparing output with the standard printf function. To test:

1. Uncomment the main function in `src/ft_printf.c`
2. Compile and run: `gcc src/ft_printf.c src/*.c -I includes && ./a.out`
