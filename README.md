# 🌊 get_next_line: Reading a Line From a File Descriptor (42 Project)

[![C Language Badge](https://img.shields.io/badge/Language-C-blue.svg)](https://en.wikipedia.org/wiki/C_(programming_language))
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![File I/O Badge](https://img.shields.io/badge/Concept-File_I%2FO-informational)](https://en.wikipedia.org/wiki/Input/output)

### 🌟 Project Overview

This repository contains **get\_next\_line** (GNL), a core project from the **42 Common Core curriculum**.

The goal of this project is to write a function that, when called in a loop, reads a line ending with a newline character (`\n`) from a given file descriptor and returns it. This project is a practical exercise in managing memory, working with file descriptors, and understanding the persistence of `static` variables across function calls.

#### **Key Implementation Details:**
* **File Descriptor Agnostic:** The function must work correctly regardless of which file descriptor is passed to it (e.g., standard input `0`, file, pipe).
* **Single Line Return:** It returns one line at a time, including the newline character, if present.
* **Static Variable Usage:** It uses a static variable to preserve any remaining read data for the next call.
* **`BUFFER_SIZE`:** The implementation must correctly handle the reading and storage of data using the defined `BUFFER_SIZE` macro.

---

### 🛠️ Installation and Usage

`get_next_line` must be compiled and linked with your program, often alongside your `Libft`.

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/Nexus29/42-get_next_line.git](https://github.com/Nexus29/42-get_next_line.git)
    cd 42-get_next_line
    ```

2.  **Compile the Program:**
    You will need to compile `get_next_line.c`, `get_next_line_utils.c`, and your test file (`main.c`) together. You must also define the `BUFFER_SIZE` during compilation or in the header file.

    **Compilation Example (using a test file):**
    ```bash
    # Assuming BUFFER_SIZE is 42
    cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c main.c -o gnl_test
    ```
    * **Note:** You must link your **Libft** functions if your utility file uses them (e.g., `ft_strjoin`, `ft_strlen`).

3.  **Using the Function:**
    The function signature is:
    ```c
    char *get_next_line(int fd);
    ```

    **Example Usage:**
    ```c
    #include "get_next_line.h"
    #include <fcntl.h> // For open()

    int main(void)
    {
        int fd = open("test.txt", O_RDONLY);
        char *line;

        while ((line = get_next_line(fd)) != NULL)
        {
            printf("%s", line);
            free(line); // Don't forget to free the returned line!
        }
        close(fd);
        return (0);
    }
    ```

---

### 💡 Function Return Values

| Return Value | Condition |
| :--- | :--- |
| **A string (char \*)** | The successfully read line. This line must be freed by the caller. |
| **`NULL`** | An error occurred (e.g., invalid file descriptor, read error), OR the end of the file (EOF) has been reached and there is no more data to read. |

---

### 👤 Author

* **Giovanni Pio Lancellotta** - [Nexus29](https://github.com/Nexus29)
    * `42 Student ID:` **glancell**
    * `Personal Website:` *Coming Soon!*
