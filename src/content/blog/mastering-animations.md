---
title: 'Mastering CSS Animations in 2024'
description: 'Learn how to create buttery-smooth animations that delight users without sacrificing performance.'
pubDate: 2024-11-25
tags: ['css', 'animations', 'design']
author: 'Soulmad'
---

# The Art of Motion

Great animations are invisible. They guide users, provide feedback, and create emotional connections - all without getting in the way.

## The Golden Rules

### 1. Performance First

Always animate `transform` and `opacity`. These properties are GPU-accelerated and won't cause layout thrashing.

```css
/* Bad - triggers layout */
.element {
  animation: bad 0.3s;
}
@keyframes bad {
  to {
    left: 100px;
    width: 200px;
  }
}

/* Good - GPU accelerated */
.element {
  animation: good 0.3s;
}
@keyframes good {
  to {
    transform: translateX(100px) scale(1.2);
  }
}
```

### 2. Timing is Everything

The right easing function makes all the difference:

- **ease-out**: For elements entering the screen
- **ease-in**: For elements leaving
- **ease-in-out**: For state changes

### 3. Respect User Preferences

Always honor `prefers-reduced-motion`:

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

## The Magic Numbers

- **100-200ms**: Micro-interactions (buttons, toggles)
- **200-300ms**: Small movements (dropdowns, tooltips)
- **300-500ms**: Large movements (modals, page transitions)

Motion done right feels like magic.
