### **Basics of OOPs in Java**
1. **Four Main Principles of OOPs**:
   - **Encapsulation**: Wrapping data and code together in a single unit, like a class.
   - **Inheritance**: Reusing code by inheriting properties and methods from a parent class.
   - **Polymorphism**: Ability of a method or object to behave differently based on the context (method overloading and overriding).
   - **Abstraction**: Hiding implementation details and showing only essential features.

2. **Java as Object-Oriented**:  
   Java supports OOP principles but isn’t purely object-oriented because it includes primitive types (like `int`, `char`).

3. **Class vs. Object**:  
   - **Class**: Blueprint for creating objects (e.g., `class Car`).
   - **Object**: Instance of a class (e.g., `Car myCar = new Car();`).

4. **Encapsulation**:  
   Encapsulation is implemented using private fields and public getters/setters:
   ```java
   class Employee {
       private String name;
       public String getName() { return name; }
       public void setName(String name) { this.name = name; }
   }
   ```

5. **Inheritance**:  
   Example:
   ```java
   class Animal {
       void sound() { System.out.println("Animal makes a sound"); }
   }
   class Dog extends Animal {
       void sound() { System.out.println("Dog barks"); }
   }
   ```

6. **Polymorphism**:  
   - **Overloading**: Same method name, different parameter list.
   - **Overriding**: Same method name and signature, redefined in a subclass.

7. **Abstraction**:  
   Achieved via abstract classes or interfaces:
   ```java
   abstract class Shape {
       abstract void draw();
   }
   class Circle extends Shape {
       void draw() { System.out.println("Drawing Circle"); }
   }
   ```

8. **Abstract Class vs. Interface**:  
   - Abstract classes can have constructors and non-abstract methods.
   - Interfaces can only have default and static methods (Java 8+).

---

### **Advanced OOPs Concepts**
9. **Multiple Inheritance**:  
   Achieved using interfaces:
   ```java
   interface A { void display(); }
   interface B { void display(); }
   class C implements A, B {
       public void display() { System.out.println("Multiple Inheritance"); }
   }
   ```

10. **`super` Keyword**: Refers to the parent class. Used to call a parent’s constructor or method.

11. **Method Overriding Rules**:  
    - Same method name, signature, and return type.
    - Access modifier should not be more restrictive.
    - The method must not be `static` or `final`.

12. **Constructors in Java**:  
    Constructors cannot be overridden but can be overloaded.

13. **Overloading `main`**:  
    You can overload `main`, but only the standard `public static void main(String[] args)` is used by the JVM.

14. **`this` Keyword**: Refers to the current class’s instance.

15. **Dynamic Method Dispatch**:  
    ```java
    class A {
        void display() { System.out.println("A"); }
    }
    class B extends A {
        void display() { System.out.println("B"); }
    }
    A obj = new B();
    obj.display(); // Output: B
    ```

16. **Association, Aggregation, and Composition**:  
    - **Association**: General relationship (e.g., Teacher teaches Student).
    - **Aggregation**: Weak relationship (e.g., Department has Employees).
    - **Composition**: Strong relationship (e.g., Car has Engine).

---

### **Java-Specific OOPs Features**
17. **`final`, `finally`, `finalize`**:
    - `final`: Prevent inheritance/overriding.
    - `finally`: Executes after `try-catch`.
    - `finalize`: Cleanup before garbage collection (deprecated).

18. **Multiple Levels of Inheritance**:  
    Resolved using the class hierarchy.

19. **Shallow vs. Deep Copy**:  
    - **Shallow**: Copies references.
    - **Deep**: Creates new objects.

20. **`Object` Class**:  
    Every class implicitly extends the `Object` class in Java.

---

### **Practical and Conceptual**
21. **Method Overriding Example**:
    ```java
    class Parent {
        void show() { System.out.println("Parent"); }
    }
    class Child extends Parent {
        void show() { System.out.println("Child"); }
    }
    Parent obj = new Child();
    obj.show(); // Output: Child
    ```

22. **Same Method in Interfaces**: No conflict if method signatures are the same.

23. **Nested vs. Inner Classes**:  
    - Nested: Static, accessed without creating an object.
    - Inner: Non-static, requires an object.

24. **Access Specifiers**:  
    - `private`: Only within the same class.
    - `protected`: Same package or subclass.
    - `public`: Anywhere.
    - Default: Within the same package.

25. **Static vs. Instance Variables/Methods**:  
    - **Static**: Belongs to the class, shared.
    - **Instance**: Unique to each object.

---

### **Miscellaneous**
26. **Default Methods (Java 8)**:  
    Methods with implementation in interfaces to support backward compatibility.

27. **`hashCode()` and `equals()`**:  
    Used for object comparison and hashing mechanisms.

28. **OOP in Exception Handling**:  
    Classes like `Throwable` and `Exception` follow inheritance.

29. **Singleton Class**:  
    Restricts instantiation to one object:
    ```java
    class Singleton {
        private static Singleton instance;
        private Singleton() {}
        public static Singleton getInstance() {
            if (instance == null) {
                instance = new Singleton();
            }
            return instance;
        }
    }
    ```

30. **OOP Benefits and Limitations**:  
    - **Benefits**: Reusability, scalability, and maintainability.
    - **Limitations**: Complexity and potential performance overhead.

---
