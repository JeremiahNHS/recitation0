# Recitation 0 — Git, IntelliJ, and your first Java program

By the end of this hour you will have written one line of Java, watched a test go from
red to green, and pushed the result to GitHub. That loop — **write, test, commit, push**
— is every assignment in this course, and most of a software job.

Follow the steps in order. If something goes wrong, the troubleshooting table at the
bottom covers what actually goes wrong.

---

## Before you start

| You need | Where |
|---|---|
| A GitHub account | https://github.com — sign up if you do not have one |
| IntelliJ IDEA **Community Edition** (free) | https://www.jetbrains.com/idea/download/ |
| Java 21 | IntelliJ can install it for you — see step 6 |

You do **not** need to install Maven. This project brings its own copy.

---

## Part 1 — Get your own copy of the code

**1.** Open the assignment template:

> https://github.com/DSU-CSCI-121-F26/recitation0

**2.** Click the green **Use this template** button, then **Create a new repository**.

<p><image src="./xstep4.png" height="300"></p>

**3.** Name it `recitation0`, leave it **Public**, and create it.

You now have your own copy under your own account. Everything you do from here happens
in *your* repository — you cannot break the original.

---

## Part 2 — Connect IntelliJ to GitHub

**4.** Open IntelliJ. Go to **Settings → Version Control → GitHub**, click **+**, and
choose **Log In with GitHub**.

<p><image src="./xstep13.png" height="300"></p>

Your browser opens, you approve, and IntelliJ is connected. That is the whole step.

> If that button does not work for you, there is a token-based fallback at the very
> bottom of this page. Try this way first — it is three clicks and nothing to save.

**5.** Back on **your** repository page on GitHub, click the green **Code** button and
copy the URL.

<p><image src="./xstep15.png" height="250"></p>

**6.** In IntelliJ, choose **Get from VCS**, paste the URL, and pick where to put it.

<p><image src="./xstep16.png" height="300"></p>

> **Watch the folder.** IntelliJ should add `recitation0` to the end of the path. If it
> does not, type it yourself — otherwise the project files scatter loose into your
> Documents folder.

Click **Clone**. If IntelliJ offers to install Git or a JDK, say yes.

---

## Part 3 — Run the test, and watch it fail

This project is built with **Maven**. You will use the same command in every lab this
semester, so it is worth learning once.

**7.** Open the terminal *inside IntelliJ* — **View → Tool Windows → Terminal**, or
`` Ctrl+` ``. It opens already in your project folder.

**8.** Run the tests:

```
./mvnw test
```

On Windows, use `mvnw.cmd test` instead. Every lab in this course uses this same command.

**The first run is slow.** Maven downloads what it needs, once, and prints a lot. Let it
finish.

**9.** It should say `BUILD FAILURE`, and above that:

```
Test Failed!
Expecting:
Hello World!
Actual:
```

**That is correct.** The test is checking for something the code does not do yet. A
failing test is not a mistake — it is a specification you have not met.

---

## Part 4 — Make it pass

**10.** In the project panel on the left, open `src/main/java/Recitation0.java`:

```java
public class Recitation0 {
    public static void main(String [] args) {
        System.out.println();
    }
}
```

### What is all that on line 2?

You are about to meet the most-typed line in Java. **You are not expected to understand
it today** — every word in it names something we have not covered yet. Here is the
one-sentence version of each, and the week you will actually earn it:

| Word | What it means, for now | You will really learn it |
|---|---|---|
| `public` | anyone is allowed to call this | **Week 4** — classes |
| `static` | belongs to the class itself, not to any one object | **Week 5** — methods |
| `void` | hands nothing back when it finishes | **Week 5** — methods |
| `main` | **where Java starts running** | **Week 2** — Sep 3 |
| `String [] args` | any words typed after the program name | **Week 9** — arrays |

Only one of those matters today: `main` is where the program starts. Java looks for
`main` and runs it. Everything else on that line is a promise we will come back and
keep, on the dates above.

> Python let you put code straight in a file and run it. Java does not — every line of
> Java lives inside a class, and every program starts at a `main`. That is the first
> real difference between the two languages, and it is most of why line 2 looks the way
> it does.

**11.** Put the message inside the parentheses, so the line reads **exactly** this:

```java
System.out.println("Hello World!");
```

> The exclamation mark is part of it. The test compares against `Hello World!` and will
> keep failing without it.

**12.** Run the tests again:

```
./mvnw test
```

You want `BUILD SUCCESS`. Red to green in one line of code.

---

## Part 5 — Commit and push

**13.** Open the **Commit** tab on the left.

<p><image src="./xstep25.png" height="350"></p>

**14.** Tick the changed file, write a message that says what you did — `Print Hello
World` is fine, `stuff` is not — and click **Commit and Push**.

<p><image src="./xstep27.png" height="400"></p>

**15.** Click **Push** in the window that follows.

**16.** Reload your repository page on GitHub. Your change is there.

That round trip — your machine to GitHub — is how you hand in everything this semester.

---

## Part 6 — Hand in your GitHub username

**17.** Submit your GitHub username using the form your instructor gives you in class.

This one matters more than it looks: every repository you receive for the rest of the
term is named after your GitHub username. If we do not have it, you do not get the
assignment.

---

## Congratulations

You have written, tested, committed, and pushed Java. Next week the syntax starts making
sense — beginning with that `main` on Sep 3.

---

## If something goes wrong

| Symptom | Fix |
|---|---|
| `./mvnw: Permission denied` | Run `chmod +x mvnw` once, then try again |
| `./mvnw` — command not found | You are not in the project folder. In the IntelliJ terminal, run `ls` — you should see `pom.xml`. If not, `cd` into the project |
| Windows: `./mvnw` does nothing | On Windows the command is `mvnw.cmd test`, without the `./` |
| First run takes forever | Normal, once. Maven is downloading. Leave it |
| `BUILD FAILURE` after adding the message | Check for the `!` and the quotes: `System.out.println("Hello World!");` — and the semicolon |
| No terminal tab in IntelliJ | **View → Tool Windows → Terminal** |
| IntelliJ shows no `pom.xml` / no Maven panel | You cloned into the wrong folder, or cloned the wrong repo. Check you used **your** copy's URL |
| "Log In with GitHub" does nothing | Use the token fallback below |
| Push is rejected | You are pushing to the template instead of your own copy. Check **Settings → Version Control → Remotes** points at *your* username |

---

## Appendix — token login, if the browser login fails

Only do this if step 4 did not work.

**A.** On GitHub, click your avatar → **Settings** → **Developer settings** →
**Personal access tokens** → **Tokens (classic)**.

<p><image src="./xstep7.png"></p>

**B.** **Generate new token (classic)**. Name it `CSCI-121`. Tick **repo**, **workflow**,
**gist**, and **read:org**.

<p><image src="./xstep9.png"></p>

**C.** For **Expiration**, choose **Custom** and pick a date after the end of the
semester — **December 31, 2026**.

> The date shown in the screenshot above is from an older version of this handout and is
> long past. Use December 31, 2026.

**D.** Click **Generate token**, then copy it immediately. GitHub will never show it
again. If you lose it, generate a new one — that is not a problem.

<p><image src="./xstep11.png"></p>

**E.** In IntelliJ: **Settings → Version Control → GitHub → + → Log In with Token**,
paste, and click **Add Account**.

<p><image src="./xstep12.png" height="300"></p>
