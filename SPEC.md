# Personal Homepage Specification

## Concept & Vision

A futuristic, minimalist personal homepage that feels like stepping into a cyberpunk command center. The design evokes the sensation of floating through digital space — particle stars drift past, neon light trails streak across the void, and glass-morphic UI elements hover with ethereal presence. The experience is immersive, immersive, and distinctly "future tech."

## Design Language

### Aesthetic Direction
Inspired by cyberpunk 2077 UI, Apple's visionOS, and high-end fintech dashboards. Dark, atmospheric, with strategic bursts of cyan and violet neon that feel like breathing light rather than garish decoration.

### Color Palette
- **Primary Background**: `#0a0a0f` (deep void black)
- **Secondary Background**: `#12121a` (slightly lifted dark)
- **Primary Accent**: `#00d4ff` (electric cyan)
- **Secondary Accent**: `#a855f7` (vivid purple)
- **Tertiary Accent**: `#ec4899` (hot pink for highlights)
- **Text Primary**: `#ffffff` (pure white)
- **Text Secondary**: `rgba(255, 255, 255, 0.7)` (soft white)
- **Glass Border**: `rgba(255, 255, 255, 0.1)` (subtle glass edge)
- **Glow Cyan**: `rgba(0, 212, 255, 0.5)` (cyan glow)
- **Glow Purple**: `rgba(168, 85, 247, 0.5)` (purple glow)

### Typography
- **Primary Font**: "Inter", system-ui, sans-serif
- **Display Font**: "Orbitron", monospace (for headings and special text)
- **Base Size**: 16px
- **Scale**: 1.25 (major third)
- **Headings**: Orbitron, 700 weight, letter-spacing: 0.1em
- **Body**: Inter, 400 weight, line-height: 1.6

### Spatial System
- Base unit: 8px
- Spacing scale: 8, 16, 24, 32, 48, 64, 96, 128px
- Container max-width: 1400px
- Section padding: 96px vertical, 48px horizontal

### Motion Philosophy
- **Particle Stars**: Continuous, slow drift (parallax effect with mouse movement)
- **Flowing Lines**: Animated along curved SVG paths, 8-12s loops, varying opacity
- **Neon Pulses**: Subtle breathing glow on accent elements, 3-4s cycles
- **Hover States**: 300ms cubic-bezier(0.4, 0, 0.2, 1) transitions
- **Entrance Animations**: Staggered fade-up, 600ms each, 100ms delays
- **Floating Cards**: Gentle 6s ease-in-out infinite vertical bob (3-5px range)

### Visual Assets
- **Icons**: Lucide icons (line style, 1.5px stroke)
- **Avatar**: Circular with animated gradient border (cyan → purple rotation)
- **Decorative**: Animated gradient orbs, particle canvas, SVG flow lines
- **Background Elements**: CSS gradient blobs, blur effects

## Layout & Structure

