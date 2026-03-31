# Pomodoro Timer - Design System Documentation

## Overview
This Pomodoro Timer app is designed with mobile-first principles, following professional UI/UX standards with a focus on accessibility and consistency.

## Layout System

### Mobile Grid
- **Columns**: 4-column grid system
- **Margins**: 16px (1rem) on all sides
- **Spacing**: 8px increments (8px, 16px, 24px, 32px, 40px, 48px, 64px)
- **Max Width**: 448px (28rem) for content containers

### Viewports
- **iPhone 15**: 393 × 852 px
- **Pixel 8**: 412 × 915 px
- Responsive scaling for other mobile devices

## Global Styles

### Color System (High Contrast - WCAG AA Compliant)

#### Primary Colors
```css
--color-primary-500: #1a1a2e  /* Dark navy - primary actions */
--color-primary-600: #16213e  /* Darker navy - hover states */
```

#### Accent Colors
```css
--color-accent-500: #e94560   /* Vibrant red - focus/active states */
--color-accent-600: #d63651   /* Darker red - hover states */
```

#### Neutral Colors
```css
--color-neutral-50: #ffffff   /* Pure white - backgrounds */
--color-neutral-100: #f8f9fa  /* Off-white - subtle backgrounds */
--color-neutral-200: #e9ecef  /* Light gray - borders */
--color-neutral-300: #dee2e6  /* Medium-light gray - disabled */
--color-neutral-700: #495057  /* Medium-dark gray - secondary text */
--color-neutral-800: #343a40  /* Dark gray - primary text */
--color-neutral-900: #212529  /* Almost black - headings */
```

### Typography Scale

#### Font Sizes
```css
--text-xs: 0.75rem     /* 12px */
--text-sm: 0.875rem    /* 14px */
--text-base: 1rem      /* 16px - base size */
--text-lg: 1.125rem    /* 18px */
--text-xl: 1.25rem     /* 20px */
--text-2xl: 1.5rem     /* 24px */
--text-3xl: 1.875rem   /* 30px */
--text-4xl: 2.25rem    /* 36px */
--text-5xl: 3rem       /* 48px */
--text-6xl: 3.75rem    /* 60px - timer display */
```

#### Font Weights
```css
--font-weight-normal: 400   /* Regular text */
--font-weight-medium: 500   /* Headings, buttons, labels */
```

### Spacing System (8px increments)
```css
--spacing-1: 0.5rem   /* 8px */
--spacing-2: 1rem     /* 16px - base margin */
--spacing-3: 1.5rem   /* 24px */
--spacing-4: 2rem     /* 32px */
--spacing-5: 2.5rem   /* 40px */
--spacing-6: 3rem     /* 48px */
--spacing-8: 4rem     /* 64px */
```

## Components

### Icons
- **Library**: Lucide React (outline style)
- **Size**: 24px (w-6 h-6)
- **Usage**: Play, Pause, Reset, Settings
- **Style**: Outline/stroke based for consistency

### Buttons

