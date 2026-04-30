# AiSyncapp Tasks 📋✨

**Drew's Personal Task Tracker** — Built for AiSyncapp's AI Employee Ecosystem 🤖💼

---

## 🎨 **Style & Behaviour Guide for Space Agent Widget**

When building the task viewing widget, follow these style rules:

### **Visual Style (Drew's Preferences)**
- ✅ **Heavy emoji usage** — every section needs emojis 😂💕🚀
- ✅ **Vibrant, colorful UI** — not minimalist or corporate
- ✅ **Card-based layout** — tasks in visual cards, not plain lists
- ✅ **Glassmorphism/dark theme** — modern, sleek, tech vibe
- ✅ **Animated interactions** — smooth transitions, hover effects

### **Communication Style (Drew's Voice)**
- ✅ **Best friend tone** — casual, supportive, like talking to a close friend
- ✅ **Emoji punctuation** — use emojis instead of periods sometimes 😎
- ✅ **Enthusiastic energy** — "Yo yo!" "Awesome!" "Perfect!" 
- ✅ **Portuguese/Catholic touches** — subtle nods to his heritage (not overpowering)
- ✅ **Short, punchy sentences** — no walls of text

### **Task Display Behavior**
- ✅ **Three columns**: 
  - 🔥 **Active** (in_progress)
  - ✅ **Done** (completed) 
  - 📦 **Archived** (archived/paused)
- ✅ **Click to expand** — show full task details, notes, related URLs
- ✅ **Drag & drop** — move tasks between columns
- ✅ **Quick actions** — mark complete, archive, delete with one click
- ✅ **Real-time updates** — widget should refresh when `tasks.json` changes

### **Data Source**
The widget should read from **`tasks.json`** (machine-readable) in this repo.
- Format: Array of task objects (see `tasks.json` for schema)
- Auto-sync: Poll GitHub raw content every 30 seconds
- URL: `https://raw.githubusercontent.com/AlgoTech92/tasks/main/tasks.json`

---

## 📂 **Repo Structure**
```
tasks/
├── README.md              # This file (style guide + purpose)
├── tasks.json             # Machine-readable task data (widget reads this)
├── SPACE-AGENT-WIDGET.md # Instructions for Space Agent to build the widget
└── archive/              # Archived task details (optional)
```

---

## 🚀 **Quick Start for Space Agent**

1. **Read this README** to understand Drew's style & behaviour
2. **Check `tasks.json`** to see the data schema
3. **Read `SPACE-AGENT-WIDGET.md`** for widget specs
4. **Build the widget** that:
   - Fetches `tasks.json` from this repo
   - Displays tasks in Drew's style (emoji-heavy, card-based)
   - Supports drag-and-drop between Active/Done/Archived
   - Updates in real-time when tasks change

---

## 💡 **Example Task Display (Drew's Style)**

```
📋 ACTIVE TASKS 🔥

┌─────────────────────────────┐
│ 🚀 Deploy AiSyncapp to Coolify │
│ Status: in_progress 🏗️         │
│                                 │
│ ✅ Step-by-step guide ready     │
│ ⏳ Waiting for Drew to deploy   │
│                                 │
│ [✅ Complete] [📦 Archive]     │
└─────────────────────────────┘

┌─────────────────────────────┐
│ 🔧 Fix Cloudflare WAF Block  │
│ Status: archived 📦            │
│                                 │
│ ❌ Error 1010 - WAF violation  │
│ ⏳ Blocked by Cloudflare/Traefik│
│                                 │
│ [♻️ Unarchive] [🗑️ Delete]    │
└─────────────────────────────┘
```

---

## 🤖 **AI Employee Integration**

This task tracker is part of Drew's **AiSyncapp AI Employee Ecosystem**:
- **Humans hire AI agents** as specialized "employees" 
- **Tasks** can be assigned to AI agents (Nova 🤖, Pixel ⚡, Blaze 🔥)
- **Widget** runs inside AiSyncapp (Open-WebUI fork)
- **Space Agent** builds the widget (browser-first, reshapes its own UI)

---

**Created**: 2026-04-30  
**Owner**: Drew (AlgoTech92)  
**Purpose**: Task tracking for AiSyncapp development  
**Style**: Emoji-heavy, best-friend vibe, card-based UI 😎✨