### Page Architecture
```
┌─────────────────────────────────────────────────────────┐
│ [CANVAS: Particle Star Field - Full Page Background]   │
│ [SVG: Flowing Light Lines - Animated Curves]            │
│ [GRADIENT BLOBS: Soft Neon Orbs - Blurred, Animated]    │
├─────────────────────────────────────────────────────────┤
│  ┌──────────────────────────────────────────────────┐   │
│  │ GLASS MORPHIC NAVBAR (Floating, Centered)         │   │
│  │ [Logo]  [Home] [About] [Skills] [Projects] [Contact] │
│  └──────────────────────────────────────────────────┘   │
├─────────────────────────────────────────────────────────┤
│                                                         │
│              ┌─────────────────────┐                   │
│              │   GLASS CARD         │                   │
│              │   ┌─────────────┐    │                   │
│              │   │   AVATAR    │    │                   │
│              │   │  (Glow)    │    │                   │
│              │   └─────────────┘    │                   │
│              │   NAME (Glow Text)  │                   │
│              │   TITLE             │                   │
│              │   SOCIAL LINKS      │                   │
│              └─────────────────────┘                   │
│                                                         │
│              [SECTION INDICATORS - Right Side]          │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

### Responsive Strategy
- **Desktop (1200px+)**: Full layout, all effects at full intensity
- **Tablet (768px-1199px)**: Slightly reduced particle count, simplified flow lines
- **Mobile (< 768px)**: Bottom navigation bar, reduced animations, stacked layout

### Visual Pacing
Hero section dominates viewport with centered focal point. Content sections revealed through scroll with smooth transitions. Breathing room between sections (96px gaps).

## Features & Interactions

### 1. Particle Star Field (Background)
- **Behavior**: 150+ particles drifting slowly across canvas
- **Parallax**: Mouse movement creates subtle depth shift
- **Variation**: 3 size classes (1px, 2px, 3px), varying opacity (0.3-1.0)
- **Colors**: White with cyan/purple tint on some particles

### 2. Flowing Light Lines (Background)
- **Count**: 4-6 curved SVG paths
- **Animation**: Dash-offset animation creating flow illusion
- **Colors**: Gradient strokes (cyan → purple → pink)
- **Opacity**: 0.3-0.6 (subtle, not overwhelming)

### 3. Neon Glow Orbs (Background)
- **Count**: 3 large gradient blobs
- **Animation**: Slow drift + scale pulse (8-12s cycles)
- **Position**: Behind content, in periphery
- **Blur**: 100-150px gaussian blur

### 4. Glass Morphic Navigation Bar
- **Appearance**: Centered horizontal bar, 60px height
- **Background**: `rgba(255, 255, 255, 0.05)` with backdrop blur (20px)
- **Border**: 1px solid `rgba(255, 255, 255, 0.1)`
- **Border Radius**: 20px
- **Effect**: Subtle shadow with cyan tint
- **States**:
  - Default: 0.8 opacity
  - Hover: 1.0 opacity, slight scale (1.02)
  - Active link: Cyan underline glow

### 5. Hero Section - Centered Profile Card
- **Container**: Glass card, 420px max-width
- **Background**: `rgba(255, 255, 255, 0.03)`
- **Border**: 1px solid `rgba(255, 255, 255, 0.1)`
- **Backdrop Filter**: 20px blur
- **Avatar Container**:
  - Size: 140px circle
  - Border: 3px solid transparent (animated gradient)
  - Glow: Box shadow with cyan/purple gradient
  - Animation: Gradient rotation (4s), gentle pulse
- **Name**:
  - Font: Orbitron, 32px, 700 weight
  - Effect: Text gradient (cyan → purple) + text-shadow glow
- **Title**:
  - Font: Inter, 16px, 400 weight
  - Color: rgba(255, 255, 255, 0.7)
  - Letter-spacing: 0.2em, uppercase
- **Social Links**: Icon row with hover glow effects

### 6. Side Navigation (Section Indicators)
- **Position**: Fixed right side, vertically centered
- **Style**: Vertical dots with connecting line
- **Behavior**: Click scrolls to section, current section highlighted
- **Hover**: Tooltip appears with section name

### 7. Floating Animation
- **Card Float**: Hero card has continuous 6s ease-in-out vertical bob
- **Range**: 5px up/down
- **Sync**: Multiple elements stagger their float phase

## Component Inventory

### Navigation Bar Component
| State | Appearance |
|-------|------------|
| Default | Glass bg, 0.8 opacity, horizontal layout |
| Hover (item) | Cyan text glow, slight underline |
| Active (item) | Solid cyan underline, full opacity |
| Scrolled | Slightly increased opacity (0.95) |

### Profile Card Component
| State | Appearance |
|-------|------------|
| Default | Glass container, centered avatar + text |
| Hover | Subtle border glow increase |
| Loading | Skeleton pulse animation |

### Avatar Component
| State | Appearance |
|-------|------------|
| Default | Circular image, animated gradient border |
| Hover | Glow intensifies, slight scale |
| Loading | Gradient shimmer placeholder |

### Social Icon Component
| State | Appearance |
|-------|------------|
| Default | White icon, 0.7 opacity |
| Hover | Cyan glow, 1.0 opacity, scale 1.1 |
| Active | Brief flash effect |

### Side Indicator Component
| State | Appearance |
|-------|------------|
| Default | Small dot (6px), 0.3 opacity |
| Hover | 0.6 opacity, tooltip visible |
| Active | 1.0 opacity, cyan color, larger (8px) |

## Technical Approach

### Stack
- **Single HTML file** with embedded CSS and JavaScript
- **Vanilla JavaScript** for all interactions
- **CSS Custom Properties** for theming
- **Canvas API** for particle system
- **CSS Animations** + **requestAnimationFrame** for smooth motion

### Architecture
```
index.html
├── <style> - All CSS including animations
├── <body>
│   ├── <canvas id="particles"> - Star field
│   ├── <svg class="flow-lines"> - Animated curves
│   ├── <div class="glow-orbs"> - Background blobs
│   ├── <nav class="navbar"> - Glass navigation
│   ├── <main>
│   │   └── <section class="hero">
│   │       ├── <div class="profile-card">
│   │       └── ...
│   └── <div class="side-nav"> - Section indicators
└── <script> - All JavaScript
```

### Key Implementation Details
1. **Particle System**: Canvas-based, 150 particles, mouse parallax, requestAnimationFrame loop
2. **Flow Lines**: SVG paths with stroke-dasharray/dashoffset animation
3. **Glass Effect**: backdrop-filter: blur(20px), semi-transparent backgrounds
4. **Gradient Border**: Conic-gradient + rotation animation on avatar
5. **Text Glow**: Multiple text-shadow layers + background-clip: text
6. **Smooth Scroll**: CSS scroll-behavior + JS for side nav sync
