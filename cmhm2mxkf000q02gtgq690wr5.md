---
title: "Fixing Email Preview Scrollbar Accessibility in Ghost CMS (25304)"
seoTitle: "Email Preview Scrollbar Fix in Ghost CMS"
seoDescription: "Enhance Ghost CMS email previews with scrollbars, better keyboard navigation, and focus management for inclusivity"
datePublished: Wed Nov 05 2025 14:06:34 GMT+0000 (Coordinated Universal Time)
cuid: cmhm2mxkf000q02gtgq690wr5
slug: fixing-email-preview-scrollbar-accessibility-in-ghost-cms-25304
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1762351403969/a59e6835-ec32-43ac-8ba4-d851850a7b54.png
tags: ember, emberjs, github, opensource, ghost, accessibility, git, navigation, admin, ghostcms, open-source, scrollbar

---

## Introduction

Contributing to Ghost CMS has been a great learning experience for me. I started with small fixes, and now I have a better understanding of how good design and accessibility improve user experiences.

So far, I have solved three issues: #25050, #24608, and #24706. Each one has taught me more about Ghost’s Ember.js frontend, user interface consistency, and working in open-source projects.

In my fourth contribution, #25304, I addressed an important accessibility issue in the email preview. What appeared to be a simple scrollbar bug turned out to be a practical lesson in focus management, keyboard navigation, and inclusive design.

## Understanding the Problem

When I first looked at issue [#25304](https://github.com/TryGhost/Ghost/issues/25304), it seemed simple: the email preview in Ghost’s post editor didn’t show a visible scrollbar.  
But as I investigated further, I realised this was more than a visual problem; it was an accessibility issue. Without a scrollbar, users who depend on keyboard navigation or two-button mice couldn't scroll through long email previews.

I tested the issue locally and confirmed that:

* The CSS was hiding the scrollbar.
    
* The iframe couldn’t be focused using the keyboard.
    
* Arrow keys, Page Up/Down, and Tab navigation didn’t work.
    

This was a small UX gap but had a big impact, especially for users who depend on accessible navigation.

So, I decided to review the email preview component in the Ember.js admin frontend to find out why this was happening and how to fix it.

## My Thought Process

I started by learning how the email preview works. Since Ghost’s admin panel uses Ember.js, I found the component that shows the preview modal.

I searched the code and located the relevant files at:

* ghost/admin/app/components/editor/modals/preview/email.js
    
* ghost/admin/app/components/editor/modals/preview/email.hbs
    

Next, I used the browser’s DevTools to check the iframe. I noticed something important: the scrollbar was hidden by CSS:

```css
html::-webkit-scrollbar {
    display: none;
}
html {
    scrollbar-width: none;
}
```

This explained why the scrollbar was not visible. However, there was more to the problem: even when using a mouse wheel, the iframe could not be focused, which meant keyboard users couldn’t scroll at all.

I had a clear conclusion: The issue was not just about styling; it was also about focus management and accessibility.

I decided to fix the problem in three steps:

1. Allow scrollbars to show again.
    
2. Make the iframe keyboard-focusable.
    
3. Manage focus properly when users tab into the preview area.
    

This plan gave me a clear direction; a small UI change could greatly improve accessibility and usability.

## The Fix

I focused on improving the email preview to make it easier to use and accessible. I made three key changes that had a big impact.

### 1\. Make Scrollbars Visible Again

The original code hides the scrollbar completely. I changed it so the scrollbar shows when there is too much content for the screen:

```css
const INJECTED_CSS = `
html,
body {
    overflow-y: auto;
}
`;
```

Now, users can see the scrollbar whenever needed, making it clear that they can scroll.

### 2\. Make the Iframe Keyboard-Focusable

Next, I ensured users can navigate to the iframe using the keyboard by adding a tabindex:

```html
<iframe
    class="gh-pe-iframe"
    title="Email preview"
    tabindex="0"
    sandbox="allow-same-origin allow-popups allow-popups-to-escape-sandbox"
    {{did-insert this.renderEmailPreview}}
    {{did-update this.renderEmailPreview @memberSegment}}
    {{on "focusin" this.focusPreviewFrame}}
></iframe>
```

This change allows users to tab into the preview and use the arrow keys or Page Up/Down to scroll.

### 3\. Manage Focus Inside the Iframe

Finally, I ensured the iframe’s body could receive focus, not just the iframe itself. This is where keyboard navigation works best.

```javascript
@action
focusPreviewFrame(event) {
    const iframe = event?.target;
    try {
        const body = iframe.contentDocument?.body;
        if (body && !body.hasAttribute('tabindex')) {
            body.setAttribute('tabindex', '-1');
        }
        body?.focus({preventScroll: true});
    } catch {
        iframe.contentWindow?.focus();
    }
}
```

This change allowed keyboard events to be handled correctly and scrolling to work smoothly.

After making these changes, the email preview modal is now fully scrollable, accessible with a keyboard, and easy to see. This small fix made Ghost’s editor more inclusive and enjoyable to use.

## Testing and Verification

After making the fix, I wanted to ensure it improved the experience in real use. I ran Ghost in development mode and launched the email preview. This time, I quickly noticed the difference:

✅ The scrollbar appeared when needed.  
✅ I could focus on the iframe using the Tab key.  
✅ The arrow keys, Page Up/Down, and Space/Shift+Space scrolled smoothly.  
✅ The mouse wheel and scrollbar dragging worked perfectly.

To prevent any future issues, I added a test that checks if the iframe has `tabindex="0"` and that its body gets focus correctly. This way, upcoming updates won’t undo the accessibility fix.

All tests passed, and the UI worked consistently across different browsers.

This testing reminded me how important it is to check real behaviour, not just the code. Accessibility fixes matter when they help someone use the product more comfortably.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1762231521475/1f5b1722-1a4f-483b-b30c-2e377a4c7a02.png align="center")

## Submitting the Pull Request

After confirming that the fix worked and all tests passed, I submitted a pull request to Ghost’s main branch: [Pull Request #**25334**](https://github.com/TryGhost/Ghost/pull/25334)

The pull request included:

* Visible scrollbars in the email preview.
    
* Added `tabindex="0"` to the iframe for keyboard access.
    
* A focus handler to ensure the iframe body receives focus.
    
* An acceptance test to prevent future issues.
    

## Impact and Lessons Learned

This contribution showed me that even small improvements in accessibility can make a big difference. By fixing the email preview scrollbar and improving keyboard navigation:

* Keyboard-only users can navigate and scroll email previews easily.
    
* Mouse users can drag scrollbars instead of just using the wheel.
    
* All users benefit from a clearer and more predictable interface.
    

Working on this issue also reinforced the importance of patience, attention to detail, and clear communication in open-source projects. Accessibility isn’t just a feature; it’s about making software usable for everyone.

Contributing to Ghost has been a rewarding experience. I look forward to making the platform more inclusive and user-friendly.

## After Screenshot

Here’s the updated email preview with the scrollbar and keyboard accessibility:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1762351350276/ae885bd7-40b0-43df-917f-d71914829805.png align="center")

## Resources

* [Ghost Contributing Guide](https://github.com/TryGhost/Ghost/blob/main/.github/CONTRIBUTING.md)
    
* [Ember.js Documentation](https://emberjs.com/)
    
* [WebAIM: Keyboard Accessibility](https://webaim.org/techniques/keyboard/)
    
* [MDN: Focus Management](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/focus)
    
* [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/)