# Hajj_Guide — Improvement Report

**Date:** August 27, 2026  
**Analysis Type:** Errors, Inconsistencies, Incompleteness, Missed Sections

---

## 🔴 Errors Found

### 1. Hajj Countdown — Hardcoded Date
- The countdown timer references `hajjDays`, `hajjHours`, `hajjMins`, `hajjSecs` elements but the JavaScript for the countdown was **truncated** in the file read. If the countdown is hardcoded to a specific date, it will be wrong for other years. The Islamic calendar shifts ~11 days earlier each Gregorian year.

### 2. Checklist Not Persisted
- The checklist items have `onclick` handlers and `class="checklist-item"` but the JavaScript for checklist persistence (localStorage) was not visible in the truncated file. If it's missing, all checked items are lost on page refresh.

### 3. File Truncation
- The file was truncated at line ~600 during the read, meaning the JavaScript section (tab switching, countdown logic, checklist logic, FAQ accordion) was not fully captured. This may hide additional bugs.

---

## 🟡 Inconsistencies

### 1. Light Theme Only
- Unlike Sharia-Law, Revert-Guide, and other projects, Hajj_Guide has **no dark/light theme toggle**. This breaks consistency with the rest of the Islamic app suite.

### 2. Dua Cards — Missing Arabic Text Issues
- The dua cards show Arabic text, transliteration, and translation, but the Arabic text uses `font-family: 'Amiri', serif` which may not render all diacritical marks correctly. Should verify with `Noto Naskh Arabic` (which is loaded in the `<head>` but not used for dua cards).

### 3. Inconsistent Color Scheme
- Uses emerald/gold scheme matching Islamic_Finance and Salah-guide, but the background pattern (`radial-gradient`) is slightly different — cream vs. green-cream blend.

### 4. Tab Navigation Style
- Uses a pill-style tab bar while Sharia-Law uses a different tab style. For app suite consistency, these should match.

---

## 🟠 Incompleteness

### 1. Missing Ihram Rules
- The overview mentions "Hajj rules" but doesn't detail what's prohibited during Ihram (no cutting hair, no perfume, no hunting, no marital relations, etc.). This is **critical** for Hajj preparation.

### 2. No Packing/Preparation Checklist
- The checklist covers ritual items but doesn't include a **comprehensive packing list**:
  - Medications
  - Travel documents
  - Phone/charger
  - Comfortable shoes
  - Umbrella/sun protection
  - ID copies

### 3. No Health/Safety Section
- Hajj involves extreme heat, large crowds, and physical exertion. Should include:
  - Heat exhaustion prevention
  - COVID/health protocols
  - Emergency contacts
  - What to do if separated from group

### 4. Missing Muqir/Prohibited Acts
- Common mistakes and prohibitions during Hajj are not covered in detail.

### 5. No Maps
- A visual map of Makkah showing the route between Mina, Arafat, Muzdalifah, and Jamarat would be extremely helpful. Currently only described in text.

---

## 🔵 Missed Sections & Improvements

### 1. Missing Sections
- **Travel logistics** — visa, flights, transportation in Makkah
- **Health preparation** — vaccinations, fitness, medications
- **Financial planning** — budget estimation, costs breakdown
- **Spiritual preparation** — recommended duas, spiritual mindset
- **Common mistakes** — what to avoid during Hajj
- **Hajj for women** — specific rules and considerations
- **Hajj for elderly/disabled** — accommodations and alternatives
- **Umrah guide** — many perform Umrah separately

### 2. Interactive Features
- **Day-by-day itinerary builder** — personalized based on type of Hajj selected
- **Packing checklist** with progress tracking
- **Dua collection** — save favorites, audio playback
- **Budget calculator** — estimate Hajj costs
- **Countdown widget** — already present but needs year calculation

### 3. Technical Improvements
- No `<meta>` tags for social sharing (OG tags missing)
- No service worker for offline access
- No `manifest.json` for PWA
- No accessibility (ARIA labels, keyboard navigation)
- No error handling for countdown timer

---

## 📋 Priority Recommendations

| Priority | Issue | Impact |
|----------|-------|--------|
| 🔴 P0 | Verify countdown is dynamic (not hardcoded) | Will break next year |
| 🔴 P0 | Ensure checklist persists in localStorage | Data loss on refresh |
| 🟡 P1 | Add Ihram rules/prohibitions section | Critical safety info |
| 🟡 P1 | Add health/safety section | Critical for pilgrims |
| 🟡 P1 | Add dark theme toggle | Consistency with suite |
| 🟠 P2 | Add maps of Hajj sites | Spatial understanding |
| 🟠 P2 | Add packing checklist | Practical utility |
| 🔵 P3 | Add budget calculator | Financial planning |
| 🔵 P3 | Add day-by-day personalized itinerary | Personalization |
