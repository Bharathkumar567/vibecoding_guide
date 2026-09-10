# UI/UX DOCUMENT - Complete Guide

## Table of Contents
1. What is UI/UX Document?
2. Purpose & Importance
3. Who Creates It?
4. When to Create It?
5. Complete Structure & Components
6. Design System Specifications
7. Component Library
8. Real Examples
9. Best Practices
10. Template & Checklist

---

## 1. WHAT IS UI/UX DOCUMENT?

**UI/UX Document** is a comprehensive specification that defines:
- **HOW** the product LOOKS visually
- **HOW** users INTERACT with it
- **WHAT** components are available
- **HOW** the user experience flows
- **WHAT** design system is used
- **HOW** it works on all devices
- **HOW** accessible it is

### Key Characteristics:
- **Visual specifications** - pixel-perfect design
- **Interaction details** - how things respond to user actions
- **Component-based** - reusable UI components
- **Accessibility-focused** - WCAG 2.1 AA standards
- **Device-inclusive** - mobile, tablet, desktop
- **Complete** - all screens and states documented
- **Development-ready** - engineers can code from this

### Who Reads UI/UX Document?
- Product Designers ✓
- Frontend Engineers ✓
- QA Engineers ✓
- Stakeholders ✓
- Developers ✓
- Design Systems Team ✓

---

## 2. PURPOSE & IMPORTANCE

### Why Is UI/UX Document Important?

**Design Alignment:**
- All designers follow same standards
- Consistency across the product
- Clear design language
- Faster design iteration

**Quality & User Experience:**
- Users have smooth, intuitive experience
- Reduced learning curve
- Fewer usability issues
- Higher satisfaction

**Engineering Efficiency:**
- Engineers know exactly what to build
- Less back-and-forth on design details
- Faster development
- Fewer design changes during coding

**Accessibility:**
- Ensures product is usable by everyone
- WCAG compliance documented
- Keyboard navigation planned
- Screen reader support specified

**Consistency:**
- Component reuse reduces redundancy
- Design tokens ensure consistency
- Faster feature development
- Easier to maintain

**Documentation:**
- Serves as design reference
- Helps onboard new designers
- Records design decisions
- Historical context for changes

---

## 3. WHO CREATES IT?

### Primary Owner: **Product/UX Designer**

**Responsibilities:**
- Leads design process
- Creates wireframes and mockups
- Defines interaction patterns
- Ensures usability
- Documents design decisions
- Maintains design consistency

### Contributors:

**UX Researchers:**
- Provide user research insights
- Conduct usability testing
- Identify pain points
- Validate design solutions

**Interaction Designers:**
- Design micro-interactions
- Specify animations
- Plan state transitions
- Define gestures

**Visual Designers:**
- Create high-fidelity designs
- Define visual hierarchy
- Choose typography
- Select color palette

**Accessibility Specialist:**
- Ensures WCAG compliance
- Tests with assistive technologies
- Validates color contrast
- Reviews keyboard navigation

**Frontend Engineers:**
- Provide implementation insights
- Identify constraints
- Validate technical feasibility
- Suggest optimizations

### Sign-off Required From:
- Lead Designer ✓
- Product Manager ✓
- Engineering Lead ✓ (technical feasibility)
- Accessibility Lead ✓ (if required)

---

## 4. WHEN TO CREATE IT?

### Timeline in Product Development:

```
User Research → Wireframes → Mockups → Prototypes → Handoff → Dev

Week 1-2:      Week 2-3:    Week 3-4:   Week 4-5:    Week 5:     Week 6+:
- Research     - Low-fi     - High-fi   - Clickable  - Final      - Coding
- Interviews   - Sketches   - Detailed  - Interactive- Approval   - Testing
- Usability    - User flows - Visual    - User test  - Assets
  gaps         - Feedback   design      - Refinement - Specs
```

### Trigger Points for UI/UX Document:

✅ **After PRD approval** (with TRD in parallel)
✅ **Before engineering starts coding**
✅ **For new features or major redesigns**
✅ **For new user flows**
✅ **When changing design system**

### Timeline Considerations:

- **Simple feature:** 2-3 weeks design
- **Medium feature:** 3-4 weeks design
- **Complex system:** 4-8 weeks design
- **Before PRD freeze:** Research complete
- **Before design freeze:** Design complete

---

## 5. COMPLETE STRUCTURE & COMPONENTS

### Section 1: COVER PAGE & METADATA

```markdown
# UI/UX DESIGN DOCUMENT

**Product/Feature:** [Product Name]
**Version:** 1.0
**Document Owner:** [Lead Designer Name]
**Created Date:** [Date]
**Last Updated:** [Date]
**Status:** WIP / In Review / Final / Active

**Key Stakeholders:**
- Lead Designer: [Name]
- Product Manager: [Name]
- Engineering Lead: [Name]
- Accessibility Lead: [Name]

**Approval Sign-off:**
- Design: [Signature] Date: ___
- Product: [Signature] Date: ___
- Engineering: [Signature] Date: ___

**Related Documents:**
- PRD: [Link to PRD]
- TRD: [Link to TRD]
- Design Files: [Figma link]
- Prototype: [Prototype link]
```

---

