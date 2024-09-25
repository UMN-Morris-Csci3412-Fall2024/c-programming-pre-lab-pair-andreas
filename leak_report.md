# Leak Report

## Memory Leak Report for `clean_whitespace.c`

### Identified Memory Leaks

#### 1. Memory Leak in `strip` Function

The `strip` function allocates memory for the cleaned string using `calloc`. This memory was not being freed properly, leading to memory leaks.

#### 2. Memory Leak in `is_clean` Function

The `is_clean` function calls `strip` and compares the result with the original string. The memory allocated by `strip` was not being freed in all cases, leading to memory leaks.

### Solutions Applied

#### 1. Fixing Memory Leak in `strip` Function

Changed the `strip` function to ensure that it always returns a dynamically allocated string, and the caller is responsible for freeing this memory.

#### 2. Fixing Memory Leak in `is_clean` Function

Changed the `is_clean` function so that it would free the memory allocated by `strip` after comparing the strings.

#### 3. Fixing Memory Leaks in Test File

Updated the test file to ensure that all dynamically allocated memory is properly freed after each test case that calls `strip`.
