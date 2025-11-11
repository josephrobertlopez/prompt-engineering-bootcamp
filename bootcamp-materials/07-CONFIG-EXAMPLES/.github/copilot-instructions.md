# GitHub Copilot Instructions - Spring Boot 3 Migration

**Standard:** Official Microsoft/GitHub Copilot configuration format
**Documentation:** https://docs.github.com/en/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot
**Maturity:** 🟡 Tier 2 (Official GitHub standard, ~2 years)

---

## Project Context

This project is migrating from Spring Boot 2.7 to Spring Boot 3.2.

### Technology Stack
- Spring Boot 3.2.x
- Java 17+
- Jakarta EE (migrated from javax)
- Maven build system

---

## Migration Standards

### Package Transformations

Transform all javax.* imports to jakarta.* namespace:

```java
// BEFORE (Spring Boot 2.7)
import javax.validation.Valid;
import javax.servlet.http.HttpServletRequest;
import javax.persistence.Entity;

// AFTER (Spring Boot 3.2)
import jakarta.validation.Valid;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.persistence.Entity;
```

### Annotation Modernization

Use specific HTTP method annotations instead of @RequestMapping:

```java
// BEFORE (verbose)
@RequestMapping(value = "/users", method = RequestMethod.GET)
public ResponseEntity<List<User>> getAllUsers() { }

// AFTER (modern)
@GetMapping("/users")
public ResponseEntity<List<User>> getAllUsers() { }
```

Apply to all HTTP methods:
- GET → @GetMapping
- POST → @PostMapping
- PUT → @PutMapping
- DELETE → @DeleteMapping
- PATCH → @PatchMapping

### Dependency Injection

Use constructor injection with @RequiredArgsConstructor (Lombok):

```java
// BEFORE (field injection)
@Autowired
private UserService userService;

// AFTER (constructor injection)
@RequiredArgsConstructor
public class UserController {
    private final UserService userService;
}
```

---

## Code Quality Standards

### Must Maintain
- ✅ All existing API endpoints unchanged (same URLs, same contracts)
- ✅ All business logic preserved exactly
- ✅ All unit tests continue passing
- ✅ No breaking changes to API consumers

### Must Eliminate
- ❌ No javax.* imports (all must be jakarta.*)
- ❌ No @Deprecated warnings
- ❌ No field injection with @Autowired
- ❌ No verbose @RequestMapping where specific annotations exist

### Compilation Requirements
- Must compile cleanly with Spring Boot 3.2.x
- Must compile with Java 17+
- Must pass all existing tests without modification

---

## Exception Handling Strategy

**Decision:** Keep current ResponseEntity-based exception handling.

**Rationale:** Migration focuses on framework upgrade, not feature enhancements. Maintain minimal changes strategy.

```java
// KEEP THIS PATTERN (do not change to ProblemDetail)
try {
    User user = userService.createUser(user);
    return ResponseEntity.status(HttpStatus.CREATED).body(user);
} catch (IllegalArgumentException e) {
    return ResponseEntity.badRequest().build();
} catch (EntityNotFoundException e) {
    return ResponseEntity.notFound().build();
}
```

**Future work:** Spring Boot 3's ProblemDetail (RFC 7807) can be adopted in separate enhancement phase.

---

## Phased Migration Approach

When migrating controllers, follow this order:

### Phase 1: Package Updates
1. Replace all javax.* imports with jakarta.*
2. Verify compilation succeeds
3. Checkpoint: `mvn compile` passes

### Phase 2: Annotation Modernization
1. Replace @RequestMapping(method=X) with @XMapping
2. Verify no @Deprecated warnings
3. Checkpoint: IDE shows no warnings

### Phase 3: Dependency Injection
1. Add @RequiredArgsConstructor if missing
2. Ensure services are final fields
3. Remove @Autowired on constructors
4. Checkpoint: Application starts, dependency injection works

---

## References

**Architecture Decision Records:**
- See docs/adr/0001-spring-migration-standards.md for full rationale
- See docs/adr/0002-exception-handling-strategy.md for ProblemDetail decision

**Official Documentation:**
- Spring Boot 3.2 Migration Guide: https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.2-Migration-Guide
- Jakarta EE Namespace: https://jakarta.ee/specifications/platform/9/

---

## Pattern Application

This file demonstrates:
- **Persona Pattern:** Establishes AI as Spring Boot migration specialist
- **Few-shot Pattern:** Provides before/after transformation examples
- **Template Pattern:** Structures expectations (phases, requirements)
- **Decision Documentation:** Explains strategy choices (exception handling)

**Alternative formats:** This same content could be structured as:
- ADR (Architecture Decision Record) in docs/adr/
- .cursorrules file (Cursor IDE specific)
- .aidigestrc file (Aider tool specific)

**Choose format based on your team's tools and preferences.**
