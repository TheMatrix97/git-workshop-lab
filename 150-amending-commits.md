# Alice: amending commits

It is easy to realize there was an error just a second after commiting some files.
Here, Alice will correct one of such mistakes.

## Lab

* She starts by reaching her working area

```bash
cd alice/book
```

* Alice just realizes they forgot to write the name of the different chapters. It is going
to take some work to correct it, so she creates a new branch (the project is starting to
get some complexity, so she agrees with Bob to use `feat` as the prefix for *feature* oriented
branches)

```bash
git checkout -b feat_headings
```

* Now she will start updating the different chapters, starting with the first one:

```bash
sed -i '2i\## Chapter one' chapter-01.md
cat chapter-01.md
```

* Time to update the repo:

```bash
git add chapter-01.md
git commit -m "Updated chapter"
```

* Umh... looking at the project history, Alice is not very proud of her last commit message

```bash
git log --oneline
```

<details>
<summary>
So she is going to replace the message by replacing the old `commit` with a new one, changing
the commit message. This action, in effect, will rewrite the history of the project (although
in a very controlled way)

```bash
git commit --████ -m "Added chapter number (1)"
```
</summary>

---
#### Solution

```bash
git commit --amend -m "Added chapter number (1)"
```

---
</details>

* Now it looks much better:

```bash
git log --oneline
```

* The old commit will remain until the [garbage collector](https://renatogentil.medium.com/hands-on-git-garbage-collections-fb9e7c1dd5fc) happens:

```bash
git reflog
```
