
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






3)1) git init and push
2)git config --global user.name "Sony"
)git config --global user.email "Sony@gmail.com"




3)a)git branch ui-fixes
git checkout ui-fixes
git fetch origin
git rebase origin/main
git push --set-upstream origin ui-fixes

3)b)git stash
git fetch origin
git checkout main
git reset origin/main
git stash pop


3)c)git checkout main
git pull origin main
git merge payment-module
git add bookingcontroller.java
git commit -m "Resolved conflict in BookingController.java"
git push origin main

---

If you want, I can **draw a simple flow diagram** showing **branches, commits, and steps** for all 6 scenarios, so it’s easy to visualize.

Do you want me to do that?
