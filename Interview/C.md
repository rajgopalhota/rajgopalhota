Here’s a comprehensive list of **C programming interview questions and answers** ranging from **basics to advanced concepts** with code snippets where applicable.

---

### **Basic C Programming Questions**

1. **What is C?**
   - **Answer:** C is a general-purpose, procedural programming language developed by Dennis Ritchie in 1972. It is widely used for system programming, embedded systems, and application development.

2. **What are the key features of C?**
   - **Answer:**
     - Simple and efficient.
     - Procedural language with structured programming.
     - Supports low-level (hardware-level) programming.
     - Rich library of built-in functions.
     - Portable and flexible.

3. **What is the difference between `#include <stdio.h>` and `#include "stdio.h"`?**
   - **Answer:** 
     - `<stdio.h>`: Searches for the header file in the standard include directories.
     - `"stdio.h"`: Searches for the header file in the current working directory first, then in the standard include directories.

4. **What are the basic data types in C?**
   - **Answer:** 
     - `int`: Integer.
     - `float`: Floating-point.
     - `char`: Character.
     - `double`: Double-precision floating-point.
     - `void`: No value.

5. **What is the difference between `printf()` and `scanf()`?**
   - **Answer:** 
     - `printf()`: Outputs data to the console.
     - `scanf()`: Reads input from the user.
   ```c
   int x;
   printf("Enter a number: ");
   scanf("%d", &x);
   printf("You entered: %d", x);
   ```

---

### **Intermediate C Questions**

6. **What is the difference between a pointer and an array?**
   - **Answer:** An array is a collection of elements stored in contiguous memory locations, while a pointer is a variable that stores the memory address of another variable.
   ```c
   int arr[3] = {1, 2, 3};
   int *ptr = arr;
   printf("%d", *(ptr + 1)); // Outputs 2
   ```

7. **What is a null pointer?**
   - **Answer:** A null pointer is a pointer that does not point to any memory location. It is often used to indicate an uninitialized or invalid pointer.
   ```c
   int *ptr = NULL;
   if (ptr == NULL) {
       printf("Pointer is null");
   }
   ```

8. **What is a `static` variable in C?**
   - **Answer:** A `static` variable retains its value between function calls and is initialized only once.
   ```c
   void count() {
       static int x = 0;
       x++;
       printf("%d\n", x);
   }
   ```

9. **What is the difference between `struct` and `union`?**
   - **Answer:**
     - In a `struct`, each member has its own memory location.
     - In a `union`, all members share the same memory location.
   ```c
   struct Student { int id; char name[20]; };
   union Data { int i; float f; };
   ```

10. **What are function pointers?**
    - **Answer:** Function pointers are pointers that point to the address of a function.
    ```c
    void hello() { printf("Hello!"); }
    void (*func_ptr)() = hello;
    func_ptr(); // Calls hello()
    ```

---

### **Advanced C Questions**

11. **What is dynamic memory allocation in C?**
    - **Answer:** It is the process of allocating memory during runtime using functions like `malloc`, `calloc`, `realloc`, and `free`.
    ```c
    int *ptr = (int *)malloc(5 * sizeof(int));
    free(ptr); // Frees allocated memory
    ```

12. **What are storage classes in C?**
    - **Answer:** Define the scope, visibility, and lifetime of variables.
      - `auto`: Default storage class for local variables.
      - `register`: Requests the variable to be stored in a CPU register.
      - `static`: Retains the value between function calls.
      - `extern`: Declares a global variable visible to all files.

13. **What is a volatile keyword?**
    - **Answer:** Indicates that a variable may be changed by external sources and prevents the compiler from optimizing it.
    ```c
    volatile int flag = 1;
    ```

14. **What is the difference between pass-by-value and pass-by-reference?**
    - **Answer:**
      - Pass-by-value: A copy of the actual value is passed.
      - Pass-by-reference: The address of the variable is passed.
    ```c
    void increment(int *num) { (*num)++; }
    ```

15. **What is recursion?**
    - **Answer:** A function that calls itself to solve smaller instances of a problem.
    ```c
    int factorial(int n) {
        if (n == 0) return 1;
        return n * factorial(n - 1);
    }
    ```

---

### **Additional Questions (16–30)**

16. **What is a dangling pointer?**
    - **Answer:** A pointer pointing to memory that has already been deallocated.

17. **How are arrays passed to functions?**
    - **Answer:** Arrays are passed as pointers to the first element.

18. **What is the difference between `malloc` and `calloc`?**
    - **Answer:**
      - `malloc`: Allocates uninitialized memory.
      - `calloc`: Allocates memory initialized to zero.

19. **What is the difference between `==` and `=` in C?**

20. **Explain the concept of preprocessor directives.**

21. **What is the difference between a macro and an inline function?**

22. **What is an enum in C?**

23. **How is a stack different from a heap in memory allocation?**

24. **What are bitwise operators in C?**

25. **Explain the difference between `sizeof` and `strlen`.**

26. **What is the use of `typedef` in C?**

