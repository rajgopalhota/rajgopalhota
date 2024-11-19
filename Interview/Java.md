Java interview questions and answers, categorized into **Fundamentals**, **OOP Concepts**, **Core Java**, and **Advanced Java**. I've included code snippets where applicable. 

---

### **Fundamental Java Questions**
1. **What is Java?**
   - **Answer:** Java is a high-level, class-based, object-oriented programming language designed to have as few implementation dependencies as possible. It is platform-independent due to its JVM-based execution model.

2. **What are the key features of Java?**
   - **Answer:** Some features are:
     - Platform-independent
     - Object-oriented
     - Multithreaded
     - Secure
     - Robust
     - High performance through JIT (Just-In-Time compiler).

3. **What is the difference between JDK, JRE, and JVM?**
   - **Answer:** 
     - **JDK (Java Development Kit):** Contains tools needed to develop and run Java applications.
     - **JRE (Java Runtime Environment):** Provides libraries and JVM to run Java applications.
     - **JVM (Java Virtual Machine):** Converts bytecode to machine code and executes it.

4. **Explain public static void main(String[] args).**
   - **Answer:** 
     - **public:** Accessible by JVM from anywhere.
     - **static:** No need to create an object to invoke the method.
     - **void:** Does not return any value.
     - **main:** The entry point of the program.

5. **What is the purpose of the `final` keyword in Java?**
   - **Answer:**
     - `final` class: Cannot be subclassed.
     - `final` method: Cannot be overridden.
     - `final` variable: Its value cannot be modified once assigned.

---

### **OOP Concepts**
6. **What are the four pillars of OOP?**
   - **Answer:** Encapsulation, Abstraction, Inheritance, Polymorphism.

7. **What is Encapsulation? Provide an example.**
   - **Answer:** Encapsulation is wrapping data and code into a single unit (class) and restricting access to its components using access modifiers.
   ```java
   class EncapsulationExample {
       private String name;

       public String getName() {
           return name;
       }

       public void setName(String name) {
           this.name = name;
       }
   }
   ```

8. **What is Inheritance?**
   - **Answer:** Inheritance allows a class to inherit properties and methods of another class.
   ```java
   class Animal {
       void eat() { System.out.println("This animal eats food."); }
   }

   class Dog extends Animal {
       void bark() { System.out.println("Dog barks."); }
   }

   public class Test {
       public static void main(String[] args) {
           Dog d = new Dog();
           d.eat(); // Inherited method
           d.bark();
       }
   }
   ```

9. **What is Polymorphism?**
   - **Answer:** Polymorphism means "many forms" and occurs in two ways:
     - Compile-time (Method Overloading)
     - Runtime (Method Overriding)
   ```java
   class Shape {
       void draw() { System.out.println("Drawing Shape"); }
   }

   class Circle extends Shape {
       void draw() { System.out.println("Drawing Circle"); }
   }

   public class Test {
       public static void main(String[] args) {
           Shape s = new Circle();
           s.draw(); // Runtime polymorphism
       }
   }
   ```

10. **What is the difference between abstract class and interface?**
    - **Answer:** 
      - Abstract class: Can have method implementations, fields, and constructors.
      - Interface: All methods are public and abstract by default.

---

### **Core Java Questions**
11. **What are Java's access modifiers?**
    - **Answer:** `private`, `default` (no modifier), `protected`, `public`.

12. **What is the difference between `==` and `.equals()`?**
    - **Answer:** 
      - `==` checks for reference equality.
      - `.equals()` checks for value equality.

13. **Explain the `String` class in Java.**
    - **Answer:** `String` is immutable, meaning once created, its value cannot be changed.

14. **What are `StringBuilder` and `StringBuffer`?**
    - **Answer:** Both are mutable. 
      - `StringBuilder` is faster but not thread-safe.
      - `StringBuffer` is thread-safe but slower.

15. **What is the difference between `ArrayList` and `LinkedList`?**
    - **Answer:** 
      - `ArrayList`: Fast access but slow insertion/deletion.
      - `LinkedList`: Fast insertion/deletion but slower access.

16. **How does a HashMap work?**
    - **Answer:** Uses key-value pairs and a hash function to determine bucket location. Collision is handled via chaining or open addressing.

