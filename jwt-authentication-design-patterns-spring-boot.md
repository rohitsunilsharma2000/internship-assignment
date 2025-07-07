To implement **JWT (JSON Web Token) based authentication and authorization** in a Spring Boot application, a combination of design patterns is often used for clarity, separation of concerns, and maintainability.

Here are the best-suited **design patterns** for implementing this functionality:

---

## ✅ 1. **Filter Pattern**

**Where:** Use a `OncePerRequestFilter` (like `JwtAuthenticationFilter`)
**Why:** Intercepts each HTTP request once and extracts + validates the JWT before allowing access.

> 🔧 Used to preprocess requests, extract the token from headers, and validate it.

---

## ✅ 2. **Strategy Pattern**

**Where:** For token validation strategy, especially if supporting multiple auth mechanisms (e.g., JWT, OAuth, API Key).
**Why:** Easily switch between different validation methods.

> 🔧 You can define an interface `TokenValidatorStrategy` and have `JwtValidator`, `OAuthValidator`, etc. implement it.

---

## ✅ 3. **Factory Pattern**

**Where:** To instantiate different token validators based on the request or user type.
**Why:** Centralized logic to create different types of authentication mechanisms.

---

## ✅ 4. **Builder Pattern**

**Where:** For creating complex JWTs with claims.
**Why:** Makes it easy to customize the JWT payload in a step-by-step manner.

> 🔧 Example: `JwtBuilder builder = Jwts.builder().setSubject().setClaims().setExpiration()...`

---

## ✅ 5. **Singleton Pattern**

**Where:** For utility classes like `JwtUtil` or `JwtTokenProvider`
**Why:** Ensures a single, reusable instance across the application.

---

## ✅ 6. **Adapter Pattern** *(Optional)*

**Where:** To integrate JWT logic with Spring Security seamlessly.
**Why:** Makes external library or token logic work with Spring Security filters or components.

---

### 🧩 Suggested Structure (Spring Boot)

```
com.example.security
│
├── config
│   └── SecurityConfig.java
│
├── jwt
│   ├── JwtAuthenticationFilter.java     → Filter Pattern
│   ├── JwtTokenProvider.java            → Singleton + Builder
│   └── JwtValidatorStrategy.java        → Strategy
│
├── factory
│   └── AuthValidatorFactory.java        → Factory Pattern
│
├── model
│   └── UserPrincipal.java
│
├── controller
│   └── AuthController.java
│
├── service
│   └── AuthService.java
```

---

### ✅ Summary Table

| Design Pattern    | Used For                                |
| ----------------- | --------------------------------------- |
| Filter Pattern    | Preprocessing requests (JWT extraction) |
| Strategy Pattern  | Swappable token validation logic        |
| Factory Pattern   | Dynamic token validator creation        |
| Builder Pattern   | Step-wise JWT construction              |
| Singleton Pattern | Reusable JWT provider/utility           |
| Adapter Pattern   | Integration with Spring Security        |

---