27. **How do you implement a linked list in C?**

28. **What are the key differences between C and C++?**

29. **What is a segmentation fault?**

30. **How do you handle file operations in C?**


### **Intermediate and Advanced C Programming Questions (Questions 21–40)**

---

21. **What is the difference between `malloc()` and `calloc()`?**
   - **Answer:** 
     - `malloc()` allocates memory but doesn’t initialize it.
     - `calloc()` allocates memory and initializes it to zero.
   ```c
   int *arr1 = (int *)malloc(5 * sizeof(int)); // Uninitialized
   int *arr2 = (int *)calloc(5, sizeof(int)); // Initialized to 0
   ```

22. **What is the use of the `sizeof` operator?**
   - **Answer:** Determines the size of a data type or object in bytes.
   ```c
   printf("Size of int: %lu", sizeof(int)); // Output depends on architecture
   ```

23. **What is a function pointer?**
   - **Answer:** A pointer that stores the address of a function.
   ```c
   void greet() { printf("Hello!"); }
   void (*funcPtr)() = greet;
   funcPtr(); // Calls greet()
   ```

24. **What is the difference between a pointer and an array?**
   - **Answer:** A pointer stores a memory address, while an array is a collection of elements stored contiguously.
   ```c
   int arr[3] = {1, 2, 3};
   int *ptr = arr; // Points to the first element
   printf("%d", *(ptr + 1)); // Outputs 2
   ```

25. **How do you use a `struct` with a pointer?**
   ```c
   struct Point { int x, y; };
   struct Point p = {1, 2};
   struct Point *ptr = &p;
   printf("x: %d, y: %d", ptr->x, ptr->y);
   ```

26. **What is the difference between `getchar()` and `scanf()`?**
   - **Answer:** 
     - `getchar()`: Reads a single character.
     - `scanf()`: Reads formatted input.
   ```c
   char c = getchar(); // Reads one character
   scanf("%c", &c);    // Reads formatted input
   ```

27. **What is the purpose of `volatile`?**
   - **Answer:** Prevents the compiler from optimizing the variable, ensuring it is read directly from memory.
   ```c
   volatile int flag = 1;
   ```

28. **What is a segmentation fault?**
   - **Answer:** Occurs when a program attempts to access restricted memory.
   ```c
   int *ptr = NULL;
   printf("%d", *ptr); // Causes a segmentation fault
   ```

29. **What is the difference between `exit()` and `_Exit()`?**
   - **Answer:** 
     - `exit()`: Performs cleanup tasks before terminating the program.
     - `_Exit()`: Terminates the program immediately without cleanup.

30. **What is the difference between a stack and a heap?**
   - **Answer:** 
     - **Stack:** Used for static memory allocation, faster, limited size.
     - **Heap:** Used for dynamic memory allocation, slower, larger size.

31. **What is a `union` in C?**
   - **Answer:** A `union` allows multiple variables to share the same memory location.
   ```c
   union Data { int i; float f; };
   union Data d;
   d.i = 10;
   printf("%d", d.i);
   ```

32. **What is `typedef` in C?**
   - **Answer:** Allows you to create aliases for data types.
   ```c
   typedef unsigned int uint;
   uint age = 25;
   ```

33. **What is the difference between `break` and `continue`?**
   - **Answer:** 
     - `break`: Exits the loop or switch statement.
     - `continue`: Skips the current iteration and continues the loop.
   ```c
   for (int i = 0; i < 5; i++) {
       if (i == 2) continue;
       printf("%d ", i);
   }
   ```

34. **What are macros in C?**
   - **Answer:** Macros are preprocessor directives used for constant definitions or inline code.
   ```c
   #define PI 3.14
   printf("Value of PI: %f", PI);
   ```

35. **What is the difference between `#define` and `const`?**
   - **Answer:**
     - `#define`: Preprocessor directive, no memory allocated.
     - `const`: Allocates memory, type-checked by the compiler.
   ```c
   const int num = 10;
   ```

36. **What are bitwise operators in C?**
   - **Answer:** Operators that work on bits: `&`, `|`, `^`, `~`, `<<`, and `>>`.
   ```c
   int x = 5, y = 3;
   printf("%d", x & y); // Bitwise AND
   ```

37. **How do you reverse a string in C?**
   ```c
   void reverse(char *str) {
       int len = strlen(str);
       for (int i = 0; i < len / 2; i++) {
           char temp = str[i];
           str[i] = str[len - i - 1];
           str[len - i - 1] = temp;
       }
   }
   ```

38. **What is a null pointer?**
   - **Answer:** A pointer that doesn’t point to any memory location.
   ```c
   int *ptr = NULL;
   ```

39. **How do you implement a linked list in C?**
   ```c
   struct Node {
       int data;
       struct Node *next;
   };
   ```

40. **What are command-line arguments in C?**
   ```c
   int main(int argc, char *argv[]) {
       printf("First argument: %s", argv[0]);
       return 0;
   }
   ```