### Section 2: DESIGN VISION & PRINCIPLES

**Purpose:** 
High-level design philosophy and goals

**Length:** 
1-2 pages

```markdown
## Design Vision & Principles

### 2.1 Design Vision

"Make code review enjoyable and insightful, not painful and tedious.
Developers should spend minutes reviewing code, not hours. The tool
should be so intuitive that new developers need zero training."

### 2.2 Design Goals

1. **Reduce Friction** - Make code review quick and easy
2. **Build Confidence** - Provide clear, actionable feedback
3. **Educate** - Help developers learn best practices
4. **Respect Time** - Don't waste developer time
5. **Delight** - Make the experience pleasant

### 2.3 Design Principles

**1. Clarity Over Cleverness**
- Clear labeling
- Obvious interactions
- No hidden features
- Straightforward language

Example: "Shows findings" vs. "Presents analysis results"

**2. Consistency**
- Same patterns work the same way everywhere
- Predictable layouts
- Familiar components
- Standard terminology

Example: All buttons have the same interaction style

**3. Feedback**
- Always inform user of system status
- Show progress for long operations
- Acknowledge user actions
- Clear error messages

Example: Loading spinner during analysis, success toast after

**4. Efficiency**
- Respect developer time
- Minimize clicks to get value
- Quick feedback loops
- Keyboard shortcuts for power users

Example: Findings visible in GitHub without leaving GitHub

**5. Accessibility**
- Works for everyone
- Keyboard navigable
- Screen reader compatible
- Color-blind friendly

Example: Use icons + text, not color alone

### 2.4 Target Users & Personas

**Primary: Senior Developer (Sarah)**
- Goal: Quickly review code
- Pain: Spends 2-4 hours on reviews
- Needs: Fast, integrated, no context switching

**Secondary: Junior Developer (Alex)**
- Goal: Learn from feedback
- Pain: Feedback not educational
- Needs: Clear explanations, resources

**Tertiary: CTO (Marcus)**
- Goal: See team metrics
- Pain: No visibility into code quality
- Needs: Dashboard, analytics, reports

---

### Section 3: USER RESEARCH & INSIGHTS

**Purpose:** 
Document research findings that informed design

**Length:** 
1-2 pages

```markdown
## User Research & Insights

### 3.1 Research Conducted

**Interviews:** 15 senior developers
- Questions about pain points
- Current workflow
- Tool preferences
- Feature wishlist

**Key Finding:** "The biggest pain is context switching.
If I have to leave GitHub, I'm already frustrated."

**Surveys:** 200 developers
- Time spent on reviews: Average 2.5 hours/day
- Biggest frustration: Waiting for review (mentioned by 65%)
- Willing to pay: 65% said "definitely" or "probably"

**Usability Testing:** 8 sessions with prototypes
- Finding: Users expected findings in GitHub itself
- Finding: Explanations were valued highly
- Finding: Dashboard metrics helped CTOs

### 3.2 Design Implications

| Finding | Design Solution |
|---------|-----------------|
| Context switching painful | GitHub native integration (no separate tool) |
| Waiting for review | Real-time feedback |
| Inconsistent feedback | Standardized AI review |
| Need for education | Link resources to every finding |
| Need for metrics | Admin dashboard with analytics |

### 3.3 Accessibility Audit

**Current State (if redesign):**
- Color contrast: Some text too light
- Keyboard nav: Tab order broken
- Screen reader: Missing ARIA labels
- Mobile: Text too small

**Design Targets:**
- WCAG 2.1 Level AA
- Keyboard navigable (Tab, Enter, Escape)
- Screen reader tested
- Mobile-first responsive

---

### Section 4: INFORMATION ARCHITECTURE

**Purpose:** 
How the product is organized and navigated

**Length:** 
1-2 pages with diagrams

```markdown
## Information Architecture

### 4.1 Site Map / App Structure

```
Home/Dashboard
├── Dashboard
│   ├── Recent Activity
│   ├── Team Metrics
│   └── Quick Actions
├── Repositories
│   ├── Repository List
│   └── Repository Settings
│       ├── Configuration
│       └── Team Members
├── Pull Requests
│   ├── PR Analysis
│   │   ├── Findings
│   │   ├── Discussion
│   │   └── History
│   └── PR Details
├── Settings
│   ├── Account
│   ├── Team
│   │   ├── Members
│   │   ├── Configuration
│   │   └── Billing
│   ├── Notifications
│   └── Preferences
└── Help
    ├── Documentation
    ├── FAQ
    └── Contact Support
```

### 4.2 Navigation Model

**Primary Navigation:**
- Top header with logo, search, user menu
- Persistent across all pages
- Responsive: hamburger menu on mobile

**Secondary Navigation:**
- Sidebar or tabs based on context
- Changes based on current section
- Collapsible on mobile

**Breadcrumbs:**
- Shows current location in hierarchy
- Repository > PR #123 > Findings
- Helps users understand context
- Clickable for quick navigation

### 4.3 User Flow: Core Flow

```
USER ARRIVES
↓
See GitHub PR in Browser
↓
Tool Reviews Code
↓
Comments Appear in GitHub
↓
User Clicks Finding
↓
Modal Opens: Finding Details
↓
See Suggestion + Resource Link
↓
User Fixes Code
↓
Resubmit PR
↓
Tool Re-analyzes
↓
Findings Update in Real-time
```

### 4.4 Content Hierarchy

**Primary Content:**
- Code findings
- Suggested fixes
- Learning resources
- Status messages

**Secondary Content:**
- Historical findings
- Team statistics
- Account settings
- Help documentation

**Tertiary Content:**
- Metadata (timestamps, confidence scores)
- Attribution (who dismissed, when)
- Advanced options (for admins)

---

### Section 5: WIREFRAMES

**Purpose:** 
Low-fidelity representation of layouts and interactions

**Length:** 
5+ pages with wireframes

```markdown
## Wireframes

