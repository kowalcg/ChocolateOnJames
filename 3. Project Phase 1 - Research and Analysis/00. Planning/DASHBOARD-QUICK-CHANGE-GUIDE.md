# Dashboard Quick Change Guide
## How to Create a New Meeting Dashboard in 15 Minutes

**Last Updated:** November 3, 2025

---

## Quick Overview

You have a master dashboard template that's already styled and functional. To create a new dashboard for each meeting/week, you only need to update **6 KEY SECTIONS** by copying/pasting new content.

---

## The 6 Things You Need to Change

### ✅ 1. **HEADER SECTION** (Lines 588-606)
**What to change:**
- Meeting subtitle
- Meeting date
- Attendees
- Meeting focus

**Where to find it:**
Search for: `<header>` (around line 588)

**Example Change:**
```html
<!-- CURRENT -->
<p>Strategic Review Dashboard - Week 1-2 Progress & Platform Decision</p>

<!-- CHANGE TO -->
<p>Strategic Review Dashboard - Week 3-4 Progress & Strategy Implementation</p>
```

---

### ✅ 2. **MEETING INFO BOX** (Lines 593-606)
**What to change:**
- Date and time
- Attendees names
- Focus topic

**Where to find it:**
Search for: `<div class="meeting-info">` (around line 593)

**Example Change:**
```html
<!-- CURRENT -->
<strong>Meeting Date</strong>
Monday, November 3, 2025 - 10:00 AM

<!-- CHANGE TO -->
<strong>Meeting Date</strong>
Monday, November 10, 2025 - 2:00 PM
```

---

### ✅ 3. **TAB BUTTONS** (Lines 608-618)
**What to change:**
- Tab names/labels
- Tab emojis (if needed)
- Number of tabs (add/remove as needed)

**Where to find it:**
Search for: `<div class="tabs">` (around line 608)

**Example:**
```html
<button class="tab-button active" data-tab="overview">📊 Executive Overview</button>
<button class="tab-button" data-tab="progress">✅ Week 3-4 Progress</button>
<button class="tab-button" data-tab="strategy">🎯 New Strategy Items</button>
```

**IMPORTANT:** Keep the `data-tab="xxx"` attribute - this must match the tab content ID!

---

### ✅ 4. **TAB CONTENTS** (Multiple sections starting at line 621)
**What to change:**
- All the actual content inside each tab
- Tables, lists, metrics, charts

**Where to find it:**
Search for: `<!-- Tab 1:` or `<!-- Tab 2:` etc.

**Structure of each tab:**
```html
<!-- Tab 1: Executive Overview -->
<div id="overview" class="tab-content active">
    <h2>📊 Executive Overview</h2>

    <!-- YOUR CONTENT GOES HERE -->
    <!-- Replace all the text, tables, lists with new content -->

</div>
```

**KEY RULE:** The `id="overview"` MUST match the tab button's `data-tab="overview"`

---

### ✅ 5. **PROGRESS METRICS** (Various locations)
**What to change:**
- Percentage complete (87.5% → new %)
- Deliverables completed (7/8 → new numbers)
- Status cards

**Where to find it:**
Search for: `<div class="metric">` or `progress-fill`

**Example:**
```html
<!-- CURRENT -->
<div class="metric">87.5%</div>
<div class="progress-bar">
    <div class="progress-fill" style="width: 87.5%">87.5%</div>
</div>

<!-- CHANGE TO -->
<div class="metric">95%</div>
<div class="progress-bar">
    <div class="progress-fill" style="width: 95%">95%</div>
</div>
```

---

### ✅ 6. **ACTION ITEMS & ALERTS** (Various locations)
**What to change:**
- Success alerts (green boxes)
- Warning alerts (yellow boxes)
- Action items lists

**Where to find it:**
Search for: `<div class="alert success">` or `<div class="alert warning">`

**Example:**
```html
<div class="alert success">
    <h4>✅ Key Wins This Week</h4>
    <ul>
        <li><strong>NEW WIN:</strong> Description here</li>
        <li><strong>NEW WIN:</strong> Another achievement</li>
    </ul>
</div>
```

---

## Step-by-Step Process

### **For Each New Meeting Dashboard:**

1. **Copy the template file**
   - File: `DASHBOARD-TEMPLATE-MASTER.html`
   - Save as: `MEETING-DASHBOARD-NOV-10.html` (use new date)

2. **Update Header (2 minutes)**
   - Search for `<header>`
   - Change the subtitle and meeting info

3. **Update Tabs if needed (3 minutes)**
   - Keep same tabs? Skip this
   - Add/remove tabs? Update the `<div class="tabs">` section

4. **Update Tab Contents (10 minutes)**
   - Go through each `<!-- Tab X: -->` section
   - Copy/paste your new content
   - Update tables, lists, metrics

5. **Double-check (2 minutes)**
   - Open in browser
   - Click through all tabs
   - Make sure everything shows correctly

---

## Quick Reference: Common Elements

### **Creating a Table:**
```html
<table class="growth-table">
    <thead>
        <tr>
            <th>Column 1</th>
            <th>Column 2</th>
            <th>Column 3</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Data 1</td>
            <td>Data 2</td>
            <td>Data 3</td>
        </tr>
    </tbody>
</table>
```

### **Creating a Success Alert:**
```html
<div class="alert success">
    <h4>✅ Title</h4>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>
</div>
```

### **Creating a Warning Alert:**
```html
<div class="alert warning">
    <h4>⚠️ Title</h4>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>
</div>
```

### **Creating Status Cards:**
```html
<div class="status-grid">
    <div class="status-card">
        <h4>Card Title</h4>
        <div class="metric">87.5%</div>
        <p>Description text</p>
    </div>
    <div class="status-card warning">
        <h4>Warning Card</h4>
        <div class="metric">50%</div>
        <p>Description text</p>
    </div>
</div>
```

---

## Don't Touch These Sections!

❌ **Lines 1-585** - All the CSS styling (leave this alone!)
❌ **Lines 2400+** - JavaScript code at the bottom (leave this alone!)
❌ Class names like `class="alert success"` (keep these exactly as-is)
❌ The structure tags like `<div>`, `</div>` (be careful with these)

---

## Troubleshooting

### **Problem: Tab doesn't show content when clicked**
**Solution:** Make sure the tab button's `data-tab="xxx"` matches the content `id="xxx"`

### **Problem: Styling looks broken**
**Solution:** You probably deleted a `</div>` tag. Compare with the template.

### **Problem: Can't find where to change something**
**Solution:** Use Find (Cmd+F / Ctrl+F) to search for the text you see on the page

---

## Time-Saving Tips

1. **Prepare your content first** - Write all your updates in a separate document, then copy/paste into the HTML

2. **Use Find & Replace** - If you need to change "Week 1-2" to "Week 3-4" everywhere, use Find & Replace

3. **Keep the template clean** - Never edit `DASHBOARD-TEMPLATE-MASTER.html` - always make a copy first!

4. **Test in browser** - After each major change, refresh your browser to see how it looks

---

## Next Steps

1. Review the template file: `DASHBOARD-TEMPLATE-MASTER.html`
2. Use the content planning sheet: `DASHBOARD-CONTENT-PLANNER.md`
3. Create your first new dashboard using this guide

**Questions?** This guide covers 90% of what you'll need to change. For special requests, you can always ask for help!
