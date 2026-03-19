<!--
index: true
type: learning-repo-index
owner: bhf
topic: java
llm-accessible: true
-->

<a id="top"></a>
[![StayTuned](https://img.shields.io/badge/~%24-StayTuned_-000000?style=flat&labelColor=000000&color=000000)](https://sanjeev.pages.dev)

# stay-learning

![brain](brain.gif)

Whether you're up or you're down, just StayLearning. 

An index of learning examples to help friends. 

Each repository isolates a specific library, API, or technique and demonstrates it with minimal, runnable examples. 

This document is designed to serve as a navigable index for humans, LLMs, and MCP tools.

---

## Table of Contents

- [stay-learning](#stay-learning)
  - [Table of Contents](#table-of-contents)
  - [How to Use This Index](#how-to-use-this-index)
  - [Repository Index](#repository-index)
    - [st-learning-java-streams](#st-learning-java-streams)
    - [st-learning-java-arenas](#st-learning-java-arenas)
    - [st-learning-spi](#st-learning-spi)
    - [st-learning-jpms `[private]`](#st-learning-jpms-private)
    - [st-learning-mapstruct](#st-learning-mapstruct)
    - [st-learning-base `[private]`](#st-learning-base-private)
  - [Quick Reference](#quick-reference)
  - [For LLMs and MCP Tools](#for-llms-and-mcp-tools)
    - [Machine-readable repo list](#machine-readable-repo-list)

---

## How to Use This Index

- Each entry below describes one repository, its purpose, and the key concepts it demonstrates.
- All repositories follow the naming convention `st-learning-<topic>`
- Repositories marked `[private]` require access rights.
- The base template repository is [`st-learning-base`](#st-learning-base) — use it to bootstrap new examples.

---

## Repository Index

### [st-learning-java-streams](https://github.com/bhf/st-learning-java-streams)

**Topics:** `java` `streams` `collections` `functional-programming` `collectors`

A collection of small, paired examples demonstrating the Java Streams API versus traditional (pre-stream) loop-based approaches. Each example shows the manual solution alongside the concise Stream equivalent.

**Packages and examples:**

| Package | Concept | Example class |
|---|---|---|
| `streams.filter` | Filtering with `Stream.filter` | `FilterExample` |
| `streams.map` | Transformation with `Stream.map` | `MapExample` |
| `streams.group` | Grouping with `Collectors.groupingBy` | `GroupExample` |
| `streams.flatmap` | Flattening with `Stream.flatMap` | `FlatMapExample` |
| `streams.reduce` | Aggregation/reduction | `ReduceExample` |
| `streams.find` | Finding with `findFirst()` | `FindExample` |
| `streams.collectors` | Counting, toMap, joining, partitioning, averaging, summarizing, downstream collectors | `CountingExample`, `ToMapExample`, `JoiningExample`, `PartitionExample`, `AveragingExample`, `SummarizingExample`, `DownstreamExample` |

---

### [st-learning-java-arenas](https://github.com/bhf/st-learning-java-arenas)

**Topics:** `java` `memory` `arenas` `foreign-memory` `jdk24` `java.lang.foreign`

Demonstrates native memory allocation and management using Java's `java.lang.foreign` API — specifically `Arena` and `MemorySegment`. Shows how to allocate, write, read, and free off-heap native memory.

**Key class:** `com.bhf.learning.memory.ArenaExample`

**Requirements:** JDK 21+ (tested on JDK 24)

---

### [st-learning-spi](https://github.com/bhf/st-learning-spi)

**Topics:** `java` `spi` `service-provider-interface` `serviceloader` `design-patterns` `extensibility`

Demonstrates the Java Service Provider Interface (SPI) mechanism using `ServiceLoader`. Uses an `IdentifierProvider` interface with two implementations (`RandomUuidProvider`, `TimestampIdProvider`) and a factory that selects a provider via system property, environment variable, or `ServiceLoader` fallback.

**Key classes:**
- Interface: `com.bhf.learning.spi.IdentifierProvider`
- Implementations: `RandomUuidProvider` (`uuid`), `TimestampIdProvider` (`timestamp`)
- Factory: `com.bhf.learning.spi.IdentifierProviderFactory`

**Programmatic usage:**
```java
IdentifierProvider p = IdentifierProviderFactory.loadFromConfig();
System.out.println(p.name() + " -> " + p.id());
```

---

### [st-learning-jpms](https://github.com/bhf/st-learning-jpms) `[private]`

**Topics:** `java` `jpms` `jlink` `modules` `gradle` `docker` `java21`

A multi-module Gradle project demonstrating the Java Platform Module System (JPMS) and `JLink` for creating a minimal custom Java runtime image. Shows `module-info.java` usage across modules, inter-module dependencies, and Docker packaging.

**Module structure:**

| Module | Purpose |
|---|---|
| `common` | Shared utilities and logger |
| `messages` | Message types and entities (Java Records) |
| `domain` | Domain logic; depends on `common` and `messages` |
| `application` | Entry point, wires modules, configured for JLink |

---

### [st-learning-mapstruct](https://github.com/bhf/st-learning-mapstruct)

**Topics:** `java` `mapstruct` `object-mapping` `dto` `records` `enums` `gradle-kotlin-dsl` `junit5`

Demonstrates common MapStruct mapping patterns and recipes with JUnit 5 tests.

**Examples:**

| Example | Concept |
|---|---|
| Basic | `PersonEntity` → `PersonDTO` simple mapping |
| Record | Mapping to a Java `record`-based DTO |
| Enum | Mapping between different enum types (external → domain) |
| Source property | Property-style accessors (`firstName()`) on source |
| Target property | Property-style accessors on target with `@AfterMapping` |
| Iterable | `Iterable<Item>` source → `List<ItemDTO>` target |

---

### [st-learning-base](https://github.com/bhf/st-learning-base) `[private]`

**Topics:** `java` `gradle` `template` `starter`

A minimal starter template used to bootstrap new `st-learning` example repositories. Contains the base Gradle build setup for small Java learning projects. Use this as the starting point when creating a new topic repository.

---

## Quick Reference

| Repository | Topics | Access |
|---|---|---|
| [st-learning-java-streams](https://github.com/bhf/st-learning-java-streams) | Streams, Collectors, Functional | Public |
| [st-learning-java-arenas](https://github.com/bhf/st-learning-java-arenas) | Foreign Memory, Arenas, JDK 24 | Public |
| [st-learning-spi](https://github.com/bhf/st-learning-spi) | SPI, ServiceLoader, Extensibility | Public |
| [st-learning-jpms](https://github.com/bhf/st-learning-jpms) | JPMS, JLink, Multi-module, Docker | Private |
| [st-learning-mapstruct](https://github.com/bhf/st-learning-mapstruct) | MapStruct, DTO mapping, Records | Public |
| [st-learning-base](https://github.com/bhf/st-learning-base) | Starter template | Private |

---

## For LLMs and MCP Tools

This index repository exists at `https://github.com/bhf/st-learning`. To access a specific example repository:

1. **List all repos in this family:** Search GitHub for `org:bhf st-learning` or `user:bhf st-learning`.
2. **Navigate to a topic:** Use the table above to identify the relevant repo, then fetch its README or source files directly.
3. **Clone and run:** Each repo uses Gradle and can be built with `./gradlew build` or `./gradlew test`. Private repos require authentication.
4. **Language/runtime:** All repos use Java (JDK 21+) and Gradle (Kotlin or Groovy DSL).

### Machine-readable repo list

The full index is available as [st-learning-index.json](st-learning-index.json).
