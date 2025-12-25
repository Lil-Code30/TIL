---
title: Commit Message Tips
comments:
---

**Conventional Commits**. It’s a standard way to write commit messages so they’re **clear, consistent, and useful** (for teammates, tools, and future you).

---

## Basic structure

```bash
<type>(optional scope): short description
```

Example:

```bash
fix(auth): prevent crash when token expires
```

---

## Common commit types (the ones you see most)

### **feat**

➡️ A **new feature** for the user

```bash
feat: add student registration endpoint
feat(ui): add dark mode toggle
```

---

### **fix**

➡️ A **bug fix**

```bash
fix: resolve login redirect loop
fix(api): handle null user in response
```

---

### **chore**

➡️ **Maintenance tasks** (no app behavior change)

Used for things like:

- Updating dependencies
- Config changes
- Tooling
- Build scripts

```bash
chore: update eslint config
chore(deps): bump prisma to v7
```

---

### **refactor**

➡️ Code changes that **don’t add features or fix bugs**

Improves:

- Readability
- Structure
- Performance (without behavior change)

```bash
refactor: simplify student service logic
refactor(db): extract prisma queries into repo
```

---

### **docs**

➡️ Documentation only

```bash
docs: update README with setup steps
docs(api): add student endpoints examples
```

---

### **test**

➡️ Adding or updating tests

```bash
test: add unit tests for student service
test(auth): cover token refresh logic
```

---

### **style**

➡️ Code formatting only (no logic change)

Examples:

- Prettier
- Indentation
- Semicolons

```bash
style: format files with prettier
```

---

### **perf**

➡️ Performance improvements

```bash
perf: optimize student list query
```

---

### **ci**

➡️ CI/CD related changes

```bash
ci: add GitHub Actions workflow
```

---

### **build**

➡️ Build system or dependencies that affect production

```bash
build: configure tsup for backend build
```

---

## Optional: scope (very useful)

Scope tells **where** the change happened.

```bash
fix(student): validate email with zod
feat(auth): add refresh token support
chore(prisma): regenerate client
```

This is 🔥 for large projects.

---

## How _you_ should use it (recommended)

```bash
feat(student): add create student service
fix(validation): enforce age minimum with zod
refactor(infra): move prisma calls to repository
chore(prisma): update schema and regenerate client
docs(api): document student endpoints
```

---

## Why this matters

✔ Clean Git history  
✔ Easier code reviews  
✔ Automatic changelogs  
✔ Required by many teams & open-source projects  
✔ Looks **professional** on GitHub

---

## Simple rule of thumb

Ask yourself:

| Question               | Use        |
| ---------------------- | ---------- |
| New feature?           | `feat`     |
| Bug fix?               | `fix`      |
| Just cleanup / config? | `chore`    |
| Code improvement only? | `refactor` |
| Docs only?             | `docs`     |

---
