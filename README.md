# Recitation 0 — Git, IntelliJ, and your first Java program

**Full instructions: [`Instructions/README.md`](Instructions/README.md).** Follow them in
order.

## What you are doing

Two things, and you commit and push both:

1. **One line of Java** — make a failing test pass.
2. **One class diagram** — of a real object you choose, in `design.md`.

That loop is every assignment this semester:

```
write  →  ./mvnw test  →  commit  →  push
```

## The one command

```
./mvnw test          # macOS / Linux
mvnw.cmd test        # Windows
```

This is a **Maven** project. It brings its own copy of Maven, so there is nothing to
install — the first run downloads what it needs and is slow exactly once.

## Task 1 — make the test pass

`src/main/java/Recitation0.java` currently prints nothing:

```java
System.out.println();
```

Make it print `Hello World!` — the exclamation mark included, because the test checks for
it.

### About `public static void main`

You will meet that line in step 10 and it will look like noise. It is supposed to, for
now — every word in it names something the course has not covered yet. The instructions
list what each word means and the exact week you will properly learn it. `main` is the
only one that matters today: **it is where Java starts running.**

## Task 2 — draw one object

Open `design.md` and fill it in for a real object from your own life — the one from
Tuesday's exit ticket works. Identity, one responsibility, and a small class diagram.

You write the diagram as text. **GitHub draws the picture** when you push, which is why
the diagram lives in the repo next to the code instead of in a slide deck where it goes
stale.

## Also due

Your **GitHub username**, submitted through the form given in class. Every repository you
receive for the rest of the term is named after it.

## Optional, and the most fun thing in this course

Fork the [Robocode arena](https://github.com/DSU-CSCI-121-F26/robocode-arena) and get
yourself a tank. Ungraded, runs all semester, tournament on the last day of class. The
take-home section at the end of the instructions walks you in.
