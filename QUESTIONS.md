# Reflection Questions

Answer these as you go — don't wait until the end. Some answers only exist
*after* you've done a step, so fill this in progressively.

Your answers will be reviewed alongside your code. Generic or copy-pasted
answers (that don't reference your actual output) will be sent back for
revision.

---

## Part 1 — Before touching anything (after reading CONTRIBUTING.md)

**1. What branch naming convention does this project use? Give an example
branch name you plan to use.**

> The project uses `<type>/<short-description>`where `<type>` must be one of `feature`, `fix`, `docs`or `chore`I used `docs/add-my-name`since my change only edits a documentation file

**2. What commit message format is required? Write the exact commit message
you plan to use for your change.**

> Conventional Commits: `<type>: <short summary>`with an optional longer description The exact message I used was `docs: add name to contributors list`

**3. Does this project expect a linked issue before opening a PR, or is a PR
description enough?**

> A PR description alone is not enough on its own: CONTRIBUTING.md says to "link the related task/issue in your PR description" So I will link the task by writing `Closes #1` (Issue #1, "Task") in the PR description

---

## Part 2 — After forking and cloning

**4. Paste the output of `git remote -v` from your local clone. Which remote
is `origin` and which is `upstream`, and why does that distinction matter?**

> ```
> origin    https://github.com/mmbayoumitaha/Practice-Repository.git (fetch)
> origin    https://github.com/mmbayoumitaha/Practice-Repository.git (push)
> upstream  https://github.com/IbrahimYasserM/Practice-Repository.git (fetch)
> upstream  https://github.com/IbrahimYasserM/Practice-Repository.git (push)
> ```
> `origin` is my own fork (mmbayoumitaha) which I cloned and can push to `upstream` is the original repo (IbrahimYasserM) which I only fetch from The distinction matters because I don't have push access to upstream: my branch goes to origin and I open a PR from origin into upstream's `main`Upstream is also where I got the `conflict-practice` branch from using `git fetch upstream`

---

## Part 3 — After making your change

**5. Paste the output of `git log --oneline -3`. Do your commit message(s)
follow the convention from `CONTRIBUTING.md`?**

> ```
> c35d963 (HEAD -> docs/add-my-name) docs: add name to contributors list
> 3b30f00 (upstream/main, upstream/HEAD, origin/main, origin/HEAD, main) Clarify task labeling in README
> f5ecf54 Revise task assignment instructions in README
> ```
> YesMy commit `c35d963` uses the `docs:` type followed by a short summary, which matches the Conventional Commits format required by CONTRIBUTING.md


---

## Part 4 — After hitting the seeded merge conflict

**6. What caused the conflict? Which file and lines were involved?**

> The conflict was in `CONTRIBUTORS.md` in lines 12–17 (the conflict markers `<<<<<<< HEAD` through `>>>>>>> upstream/conflict-practice`) right below the "Add your line below this comment" comment and after Ibrahim's line On my branch I added `- Mohamed Bayoumi - mmbayoumitaha - fun fact: new head flutter`and the `conflict-practice` branch added `- Mohammed Nasser — MohammedNaser28` in the same place Both sides changed the same lines so Git couldn't decide which one to keep and stopped with `CONFLICT (content): Merge conflict in CONTRIBUTORS.md`

**7. How did you resolve it — what did you keep, remove, or combine, and why?**

> I kept both lines because they belong to two different contributors and discarding either would delete someone's entry I removed the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) and an extra blank line I ordered them alphabetically by first name as the comment in the file requires: "Mohamed" comes before "Mohammed" (the sixth letter `e` comes before `m`) Then I ran `git add CONTRIBUTORS.md` and `git commit --no-edit` to complete the merge (merge commit `db61495`)

---

## Part 5 — After opening your PR

**8. Paste your PR link. How many commits and how many files changed does
your PR show?**

> PR link: (add after opening the PR) Commits: (add). Files changed: (add)

---

## Part 6 — Final reflection

**9. What's one thing about this workflow that surprised you, confused you,
or felt different from what you expected going in?**

> What surprised me was that Git doesn't make the choice for you in a conflict: it puts both versions in the file with markers and I have to decide what the final file should look like I had expected one side to just win I also learned that `git fetch` only downloads the other repo's branches without changing my files so I could merge `upstream/conflict-practice` on purpose when I was ready

**10. If a teammate asked you to explain the difference between `fork`,
`clone`, `origin`, and `upstream` in one or two sentences each, what would
you say?**

> - `fork`: your own copy of someone else's repo on GitHub which you can change freely
> - `clone`: downloading a repo to your computer so you can work on it locally
> - `origin`: the default name Git gives to the remote you cloned from in my case my fork, where I push my branches
> - `upstream`: the name I gave to the original repo I forked from where I fetch updates and other branches and which I send my PR to