---

### **Advanced Java Questions**
17. **What is Java Stream API?**
    - **Answer:** Used to process collections of data in a functional style.
    ```java
    List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
    numbers.stream().filter(n -> n % 2 == 0).forEach(System.out::println);
    ```

18. **What is the difference between `Checked` and `Unchecked` exceptions?**
    - **Answer:** 
      - Checked: Must be handled or declared (`IOException`).
      - Unchecked: Runtime exceptions that don't need handling (`NullPointerException`).

19. **What are lambdas in Java?**
    - **Answer:** Provide a concise way to write anonymous functions.
    ```java
    (parameters) -> expression
    ```

20. **Explain the concept of functional interfaces.**
    - **Answer:** Interfaces with a single abstract method annotated with `@FunctionalInterface`.

### **Core Java Questions (Continued)**

21. **What are the main differences between `List`, `Set`, and `Map`?**
    - **Answer:**
      - **List:** Ordered collection; allows duplicates (`ArrayList`, `LinkedList`).
      - **Set:** Unordered collection; does not allow duplicates (`HashSet`, `TreeSet`).
      - **Map:** Stores key-value pairs; keys are unique (`HashMap`, `TreeMap`).

22. **What is the purpose of the `transient` keyword?**
    - **Answer:** Fields marked `transient` are not serialized when the object is converted to a byte stream.

23. **What is `volatile` in Java?**
    - **Answer:** The `volatile` keyword ensures that a variable is read from and written to the main memory, not a thread's local cache. It guarantees visibility of changes to variables across threads.

24. **Explain the concept of the `synchronized` keyword.**
    - **Answer:** It ensures that only one thread can access a block of code or method at a time, preventing race conditions.

25. **What is the difference between `throw` and `throws`?**
    - **Answer:** 
      - **throw:** Used to explicitly throw an exception in a method or block.
      - **throws:** Declares the exceptions that a method can throw.

26. **What is `try-with-resources`?**
    - **Answer:** A feature to automatically close resources implementing `AutoCloseable`.
    ```java
    try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
        System.out.println(br.readLine());
    } catch (IOException e) {
        e.printStackTrace();
    }
    ```

27. **Explain `HashSet` vs. `TreeSet`.**
    - **Answer:** 
      - **HashSet:** Unordered, uses hashing, and is faster.
      - **TreeSet:** Ordered, uses Red-Black Tree, and is slower.

28. **What is the difference between `Array` and `ArrayList`?**
    - **Answer:** 
      - **Array:** Fixed size, can hold primitives.
      - **ArrayList:** Dynamic size, can only hold objects.

29. **Explain method overloading vs. overriding.**
    - **Answer:**
      - **Overloading:** Same method name, different parameter lists (compile-time polymorphism).
      - **Overriding:** Subclass provides a specific implementation of a method in the parent class (runtime polymorphism).

30. **What is the difference between `Comparable` and `Comparator`?**
    - **Answer:** 
      - **Comparable:** Used to define a natural ordering for a class.
      - **Comparator:** Used to define custom orderings.
    ```java
    class Employee implements Comparable<Employee> {
        int id;
        public int compareTo(Employee e) {
            return this.id - e.id;
        }
    }
    ```

---

### **OOP Questions (Continued)**

31. **What is the `super` keyword in Java?**
    - **Answer:** Refers to the parent class's method, field, or constructor.
    ```java
    class Parent {
        void display() { System.out.println("Parent class method"); }
    }

    class Child extends Parent {
        void display() {
            super.display(); // Calls Parent class method
            System.out.println("Child class method");
        }
    }
    ```

32. **Can a constructor be inherited?**
    - **Answer:** No, constructors are not inherited.

33. **What is an `interface` in Java?**
    - **Answer:** An interface is a contract that classes implement. Methods in interfaces are abstract by default (since Java 8, interfaces can also have default and static methods).

34. **What is the difference between `this` and `super`?**
    - **Answer:**
      - `this`: Refers to the current object.
      - `super`: Refers to the parent class.

35. **What is multiple inheritance? Does Java support it?**
    - **Answer:** Java does not support multiple inheritance with classes but allows it with interfaces to avoid the diamond problem.

