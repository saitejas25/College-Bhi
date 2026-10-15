# ⚡ College Bhai — All-in-One Student Productivity & Campus Tracker

**College Bhai** is a modern, responsive, single-page web dashboard designed specifically for college students. It centralizes course attendance tracking, assignment deadlines, weekly class schedules, a Pomodoro study timer, and college hackathon/event calendars into a sleek, unified, dark/light mode interface.

Built using **React**, **Tailwind CSS**, **Lucide Icons**, and **LocalStorage** for zero-install browser persistence. The timetable PDF reader loads PDF.js from a CDN; PDF contents are extracted locally in the browser and are not uploaded.

On first launch, create a student profile to personalize the dashboard. The app starts with empty academic data; add your own subjects, assignments, events, timetable, and grades. No login or online account is required, and profile and dashboard data are stored in the current browser.

---

## 🚀 Quick Start

### Option 1: Direct Browser Launch (Zero Installation)
Simply double-click `start-dashboard.bat` or open `index.html` directly in any modern browser (Chrome, Edge, Brave, Firefox, Safari).

### Option 2: Local HTTP Server (PowerShell)
Right-click `server.ps1` and select **Run with PowerShell**, or execute:
```powershell
powershell -ExecutionPolicy Bypass -File server.ps1
```
This serves the application locally at `http://localhost:5173/`.

---

## 🌟 Core Modules & Features

### 1. Header & Quick Summary
- **Real-Time Clock & Date**: Displays formatted day, date, and live digital time.
- **Inspirational Quote of the Day**: Rotating academic and growth mindset quotes with a shuffle button (`✨`).
- **Quick Stat Badges (Overview KPIs)**:
  - **Overall Attendance %**: Aggregate percentage across all enrolled courses with safe/at-risk indicators.
  - **Active Study Tasks**: Count of pending assignments with high-priority breakdown.
  - **Upcoming Events**: Campus events happening in the next 14 days with RSVP counter.
  - **Pomodoro Deep Work**: Focus sessions and minutes completed today against daily target.
- **Dark / Light Theme Toggle**: Seamless shadcn/ui aesthetic with persistent theme preference in `localStorage`.
- **Data Management**:
  - **Export Backup (JSON)**: Save all subjects, tasks, events, and timetable to a `.json` backup file.
  - **Import Backup**: Restore your saved configuration on any device.

---

### 2. Attendance Tracker Module
Designed specifically around university 75% attendance regulations.
- **Course Attributes**:
  - Subject Name (e.g., *Data Structures & Algorithms*)
  - Subject Code (e.g., *CS301*)
  - Total Classes Held
  - Classes Attended
  - Minimum Required % (default 75%, customizable per subject from 50% to 100%)
- **Color-Coded Visual Progress Bar**:
  - 🟢 **Emerald**: When attendance is $\ge$ required threshold.
  - 🔴 **Rose/Amber**: When attendance falls below required threshold.
  - Target marker line indicates exactly where the 75% cutoff sits on each subject's progress bar.
- **One-Click Quick Daily Logging**:
  - **`+ Present`**: Increments attended and total classes held by 1.
  - **`+ Absent`**: Increments total classes held by 1 (attended stays unchanged).
  - **`Undo`**: Reverts the last logged action to quickly correct accidental clicks.
- **Smart Mathematical Calculation Engine**:
  - **If Attendance is Safe ($\ge 75\%$)**:
    $$\text{Bunkable Classes } X = \left\lfloor \frac{\text{Attended}}{R} - \text{Total} \right\rfloor \quad \text{where } R = \frac{\text{Required \%}}{100}$$
    *Displays: "🎉 You can bunk X more classes and still maintain 75%!"*
  - **If Attendance is in Shortage ($< 75\%$)**:
    $$\text{Consecutive Classes Needed } Y = \left\lceil \frac{R \cdot \text{Total} - \text{Attended}}{1 - R} \right\rceil$$
    *Displays: "🚨 Attendance Shortage! You need to attend Y more consecutive classes to reach 75%."*

---

### 3. Study & Task Manager Module
- **Priority-Driven To-Do List**:
  - Tag tasks as **High** (Red), **Medium** (Amber), or **Low** (Green).
  - Associate tasks with specific enrolled subjects.
  - Due date picker with smart countdown labels: *Overdue!*, *Due Today*, or *In X days*.
  - Notes field for lab requirements, submission portals, and code snippets.
  - Strike-through checkbox with celebration confetti effect upon completion.
  - Filter by status (**All**, **Active**, **Completed**), by priority, and live text search.
- **Weekly Class & Study Timetable**:
  - Day-wise selector (**Monday through Sunday**).
  - Manage timetable slots with Time, Subject, Venue/Room (*LH-101*, *CS Lab 3*), and Slot Type (*Lecture*, *Lab*, *Tutorial*, *Self Study*, *Project*).
  - Add and remove timetable slots with persistent storage.
  - Upload a text-based college timetable PDF to extract weekday class entries, review a day-by-day preview, and confirm before replacing the saved schedule. PDF extraction runs in the browser; scanned image-only PDFs are not supported.

