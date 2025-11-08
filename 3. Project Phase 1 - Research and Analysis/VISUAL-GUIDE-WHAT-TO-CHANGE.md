# Visual Guide: What to Change
## The 4 Bright Markers in Your Template

When you open `DASHBOARD-TEMPLATE-MASTER.html`, you'll see these bright comment markers that show you exactly what to change:

---

## ✏️ EDIT SECTION 1: HEADER
**Location:** Line ~590
**What it looks like:**
```html
<!-- ============================================ -->
<!-- ✏️ EDIT SECTION 1: HEADER -->
<!-- Change the subtitle for each new meeting -->
<!-- ============================================ -->
<header>
    <h1>🍫 Chocolat on James</h1>
    <p>Strategic Review Dashboard - Week 1-2 Progress & Platform Decision</p>
</header>
```

**What to change:**
- The subtitle line that says "Week 1-2 Progress & Platform Decision"

**Example for next meeting:**
```html
<p>Strategic Review Dashboard - Week 3-4 Strategy Implementation</p>
```

---

## ✏️ EDIT SECTION 2: MEETING INFO
**Location:** Line ~600
**What it looks like:**
```html
<!-- ============================================ -->
<!-- ✏️ EDIT SECTION 2: MEETING INFO -->
<!-- Update date, time, attendees, focus -->
<!-- ============================================ -->
<div class="meeting-info">
    <div>
        <strong>Meeting Date</strong>
        Monday, November 3, 2025 - 10:00 AM
    </div>
    <div>
        <strong>Attendees</strong>
        Greg Kowalczyk, Dale Guenter, Dan Edwards
    </div>
    <div>
        <strong>Focus</strong>
        Platform Decision & Week 1-2 Review
    </div>
</div>
```

**What to change:**
- Meeting date and time
- Attendees (if different)
- Focus topic

**Example for next meeting:**
```html
<div class="meeting-info">
    <div>
        <strong>Meeting Date</strong>
        Monday, November 10, 2025 - 2:00 PM
    </div>
    <div>
        <strong>Attendees</strong>
        Greg Kowalczyk, Dan Edwards
    </div>
    <div>
        <strong>Focus</strong>
        SEO & Social Media Strategy Review
    </div>
</div>
```

---

## ✏️ EDIT SECTION 3: TAB BUTTONS
**Location:** Line ~620
**What it looks like:**
```html
<!-- ============================================ -->
<!-- ✏️ EDIT SECTION 3: TAB BUTTONS -->
<!-- Update tab labels, add/remove tabs as needed -->
<!-- IMPORTANT: Keep data-tab="xxx" matching the content id="xxx" below! -->
<!-- ============================================ -->
<div class="tabs">
    <button class="tab-button active" data-tab="overview">📊 Executive Overview</button>
    <button class="tab-button" data-tab="progress">✅ Week 1-2 Progress</button>
    <button class="tab-button" data-tab="research">🔍 Market Research</button>
    ...
</div>
```

**What to change:**
- Tab labels (the text between `>` and `</button>`)
- Add new tabs by copying a button line
- Remove tabs by deleting a button line

**Example changes:**
```html
<!-- Change week number -->
<button class="tab-button" data-tab="progress">✅ Week 3-4 Progress</button>

<!-- Add a new tab -->
<button class="tab-button" data-tab="seo">🔍 SEO Strategy</button>

<!-- Remove a tab (just delete the line) -->
```

**⚠️ IMPORTANT:**
- The `data-tab="overview"` part MUST match the `id="overview"` in the content section below
- If you change one, change both!

---

## ✏️ EDIT SECTION 4: TAB CONTENTS
**Location:** Line ~640 and throughout
**What it looks like:**
```html
<!-- ============================================ -->
<!-- ✏️ EDIT SECTION 4: TAB CONTENTS -->
<!-- Replace the content inside each tab with your new meeting data -->
<!-- Keep the structure (div, h2) but change the text, tables, lists -->
<!-- ============================================ -->

<!-- Tab 1: Executive Overview -->
<div id="overview" class="tab-content active">
    <h2>📊 Executive Overview</h2>

    <h3 style="color: #6B4423;">Your Heading Here</h3>
    <p>Your paragraph text here...</p>

    <table class="growth-table">
        <thead>
            <tr>
                <th>Column 1</th>
                <th>Column 2</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Data 1</td>
                <td>Data 2</td>
            </tr>
        </tbody>
    </table>

    <div class="alert success">
        <h4>✅ Key Wins</h4>
        <ul>
            <li>Win 1</li>
            <li>Win 2</li>
        </ul>
    </div>
</div>
```

