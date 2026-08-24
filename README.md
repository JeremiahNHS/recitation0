# Recitation 0 — Git, IntelliJ, and your first Java program

**Full instructions: [`Instructions/README.md`](Instructions/README.md).** Follow them in
order.

## What you are doing

Writing one line of Java, watching a test go from red to green, and pushing it to GitHub.

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

## The task

`src/main/java/Recitation0.java` currently prints nothing:

```java
System.out.println();
```

Make it print `Hello World!` — the exclamation mark included, because the test checks for
it. Then commit and push.

## About `public static void main`

You will meet that line in step 10 and it will look like noise. It is supposed to, for
now — every word in it names something the course has not covered yet. The instructions
list what each word means and the exact week you will properly learn it. `main` is the
only one that matters today: **it is where Java starts running.**

## Also due

Your **GitHub username**, submitted through the form given in class. Every repository you
receive for the rest of the term is named after it.
