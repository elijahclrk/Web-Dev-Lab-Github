# Web Dev Lab

A collaborative space for learning, building, and experimenting with HTML, CSS, JavaScript, and modern web projects.

---

# Git Guide: Pull and Push (Step by Step)

**Pull** = download the latest code from GitHub to your computer.
**Push** = upload your changes from your computer to GitHub.

```
GitHub (online)  ──── PULL ────▶  Your computer
GitHub (online)  ◀─── PUSH ────  Your computer
```

---

## Part 1: Setup (do this only once)

### Step 1. Install Git
Download and install it from [git-scm.com](https://git-scm.com).

Check if it works:

```bash
git --version
```

You should see something like `git version 2.x.x`.

### Step 2. Tell Git who you are

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Use the **same email** as your GitHub account.

### Step 3. Get invited
Ask the repo owner to add you:
**Repo → Settings → Collaborators → Add people**.
Accept the invite from your email or GitHub notifications.

### Step 4. Clone the repo
This copies the project to your computer.

1. Open the repo on GitHub.
2. Click the green **Code** button and copy the HTTPS link.
3. Open your terminal and run:

```bash
git clone https://github.com/YOUR-USERNAME/web-dev-lab.git
```

4. Go inside the project folder:

```bash
cd web-dev-lab
```

---

## Part 2: PULL (Download the latest code)

> Always **pull first** before you start working. This makes sure you have your teammates' latest changes.

### Step 1. Open the project folder

```bash
cd web-dev-lab
```

### Step 2. Check where you are (optional but helpful)

```bash
git status
```

If it says `nothing to commit, working tree clean`, you're good to pull.
If you have unsaved changes, **commit them first** (see the Push steps below).

### Step 3. Pull the changes

```bash
git pull origin main
```

- `origin` = the GitHub copy of the repo
- `main` = the branch you're downloading from

### Step 4. Read the result

| Message | Meaning |
|---|---|
| `Already up to date.` | Nothing new. You have the latest. |
| Shows a list of files changed | New code was downloaded. Your files are updated. |
| `CONFLICT` | Two people edited the same lines. See **Fixing Problems** below. |

You're ready to work!

---

## Part 3: PUSH (Upload your changes)

> Do this after you finish a task. Follow the steps **in order**.

### Step 1. Pull first
Get the latest code so your push doesn't get rejected.

```bash
git pull origin main
```

### Step 2. Check what you changed

```bash
git status
```

- **Red** files = changed but not yet staged
- **Green** files = staged and ready to commit

### Step 3. Stage your changes
Staging means choosing which changes to save.

```bash
git add .
```

`.` means "all changed files." To add just one file:

```bash
git add index.html
```

Run `git status` again. Your files should now be green.

### Step 4. Commit your changes
A commit is a saved snapshot with a message.

```bash
git commit -m "Add navbar to homepage"
```

Write a short message that says **what you did**. Start with a verb like Add, Fix, Update, or Remove.

### Step 5. Push to GitHub

```bash
git push origin main
```

### Step 6. Check GitHub
Open your repo in the browser and refresh. Your changes and commit message should be there.

---

## First Push to an Empty Repo

Use this only if the GitHub repo is **brand new and empty**, and your files are still only on your computer.

```bash
cd your-project-folder
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/web-dev-lab.git
git push -u origin main
```

After this, you can use plain `git pull` and `git push`.

**No terminal?** On GitHub, tap **Add file → Upload files**, choose your files, then tap **Commit changes**.

---

## Fixing Problems

### Push was rejected
**Why:** Someone pushed before you.
**Fix:** Pull first, then push again.

```bash
git pull origin main
git push origin main
```

### Merge conflict
**Why:** You and a teammate edited the same lines.
**Fix:**

1. Open the file marked `CONFLICT`. You will see:

```
<<<<<<< HEAD
your version
=======
their version
>>>>>>> origin/main
```

2. Keep the correct code. Delete the `<<<<<<<`, `=======`, and `>>>>>>>` lines.
3. Save the file, then run:

```bash
git add .
git commit -m "Resolve merge conflict"
git push origin main
```

### Login failed
GitHub doesn't accept your account password in Git anymore. Use a **Personal Access Token** instead:
**GitHub → Settings → Developer settings → Personal access tokens**. Paste the token when Git asks for a password.

---

## Quick Reminder

```
1. PULL    git pull origin main
2. WORK    edit your code
3. STATUS  git status
4. ADD     git add .
5. COMMIT  git commit -m "message"
6. PUSH    git push origin main
```