**What to change:**
- Everything INSIDE the `<div id="overview" class="tab-content active">` tags
- Replace text, numbers, tables with your new data
- Keep the structure (the `<div>`, `<table>`, `<ul>` tags)

**⚠️ What NOT to change:**
- Don't change: `<div id="overview" class="tab-content active">`
- Don't change: class names like `class="growth-table"`
- Don't delete the closing `</div>` at the end

---

## Quick Visual: The Whole Structure

```
DASHBOARD-TEMPLATE-MASTER.html
│
├── [CSS Styling - Lines 1-585]
│   └── ❌ DON'T TOUCH THIS
│
├── ✏️ SECTION 1: Header (~line 590)
│   └── ✅ Change subtitle
│
├── ✏️ SECTION 2: Meeting Info (~line 600)
│   └── ✅ Change date, attendees, focus
│
├── ✏️ SECTION 3: Tab Buttons (~line 620)
│   └── ✅ Change tab labels (optional)
│
├── ✏️ SECTION 4: Tab Contents (~line 640+)
│   ├── Tab 1: Overview
│   │   └── ✅ Replace content
│   ├── Tab 2: Progress
│   │   └── ✅ Replace content
│   ├── Tab 3: Research
│   │   └── ✅ Replace content
│   ├── Tab 4: Market
│   │   └── ✅ Replace content
│   └── ... (more tabs)
│
└── [JavaScript Code - Last ~100 lines]
    └── ❌ DON'T TOUCH THIS
```

---

## Color-Coded: Safe vs. Dangerous

### ✅ **SAFE TO CHANGE** (Green Zone)
```html
✅ Text between > and < tags:
   <p>THIS TEXT IS SAFE TO CHANGE</p>

✅ Numbers and percentages:
   <div class="metric">87.5%</div>  ← Change the 87.5%

✅ List items:
   <li>THIS IS SAFE TO CHANGE</li>

✅ Table data:
   <td>THIS IS SAFE TO CHANGE</td>
```

### ⚠️ **BE CAREFUL** (Yellow Zone)
```html
⚠️ Adding/removing whole sections:
   <div class="alert success">  ← Copy the whole block
       ...content...
   </div>

⚠️ Tab button data-tab must match content id:
   data-tab="overview"  ←→  id="overview"
```

### ❌ **DON'T TOUCH** (Red Zone)
```html
❌ Class names:
   class="growth-table"  ← Keep exactly as-is

❌ CSS (Lines 1-585):
   Everything between <style> and </style>

❌ JavaScript (Last ~100 lines):
   Everything between <script> and </script>

❌ Structure tags (unless copying whole blocks):
   <div>, </div>, <table>, </table>
```

---

## Real Example: Changing Progress Percentage

**BEFORE:**
```html
<div class="status-card">
    <h4>Overall Progress</h4>
    <div class="metric">87.5%</div>
    <div class="progress-bar">
        <div class="progress-fill" style="width: 87.5%">87.5%</div>
    </div>
    <p>7 of 8 deliverables complete</p>
</div>
```

**AFTER (for 95% complete):**
```html
<div class="status-card">
    <h4>Overall Progress</h4>
    <div class="metric">95%</div>
    <div class="progress-bar">
        <div class="progress-fill" style="width: 95%">95%</div>
    </div>
    <p>19 of 20 deliverables complete</p>
</div>
```

**What changed:**
1. `87.5%` → `95%` (in metric div)
2. `width: 87.5%` → `width: 95%` (in progress-fill)
3. `87.5%` → `95%` (inside progress-fill)
4. `7 of 8` → `19 of 20` (in paragraph)

---

## The Golden Rule

> **If you see `<!-- ✏️ EDIT SECTION -->`, you can change what's inside.**
>
> **If you DON'T see that marker, be very careful!**

---

## Quick Checklist for Each New Dashboard

When creating a new dashboard, search for these 4 markers in order:

1. ✏️ EDIT SECTION 1: → Update header subtitle
2. ✏️ EDIT SECTION 2: → Update meeting info
3. ✏️ EDIT SECTION 3: → Update tab labels (if needed)
4. ✏️ EDIT SECTION 4: → Update all tab contents

**That's it!** Those 4 markers tell you exactly where to make changes.

---

## Pro Tip: Use Find

In your text editor:
1. Press **Cmd+F** (Mac) or **Ctrl+F** (Windows)
2. Search for: `✏️ EDIT SECTION`
3. Hit "Next" to jump to each marker
4. Make your changes
5. Repeat for all 4 sections

**Time saved:** Instead of scrolling through 2,500 lines, you jump straight to what needs changing!

---

**You're ready!** Open the template and look for those bright `✏️ EDIT SECTION` markers. Everything you need to change is clearly marked.
