# get_next_line

> a core 42 school project that involves creating a function to read a file descriptor line by line, handling buffers and dynamic memory management in c.

## 🧠 project goals

- implement a function that reads one line at a time from a file descriptor
- handle reading with a fixed-size buffer and dynamic memory allocation
- correctly return lines including newline characters until EOF
- support multiple file descriptors simultaneously (bonus)
- follow 42 school constraints and allowed functions (`read`, `malloc`, `free`)

## ⚙️ technologies

- c programming language
- linux system calls (`read`, `open`, `close`)
- dynamic memory management (`malloc`, `free`)
- buffer handling techniques

## 🗂️ project content

- `get_next_line.c`: main function implementation
- `get_next_line_utils.c`: helper functions (e.g., string manipulation)
- `get_next_line_bonus.c`: bonus part implementation supporting multiple fds
- `get_next_line_utils_bonus.c`: bonus helper functions
- `get_next_line.h`: header file with prototypes and macros
- `get_next_line_bonus.h`: header file for bonus functions and macros

## 📋 usage example

```c
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include "get_next_line.h"

int main(void)
{
    int fd = open("example.txt", O_RDONLY);
    if (fd < 0)
        return (1);

    char *line;
    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return (0);
}

🛠️ compilation
compile your code with appropriate flags and define BUFFER_SIZE to set your buffer size:
# for main part
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c -o get_next_line

# for bonus part
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line_bonus.c get_next_line_utils_bonus.c -o get_next_line_bonus
💡 notes
the caller is responsible for freeing the memory allocated for each returned line

the function returns NULL on end-of-file or if an error occurs

buffer size is controlled by the BUFFER_SIZE macro

🎉 bonus features
supports reading simultaneously from multiple file descriptors without mixing their buffers or states

robust error handling and memory management to avoid leaks or crashes

dynamic adjustment to any BUFFER_SIZE defined at compile time

✍️ author
maroun sarkis – @maroun28
