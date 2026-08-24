# Recitation 0 — Git, IntelliJ, and your first Java program

By the end of this hour you will have written one line of Java, watched a test go from
red to green, pushed the result to GitHub, and committed a class diagram of an object of
your own choosing. That loop — **write, test, commit, push** — is every assignment in
this course, and most of a software job.

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

## Part 6 — Draw your first class diagram

You have spent two lectures on what an object *is* — identity, state, behavior — and on
deciding when one object should be two. Now you write one down.

**17.** In the project panel, open **`design.md`**. It is a fill-in-the-blanks file.

**18.** Answer the first three sections about **one real object from your own life** —
the one from Tuesday's exit ticket works perfectly. A library card, a vending machine,
your car. Not something from a program.

The third question is the one that matters:

> **Its one responsibility** — one sentence, starting with a verb. If you need the word
> "and", you are probably looking at two objects.

That is Thursday's Single Responsibility idea, applied to something you already
understand.

**19.** Now the diagram. Find the `mermaid` block in `design.md` and replace `Example`
with your object.

```
classDiagram
    class VendingMachine {
        String location
        int itemsRemaining
        dispense(String) void
        isEmpty() boolean
    }
```

Three rules, and that is genuinely all of it for today:

| Rule | |
|---|---|
| Every diagram starts with `classDiagram` | then `class YourName { ... }` |
| **State goes on top** | written `type name` — same order as Java |
| **Behavior goes underneath** | ends in `()`, and the return type goes **after**: `isEmpty() boolean` |

> That last one is backwards from Java and it trips everyone up exactly once. It is the
> UML convention, not a typo.

**20.** To experiment without pushing, paste your block into
[mermaid.live](https://mermaid.live) and watch it draw as you type. When it looks right,
put it back in `design.md`.

> **Why write a picture as text?** Because it lives in the repo next to the code it
> describes, so when the code changes the diagram is right there to change with it. A
> diagram in a slide deck goes stale the day after you draw it.

---

## Part 7 — Commit and push again

**21.** Same loop as before: **Commit** tab, tick `design.md`, write a message, **Commit
and Push**.

**22.** Open your repository on GitHub and click `design.md`.

**GitHub drew your diagram.** You wrote text; the picture came for free, and anyone who
opens your repo sees it.

That is the second time you have run write → test → commit → push in one session. It is
the loop for the rest of the semester.

---

## Part 8 — Hand in your GitHub username

**23.** Submit your GitHub username using the form your instructor gives you in class.

This one matters more than it looks: every repository you receive for the rest of the
term is named after your GitHub username. If we do not have it, you do not get the
assignment.

---

## Congratulations

You have written, tested, committed, and pushed Java, and you have committed a class
diagram of your own object. Next week the syntax starts making sense — beginning with
that `main` on Sep 3.

---

## Take-home — get yourself a tank

Optional, ungraded, and the most fun thing in this course.

**Robocode** is a game where you write a Java class and it becomes a tank that fights
other people's tanks. There is a tournament on the last day of class.

> https://github.com/DSU-CSCI-121-F26/robocode-arena

Fork it and follow its README. You will need to install Robocode itself — a separate
download, which is why it is not part of today's session. Budget twenty minutes.

Your first change is one number, and you do not need any Java you have not seen:

```
./tourney init <your-github-username> ThunderTank
```

Then open your bot, change `MOVE_DISTANCE` from `100` to `20`, and run:

```
./tourney
```

Watch the scoreboard. Change it to `400`. Watch again. That is a variable changing the
behavior of a program, which is most of what Chapter 2 is about — and you got there
before we taught it.

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
| The diagram does not render on GitHub | The block must open with three backticks followed by `mermaid`, and the first line inside must be `classDiagram`. Check both, then reload |
| The diagram renders but is empty | You have `class Name` with nothing after it, or your braces do not match. Paste it into [mermaid.live](https://mermaid.live) — it points at the exact line |
| `design.md` looks like plain text in IntelliJ | Normal. IntelliJ does not draw Mermaid without a plugin. Push it and look on GitHub |

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
