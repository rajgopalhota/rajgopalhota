
### **React Interview Questions**
1. **What is React? Why is it used?**  
   React is a JavaScript library for building user interfaces. It is used for creating fast, dynamic, and scalable web applications.

2. **What are the features of React?**  
   - Virtual DOM
   - Component-based architecture
   - Unidirectional data flow
   - JSX for templating

3. **What is JSX?**  
   JSX (JavaScript XML) allows you to write HTML-like syntax within JavaScript.  
   Example:
   ```jsx
   const element = <h1>Hello, World!</h1>;
   ```

4. **What is the difference between functional and class components?**  
   - **Class Components**: Can manage state and lifecycle methods (older approach).
   - **Functional Components**: Use hooks for state and lifecycle (modern approach).

5. **What are React hooks? Name some commonly used hooks.**  
   Hooks allow functional components to manage state and lifecycle. Common hooks include:
   - `useState`
   - `useEffect`
   - `useContext`
   - `useReducer`

6. **What is the Virtual DOM?**  
   The Virtual DOM is a lightweight copy of the real DOM. React updates the Virtual DOM first and then efficiently updates the real DOM.

7. **What is the difference between state and props in React?**  
   - **State**: Local to a component and can be changed.
   - **Props**: Passed from parent to child, immutable.

8. **What is React Router?**  
   React Router is a library for handling navigation and routing in React applications.

9. **How do you handle forms in React?**  
   By using controlled components with `onChange` handlers to sync input values with the component’s state.

10. **What is Redux? How does it relate to React?**  
    Redux is a state management library used for managing global application state. It can be integrated with React using `react-redux`.

---

### **Spring Boot Interview Questions**
1. **What is Spring Boot?**  
   Spring Boot simplifies building production-ready Spring applications with minimal configuration.

2. **What are the advantages of Spring Boot?**  
   - Auto-configuration
   - Embedded servers (Tomcat, Jetty)
   - Starter dependencies
   - Production-ready features (e.g., Actuator)

3. **What is the difference between Spring and Spring Boot?**  
   - **Spring**: Provides a comprehensive framework but requires extensive configuration.
   - **Spring Boot**: Builds on Spring to simplify setup with default configurations.

4. **What is a Spring Boot Starter?**  
   A pre-defined dependency to simplify configuration for specific features (e.g., `spring-boot-starter-web` for web applications).

5. **What is Spring Boot Auto-configuration?**  
   Spring Boot automatically configures components based on the dependencies and properties defined.

6. **What is the purpose of the `application.properties` or `application.yml` file?**  
   It is used to configure application-specific properties like server port, database settings, etc.

7. **What is the role of the `@SpringBootApplication` annotation?**  
   It is a convenience annotation combining `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`.

8. **What are Spring Boot Actuators?**  
   Actuators provide endpoints for monitoring and managing a Spring Boot application (e.g., `/actuator/health`).

9. **What is the use of the `@RestController` annotation?**  
   Combines `@Controller` and `@ResponseBody` to create RESTful APIs.

10. **How do you connect Spring Boot to a database?**  
    - Add dependencies (e.g., `spring-boot-starter-data-jpa`).
    - Configure `application.properties`:
      ```properties
      spring.datasource.url=jdbc:mysql://localhost:3306/db_name
      spring.datasource.username=root
      spring.datasource.password=password
      ```

11. **What is Hibernate in Spring Boot?**  
    Hibernate is an ORM framework used for interacting with databases. It is often integrated with Spring Boot for database operations.

12. **What is a Spring Boot Microservice?**  
    A Spring Boot application designed as an independent, loosely coupled service performing specific tasks.

13. **What is the use of `@Entity` and `@Table` in Spring Boot?**  
    - `@Entity`: Marks a class as a JPA entity.
    - `@Table`: Specifies the database table associated with the entity.

14. **How do you handle exceptions in Spring Boot?**  
    Use `@ControllerAdvice` and `@ExceptionHandler` for global exception handling.

15. **What is Spring Boot Security?**  
    A module for securing applications (authentication, authorization). Configured using dependencies and annotations like `@EnableWebSecurity`.

---
