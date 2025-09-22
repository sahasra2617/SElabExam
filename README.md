Perfect! Let’s go **step by step**, starting from scratch, for **all 6 scenarios**, showing the **full workflow from creating branches to resolving the issue** using simple Git commands (no cherry-pick). I’ll assume your repository is called `metro` and you are in the project folder.

---

## **1️⃣ Move a commit from `main` to `ui-fixes`**

**Scenario:** You accidentally committed UI fixes on `main`, but they should be in `ui-fixes`.

**Steps:**

```bash
# Step 1: Make sure you are on main
git checkout main

# Step 2: Create ui-fixes branch if it doesn't exist
git checkout -b ui-fixes

# Step 3: Switch back to main to remove the last commit
git checkout main

# Step 4: Save the last commit as a patch
git format-patch -1 HEAD

# Step 5: Remove the last commit from main
git reset --hard HEAD~1

# Step 6: Switch to ui-fixes and apply the patch
git checkout ui-fixes
git apply ../0001-*.patch  # Use the actual patch file name
git add .
git commit -m "Move UI fixes to ui-fixes branch"
```

✅ Now `main` is clean, and `ui-fixes` has the commit.

---

## **2️⃣ Remote main was force-pushed, align local safely**

**Scenario:** Your teammate force-pushed main; your local `main` is out of sync.

**Steps:**

```bash
# Step 1: Backup your local main in case you have unpushed work
git checkout -b backup-main

# Step 2: Fetch latest changes from remote
git fetch origin

# Step 3: Reset local main to match remote
git checkout main
git reset --hard origin/main
```

✅ Local `main` now matches remote without losing your work (it's saved in `backup-main`).

---

## **3️⃣ Merge conflict in `booking.java` while merging payment-module**

**Scenario:** You are merging `payment-module` into `main` and face a conflict.

**Steps:**

```bash
# Step 1: Make sure main is up to date
git checkout main
git pull origin main

# Step 2: Merge payment-module
git merge payment-module

# Step 3: Git shows conflict in booking.java
# Open booking.java, manually resolve conflicts (remove <<<<<<<, =======, >>>>>>> markers)

# Step 4: Mark the file as resolved
git add booking.java

# Step 5: Complete the merge
git commit -m "Resolved conflict in booking.java while merging payment-module"
```

✅ Merge complete with conflicts resolved.

---

## **4️⃣ Recover deleted branch (booking-module) before merge**

**Scenario:** You accidentally deleted a branch but its commits were not merged.

**Steps:**

```bash
# Step 1: See recent commits including deleted branches
git reflog

# Step 2: Find the last commit hash of the deleted branch

# Step 3: Restore the branch
git checkout -b booking-module <commit-hash>
```

✅ The deleted branch is restored and you can continue working.

---

## **5️⃣ Combine 3 commits in flight.java into one**

**Scenario:** You made 3 commits, manager wants a single commit.

**Steps:**

```bash
# Step 1: Start interactive rebase for last 3 commits
git rebase -i HEAD~3
```

* In the editor:

  * Keep the first line as `pick`
  * Change the next two lines from `pick` to `squash` (or `s`)
* Save and edit commit message as one combined message
* Finish rebase

✅ All 3 commits are now one single commit.

---

## **6️⃣ Restore a deleted feature branch**

**Scenario:** You committed on `feature` branch but deleted it.

**Steps:**

```bash
# Step 1: Look at recent commits
git reflog

# Step 2: Find the last commit hash of feature branch

# Step 3: Restore the branch
git checkout -b feature <commit-hash>
```

✅ Feature branch is back with all its commits.

---

### **Extra Tips:**

1. Always **backup your branch** before risky operations:

```bash
git checkout -b backup-branch
```

2. Always **pull latest changes** before merging:

```bash
git checkout main
git pull origin main
```

3. Use `git log --oneline` to see commits clearly.

---

If you want, I can **draw a simple flow diagram** showing **branches, commits, and steps** for all 6 scenarios, so it’s easy to visualize.

Do you want me to do that?