36. **What are design patterns in Java?**
    - **Answer:** Reusable solutions to common software design problems. Examples include Singleton, Factory, and Observer patterns.

---

### **Advanced Java Questions**

37. **What is the Java Reflection API?**
    - **Answer:** Used to inspect and modify runtime behavior of classes, methods, and fields.
    ```java
    Class<?> cls = Class.forName("java.util.ArrayList");
    Method[] methods = cls.getDeclaredMethods();
    for (Method method : methods) {
        System.out.println(method.getName());
    }
    ```

38. **What is the difference between `Executor` and `ExecutorService`?**
    - **Answer:** 
      - `Executor`: Simple interface for launching tasks.
      - `ExecutorService`: Extends `Executor`, provides lifecycle management for thread pools.

39. **What is the Java Memory Model?**
    - **Answer:** Defines how threads interact with memory, focusing on the visibility of changes to variables and ordering of instructions.

40. **What are annotations in Java?**
    - **Answer:** Metadata for code that does not affect program execution. Common examples include `@Override`, `@FunctionalInterface`, and custom annotations.

41. **What is the difference between `Callable` and `Runnable`?**
    - **Answer:**
      - `Runnable`: Does not return a result.
      - `Callable`: Returns a result and can throw exceptions.
    ```java
    Callable<Integer> task = () -> { return 123; };
    ```

42. **What is garbage collection in Java?**
    - **Answer:** The process of reclaiming memory used by unreferenced objects.

43. **What are the types of references in Java?**
    - **Answer:** Strong, Weak, Soft, and Phantom references.

44. **Explain the `Optional` class in Java.**
    - **Answer:** A container for optional values to handle nulls safely.
    ```java
    Optional<String> name = Optional.ofNullable(null);
    System.out.println(name.orElse("Default Name"));
    ```

45. **What is the Stream API in Java?**
    - **Answer:** Provides functional-style operations on collections and streams.
    ```java
    List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);
    list.stream().filter(i -> i % 2 == 0).forEach(System.out::println);
    ```
### **Advanced Java Questions (Continued)**

46. **What is the purpose of `synchronized` blocks?**
    - **Answer:** `synchronized` blocks allow locking only critical sections of code, improving performance compared to synchronizing entire methods.
    ```java
    public void increment() {
        synchronized (this) {
            counter++;
        }
    }
    ```

47. **What are Java's thread states?**
    - **Answer:** 
      - **New:** Thread is created but not started.
      - **Runnable:** Thread is ready to run but not running.
      - **Blocked:** Waiting to acquire a lock.
      - **Waiting:** Indefinitely waiting for another thread.
      - **Timed Waiting:** Waiting for a specific time.
      - **Terminated:** Thread has finished execution.

48. **What is deadlock in Java?**
    - **Answer:** Deadlock occurs when two or more threads are waiting for each other to release locks, causing an infinite wait.

49. **How do you avoid deadlock?**
    - **Answer:**
      - Use try-locks with timeouts (`ReentrantLock`).
      - Avoid nested locks.
      - Lock in a consistent order.

50. **What is the `ThreadLocal` class?**
    - **Answer:** Provides thread-specific variables.
    ```java
    ThreadLocal<Integer> threadId = ThreadLocal.withInitial(() -> (int) Thread.currentThread().getId());
    ```

51. **What is a daemon thread?**
    - **Answer:** A daemon thread runs in the background and terminates when all user threads finish.
    ```java
    Thread t = new Thread(task);
    t.setDaemon(true);
    ```

52. **Explain `Future` and `CompletableFuture` in Java.**
    - **Answer:**
      - `Future`: Represents the result of an asynchronous computation.
      - `CompletableFuture`: Extends `Future` and supports functional programming features.
    ```java
    CompletableFuture.supplyAsync(() -> "Result").thenAccept(System.out::println);
    ```

53. **What is the difference between `wait()` and `sleep()`?**
    - **Answer:** 
      - `wait()`: Causes the thread to wait for a signal (object lock released).
      - `sleep()`: Pauses the thread for a specified time (object lock not released).