---

### 4. Built-in Pomodoro Study Timer
- **Science-Backed Focus Cycles**:
  - **Focus Mode**: 25 minutes of distraction-free study.
  - **Short Break**: 5 minutes of rest.
  - **Long Break**: 15 minutes of recovery.
- **Interactive UI**:
  - High-precision circular SVG progress ring.
  - Play, Pause, Reset, and Skip controls.
  - **Subject Tagging**: Link your active focus session to a specific course.
  - **Gentle Bell Chime**: Synthesized via the browser's native **Web Audio API** (no external audio files required, works 100% offline).
  - Daily session and study minute counter saved automatically.

---

### 5. College Events & Hackathon Calendar Module
- **Categorized Event Tracking**:
  - **Hackathons** 💻, **Festivals** 🎭, **Club Meets** 🤝, **Seminars** 🎓, **Exams** 📝, **Workshops** 🛠️.
- **Calendar PDF Import**: Upload a text-based college calendar PDF, automatically detect dated events and categorize them, review/edit each event, and add them to your calendar. PDF processing stays in the browser; scanned image-only calendars are not supported.
- **Dual Display Modes**:
  - **Card Grid View**: Rich visual cards with badges and metadata.
  - **Compact List View**: Streamlined tabular agenda.
- **Smart Countdown Badges**:
  - Real-time days difference: *Today!*, *Tomorrow*, *In 3 days*, or *Past Event*.
- **RSVP Tracking**:
  - One-click toggle between **Going** (✅), **Interested** (⭐), and **Not Decided**.
- **Event Creation**:
  - Title, Category, Date, Time, Venue, and Description fields.

---

### 6. CGPI & SGPA Academic Performance Calculator
- **Semester-Wise SGPA & Cumulative CGPI Calculation**:
  - Credit-weighted calculation engine across all college semesters:
    $$\text{CGPI} = \frac{\sum (\text{Credits}_i \times \text{SGPA}_i)}{\sum \text{Credits}_i}$$
  - Dual calculation options: direct semester SGPA/credits input or granular course-by-course breakdown.
  - Course-level grade point computation from credits and standard 10-point grades:
    $$\text{Semester SGPA} = \frac{\sum (\text{Course Credits} \times \text{Grade Points})}{\sum \text{Course Credits}}$$
- **Multi-University Percentage Conversion**:
  - **VTU / CBSE Formula**: $\text{Percentage} = \text{CGPI} \times 9.5$
  - **AICTE Formula**: $\text{Percentage} = (\text{CGPI} - 0.75) \times 10$
  - **Direct Multiplier**: $\text{Percentage} = \text{CGPI} \times 10$
  - Switchable via instant one-click toggle with real-time recalculation.
- **Academic Honors Classification**:
  - Instant classification badge based on cumulative score:
    - **First Class with Distinction**: $\text{CGPI} \ge 7.75$ (Emerald)
    - **First Class**: $\text{CGPI} \ge 6.75$ (Blue)
    - **Higher Second Class**: $\text{CGPI} \ge 6.00$ (Amber)
    - **Second Class**: $\text{CGPI} \ge 5.00$ (Orange)
    - **Pass Class**: $\text{CGPI} \ge 4.00$ (Zinc)
- **Target CGPI Planner & What-If Predictor**:
  - Set target graduation CGPI (e.g., 8.50) and degree credit requirement (e.g., 160 credits).
  - Calculates the required SGPA across remaining semesters:
    $$\text{Required Future SGPA} = \frac{(\text{Target CGPI} \times \text{Total Credits}) - (\text{Current CGPI} \times \text{Completed Credits})}{\text{Total Credits} - \text{Completed Credits}}$$
  - Feasibility status indicator warns if required score exceeds 10.0 or celebrates if already achieved.
- **Visual Analytics & Degree Progress**:
  - Radial score dial with glowing color dynamics (emerald/amber/rose).
  - Semester-by-semester SGPA trend sparkline bar graph.
  - Degree completion progress bar tracking credits earned toward degree completion.
- **10-Point Scale Reference Guide**:
  - Embedded quick lookup sheet: Outstanding (`O`: 10), Excellent (`A+`: 9), Very Good (`A`: 8), Good (`B+`: 7), Above Average (`B`: 6), Average (`C`: 5), Pass (`P`: 4), Fail (`F`: 0).

---

## 📐 Layout Architecture & Navigation

### 1. Overall Shell
- **Fixed Sidebar (Desktop)**: 224px fixed left sidebar (`w-[224px] fixed inset-y-0 left-0`) providing instant, persistent navigation.
- **Mobile Responsive Drawer**: On small screens, collapses into a top hamburger menu that opens a slide-over navigation drawer with backdrop blur.
- **Independent Scroll**: The right-hand main content area scrolls independently (`overflow-y-auto`) while the left sidebar remains anchored.

