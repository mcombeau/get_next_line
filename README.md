# get_next_line

<p align="center">
  <img src="https://github.com/mcombeau/mcombeau/blob/main/42_badges/get_next_linee.png" alt="get_next_line 42 project badge"/>
</p>


The 42 school's get_next_line project is where we learn to read from a file descriptor, as well as the use of static variables.

This function returns a single line from a given file descriptor. If called in a loop, get_next_line returns the entire contents of a file, line by line until it reaches the end of the file. It can be compiled specifying any buffer size.

---

:us: Read my article in English about this project: [get_next_line: reading from a file descriptor](https://www.codequoi.com/en/42-get_next_line-project/)

:fr: Lire mon article en français sur ce projet :  [get_next_line : lire depuis un descripteur de fichier](https://www.codequoi.com/42-get_next_line/)

---

## Status

Finished: 2022-01-21.
Grade: 125/100.

## Usage
This function is not a stand-alone program, its files must be included and compiled within another project.

Example ``main.c``:
```c
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>
#include "get_next_line.h"

int	main(int argc, char **argv)
{
	int	fd;
	char	*line;

	(void)argc;
	fd = open(argv[1], O_RDONLY);
	line = "";
	while (line != NULL)
	{
		line = get_next_line(fd);
		printf("%s", line);
	}
	fd = close(fd);
	return (0);
}
```
Compilation:
```bash
gcc main.c get_next_line.c get_next_line_utils.c
```
``BUFFER_SIZE`` can be specified at compilation to override the default ``BUFFER_SIZE``:
```bash
gcc -D BUFFER_SIZE=42 main.c get_next_line.c get_next_line_utils.c
```
Execution:
```bash
./a.out [file]
```
Output should show the entire contents of the given file.

Execution with stdin:
```bash
./a.out /dev/tty
```
Program will wait for input, then once the enter key is pressed, print out the input as well as get_next_line's output. The process can be killed with ``ctrl-c``.

---
Made by mcombeau: mcombeau@student.42.fr | LinkedIn: [mcombeau](https://www.linkedin.com/in/mia-combeau-86653420b/) | Website: [codequoi.com](https://www.codequoi.com)
