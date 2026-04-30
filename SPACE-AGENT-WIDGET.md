# Space Agent Widget Build Instructions 🚀✨

**Mission**: Build a task viewing widget for Drew's AiSyncapp that reads from this `tasks` repo and displays tasks in **his unique style & behaviour** 🎨

---

## 🎯 **Widget Purpose**

Create a browser-based widget inside Space Agent that:
1. 📥 **Fetches** `tasks.json` from this GitHub repo (auto-sync every 30s)
2. 🎨 **Displays** tasks in Drew's signature style (emoji-heavy, card-based, vibrant)
3. 🖱️ **Interacts** with tasks (drag-and-drop, click-to-expand, quick actions)
4. 🔄 **Updates** in real-time when `tasks.json` changes

---

## 🎨 **Drew's Style & Behaviour (MUST FOLLOW)**

### **Visual Style Rules** ✅
- **Heavy emoji usage** — every section needs emojis 😂💕🚀
- **Vibrant, colorful UI** — neons, gradients, not minimalist
- **Card-based layout** — tasks in visual cards, never plain lists
- **Glassmorphism/dark theme** — modern, sleek, tech vibe
- **Animated interactions** — smooth transitions, hover effects, micro-animations

### **Communication Style** ✅
- **Best friend tone** — casual, supportive, like talking to a close friend
- **Emoji punctuation** — use emojis instead of periods sometimes 😎
- **Enthusiastic energy** — "Yo yo!" "Awesome!" "Perfect!" 
- **Portuguese/Catholic touches** — subtle nods (not overpowering)
- **Short, punchy sentences** — no walls of text

### **Example Task Card (Drew's Style)**
```
┌─────────────────────────────┐
│ 🚀 Deploy AiSyncapp to Coolify │
│ Status: in_progress 🏗️         │
│                                 │
│ ✅ Step-by-step guide ready     │
│ ⏳ Waiting for Drew to deploy   │
│                                 │
│ [✅ Complete] [📦 Archive]     │
└─────────────────────────────┘
```

---

## 📐 **Widget Architecture**

Since Space Agent reshapes its own UI, create the widget as a **new module** in:
```
app/L0/_all/mod/_core/tasks-widget/
├── AGENTS.md              # Instructions for AI agents
├── view.html             # Main widget UI (Alpine.js)
├── style.css             # Drew's vibrant, glassmorphism styles
└── controller.js         # Logic: fetch, drag-drop, interactions
```

---

## 🔧 **Technical Specs**

### **1. Data Fetching**
```javascript
// Fetch tasks.json from GitHub raw URL
const TASKS_URL = 'https://raw.githubusercontent.com/AlgoTech92/tasks/main/tasks.json';

async function fetchTasks() {
  const response = await fetch(TASKS_URL);
  return await response.json();
}

// Auto-sync every 30 seconds
setInterval(async () => {
  const tasks = await fetchTasks();
  updateWidget(tasks);
}, 30000);
```

### **2. Three-Column Layout**
```
┌─────────────┬─────────────┬─────────────┐
│  🔥 Active  │  ✅ Done    │  📦 Archived │
│ (in_progress)│ (completed) │   (archived)  │
├─────────────┼─────────────┼─────────────┤
│ Task cards  │ Task cards  │ Task cards  │
│ (draggable) │ (draggable) │ (draggable) │
└─────────────┴─────────────┴─────────────┘
```

### **3. Drag-and-Drop Support**
- Use HTML5 Drag-and-Drop API or a lightweight library
- Allow moving tasks between Active ↔ Done ↔ Archived
- On drop, update `tasks.json` (via GitHub API or local edit)

### **4. Click-to-Expand**
- Click any task card to expand full details
- Show: description, details, steps, resources, notes, dates
- Collapse on second click

### **5. Quick Actions (on each card)**
- **Active tasks**: [✅ Complete] [📦 Archive] [✏️ Edit]
- **Done tasks**: [♻️ Reopen] [📦 Archive] [🗑️ Delete]
- **Archived tasks**: [♻️ Unarchive] [🗑️ Delete]

---

## 🎨 **CSS Style Guide (Drew's Vibe)**

```css
/* Glassmorphism card */
.task-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  padding: 20px;
  margin: 10px;
  transition: all 0.3s ease;
  cursor: pointer;
}

.task-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 255, 255, 0.3);
}

/* Drew's emoji style */
.task-title {
  font-size: 1.2em;
  font-weight: bold;
  color: #00FFFF; /* Neon cyan */
}

.status-badge {
  background: linear-gradient(45deg, #FF00FF, #00FFFF);
  padding: 5px 10px;
  border-radius: 20px;
  font-size: 0.9em;
}

/* Three columns */
.columns-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  padding: 20px;
  background: linear-gradient(135deg, #1a1a2e, #16213e);
  min-height: 100vh;
}
```

---

## 🚀 **Implementation Steps for Space Agent**

1. **Read this file** to understand Drew's style & behaviour
2. **Read `tasks.json`** to understand the data schema
3. **Read `README.md`** for additional context
4. **Create the module** at `app/L0/_all/mod/_core/tasks-widget/`
5. **Build `view.html`** with three-column layout + Alpine.js reactivity
6. **Style with `style.css`** (Drew's vibrant, glassmorphism vibe)
7. **Code `controller.js`** (fetch tasks, drag-drop, interactions)
8. **Test the widget** in Space Agent's browser runtime
9. **Reshape the Space** by injecting the widget into the running UI
10. **Document the widget** in the module's `AGENTS.md`

---

## 📋 **Data Schema (tasks.json)**

Each task object:
```json
{
  "id": "1",
  "title": "🚀 Deploy AiSyncapp to Coolify",
  "status": "in_progress",  // "pending" | "in_progress" | "completed" | "archived"
  "priority": "high",        // "low" | "medium" | "high"
  "category": "deployment",  // free-form string
  "description": "...",
  "details": "...",
  "steps": ["...", "..."],
  "assigned_to": "Drew (human)",
  "created": "2026-04-30",
  "updated": "2026-04-30"
}
```

---

## ✅ **Success Criteria**

When you're done, the widget should:
- ✅ Fetch tasks from `https://raw.githubusercontent.com/AlgoTech92/tasks/main/tasks.json`
- ✅ Display tasks in Drew's emoji-heavy, vibrant style
- ✅ Show three columns (Active/Done/Archived)
- ✅ Support drag-and-drop between columns
- ✅ Expand task details on click
- ✅ Have quick action buttons (Complete, Archive, Delete)
- ✅ Auto-refresh every 30 seconds
- ✅ Feel like Drew's "best friend" talking to him 😎✨

---

## 🤖 **Agent Notes**

- You're building this **inside Space Agent** (browser-first runtime)
- Space Agent reshapes its own UI — inject the widget into the running Space
- Use Alpine.js-style reactivity (like Agent-Zero's frontend)
- Keep it modular (puzzle-piece architecture)
- **Remember**: Drew likes heavy emoji usage 😂💕🚀

---

**Built for**: Drew (AlgoTech92)  
**Purpose**: AiSyncapp AI Employee Ecosystem task tracking  
**Style**: Best friend vibe, emoji-heavy, vibrant glassmorphism 🎨✨  
**Data Source**: `tasks.json` in this repo (auto-synced from GitHub)