#### Primary Button (Play/Pause)
- Size: 64px × 64px circular
- Background: Primary color (#030213)
- Icon: 24px, filled on active
- Shadow: Large elevation
- States: Default, Hover (90% opacity), Active

#### Secondary Button (Reset)
- Size: 64px × 64px circular
- Background: Muted color
- Icon: 24px, outline
- States: Default, Hover (80% opacity)

#### Tab Buttons (Session Type)
- Height: Auto with py-2 (16px vertical padding)
- Padding: px-4 (16px horizontal)
- Border Radius: 8px
- Active: Primary background with white text
- Inactive: Muted background with muted text
- Transition: All colors with smooth animation

### Timer Display

#### Progress Circle
- Diameter: 288px (w-72 h-72)
- Stroke Width: 8px
- Background Ring: Muted color
- Progress Ring: Primary color
- Animation: Smooth transition (1s duration)
- Cap Style: Rounded (strokeLinecap="round")

#### Time Text
- Font Size: 3.75rem (60px)
- Font Family: Monospace for consistent digit width
- Tracking: Tight (-0.025em)
- Color: Foreground color for high contrast

### Input Fields (Settings)
- Height: Auto with py-3 (24px vertical padding)
- Padding: px-4 (16px horizontal)
- Background: Input background color
- Border: 1px solid border color
- Border Radius: 8px
- Focus: 2px ring with ring color
- Type: Number with min/max constraints

### Lists

#### Session Counter
- Dot Size: 12px × 12px (w-3 h-3)
- Shape: Rounded full (circular)
- Spacing: 8px gap between dots
- Active: Primary color
- Inactive: Muted color
- Layout: Horizontal flex, centered

## Accessibility (WCAG AA Compliance)

### Contrast Ratios
- **Text on White**: Minimum 4.5:1 ratio
  - Foreground (#030213) on Background (#ffffff): 18.5:1 ✓
  - Muted text (#717182) on Background: 4.8:1 ✓

- **Interactive Elements**: Minimum 3:1 ratio
  - Primary button background meets requirement ✓
  - All interactive states have sufficient contrast ✓

### Semantic HTML
- Proper heading hierarchy (h1, h2, etc.)
- Semantic button elements
- ARIA labels for icon-only buttons
- Form labels properly associated with inputs

### Keyboard Navigation
- All interactive elements are keyboard accessible
- Focus states clearly visible
- Logical tab order

### Screen Reader Support
- ARIA labels on icon buttons
- Descriptive button text
- Semantic HTML structure

## Layout Patterns

### Auto-layout Principles
All components use flexbox for automatic spacing and alignment:

```css
/* Vertical Stack */
.flex.flex-col.gap-4  /* 32px spacing */

/* Horizontal Row */
.flex.gap-2           /* 16px spacing */

/* Centered Content */
.flex.items-center.justify-center
```

### Component Spacing
- Header: py-4 (32px vertical padding)
- Main content: px-4 (16px horizontal padding)
- Section gaps: mb-12 (48px margin-bottom)
- Button groups: gap-4 (32px between buttons)
- Tab groups: gap-2 (16px between tabs)

## Responsive Behavior

### Mobile First (Default)
- Full-width layouts with 16px margins
- Stacked vertical layouts
- Touch-friendly 64px button sizes
- Minimum touch target: 44px × 44px

### Tablet/Desktop
- Content max-width constraints
- Centered layouts
- Preserved mobile interaction patterns
- Scales smoothly without breaking

## States & Interactions

### Timer States
1. **Idle**: Timer paused, awaiting start
2. **Running**: Timer actively counting down
3. **Complete**: Session finished, auto-transition

### Session Types
1. **Work**: Primary focus session (default 25 min)
2. **Short Break**: Rest period (default 5 min)
3. **Long Break**: Extended rest (default 15 min, every 4 sessions)

### Transitions
- Color changes: 200ms ease
- Opacity changes: 200ms ease
- Progress ring: 1000ms for smooth animation
- All transitions use CSS for performance

## File Structure
```
/src/app/
  ├── App.tsx                      # Main entry point
  └── components/
      └── PomodoroTimer.tsx        # Complete timer component

/src/styles/
  ├── theme.css                    # Global color & typography tokens
  ├── tailwind.css                 # Tailwind imports
  └── index.css                    # Global styles
```

## Usage Notes

### Customization
Users can customize:
- Work duration (1-60 minutes)
- Short break duration (1-30 minutes)
- Long break duration (1-60 minutes)
- Sessions until long break (1-10 sessions)

### Notifications
- Browser notifications on session completion
- Requires user permission grant
- Graceful fallback if denied

### Data Persistence
- Settings stored in component state
- No backend required for basic functionality
- Can be extended with localStorage for persistence

## Performance

### Optimization Techniques
- CSS transitions for smooth animations
- Efficient timer using setInterval
- Minimal re-renders with proper state management
- No external API calls
- Lightweight icon library

### Best Practices
- Mobile-first responsive design
- Semantic HTML for accessibility
- High contrast for readability
- Touch-friendly interactions
- Consistent spacing system