### 5.1 Dashboard Wireframe

```
┌─────────────────────────────────────┐
│ Logo   Search   [Settings] [User] │  Header
├─────────────────────────────────────┤
│ Sidebar                  │ Main Content  │
│                         │              │
│ Dashboard               │ Welcome!      │
│ Repositories            │ Last 7 days:  │
│ Pull Requests           │ - 47 reviews  │
│ Settings                │ - 23 issues   │
│ Help                    │ - 2 security  │
│                         │              │
│                         │ [Recent PRs]  │
│                         │ [Team Stats]  │
└─────────────────────────────────────┘
```

### 5.2 PR Analysis Wireframe (GitHub View)

```
┌─────────────────────────────────────┐
│ GitHub PR View                      │  GitHub
├─────────────────────────────────────┤
│                                     │
│ AutoReview Analysis                 │  Our Section
├─────────────────────────────────────┤
│ ⚠️ 2 Critical | ⚠️ 5 Warning | ℹ️ 3 Info │
│                                     │
│ Finding 1                          │
│ [🔴] SQL Injection Risk            │
│ Line 45: user SQL query            │
│ [View Details] [Dismiss]           │
│                                     │
│ Finding 2                          │
│ [🟡] Performance Issue              │
│ Line 78: N+1 Query                 │
│ [View Details] [Dismiss]           │
│                                     │
└─────────────────────────────────────┘
```

### 5.3 Finding Details Modal

```
┌─────────────────────────────────────┐
│ ✕                                   │  Close Button
├─────────────────────────────────────┤
│ 🔴 CRITICAL: SQL Injection          │  Severity + Title
│                                     │
│ Description:                        │
│ User input concatenated into SQL    │
│                                     │
│ Code:                               │  Code Sample
│ const q = `SELECT * FROM users      │
│   WHERE id = ${userId}`;            │
│                                     │
│ Suggestion:                         │  Suggested Fix
│ Use parameterized queries           │
│ const q = 'SELECT * FROM users'     │
│                                     │
│ 📚 Learn more →                     │  Resource Link
│                                     │
│ [Dismiss as False Positive]         │  Dismiss Option
│ [Mark as Will Fix Later]            │
└─────────────────────────────────────┘
```

### 5.4 Configuration Wireframe

```
┌─────────────────────────────────────┐
│ Team Configuration                  │  Title
├─────────────────────────────────────┤
│                                     │
│ Security Rules                      │  Section
│ ☑️ SQL Injection       [Critical]   │
│ ☑️ XSS                 [Critical]   │
│ ☑️ Hardcoded Secrets   [Critical]   │  Toggles
│ ☑️ Weak Crypto         [Warning]    │
│                                     │
│ Performance Rules                   │
│ ☑️ N+1 Queries         [Warning]    │
│ ☐ Unbounded Loops      [Info]       │
│                                     │
│ Exclusions                          │
│ Directories: node_modules, build/   │
│ Files: *.test.js, *.spec.js         │
│                                     │
│ [Save Changes]                      │  Save Button
└─────────────────────────────────────┘
```

### 5.5 States & Variations

**Empty State:**
```
┌─────────────────────────────────────┐
│ No Findings Yet                     │
│                                     │
│ 🎉 Great! No issues found.          │
│                                     │
│ Your code looks good!               │
│                                     │
│ [Learn Best Practices →]            │
└─────────────────────────────────────┘
```

**Loading State:**
```
┌─────────────────────────────────────┐
│ ⏳ Analyzing your code...            │
│                                     │
│ [████░░░░░] 40% Complete            │
│                                     │
│ This usually takes 10-30 seconds    │
└─────────────────────────────────────┘
```

**Error State:**
```
┌─────────────────────────────────────┐
│ ❌ Analysis Failed                   │
│                                     │
│ We couldn't analyze this PR.        │
│ Try again or contact support.       │
│                                     │
│ [Try Again]  [Contact Support]      │
└─────────────────────────────────────┘
```

---

### Section 6: DESIGN SYSTEM / COMPONENT LIBRARY

**Purpose:** 
Detailed specifications for all reusable components

**Length:** 
6-8 pages with comprehensive component specs

```markdown
## Design System / Component Library

### 6.1 Color Palette

**Primary Colors:**
```
Primary Blue:    #0066CC
  - Usage: CTAs, primary actions, links
  - Light: #E6F0FF
  - Dark: #003D99
  - Text on this: White

Secondary Gray:  #6B7280
  - Usage: Secondary text, borders
  - Light: #F3F4F6
  - Dark: #1F2937