### **Intermediate to Advanced C Programming Questions (Questions 41–60)**

---

41. **What is the difference between `fgets()` and `gets()`?**
   - **Answer:** 
     - `fgets()`: Reads a line from a file or standard input and prevents buffer overflow by limiting the number of characters.
     - `gets()`: Unsafe and can lead to buffer overflow.
   ```c
   char str[50];
   fgets(str, sizeof(str), stdin); // Safe
   ```

42. **What is a pointer to a pointer in C?**
   - **Answer:** A pointer that stores the address of another pointer.
   ```c
   int x = 10;
   int *p = &x;
   int **pp = &p;
   printf("Value: %d", **pp);
   ```

43. **What is the use of `memcpy()` in C?**
   - **Answer:** Copies a block of memory from one location to another.
   ```c
   char src[50] = "Hello, World!";
   char dest[50];
   memcpy(dest, src, strlen(src) + 1);
   printf("%s", dest);
   ```

44. **What is the difference between `memset()` and `memcpy()`?**
   - **Answer:** 
     - `memset()`: Fills a block of memory with a specific value.
     - `memcpy()`: Copies memory from one location to another.
   ```c
   char str[50] = "Hello!";
   memset(str, '*', 3); // Changes first 3 chars to '*'
   ```

45. **How do you swap two variables without using a third variable?**
   ```c
   int a = 5, b = 10;
   a = a + b;
   b = a - b;
   a = a - b;
   printf("a: %d, b: %d", a, b);
   ```

46. **How do you find the length of a string without `strlen()`?**
   ```c
   int length(char *str) {
       int count = 0;
       while (*str++) count++;
       return count;
   }
   ```

47. **What is a segmentation fault in C?**
   - **Answer:** Occurs when a program tries to access an invalid memory location.
   ```c
   int *ptr = NULL;
   printf("%d", *ptr); // Causes segmentation fault
   ```

48. **How do you check if a number is even or odd without using the modulus operator?**
   ```c
   int isEven(int num) {
       return (num & 1) == 0; // Checks if the last bit is 0
   }
   ```

49. **What is the difference between `strcpy()` and `strncpy()`?**
   - **Answer:** 
     - `strcpy()`: Copies a string without checking bounds.
     - `strncpy()`: Copies a specified number of characters.
   ```c
   char dest[5];
   strncpy(dest, "Hello, World!", sizeof(dest) - 1);
   ```

50. **How do you reverse a number in C?**
   ```c
   int reverse(int num) {
       int rev = 0;
       while (num != 0) {
           rev = rev * 10 + num % 10;
           num /= 10;
       }
       return rev;
   }
   ```

51. **What is a memory leak?**
   - **Answer:** Occurs when dynamically allocated memory is not freed.
   ```c
   int *ptr = (int *)malloc(sizeof(int));
   // Missing free(ptr); causes memory leak
   ```

52. **How do you implement a stack using arrays?**
   ```c
   #define MAX 5
   int stack[MAX], top = -1;
   void push(int value) {
       if (top < MAX - 1) stack[++top] = value;
   }
   ```

53. **What is the difference between `++i` and `i++`?**
   - **Answer:** 
     - `++i`: Increments before the expression is evaluated.
     - `i++`: Increments after the expression is evaluated.

54. **What is `realloc()` in C?**
   - **Answer:** Resizes previously allocated memory.
   ```c
   int *arr = (int *)malloc(2 * sizeof(int));
   arr = (int *)realloc(arr, 5 * sizeof(int));
   ```

55. **How do you find the factorial of a number?**
   ```c
   int factorial(int n) {
       return (n == 0) ? 1 : n * factorial(n - 1);
   }
   ```

56. **How do you check for a palindrome string?**
   ```c
   int isPalindrome(char *str) {
       int len = strlen(str), i;
       for (i = 0; i < len / 2; i++) {
           if (str[i] != str[len - i - 1]) return 0;
       }
       return 1;
   }
   ```

57. **What is a double pointer?**
   - **Answer:** A pointer to another pointer.
   ```c
   int x = 10;
   int *p = &x;
   int **pp = &p;
   printf("%d", **pp);
   ```

58. **How do you merge two sorted arrays?**
   ```c
   void merge(int arr1[], int n1, int arr2[], int n2, int merged[]) {
       int i = 0, j = 0, k = 0;
       while (i < n1 && j < n2) {
           merged[k++] = (arr1[i] < arr2[j]) ? arr1[i++] : arr2[j++];
       }
       while (i < n1) merged[k++] = arr1[i++];
       while (j < n2) merged[k++] = arr2[j++];
   }
   ```

59. **What is the difference between `free()` and `delete`?**
   - **Answer:** 
     - `free()` is used in C to deallocate memory.
     - `delete` is used in C++.

60. **How do you handle signals in C?**
   ```c
   #include <signal.h>
   void handleSignal(int sig) {
       printf("Caught signal: %d\n", sig);
   }
   int main() {
       signal(SIGINT, handleSignal);
       while (1);
   }
   ```
