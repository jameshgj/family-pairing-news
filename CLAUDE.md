# Family Pairing News — Claude Code Instructions

This project is a **daily intelligence dashboard** tracking youth safety legislation, parental controls, and competitor activity across social platforms. It is published via GitHub Pages as a single `index.html` file.

## Project Structure

```
index.html              — The full dashboard (HTML + CSS + JS, single file)
briefs/                 — Markdown source briefs (one per day)
CLAUDE.md               — These instructions
```

## How to Add a New Daily Brief

When asked to create a new daily update, follow these steps:

### Step 1: Research the day's news

Search the web for the latest developments in these categories:
- **Youth safety legislation** (federal, state, international)
- **Platform parental control updates** (TikTok Family Pairing, Instagram Teen Accounts, YouTube Family Link, Snapchat Family Center, Discord Family Center, Roblox, Apple/Google, X, BeReal, Pinterest)
- **Legal actions** (lawsuits, fines, regulatory enforcement)
- **Industry signals** (standards bodies, advocacy orgs, policy statements)
- **Media & opinion** (news coverage, op-eds, public sentiment)

Focus on what changed since the last brief. Use real, verifiable sources with links.

### Step 2: Create the markdown brief

Save a new file in `briefs/` named `youth-safety-brief-YYYY-MM-DD.md` following the exact structure of existing briefs. Include:

1. **Top 3 Headlines** — the most significant developments, with source links
2. **Legislation Tracker** — tables for US Federal, US State, UK, EU, Australia, and other jurisdictions
3. **Competitor Watch** — updates per platform (TikTok, Meta/Instagram, YouTube, Snapchat, Discord, Roblox, Apple/Google, X, BeReal, Pinterest)
4. **Industry Signals** — standards bodies, advocacy orgs, research
5. **Legal Actions** — active cases, verdicts, fines
6. **Media & Opinion** — notable coverage and public sentiment

If there is nothing new for a section or platform, say "No new developments" — do not omit the section.

### Step 3: Add the daily brief to `index.html`

Insert a new `daily-brief` block into the correct week section in `index.html`. Follow this structure exactly:

#### Determine the week

- Calculate the ISO week number (YYYY-Www) for the brief's date
- If a `week-section` with that `data-week` already exists, add the new `daily-brief` div **above** existing briefs within that week (newest first)
- If this is a new week, create a new `week-section` block **above** all existing week sections (newest week first)

#### New week section template (only if needed)

```html
<!-- ============================================================ -->
<!-- WEEK: YYYY-Www (Mon D – Mon D) -->
<!-- ============================================================ -->
<div class="week-section" data-week="YYYY-Www">
    <div class="week-header" onclick="toggleWeek(this)">
        <h2>
            Week of Mon D – Mon D, YYYY
            <span class="week-label">Www</span>
        </h2>
        <span class="week-toggle">&#9660;</span>
    </div>
    <div class="week-content">

        <!-- Weekly Summary -->
        <div style="padding: 20px;">
            <div class="weekly-summary">
                <h3>Weekly Summary — Www</h3>
                <ul>
                    <li>Key development 1</li>
                    <li>Key development 2</li>
                </ul>
            </div>
        </div>

        <!-- Daily briefs go here, newest first -->

    </div>
</div>
```

#### Daily brief template

