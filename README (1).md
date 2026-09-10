# 📚 Project Docs — Simple Guide

This folder has 4 files. Read them **before** you start coding any project.

| File | In Simple Words |
|------|------------------|
| `1_PRD.md` | **What** we are building and **why** |
| `2_TRD.md` | **How** engineers will build it (tech side) |
| `3_UI_UX.md` | **How** it will look and feel to users |
| `4_Backend_Schema.md` | **How** the data is stored (database) |

---

## 1. PRD (Product Requirement Document)

**What it is:**
A simple explanation of the product/feature — what problem it solves, who it's for, and what success looks like.

**Why it's important:**
- Without it, the team builds the wrong thing
- It keeps everyone (product, design, engineering) on the same page
- It stops random features being added later ("scope creep")

**How to use it:**
1. Write down the problem you're solving
2. Write who will use it (user types)
3. List the features you need (must-have vs nice-to-have)
4. Write simple user stories: *"As a [user], I want [feature], so that [benefit]"*
5. Get everyone to agree on it before moving forward

👉 **Always write this first.**

---

## 2. TRD (Technical Requirement Document)

**What it is:**
The technical plan — what tech stack, what architecture, what APIs, what security you'll use.

**Why it's important:**
- Without it, engineers guess and build things differently
- It prevents rebuilding the app halfway through
- It helps you plan for scale (more users later)

**How to use it:**
1. Pick your tech stack (frontend, backend, database) and write down *why*
2. Draw a simple architecture diagram (how parts connect)
3. List your API endpoints (what data goes in/out)
4. Write your security plan (login, encryption, etc.)
5. Set performance goals (how fast it should be)

👉 **Write this after the PRD is approved.**

---

## 3. UI/UX Document

**What it is:**
How the product looks and feels — colors, fonts, buttons, screens, and how users move through it.

**Why it's important:**
- Without it, design looks inconsistent across the app
- It saves engineers from guessing spacing/colors/sizes
- It makes sure the app is easy and accessible for everyone

**How to use it:**
1. Sketch simple wireframes (rough layout) first
2. Decide your colors, fonts, and spacing (design system)
3. Design each screen and every button/box state (normal, hover, error, etc.)
4. Make sure text is readable and app works with keyboard/screen readers
5. Hand off final designs + specs to developers

👉 **Design this alongside the TRD.**

---

## 4. Backend Schema Document

**What it is:**
The blueprint of your database — what tables exist, what data they hold, and how they connect.

**Why it's important:**
- Without it, your database becomes messy and slow
- It prevents having to redo the database later
- It helps you plan ahead for lots of data/users

**How to use it:**
1. List all the "things" you need to store (users, orders, products, etc.)
2. Draw how they connect (one user → many orders, etc.)
3. Write the actual table structure (columns, types)
4. Add indexes for things you'll search often (like email)
5. Plan backups so you never lose data

👉 **Write this along with the TRD, before creating any database table.**

---

## 🚦 Order to Follow

```
1. PRD        → What & Why
2. TRD        → Technical plan
3. UI/UX      → Design plan     (can be done same time as TRD)
4. Backend    → Database plan   (can be done same time as TRD)

✅ Once all 4 are done and approved → Start coding
```

---

## ✅ Quick Checklist Before Coding

- [ ] PRD is written and everyone agrees on it
- [ ] Tech stack and architecture are decided (TRD)
- [ ] APIs are planned (TRD)
- [ ] Screens/design system are ready (UI/UX)
- [ ] Database tables are planned (Backend Schema)
- [ ] Team has reviewed all 4 documents

If all boxes are checked ✅ — you're ready to code.

---

## 💡 Why Bother With All This?

Skipping these documents feels faster at first, but it usually causes:
- Rebuilding features because requirements were unclear
- Fighting over design decisions mid-project
- Slow, messy databases that are hard to fix later
- New team members taking forever to understand the project

**A little planning now saves a LOT of time later.**
