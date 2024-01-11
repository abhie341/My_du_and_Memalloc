# Directory_size and Memory allocation
## my_du - Directory Size Calculator for Linux

`my_du` is a customized version of the `du` command, tailored for Linux systems. It provides the size of a directory, including its files, sub-directories, the directory itself, and the symbolic link file size, if any.

## Key Features

1. **Comprehensive Size Calculation:**
   - The size calculation includes the total size of files, sub-directories, and the directory itself.
   - Symbolic link file sizes are considered in the calculation, assuming they do not point to the same directory being analyzed, and there are no loops.

2. **Forked Process Architecture:**
   - The program utilizes the fork system call to create a child process for each immediate sub-directory.
   - Each child process independently calculates the size of its assigned directory and communicates the result to the parent process.

3. **Efficient Communication using Pipes:**
   - Communication between the parent and child processes is established through pipes.
   - A single pipe is used for efficient data exchange.

4. **Handling Symbolic Links:**
   - Symbolic links are managed by the parent process.
   - The program ensures that symbolic links do not lead to the same directory under consideration, preventing potential loops.

## How to Run

1. **Compilation:**
   - Compile the program using the following command:

     ```bash
     gcc -o my_du my_du.c
     ```

2. **Execution:**
   - Run the program with the desired relative path to the directory you want to analyze:

     ```bash
     ./my_du <relative path to the directory>
     ```

Replace `<relative path to the directory>` with the actual path you want to analyze.

Note: Ensure that the program has the necessary permissions to access the specified directory.

Feel free to explore the program and contribute to its improvement. If you encounter any issues or have suggestions, consider opening an issue or submitting a pull request.
