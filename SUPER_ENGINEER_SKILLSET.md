# 🧠 Super Engineer Skillset — The Complete Concept Map

> A parent → child map of what a senior/staff Java engineer with 15+ years of experience should know.
> Every section starts with a **tree view** (the big picture). After that come the **child concepts** with the key points, gotchas and interview-style questions to check yourself.
>
> **How to use this file**
> - Tick `- [ ]` → `- [x]` as you master each item. Edit it in VS Code or Obsidian, or on GitHub.
> - Rate yourself on each parent topic: **L1** = heard of it · **L2** = can use it · **L3** = can explain the internals · **L4** = can teach it and make trade-offs.
> - A 15-year engineer should aim for **L3 across the board and L4 in 3–4 areas**.
> - "❓" lines are self-test questions. If you can't answer one out loud in 2 minutes, revisit the topic.

---

## 📑 Table of Contents

| # | Area | # | Area |
|---|------|---|------|
| 1 | [Core Java — Language Fundamentals](#1-core-java--language-fundamentals) | 14 | [Low-Level Design (LLD)](#14-low-level-design-lld) |
| 2 | [Core Java — OOP](#2-core-java--object-oriented-programming) | 15 | [System Design (HLD)](#15-system-design-hld) |
| 3 | [Core Java — Collections](#3-core-java--collections-framework) | 16 | [Architecture Styles & DDD](#16-architecture-styles--ddd) |
| 4 | [Core Java — Modern Java (8 → 25)](#4-modern-java-8--25) | 17 | [Databases](#17-databases) |
| 5 | [Core Java — Concurrency](#5-concurrency--multithreading) | 18 | [Messaging & Streaming](#18-messaging--event-streaming) |
| 6 | [JVM Internals & Performance](#6-jvm-internals-memory--performance) | 19 | [Testing](#19-testing) |
| 7 | [Spring Framework Core](#7-spring-framework-core) | 20 | [DevOps, Build & Cloud](#20-devops-build--cloud) |
| 8 | [Spring Boot](#8-spring-boot) | 21 | [Observability & Production](#21-observability--production-engineering) |
| 9 | [Spring Data, JPA & Hibernate](#9-spring-data-jpa--hibernate) | 22 | [Security (AppSec)](#22-application-security) |
| 10 | [Spring Web, REST & WebFlux](#10-spring-web-rest--webflux) | 23 | [CS Fundamentals: OS & Networking](#23-cs-fundamentals-os--networking) |
| 11 | [Spring Security](#11-spring-security) | 24 | [AI-Assisted Engineering](#24-ai-assisted-engineering-2026-must-know) |
| 12 | [Microservices & Spring Cloud](#12-microservices--spring-cloud) | 25 | [Senior/Staff Engineer Soft Skills](#25-seniorstaff-engineer-skills-non-technical) |
| 13 | [DSA](#13-data-structures--algorithms-dsa) | 26 | [Design Principles & Patterns](#26-design-principles) |
| — | | 27 | [Design Patterns (GoF + Enterprise)](#27-design-patterns) |
| — | | 28 | [Study Roadmap & Resources](#28-study-roadmap--resources) |

---

## 🗺️ Master Mind-Map (Top Level)

```
SUPER ENGINEER
├── Programming Foundation
│   ├── Core Java (Language, OOP, Collections, Modern Java, Concurrency)
│   ├── JVM Internals (Memory, GC, JIT, Class Loading, Tuning)
│   └── DSA (Complexity, Data Structures, Algorithms, Problem Patterns)
├── Frameworks & Ecosystem
│   ├── Spring Core (IoC, DI, AOP, Bean Lifecycle)
│   ├── Spring Boot (Auto-config, Actuator, Config, Testing)
│   ├── Spring Data/JPA/Hibernate
│   ├── Spring Web/WebFlux/REST
│   ├── Spring Security (AuthN, AuthZ, OAuth2, JWT)
│   └── Spring Cloud / Microservices
├── Design
│   ├── Design Principles (SOLID, DRY, KISS, YAGNI, GRASP)
│   ├── Design Patterns (GoF, Enterprise, Microservice, Concurrency)
│   ├── Low-Level Design (class modelling, case studies)
│   ├── High-Level/System Design (scalability, distributed systems)
│   └── Architecture (Layered, Hexagonal, Clean, DDD, EDA, CQRS)
├── Data
│   ├── Relational DBs (SQL, indexing, transactions, tuning)
│   ├── NoSQL (Document, KV, Column, Graph), Caching (Redis)
│   └── Messaging & Streaming (Kafka, RabbitMQ)
├── Delivery & Operations
│   ├── Testing (Unit, Integration, Contract, Performance)
│   ├── Build & DevOps (Maven/Gradle, Git, Docker, K8s, CI/CD)
│   ├── Cloud (AWS/Azure/GCP core services)
│   ├── Observability (Logs, Metrics, Traces, SLOs)
│   └── Security (OWASP, crypto basics, secrets)
├── CS Fundamentals (OS, Networking, HTTP, TCP/IP, DNS, TLS)
├── AI-Assisted Engineering (LLMs, RAG, Spring AI, AI coding tools)
└── Senior/Staff Skills (Ownership, Communication, Mentoring, ADRs, Estimation)
```

---

# 1. Core Java — Language Fundamentals

```
Language Fundamentals
├── JDK / JRE / JVM
├── Data Types
│   ├── Primitives (byte, short, int, long, float, double, char, boolean)
│   ├── Wrapper Classes & Autoboxing (Integer cache −128..127)
│   └── Type Casting (widening, narrowing), Type Promotion
├── Variables (local, instance, static), Scope, var (Java 10)
├── Operators (arithmetic, bitwise, shift >> >>>, ternary, instanceof)
├── Control Flow (if, switch, loops, labeled break/continue)
├── Strings
│   ├── Immutability & String Pool
│   ├── String vs StringBuilder vs StringBuffer
│   ├── intern(), equals vs ==, compact strings (Java 9)
│   └── Text Blocks (Java 15)
├── Arrays (1D, 2D, jagged, Arrays utility)
├── Methods
│   ├── Pass-by-value (always! even for references)
│   ├── Overloading, Varargs
│   └── static vs instance methods
├── Keywords: final, static, this, super, transient, volatile, synchronized, native, strictfp
├── Exceptions
│   ├── Hierarchy (Throwable → Error / Exception → RuntimeException)
│   ├── Checked vs Unchecked
│   ├── try-catch-finally, try-with-resources, AutoCloseable
│   ├── Multi-catch, suppressed exceptions
│   └── Custom exceptions & best practices
├── Packages & Access Modifiers (private, default, protected, public)
├── Object class methods (equals, hashCode, toString, clone, finalize, wait/notify)
├── Inner Classes (static nested, inner, local, anonymous)
├── Enums (fields, methods, abstract methods, EnumMap/EnumSet)
├── Annotations (built-in, meta-annotations, retention, custom)
├── Generics
│   ├── Type parameters, bounded types
│   ├── Wildcards (? extends / ? super — PECS)
│   └── Type erasure & its limitations
├── Reflection API
├── I/O & NIO (streams, readers, Files, Path, Channels, Buffers)
├── Serialization (Serializable, serialVersionUID, Externalizable)
└── Java Platform Module System (JPMS, Java 9)
```

### 1.1 JDK, JRE, JVM
- [ ] **JDK** = JRE + dev tools (javac, jar, jshell, jlink, jcmd, jfr). **JRE** = JVM + core libs. **JVM** = runtime that executes bytecode.
- [ ] Compile flow: `.java → javac → .class (bytecode) → ClassLoader → JVM (interpreter + JIT) → native code`.
- [ ] "Write once, run anywhere": the bytecode is portable, the JVM is platform specific.
- [ ] Since Java 11 there is no separate JRE download. Use `jlink` to build custom runtimes.
- ❓ Why is Java both compiled and interpreted?

### 1.2 Data Types & Wrappers
- [ ] Sizes: byte 1B, short 2B, int 4B, long 8B, float 4B, double 8B, char 2B (UTF-16), boolean (JVM dependent).
- [ ] **Autoboxing pitfalls**: `Integer a=127, b=127; a==b → true`, but with 128 → false (Integer cache). Always use `.equals()`.
- [ ] Unboxing a `null` Integer → `NullPointerException`.
- [ ] Never use `float`/`double` for money. Use `BigDecimal` (built with the String constructor) or long cents.
- [ ] Integer overflow is silent. Use `Math.addExact()` to detect it.
- ❓ What does `0.1 + 0.2 == 0.3` return, and why?

### 1.3 Strings
- [ ] Strings are **immutable**, which gives thread safety, safe hashCode caching, pool sharing and security (class names, URLs).
- [ ] **String Pool** lives in the heap (it moved from PermGen in Java 7). Literals go to the pool; `new String("x")` creates a new object.
- [ ] `StringBuilder` (not synchronized, fast) vs `StringBuffer` (synchronized, legacy).
- [ ] `+` concatenation in loops creates garbage, so use StringBuilder. Since Java 9 the compiler uses `invokedynamic` (`StringConcatFactory`) for single expressions.
- [ ] Compact Strings (Java 9): Latin-1 strings use a `byte[]` with 1 byte per char.
- [ ] Useful APIs: `strip()`, `isBlank()`, `lines()`, `repeat()`, `String.join`, `formatted()`, text blocks `"""`.
- ❓ Why is `char[]` preferred over String for passwords?

### 1.4 Pass-by-Value
- [ ] Java is **always pass-by-value**. For objects, the value passed is a copy of the reference.
- [ ] Reassigning the parameter inside a method does not affect the caller. Mutating the object through it does.

### 1.5 Important Keywords
- [ ] `final`: a variable can't be reassigned, a method can't be overridden, a class can't be extended. A final reference ≠ an immutable object.
- [ ] `static`: belongs to the class. Covers static blocks (run at class init), static nested classes, and static imports.
- [ ] `transient`: the field is skipped during serialization.
- [ ] `volatile`: visibility and ordering guarantees, **not atomicity** (see Concurrency).
- [ ] Effectively final: a requirement for lambdas and anonymous classes that capture locals.

### 1.6 Exceptions
- [ ] Hierarchy: `Throwable` → `Error` (OOM, StackOverflow; don't catch these) and `Exception` → `RuntimeException` (unchecked).
- [ ] **Checked** = recoverable, the compiler forces handling (IOException). **Unchecked** = programming errors (NPE, IllegalArgumentException).
- [ ] `finally` always runs, except on `System.exit()`, a JVM crash, or a daemon thread dying.
- [ ] A `return` in `finally` overrides the try's return or exception. **Never do this.**
- [ ] try-with-resources closes resources in reverse order. Exceptions thrown on close become **suppressed** (`getSuppressed()`).
- [ ] Best practices: catch specific exceptions, don't swallow them, wrap with a cause (`new X("msg", e)`), throw early and catch late, and keep exceptions out of normal control flow.
- [ ] Spring/modern trend: prefer unchecked domain exceptions plus a global handler.
- ❓ Difference between `throw` and `throws`? Can you override a method and throw a broader checked exception?

### 1.7 Object Class Contract
- [ ] **equals/hashCode contract**: equal objects must have equal hashCodes. Unequal objects *may* collide.
- [ ] Override both or neither. A broken contract breaks HashMap and HashSet.
- [ ] equals must be reflexive, symmetric, transitive, consistent, and return false for null.
- [ ] `clone()` is broken by design (shallow copy, `Cloneable` marker). Prefer copy constructors or static factories.
- [ ] `finalize()` is deprecated for removal. Use `Cleaner` or try-with-resources.
- ❓ What happens if you put a mutable key in a HashMap and then mutate it?

### 1.8 Inner Classes
- [ ] **Static nested** has no reference to the outer instance. This is the preferred kind and is used by the Builder pattern.
- [ ] **Inner (non-static)** holds an implicit reference to the outer instance, which is a memory-leak risk.
- [ ] **Local** and **anonymous** classes can capture effectively-final locals.

### 1.9 Enums
- [ ] Enums are full classes: constructors (always private), fields, methods, constant-specific bodies.
- [ ] They are inherently singletons and serialization safe, which makes them the best Singleton implementation.
- [ ] `EnumMap` and `EnumSet` are extremely fast because they are backed by arrays and bit vectors.
- [ ] Enums can be used for the Strategy pattern and for state machines.

### 1.10 Generics
- [ ] They give compile-time type safety and remove casts.
- [ ] **Type erasure**: generic type info is removed at runtime. So there's no `new T()`, no `T[]`, no `instanceof List<String>`, and no overloading on `List<String>` vs `List<Integer>`.
- [ ] Bounded types: `<T extends Comparable<T>>`.
- [ ] **PECS** — *Producer Extends, Consumer Super*: `List<? extends Number>` is for reading, `List<? super Integer>` is for writing.
- [ ] `List<Object>` is NOT a supertype of `List<String>` (invariance). Arrays are covariant, which leads to `ArrayStoreException`.
- [ ] Generic methods: `public static <T> T first(List<T> l)`.
- ❓ Explain `Collections.copy(List<? super T> dest, List<? extends T> src)`.

### 1.11 Annotations & Reflection
- [ ] Retention: `SOURCE` (Lombok, @Override), `CLASS`, `RUNTIME` (Spring, JPA).
- [ ] Target: TYPE, METHOD, FIELD, PARAMETER, and so on. Other meta-annotations: `@Inherited`, `@Repeatable`, `@Documented`.
- [ ] Reflection: `Class.forName`, `getDeclaredMethods`, `setAccessible`, `Method.invoke`. It's slow and breaks encapsulation, but it powers every framework.
- [ ] `MethodHandle` and `VarHandle` are faster, type-safe alternatives.
- [ ] Dynamic proxies (`java.lang.reflect.Proxy`) work for interfaces only. CGLIB/ByteBuddy work by subclassing (this is how Spring AOP works).

### 1.12 I/O and NIO
- [ ] Classic I/O: byte streams (`InputStream`) vs character streams (`Reader`), decorators (`BufferedReader`). This is the **Decorator pattern**.
- [ ] NIO.2: `Path`, `Files.readAllLines`, `Files.lines` (lazy stream), `Files.walk`, `WatchService`.
- [ ] NIO: Channels, Buffers (flip/clear/compact), Selectors (non-blocking multiplexing, the basis of Netty).
- [ ] Blocking vs non-blocking vs async I/O (`AsynchronousFileChannel`).
- [ ] Memory-mapped files (`MappedByteBuffer`) and zero-copy (`transferTo`). Kafka relies on these.

### 1.13 Serialization
- [ ] `Serializable` is a marker interface. Declare `serialVersionUID` explicitly.
- [ ] Hooks: `writeObject`/`readObject`, `readResolve` (protects a Singleton), `writeReplace` (the serialization proxy pattern).
- [ ] **Security risk**: Java deserialization attacks. Avoid native serialization and use JSON or Protobuf. Use deserialization filters (`ObjectInputFilter`) if you must.

### 1.14 JPMS (Modules)
- [ ] `module-info.java`: `requires`, `exports`, `opens` (for reflection), `provides/uses` (ServiceLoader).
- [ ] Strong encapsulation of JDK internals. Know why `--add-opens` flags show up in builds.

---

# 2. Core Java — Object-Oriented Programming

```
OOP
├── Four Pillars
│   ├── Encapsulation
│   ├── Abstraction
│   ├── Inheritance
│   └── Polymorphism (compile-time / runtime)
├── Class & Object (constructors, chaining, init blocks, order of init)
├── Abstract Class vs Interface (default, static, private methods)
├── Overloading vs Overriding (rules, covariant returns)
├── Composition vs Inheritance (favour composition)
├── Association / Aggregation / Composition (UML relationships)
├── Immutability (how to design immutable classes)
├── Static vs Dynamic Binding
├── Coupling & Cohesion
├── Marker / Functional Interfaces
└── Sealed Classes & Records (modern OOP)
```

### 2.1 The Four Pillars
- [ ] **Encapsulation**: hide state, expose behaviour, keep invariants. It's more than getters and setters. Avoid an anemic model.
- [ ] **Abstraction**: expose *what*, hide *how* (interfaces, abstract classes).
- [ ] **Inheritance**: an IS-A relationship and code reuse. Fragile base class problem. Java has single class inheritance and multiple interface inheritance.
- [ ] **Polymorphism**:
  - [ ] Compile-time (static): method overloading.
  - [ ] Runtime (dynamic): overriding, resolved by the actual object type through the vtable / dynamic dispatch.
- ❓ Can you override static methods? (No, that's method hiding.) Private methods? (No.)

### 2.2 Constructors & Initialization Order
- [ ] Order: static blocks (parent → child, once) → instance init blocks and field initializers → constructor (parent first via `super()`).
- [ ] `this()` and `super()` must be the first statement. Java 22+ previews "statements before super" (flexible constructor bodies, final in Java 25).
- [ ] Don't call overridable methods from a constructor: the subclass fields aren't initialized yet.

### 2.3 Abstract Class vs Interface
| Aspect | Abstract Class | Interface |
|---|---|---|
| State | Instance fields | Only constants (`public static final`) |
| Constructors | Yes | No |
| Methods | Any | abstract, `default`, `static`, `private` (Java 9) |
| Inheritance | Single | Multiple |
| Use when | Shared state/base behaviour (Template Method) | Capability/contract (CAN-DO) |
- [ ] Diamond problem with default methods: the class must override and can call `A.super.method()`.

### 2.4 Overloading vs Overriding Rules
- [ ] Overriding: same signature. The return type can be covariant. Access can't be more restrictive. The method can't throw broader checked exceptions. Use `@Override`.
- [ ] Overloading resolution order: exact match → widening → boxing → varargs.

### 2.5 Composition over Inheritance
- [ ] Inheritance breaks encapsulation: subclasses depend on parent implementation details. Classic example: a `HashSet` subclass counting adds while `addAll` calls `add`.
- [ ] Prefer HAS-A with delegation. This enables Strategy, Decorator and runtime flexibility.

### 2.6 Relationships (UML)
- [ ] **Association**: a uses-a relationship (Teacher ↔ Student).
- [ ] **Aggregation**: a weak has-a; the part can exist independently (Department ◇— Teacher).
- [ ] **Composition**: a strong has-a; the part dies with the whole (House ◆— Room).
- [ ] **Dependency**: a transient use, such as a method parameter.
- [ ] **Realization / Generalization**: implements / extends.

### 2.7 Designing Immutable Classes
- [ ] Make the class `final`, all fields `private final`, and provide no setters.
- [ ] Defensive copies of mutable inputs and outputs (Dates, Lists), or use `List.copyOf()`.
- [ ] Benefits: thread safety, safe as map keys, cacheable, simpler reasoning.
- [ ] Records make this easy, but their components can still be mutable objects.

### 2.8 Records & Sealed Classes (Modern OOP)
- [ ] `record Point(int x, int y)` is a transparent data carrier with auto-generated equals, hashCode, toString and accessors. Compact constructors handle validation.
- [ ] `sealed interface Shape permits Circle, Square` restricts the hierarchy and makes pattern-matching switches exhaustive.
- [ ] Together they give you **algebraic data types** and data-oriented programming.

---

# 3. Core Java — Collections Framework

```
Collections Framework
├── Iterable → Collection
│   ├── List
│   │   ├── ArrayList (dynamic array, grow 1.5x)
│   │   ├── LinkedList (doubly linked, also Deque)
│   │   ├── Vector / Stack (legacy, synchronized)
│   │   └── CopyOnWriteArrayList (concurrent)
│   ├── Set
│   │   ├── HashSet (backed by HashMap)
│   │   ├── LinkedHashSet (insertion order)
│   │   ├── TreeSet (Red-Black tree, sorted, NavigableSet)
│   │   └── EnumSet, ConcurrentSkipListSet, CopyOnWriteArraySet
│   └── Queue / Deque
│       ├── PriorityQueue (binary heap)
│       ├── ArrayDeque (preferred stack/queue)
│       └── BlockingQueue (ArrayBlockingQueue, LinkedBlockingQueue, PriorityBlockingQueue, DelayQueue, SynchronousQueue)
├── Map (not a Collection)
│   ├── HashMap (array + linked list/tree buckets)
│   ├── LinkedHashMap (access order → LRU cache)
│   ├── TreeMap (Red-Black tree, NavigableMap)
│   ├── Hashtable (legacy)
│   ├── ConcurrentHashMap
│   ├── WeakHashMap, IdentityHashMap, EnumMap
│   └── ConcurrentSkipListMap
├── Sequenced Collections (Java 21: getFirst, getLast, reversed)
├── Utility: Collections, Arrays, List.of / Map.of (immutable)
├── Comparable vs Comparator
├── Iterator, ListIterator, Fail-fast vs Fail-safe
└── Big-O of every operation
```

### 3.1 HashMap Internals (asked in almost every interview)
- [ ] Structure: `Node<K,V>[] table`. Default capacity is 16 and the **load factor is 0.75**. It resizes (doubles) when `size > capacity × LF`.
- [ ] `put`: `hash = h ^ (h >>> 16)` → index `(n-1) & hash` → empty bucket gets a new node; otherwise walk the chain and `equals` check → replace or append.
- [ ] **Treeification (Java 8)**: when a bucket's chain is ≥ 8 *and* the table is ≥ 64, it becomes a Red-Black tree, so the worst case goes from O(n) to O(log n). It goes back to a list at ≤ 6.
- [ ] Capacity is always a power of 2, so `&` can replace `%`.
- [ ] Resizing rehashes nodes into either the same index or `index + oldCap`.
- [ ] One null key is allowed (in bucket 0). Not thread safe: in Java 7, concurrent resizes could create an infinite loop.
- [ ] Iteration order is not guaranteed.
- ❓ What happens if `hashCode()` always returns 1? What if `equals` is overridden but `hashCode` isn't?

### 3.2 ConcurrentHashMap Internals
- [ ] Java 7 used segment locking (16 segments).
- [ ] **Java 8+** uses CAS for empty bins and `synchronized` on the bin head node for collisions. Reads are lock-free (volatile reads).
- [ ] Null keys and values are **not allowed**, because `get()` returning null would be ambiguous.
- [ ] Atomic compound operations: `putIfAbsent`, `computeIfAbsent`, `merge`, `compute`.
- [ ] Iterators are weakly consistent (no ConcurrentModificationException).
- [ ] `size()` is an estimate under contention (it uses `CounterCell`s like LongAdder). Use `mappingCount()`.
- ❓ Why is `if (!map.containsKey(k)) map.put(k, v)` still a race condition with CHM?

### 3.3 Other Key Internals
- [ ] **ArrayList**: default capacity 10 (allocated lazily) and grows by 1.5×. `get` is O(1). Adding or removing in the middle is O(n). Pre-size it if you know the count.
- [ ] **LinkedList**: O(1) insert at the ends and O(n) access. It's rarely better than ArrayList in practice because of poor cache locality.
- [ ] **ArrayDeque**: a circular array, faster than Stack and LinkedList. Use it as both stack and queue. No nulls.
- [ ] **PriorityQueue**: a min-heap by default. `offer`/`poll` are O(log n) and `peek` is O(1). Iteration is NOT sorted.
- [ ] **TreeMap**: Red-Black tree with O(log n). Has `floorKey`, `ceilingKey`, `headMap`, `tailMap`, `subMap`.
- [ ] **LinkedHashMap**: `accessOrder=true` plus overriding `removeEldestEntry()` gives an **LRU cache** in about 5 lines.
- [ ] **WeakHashMap**: entries are removed when the key is only weakly reachable (good for caches and metadata).
- [ ] **IdentityHashMap**: compares with `==` instead of equals (used for graph traversal and serialization).
- [ ] **CopyOnWriteArrayList**: every write copies the array. Good for read-mostly data such as listener lists.

### 3.4 Fail-Fast vs Fail-Safe
- [ ] Fail-fast iterators (ArrayList, HashMap) throw `ConcurrentModificationException` based on `modCount`.
- [ ] Fail-safe or weakly consistent iterators (CHM, CopyOnWrite) work on a snapshot or tolerate modification.
- [ ] To remove safely while iterating, use `iterator.remove()` or `removeIf()`.

### 3.5 Comparable vs Comparator
- [ ] `Comparable.compareTo` is the natural order, defined inside the class. `Comparator` is an external, pluggable order.
- [ ] `Comparator.comparing(Person::getAge).thenComparing(Person::getName).reversed()`.
- [ ] Keep compareTo consistent with equals (TreeSet relies on compareTo, not equals).
- [ ] Never write `return a - b` in a comparator, because it can overflow. Use `Integer.compare`.

### 3.6 Immutable Collections
- [ ] `List.of()`, `Set.of()`, `Map.of()` (Java 9) are truly immutable and reject nulls.
- [ ] `Collections.unmodifiableList()` is only a **view**: changes to the underlying list still show through.
- [ ] `Stream.toList()` (Java 16) returns an unmodifiable list.

### 3.7 Big-O Cheat Sheet
| Structure | get/access | search | insert | delete |
|---|---|---|---|---|
| ArrayList | O(1) | O(n) | O(1) amortized end / O(n) mid | O(n) |
| LinkedList | O(n) | O(n) | O(1) ends | O(1) at node |
| HashMap/HashSet | O(1) avg | O(1) avg | O(1) avg | O(1) avg |
| TreeMap/TreeSet | O(log n) | O(log n) | O(log n) | O(log n) |
| PriorityQueue | O(1) peek | O(n) | O(log n) | O(log n) poll |
| ArrayDeque | O(1) ends | O(n) | O(1) ends | O(1) ends |

---

# 4. Modern Java (8 → 25)

```
Modern Java
├── Java 8 (the functional revolution)
│   ├── Lambdas & Functional Interfaces
│   ├── Method References (static, instance, constructor)
│   ├── Streams API (intermediate/terminal, lazy, parallel)
│   ├── Collectors (groupingBy, partitioningBy, toMap, joining)
│   ├── Optional
│   ├── Default & static interface methods
│   ├── java.time (LocalDate, Instant, ZonedDateTime, Duration)
│   └── CompletableFuture
├── Java 9–11: modules, List.of, var, HttpClient, String methods, jshell
├── Java 12–17 (LTS 17): switch expressions, text blocks, records, sealed classes, pattern matching instanceof, helpful NPEs
├── Java 18–21 (LTS 21): virtual threads, record patterns, pattern matching for switch, sequenced collections, generational ZGC
└── Java 22–25 (LTS 25): unnamed variables (_), stream gatherers, scoped values, structured concurrency, flexible constructor bodies, compact source files & instance main, module imports, FFM API, compact object headers
```

### 4.1 Lambdas & Functional Interfaces
- [ ] A functional interface has exactly one abstract method (`@FunctionalInterface`).
- [ ] Core interfaces in `java.util.function`:
  - [ ] `Supplier<T>` () → T · `Consumer<T>` T → void · `Function<T,R>` T → R · `Predicate<T>` T → boolean
  - [ ] `BiFunction`, `UnaryOperator`, `BinaryOperator`, and primitive specializations (`IntFunction`, `ToLongFunction`) that avoid boxing.
- [ ] Composition: `andThen`, `compose`, `Predicate.and/or/negate`.
- [ ] Lambdas compile to `invokedynamic`, not anonymous classes. `this` refers to the enclosing instance.
- [ ] Method references: `String::length`, `System.out::println`, `ArrayList::new`.

### 4.2 Streams API
- [ ] Pipeline: **source → intermediate ops (lazy) → terminal op (triggers execution)**.
- [ ] Intermediate ops: `filter`, `map`, `flatMap`, `distinct`, `sorted`, `peek`, `limit`, `skip`, `takeWhile`, `dropWhile`, `mapMulti`.
- [ ] Terminal ops: `collect`, `forEach`, `reduce`, `count`, `min/max`, `anyMatch/allMatch/noneMatch`, `findFirst/findAny`, `toList()`.
- [ ] Stateless (`map`) vs stateful (`sorted`, `distinct`) operations. Short-circuiting ops (`limit`, `anyMatch`).
- [ ] A stream can be consumed **only once**.
- [ ] **Collectors**: `toList`, `toSet`, `toMap` (watch out for duplicate keys, so pass a merge function), `groupingBy` (with downstream collectors like `counting`, `mapping`, `summingInt`), `partitioningBy`, `joining`, `teeing`, `collectingAndThen`.
- [ ] **Parallel streams** use the common ForkJoinPool. They're good for CPU-bound work on large data with cheap splitting (arrays). They're bad for I/O, small data, LinkedList, or shared mutable state.
- [ ] Avoid side effects in lambdas and keep them stateless and non-interfering.
- [ ] Stream Gatherers (Java 24, final): `Stream.gather(Gatherers.windowFixed(3))` for custom intermediate operations.
- ❓ Find the second-highest salary per department with streams. Group employees by dept → average salary.

### 4.3 Optional
- [ ] Use it as a **return type** for "maybe absent". Don't use it for fields, parameters, or collections.
- [ ] Prefer `map`, `flatMap`, `filter`, `orElse`, `orElseGet` (lazy), `orElseThrow`, `ifPresentOrElse`, `or`.
- [ ] `orElse(expensiveCall())` evaluates the call eagerly. Use `orElseGet`.
- [ ] Avoid `get()` without `isPresent()`. Better still, don't use `get()` at all.

### 4.4 java.time
- [ ] Immutable and thread safe, replacing `Date`/`Calendar`/`SimpleDateFormat` (which isn't thread safe!).
- [ ] `LocalDate/LocalTime/LocalDateTime` (no zone), `ZonedDateTime`, `OffsetDateTime`, `Instant` (UTC machine time).
- [ ] `Duration` (time-based) vs `Period` (date-based). `DateTimeFormatter` is thread safe.
- [ ] Best practice: store UTC (`Instant`) and convert to the user's zone only at display time.

### 4.5 Switch Expressions & Pattern Matching
- [ ] Arrow syntax `case X -> ...`, no fall-through, `yield` for block bodies.
- [ ] Pattern matching for instanceof: `if (obj instanceof String s && s.length() > 3)`.
- [ ] Pattern matching for switch (21): `case Circle c -> ...`, guards `case Circle c when c.r() > 10`, `case null`.
- [ ] Record patterns (21): `case Point(int x, int y) -> ...`, which can be nested.
- [ ] Unnamed variables `_` (22): `case Point(var x, _)`.
- [ ] Primitive patterns in switch/instanceof are in preview (23+).

### 4.6 Virtual Threads (Project Loom — Java 21) ⭐
- [ ] Lightweight threads managed by the JVM and **mounted on carrier threads** (a ForkJoinPool). You can run millions of them.
- [ ] When one blocks on I/O, it **unmounts** and the carrier thread is freed. This gives thread-per-request scalability without reactive code.
- [ ] Create them with `Thread.ofVirtual().start(...)` or `Executors.newVirtualThreadPerTaskExecutor()`. In Spring Boot 3.2+, set `spring.threads.virtual.enabled=true`.
- [ ] **Don't pool virtual threads.** Limit concurrency with a `Semaphore` instead.
- [ ] **Pinning**: before Java 24, a virtual thread blocking inside a `synchronized` block pinned its carrier. JEP 491 (Java 24) fixed this for synchronized. Native calls still pin.
- [ ] They help I/O-bound work, not CPU-bound work. ThreadLocals still work but are costly at scale, so prefer **Scoped Values**.
- ❓ When would virtual threads NOT help? How do they compare with WebFlux?

### 4.7 Structured Concurrency & Scoped Values
- [ ] `StructuredTaskScope` treats a group of subtasks as one unit: if one fails, the others are cancelled, and there are no leaked threads. Still preview as of Java 25.
- [ ] `ScopedValue`: immutable, bounded-lifetime context sharing, a ThreadLocal replacement (final in Java 25).

### 4.8 Other Notable Features
- [ ] `var` for locals (10). Use it when the type is obvious.
- [ ] `HttpClient` (11): HTTP/2, sync and async.
- [ ] Helpful NullPointerExceptions (14).
- [ ] Sequenced Collections (21): `getFirst()`, `getLast()`, `reversed()`.
- [ ] Foreign Function & Memory API (22): replaces JNI.
- [ ] Compact source files & instance main methods (25): `void main() { ... }`.
- [ ] Module import declarations (25): `import module java.base;`.
- [ ] Compact Object Headers (25, product feature): smaller object headers and less heap use.
- [ ] Release cadence: a new version every 6 months, with an **LTS** every 2 years (8, 11, 17, 21, 25).

---

# 5. Concurrency & Multithreading

```
Concurrency
├── Basics
│   ├── Process vs Thread
│   ├── Thread lifecycle (NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING, TERMINATED)
│   ├── Creating threads (Thread, Runnable, Callable, Executor)
│   └── Daemon threads, priorities, interrupts
├── Java Memory Model (JMM)
│   ├── Visibility, Atomicity, Ordering
│   ├── happens-before rules
│   └── volatile, final field semantics
├── Synchronization
│   ├── synchronized (object/class monitor, reentrant)
│   ├── wait / notify / notifyAll
│   ├── Locks: ReentrantLock, ReadWriteLock, StampedLock
│   └── Condition variables
├── Atomics & CAS (AtomicInteger, LongAdder, AtomicReference, ABA problem)
├── Executors Framework
│   ├── ThreadPoolExecutor (core, max, queue, rejection policy)
│   ├── ScheduledExecutorService
│   ├── ForkJoinPool & work stealing
│   └── Future, CompletableFuture
├── Synchronizers (CountDownLatch, CyclicBarrier, Semaphore, Phaser, Exchanger)
├── Concurrent Collections (CHM, BlockingQueue, CopyOnWrite, ConcurrentSkipList)
├── ThreadLocal (and memory leaks in pools)
├── Problems: Race condition, Deadlock, Livelock, Starvation, False sharing
├── Virtual Threads, Structured Concurrency (see Modern Java)
└── Reactive (Project Reactor basics — see WebFlux)
```

### 5.1 Thread Basics
- [ ] `Runnable` returns nothing. `Callable<V>` returns a value and can throw checked exceptions.
- [ ] `start()` creates a new thread; `run()` just calls the method on the current thread.
- [ ] `join()` waits for a thread to finish. `sleep()` keeps held locks. `wait()` releases the monitor.
- [ ] **Interruption is cooperative**: check `Thread.interrupted()` and handle `InterruptedException` by restoring the flag (`Thread.currentThread().interrupt()`). Never swallow it.
- [ ] Daemon threads don't keep the JVM alive.

### 5.2 Java Memory Model ⭐
- [ ] Three problems: **Atomicity** (`count++` is read-modify-write), **Visibility** (CPU caches), **Ordering** (compiler/CPU reordering).
- [ ] **happens-before** rules: program order, monitor unlock → lock, volatile write → read, `Thread.start()`, `Thread.join()`, final field freeze.
- [ ] `volatile` guarantees visibility and prevents reordering, but does **not** make compound actions atomic.
- [ ] **Double-checked locking** needs a `volatile` instance, otherwise another thread can see a partially constructed object.
- ❓ Why is `volatile int count; count++` not thread safe?

### 5.3 synchronized vs Locks
- [ ] `synchronized` is intrinsic, reentrant, and auto-released (even on exceptions). It's simple. Instance methods lock `this`; static methods lock the `Class`.
- [ ] `ReentrantLock` adds `tryLock(timeout)`, `lockInterruptibly()`, fairness, and multiple `Condition`s. Always `unlock()` in `finally`.
- [ ] `ReadWriteLock` allows many readers or one writer. Good for read-heavy data.
- [ ] `StampedLock` supports optimistic reads (no lock, then validate). It's fast but not reentrant.
- [ ] wait/notify: always call them inside synchronized and wait in a **while loop** (spurious wakeups). This is the producer-consumer classic.

### 5.4 Atomics & CAS
- [ ] Compare-And-Swap is a CPU instruction, which makes it lock-free and non-blocking. Spin-retry loops.
- [ ] `AtomicInteger.incrementAndGet()`, `updateAndGet()`, `accumulateAndGet()`.
- [ ] `LongAdder` is better than AtomicLong under high contention because it uses striped cells.
- [ ] **ABA problem**: the value goes A→B→A and CAS succeeds wrongly. Fix it with `AtomicStampedReference`.

### 5.5 Executor Framework ⭐
- [ ] `ThreadPoolExecutor(core, max, keepAlive, queue, threadFactory, rejectionHandler)`.
- [ ] Task flow: threads < core → new thread · else queue the task · queue full and threads < max → new thread · else **reject**.
- [ ] Rejection policies: `AbortPolicy` (default, throws), `CallerRunsPolicy` (back-pressure), `DiscardPolicy`, `DiscardOldestPolicy`.
- [ ] ⚠️ `Executors.newFixedThreadPool` uses an **unbounded** LinkedBlockingQueue (OOM risk). `newCachedThreadPool` has unbounded threads. Prefer an explicitly configured `ThreadPoolExecutor` in production.
- [ ] Pool sizing: CPU-bound ≈ `cores + 1`. I/O-bound ≈ `cores × (1 + wait/compute)`.
- [ ] Always `shutdown()` then `awaitTermination()`. Name your threads with a custom ThreadFactory.
- [ ] `ForkJoinPool`: divide and conquer (`RecursiveTask`) with **work stealing**. Backs parallel streams and CompletableFuture's default executor.

### 5.6 CompletableFuture ⭐
- [ ] Creation: `supplyAsync(supplier, executor)` (always pass a custom executor for I/O), `runAsync`.
- [ ] Transform: `thenApply` (map), `thenCompose` (flatMap), `thenCombine` (zip two), `thenAccept`, `thenRun`.
- [ ] Combine: `allOf`, `anyOf`.
- [ ] Errors: `exceptionally`, `handle`, `whenComplete`.
- [ ] Timeouts: `orTimeout`, `completeOnTimeout` (Java 9).
- [ ] `*Async` variants run on a different thread or executor.
- ❓ Call 3 services in parallel, combine the results, and fall back on failure.

### 5.7 Synchronizers
- [ ] `CountDownLatch`: wait for N events. One-shot.
- [ ] `CyclicBarrier`: N threads wait for each other. Reusable, with an optional barrier action.
- [ ] `Semaphore`: limits concurrent access to N permits (rate limiting, connection limits).
- [ ] `Phaser`: a flexible, multi-phase barrier with dynamic parties.
- [ ] `Exchanger`: two threads swap data.

### 5.8 ThreadLocal
- [ ] Per-thread storage, used for user context, transactions (Spring), and SimpleDateFormat.
- [ ] ⚠️ **Memory leak in thread pools**: always call `remove()` in `finally`. `InheritableThreadLocal` passes values to child threads.

### 5.9 Concurrency Problems
- [ ] **Race condition**: the result depends on timing. Fix: synchronization or atomics.
- [ ] **Deadlock**: needs all four Coffman conditions (mutual exclusion, hold and wait, no preemption, circular wait). Fixes: lock ordering, `tryLock` with timeout. Detect with a thread dump (`jstack`).
- [ ] **Livelock**: threads keep reacting to each other without making progress.
- [ ] **Starvation**: a thread never gets the resource (unfair locks).
- [ ] **False sharing**: separate variables on the same CPU cache line. Fix with `@Contended` or padding.
- ❓ Write a deadlock in 10 lines, then fix it.

### 5.10 Classic Coding Exercises
- [ ] Producer-Consumer (wait/notify, BlockingQueue)
- [ ] Print odd/even with two threads; print in sequence with N threads
- [ ] Thread-safe Singleton (enum, holder idiom, DCL)
- [ ] Your own thread pool and blocking queue
- [ ] Rate limiter (token bucket)
- [ ] Thread-safe LRU cache
- [ ] Dining philosophers, reader-writer problem

---

# 6. JVM Internals, Memory & Performance

```
JVM
├── Architecture
│   ├── Class Loader Subsystem (Loading → Linking[Verify, Prepare, Resolve] → Initialization)
│   │   └── Bootstrap → Platform → Application loaders, parent delegation model
│   ├── Runtime Data Areas
│   │   ├── Heap (Young[Eden, S0, S1], Old) — shared
│   │   ├── Metaspace (class metadata, native memory; replaced PermGen in Java 8)
│   │   ├── JVM Stack (frames: locals, operand stack) — per thread
│   │   ├── PC Register, Native Method Stack — per thread
│   │   └── Code Cache (JIT compiled code)
│   └── Execution Engine (Interpreter, JIT [C1, C2, tiered], GC)
├── Garbage Collection
│   ├── Reachability, GC Roots, Mark-Sweep-Compact
│   ├── Generational hypothesis, Minor/Major/Full GC
│   ├── Collectors: Serial, Parallel, G1 (default), ZGC, Shenandoah, Epsilon
│   └── Reference types: Strong, Soft, Weak, Phantom
├── JIT optimizations (inlining, escape analysis, loop unrolling, deoptimization)
├── Memory problems (leaks, OOM types, StackOverflow)
├── Tuning flags (-Xms, -Xmx, -Xss, -XX:MaxMetaspaceSize, GC flags)
├── Tools: jcmd, jstack, jmap, jstat, JFR + JMC, VisualVM, async-profiler, Eclipse MAT
├── Containers & JVM (UseContainerSupport, MaxRAMPercentage)
└── Startup: CDS/AppCDS, CRaC, GraalVM Native Image, Project Leyden (AOT cache)
```

### 6.1 Class Loading
- [ ] **Parent delegation**: a loader asks its parent first. This stops someone overriding `java.lang.String`.
- [ ] Loaders: Bootstrap (core, native) → Platform (formerly Extension) → Application (classpath) → custom loaders (Tomcat, OSGi, hot reload).
- [ ] Class initialization happens on first active use (`new`, static method or field access, reflection).
- [ ] `ClassNotFoundException` (dynamic load fails) vs `NoClassDefFoundError` (the class was present at compile time but is missing at runtime, or its static init failed).

### 6.2 Memory Areas
- [ ] **Heap**: objects. Young gen (Eden + 2 Survivors) and Old gen. Objects promote after surviving N GCs (tenuring threshold).
- [ ] **Stack**: one frame per method call; holds primitives and references. `StackOverflowError` usually means deep recursion.
- [ ] **Metaspace**: class metadata in native memory. Classloader leaks (redeploys) cause `OutOfMemoryError: Metaspace`.
- [ ] Escape analysis: objects that don't escape a method may be scalar-replaced, so no heap allocation happens.

### 6.3 Garbage Collection ⭐
- [ ] **GC Roots**: stack locals, static fields, active threads, JNI refs. Anything unreachable is garbage.
- [ ] Algorithms: mark-sweep (fragmentation), mark-compact, copying (Young gen).
- [ ] **Stop-The-World (STW)** pauses. Throughput vs latency vs footprint trade-off.
- [ ] Collectors:
  - [ ] **Serial**: single thread, for small heaps and clients.
  - [ ] **Parallel**: throughput focused (batch jobs).
  - [ ] **G1** (default since 9): region based with pause targets (`-XX:MaxGCPauseMillis=200`). Mixed collections.
  - [ ] **ZGC**: sub-millisecond pauses on terabyte heaps; concurrent with colored pointers and load barriers. Generational ZGC arrived in 21 and is the only mode from 23.
  - [ ] **Shenandoah**: low pause, concurrent compaction (generational mode in recent JDKs).
  - [ ] **Epsilon**: a no-op GC for testing.
- [ ] Reference types: **Soft** (cleared under memory pressure, for caches), **Weak** (cleared at the next GC; WeakHashMap), **Phantom** (post-mortem cleanup via `Cleaner`).
- [ ] Read GC logs: `-Xlog:gc*:file=gc.log`.

### 6.4 OutOfMemoryError Types
- [ ] `Java heap space`: a leak or an undersized heap. Take a heap dump (`-XX:+HeapDumpOnOutOfMemoryError`) and analyse it in Eclipse MAT (dominator tree, retained size).
- [ ] `GC overhead limit exceeded`: more than 98% of time spent in GC.
- [ ] `Metaspace`: classloader leaks.
- [ ] `unable to create native thread`: too many threads or OS limits.
- [ ] `Direct buffer memory`: NIO buffers / Netty.
- [ ] Common leak sources: static collections, unclosed resources, ThreadLocal in pools, listeners never removed, unbounded caches, inner-class references.

### 6.5 JIT Compilation
- [ ] Tiered compilation: interpreter → C1 (fast compile, light optimization) → C2 (aggressive optimization for hot code).
- [ ] Optimizations: method inlining, escape analysis, dead code elimination, loop unrolling, lock elision and coarsening.
- [ ] **Deoptimization** happens when assumptions break (for example a new subclass gets loaded).
- [ ] JVM warm-up is why microbenchmarks need **JMH**.

### 6.6 Production Diagnostics Toolkit
- [ ] `jcmd <pid> Thread.print` / `GC.heap_dump` / `VM.flags` / `JFR.start`
- [ ] Thread dumps: look for BLOCKED threads, deadlocks, and thread-pool exhaustion. Take 3 dumps 5–10 seconds apart.
- [ ] **Java Flight Recorder (JFR)**: low-overhead, always-on profiling. Analyse it in JDK Mission Control.
- [ ] **async-profiler**: CPU and allocation flame graphs.
- [ ] High CPU: `top -H` gives the thread id → convert it to hex → find it in the thread dump.
- ❓ Production app is slow and memory keeps growing. Walk through your exact steps.

### 6.7 JVM in Containers & Startup
- [ ] The JVM is container aware (since 10 / 8u191). Use `-XX:MaxRAMPercentage=75` rather than a hard-coded `-Xmx` in Kubernetes.
- [ ] Set container memory limits higher than the heap: you also need room for metaspace, thread stacks, direct memory and the code cache.
- [ ] Faster startup: AppCDS, **GraalVM Native Image** (AOT, small footprint, closed-world limits on reflection), **CRaC** (checkpoint/restore), **Project Leyden** AOT cache (JDK 24+).

---

# 7. Spring Framework Core

```
Spring Core
├── IoC (Inversion of Control) & DI (Dependency Injection)
│   ├── Constructor / Setter / Field injection
│   ├── BeanFactory vs ApplicationContext
│   └── Resolving ambiguity: @Qualifier, @Primary, by-name, List<Interface> injection
├── Bean Definition & Configuration
│   ├── XML (legacy) → Annotations (@Component, @Service, @Repository, @Controller)
│   ├── Java Config (@Configuration + @Bean), full vs lite mode
│   └── Component scanning
├── Bean Scopes (singleton, prototype, request, session, application, websocket)
├── Bean Lifecycle
│   ├── Instantiate → Populate → Aware interfaces → BeanPostProcessor(before) → @PostConstruct/afterPropertiesSet/init-method → BPP(after) → Ready → @PreDestroy/destroy
│   ├── BeanPostProcessor vs BeanFactoryPostProcessor
│   └── Circular dependencies (3-level cache; disallowed by default in Boot 2.6+)
├── AOP (Aspect-Oriented Programming)
│   ├── Aspect, Advice (Before, After, AfterReturning, AfterThrowing, Around), Pointcut, JoinPoint, Weaving
│   ├── Proxies: JDK Dynamic (interfaces) vs CGLIB (subclass)
│   └── Self-invocation problem
├── Environment, Profiles, @Value, PropertySources
├── Spring Expression Language (SpEL)
├── Application Events (ApplicationEvent, @EventListener, @TransactionalEventListener, async events)
├── Resource abstraction, MessageSource (i18n)
├── Validation (Bean Validation / JSR-380, @Valid, @Validated)
├── Transaction management (declarative @Transactional — see JPA section)
├── Caching abstraction (@Cacheable, @CacheEvict, @CachePut)
├── Scheduling (@Scheduled, @Async, TaskExecutor)
└── Spring 6 / 7 changes (Jakarta EE namespace, AOT, observability, Java 17 baseline, JSpecify null-safety, API versioning, resilience annotations in 7)
```

### 7.1 IoC & DI
- [ ] **IoC**: the framework controls object creation and wiring (Hollywood principle: "don't call us, we'll call you").
- [ ] **Constructor injection** is recommended: it allows immutability (final fields), makes dependencies explicit, is test friendly, and fails fast. No `@Autowired` is needed with a single constructor.
- [ ] Field injection is discouraged: it hides dependencies, can't use final, and is hard to test.
- [ ] `ApplicationContext` = BeanFactory + events + i18n + AOP integration + eager singleton instantiation.
- [ ] Multiple implementations: `@Primary`, `@Qualifier("x")`, inject a `List<PaymentGateway>` or `Map<String, PaymentGateway>` (great for Strategy).
- [ ] `ObjectProvider<T>` for lazy or optional dependencies.

### 7.2 Stereotypes & Configuration
- [ ] `@Component` is generic. `@Service` marks business logic. `@Repository` adds exception translation to `DataAccessException`. `@Controller`/`@RestController` are the web layer.
- [ ] `@Configuration` classes are CGLIB proxied, so calling a `@Bean` method from another returns the same singleton (full mode). `@Component` with `@Bean` methods is "lite mode" (no proxying).
- [ ] `@Import`, `@ComponentScan`, `@Conditional`.

### 7.3 Bean Scopes ⭐
- [ ] **singleton** (default): one instance per container, NOT per JVM. Must be stateless or thread safe.
- [ ] **prototype**: a new instance per request. Spring doesn't manage its destruction.
- [ ] Web scopes: request, session, application, websocket.
- [ ] ⚠️ **Prototype injected into a singleton** is created only once. Fixes: `ObjectProvider`, `@Lookup` method injection, or a scoped proxy (`proxyMode = ScopedProxyMode.TARGET_CLASS`).

### 7.4 Bean Lifecycle ⭐
1. [ ] Instantiation (constructor)
2. [ ] Populate properties (DI)
3. [ ] `BeanNameAware`, `BeanFactoryAware`, `ApplicationContextAware`
4. [ ] `BeanPostProcessor.postProcessBeforeInitialization`
5. [ ] `@PostConstruct` → `InitializingBean.afterPropertiesSet()` → custom `initMethod`
6. [ ] `BeanPostProcessor.postProcessAfterInitialization` (**AOP proxies are created here**)
7. [ ] Bean is ready → ... → shutdown: `@PreDestroy` → `DisposableBean.destroy()` → `destroyMethod`
- [ ] **BeanFactoryPostProcessor** modifies bean *definitions* before beans are created (for example `PropertySourcesPlaceholderConfigurer`).
- [ ] **BeanPostProcessor** modifies bean *instances* (for example `AutowiredAnnotationBeanPostProcessor`).
- [ ] `SmartInitializingSingleton`, `ApplicationRunner`/`CommandLineRunner`, and `ApplicationReadyEvent` are startup hooks.

### 7.5 AOP ⭐
- [ ] Concepts: **Aspect** (module), **Advice** (what and when), **Pointcut** (where), **JoinPoint** (a method execution in Spring), **Weaving** (runtime proxies in Spring; compile/load time in AspectJ).
- [ ] Pointcut expressions: `execution(* com.app.service.*.*(..))`, `@annotation(com.app.Audited)`, `within(...)`, `bean(...)`.
- [ ] `@Around` with `ProceedingJoinPoint.proceed()` is the most powerful advice (timing, retries).
- [ ] **Proxy types**: JDK dynamic proxies (interface based) vs CGLIB (subclass). Spring Boot defaults to CGLIB (`proxyTargetClass=true`).
- [ ] ⚠️ **Self-invocation**: calling `this.method()` inside the same bean bypasses the proxy, so `@Transactional`, `@Async` and `@Cacheable` silently do nothing. Fixes: move the method to another bean, self-inject, or use `AopContext.currentProxy()`.
- [ ] Final classes and methods can't be proxied by CGLIB. Private methods aren't advised.
- [ ] Used under the hood by: transactions, caching, security (`@PreAuthorize`), async, retry.

### 7.6 Events
- [ ] `ApplicationEventPublisher.publishEvent(obj)` with `@EventListener`. Listeners are synchronous by default; add `@Async` for async.
- [ ] `@TransactionalEventListener(phase = AFTER_COMMIT)` acts only after the DB commit succeeds. Useful for sending emails and messages, but it's not a replacement for the outbox pattern.

### 7.7 Async & Scheduling
- [ ] `@EnableAsync` + `@Async` on public methods called from another bean. Return `CompletableFuture`. Configure a custom `TaskExecutor` (the default before Boot 2.1 was SimpleAsyncTaskExecutor, which made a new thread per task).
- [ ] `@Scheduled(fixedRate | fixedDelay | cron)`. In clusters every instance runs the job, so use **ShedLock** or Quartz for distributed locking.

### 7.8 Caching Abstraction
- [ ] `@EnableCaching`, `@Cacheable(value="users", key="#id")`, `@CachePut`, `@CacheEvict(allEntries=true)`, `@Caching`.
- [ ] Providers: ConcurrentMap (default), **Caffeine** (local), **Redis** (distributed).
- [ ] Watch for the self-invocation problem, a missing TTL, and caching nulls.

---

# 8. Spring Boot

```
Spring Boot
├── Philosophy: convention over configuration, opinionated defaults, embedded server
├── @SpringBootApplication = @Configuration + @EnableAutoConfiguration + @ComponentScan
├── Auto-Configuration
│   ├── AutoConfiguration.imports (Boot 3) / spring.factories (Boot 2)
│   ├── @Conditional* (OnClass, OnMissingBean, OnProperty, OnWebApplication)
│   ├── Debugging: --debug, conditions report, /actuator/conditions
│   └── Writing custom starters
├── Starters (spring-boot-starter-web, -data-jpa, -security, -actuator, -test...)
├── Externalized Configuration
│   ├── application.properties / .yml, profiles (application-{profile}.yml)
│   ├── Property source order (command line > env vars > config files > defaults)
│   ├── @Value vs @ConfigurationProperties (type-safe, validated, records)
│   └── Config import (configtree, Vault, Config Server)
├── Embedded Servers (Tomcat default, Jetty, Undertow, Netty for WebFlux)
├── Actuator (health, metrics, info, env, loggers, threaddump, heapdump, prometheus)
├── Logging (SLF4J + Logback default, levels, structured logging in Boot 3.4+)
├── DevTools (restart, live reload)
├── Testing (@SpringBootTest, slices: @WebMvcTest, @DataJpaTest, @JsonTest, Testcontainers, @ServiceConnection)
├── Packaging (fat jar layout, layered jars, Buildpacks, Docker images)
├── Startup lifecycle & events (ApplicationStartingEvent ... ApplicationReadyEvent)
├── Graceful shutdown, liveness/readiness probes
├── Boot 3.x: Java 17+, Jakarta EE 9+, Observability (Micrometer Tracing), AOT & GraalVM Native, Virtual Threads, Docker Compose support, RestClient, JdbcClient
└── Boot 4.x (late 2025): Spring Framework 7, Jakarta EE 11, modularized auto-configuration, JSpecify null-safety, API versioning, HTTP service clients
```

### 8.1 How Spring Boot Starts (Know This Flow) ⭐
1. [ ] `SpringApplication.run()` → determine the app type (servlet/reactive/none)
2. [ ] Load `ApplicationContextInitializer`s and `ApplicationListener`s
3. [ ] Prepare the `Environment` (property sources, profiles)
4. [ ] Print the banner, create the `ApplicationContext`
5. [ ] Refresh the context → load bean definitions → run auto-config conditions → instantiate singletons → start the embedded web server
6. [ ] Call `ApplicationRunner` / `CommandLineRunner` beans → publish `ApplicationReadyEvent`

### 8.2 Auto-Configuration ⭐
- [ ] Boot reads candidate classes from `META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports`.
- [ ] Each one is guarded by conditions, for example: `@ConditionalOnClass(DataSource.class)` + `@ConditionalOnMissingBean` gives "configure a DataSource unless the user defined one".
- [ ] **User-defined beans win.** That's the back-off principle.
- [ ] Exclude with `@SpringBootApplication(exclude = DataSourceAutoConfiguration.class)`.
- [ ] Run with `--debug` to see the Conditions Evaluation Report.
- [ ] **Custom starter**: an autoconfigure module (`@AutoConfiguration` + conditions + `@ConfigurationProperties`) plus a starter module (dependencies only).
- ❓ How does Boot know to configure Tomcat and Jackson when you add starter-web?

### 8.3 Configuration ⭐
- [ ] `@ConfigurationProperties(prefix="app.mail")` with a record or class, `@Validated`, and relaxed binding (`app.mail.host-name` = `APP_MAIL_HOSTNAME`).
- [ ] Prefer it over scattered `@Value` lookups.
- [ ] Profiles: `spring.profiles.active=prod`, `@Profile("dev")`, profile groups, `spring.config.activate.on-profile`.
- [ ] Precedence (high → low): command-line args → `SPRING_APPLICATION_JSON` → OS env vars → profile-specific config outside the jar → inside the jar → `application.yml` → defaults.
- [ ] Secrets never go in Git. Use env vars, Vault, AWS Secrets Manager, or Kubernetes Secrets.

### 8.4 Actuator
- [ ] Endpoints: `/health` (with liveness/readiness groups), `/metrics`, `/prometheus`, `/info`, `/loggers` (change log levels at runtime!), `/env`, `/threaddump`, `/heapdump`, `/mappings`, `/beans`, `/conditions`.
- [ ] Secure them: expose only what's needed, run on a separate management port, protect with Spring Security.
- [ ] Custom `HealthIndicator`s and custom metrics with Micrometer (`Counter`, `Timer`, `Gauge`).

### 8.5 Production Readiness
- [ ] Graceful shutdown: `server.shutdown=graceful`, `spring.lifecycle.timeout-per-shutdown-phase`.
- [ ] Kubernetes probes: `/actuator/health/liveness` and `/actuator/health/readiness`.
- [ ] Connection pool (HikariCP default) sizing: `maximum-pool-size`. Start with a small pool (~10), because more is not faster.
- [ ] Tomcat thread pool: `server.tomcat.threads.max` (default 200). Or use virtual threads.
- [ ] Layered jars + Buildpacks (`./mvnw spring-boot:build-image`) for efficient Docker layers.

### 8.6 Modern Boot Features
- [ ] `RestClient` (sync, fluent, replaces RestTemplate for new code), `WebClient` (reactive), and HTTP Interface clients (`@HttpExchange`).
- [ ] `JdbcClient`: a fluent JDBC API.
- [ ] Docker Compose support and **Testcontainers `@ServiceConnection`**.
- [ ] Problem Details (RFC 9457, formerly RFC 7807) error responses: `spring.mvc.problemdetails.enabled=true`.
- [ ] GraalVM native images (`spring-boot:build-image -Pnative`), AOT processing.
- [ ] Virtual threads: `spring.threads.virtual.enabled=true`.
- [ ] Structured logging (ECS/Logstash/GELF JSON) in Boot 3.4+.

---

# 9. Spring Data, JPA & Hibernate

```
Persistence
├── JDBC basics (DataSource, Connection, PreparedStatement, connection pooling - HikariCP)
├── JPA (spec) vs Hibernate (implementation) vs Spring Data JPA (repository abstraction)
├── Entity Mapping
│   ├── @Entity, @Table, @Id, @GeneratedValue (IDENTITY, SEQUENCE, TABLE, UUID)
│   ├── @Column, @Enumerated(STRING!), @Embedded/@Embeddable, @Lob, converters
│   ├── Relationships: @OneToOne, @OneToMany, @ManyToOne, @ManyToMany
│   ├── Owning side vs inverse side (mappedBy), cascade, orphanRemoval
│   └── Inheritance: SINGLE_TABLE, JOINED, TABLE_PER_CLASS, @MappedSuperclass
├── Persistence Context & Entity Lifecycle (Transient, Managed, Detached, Removed)
│   ├── First-level cache, dirty checking, flush modes
│   └── EntityManager ops: persist, merge, remove, find, getReference, detach, refresh
├── Fetching
│   ├── LAZY vs EAGER (defaults: *ToOne = EAGER, *ToMany = LAZY)
│   ├── N+1 problem & fixes (JOIN FETCH, @EntityGraph, batch size, DTO projections)
│   └── LazyInitializationException, Open Session in View anti-pattern
├── Querying: derived queries, @Query (JPQL / native), Criteria API, Specifications, QueryDSL, projections, pagination & sorting
├── Transactions
│   ├── @Transactional (propagation, isolation, readOnly, rollbackFor, timeout)
│   ├── ACID; isolation anomalies
│   └── Pitfalls (self-invocation, checked exceptions, private methods)
├── Locking: Optimistic (@Version) vs Pessimistic (PESSIMISTIC_WRITE / SELECT FOR UPDATE)
├── Caching: L1 (session), L2 (Ehcache/Hazelcast), query cache
├── Performance: batching inserts, read-only queries, stateless sessions, connection pool sizing
├── Auditing (@CreatedDate, @LastModifiedBy, Envers)
├── Schema migration: Flyway / Liquibase (never ddl-auto=update in prod)
└── Spring Data family: JDBC, MongoDB, Redis, Elasticsearch, R2DBC
```

### 9.1 Entity Lifecycle ⭐
- [ ] **Transient** (new, unknown to the persistence context) → `persist()` → **Managed** (tracked, dirty-checked) → `detach()`/close → **Detached** → `merge()` → Managed → `remove()` → **Removed**.
- [ ] **Dirty checking**: changes to managed entities are flushed automatically at commit. No `save()` call is needed inside a transaction.
- [ ] Flush ≠ commit. Flush sends SQL; commit makes it permanent. Auto-flush happens before queries.
- [ ] `save()` in Spring Data calls `persist` when the entity is new and `merge` otherwise. `merge` returns a *new* managed instance.
- [ ] `getReference()` returns a lazy proxy without hitting the DB.

### 9.2 Relationships Best Practices ⭐
- [ ] The **owning side** holds the foreign key (usually the `@ManyToOne`). `mappedBy` marks the inverse side.
- [ ] Keep both sides in sync with helper methods (`addItem()` sets `item.setOrder(this)`).
- [ ] Prefer a **bidirectional @OneToMany with @ManyToOne**. A unidirectional @OneToMany creates a join table or extra updates.
- [ ] **Make every association LAZY**, including `@ManyToOne(fetch = LAZY)`.
- [ ] `@ManyToMany`: use a `Set`, not a List (Hibernate deletes and reinserts List collections). Better still, use an explicit join entity.
- [ ] Cascade only parent → child (aggregates). Never put `CascadeType.REMOVE` on `@ManyToMany`.
- [ ] `equals`/`hashCode` for entities: base them on a business key, or on the id with a constant hashCode. Never use auto-generated fields naively.
- [ ] `@Enumerated(EnumType.STRING)`. ORDINAL breaks when someone reorders the enum.

### 9.3 The N+1 Problem ⭐⭐
- [ ] 1 query loads N parents, then N more queries load each parent's children.
- [ ] Detect it with SQL logging (`spring.jpa.show-sql`, `hibernate.generate_statistics`), datasource-proxy, or Hypersistence Optimizer.
- [ ] Fixes:
  - [ ] `JOIN FETCH` in JPQL: `select o from Order o join fetch o.items`
  - [ ] `@EntityGraph(attributePaths = "items")`
  - [ ] `@BatchSize(size = 50)` / `hibernate.default_batch_fetch_size`
  - [ ] DTO projections (interface or record/constructor expressions) for read-only views
- [ ] ⚠️ Pagination with collection fetch joins paginates in memory (HHH90003004 warning). Paginate IDs first, then fetch.
- [ ] Fetch-joining two List collections throws `MultipleBagFetchException`.

### 9.4 LazyInitializationException & OSIV
- [ ] It happens when you access a lazy association after the session is closed.
- [ ] **Open Session In View** (`spring.jpa.open-in-view=true` by default!) keeps the session open into the view layer, which hides N+1 problems and holds DB connections longer. **Disable it** and fetch what you need in the service layer.

### 9.5 @Transactional ⭐⭐
- [ ] **Propagation**:
  - [ ] `REQUIRED` (default): join the existing transaction or create one.
  - [ ] `REQUIRES_NEW`: suspend the current one and start a new, independent transaction (audit logs).
  - [ ] `NESTED`: savepoint within the current transaction.
  - [ ] `SUPPORTS`, `NOT_SUPPORTED`, `MANDATORY`, `NEVER`.
- [ ] **Isolation**: `READ_UNCOMMITTED`, `READ_COMMITTED` (Postgres/Oracle default), `REPEATABLE_READ` (MySQL InnoDB default), `SERIALIZABLE`.
- [ ] **Rollback rules**: by default only **unchecked** exceptions and Errors roll back. Use `rollbackFor = Exception.class` for checked ones.
- [ ] `readOnly = true` skips dirty checking and flushes, and lets you route to read replicas.
- [ ] Pitfalls: self-invocation (proxy bypass), private methods ignored, catching exceptions without rethrowing, and the "UnexpectedRollbackException" when an inner REQUIRED method marked the transaction rollback-only.
- [ ] Put `@Transactional` on the **service layer**, not on controllers or repositories.
- [ ] Keep transactions short. No remote HTTP calls inside them.
- ❓ Method A (REQUIRED) calls B (REQUIRES_NEW), and B throws. What happens to A? What if A throws after B commits?

### 9.6 Isolation Anomalies
| Anomaly | Meaning | Prevented by |
|---|---|---|
| Dirty read | Reading uncommitted data | READ_COMMITTED+ |
| Non-repeatable read | Same row read twice, different values | REPEATABLE_READ+ |
| Phantom read | Same query, new rows appear | SERIALIZABLE (MySQL RR mostly prevents via gap locks) |
| Lost update | Two txns overwrite each other | Optimistic/pessimistic locking |
| Write skew | Two txns read overlapping data, write disjoint data, violate invariant | SERIALIZABLE / explicit locks |

### 9.7 Locking ⭐
- [ ] **Optimistic**: a `@Version` column; update `WHERE version = ?`. On conflict you get `OptimisticLockException`, so retry. Best for low contention.
- [ ] **Pessimistic**: `@Lock(LockModeType.PESSIMISTIC_WRITE)` turns into `SELECT ... FOR UPDATE`. Use it under high contention or for money transfers. Watch for deadlocks and set lock timeouts.
- [ ] Distributed locking across services: DB row locks, Redis (Redisson), ZooKeeper. See System Design.

### 9.8 Performance Checklist
- [ ] `hibernate.jdbc.batch_size=50`, `order_inserts=true`, `order_updates=true`. IDENTITY ids **disable insert batching**, so use SEQUENCE with a pooled optimizer.
- [ ] Use projections for reads and entities for writes.
- [ ] Use pagination (`Pageable`). For deep pages, prefer keyset (seek) pagination over OFFSET.
- [ ] Bulk updates with `@Modifying @Query` bypass the persistence context, so clear it afterwards.
- [ ] Clear the persistence context in batch loops (`em.flush(); em.clear();`).
- [ ] Manage schema with **Flyway/Liquibase**. Set `ddl-auto=validate` (or none) in production.

---

# 10. Spring Web, REST & WebFlux

```
Web Layer
├── Servlet fundamentals (Servlet, Filter, Listener, container, thread-per-request)
├── Spring MVC
│   ├── DispatcherServlet flow (HandlerMapping → HandlerAdapter → Controller → ViewResolver/MessageConverter)
│   ├── @RestController, @RequestMapping, @GetMapping..., @PathVariable, @RequestParam, @RequestBody, @RequestHeader
│   ├── ResponseEntity, HttpMessageConverters (Jackson)
│   ├── Validation (@Valid, BindingResult, groups, custom validators)
│   ├── Exception handling (@ExceptionHandler, @ControllerAdvice, ProblemDetail)
│   ├── Filters vs Interceptors (HandlerInterceptor) vs AOP
│   ├── CORS, content negotiation, file upload, async (DeferredResult, Callable, SseEmitter)
├── REST API Design
│   ├── Richardson Maturity Model, resources & nouns, HTTP methods & idempotency
│   ├── Status codes, error format, versioning, pagination, filtering, HATEOAS
│   ├── Idempotency keys, ETags/caching, rate limit headers
│   └── OpenAPI / Swagger (springdoc)
├── HTTP clients: RestTemplate (maintenance), RestClient, WebClient, @HttpExchange interfaces, OpenFeign
├── Spring WebFlux (Reactive)
│   ├── Reactive Streams (Publisher, Subscriber, Subscription, back-pressure)
│   ├── Project Reactor (Mono, Flux, operators, schedulers)
│   ├── Netty event loop, non-blocking I/O
│   └── When to use vs MVC + Virtual Threads
├── Other API styles: GraphQL (Spring for GraphQL), gRPC, WebSocket/STOMP, SSE
└── Jackson deep-dive (ObjectMapper config, @JsonIgnore, @JsonProperty, polymorphism, custom (de)serializers, dates)
```

### 10.1 DispatcherServlet Request Flow ⭐
1. [ ] The request passes through the **Filter chain** (servlet level; Spring Security lives here)
2. [ ] `DispatcherServlet` → `HandlerMapping` finds the controller method
3. [ ] `HandlerInterceptor.preHandle()`
4. [ ] `HandlerAdapter` invokes the method → argument resolvers (binding and validation)
5. [ ] The return value goes through an `HttpMessageConverter` (Jackson → JSON)
6. [ ] `postHandle()` → `afterCompletion()`
7. [ ] Exceptions go to `HandlerExceptionResolver` → `@ControllerAdvice`

### 10.2 Filter vs Interceptor vs AOP
| | Filter | Interceptor | AOP |
|---|---|---|---|
| Level | Servlet container | Spring MVC | Any Spring bean |
| Knows handler? | No | Yes | Method level |
| Use for | Security, CORS, logging, compression | Auth checks, locale, timing per handler | Transactions, auditing, cross-cutting business |

### 10.3 REST Design Principles ⭐
- [ ] Resources are nouns, plural, and hierarchical: `GET /customers/42/orders`.
- [ ] HTTP methods and **idempotency**: GET/PUT/DELETE are idempotent, POST is not, PATCH is not guaranteed to be. GET/HEAD/OPTIONS are **safe**.
- [ ] Status codes: 200, 201 (+ `Location` header), 202 (async), 204, 400, 401 (unauthenticated) vs 403 (unauthorized), 404, 409 (conflict), 412 (precondition failed), 422, 429 (rate limited), 500, 502, 503, 504.
- [ ] Errors use **RFC 9457 Problem Details** (`type`, `title`, `status`, `detail`, `instance`).
- [ ] Versioning: URI (`/v1/`), header, media type. Spring 7 has first-class API versioning. Pick one and be consistent.
- [ ] Pagination: offset/limit (simple) vs **cursor/keyset** (scalable and consistent).
- [ ] **Idempotency-Key header** for safe POST retries (payments).
- [ ] Caching: `ETag` / `If-None-Match`, `Cache-Control`. Optimistic concurrency: `If-Match`.
- [ ] Richardson Maturity Model: L0 (POX) → L1 (resources) → L2 (HTTP verbs) → L3 (HATEOAS).
- [ ] Contract first with OpenAPI.
- ❓ Design a REST API for a library system. How would you handle a long-running report generation?

### 10.4 Exception Handling
- [ ] `@RestControllerAdvice` with `@ExceptionHandler(XNotFound.class)` returning `ProblemDetail`.
- [ ] Map domain exceptions to HTTP codes in one place. Never leak stack traces.
- [ ] Extend `ResponseEntityExceptionHandler` to customise the standard MVC exceptions.

### 10.5 Reactive / WebFlux ⭐
- [ ] Reactive Streams interfaces: `Publisher`, `Subscriber`, `Subscription` (request(n) = **back-pressure**), `Processor`.
- [ ] `Mono<T>` emits 0..1 items; `Flux<T>` emits 0..N.
- [ ] Nothing happens until you **subscribe** (it's lazy, cold by default).
- [ ] Key operators: `map`, `flatMap` (async, unordered), `concatMap` (ordered), `zip`, `merge`, `switchIfEmpty`, `onErrorResume`, `retryWhen`, `timeout`, `buffer`, `window`.
- [ ] Schedulers: `boundedElastic` (for blocking calls), `parallel` (CPU). `subscribeOn` vs `publishOn`.
- [ ] **Never block** on an event-loop thread (no `block()`, JDBC, or Thread.sleep). Use BlockHound to detect it.
- [ ] Use R2DBC for reactive DB access. Context propagation goes through Reactor `Context` (not ThreadLocal).
- [ ] **When to choose WebFlux**: streaming, very high concurrency gateways (Spring Cloud Gateway), event-driven back-pressure. Otherwise **MVC + virtual threads** is simpler for most CRUD services in 2026.

### 10.6 Jackson Essentials
- [ ] `ObjectMapper` is thread safe after configuration, so reuse it.
- [ ] `FAIL_ON_UNKNOWN_PROPERTIES` (Boot disables it), `JavaTimeModule` for java.time, `@JsonInclude(NON_NULL)`.
- [ ] Polymorphism: `@JsonTypeInfo` + `@JsonSubTypes`. Avoid default typing (deserialization gadget CVEs).
- [ ] Jackson 3 (`tools.jackson` package) is the default in Spring Boot 4.

---

# 11. Spring Security

```
Spring Security
├── Architecture
│   ├── DelegatingFilterProxy → FilterChainProxy → SecurityFilterChain(s)
│   ├── Important filters (CORS, CSRF, Authentication, ExceptionTranslation, Authorization)
│   ├── SecurityContextHolder / SecurityContext / Authentication
│   └── AuthenticationManager → ProviderManager → AuthenticationProvider → UserDetailsService + PasswordEncoder
├── Authentication
│   ├── Form login, HTTP Basic, session management
│   ├── JWT (stateless), Opaque tokens
│   ├── OAuth2 / OIDC (Login, Resource Server, Client, Authorization Server)
│   ├── MFA, Passkeys/WebAuthn, One-Time Tokens (Security 6.4+)
│   └── LDAP, SAML2
├── Authorization
│   ├── URL-based (authorizeHttpRequests, requestMatchers)
│   ├── Method security (@PreAuthorize, @PostAuthorize, @Secured)
│   ├── Roles vs Authorities, role hierarchy
│   └── RBAC vs ABAC vs ReBAC
├── Password storage (BCrypt, Argon2, DelegatingPasswordEncoder)
├── CSRF, CORS, Security headers (HSTS, CSP, X-Frame-Options)
├── Session fixation, concurrency control, remember-me
└── Testing (@WithMockUser, SecurityMockMvcRequestPostProcessors)
```

### 11.1 Architecture ⭐
- [ ] The servlet `DelegatingFilterProxy` delegates to the Spring bean `FilterChainProxy`, which picks the matching `SecurityFilterChain`.
- [ ] Configure it as a `SecurityFilterChain` bean using the lambda DSL. `WebSecurityConfigurerAdapter` was removed in Security 6.
- [ ] Authentication flow: a filter extracts credentials → `AuthenticationManager.authenticate()` → a provider validates them (via `UserDetailsService` + `PasswordEncoder`) → the result is stored in `SecurityContextHolder` (ThreadLocal).
- [ ] `ExceptionTranslationFilter` maps `AuthenticationException` to 401 (AuthenticationEntryPoint) and `AccessDeniedException` to 403 (AccessDeniedHandler).

### 11.2 JWT ⭐
- [ ] Structure: `header.payload.signature` (Base64URL). Signed (JWS), optionally encrypted (JWE). **The payload is readable by anyone**, so put no secrets in it.
- [ ] Signing algorithms: HS256 (shared secret) vs RS256/ES256 (asymmetric, verify with the public key from JWKS).
- [ ] Validate the signature, `exp`, `nbf`, `iss` and `aud`. Reject `alg: none`.
- [ ] Short-lived access tokens with refresh tokens (rotation, reuse detection).
- [ ] Revocation is hard with stateless tokens: use short TTLs, a denylist, or opaque tokens with introspection.
- [ ] Browsers: storing tokens in localStorage exposes them to XSS; httpOnly cookies need CSRF protection. The **BFF pattern** is the current best practice for SPAs.

### 11.3 OAuth 2.0 / OIDC ⭐
- [ ] Roles: Resource Owner, Client, Authorization Server, Resource Server.
- [ ] Grant types: **Authorization Code + PKCE** (web, SPA, mobile), **Client Credentials** (service to service), Device Code, Refresh Token. Implicit and Password grants are **deprecated** (OAuth 2.1).
- [ ] **OIDC** = an identity layer on OAuth2. It adds the `id_token` (JWT), the `/userinfo` endpoint and discovery.
- [ ] OAuth2 is for **authorization** (delegated access); OIDC is for **authentication**.
- [ ] Spring: `oauth2Login()` (client), `oauth2ResourceServer().jwt()` (APIs), Spring Authorization Server, Keycloak, Okta, Auth0, Entra ID.
- ❓ Draw the Authorization Code + PKCE flow from memory.

### 11.4 Authorization
- [ ] `hasRole('ADMIN')` checks the authority `ROLE_ADMIN`; `hasAuthority('order:read')` checks the exact string.
- [ ] `@EnableMethodSecurity` + `@PreAuthorize("hasRole('ADMIN') or #userId == authentication.name")`.
- [ ] Models: RBAC (roles), ABAC (attributes and policies, e.g. OPA), ReBAC (relationships, e.g. Google Zanzibar / OpenFGA).

### 11.5 Web Security Basics in Spring
- [ ] **CSRF**: required for cookie or session auth. Can be disabled for stateless bearer-token APIs.
- [ ] **CORS** is a browser protection, not server security. Configure allowed origins explicitly and never use `*` with credentials.
- [ ] Passwords: `BCryptPasswordEncoder` / Argon2, and `DelegatingPasswordEncoder` (`{bcrypt}` prefix) for migrations.
- [ ] Security headers are on by default: HSTS, X-Content-Type-Options, X-Frame-Options. Add a CSP.

---

# 12. Microservices & Spring Cloud

```
Microservices
├── Fundamentals
│   ├── Monolith vs Modular Monolith vs Microservices vs Serverless
│   ├── When NOT to use microservices
│   ├── Decomposition: by business capability, by subdomain (DDD bounded contexts)
│   └── Conway's Law, team topologies
├── Communication
│   ├── Synchronous: REST, gRPC, GraphQL
│   ├── Asynchronous: messaging/events (Kafka, RabbitMQ)
│   └── API Gateway, BFF (Backend for Frontend)
├── Service Discovery (client-side: Eureka; server-side: K8s Services, Consul)
├── Configuration (Spring Cloud Config, K8s ConfigMaps, Vault)
├── Resilience (Resilience4j)
│   ├── Timeout, Retry (with backoff + jitter), Circuit Breaker, Bulkhead, Rate Limiter, Fallback
├── Data Management
│   ├── Database per service, shared DB anti-pattern
│   ├── Distributed transactions: 2PC (avoid) vs Saga (choreography / orchestration)
│   ├── Transactional Outbox, Inbox/Idempotent consumer, CDC (Debezium)
│   ├── CQRS, Event Sourcing, API Composition
├── Observability: distributed tracing (Micrometer Tracing + OpenTelemetry), correlation IDs, centralized logging
├── Security: edge auth at gateway, token propagation, mTLS, service mesh
├── Deployment: containers, K8s, service mesh (Istio/Linkerd), blue-green, canary
├── Testing: contract testing (Spring Cloud Contract, Pact), consumer-driven contracts
├── Migration: Strangler Fig, Anti-Corruption Layer, Branch by Abstraction
└── Spring Cloud stack: Gateway, Config, OpenFeign, LoadBalancer, Stream, Function, Kubernetes
```

### 12.1 Monolith vs Microservices ⭐
- [ ] Microservices benefits: independent deployment and scaling, team autonomy, tech diversity, fault isolation.
- [ ] Costs: distributed-system complexity, network latency, data consistency, operational overhead, harder debugging and testing.
- [ ] **Modular monolith** (Spring Modulith) is often the right starting point: clear module boundaries without the distributed cost.
- [ ] Rule: don't do microservices without CI/CD, observability, automated testing, and team scale to justify them.
- [ ] Distributed monolith anti-pattern: services that must be deployed together and share a DB or synchronous call chains.
- ❓ When would you merge microservices back into a monolith?

### 12.2 Communication Patterns
- [ ] Sync (REST/gRPC) is simple but creates temporal coupling and cascading failures.
- [ ] Async (events) gives loose coupling, resilience and scalability, at the cost of eventual consistency and complexity.
- [ ] **gRPC**: HTTP/2, Protobuf, streaming, strongly typed contracts. Great for internal service-to-service calls.
- [ ] **API Gateway**: routing, auth, rate limiting, aggregation, SSL termination (Spring Cloud Gateway, Kong, AWS API GW).
- [ ] **BFF**: a separate gateway per client type (web, mobile).

### 12.3 Resilience Patterns ⭐⭐
- [ ] **Timeout**: every remote call needs connect and read timeouts. A missing timeout means threads hang and the failure cascades.
- [ ] **Retry**: only for idempotent operations, with **exponential backoff + jitter**, and capped. Beware retry storms; use a retry budget.
- [ ] **Circuit Breaker**: states CLOSED → (failure rate > threshold) → OPEN (fail fast) → wait → HALF_OPEN (trial calls) → CLOSED/OPEN.
- [ ] **Bulkhead**: isolate resources (separate thread pools or semaphores per dependency) so one slow dependency can't starve everything.
- [ ] **Rate Limiter**: protect yourself and downstream services.
- [ ] **Fallback**: cached or default response, graceful degradation.
- [ ] Ordering in Resilience4j: Retry( CircuitBreaker( RateLimiter( TimeLimiter( Bulkhead( call ) ) ) ) ).
- ❓ How do you prevent a slow payment service from bringing down the order service?

### 12.4 Distributed Data ⭐⭐
- [ ] **Database per service** keeps services loosely coupled. Cross-service queries use API composition or CQRS read models.
- [ ] **2PC** (two-phase commit): blocking, coordinator is a single point of failure, poor availability. Avoid it in microservices.
- [ ] **Saga**: a sequence of local transactions, each with a **compensating transaction**.
  - [ ] *Choreography*: services react to each other's events. Decentralized and simple for 2–3 steps, but hard to trace.
  - [ ] *Orchestration*: a central orchestrator (Temporal, Camunda, a custom state machine). Clearer for complex flows.
  - [ ] Sagas have no isolation, so handle anomalies with semantic locks, commutative updates, and re-reading values.
- [ ] **Transactional Outbox** ⭐: write business data and the event to an outbox table in the *same local transaction*. A relay (poller or CDC/Debezium) then publishes to Kafka. This solves the **dual-write problem**.
- [ ] **Idempotent Consumer / Inbox**: store processed message IDs and dedupe, because delivery is at-least-once.
- [ ] **CDC (Change Data Capture)**: Debezium reads the DB transaction log and streams changes.
- ❓ Order service saves the order then publishes an event, and the publish fails. What now? (→ Outbox)

### 12.5 Service Discovery & Load Balancing
- [ ] Client-side discovery (Eureka + Spring Cloud LoadBalancer) vs server-side (Kubernetes Service/DNS, AWS ALB).
- [ ] On Kubernetes you usually don't need Eureka: K8s Services and DNS handle discovery.
- [ ] Load-balancing algorithms: round robin, least connections, weighted, consistent hashing, power of two choices.

### 12.6 Service Mesh
- [ ] A sidecar or ambient proxy (Envoy) handles mTLS, retries, timeouts, traffic shifting and telemetry, outside the application code.
- [ ] Istio, Linkerd. Trade-off: operational complexity.

### 12.7 Migration Patterns
- [ ] **Strangler Fig**: gradually route features from the monolith to new services behind a facade or gateway.
- [ ] **Anti-Corruption Layer**: a translation layer that protects the new domain model from a legacy model.
- [ ] **Branch by Abstraction**, **Parallel Run**, feature toggles.

### 12.8 Twelve-Factor App (checklist)
- [ ] 1 Codebase · 2 Dependencies · 3 Config in env · 4 Backing services as attached resources · 5 Build/release/run · 6 Stateless processes · 7 Port binding · 8 Concurrency · 9 Disposability · 10 Dev/prod parity · 11 Logs as event streams · 12 Admin processes

---

# 13. Data Structures & Algorithms (DSA)

```
DSA
├── Foundations
│   ├── Time & Space Complexity (Big-O, Θ, Ω), amortized analysis
│   ├── Recursion (base case, call stack, recursion tree), Master theorem
│   └── Bit manipulation
├── Linear Data Structures
│   ├── Array, Dynamic Array, Strings
│   ├── Linked List (singly, doubly, circular)
│   ├── Stack, Queue, Deque, Monotonic Stack/Queue
│   └── Hash Table (hashing, collisions: chaining, open addressing)
├── Non-Linear Data Structures
│   ├── Trees (Binary Tree, BST, AVL, Red-Black, B-Tree/B+Tree, N-ary)
│   ├── Heap / Priority Queue
│   ├── Trie (prefix tree)
│   ├── Segment Tree, Fenwick Tree (BIT)
│   ├── Graphs (adjacency list/matrix, directed/undirected, weighted)
│   └── Disjoint Set Union (Union-Find)
├── Probabilistic DS: Bloom Filter, Count-Min Sketch, HyperLogLog, Skip List
├── Algorithms
│   ├── Sorting (Bubble, Selection, Insertion, Merge, Quick, Heap, Counting, Radix, TimSort)
│   ├── Searching (Linear, Binary Search + variants, Binary search on answer)
│   ├── Two Pointers, Sliding Window, Prefix Sum
│   ├── Recursion & Backtracking (subsets, permutations, N-Queens, Sudoku)
│   ├── Divide & Conquer
│   ├── Greedy (interval scheduling, Huffman, activity selection)
│   ├── Dynamic Programming (1D, 2D, knapsack, LIS, LCS, edit distance, intervals, bitmask, trees)
│   ├── Graph algorithms (BFS, DFS, Topological Sort, Dijkstra, Bellman-Ford, Floyd-Warshall, Prim, Kruskal, Tarjan/Kosaraju SCC, bipartite)
│   └── String algorithms (KMP, Rabin-Karp, Z-algorithm, Manacher)
└── Problem-Solving Patterns (the 20 patterns that cover most interview problems)
```

### 13.1 Complexity
- [ ] Order: O(1) < O(log n) < O(√n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) < O(n!).
- [ ] Rough rule for 1 second: n ≤ 10⁸ → O(n); n ≤ 10⁶ → O(n log n); n ≤ 10⁴ → O(n²); n ≤ 20 → O(2ⁿ).
- [ ] Amortized analysis: dynamic array append is O(1) amortized.
- [ ] Space complexity includes the recursion stack.
- [ ] Master theorem: T(n) = aT(n/b) + f(n) (e.g. merge sort gives O(n log n)).

### 13.2 Linear Structures
- [ ] **Arrays/Strings**: in-place reversal, rotation, Kadane's algorithm (max subarray), Dutch national flag.
- [ ] **Linked List**: reverse (iterative and recursive), detect a cycle (Floyd's tortoise and hare), find the middle, merge two sorted lists, remove the Nth node from the end, LRU cache (HashMap + DLL).
- [ ] **Stack**: valid parentheses, min stack, evaluate RPN, **monotonic stack** (next greater element, largest rectangle in a histogram, daily temperatures).
- [ ] **Queue**: BFS, sliding window maximum (monotonic deque), queue via two stacks.
- [ ] **Hashing**: two sum, group anagrams, longest consecutive sequence, subarray sum equals K (prefix sum + map).

### 13.3 Trees ⭐
- [ ] Traversals: preorder, inorder (sorted for a BST), postorder, level-order (BFS). Know iterative versions too.
- [ ] Problems: height or diameter, balanced check, LCA, path sum, serialize/deserialize, validate a BST, kth smallest, right-side view, zigzag, build a tree from traversals.
- [ ] **BST** operations are O(h): O(log n) when balanced, O(n) when skewed.
- [ ] **Self-balancing trees**: AVL (strict balance, faster lookups) vs Red-Black (fewer rotations; used in TreeMap and HashMap buckets).
- [ ] **B-Tree / B+Tree**: wide, shallow trees used by database indexes and file systems. B+Tree keeps data in the leaves, and the linked leaves make range scans fast.
- [ ] **Heap**: complete binary tree stored in an array (children at 2i+1 and 2i+2). Heapify is O(n). Problems: top-K elements, Kth largest, merge K sorted lists, median of a stream (two heaps).
- [ ] **Trie**: autocomplete, word search II, prefix counting.
- [ ] **Segment tree / Fenwick tree**: range queries with point updates in O(log n).

### 13.4 Graphs ⭐
- [ ] Representations: adjacency list (sparse) vs matrix (dense).
- [ ] **BFS**: shortest path in unweighted graphs, level order, multi-source BFS (rotting oranges).
- [ ] **DFS**: connected components, cycle detection, flood fill, number of islands.
- [ ] **Topological sort**: Kahn's algorithm (BFS on in-degrees) or DFS. Used for course schedule, build order, and dependency resolution.
- [ ] **Dijkstra**: non-negative weights, PQ, O((V+E) log V). **Bellman-Ford**: handles negative weights and detects negative cycles. **Floyd-Warshall**: all pairs, O(V³).
- [ ] **MST**: Kruskal (sort edges + Union-Find), Prim (PQ).
- [ ] **Union-Find**: path compression + union by rank gives near-O(1). Redundant connection, accounts merge, number of provinces.
- [ ] SCC (Tarjan/Kosaraju), bridges and articulation points, bipartite check (2-coloring), A* search.

### 13.5 Dynamic Programming ⭐
- [ ] Ingredients: **optimal substructure** + **overlapping subproblems**.
- [ ] Approaches: top-down (memoized recursion) → bottom-up (tabulation) → space optimization.
- [ ] Framework: define the state → recurrence → base case → order of computation → answer.
- [ ] Classic families:
  - [ ] 1D: climbing stairs, house robber, decode ways, coin change, word break
  - [ ] 2D grid: unique paths, minimum path sum, maximal square
  - [ ] Knapsack: 0/1, unbounded, subset sum, partition equal subset
  - [ ] Subsequences: LIS (O(n log n) with patience sorting), LCS, edit distance, longest palindromic subsequence
  - [ ] Intervals: matrix chain multiplication, burst balloons
  - [ ] Stocks: buy/sell with cooldown and fees (state machine DP)
  - [ ] Bitmask DP (TSP), DP on trees, digit DP

### 13.6 Sorting
| Algorithm | Best | Avg | Worst | Space | Stable |
|---|---|---|---|---|---|
| Bubble / Insertion | O(n) | O(n²) | O(n²) | O(1) | Yes |
| Selection | O(n²) | O(n²) | O(n²) | O(1) | No |
| Merge | O(n log n) | O(n log n) | O(n log n) | O(n) | Yes |
| Quick | O(n log n) | O(n log n) | O(n²) | O(log n) | No |
| Heap | O(n log n) | O(n log n) | O(n log n) | O(1) | No |
| Counting / Radix | O(n+k) | O(n+k) | O(n+k) | O(n+k) | Yes |
- [ ] Java: `Arrays.sort(int[])` uses **Dual-Pivot Quicksort**. `Arrays.sort(Object[])` and `Collections.sort` use **TimSort** (stable, adaptive).

### 13.7 The Problem-Solving Patterns ⭐⭐
- [ ] 1. **Two Pointers**: pair sums, 3Sum, container with most water, remove duplicates
- [ ] 2. **Sliding Window** (fixed or variable): longest substring without repeats, minimum window substring
- [ ] 3. **Fast & Slow Pointers**: cycle detection, happy number, middle of a list
- [ ] 4. **Merge Intervals**: merge, insert, meeting rooms
- [ ] 5. **Cyclic Sort**: missing or duplicate numbers in the range 1..n
- [ ] 6. **In-place Linked List Reversal**
- [ ] 7. **Tree BFS**
- [ ] 8. **Tree DFS**
- [ ] 9. **Two Heaps**: median of a stream, scheduling
- [ ] 10. **Subsets / Backtracking**: permutations, combinations, combination sum
- [ ] 11. **Modified Binary Search**: rotated array, first/last position, **binary search on the answer** (Koko eating bananas)
- [ ] 12. **Top-K Elements** (heap / quickselect)
- [ ] 13. **K-way Merge**
- [ ] 14. **Topological Sort**
- [ ] 15. **Monotonic Stack**
- [ ] 16. **Prefix Sum + HashMap**
- [ ] 17. **Union-Find**
- [ ] 18. **Trie**
- [ ] 19. **Greedy**: jump game, gas station, interval scheduling
- [ ] 20. **Dynamic Programming** (see the families above)
- [ ] Recommended practice lists: **Blind 75 → NeetCode 150 → Grind 169**. Do them in Java and say the complexity out loud.

### 13.8 Probabilistic / System-Design Data Structures
- [ ] **Bloom filter**: "definitely not / maybe yes" membership. Used for cache-penetration protection and DB lookups (Cassandra, HBase).
- [ ] **Count-Min Sketch**: approximate frequencies (heavy hitters).
- [ ] **HyperLogLog**: approximate count of distinct items (Redis `PFCOUNT`).
- [ ] **Skip list**: probabilistic balanced structure (Redis sorted sets, ConcurrentSkipListMap).
- [ ] **Consistent hashing ring**, **Merkle tree** (anti-entropy, Git, blockchains), **LSM tree** (write-optimized storage), **Geohash / Quadtree** (location queries).

---

# 14. Low-Level Design (LLD)

```
LLD
├── Process: requirements → use cases → entities/classes → relationships → APIs/methods → patterns → code → edge cases & concurrency
├── UML: Class diagram, Sequence diagram, Activity/State diagram, Use-case diagram
├── Principles applied: SOLID, composition, encapsulation, interfaces
├── Patterns applied: Strategy, State, Factory, Observer, Builder, Singleton, Command, Chain of Responsibility
└── Classic case studies (practice each in Java, ~45 min)
    ├── Parking Lot · Elevator System · Vending Machine · ATM
    ├── Library Management · Hotel Booking · Movie Ticket Booking (BookMyShow, seat locking)
    ├── Splitwise · Snake & Ladder · Tic-Tac-Toe · Chess
    ├── LRU/LFU Cache · Rate Limiter · Logger framework · Pub-Sub / Message Queue
    ├── Food Delivery (order state machine) · Ride Sharing (Uber matching)
    ├── Online Shopping Cart & Discount engine · Payment Gateway · Notification Service
    ├── In-memory Key-Value Store · File System · Task Scheduler · Job Scheduler (cron)
    └── Stack Overflow · Meeting Room Scheduler · Inventory Management
```

### 14.1 LLD Interview Approach
- [ ] 1. **Clarify requirements** (functional, non-functional, scope out extras). Ask about concurrency.
- [ ] 2. **Identify entities** (nouns) and **behaviours** (verbs).
- [ ] 3. Draw the **class diagram**: relationships (IS-A, HAS-A), multiplicity.
- [ ] 4. Define **interfaces** first, then implementations.
- [ ] 5. Apply **patterns** where they remove `if-else` chains or tight coupling. Don't force them.
- [ ] 6. Write clean code: enums for states, immutability, validation, custom exceptions.
- [ ] 7. Handle **concurrency** (seat booking → locks, CHM, optimistic locking) and edge cases.
- [ ] 8. Discuss **extensibility**: "how would you add X?" Show the Open/Closed principle.

### 14.2 Common Pattern Mapping in LLD
| Problem element | Pattern |
|---|---|
| Different pricing / payment / parking strategy | Strategy |
| Order / elevator / vending machine states | State |
| Create vehicles / notifications by type | Factory / Abstract Factory |
| Notify users on events | Observer |
| Complex object creation (Pizza, HTTP request) | Builder |
| Single parking lot / config manager | Singleton (prefer DI) |
| Undo/redo, task queues | Command |
| Logger levels / approval workflow / ATM cash dispense | Chain of Responsibility |
| Add features to a coffee/pizza dynamically | Decorator |
| Integrate third-party payment APIs | Adapter |
| Tree structures (file system, org chart) | Composite |

---

# 15. System Design (HLD)

```
System Design
├── Fundamentals
│   ├── Requirements: Functional vs Non-functional (scalability, availability, latency, consistency, durability)
│   ├── Back-of-the-envelope estimation (QPS, storage, bandwidth, latency numbers)
│   ├── Scalability: vertical vs horizontal, stateless services
│   ├── Availability: nines, redundancy, failover, SPOF
│   ├── Latency vs Throughput, percentiles (p50/p95/p99)
│   └── Reliability, Durability, Maintainability, Observability
├── Distributed Systems Theory
│   ├── CAP theorem, PACELC
│   ├── Consistency models (strong, linearizable, sequential, causal, eventual, read-your-writes)
│   ├── Consensus (Paxos, Raft), leader election, quorum (R + W > N)
│   ├── Clocks (physical, Lamport, vector clocks, hybrid logical clocks), ordering
│   ├── Fallacies of distributed computing
│   ├── Failure modes (crash, omission, Byzantine), split brain, fencing tokens
│   └── Delivery semantics (at-most-once, at-least-once, exactly-once / effectively-once)
├── Building Blocks
│   ├── DNS, CDN, Load Balancer (L4/L7), Reverse Proxy, API Gateway
│   ├── Application servers (stateless), Service discovery
│   ├── Caching (client, CDN, app, distributed; strategies & eviction)
│   ├── Databases (SQL vs NoSQL), Replication, Partitioning/Sharding, Indexing
│   ├── Message Queues & Event Streams
│   ├── Object/Blob storage (S3), File systems (HDFS)
│   ├── Search (Elasticsearch/OpenSearch, inverted index)
│   ├── Rate limiter, Distributed lock, ID generator (Snowflake), Scheduler
│   ├── Consistent hashing
│   └── Monitoring/alerting
├── Data-intensive patterns: batch vs stream processing, Lambda/Kappa architecture, data lakes/warehouses
├── Communication: REST, gRPC, GraphQL, WebSockets, SSE, long polling, webhooks
├── Security in design: authN/Z, encryption at rest/in transit, secrets, zero trust
└── Classic case studies (see 15.8)
```

### 15.1 The System Design Interview Framework ⭐
- [ ] **1. Requirements (5 min)**: functional (what), non-functional (scale, latency, availability, consistency), out of scope.
- [ ] **2. Estimation (5 min)**: DAU → QPS (avg and peak), read:write ratio, storage per year, bandwidth.
- [ ] **3. API design (5 min)**: endpoints, request/response, pagination, auth.
- [ ] **4. Data model (5 min)**: entities, choice of DB with a reason, schema, keys, partition key.
- [ ] **5. High-level design (10 min)**: boxes and arrows covering client → LB → services → cache → DB → queue.
- [ ] **6. Deep dives (15 min)**: bottlenecks, scaling the hot path, failure handling, consistency, hot keys.
- [ ] **7. Wrap-up**: trade-offs, monitoring, future improvements.
- [ ] Always say **"it depends, and here's the trade-off…"**. There's no single right answer.

### 15.2 Numbers Every Engineer Should Know
- [ ] L1 cache ~1 ns · RAM ~100 ns · SSD random read ~16–100 µs · network within a datacenter ~0.5 ms · disk seek ~2–10 ms · cross-continent round trip ~150 ms.
- [ ] 1 day ≈ 86,400 s ≈ **10⁵ s**. 1M requests/day ≈ 12 QPS. 100M/day ≈ 1,200 QPS.
- [ ] Availability: 99.9% ≈ 8.76 h/year down · 99.99% ≈ 52.6 min/year · 99.999% ≈ 5.26 min/year.
- [ ] Powers of 2: 2¹⁰ ≈ 1 thousand (KB), 2²⁰ ≈ 1 million (MB), 2³⁰ ≈ 1 billion (GB), 2⁴⁰ ≈ 1 trillion (TB).
- [ ] A Postgres node handles ~10k simple QPS; Redis ~100k+ ops/s per node; Kafka partition ~10 MB/s+ (rough guides only).

### 15.3 Scalability Concepts
- [ ] **Vertical scaling** (bigger machine): simple, but has a ceiling and is a single point of failure.
- [ ] **Horizontal scaling** (more machines): needs **stateless services**, with state moved to the DB, cache, or session store.
- [ ] **Load balancers**: L4 (TCP, fast) vs L7 (HTTP aware: path routing, TLS termination). Health checks, sticky sessions (avoid them).
- [ ] **Auto-scaling** on CPU, QPS, or queue depth.
- [ ] **Read-heavy** systems: cache + read replicas + CDN. **Write-heavy**: sharding, queues to absorb spikes, LSM-based stores, batching.

### 15.4 Distributed Systems Theory ⭐⭐
- [ ] **CAP**: when a network **P**artition happens, choose **C**onsistency or **A**vailability. CP: HBase, ZooKeeper, etcd. AP: Cassandra, DynamoDB (configurable).
- [ ] **PACELC**: if there's a Partition, choose A or C; **E**lse, choose Latency or Consistency.
- [ ] **Consistency models**: linearizable (strongest) > sequential > causal > read-your-writes / monotonic reads > eventual.
- [ ] **Quorum**: N replicas, write to W, read from R. **R + W > N** gives strong reads (e.g. N=3, W=2, R=2).
- [ ] **Consensus (Raft)**: leader election, log replication, needs a majority. Used by etcd, Consul, and Kafka KRaft.
- [ ] **Clocks**: wall clocks drift (NTP), so don't order events by timestamp across machines. Lamport clocks give a total order consistent with causality; vector clocks detect concurrency.
- [ ] **Split brain**: two leaders. Prevent it with quorums and **fencing tokens**.
- [ ] **Exactly-once** is really "at-least-once delivery + idempotent processing" (or transactional processing like Kafka EOS).
- [ ] **Fallacies**: the network is reliable, latency is zero, bandwidth is infinite, the network is secure, topology doesn't change, there's one administrator, transport cost is zero, the network is homogeneous.

### 15.5 Caching ⭐⭐
- [ ] Layers: browser → CDN → API gateway → application (local Caffeine) → distributed (Redis) → DB buffer pool.
- [ ] **Strategies**:
  - [ ] **Cache-aside (lazy loading)**: the app reads the cache; on a miss it reads the DB and fills the cache. The most common.
  - [ ] **Read-through**: the cache loads from the DB itself.
  - [ ] **Write-through**: write the cache and DB synchronously. Consistent, slower writes.
  - [ ] **Write-behind (write-back)**: write the cache, flush to the DB asynchronously. Fast, risk of data loss.
  - [ ] **Write-around**: write the DB only; the cache fills on read.
- [ ] **Eviction**: LRU, LFU, FIFO, TTL. Redis supports `allkeys-lru`, `volatile-ttl` and others.
- [ ] **Problems**:
  - [ ] **Cache stampede / thundering herd**: a hot key expires and many requests hit the DB. Fixes: a lock or single-flight, early probabilistic refresh, stale-while-revalidate.
  - [ ] **Cache penetration**: queries for non-existent keys. Fixes: cache nulls, Bloom filter.
  - [ ] **Cache avalanche**: many keys expire at once. Fix: add jitter to TTLs.
  - [ ] **Hot keys**: replicate the key, add a local cache layer, shard the key.
  - [ ] **Consistency**: invalidate on write (delete rather than update), delayed double delete, or CDC-driven invalidation.
- ❓ Why delete the cache entry rather than update it on write?

### 15.6 Database Scaling ⭐⭐
- [ ] **Replication**:
  - [ ] Leader-follower (master-slave): writes go to the leader, reads to followers. Replication lag means you need read-your-writes handling.
  - [ ] Multi-leader: multi-region writes, conflict resolution (LWW, CRDTs).
  - [ ] Leaderless (Dynamo style): quorums, read repair, hinted handoff.
  - [ ] Sync vs async replication: durability vs latency.
- [ ] **Partitioning / sharding**:
  - [ ] Range based (hot spots possible), hash based (even spread, poor range queries), directory/lookup based, geo based.
  - [ ] **Consistent hashing** with virtual nodes minimizes data movement when nodes are added or removed.
  - [ ] Challenges: cross-shard joins and transactions, rebalancing, hot partitions (celebrity problem), global secondary indexes.
- [ ] **Denormalization** for read performance. Materialized views.
- [ ] **Federation**: split databases by function.

### 15.7 Other Building Blocks
- [ ] **CDN**: push vs pull; static assets, video, and edge caching of APIs.
- [ ] **Unique ID generation**: UUIDv4 (random, bad for B-tree locality) → **UUIDv7 / ULID** (time ordered) → **Snowflake** (timestamp + machine ID + sequence, 64 bits) → DB ticket servers.
- [ ] **Rate limiting algorithms**: token bucket (allows bursts), leaky bucket (smooth), fixed window (boundary burst), sliding window log (accurate, memory heavy), sliding window counter (a good compromise). Distributed version: Redis + Lua.
- [ ] **Distributed lock**: Redis `SET key val NX PX` (Redlock is controversial), ZooKeeper/etcd (CP). Always use a lease (TTL) and a **fencing token**.
- [ ] **Search**: inverted index, tokenization, relevance (TF-IDF/BM25), Elasticsearch shards and replicas, syncing the search index from the DB through CDC.
- [ ] **Blob storage**: S3; pre-signed URLs; multipart upload; metadata in the DB, bytes in S3.
- [ ] **Real-time communication**: polling < long polling < SSE (server → client) < WebSockets (bidirectional). Scaling WebSockets: a connection gateway plus pub/sub (Redis or Kafka).
- [ ] **Geo/location**: geohash, quadtree, S2, Redis GEO, PostGIS.
- [ ] **Batch vs stream processing**: Spark (batch), Flink/Kafka Streams (stream). Lambda vs Kappa architecture.

### 15.8 Classic Case Studies (practice each end-to-end) ⭐
- [ ] URL Shortener (TinyURL): base62, ID generation, redirect 301 vs 302, caching, analytics
- [ ] Rate Limiter (distributed)
- [ ] Pastebin
- [ ] Key-Value Store (Dynamo): partitioning, replication, quorum, vector clocks, gossip, Merkle trees
- [ ] Unique ID Generator (Snowflake)
- [ ] News Feed / Timeline (Twitter, Instagram): fan-out on write vs read, the celebrity problem, ranking
- [ ] Chat System (WhatsApp, Slack): WebSockets, presence, message ordering, delivery receipts, offline storage
- [ ] Notification System: multi-channel, templates, retries, user preferences, dedupe
- [ ] Search Autocomplete / Typeahead: trie, top-K, caching
- [ ] Web Crawler: politeness, URL frontier, dedupe (Bloom filter), distributed crawling
- [ ] Video Streaming (YouTube, Netflix): upload pipeline, transcoding, adaptive bitrate (HLS/DASH), CDN
- [ ] File Storage & Sync (Dropbox, Google Drive): chunking, dedupe, metadata DB, sync conflicts
- [ ] Ride Sharing (Uber): location updates, geo-indexing, matching, surge pricing
- [ ] Food Delivery (Swiggy, DoorDash), Hotel / Ticket Booking (concurrency, seat holds, double-booking prevention)
- [ ] Payment System: idempotency, ledger (double-entry), reconciliation, exactly-once, PSP integration
- [ ] E-commerce (Amazon): catalog, cart, inventory reservation, order saga, flash sales
- [ ] Distributed Message Queue (Kafka design)
- [ ] Metrics / Monitoring System: time-series DB, aggregation, downsampling
- [ ] Leaderboard (Redis sorted sets), Top-K heavy hitters
- [ ] Google Docs (collaborative editing: OT vs CRDT)
- [ ] Distributed Job Scheduler / Cron
- [ ] Ad click aggregation (stream processing, exactly-once)
- [ ] LLM-powered app (RAG chatbot): vector DB, embeddings, caching, guardrails, cost/latency

---

# 16. Architecture Styles & DDD

```
Architecture
├── Architectural Styles
│   ├── Layered (N-tier: Controller → Service → Repository)
│   ├── Hexagonal (Ports & Adapters)
│   ├── Onion / Clean Architecture
│   ├── Modular Monolith (Spring Modulith)
│   ├── Microservices, Service-Oriented (SOA)
│   ├── Event-Driven Architecture (EDA)
│   ├── Serverless / FaaS
│   ├── Microkernel (plugin), Pipe-and-Filter, Space-based
│   └── Cell-based architecture
├── Patterns: CQRS, Event Sourcing, Saga, Outbox, Strangler Fig, Sidecar, Ambassador, BFF
├── Domain-Driven Design
│   ├── Strategic: Domain, Subdomains (Core/Supporting/Generic), Bounded Context, Ubiquitous Language, Context Mapping
│   └── Tactical: Entity, Value Object, Aggregate & Aggregate Root, Domain Service, Application Service, Repository, Factory, Domain Event
├── Quality Attributes & Trade-offs (ATAM), Fitness functions (ArchUnit)
├── Documentation: C4 Model, ADRs (Architecture Decision Records), arc42
└── Evolutionary architecture, technical debt management
```

### 16.1 Architecture Styles ⭐
- [ ] **Layered**: simple and familiar. Risks: the business logic leaks into the layers, and the code becomes database-centric.
- [ ] **Hexagonal (Ports & Adapters)**: the domain core is in the centre. *Ports* are interfaces; *adapters* implement them (REST, DB, Kafka). The domain has no framework dependencies, so it's testable and the infrastructure is swappable.
- [ ] **Clean / Onion**: dependencies point **inward** (Entities ← Use Cases ← Interface Adapters ← Frameworks). This is the Dependency Rule.
- [ ] **Event-Driven**: event notification vs event-carried state transfer vs event sourcing. Broker vs mediator topologies.
- [ ] **Serverless**: pay per use, auto-scaling. Cold starts, vendor lock-in, execution time limits.
- [ ] Enforce boundaries with **ArchUnit** tests or Spring Modulith verification.

### 16.2 CQRS & Event Sourcing ⭐
- [ ] **CQRS**: separate the write model (commands, normalized, consistency) from the read model (queries, denormalized, fast). Read models are updated through events, so they're eventually consistent.
- [ ] Use it when read and write workloads or models differ a lot. It's overkill for CRUD.
- [ ] **Event Sourcing**: store the *events* as the source of truth (an append-only log) rather than current state. Rebuild state by replay, and use snapshots for performance.
  - [ ] Pros: full audit trail, temporal queries, debugging, event-driven integration.
  - [ ] Cons: complexity, event schema evolution (upcasting), eventual consistency, learning curve.
  - [ ] Tools: Axon Framework, EventStoreDB, Kafka (with care).

### 16.3 Domain-Driven Design ⭐⭐
- [ ] **Ubiquitous Language**: the same terms in code, conversations, and docs.
- [ ] **Bounded Context**: a boundary within which a model is consistent ("Customer" means different things in Sales and Support). It often maps to a microservice.
- [ ] **Subdomains**: Core (competitive advantage; invest here), Supporting, Generic (buy or use SaaS).
- [ ] **Context mapping**: Partnership, Shared Kernel, Customer-Supplier, Conformist, **Anti-Corruption Layer**, Open Host Service, Published Language.
- [ ] **Entity**: has identity and a lifecycle. **Value Object**: immutable, equality by value (Money, Address). Prefer value objects.
- [ ] **Aggregate**: a consistency boundary. Only the **Aggregate Root** is referenced from outside. **One transaction modifies one aggregate.** Reference other aggregates by ID. Keep aggregates small.
- [ ] **Domain Event**: something that happened (`OrderPlaced`), named in the past tense.
- [ ] **Domain Service**: logic that doesn't belong to one entity. **Application Service**: orchestrates use cases, transactions, and security.
- [ ] **Repository**: a collection-like interface per aggregate root.
- [ ] Avoid the **Anemic Domain Model** (entities that are just getters and setters, with all logic in services).
- [ ] Event Storming is a workshop technique for discovering domains and events.

### 16.4 Documenting Architecture
- [ ] **C4 Model**: Context → Containers → Components → Code (zoom levels).
- [ ] **ADR**: Title, Status, Context, Decision, Consequences. Keep them in the repo. *A staff engineer's best friend.*
- [ ] Diagrams as code: PlantUML, Mermaid, Structurizr.

---

# 17. Databases

```
Databases
├── Relational (PostgreSQL, MySQL, Oracle)
│   ├── SQL: DDL/DML, Joins (inner, left, right, full, cross, self), subqueries, CTEs (recursive), window functions, GROUP BY/HAVING, UNION
│   ├── Normalization (1NF, 2NF, 3NF, BCNF) & Denormalization
│   ├── Keys & Constraints (PK, FK, unique, check), surrogate vs natural keys
│   ├── Indexing (B+Tree, Hash, GIN/GiST, composite, covering, partial, clustered vs non-clustered)
│   ├── Query execution: EXPLAIN / EXPLAIN ANALYZE, query planner, statistics
│   ├── Transactions: ACID, isolation levels, MVCC, locking (row/table, gap, deadlocks)
│   ├── Storage internals: pages, WAL/redo logs, buffer pool, vacuum (Postgres)
│   ├── Stored procedures, triggers, views, materialized views
│   ├── Partitioning (range, list, hash), Replication
│   └── Connection pooling (HikariCP, PgBouncer)
├── NoSQL
│   ├── Key-Value (Redis, DynamoDB)
│   ├── Document (MongoDB, Couchbase)
│   ├── Wide-Column (Cassandra, HBase, ScyllaDB)
│   ├── Graph (Neo4j)
│   ├── Time-Series (InfluxDB, TimescaleDB, Prometheus)
│   ├── Search (Elasticsearch / OpenSearch)
│   └── Vector DBs (pgvector, Pinecone, Weaviate, Milvus) — for AI/RAG
├── Storage engines: B-Tree vs LSM-Tree (memtable, SSTables, compaction)
├── Redis deep-dive (data types, persistence RDB/AOF, eviction, pub/sub, streams, cluster, sentinel, Lua)
├── Choosing a DB (decision factors)
└── NewSQL / Distributed SQL (CockroachDB, YugabyteDB, Spanner, TiDB)
```

### 17.1 SQL Must-Knows ⭐
- [ ] Logical execution order: `FROM → JOIN → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY → LIMIT`.
- [ ] **Window functions**: `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, `LAG/LEAD`, `SUM() OVER (PARTITION BY ... ORDER BY ...)`. Top-N per group and running totals.
- [ ] CTEs (`WITH`) and **recursive CTEs** (hierarchies, org charts).
- [ ] `EXISTS` vs `IN` vs `JOIN`. NULL semantics (`NOT IN` with NULLs returns nothing!). `COALESCE`.
- [ ] Classic questions: Nth highest salary, duplicates, employees earning more than their manager, consecutive days, pivots, gaps and islands.

### 17.2 Indexing ⭐⭐
- [ ] B+Tree index: O(log n) lookups; good for equality, range, ORDER BY, and prefix LIKE `'abc%'`.
- [ ] **Composite index (a, b, c)** follows the **leftmost prefix rule**: it serves `a`, `a,b`, and `a,b,c`, but not `b` alone. Put equality columns before range columns.
- [ ] **Covering index**: every column the query needs is in the index, so it's an index-only scan (`INCLUDE` in Postgres).
- [ ] **Clustered index** (InnoDB primary key = the table's physical order) vs secondary indexes (which store the PK, so lookups take two steps).
- [ ] Indexes are bypassed by: functions on the column (`WHERE LOWER(email)`, so use expression indexes), leading wildcards `'%x'`, implicit type casts, OR conditions, and low selectivity.
- [ ] Cost: indexes slow down writes and use storage. Remove unused ones.
- [ ] Partial indexes (`WHERE deleted = false`), GIN (JSONB, full-text, arrays), BRIN (huge append-only tables).
- [ ] **EXPLAIN ANALYZE**: look for Seq Scan vs Index Scan, rows estimated vs actual, nested loop vs hash join vs merge join.
- ❓ A query was fast last month and is slow now. How do you investigate?

### 17.3 Transactions & MVCC
- [ ] **ACID**: Atomicity (all or nothing, undo log), Consistency (constraints), Isolation (concurrency control), Durability (WAL, fsync).
- [ ] **MVCC**: readers don't block writers. Each transaction sees a snapshot (row versions). In Postgres, dead tuples need **VACUUM**.
- [ ] Locks: shared vs exclusive, row vs table, InnoDB gap and next-key locks, `SELECT ... FOR UPDATE SKIP LOCKED` (job queues!).
- [ ] Deadlocks: the DB detects them and aborts one transaction. Prevent them with a consistent lock order and short transactions.

### 17.4 Normalization
- [ ] 1NF: atomic values, no repeating groups. 2NF: no partial dependency on a composite key. 3NF: no transitive dependency. BCNF: every determinant is a candidate key.
- [ ] Denormalize deliberately for read performance (reporting, read models).

### 17.5 NoSQL Data Modelling
- [ ] **Model around queries**, not entities (especially Cassandra and DynamoDB).
- [ ] **Cassandra**: the partition key decides distribution and the clustering key decides sort order within a partition. Writes are cheap (LSM). Tunable consistency (ONE, QUORUM, ALL). No joins. Avoid big partitions.
- [ ] **DynamoDB**: PK + sort key, GSI/LSI, single-table design, capacity modes, DynamoDB Streams.
- [ ] **MongoDB**: embed vs reference, aggregation pipeline, indexes, replica sets, sharding, multi-document transactions (since 4.0).
- [ ] **B-Tree vs LSM-Tree**: B-Tree is read optimized with in-place updates. LSM is write optimized (memtable → SSTables → compaction) with read amplification, mitigated by Bloom filters.

### 17.6 Redis Deep-Dive ⭐
- [ ] Single-threaded command execution (I/O threads since 6), in-memory, sub-millisecond.
- [ ] Data types: String, Hash, List, Set, **Sorted Set** (leaderboards, delay queues), Bitmap, HyperLogLog, Geo, **Streams** (consumer groups), JSON, vector sets/search.
- [ ] Persistence: **RDB** (snapshots) vs **AOF** (append log, fsync policies), or both.
- [ ] HA: **Sentinel** (failover) vs **Cluster** (16384 hash slots, sharding).
- [ ] Use cases: caching, sessions, rate limiting (INCR + EXPIRE or Lua), distributed locks, pub/sub, leaderboards, queues.
- [ ] Pitfalls: big keys, hot keys, `KEYS *` in production (use `SCAN`), memory fragmentation, no TTL.
- [ ] Licensing note: Redis moved to source-available licences in 2024 and added AGPL in 2025; **Valkey** is the Linux Foundation fork.

### 17.7 Choosing a Database
| Need | Choose |
|---|---|
| Transactions, relations, complex queries | PostgreSQL / MySQL |
| Flexible schema, document-shaped data | MongoDB |
| Massive write throughput, time-ordered, multi-DC | Cassandra / ScyllaDB |
| Serverless key-value at any scale | DynamoDB |
| Caching, ephemeral fast data | Redis / Valkey |
| Full-text search, log analytics | Elasticsearch / OpenSearch |
| Relationships/graph traversals | Neo4j |
| Metrics, IoT | TimescaleDB / InfluxDB / Prometheus |
| Embeddings / semantic search | pgvector / dedicated vector DB |
| Global strong consistency SQL | Spanner / CockroachDB |

---

# 18. Messaging & Event Streaming

```
Messaging
├── Concepts
│   ├── Point-to-point (queue) vs Publish-Subscribe (topic)
│   ├── Message vs Event vs Command
│   ├── Delivery guarantees (at-most-once, at-least-once, exactly-once)
│   ├── Ordering, partitioning, idempotency, deduplication
│   ├── Dead Letter Queue (DLQ), retries, poison messages
│   └── Back-pressure, consumer lag
├── Apache Kafka
│   ├── Broker, Topic, Partition, Offset, Segment, Replication (leader/follower, ISR)
│   ├── Producer (acks, idempotence, batching, linger.ms, compression, partitioner)
│   ├── Consumer & Consumer Groups (rebalancing, offset commits, cooperative rebalancing)
│   ├── Exactly-once semantics (idempotent producer + transactions)
│   ├── Retention vs Log compaction
│   ├── KRaft (ZooKeeper removed in Kafka 4.0), Schema Registry (Avro/Protobuf)
│   ├── Kafka Streams, Kafka Connect, ksqlDB
│   └── Share groups / queues for Kafka (KIP-932)
├── RabbitMQ (AMQP: exchanges [direct, topic, fanout, headers], queues, bindings, acks, quorum queues, streams)
├── Others: ActiveMQ/Artemis, AWS SQS/SNS/Kinesis/EventBridge, Google Pub/Sub, Azure Service Bus, Pulsar, NATS
└── Spring integration: Spring Kafka (@KafkaListener, KafkaTemplate, error handlers, DLT), Spring AMQP, Spring Cloud Stream
```

### 18.1 Kafka Core ⭐⭐
- [ ] A **topic** is split into **partitions**, the unit of parallelism and ordering. **Ordering is guaranteed only within a partition.**
- [ ] Messages with the same key go to the same partition (hash of the key), giving per-entity ordering (e.g. orderId).
- [ ] **Replication factor** (usually 3). The leader handles reads and writes; followers replicate. **ISR** = in-sync replicas.
- [ ] Producer `acks`: 0 (fire and forget), 1 (leader only), **all** (all ISRs, with `min.insync.replicas=2`).
- [ ] `enable.idempotence=true` (the default since 3.0) prevents duplicates from producer retries.
- [ ] **Consumer group**: each partition goes to exactly one consumer in the group, so the maximum parallelism equals the number of partitions.
- [ ] **Offset commit**: auto (risky) vs manual. Committing after processing gives at-least-once, so make consumers **idempotent**.
- [ ] **Rebalancing**: triggered when consumers join or leave. Cooperative-sticky rebalancing reduces stop-the-world. Watch `max.poll.interval.ms`.
- [ ] **Exactly-once**: idempotent producer + transactions (`read_committed` consumers), for consume-transform-produce within Kafka.
- [ ] **Retention** (time or size) vs **log compaction** (keeps the latest value per key, which turns a topic into a changelog/table).
- [ ] Why Kafka is fast: sequential disk I/O, OS page cache, zero-copy (`sendfile`), batching, compression.
- [ ] Consumer lag monitoring (Burrow, kafka-exporter) is a key operational metric.
- ❓ How do you guarantee ordering and still scale? How do you handle a poison message?

### 18.2 Kafka vs RabbitMQ
| | Kafka | RabbitMQ |
|---|---|---|
| Model | Distributed commit log (pull) | Message broker (push) |
| Retention | Keeps messages (replayable) | Deletes on ack |
| Throughput | Very high | High |
| Routing | Simple (topic/partition) | Rich (exchanges, bindings) |
| Ordering | Per partition | Per queue |
| Best for | Event streaming, event sourcing, analytics, CDC | Task queues, complex routing, RPC, per-message acks |

### 18.3 Reliable Messaging Patterns
- [ ] Retry topics with backoff, then a **DLQ/DLT** (Spring Kafka `DefaultErrorHandler` + `DeadLetterPublishingRecoverer`, or `@RetryableTopic`).
- [ ] Idempotent consumers (dedupe table, natural idempotency, upserts).
- [ ] Outbox pattern for reliable publishing (see 12.4).
- [ ] Schema evolution: Avro or Protobuf with Schema Registry; backward and forward compatibility rules.
- [ ] Event design: thin events (ID only, consumer calls back) vs fat events (event-carried state). Include an event ID, timestamp, version, and correlation ID. CloudEvents spec.

---

# 19. Testing

```
Testing
├── Test Pyramid (Unit > Integration > E2E) / Testing Trophy
├── Unit Testing
│   ├── JUnit 5 / 6 (lifecycle, @ParameterizedTest, @Nested, assertions, extensions)
│   ├── Mockito (mock, spy, stub, verify, ArgumentCaptor, strict stubs)
│   ├── AssertJ (fluent assertions)
│   └── Test doubles: Dummy, Stub, Spy, Mock, Fake
├── Integration Testing
│   ├── Spring Boot test slices (@WebMvcTest, @DataJpaTest, @JsonTest, @RestClientTest)
│   ├── @SpringBootTest, MockMvc, WebTestClient, @MockitoBean (replaces @MockBean)
│   ├── Testcontainers (real DB, Kafka, Redis in Docker)
│   └── WireMock (stub external HTTP)
├── Contract Testing (Pact, Spring Cloud Contract)
├── E2E / UI (Selenium, Playwright, Cypress)
├── Performance Testing (JMeter, Gatling, k6; load, stress, soak, spike)
├── Microbenchmarking (JMH)
├── Mutation Testing (PIT), Code coverage (JaCoCo) — coverage ≠ quality
├── Property-based testing (jqwik), Architecture tests (ArchUnit)
├── Chaos Engineering (Chaos Monkey, Litmus, fault injection)
└── Practices: TDD (Red-Green-Refactor), BDD (Cucumber, Given-When-Then), FIRST principles, test naming
```

### 19.1 Key Points
- [ ] **FIRST**: Fast, Independent, Repeatable, Self-validating, Timely.
- [ ] Structure tests as **Arrange-Act-Assert** (Given-When-Then).
- [ ] Mock at boundaries (external systems). Don't mock what you don't own; wrap it instead. Don't mock value objects.
- [ ] **Testcontainers > H2** for integration tests: test against the real database engine.
- [ ] Use slices for speed and `@SpringBootTest` sparingly. Reuse the Spring context (watch out for `@DirtiesContext` and differing `@MockitoBean` sets, which create new contexts).
- [ ] TDD gives design feedback: hard-to-test code is a design smell.
- [ ] Flaky tests: time (inject a `Clock`), ordering, shared state, async waits (use **Awaitility**, not sleep).
- [ ] Performance testing: define SLOs first; measure p95/p99, not averages; account for coordinated omission.

---

# 20. DevOps, Build & Cloud

```
DevOps & Cloud
├── Version Control: Git (branching strategies, rebase vs merge, cherry-pick, bisect, reflog, hooks)
├── Build Tools
│   ├── Maven (lifecycle, phases, goals, scopes, dependency mgmt, BOM, plugins, profiles, multi-module)
│   └── Gradle (tasks, Kotlin DSL, build cache, incremental builds)
├── Containers: Docker (image layers, multi-stage builds, distroless, JVM in containers, docker-compose)
├── Orchestration: Kubernetes
│   ├── Pod, ReplicaSet, Deployment, StatefulSet, DaemonSet, Job/CronJob
│   ├── Service (ClusterIP, NodePort, LoadBalancer), Ingress / Gateway API
│   ├── ConfigMap, Secret, Volumes, PV/PVC
│   ├── Probes (liveness, readiness, startup), resources (requests/limits), HPA/VPA, KEDA
│   ├── Namespaces, RBAC, NetworkPolicies
│   └── Helm, Kustomize, Operators
├── CI/CD: Jenkins, GitHub Actions, GitLab CI; pipelines, quality gates (SonarQube), artifact repos (Nexus/Artifactory)
├── Deployment Strategies: Rolling, Blue-Green, Canary, Feature Flags, A/B, Shadow
├── Infrastructure as Code: Terraform/OpenTofu, CloudFormation, Pulumi; GitOps (ArgoCD, Flux)
├── Cloud (AWS-focused; know equivalents in Azure/GCP)
│   ├── Compute: EC2, ECS, EKS, Lambda, Fargate
│   ├── Storage: S3, EBS, EFS
│   ├── DB: RDS, Aurora, DynamoDB, ElastiCache
│   ├── Messaging: SQS, SNS, Kinesis, MSK, EventBridge
│   ├── Networking: VPC, subnets, security groups, NAT, Route 53, ALB/NLB, CloudFront, API Gateway
│   ├── Security: IAM (roles, policies, least privilege), KMS, Secrets Manager, Cognito
│   └── Observability: CloudWatch, X-Ray
├── Well-Architected Framework (Operational excellence, Security, Reliability, Performance, Cost, Sustainability)
├── FinOps / cost awareness
└── Platform engineering & Internal Developer Platforms (Backstage)
```

### 20.1 Git Essentials
- [ ] Branching: trunk-based development (preferred with CI/CD and feature flags) vs GitFlow (release heavy).
- [ ] `merge` (keeps history, merge commits) vs `rebase` (linear history; **never rebase shared branches**).
- [ ] Power tools: `git bisect` (find the bad commit), `git reflog` (recover lost commits), `cherry-pick`, `stash`, interactive rebase to clean up history, `git blame -w`.
- [ ] Conventional commits, small PRs, meaningful messages.

### 20.2 Maven Essentials
- [ ] Lifecycle: `validate → compile → test → package → verify → install → deploy`.
- [ ] Scopes: compile, provided, runtime, test, system, import (BOMs).
- [ ] Dependency conflicts: **nearest definition wins**. Inspect with `mvn dependency:tree`; use `<exclusions>` and `<dependencyManagement>`.
- [ ] Multi-module builds, parent POMs, the Spring Boot parent and BOM, Maven Wrapper (`mvnw`), Enforcer plugin.

### 20.3 Docker for Java
- [ ] Multi-stage builds: build with the JDK, run on a JRE or distroless image. Use **layered jars** for caching.
- [ ] Don't run as root. Pin image versions. Keep images small (Alpine/distroless; watch for musl issues).
- [ ] JVM flags: `-XX:MaxRAMPercentage=75`; set requests and limits.
- [ ] Know: image vs container, layers and caching, volumes, networks, `ENTRYPOINT` vs `CMD`, `.dockerignore`.

### 20.4 Kubernetes Essentials ⭐
- [ ] **Deployment** (stateless, rolling updates) vs **StatefulSet** (stable identity and storage: databases, Kafka).
- [ ] **Probes**: liveness (restart if dead), readiness (remove from load balancing if not ready), startup (slow-starting apps). Never make liveness depend on downstream services.
- [ ] **Requests vs limits**: CPU limits can cause throttling; a memory limit breach means OOMKilled.
- [ ] **HPA** scales on CPU or custom metrics; **KEDA** scales on events (Kafka lag).
- [ ] Graceful shutdown: SIGTERM → preStop hook → `terminationGracePeriodSeconds`.
- [ ] ConfigMaps and Secrets (base64 is not encryption; use Sealed Secrets, External Secrets, or Vault).

### 20.5 Deployment Strategies
- [ ] **Rolling**: gradually replace pods. **Blue-Green**: switch traffic between two environments (instant rollback, double cost). **Canary**: route a small percentage first and watch metrics. **Feature flags**: decouple deploy from release. **Shadow**: mirror traffic.
- [ ] Database migrations must be **backward compatible** (expand → migrate → contract) for zero-downtime deploys.

---

# 21. Observability & Production Engineering

```
Observability
├── Three Pillars: Logs, Metrics, Traces (+ Profiles, Events)
├── Logging: SLF4J/Logback/Log4j2, structured JSON logs, MDC (correlation ID), log levels, ELK/EFK, Loki
├── Metrics: Micrometer, Prometheus, Grafana; RED (Rate, Errors, Duration) & USE (Utilization, Saturation, Errors), Four Golden Signals
├── Tracing: OpenTelemetry, Micrometer Tracing, Zipkin/Jaeger/Tempo; trace, span, context propagation (W3C traceparent)
├── SLI / SLO / SLA, Error budgets
├── Alerting: symptom-based, actionable, avoid alert fatigue; on-call, runbooks
├── Incident Management: detection, triage, mitigation, RCA, blameless postmortems
├── Reliability Engineering: SRE principles, capacity planning, load shedding, graceful degradation, chaos engineering
└── Performance Engineering: profiling, latency analysis, Little's Law, Amdahl's Law, bottleneck analysis
```

### 21.1 Key Concepts ⭐
- [ ] **SLI** = a measured indicator (e.g. % of requests < 300 ms). **SLO** = the internal target (99.9%). **SLA** = the contractual promise with penalties. **Error budget** = 100% − SLO; spend it on releases.
- [ ] **Four Golden Signals**: latency, traffic, errors, saturation.
- [ ] **RED** for services, **USE** for resources.
- [ ] **Structured logging** with a correlation/trace ID in MDC across services. Never log secrets or PII.
- [ ] **OpenTelemetry** is the vendor-neutral standard (SDK + Collector + OTLP).
- [ ] Prometheus metric types: Counter, Gauge, Histogram (server-side percentiles across instances), Summary. Watch label **cardinality**.
- [ ] **Little's Law**: L = λ × W (concurrency = throughput × latency). Use it to size thread pools and connection pools.
- [ ] **Amdahl's Law**: the serial fraction limits the speedup from parallelism.
- [ ] Tail latency matters at scale: with fan-out, p99 becomes the common case. Mitigate with hedged requests and timeouts.

### 21.2 Production Debugging Playbook
- [ ] High latency → check traces (which span?) → DB slow queries, connection pool wait, GC pauses, thread pool saturation, downstream latency.
- [ ] High CPU → thread dump + profiler (flame graph) → hot loops, regex, serialization, GC.
- [ ] Memory growth → heap histogram over time (`jcmd GC.class_histogram`) → heap dump → MAT.
- [ ] Errors spike → recent deploy? config change? dependency outage? → roll back first, investigate later.
- [ ] Always: **mitigate first, root cause second.** Write a blameless postmortem with action items.

---

# 22. Application Security

```
Security
├── OWASP Top 10 (2021; 2025 edition released)
│   ├── Broken Access Control (IDOR)
│   ├── Cryptographic Failures
│   ├── Injection (SQL, NoSQL, LDAP, OS command, XSS)
│   ├── Insecure Design
│   ├── Security Misconfiguration
│   ├── Vulnerable & Outdated Components (supply chain)
│   ├── Identification & Authentication Failures
│   ├── Software & Data Integrity Failures (deserialization, CI/CD)
│   ├── Security Logging & Monitoring Failures
│   └── SSRF
├── OWASP API Security Top 10 (BOLA, broken auth, excessive data exposure, rate limiting...)
├── Cryptography basics: hashing vs encryption vs encoding, symmetric (AES-GCM) vs asymmetric (RSA, ECC), signatures, HMAC, salting, key rotation
├── TLS/HTTPS, mTLS, certificates & PKI
├── Secrets management (Vault, cloud secret managers), never in code
├── Secure SDLC: threat modelling (STRIDE), SAST, DAST, SCA (Dependabot, Snyk, OWASP Dependency-Check), SBOM
├── Zero Trust, least privilege, defence in depth
└── Compliance awareness: GDPR, PCI-DSS, HIPAA, SOC2 (data handling, encryption, auditing)
```

### 22.1 Must-Know for Java Developers ⭐
- [ ] **SQL injection**: always use `PreparedStatement` or parameterized JPQL. Never concatenate input into queries (including native queries and `ORDER BY` clauses).
- [ ] **XSS**: encode output, add a Content Security Policy, and treat all user input as untrusted.
- [ ] **IDOR / BOLA**: check that the resource belongs to the authenticated user on every request.
- [ ] **SSRF**: validate and allowlist outbound URLs. Block access to metadata IPs (169.254.169.254).
- [ ] **Deserialization**: avoid Java native serialization and Jackson default typing.
- [ ] **Log4Shell (CVE-2021-44228)**: a lesson in supply-chain risk. Keep dependencies patched; generate an SBOM.
- [ ] **Hashing ≠ encryption**: hash passwords with BCrypt/Argon2 (slow and salted), never MD5 or SHA-1. Encryption is reversible (AES-GCM).
- [ ] Mass assignment: don't bind request bodies directly to entities. Use DTOs.
- [ ] Rate limit authentication endpoints. Use generic error messages ("invalid credentials").
- [ ] **STRIDE**: Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of privilege.

---

# 23. CS Fundamentals: OS & Networking

```
CS Fundamentals
├── Operating Systems
│   ├── Process vs Thread, context switching, scheduling (round-robin, priority, CFS)
│   ├── Memory: virtual memory, paging, page faults, TLB, swapping
│   ├── Concurrency primitives: mutex, semaphore, monitor, spinlock
│   ├── Deadlock (conditions, prevention, avoidance — Banker's algorithm)
│   ├── File systems, inodes, file descriptors, page cache
│   ├── I/O models: blocking, non-blocking, multiplexing (select/poll/epoll), async (io_uring)
│   └── Linux skills: top/htop, ps, netstat/ss, lsof, strace, vmstat, iostat, df/du, grep/awk/sed, journalctl
├── Networking
│   ├── OSI (7 layers) vs TCP/IP (4 layers)
│   ├── IP, subnetting, CIDR, NAT, private ranges
│   ├── TCP (3-way handshake, 4-way teardown, flow control, congestion control, TIME_WAIT) vs UDP
│   ├── DNS resolution (recursive, authoritative, TTL, record types A/AAAA/CNAME/MX/TXT)
│   ├── HTTP/1.1 vs HTTP/2 (multiplexing, HPACK) vs HTTP/3 (QUIC over UDP)
│   ├── HTTPS / TLS 1.3 handshake, certificates, SNI
│   ├── Keep-alive, connection pooling, head-of-line blocking
│   ├── Proxies (forward vs reverse), load balancers (L4/L7)
│   └── Cookies, sessions, CORS, WebSockets
└── "What happens when you type a URL into the browser?" (end-to-end)
```

### 23.1 Key Points
- [ ] **TCP**: reliable, ordered, connection oriented, with flow control (receive window) and congestion control (slow start, CUBIC/BBR). **UDP**: fast, connectionless (DNS, video, QUIC).
- [ ] **TIME_WAIT** buildup on clients making many short connections means you should use connection pooling and keep-alive.
- [ ] **HTTP/2**: binary framing, multiplexed streams over one connection, header compression. TCP head-of-line blocking remains, which **HTTP/3/QUIC** fixes.
- [ ] **TLS 1.3**: 1-RTT handshake (0-RTT resumption), forward secrecy.
- [ ] **epoll** (Linux) is what lets Netty, Nginx and Node handle huge numbers of connections with few threads.
- [ ] **URL → page**: DNS lookup → TCP handshake → TLS handshake → HTTP request → LB → server → response → browser renders (parse HTML, CSSOM, JS, paint). Be ready to go deep on any step.

---

# 24. AI-Assisted Engineering (2026 Must-Know)

```
AI for Engineers
├── Using AI tools effectively
│   ├── AI coding assistants & agents (Claude Code, Copilot, Cursor) — prompting, reviewing, verifying
│   ├── Writing good specs/context (CLAUDE.md, ADRs) for agents
│   └── Risks: hallucination, insecure code, licence issues, over-reliance
├── LLM fundamentals
│   ├── Tokens, context window, temperature, embeddings
│   ├── Prompt engineering (system prompts, few-shot, structured output)
│   ├── Tool use / function calling, agents, MCP (Model Context Protocol)
│   └── Evaluation (evals), guardrails, cost & latency management
├── RAG (Retrieval-Augmented Generation)
│   ├── Chunking, embeddings, vector stores (pgvector), hybrid search, re-ranking
│   └── Grounding, citations, freshness
├── Java ecosystem: Spring AI (ChatClient, advisors, VectorStore, tool calling, MCP), LangChain4j
└── Designing AI features: streaming responses, caching, rate limits, PII handling, observability of LLM calls
```

### 24.1 Key Points
- [ ] Treat AI output like a junior engineer's PR: **review, test, verify**. You stay accountable for the code.
- [ ] Senior value has shifted toward problem framing, system design, code review, and verification, which this whole document covers.
- [ ] Spring AI provides a portable API across model providers (Anthropic, OpenAI, Bedrock, Ollama), plus structured output to POJOs, advisors for memory and RAG, and MCP client/server support.
- [ ] Know the RAG pipeline end-to-end: ingest → chunk → embed → store → retrieve → augment the prompt → generate → evaluate.

---

# 25. Senior/Staff Engineer Skills (Non-Technical)

```
Senior / Staff Skills
├── Technical Leadership
│   ├── Owning outcomes, not tasks
│   ├── Technical vision & roadmaps, managing tech debt
│   ├── Writing design docs / RFCs / ADRs
│   ├── Making & communicating trade-offs
│   └── Driving cross-team alignment
├── Execution
│   ├── Estimation (ranges, uncertainty, breaking down work)
│   ├── Risk identification & de-risking (spikes, prototypes)
│   ├── Incremental delivery, MVP thinking
│   └── Prioritization (impact vs effort)
├── Code Quality & Review
│   ├── Clean code, refactoring (Martin Fowler's catalog), code smells
│   ├── Giving constructive code reviews
│   └── Setting standards (linters, conventions, templates)
├── People
│   ├── Mentoring & coaching, delegation
│   ├── Communication (written > verbal at scale), presenting to execs
│   ├── Influence without authority
│   └── Conflict resolution, giving feedback
├── Business Acumen: understanding product, users, cost, metrics
├── Interviewing & hiring
└── Personal: continuous learning, reading papers/blogs, writing/speaking, open-source
```

### 25.1 Key Points
- [ ] **Staff archetypes** (Will Larson): Tech Lead, Architect, Solver, Right Hand.
- [ ] Clean code: meaningful names, small functions, one level of abstraction per function, no side effects, command-query separation, boy-scout rule.
- [ ] **Code smells**: long method, large class, feature envy, primitive obsession, shotgun surgery, divergent change, data clumps, switch statements, speculative generality, message chains.
- [ ] **Refactorings**: extract method/class, replace conditional with polymorphism, introduce parameter object, move method, replace magic number.
- [ ] Technical debt quadrant (Fowler): reckless/prudent × deliberate/inadvertent.
- [ ] Behavioural interviews: prepare **STAR** stories (Situation, Task, Action, Result) for conflict, failure, leadership, ambiguity, and influence.
- [ ] Writing a design doc: context → goals and non-goals → proposal → alternatives considered → risks → rollout plan → metrics.

---

# 26. Design Principles

```
Design Principles
├── SOLID
│   ├── S — Single Responsibility
│   ├── O — Open/Closed
│   ├── L — Liskov Substitution
│   ├── I — Interface Segregation
│   └── D — Dependency Inversion
├── DRY (Don't Repeat Yourself) — vs WET; beware wrong abstractions
├── KISS (Keep It Simple)
├── YAGNI (You Aren't Gonna Need It)
├── Composition over Inheritance
├── Law of Demeter (principle of least knowledge)
├── Tell, Don't Ask
├── Separation of Concerns
├── High Cohesion, Low Coupling
├── Encapsulate What Varies
├── Program to an Interface, not an Implementation
├── Fail Fast
├── Principle of Least Astonishment
├── Command-Query Separation (CQS)
├── GRASP (Information Expert, Creator, Controller, Low Coupling, High Cohesion, Polymorphism, Pure Fabrication, Indirection, Protected Variations)
└── Package principles (REP, CCP, CRP; ADP, SDP, SAP)
```

### 26.1 SOLID ⭐⭐
- [ ] **SRP**: a class should have **one reason to change** (one actor/stakeholder). It's about cohesion, not "do one thing".
  - Smell: `OrderService` that validates, prices, saves, emails and generates PDFs.
- [ ] **OCP**: open for extension, closed for modification. Add new behaviour through new classes (Strategy, polymorphism) instead of editing `if/else` or `switch` chains.
  - Example: a new `PaymentMethod` implementation with no changes to the `PaymentProcessor`.
- [ ] **LSP**: subtypes must be usable wherever their base type is expected without breaking correctness. Don't strengthen preconditions or weaken postconditions.
  - Classic violation: `Square extends Rectangle`. Another: `ReadOnlyList.add()` throwing UnsupportedOperationException.
- [ ] **ISP**: clients shouldn't depend on methods they don't use. Prefer small, role-specific interfaces (`Printer`, `Scanner` instead of `MultiFunctionDevice`).
- [ ] **DIP**: high-level modules depend on **abstractions**, not concretions, and the abstractions are owned by the high-level module. Spring DI is the mechanism; DIP is the principle. Hexagonal architecture is DIP at the architectural level.
- ❓ Give a real example from your own codebase of each SOLID violation and how you'd fix it.

### 26.2 Other Principles
- [ ] **DRY** is about knowledge, not just code. Duplication is cheaper than the wrong abstraction (Sandi Metz). Rule of three.
- [ ] **Law of Demeter**: avoid `a.getB().getC().doX()` train wrecks. Talk to friends, not strangers.
- [ ] **Tell, Don't Ask**: `account.withdraw(100)` rather than `if (account.getBalance() >= 100) account.setBalance(...)`.
- [ ] **Coupling** types (worst → best): content, common (global), control, stamp, data, message.
- [ ] **Cohesion** types (worst → best): coincidental, logical, temporal, procedural, communicational, sequential, functional.
- [ ] **Package principles**: Acyclic Dependencies (no cycles), Stable Dependencies (depend toward stability), Stable Abstractions (stable packages should be abstract).

---

# 27. Design Patterns

```
Design Patterns
├── GoF Creational (5)
│   ├── Singleton
│   ├── Factory Method
│   ├── Abstract Factory
│   ├── Builder
│   └── Prototype
├── GoF Structural (7)
│   ├── Adapter
│   ├── Bridge
│   ├── Composite
│   ├── Decorator
│   ├── Facade
│   ├── Flyweight
│   └── Proxy
├── GoF Behavioral (11)
│   ├── Chain of Responsibility
│   ├── Command
│   ├── Interpreter
│   ├── Iterator
│   ├── Mediator
│   ├── Memento
│   ├── Observer
│   ├── State
│   ├── Strategy
│   ├── Template Method
│   └── Visitor
├── Other OO patterns: Null Object, Object Pool, Dependency Injection, Service Locator, Specification, Value Object, Fluent Interface
├── Enterprise (PoEAA): Repository, Unit of Work, Identity Map, Data Mapper, Active Record, DTO, Service Layer, Lazy Load, Front Controller, MVC, Gateway, Registry
├── Microservice / Cloud patterns: API Gateway, BFF, Service Discovery, Circuit Breaker, Bulkhead, Retry, Saga, Outbox, CQRS, Event Sourcing, Strangler Fig, ACL, Sidecar, Ambassador, Database-per-service, Leader Election, Sharding, Throttling, Competing Consumers, Claim Check, Cache-Aside
├── Concurrency patterns: Producer-Consumer, Thread Pool, Future/Promise, Read-Write Lock, Active Object, Monitor, Balking, Guarded Suspension, Double-Checked Locking, Thread-per-message, Reactor/Proactor
├── Integration patterns (EIP): Message Channel, Router, Translator, Splitter, Aggregator, Content-Based Router, Dead Letter Channel, Idempotent Receiver (Apache Camel / Spring Integration)
└── Anti-patterns: God Object, Spaghetti Code, Golden Hammer, Lava Flow, Big Ball of Mud, Anemic Domain Model, Singleton abuse, Premature optimization, Distributed Monolith, Shared Database, Chatty services
```

> For each pattern know: **Intent → Problem it solves → Structure → Java/Spring example → When NOT to use.**

### 27.1 Creational Patterns
- [ ] **Singleton**: one instance with global access.
  - Implementations: eager, lazy synchronized, **double-checked locking with volatile**, **Bill Pugh holder idiom**, **enum** (best: reflection and serialization safe).
  - Breaking it: reflection, serialization (fix with `readResolve`), cloning, multiple classloaders.
  - In Spring, beans are singletons per container, so prefer DI over hand-written singletons (which are hard to test and hide global state).
  - JDK: `Runtime.getRuntime()`.
- [ ] **Factory Method**: subclasses or a method decide which concrete class to instantiate.
  - JDK: `Calendar.getInstance()`, `List.of()`, `NumberFormat.getInstance()`. Spring: `FactoryBean`.
- [ ] **Abstract Factory**: families of related objects (a UI toolkit for Windows vs Mac; a DB-specific DAO family).
  - JDK: `DocumentBuilderFactory`. Spring: `BeanFactory` is conceptually close.
- [ ] **Builder**: step-by-step construction of complex or immutable objects, avoiding telescoping constructors.
  - JDK: `StringBuilder`, `HttpRequest.newBuilder()`, `Stream.builder()`. Lombok `@Builder`. Spring: `UriComponentsBuilder`, `WebClient.builder()`, `MockMvcRequestBuilders`.
- [ ] **Prototype**: create objects by cloning an existing instance (expensive creation). Spring prototype scope (a related concept). Prefer copy constructors over `clone()`.

### 27.2 Structural Patterns
- [ ] **Adapter**: converts one interface into another that the client expects (wrapping a third-party payment SDK).
  - JDK: `Arrays.asList()`, `InputStreamReader` (bytes → chars). Spring: `HandlerAdapter`, `JpaVendorAdapter`.
- [ ] **Bridge**: separate the abstraction from the implementation so both can vary (Shape × Renderer; JDBC API × drivers).
- [ ] **Composite**: tree structures; treat individual objects and groups uniformly (files and folders, menus, org charts).
  - JDK: AWT/Swing `Container`. Spring: `CompositeCacheManager`.
- [ ] **Decorator**: add responsibilities dynamically by wrapping, an alternative to subclass explosion.
  - JDK: `BufferedInputStream(new FileInputStream())`, `Collections.synchronizedList()`. Spring: `BeanDefinitionDecorator`, `TransactionAwareCacheDecorator`.
- [ ] **Facade**: a simple interface over a complex subsystem.
  - Spring: `JdbcTemplate` (over raw JDBC), `RestClient`. SLF4J is a facade over logging implementations.
- [ ] **Flyweight**: share intrinsic state to save memory with many fine-grained objects.
  - JDK: `Integer.valueOf()` cache, the String pool.
- [ ] **Proxy**: a surrogate that controls access: virtual (lazy), protection, remote, caching, logging.
  - **Spring AOP, `@Transactional`, Hibernate lazy-loading proxies**, `java.lang.reflect.Proxy`.
  - Proxy vs Decorator: same structure, different intent (control access vs add behaviour).

### 27.3 Behavioral Patterns
- [ ] **Chain of Responsibility**: pass a request along handlers until one handles it.
  - **Servlet filters, Spring Security filter chain**, HandlerInterceptors, logger levels, approval workflows.
- [ ] **Command**: encapsulate a request as an object (undo/redo, queues, macros, transactions).
  - JDK: `Runnable`/`Callable`. Task queues, CQRS commands.
- [ ] **Interpreter**: a grammar and evaluator for a simple language. SpEL, regex `Pattern`, rule engines.
- [ ] **Iterator**: sequential access without exposing internals. `Iterator`, `Spliterator`, for-each.
- [ ] **Mediator**: centralize complex communication between objects (chat room, air-traffic control).
  - Spring MVC `DispatcherServlet`, event buses, `ExecutorService` (loosely).
- [ ] **Memento**: capture and restore state without breaking encapsulation (undo, editor snapshots).
- [ ] **Observer**: one-to-many dependency; subscribers are notified on change.
  - Spring `ApplicationEvent`/`@EventListener`, JavaBeans `PropertyChangeListener`, Reactive Streams, Kafka (distributed observer/pub-sub).
- [ ] **State**: behaviour changes with internal state; replaces state `switch` statements (order lifecycle, vending machine, TCP connection).
  - Spring State Machine.
- [ ] **Strategy** ⭐: a family of interchangeable algorithms selected at runtime.
  - JDK: `Comparator`. Spring: injecting a `Map<String, PaymentStrategy>`, `PasswordEncoder`, `ResourceLoader`.
  - Strategy vs State: the client picks the strategy, whereas a state transitions itself.
- [ ] **Template Method**: an algorithm skeleton in the base class with overridable steps.
  - **`JdbcTemplate`, `RestTemplate`, `AbstractController`**, `HttpServlet.service()` → `doGet()`. The modern alternative is passing callbacks or lambdas (Strategy).
- [ ] **Visitor**: add operations to a class hierarchy without modifying it (double dispatch). AST processing, `FileVisitor`. Modern Java can replace it with **sealed types + pattern-matching switch**.

### 27.4 Pattern Comparison Cheatsheet
| Confusing pair | Difference |
|---|---|
| Factory Method vs Abstract Factory | One product via inheritance vs families of products via composition |
| Builder vs Factory | Step-by-step complex construction vs one-shot creation choosing a type |
| Adapter vs Facade | Convert an interface vs simplify a subsystem |
| Decorator vs Proxy | Add behaviour vs control access |
| Strategy vs State | External choice of algorithm vs internal state-driven behaviour change |
| Strategy vs Template Method | Composition (swap the whole algorithm) vs inheritance (override steps) |
| Observer vs Pub-Sub | Subject knows its observers vs a broker decouples publishers and subscribers |
| Mediator vs Observer | Centralized coordination vs distributed notification |

### 27.5 Enterprise Patterns (PoEAA) in Spring
- [ ] **Repository**: collection-like access to aggregates (Spring Data repositories).
- [ ] **Unit of Work**: track changes and commit them together (the JPA persistence context).
- [ ] **Identity Map**: one object per DB row per session (first-level cache).
- [ ] **Data Mapper** (JPA/Hibernate) vs **Active Record** (entity saves itself: Rails, Panache).
- [ ] **DTO**: data transfer across boundaries. Map with MapStruct or records.
- [ ] **Service Layer**: application boundary with transactions.
- [ ] **Front Controller**: `DispatcherServlet`. **MVC**: Spring MVC.
- [ ] **Specification**: composable business rules or query predicates (Spring Data `Specification`).

### 27.6 Anti-Patterns to Recognize
- [ ] **God Object / God Service**: a 3000-line `CommonUtils` or `OrderManager`.
- [ ] **Anemic Domain Model**: all logic in services, entities are bags of getters and setters.
- [ ] **Golden Hammer**: Kafka/microservices/Kubernetes for everything.
- [ ] **Big Ball of Mud**, **Spaghetti code**, **Lava flow** (dead code nobody dares remove).
- [ ] **Premature optimization**, and its opposite: ignoring performance entirely.
- [ ] **Distributed Monolith**, **Shared Database**, **Chatty services** (N network calls per request).
- [ ] **Magic numbers and strings**, **Copy-paste programming**, **Primitive obsession**.
- [ ] Catching `Exception` and swallowing it; using exceptions for flow control.

---

# 28. Study Roadmap & Resources

### 28.1 Suggested 24-Week Plan (≈ 1.5 hours a day on weekdays, 3–4 hours at weekends)

| Weeks | Focus | Deliverable |
|---|---|---|
| 1–2 | Core Java: language, OOP, Strings, Exceptions, Generics | Notes + 30 small code snippets |
| 3–4 | Collections internals + Modern Java (Streams, Optional, Records, Pattern matching) | Implement your own HashMap, ArrayList, LRU cache |
| 5–6 | Concurrency + JMM + CompletableFuture + Virtual Threads | Producer-consumer, custom thread pool, rate limiter |
| 7 | JVM internals, GC, profiling (JFR, MAT) | Profile a leaking demo app and fix it |
| 8–9 | Spring Core + Boot internals (lifecycle, AOP, auto-config) | Write a custom Spring Boot starter |
| 10–11 | JPA/Hibernate + Transactions + DB indexing & SQL | Fix N+1 issues, write an EXPLAIN ANALYZE report |
| 12 | REST design, Spring Security, OAuth2/JWT | Secure API with Keycloak + resource server |
| 13–14 | Design principles + all 23 GoF patterns | One Java example per pattern in a Git repo |
| 15–16 | LLD case studies (2–3 a week) | Parking lot, BookMyShow, Splitwise, elevator, rate limiter |
| 17–18 | Microservices, Kafka, Resilience, Outbox/Saga | Two services + Kafka + Outbox + Testcontainers |
| 19–21 | System design fundamentals + 10 case studies | Diagram + write-up per case study |
| 22 | Docker, Kubernetes, CI/CD, Observability | Deploy your project to a local K8s (kind/minikube) with Prometheus + Grafana |
| 23 | Architecture (Hexagonal, DDD, CQRS) + AI engineering (Spring AI RAG) | Refactor the project to hexagonal; add a RAG endpoint |
| **Daily, all 24 weeks** | **DSA**: 1 problem a day following the patterns (13.7) | NeetCode 150 completed |

### 28.2 Best Books (one per area)
- [ ] **Java**: *Effective Java* (3rd ed.), Joshua Bloch ⭐ · *Java Concurrency in Practice*, Brian Goetz ⭐ · *Modern Java in Action*
- [ ] **JVM**: *Optimizing Java* (Evans, Gough, Newland) · *Java Performance* (Scott Oaks, 2nd ed.)
- [ ] **Spring**: *Spring Start Here* & *Spring Security in Action* (Laurențiu Spilcă) · *Spring Boot: Up and Running* · Spring reference docs
- [ ] **JPA**: *High-Performance Java Persistence*, Vlad Mihalcea ⭐
- [ ] **Design**: *Head First Design Patterns* (2nd ed.) · *Design Patterns* (GoF) · *Clean Code* & *Clean Architecture* (Robert C. Martin) · *Refactoring* (Fowler)
- [ ] **DDD**: *Domain-Driven Design Distilled* (Vernon) → *Implementing DDD* → *DDD* (Evans) · *Learning Domain-Driven Design* (Khononov)
- [ ] **System design**: *Designing Data-Intensive Applications*, Martin Kleppmann ⭐⭐ (2nd ed. in progress) · *System Design Interview Vol 1 & 2* (Alex Xu) · *Building Microservices* (Sam Newman, 2nd ed.) · *Microservices Patterns* (Chris Richardson) · *Release It!* (Nygard)
- [ ] **Architecture**: *Fundamentals of Software Architecture* (Richards & Ford) · *Software Architecture: The Hard Parts*
- [ ] **DSA**: *Grokking Algorithms* (intro) · *Elements of Programming Interviews in Java* · *Cracking the Coding Interview*
- [ ] **Career**: *The Staff Engineer's Path* (Tanya Reilly) ⭐ · *Staff Engineer* (Will Larson) · *The Pragmatic Programmer* (20th anniv.)
- [ ] **SRE**: *Site Reliability Engineering* (Google, free online)

### 28.3 Online Resources
- [ ] **Practice**: LeetCode, NeetCode.io (roadmap + videos), AlgoMonster, Codeforces (optional)
- [ ] **System design**: ByteByteGo, *System Design Primer* (GitHub, donnemartin), Hello Interview, engineering blogs (Netflix, Uber, Meta, Discord, Stripe, Cloudflare)
- [ ] **Java/Spring**: Baeldung ⭐, Vlad Mihalcea's blog, Inside Java (inside.java), Spring blog & Spring I/O talks, Josh Long ("Spring Tips"), Dan Vega, Marco Behler, Java Champions' talks (Devoxx)
- [ ] **JVM**: Aleksey Shipilëv's JVM Anatomy Quarks, JEP index (openjdk.org/jeps)
- [ ] **Patterns**: refactoring.guru (patterns + smells) ⭐, microservices.io (Chris Richardson) ⭐, Martin Fowler's bliki
- [ ] **Distributed systems**: MIT 6.824 lectures, Jepsen analyses, *Patterns of Distributed Systems* (Unmesh Joshi)

### 28.4 Senior Interview Readiness Checklist
- [ ] I can explain HashMap, ConcurrentHashMap, and the JMM internals on a whiteboard.
- [ ] I can write a thread-safe, bounded producer-consumer without looking anything up.
- [ ] I can explain the Spring bean lifecycle, AOP proxies, and the self-invocation problem with `@Transactional`.
- [ ] I can diagnose an N+1 problem and explain propagation and isolation with examples.
- [ ] I can read a thread dump, a heap dump, and a GC log.
- [ ] I can solve a medium LeetCode problem in 25 minutes and talk through the trade-offs.
- [ ] I can design 10+ classic systems with estimation, a data model, and deep dives.
- [ ] I can do an LLD with clean, extensible Java code in 45 minutes.
- [ ] I can explain the Outbox, Saga, Circuit Breaker, CQRS, and idempotency patterns with real examples.
- [ ] I can justify every architectural decision with trade-offs, and I have written ADRs.
- [ ] I have 8–10 STAR stories ready (leadership, conflict, failure, impact, mentoring, ambiguity).
- [ ] I can explain how my systems are observed (SLOs, dashboards, alerts) and how I handled incidents.

---

> 💡 **Final advice:** At 15 years, nobody expects you to have memorised every API. They expect **depth (internals), judgement (trade-offs), and impact (ownership)**. For each topic, ask:
> 1. *How does it work internally?*
> 2. *When would I NOT use it?*
> 3. *What breaks in production, and how would I detect it?*
>
> If you can answer those three questions for most of this map, you're operating at a staff level. Good luck! 🚀