```

**Semantic Colors:**
```
Success Green:   #10B981
  - Usage: Positive actions, confirmation
  
Warning Amber:   #F59E0B
  - Usage: Caution, warnings, attention needed
  
Error Red:       #EF4444
  - Usage: Errors, critical issues
  
Info Blue:       #3B82F6
  - Usage: Informational messages
```

**Accessibility:**
- Contrast ratio: Minimum 4.5:1 for text
- Color + icon: Don't rely on color alone
- Colorblind safe: Test with Coblis

### 6.2 Typography

**Font Stack:**
```css
Heading Font:    -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto
Body Font:       -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto
Monospace Font:  "Monaco", "Courier New", monospace
```

**Sizing Scale (based on 16px base):**
```
H1: 32px (weight: 700)      - Page titles
H2: 24px (weight: 700)      - Section titles
H3: 20px (weight: 600)      - Subsection titles
H4: 16px (weight: 600)      - Small titles
Body: 16px (weight: 400)    - Regular text
Small: 14px (weight: 400)   - Metadata, secondary text
Tiny: 12px (weight: 400)    - Captions, labels
```

**Line Heights:**
```
Headings: 1.2
Body: 1.5
Compact: 1.25
```

**Font Weights:**
```
Regular: 400 (body text)
Medium: 500 (emphasized text)
Semibold: 600 (labels, small headings)
Bold: 700 (main headings)
```

### 6.3 Spacing System

**Base Unit:** 8px (multiply for all spacing)

**Spacing Scale:**
```
2px    (xs)  - 0.25 unit  - Tight spacing
4px    (xs)  - 0.5 unit   - Very tight
8px    (sm)  - 1 unit     - Tight
12px   (sm)  - 1.5 unit   - Snug
16px   (md)  - 2 units    - Comfortable
24px   (lg)  - 3 units    - Spacious
32px   (xl)  - 4 units    - Very spacious
48px   (2xl) - 6 units    - Huge space
64px   (3xl) - 8 units    - Massive space
```

**Usage Examples:**
```
Padding inside button:         12px 16px (sm md)
Margin between sections:       32px (xl)
Gap between list items:        8px (sm)
Page padding:                  24px (lg)
Card padding:                  16px (md)
```

### 6.4 Component Specifications

---

**COMPONENT: Button**

**Sizes:**
```
Small (sm)
- Height: 32px
- Padding: 8px 12px
- Font size: 14px
- Usage: Compact spaces

Medium (md) - DEFAULT
- Height: 40px
- Padding: 12px 16px
- Font size: 16px
- Usage: Most CTAs

Large (lg)
- Height: 48px
- Padding: 16px 24px
- Font size: 18px
- Usage: Important actions
```

**Variants:**

```
Primary Button (Main CTA)
Background: #0066CC
Text: White
Border: None
Hover: #003D99 (darker)
Active: #002147 (darker)
Disabled: #CCCCCC, opacity 50%

Secondary Button
Background: #F3F4F6
Text: #1F2937
Border: 1px #E5E7EB
Hover: #E5E7EB
Active: #D1D5DB
Disabled: #F9FAFB

Ghost Button
Background: transparent
Text: #0066CC
Border: 1px #0066CC
Hover: Background #E6F0FF
Active: Background #CCE0FF

Danger Button
Background: #EF4444
Text: White
Hover: #DC2626
Active: #B91C1C
```

**States:**

```
Default: As defined above

Hover: Slight darkening, slight shadow

Active/Pressed: Even darker, internal shadow

Disabled: 50% opacity, cursor not-allowed

Loading: 
- Show spinner inside button
- Disable interactions
- Keep text visible or show "Loading..."
- Duration: Show for minimum 300ms
```

**Spacing & Layout:**

```
Icon + Text Button:
Icon: 16px square
Gap between icon and text: 8px
Total height: 40px (medium)

Full Width Button:
Used in forms
Width: 100% of container
Min-width: 200px

Multiple Buttons Row:
Gap between buttons: 8px
Stack vertically on mobile (< 640px)
```

**Accessibility:**

```
- Keyboard: Focusable (tab order)
- Focus indicator: 2px outline, color #0066CC
- Screen reader: Text label clear
- Disabled buttons: Cannot be focused
- Minimum touch size: 44x44px
```

---

**COMPONENT: Input Field**

**Specifications:**

```
Default State:
Height: 40px
Padding: 12px 16px
Border: 1px #E5E7EB
Border radius: 6px
Font size: 16px
Background: White

Focus State:
Border color: #0066CC
Border width: 2px
Box shadow: 0 0 0 3px #E6F0FF (outline)
Background: White

Error State:
Border color: #EF4444
Background: #FEF2F2
Text color: #DC2626

Success State:
Border color: #10B981
Background: #F0FDF4
Text color: #059669

Disabled State:
Background: #F9FAFB
Border color: #E5E7EB
Text color: #9CA3AF
Cursor: not-allowed
```

**Label & Helper Text:**

```
Label:
Font weight: 600
Font size: 14px
Color: #1F2937
Margin bottom: 8px
Required indicator: Red asterisk (*)

Helper Text (below input):
Font size: 12px
Color: #6B7280
Margin top: 4px