54. **What is the difference between `notify()` and `notifyAll()`?**
    - **Answer:**
      - `notify()`: Wakes up one waiting thread.
      - `notifyAll()`: Wakes up all waiting threads.

---

### **Collections Framework Questions**

55. **What is the difference between `HashMap` and `Hashtable`?**
    - **Answer:** 
      - `HashMap`: Not synchronized, allows one `null` key and multiple `null` values.
      - `Hashtable`: Synchronized, does not allow `null` keys or values.

56. **What is the difference between `ConcurrentHashMap` and `HashMap`?**
    - **Answer:** 
      - `ConcurrentHashMap`: Thread-safe, segments the map for better concurrency.
      - `HashMap`: Not thread-safe.

57. **What is a `LinkedHashMap`?**
    - **Answer:** Maintains insertion order and allows `null` keys/values.

58. **What is a `PriorityQueue` in Java?**
    - **Answer:** A queue that orders elements based on their natural ordering or a custom comparator.

59. **Explain the `NavigableMap` interface.**
    - **Answer:** Extends `SortedMap` to provide navigation methods like `lowerKey()`, `higherKey()`, etc.

60. **What is the difference between `TreeSet` and `HashSet`?**
    - **Answer:**
      - `TreeSet`: Ordered, based on a Red-Black Tree.
      - `HashSet`: Unordered, backed by a `HashMap`.

---

### **JVM, Garbage Collection, and Memory Management**

61. **What is the Java heap?**
    - **Answer:** A memory area where objects are allocated.

62. **What are the main garbage collection algorithms?**
    - **Answer:** Mark-and-Sweep, Generational GC, G1 GC (Garbage-First).

63. **What are strong, weak, and soft references in Java?**
    - **Answer:** 
      - **Strong:** Prevents GC.
      - **Soft:** Eligible for GC only under memory pressure.
      - **Weak:** Always eligible for GC.

64. **What is the difference between stack memory and heap memory?**
    - **Answer:** 
      - **Stack:** Stores local variables and function calls.
      - **Heap:** Stores objects and is managed by GC.

65. **What is PermGen/Metaspace?**
    - **Answer:**
      - PermGen (before Java 8): Stores class metadata.
      - Metaspace (Java 8+): Replaces PermGen and grows dynamically.

---

### **Java 8 and Functional Programming**

66. **What are default methods in interfaces?**
    - **Answer:** Methods in interfaces with a default implementation.
    ```java
    interface Vehicle {
        default void honk() { System.out.println("Honking!"); }
    }
    ```

67. **What is a functional interface?**
    - **Answer:** An interface with exactly one abstract method, e.g., `Runnable` or `Comparator`.

68. **What is the use of the `Stream` API?**
    - **Answer:** Used for declarative processing of collections.
    ```java
    List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);
    list.stream().filter(x -> x > 2).forEach(System.out::println);
    ```

69. **What are the differences between `map()` and `flatMap()`?**
    - **Answer:** 
      - `map()`: Transforms each element.
      - `flatMap()`: Flattens nested structures.

70. **What are `Optional` and its common methods?**
    - **Answer:** A container to handle null values safely. Common methods:
      - `of()`
      - `ofNullable()`
      - `isPresent()`
      - `orElse()`

---

### **Spring Boot-Specific Java Questions**

71. **What is Spring Boot?**
    - **Answer:** A framework for building Java applications quickly with embedded servers and auto-configuration.

72. **What is Dependency Injection?**
    - **Answer:** A design pattern where objects are provided their dependencies externally.

73. **What are the types of Spring scopes?**
    - **Answer:** Singleton, Prototype, Request, Session, GlobalSession.

74. **Explain the Spring Boot starter.**
    - **Answer:** A dependency that bundles related libraries, e.g., `spring-boot-starter-web`.

75. **What is Spring Data JPA?**
    - **Answer:** Simplifies database interactions with JPA-based repositories.

---

### **Remaining Questions**

76. **What is Serialization and Deserialization in Java?**
77. **What is a marker interface in Java?**
78. **How does the `hashCode()` method work?**
79. **What are common exceptions in Java?**
80. **How do you write thread-safe code in Java?**

Let me know if you'd like a deeper dive into specific areas like **Spring Boot**, **Multithreading**, or **Functional Programming**!