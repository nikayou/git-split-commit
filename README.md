# git-split-commit
Git custom command to split a commit based on different files

## Install

- Download `git-split-commit` file
- ensure it is executable with `chmod +x`
- add it in your `PATH`

## Usage

`git split-commit <commit-id>`

## Effect

Given a commit `<commit-id>` affecting N files, will split the commit with [interactive rebase](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) into N different commitq: one for each file. It will conserve the commit message (though, it appends the operation and the affected file).


```
18451295 add A
16400912 add B
77421832 add C, modify A, delete B
81726489 add D
```

When performing `git split-commit 77421832`, you will have

```
18451295 add A
16400912 add B
48151623 add C, modify A, delete B -> A C
33254245 add C, modify A, delete B -> M A
61414522 add C, modify A, delete B -> D B
81726489 add D
```