Error Message:
Font size: 12px
Color: #DC2626
Icon: ❌ (red X)
Margin top: 4px
```

**Validation:**

```
Real-time validation:
- Start on blur (not on keystroke)
- Show error message clearly
- Keep focus in field
- Update on each keystroke after blur

Example:
Email validation regex:
^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}$
```

**Responsive:**

```
Desktop: 100% of container (max 400px usually)
Mobile: 100% of container width
Label: Always above field (never floated on mobile)
```

---

**COMPONENT: Card**

**Specifications:**

```
Layout:
Padding: 16px (md)
Border radius: 8px
Border: 1px #E5E7EB
Background: White
Box shadow: 0 1px 3px rgba(0,0,0,0.1)

Hover State:
Box shadow: 0 4px 8px rgba(0,0,0,0.15)
Transition: 200ms ease
Cursor: pointer (if clickable)

Content Structure:
├─ Header (optional)
│  └─ Title + action buttons
├─ Body
│  └─ Main content
└─ Footer (optional)
   └─ Actions or metadata
```

**Variations:**

```
Elevated Card (featured)
- Box shadow: 0 10px 20px rgba(0,0,0,0.15)
- Padding: 24px (lg)
- Used for important content

Outlined Card (secondary)
- Box shadow: none
- Border: 2px #0066CC
- Used for secondary content

Compact Card
- Padding: 12px (sm)
- Smaller font sizes
- Used for list items
```

---

**COMPONENT: Modal / Dialog**

**Specifications:**

```
Overlay:
Background: rgba(0,0,0,0.5)
Backdrop filter: blur(4px) optional
Prevents background scroll

Modal Box:
Min width: 400px
Max width: 600px (or 90% on mobile)
Border radius: 12px
Background: White
Box shadow: 0 20px 40px rgba(0,0,0,0.2)
Padding: 24px (lg)
Z-index: 1000+ (above everything)

Header:
Display: flex, space-between
Title: H2 style
Close button: Top right, ✕ icon
Border-bottom: 1px #E5E7EB (optional)
Margin-bottom: 16px

Body:
Max-height: calc(100vh - 200px) (with scroll)
Padding: 16px 0

Footer:
Border-top: 1px #E5E7EB (optional)
Padding-top: 16px
Display: flex, justify-end
Gap: 8px between buttons
```

**Animations:**

```
Open:
- Fade in overlay: 200ms
- Scale up modal: transform scale(0.9) → scale(1), 200ms
- Easing: ease-out

Close:
- Fade out overlay: 150ms
- Scale down modal: transform scale(1) → scale(0.9), 150ms
- Easing: ease-in
```

**Accessibility:**

```
- Modal has role="dialog"
- Title has id, dialog aria-labelledby="title"
- ESC key closes modal
- Focus trapped inside modal (Tab cycles)
- Focus returned to trigger on close
- Backdrop click closes (if not form)
- Semantic HTML: <button>, <form>
```

---

**COMPONENT: Notification / Toast**

**Specifications:**

```
Position: Top-right (or configurable)
- Offset from edge: 16px
- Max width: 400px

Style by Type:
Success: #10B981 background, ✓ icon
Error: #EF4444 background, ✗ icon
Warning: #F59E0B background, ⚠️ icon
Info: #3B82F6 background, ℹ️ icon

Layout:
Padding: 12px 16px (sm md)
Border radius: 8px
Display: flex, align-items center, gap 8px
Font size: 14px
Line height: 1.5

Close Button:
✕ icon, top right
Click or timeout to dismiss

Auto-dismiss:
Success: 4 seconds
Error: 6 seconds (longer, important)
Warning: 5 seconds
Info: 3 seconds

Stacking:
Multiple toasts: Stack vertically
Gap: 8px between each
Animation: Slide in from top right
```

---

### 6.5 Icons

**Icon Library:** Feather Icons

**Specifications:**

```
Sizes:
Small: 16px    - Inline in text
Medium: 24px   - Default, buttons
Large: 32px    - Standalone, hero
XL: 48px       - Very large elements

Colors:
Primary: #0066CC     - Main actions
Secondary: #6B7280   - Secondary text
Success: #10B981     - Positive
Warning: #F59E0B     - Warning
Error: #EF4444       - Error
White: #FFFFFF       - On dark backgrounds

Stroke Width: 2px (consistent)
```

**Common Icons:**
```
✓  Check       - Success, completion
✕  X           - Close, error, remove
!  Alert       - Warning, attention
ℹ  Info        - Information, help
⚙  Settings    - Configuration
👤 User        - Profile, account
🔍 Search      - Search functionality
📌 Pin         - Save, bookmark
↗ External     - Link to external
≡  Menu        - Navigation menu
← Back         - Go back
```

---

### 6.6 Shadow System

**Depth Levels:**

```
Elevation 0 (Flat):
No shadow
- Background sections
- Main content areas

Elevation 1 (Subtle):
0 1px 3px rgba(0,0,0,0.1)
- Cards, inputs, labels

Elevation 2 (Soft):
0 4px 8px rgba(0,0,0,0.15)
- Hovered cards, small dropdowns

