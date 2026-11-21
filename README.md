# SetList collection comparison

A small Java console program that compares membership checks and removals across five standard-library collection implementations:

- `HashSet`
- `LinkedHashSet`
- `TreeSet`
- `ArrayList`
- `LinkedList`

The program builds a shuffled list containing the integers from `0` through `59,999`, copies the same values into each collection, and prints elapsed times in milliseconds.

## What it measures

For each collection, the program:

1. performs 60,000 `contains` calls using randomly generated integers in the range `0` through `119,999`;
2. removes the integers `0` through `59,999`.

The output is intended to illustrate how collection choice can affect these two operations.

## Technologies

- Java
- Java Collections Framework
- GitHub Actions for a compile check

The repository does not use a build tool or third-party dependency.

## Requirements

- A JDK with `javac` and `java` available on `PATH`

The workflow in this branch uses Temurin JDK 21. The repository does not otherwise record an intended minimum Java version.

## Run locally

### Reviewing the documentation branch

This README accompanies [documentation PR #2](https://github.com/T4N3V/SetList/pull/2),
which is based on [compilation fix PR #1](https://github.com/T4N3V/SetList/pull/1).
While those changes are unmerged, use the branch below so the source matches the
commands in this README:

```bash
git clone --branch codex/document-set-list-comparison https://github.com/T4N3V/SetList.git
cd SetList
javac SetList.java
java SetList
```

The current `main` branch declares `public class SetListTest` in `SetList.java`,
so compiling that checkout as-is fails with a public-class/filename mismatch.
This documentation does not fix that source code. After PR #1 and this README
are merged into `main`, a normal clone can use the same compile and run commands.

The exact timings vary between runs and machines.

Remove the generated class file when finished:

```bash
rm SetList.class
```

On Windows Command Prompt, use `del SetList.class` instead.

## Example output shape

```text
Member test time for hash set is <milliseconds> milliseconds
Remove element time for hash set is <milliseconds> milliseconds
...
```

Real timing values are intentionally omitted because the repository does not contain verified benchmark results.

## Validation

The GitHub Actions workflow compiles `SetList.java` on Temurin JDK 21:

```bash
javac SetList.java
```

There are currently no automated assertions for output or performance.

## Limitations

This is an educational timing example, not a rigorous benchmark:

- it uses `System.currentTimeMillis()` rather than a benchmarking harness;
- it does not warm up the JVM or isolate garbage collection and JIT effects;
- membership inputs are random, so runs do not use identical lookup sequences;
- removal empties each tested collection;
- only one collection size and one operation count are used;
- the printed timings should not be treated as stable performance claims.

## Repository status

The repository contains one console entry point. It has no packaged release, test suite, license file, or graphical interface.

## Screenshots

Not applicable: the program prints text results in a terminal.