### 2. Sidebar Layout
- **Brand Header**: Modern gradient logo icon, app title (**College Bhai**), and version badge.
- **Primary Navigation Links** (Active link highlighted in rich indigo):
  1. **Dashboard** (`layoutDashboard`)
  2. **My Tasks** (`checkSquare`) with live pending count badge
  3. **Attendance** (`userCheck`) with red shortage indicator
  4. **Events** (`sparkles`) with upcoming event count
- **Tools & Utilities Section**:
  - **CGPI Calc** (`award`)
  - **Timetable** (`calendar`)
  - **Study Sprint** (`clock`)
- **Student Profile Chip (Bottom)**:
  - Displays student initials avatar, name, and year/branch.
  - Clicking opens an interactive **Profile Modal** to customize your name and academic branch.

---

## 🌟 Core Pages & Layout

### 1. Dashboard Page
- **Motivational Quote Banner**: Daily inspirational quote with one-click refresh button.
- **3 Stat Cards in a Row**:
  - **Pending Tasks**: Active pending assignments count with High Priority breakdown badge.
  - **Attendance %**: Aggregate semester percentage with Safe vs Shortage badge.
  - **Upcoming Events**: Calendar events count with RSVP "Going" tracker.
- **2-Column Grid**:
  - **Pending Tasks List**: Today's active tasks with circle completion toggles and priority badges.
  - **Next Events List**: Campus events with square date blocks (`MMM` + `DD`), venue, and days remaining badge (*Today!*, *Tomorrow*, *In X days*).
- **Full-Width Subject Attendance Progress Bars**:
  - Course name, code, attended/held numbers, and percentage badge.
  - Gradient progress bars with 75% threshold marker line.
  - Smart calculation text: *"You can bunk X more lectures"* or *"Must attend next Y consecutive classes to reach 75%"*.

### 2. Tasks Page (My Tasks)
- **Header**: Active task count + "+ Add Task" button.
- **Collapsible Add-Task Form**: Inline expandable drawer to quickly add a task with title, subject dropdown, due date, priority (High, Medium, Low), and optional notes.
- **Filter Controls**:
  - Status filter chips: **All**, **Pending**, **Completed** with live counters.
  - Priority dropdown filter: **All Priorities**, **High**, **Medium**, **Low**.
  - Live search bar.
- **Card List**:
  - Circular checkbox to mark complete with celebratory confetti.
  - Priority badge, subject tag, due date countdown label, and delete action.

### 3. Attendance Page
- **3 Summary Stat Cards**:
  - **Overall Attendance %**: Aggregate semester percentage with safe/shortage status.
  - **Classes Attended**: Total lectures attended vs total held, plus lectures missed count.
  - **Subjects at Risk**: Count of courses below 75% vs courses safely above target.
- **Red Shortage Warning Banner**:
  - Automatically alerts the student when any subject drops below 75%.
  - Lists the offending subjects by name and urges attendance to avoid exam detention.
- **Per-Subject Cards**:
  - Visual color-coded progress bar with threshold cutoff line.
  - Total held and attended counters.
  - One-tap **`+ Present`**, **`+ Absent`**, and **`Undo`** buttons.
  - Edit and delete actions.

### 4. Events Page
- **Category Filter Chips**: Across the top (**All Categories**, **Hackathons**, **Festivals**, **Club Meets**, **Seminars**, **Exams**, **Workshops**) plus RSVP filter dropdown and search bar.
- **Split Sections**:
  - **Upcoming Events**: Active and future events sorted chronologically.
  - **Past Events**: Completed events archived with subtle muted styling.
- **Event Cards**: Square date block (`monthStr` + `dayStr`), title, category badge, venue, time, description, and one-tap RSVP toggle.

### 5. CGPI & SGPA Academic Performance Calculator
- Credit-weighted SGPA & CGPI calculations with UGC/University 10-point scale.
- Multi-formula percentage conversions (VTU/CBSE, AICTE, Direct).
- Target CGPI forecasting and honors classification.

---

## 🎨 Design & UX Aesthetics
- **shadcn/ui Inspired**: Clean zinc/slate dark surfaces (`#0a0d14` background, `#111726` cards, `#1e293f` borders).
- **Responsive Layout**: Adapts gracefully across desktop monitors, laptops, tablets, and smartphones.
- **Zero-Dependency Architecture**: No `node_modules` or build step required to run.

---

## 💾 LocalStorage Data Schema

All data keys are prefixed with `collegebhai_`:
| LocalStorage Key | Description |
| :--- | :--- |
| `collegebhai_profile_v1` | Student name and branch/year for the profile chip |
| `collegebhai_theme` | `'dark'` or `'light'` mode preference |
| `collegebhai_subjects_v1` | Array of enrolled subjects with attendance and undo history |
| `collegebhai_tasks_v1` | Array of study tasks with priority and due dates |
| `collegebhai_events_v1` | Array of campus events and RSVP states |
| `collegebhai_timetable_v1` | Weekly schedule mapped by day (Mon-Sun) |
| `collegebhai_pomodoro_v1` | Daily focus count and minutes logged |
| `collegebhai_cgpi_v1` | Target CGPI, degree credits, conversion formula, semesters, courses, and SGPA history |

---

*Created with ❤️ for students striving for academic excellence and campus balance.*