```html
<!-- DAILY BRIEF: YYYY-MM-DD -->
<div class="daily-brief" data-date="YYYY-MM-DD">
    <div class="brief-date">
        <h3>DayOfWeek, Month DD, YYYY</h3>
        <span class="day-badge">YYYY-MM-DD</span>
    </div>

    <!-- TOP HEADLINES -->
    <div class="brief-section" data-category="headlines">
        <div class="section-title" onclick="toggleSection(this)">
            <span class="section-icon">&#128240;</span>
            Top Headlines
        </div>
        <div class="section-body">
            <div class="headline">
                <h4>Headline Title</h4>
                <p>Description of the development.</p>
                <a class="source-link" href="URL" target="_blank">Source Name ↗</a>
            </div>
            <!-- More headlines... -->
        </div>
    </div>

    <!-- LEGISLATION TRACKER -->
    <div class="brief-section" data-category="legislation">
        <div class="section-title" onclick="toggleSection(this)">
            <span class="section-icon">&#9878;</span>
            Legislation Tracker
        </div>
        <div class="section-body">
            <!-- Tables for each jurisdiction -->
            <h4 style="font-size:13px; color:var(--text-muted); margin: 8px 0 6px;">United States — Federal</h4>
            <table class="data-table">
                <thead><tr><th>Bill / Action</th><th>Status</th><th>Notes</th></tr></thead>
                <tbody>
                    <tr><td>Bill name</td><td><span class="status status-active">Active</span></td><td>Notes</td></tr>
                </tbody>
            </table>
            <!-- Add more jurisdiction tables as needed -->
        </div>
    </div>

    <!-- COMPETITOR WATCH -->
    <div class="brief-section" data-category="competitors">
        <div class="section-title" onclick="toggleSection(this)">
            <span class="section-icon">&#128065;</span>
            Competitor Watch
        </div>
        <div class="section-body">
            <div class="competitor-grid">
                <div class="competitor-card" style="border-left-color: var(--tiktok);">
                    <h4><span class="platform-tag tag-tiktok">TikTok</span> Family Pairing</h4>
                    <ul>
                        <li>Update or "No new developments"</li>
                    </ul>
                </div>
                <!-- More competitor cards... -->
            </div>
        </div>
    </div>

    <!-- INDUSTRY SIGNALS -->
    <div class="brief-section" data-category="industry">
        <div class="section-title" onclick="toggleSection(this)">
            <span class="section-icon">&#128161;</span>
            Industry Signals
        </div>
        <div class="section-body">
            <table class="data-table">
                <thead><tr><th>Organization</th><th>Update</th></tr></thead>
                <tbody>
                    <tr><td>Org name</td><td>Update text</td></tr>
                </tbody>
            </table>
        </div>
    </div>

    <!-- LEGAL ACTIONS -->
    <div class="brief-section" data-category="legal">
        <div class="section-title" onclick="toggleSection(this)">
            <span class="section-icon">&#9878;</span>
            Legal Actions
        </div>
        <div class="section-body">
            <table class="data-table">
                <thead><tr><th>Case</th><th>Status</th><th>Jurisdiction</th></tr></thead>
                <tbody>
                    <tr><td>Case name</td><td><span class="status status-active">Active</span></td><td>Jurisdiction</td></tr>
                </tbody>
            </table>
        </div>
    </div>

    <!-- MEDIA & OPINION -->
    <div class="brief-section" data-category="media">
        <div class="section-title" onclick="toggleSection(this)">
            <span class="section-icon">&#128220;</span>
            Media & Opinion
        </div>
        <div class="section-body">
            <div class="headline">
                <h4>Article Title</h4>
                <p>Summary of the coverage or opinion piece.</p>
            </div>
        </div>
    </div>

</div>
<!-- END DAILY BRIEF YYYY-MM-DD -->
```

### Step 4: Update the summary bar counters

Update these counters in the `summary-bar` section of `index.html`:
- **Total Briefs** (`#totalBriefs`) — increment by 1
- **Weeks Tracked** (`#totalWeeks`) — increment if this is a new week
- **Active Legislation** — update count if new bills tracked
- **Platforms Tracked** — update if new platform added
- **Legal Actions** — update count if new cases added

### Step 5: Update the header

- Set `Last updated:` date to today's date
- Increment the version badge if it's a new week (e.g., v1.0 → v1.1)

### Step 6: Update the weekly summary

If adding to an existing week, update the `weekly-summary` `<ul>` to include the new day's key developments. Keep it to 6-10 bullet points for the whole week.

## CSS Classes Reference

### Status badges
- `status-active` — green, for active/in-progress items
- `status-pending` — orange, for pending/upcoming deadlines
- `status-decided` — purple, for decided/completed actions
- `status-effective` — blue, for laws/rules now in effect

### Platform tags
- `tag-tiktok`, `tag-meta`, `tag-youtube`, `tag-snap`, `tag-roblox`, `tag-discord`, `tag-apple`

### Headline modifiers
- `tiktok-relevant` — adds TikTok-colored left border to headlines directly relevant to TikTok/Family Pairing

### Platform border colors (for competitor cards)
- `var(--tiktok)`, `var(--meta)`, `var(--youtube)`, `var(--snap)`, `var(--roblox)`, `var(--discord)`, `var(--apple)`

## Important Rules

1. **Newest first** — newest weeks at the top, newest days at the top within each week
2. **Real sources only** — every headline must link to a verifiable source
3. **Keep it factual** — no speculation or editorializing in the brief itself (opinion section is for reporting on others' opinions)
4. **Carry forward context** — reference prior developments when relevant (e.g., "following the Mar 24 verdict...")
5. **Single file** — all HTML/CSS/JS stays in `index.html`. Do not split into separate files.
6. **Commit after each update** — commit with message format: `Add daily brief: YYYY-MM-DD`
