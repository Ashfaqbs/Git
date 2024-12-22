- Scenario 

 git status 
  (use "git restore <file>..." to discard changes in working directory)
        modified:   k8s-with-springboot/simple-rest-api.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        k8s-with-springboot/image-11.png
        k8s-with-springboot/image-12.png
        k8s-with-springboot/image-13.png
        k8s-with-springboot/image-14.png
        k8s-with-springboot/image-15.png
        k8s-with-springboot/image-16.png
        k8s-with-springboot/image-17.png
        k8s-with-springboot/image-18.png
        k8s-with-springboot/image-19.png
        k8s-with-springboot/image-20.png
        k8s-with-springboot/image-21.png
        k8s-with-springboot/image-22.png
        k8s-with-springboot/image-23.png
        k8s-with-springboot/image-24.png
        k8s-with-springboot/sb-crud.md

no changes added to commit (use "git add" and/or "git commit -a")

only wnat to add all except sb-crud.md, in a single line.




### Correct Way to Exclude Files in Git

If we want to exclude a file while adding others, here are the correct options:

#### 1. **Use a Pattern with `git add`**
If we want to add all `.png` files but exclude `sb-crud.md` explicitly, use:

```bash
git add k8s-with-springboot/*.png
```

This adds all `.png` files in the directory and ignores `sb-crud.md`.

#### 2. **Add Everything Except the File**
To exclude `sb-crud.md` from being added but include everything else, we can use the `git add` command along with `find` or manual file listing.

Here’s a manual way:

```bash
git add .
git reset k8s-with-springboot/sb-crud.md
```

- `git add .`: Stages all changes.
- `git reset <file>`: Removes the specific file from the staging area.

#### 3. **Use an Explicit List**
If we don’t have too many files, we can manually add the specific files we want, separated by spaces:

```bash
git add k8s-with-springboot/image-11.png k8s-with-springboot/image-12.png k8s-with-springboot/image-13.png
```

#### 4. **Exclude via `.gitignore` Temporarily**
we can temporarily add `sb-crud.md` to a `.gitignore` file:

```bash
echo "k8s-with-springboot/sb-crud.md" >> .gitignore
```

Then add all files:

```bash
git add .
```

Finally, remove the line from `.gitignore` once you're done.

#### 5. **Interactive Add**
Use `git add -i` (interactive mode) to manually select files to stage:

```bash
git add -i
```

This will let us pick files one by one and avoid staging `sb-crud.md`.

### Best Solution to our Case
Run:

```bash
git add .
git reset k8s-with-springboot/sb-crud.md
```

This is simple and avoids manually listing all files.
