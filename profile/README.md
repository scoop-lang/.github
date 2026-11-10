<p align="center">
  <a href="https://scoop-lang.org"><img src="https://scoop-lang.org/assets/logo.svg" width="120" alt="Scoop logo"></a>
</p>

<h1 align="center">The Scoop Programming Language</h1>

<p align="center">
  <b>Familiar syntax, native performance.</b><br>
  A statically typed, Kotlin-style language with true value types, compiled straight to native binaries.
</p>

<p align="center">
  <a href="https://scoop-lang.org">Website</a> ·
  <a href="https://scoop-lang.org/docs/install.html">Install</a> ·
  <a href="https://scoop-lang.org/docs/tour.html">Language Tour</a> ·
  <a href="https://book.scoop-lang.org">The Book</a> ·
  <a href="https://scoop-lang.org/reference/stdlib.html">Standard Library</a>
</p>

> [!NOTE]
> This is the **Scoop programming language**. Looking for the Scoop package manager for Windows? Visit [scoop.sh](https://scoop.sh/).

```kotlin
struct Point(val x: Int, val y: Int)

enum Shape {
    Circle(Point, Int),
    Line(Point, Point)
}

fun describe(shape: Shape): String = when (shape) {
    case Circle(Point(0, 0), val r) -> f"circle at origin, r=${r}"
    case Circle(val center, _) -> f"circle at ${center.x},${center.y}"
    case Line(val from, val to) -> f"line of dx=${to.x - from.x}"
}

fun main() {
    val origin = Point(0, 0)
    val moved = origin.{ x: 5 }
    println(describe(Shape.Circle(origin, 3)))  // circle at origin, r=3
    println(describe(Shape.Line(origin, moved))) // line of dx=5
}
```

## Highlights

- **True value types** — `struct`, payload-carrying `enum` and tuples are immutable, identity-free values stored inline and laid out contiguously in arrays.
- **Pattern matching** — `when` with nested destructuring, guards and exhaustiveness checking that reports readable counterexamples at compile time.
- **No null** — `T?` is sugar for `Option<T>`; `?.`, `?:` and `!!` work as you'd expect.
- **Monomorphized generics + LLVM** — specialized code per type instantiation, optimized by LLVM with cross-Cone inlining.
- **Precise, moving GC** — a C runtime with generational Immix collection; deterministic resource cleanup via `close` / `use`.
- **Direct C FFI** — `@Extern`, `@CLayout`, `Ptr<T>` and `FunPtr<F>`, with `@Unsafe` marking the boundary.
- **Native desktop UI** — a declarative UI framework shipped with the toolchain: Skia rendering, native windows, menus and tray, and macOS / Material / Fluent / shadcn themes.
- **Batteries included** — one `scoop` command for `new`, `pm`, `build`, `run`, `test`, `fmt`, `check`, `doc` and `bundle`, plus an LSP server and VS Code extension; 40+ precompiled standard library Cones from collections to TLS, HTTP/2 and 2D graphics.

Runs on **macOS** (AArch64), **Linux** (x86-64, glibc / musl) and **Windows** (x64).

## Get started

```sh
# macOS / Linux
curl -fsSL https://scoop-lang.org/install.sh | sh
```

```powershell
# Windows (PowerShell)
irm https://scoop-lang.org/install.ps1 | iex
```

```sh
scoop new --group dev.example hello
cd hello
scoop run --release   # Hello, Scoop!
```

## Repositories

| Repository | Description |
| --- | --- |
| [**scoop**](https://github.com/scoop-lang/scoop) | Compiler, runtime, standard library and toolchain |
| [**scoop-book**](https://github.com/scoop-lang/scoop-book) | *The Scoop Programming Language* book — [book.scoop-lang.org](https://book.scoop-lang.org) |
| [**scoop-lang.org**](https://github.com/scoop-lang/scoop-lang.org) | Source of the official website — [scoop-lang.org](https://scoop-lang.org) |

<p align="center"><sub>Scoop is in developer preview (0.x). Licensed under Apache-2.0.</sub></p>
