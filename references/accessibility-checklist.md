# Accessibility Checklist (WCAG 2.1)

Comprehensive checklist for web accessibility compliance.

## Level A (Minimum)

### Perceivable

- [ ] **1.1.1 Non-text Content**: All images have alt text
- [ ] **1.2.1 Audio-only/Video-only**: Provide text alternatives
- [ ] **1.2.2 Captions**: Videos have captions
- [ ] **1.2.3 Audio Description**: Provide audio descriptions
- [ ] **1.3.1 Info and Relationships**: Use semantic HTML
- [ ] **1.3.2 Meaningful Sequence**: Reading order is logical
- [ ] **1.3.3 Sensory Characteristics**: Don't rely on shape/color alone
- [ ] **1.4.1 Use of Color**: Color is not only means of conveying info
- [ ] **1.4.2 Audio Control**: User can pause/stop/mute audio

### Operable

- [ ] **2.1.1 Keyboard**: All functionality via keyboard
- [ ] **2.1.2 No Keyboard Trap**: Can navigate away from components
- [ ] **2.1.4 Character Key Shortcuts**: Can disable or remap
- [ ] **2.2.1 Timing Adjustable**: User can extend time limits
- [ ] **2.2.2 Pause, Stop, Hide**: Can control moving content
- [ ] **2.3.1 Three Flashes**: No content flashes >3 times/second
- [ ] **2.4.1 Bypass Blocks**: Skip navigation link present
- [ ] **2.4.2 Page Titled**: Descriptive page titles
- [ ] **2.4.3 Focus Order**: Logical tab order
- [ ] **2.4.4 Link Purpose**: Link text describes destination
- [ ] **2.5.1 Pointer Gestures**: Alternatives for complex gestures
- [ ] **2.5.2 Pointer Cancellation**: Can cancel pointer actions
- [ ] **2.5.3 Label in Name**: Visible label matches accessible name
- [ ] **2.5.4 Motion Actuation**: Alternatives for motion controls

### Understandable

- [ ] **3.1.1 Language of Page**: `lang` attribute on `<html>`
- [ ] **3.2.1 On Focus**: No unexpected context changes
- [ ] **3.2.2 On Input**: No unexpected context changes
- [ ] **3.3.1 Error Identification**: Errors clearly identified
- [ ] **3.3.2 Labels or Instructions**: Form fields have labels

### Robust

- [ ] **4.1.1 Parsing**: Valid HTML (no duplicate IDs)
- [ ] **4.1.2 Name, Role, Value**: Custom components have ARIA

## Level AA (Standard)

### Perceivable

- [ ] **1.3.4 Orientation**: Works in both orientations
- [ ] **1.3.5 Identify Input Purpose**: Input autocomplete attributes
- [ ] **1.4.3 Contrast (Minimum)**: 4.5:1 for text, 3:1 for large text
- [ ] **1.4.4 Resize Text**: Text resizable to 200% without loss
- [ ] **1.4.5 Images of Text**: Use actual text, not images
- [ ] **1.4.10 Reflow**: Content reflows at 320px width
- [ ] **1.4.11 Non-text Contrast**: 3:1 for UI components
- [ ] **1.4.12 Text Spacing**: No loss when spacing increased
- [ ] **1.4.13 Content on Hover/Focus**: Dismissible, hoverable, persistent

### Operable

- [ ] **2.4.5 Multiple Ways**: More than one way to find pages
- [ ] **2.4.6 Headings and Labels**: Descriptive headings/labels
- [ ] **2.4.7 Focus Visible**: Visible focus indicator
- [ ] **2.4.11 Focus Not Obscured**: Focus not fully hidden

### Understandable

- [ ] **3.1.2 Language of Parts**: Mark language changes
- [ ] **3.2.3 Consistent Navigation**: Same navigation order
- [ ] **3.2.4 Consistent Identification**: Same components = same labels
- [ ] **3.3.3 Error Suggestion**: Suggest corrections
- [ ] **3.3.4 Error Prevention**: Confirm/review important actions

### Robust

- [ ] **4.1.3 Status Messages**: Use ARIA live regions

## Level AAA (Enhanced)

### Perceivable

- [ ] **1.4.6 Contrast (Enhanced)**: 7:1 for text, 4.5:1 for large
- [ ] **1.4.8 Visual Presentation**: User can adjust text presentation
- [ ] **1.4.9 Images of Text (No Exception)**: Never use text images

### Operable

- [ ] **2.1.3 Keyboard (No Exception)**: Everything via keyboard
- [ ] **2.2.3 No Timing**: No time limits
- [ ] **2.2.4 Interruptions**: User can postpone updates
- [ ] **2.2.5 Re-authenticating**: Data preserved on re-auth
- [ ] **2.3.2 Three Flashes**: No content flashes at all
- [ ] **2.4.8 Location**: Breadcrumbs or location indicator
- [ ] **2.4.9 Link Purpose (Link Only)**: Clear without context
- [ ] **2.4.10 Section Headings**: Organize content with headings

### Understandable

- [ ] **3.1.3 Unusual Words**: Define unusual terms
- [ ] **3.1.4 Abbreviations**: Expand abbreviations
- [ ] **3.1.5 Reading Level**: Supplementary content for complex text
- [ ] **3.1.6 Pronunciation**: Provide pronunciation for ambiguous words
- [ ] **3.2.5 Change on Request**: Only change context on request
- [ ] **3.3.5 Help**: Context-sensitive help available
- [ ] **3.3.6 Error Prevention (All)**: Confirm all submissions

## Quick Fixes

### Missing Alt Text
```html
<!-- Bad -->
<img src="hero.jpg">

<!-- Good -->
<img src="hero.jpg" alt="Team collaborating in modern office">

<!-- Decorative (intentionally empty) -->
<img src="decorative-line.svg" alt="" role="presentation">
```

### Color Contrast
```css
/* Bad: 2.5:1 ratio */
.text { color: #999; background: #fff; }

/* Good: 4.5:1 ratio */
.text { color: #595959; background: #fff; }
```

### Focus Indicators
```css
/* Never remove focus outlines without replacement */
:focus { outline: none; } /* BAD */

/* Provide visible focus */
:focus-visible {
  outline: 2px solid var(--primary);
  outline-offset: 2px;
}
```

### Skip Link
```html
<body>
  <a href="#main-content" class="skip-link">
    Skip to main content
  </a>
  <nav>...</nav>
  <main id="main-content">...</main>
</body>

<style>
.skip-link {
  position: absolute;
  top: -40px;
  left: 0;
  background: var(--primary);
  color: white;
  padding: 8px 16px;
  z-index: 100;
}
.skip-link:focus {
  top: 0;
}
</style>
```

### Form Labels
```html
<!-- Bad -->
<input type="email" placeholder="Email">

<!-- Good -->
<label for="email">Email address</label>
<input type="email" id="email" autocomplete="email">
```

### ARIA Live Regions
```html
<!-- For dynamic updates -->
<div role="status" aria-live="polite">
  <!-- Content announced to screen readers when changed -->
</div>

<!-- For errors/alerts -->
<div role="alert" aria-live="assertive">
  Form submission failed. Please try again.
</div>
```

## Testing Tools

| Tool | Purpose |
|------|---------|
| axe DevTools | Browser extension for automated testing |
| WAVE | Visual accessibility evaluation |
| Lighthouse | Performance + accessibility audit |
| NVDA/VoiceOver | Screen reader testing |
| Colour Contrast Analyser | Check color contrast ratios |
