---
title: "Fixing Ghost’s Dark Mode Transitions — A Developer’s Journey into UX Details"
seoTitle: "Improving Ghost's Dark Mode Transitions"
seoDescription: "Discover how fixing a dark mode transition bug in Ghost led to UX improvements and valuable lessons in frontend development"
datePublished: Wed Oct 22 2025 06:34:09 GMT+0000 (Coordinated Universal Time)
cuid: cmh1mb6dw000002lbcp81d5xi
slug: fixing-ghosts-dark-mode-transitions-a-developers-journey-into-ux-details
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1760800106750/639081c9-4c82-49b8-ba78-87a281c87ecd.png
tags: css, github, opensource, ghost, animation

---

## Introduction

When I first saw Issue [#24608](https://github.com/TryGhost/Ghost/issues/24608) on Ghost’s GitHub page about “Dark mode / light mode transitions being incorrect for most analytics sections,” I thought it would be a simple CSS fix. However, it turned out to be much more complicated. This small issue led me to explore user experience design, frontend architecture, and how to make software feel right.

## The Spark

After fixing a previous issue with spinner colours, I browsed Ghost’s issue tracker again, eager to contribute more. That’s when I found the dark mode bug. At first, it didn’t seem significant, but when I checked it out, I saw why it mattered.

Most of Ghost’s interface switched smoothly between light and dark mode with elegant fades of about 150 milliseconds. However, the analytics section changed instantly from bright to dark, which felt jarring. It was a small detail, but it broke the experience.

> Good software, I’ve learned, is about how it feels, not just about logic.

## Setting Up Ghost Locally

To debug the issue, I set up Ghost on my local machine:

```bash
git clone https://github.com/TryGhost/Ghost.git
cd Ghost
```

I was impressed with Ghost’s setup. It uses an **Nx monorepo**, meaning multiple applications (admin, analytics, libraries, tests) are in one repository—connected but modular. After setting it up with MySQL, the Ghost dashboard loaded, and I was ready to explore.

## Reproducing the Bug

At [http://localhost:2368/ghost](http://localhost:2368/ghost), I switched between dark and light themes. The issue was clear:

* **Main admin UI:** smooth, polished transitions.
    
* **Analytics UI:** instant jumps without animation.
    

I recorded it, compared it, and looked closely at the elements. I quickly realised this was not a backend issue; it was just a missing CSS transition layer.

## Tracing the Root Cause

While inspecting the components, I saw that Ghost used **Tailwind CSS** with dark mode managed by the `dark:` prefix.

The main UI components included the following classes:  
`transition-colors duration-150 ease-in-out`

But the analytics components did not have these classes. That was what was missing—the transition utilities to make colour changes smooth.

## Attempt 1: The Over-Engineered Fix

My first instinct as a developer was to over-engineer the solution. I created a reusable theme utility system:

```ts
export const getAnalyticsButtonClasses = (variant: AnalyticsButtonVariant): string => {
    const variants = {
        ghost: 'transition-colors duration-150 ease-in-out hover:bg-gray-200 dark:hover:bg-gray-700',
        outline: 'transition-colors duration-150 ease-in-out border-gray-300 dark:border-gray-600...',
    };
    return variants[variant] || '';
};
```

I thought this was clean, modular, and scalable, but when I ran the app, nothing changed. The transitions still snapped instantly. It turned out the existing components had hardcoded styles, so my utility functions weren’t being used. I had built a nice system that didn’t work.

## Attempt 2: The Practical Fix

So, I decided to take a step back. Sometimes the simple solution is the best one. I manually added transition classes to each affected component:

In **PostMenu.tsx:**

```tsx
<Button className="h-6 px-2 transition-colors duration-150 ease-in-out dark:bg-grey-900 dark:text-white dark:hover:bg-grey-800 dark:border-grey-800" variant='ghost'>
```

In **Overview.tsx:**

```tsx
<span className="text-sm font-normal transition-colors duration-150 ease-in-out dark:text-grey-400">
```

In **TopPosts.tsx:**

```tsx
const metricClass = `text-xs text-grey-500 dark:text-grey-400 transition-colors duration-150 ease-in-out ${isSelected ? 'opacity-60' : ''}`;
```

I made changes in six files with just a few lines of code, and everything began to flow again.

## Testing & Verification

Here’s how I confirmed it worked:

* ✅ **Build check:** `npm run build` passed successfully.
    
* ✅ **Manual testing:** I toggled dark/light modes repeatedly.
    

Finally, the transitions worked everywhere. There were no harsh jumps, just smooth fades—exactly how it should feel.

## Lessons from the Journey

This small issue taught me more than I expected:

* Over-engineering can slow down progress.
    
* Attention to small details improves user experience.
    
* Open source is about learning, not just fixing bugs.
    
* The simplest solution is often the easiest to maintain.
    

As developers, we often focus on complex architecture, but sometimes we just need to enhance the user experience, even if it means repeating the same class multiple times.

## Resources I Used

* [Ghost’s Contributing Guide](https://ghost.org/docs/contributing/)
    
* [Tailwind CSS Transitions](https://tailwindcss.com/docs/transition-property)
    
* [Nx Monorepo Docs](https://nx.dev/)
    

## Conclusion

When I finally toggled themes and saw everything transition smoothly, it felt satisfying. No one might notice this fix, which is part of its beauty.

> The best user experiences are those that feel seamless.

This contribution reminded me that **details matter. Always.**

*If you enjoyed this breakdown, follow me for more open-source insights, debugging stories, and frontend learnings.*