Elevation 3 (Medium):
0 10px 20px rgba(0,0,0,0.15)
- Important cards, modals, elevated content

Elevation 4 (Strong):
0 20px 40px rgba(0,0,0,0.2)
- Modals, overlays, top-level elements
```

---

### 6.7 Border Radius

**Scale:**

```
None: 0px           - Sharp edges (rare)
Small: 4px          - Subtle rounding (pills, badges)
Medium: 8px         - Default (cards, inputs, buttons)
Large: 12px         - Prominent (modals, larger cards)
Full: 9999px        - Circles, badges
```

---

### 6.8 Transitions & Animations

**Timing Functions:**

```
ease-out (default):    Faster start, slower end (UI elements)
ease-in:               Slower start, faster end (exit animations)
ease-in-out:           Smooth throughout (page transitions)
ease-linear:           Constant speed (progress bars, loaders)
```

**Standard Durations:**

```
Micro: 100ms           - Hover states, quick feedback
Short: 200ms           - State changes, toggles
Medium: 300ms          - Entering/exiting elements
Long: 500ms            - Page transitions
Delayed: 1000ms+       - Initial page load animations
```

**Animations:**

```
Fade In/Out:
opacity: 0 → 1, duration: 200ms, timing: ease-out

Slide Up:
transform: translateY(20px) → translateY(0), duration: 300ms

Scale In:
transform: scale(0.9) → scale(1), duration: 200ms

Slide from Left:
transform: translateX(-100%) → translateX(0), duration: 300ms
```

---

## 7. RESPONSIVE DESIGN

**Purpose:** 
How design adapts to different screen sizes

**Length:** 
1-2 pages

```markdown
## Responsive Design

### 7.1 Breakpoints

**Device Sizes:**

```
Mobile: 0px - 480px        - Phones
Tablet: 481px - 768px      - Tablets
Desktop: 769px+            - Laptops, desktops
Large Desktop: 1200px+     - Ultra-wide monitors
```

**Design Approach: Mobile-First**
1. Design for mobile first (smallest screen)
2. Add features as screen grows
3. Add layout complexity for larger screens

### 7.2 Mobile Design (0-480px)

**Layout:**
```
- Single column layout
- Full-width elements
- Top-to-bottom scrolling
- No sidebars

Navigation:
- Hamburger menu (≡ icon)
- Bottom tab bar for main sections
- Breadcrumbs still visible

Content:
- Large touch targets (44x44px minimum)
- Single action per screen
- Vertically stacked buttons
- Readable text (16px+)
```

**Navigation Mobile:**
```
┌──────────────────────────────┐
│ ≡    Title          Settings│  Header
├──────────────────────────────┤
│                              │
│  Content                     │
│                              │
│                              │
├──────────────────────────────┤
│ Home | Repos | PRs | Settings│  Tab Bar
└──────────────────────────────┘
```

### 7.3 Tablet Design (481-768px)

**Layout:**
```
- Two-column layout for some views
- Sidebar collapses to icons
- Can use split-view for PR + findings

Content:
- Larger touch targets still (44x44px)
- Better use of horizontal space
- More content per screen
```

### 7.4 Desktop Design (769px+)

**Layout:**
```
- Three-column possible
- Persistent sidebar
- Full feature set
- Mouse interactions

Navigation:
- Full menu visible
- No hamburger menu
- Dropdowns for submenu
```

---

## 8. ACCESSIBILITY (A11Y)

**Purpose:** 
Ensure product is usable by everyone, including users with disabilities

**Length:** 
2 pages

```markdown
## Accessibility (WCAG 2.1 Level AA)

### 8.1 Color & Contrast

**Text Contrast:**
```
Normal text (< 18px):     Minimum 4.5:1 ratio
Large text (≥ 18px):     Minimum 3:1 ratio
UI components & edges:   Minimum 3:1 ratio
```

**Testing:**
- Check with Contrast Checker tool
- Test with Colorblind Simulator (Coblis)
- Don't rely on color alone

Example of FAIL:
```
Red text on pink background = Bad contrast
```

Example of PASS:
```
Dark gray text (#333) on white background = 12.6:1 ratio ✓
```

### 8.2 Keyboard Navigation

**Tab Order:**
- Must follow logical visual order
- Left to right, top to bottom
- Skip non-interactive elements
- `tabindex="0"` for custom components (rare)
- Never `tabindex > 0`

**Focus Management:**
```
When modal opens:
- Focus moves inside modal
- Tab key cycles through modal items
- Cannot tab outside modal

When modal closes:
- Focus returns to trigger button
```

**Keyboard Shortcuts:**
```
Tab           - Move to next element
Shift+Tab     - Move to previous element
Enter         - Activate button
Space         - Toggle checkbox/radio
Arrow keys    - Navigate lists, menus
Escape        - Close modal, menu
Alt+/         - Show help (accessibility standard)
```

### 8.3 Screen Reader Support

**Semantic HTML:**
```html
<!-- Use semantic elements instead of divs -->
<nav>           <!-- Instead of: <div class="navigation"> -->
<main>          <!-- Instead of: <div id="main-content"> -->
<article>       <!-- Instead of: <div class="article"> -->
<button>        <!-- Instead of: <div onclick="..."class="button"> -->
<label>         <!-- Always pair with form inputs -->
```

**ARIA Labels:**
```html
<!-- Form inputs need labels -->
<label for="email">Email:</label>
<input id="email" type="email">

<!-- Buttons that use only icons need text -->
<button aria-label="Close modal">✕</button>

<!-- Complex components need aria-* -->
<div role="tablist">
  <button role="tab" aria-selected="true">Tab 1</button>
  <button role="tab" aria-selected="false">Tab 2</button>
</div>
<div role="tabpanel" aria-labelledby="tab1">Content</div>

<!-- Live regions for dynamic content -->
<div aria-live="polite" aria-atomic="true">
  <!-- Content that updates goes here -->
</div>
```

### 8.4 Images & Media

**Alt Text:**
```
For informative images:
<img src="chart.png" alt="Revenue increased 25% in Q1">

For decorative images:
<img src="divider.png" alt="">  <!-- Empty alt -->

For icons:
<i class="icon-check" aria-label="Success"></i>
```

**Video/Audio:**
```
- Captions for all video
- Transcripts for audio
- Controls clearly visible
- Auto-play disabled
```

### 8.5 Motion & Animation

**Respect User Preferences:**
```css
/* Reduce animations if user prefers less motion */
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

**Guidelines:**
- No auto-playing animations
- No flashing/strobing (can trigger seizures)
- Respect reduced motion preferences
- Meaningful animations only

### 8.6 Testing for Accessibility

**Manual Testing Checklist:**
- [ ] Keyboard navigation works
- [ ] Tab order is logical
- [ ] Focus indicators visible
- [ ] Color contrast sufficient
- [ ] Screen reader tested
- [ ] No keyboard traps
- [ ] Form labels present
- [ ] Error messages clear
- [ ] Links have descriptive text
- [ ] Reduced motion respected

**Tools:**
- axe DevTools (browser extension)
- Lighthouse (Chrome)
- WAVE (accessibility checker)
- Screen reader: NVDA (free)
```

---

## 9. DESIGN HANDOFF TO ENGINEERING

**Purpose:** 
Prepare design for developers to implement

**Length:** 
1-2 pages

```markdown
## Design Handoff

### 9.1 Design System Exports

**Assets Provided:**
- Colors (CSS variables, Tailwind config)
- Typography (font files, sizes, line heights)
- Spacing values (unit-based)
- Icons (SVG files, icon font)
- Shadows (CSS values)
- Border radius values
- Animation timings (CSS transitions)

**Format:**
- Figma design tokens exported
- Or: Design tokens JSON file
- Or: Tailwind config file

### 9.2 Component Specifications

**For Each Component:**
1. Visual design (high-res image)
2. All states (default, hover, active, disabled)
3. All sizes/variants
4. Responsive behavior
5. Code snippet (if complex)
6. Accessibility requirements

**Delivered In:**
- Figma with component library
- Storybook (if available)
- Component specs document

### 9.3 Developer Guidelines

**CSS Class Naming (BEM):**
```
Block: .button
Block-element: .button__text
Block-element-modifier: .button--primary
Block-modifier: .button--large
```

**No Inline Styles:**
```
❌ BAD:   <button style="background: blue; padding: 12px;">
✓ GOOD:  <button class="button button--primary">
```

**CSS Variables for Design Tokens:**
```css
/* Use CSS variables instead of hardcoding */
:root {
  --color-primary: #0066CC;
  --spacing-md: 16px;
  --font-size-body: 16px;
  --radius-default: 8px;
  --transition-default: 200ms ease-out;
}

.button {
  background-color: var(--color-primary);
  padding: var(--spacing-sm) var(--spacing-md);
  border-radius: var(--radius-default);
  transition: background-color var(--transition-default);
}
```

**Responsive Classes (Tailwind example):**
```html
<!-- Mobile-first approach -->
<div class="w-full md:w-1/2 lg:w-1/3">
  Full width on mobile, half on tablet, 1/3 on desktop
</div>
```

### 9.4 Figma File Organization

**Structure:**
```
/Components
  /Buttons
    /Button
      - All states
      - All sizes
      - All variants
  /Form
    /Input
    /Checkbox
    /Select
  /Cards
  /Modals
/Screens
  /Dashboard
  /PR Analysis
  /Settings
/Assets
  /Icons
  /Illustrations
```

**Component Best Practices:**
- Create main component
- Create variants for each state/size
- Use slots for customizable content
- Document in Figma (comments, descriptions)
- Maintain version control (dated versions)

### 9.5 Prototype & Demo

**Interactive Prototype:**
- Built in Figma prototype or Framer
- Shows user flows
- Demonstrates interactions
- Helps engineers understand experience

**Links Provided:**
- View-only Figma link
- Prototype link
- Component library/Storybook link (if exists)
```

---

## 10. DESIGN TOKENS

**Purpose:** 
Machine-readable design values for consistency

**Length:** 
1-2 pages with examples

```markdown
## Design Tokens

### JSON Format Example

```json
{
  "color": {
    "primary": {
      "50": "#E6F0FF",
      "100": "#CCE0FF",
      "200": "#99C2FF",
      "300": "#66A3FF",
      "400": "#3385FF",
      "500": "#0066CC",
      "600": "#0052A3",
      "700": "#003D7A",
      "800": "#002952",
      "900": "#001429"
    },
    "semantic": {
      "success": "#10B981",
      "warning": "#F59E0B",
      "error": "#EF4444",
      "info": "#3B82F6"
    }
  },
  "spacing": {
    "xs": "4px",
    "sm": "8px",
    "md": "16px",
    "lg": "24px",
    "xl": "32px",
    "2xl": "48px"
  },
  "typography": {
    "fontSize": {
      "xs": "12px",
      "sm": "14px",
      "base": "16px",
      "lg": "20px",
      "xl": "24px"
    },
    "fontWeight": {
      "regular": 400,
      "medium": 500,
      "semibold": 600,
      "bold": 700
    }
  },
  "borderRadius": {
    "none": "0",
    "sm": "4px",
    "md": "8px",
    "lg": "12px",
    "full": "9999px"
  },
  "shadows": {
    "sm": "0 1px 3px rgba(0,0,0,0.1)",
    "md": "0 4px 8px rgba(0,0,0,0.15)",
    "lg": "0 10px 20px rgba(0,0,0,0.15)"
  },
  "transition": {
    "short": "200ms ease-out",
    "medium": "300ms ease-out",
    "long": "500ms ease-out"
  }
}
```

### Tailwind Config Example

```javascript
module.exports = {
  theme: {
    colors: {
      primary: '#0066CC',
      secondary: '#6B7280',
      success: '#10B981',
      warning: '#F59E0B',
      error: '#EF4444'
    },
    spacing: {
      xs: '4px',
      sm: '8px',
      md: '16px',
      lg: '24px',
      xl: '32px'
    },
    fontSize: {
      xs: '12px',
      sm: '14px',
      base: '16px',
      lg: '20px'
    },
    borderRadius: {
      none: '0',
      sm: '4px',
      md: '8px',
      lg: '12px',
      full: '9999px'
    }
  }
}
```

---

## BEST PRACTICES FOR UI/UX DESIGN

✅ **DO:**
- Design with accessibility from the start
- Test with real users
- Iterate based on feedback
- Document all design decisions
- Maintain consistency across product
- Use reusable components
- Design mobile-first
- Test on real devices
- Include all states and edge cases
- Keep design system updated

❌ **DON'T:**
- Design in isolation
- Skip user testing
- Rely on color alone
- Create design and hope devs understand
- Use inconsistent patterns
- Forget about edge cases
- Skip accessibility
- Design without engineering input
- Make designs too complex
- Abandon design after launch

---

## TEMPLATE CHECKLIST

```markdown
## UI/UX Document Completion Checklist

### Section 1: Cover Page
- [ ] Document title and version
- [ ] Designer name and contact
- [ ] Stakeholder list
- [ ] Approval signatures

### Section 2: Design Vision
- [ ] Design vision statement
- [ ] Design goals (2-5)
- [ ] Design principles (4-6)
- [ ] Target users defined
- [ ] Success metrics

### Section 3: Research
- [ ] User research findings
- [ ] Usability test results
- [ ] Accessibility audit
- [ ] Design implications listed

### Section 4: Information Architecture
- [ ] Site map/app structure
- [ ] Navigation model
- [ ] User flows
- [ ] Content hierarchy

### Section 5: Wireframes
- [ ] Low-fidelity wireframes (5+ screens)
- [ ] All states documented (empty, loading, error)
- [ ] Interactions indicated
- [ ] Responsive considerations noted

### Section 6: Design System
- [ ] Color palette (primary, semantic, accessibility)
- [ ] Typography (sizes, weights, line heights)
- [ ] Spacing system (scale explained)
- [ ] Component specifications (10+ components)
- [ ] Icons library defined
- [ ] Shadows system
- [ ] Border radius scale
- [ ] Transitions & animations

### Section 7: Responsive Design
- [ ] Breakpoints defined
- [ ] Mobile design (0-480px)
- [ ] Tablet design (481-768px)
- [ ] Desktop design (769px+)
- [ ] Mobile-first approach documented

### Section 8: Accessibility
- [ ] Color contrast requirements (4.5:1 or 3:1)
- [ ] Keyboard navigation documented
- [ ] Screen reader support (ARIA labels)
- [ ] Image alt text guidelines
- [ ] Motion & animation guidelines
- [ ] Testing checklist

### Section 9: Design Handoff
- [ ] Design system exports prepared
- [ ] Component specifications for devs
- [ ] Developer guidelines
- [ ] Figma file organized
- [ ] Prototype/demo links

### Section 10: Design Tokens
- [ ] Design tokens defined (JSON)
- [ ] CSS variables documented
- [ ] Tailwind config (if applicable)

### General
- [ ] Includes high-res mockups/screenshots
- [ ] Figma link provided
- [ ] Prototype link provided
- [ ] All components visualized
- [ ] Design reviewed by stakeholders
- [ ] Sign-off obtained
- [ ] Accessible to all team members
```

---

**Final Notes:**
- Great UI/UX prevents user frustration and support tickets
- Share early and often - test with users
- Make it a living document - update as you learn
- Consistency in design is key to fast development
- Accessibility is not an afterthought - design it in
