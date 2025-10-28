---
title: "Fixing Ghost’s Disappearing Tag Bug: A Deep Dive into Issue #25020"
seoTitle: "Ghost Tag Bug Fix: Issue #25020 Insights"
seoDescription: "Fixing Ghost CMS tag bug with object comparison adjustment. Dive into the issue's analysis, resolution, and testing for seamless user experience"
datePublished: Tue Oct 28 2025 08:42:13 GMT+0000 (Coordinated Universal Time)
cuid: cmhabizpb000702lccnfr2rz3
slug: fixing-ghosts-disappearing-tag-bug-a-deep-dive-into-issue-25020
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1761640692376/77c7f027-6c30-4494-9b9a-bd2e35d0ae49.png
tags: javascript, web-development, opensource, nodejs, ghost, developer, cms, coding, career, technical-writing-1, open-source-community, open-source

---

## 1\. Introduction

Ghost is an open-source headless CMS built with Node.js, trusted by creators and publishers worldwide.

After resolving two earlier issues (#24608 on dark mode transitions and #24706 on spinner alignment), I felt ready to tackle something more challenging. That’s when I came across Issue #25020:

> “Tag disappears from dropdown after removal.”

It sounded simple, but JavaScript had other plans. This post is a breakdown of how I investigated, fixed, and learned from a subtle UI bug that made tags vanish from the editor like magic.

## 2\. Reproducing the Issue

> “When you remove a tag while the dropdown is open, it disappears and doesn’t return until the editor is closed.”

To confirm, I set up Ghost locally and followed these steps:

1. Create a new post.
    
2. Open Post Settings → Tags.
    
3. Click inside the tags input field to open the dropdown.
    
4. Select a tag, say *News*.
    
5. Without closing the dropdown, remove *News*.
    

Just as described, *News* vanished. It didn’t reappear until I closed and reopened the editor. That’s definitely not expected behaviour.

## 3\. Root Cause

My first thought was that this wasn’t a backend issue since the tags still existed in the database. It had to be a frontend problem, most likely in Ember’s tag management component. A quick search led me to the file:  
`ghost/admin/app/components/gh-tags-token-input.js`

Inside, I found this snippet:

```js
get availableTags() {
    const selectedTags = this.args.selected || [];
    const selectedSet = new Set(selectedTags);
    return this._initialTags.filter(tag => !selectedSet.has(tag));
}
```

It looked fine at first. Take the selected tags, store them in a Set, and filter them out from the dropdown list. But something was not right.

JavaScript compares objects **by reference**, not **by value**. That means:

```js
const tag1 = {id: '5', name: 'News'};
const tag2 = {id: '5', name: 'News'};

tag1 === tag2; // false
```

They look identical but are stored differently in memory. Ghost was creating new tag objects each time a user interacted with them. So when `Set.has(tag)` it ran, it compared two different object references even though both represented the same tag.

Result: Ghost thought the tag was still selected and kept it filtered out.

### 4\. The Fix

Once I pinpointed the issue, the fix was simple. Instead of comparing entire objects, I compared tag IDs, which are unique and constant across references.

**Before:**

```js
const selectedSet = new Set(selectedTags);
return this._initialTags.filter(tag => !selectedSet.has(tag));
```

**After:**

```js
const selectedTagIds = new Set(selectedTags.map(tag => tag.id));
return this._initialTags.filter(tag => !selectedTagIds.has(tag.id));
```

Just two lines changed, and the disappearing tags were gone for good.

### 5\. Testing the Solution

I reloaded Ghost, repeatedly adding and removing tags: “News,” “Tech,” and “Updates.”  
This time, every tag reappeared instantly in the dropdown. No more vanishing act.

Then I ran:

```bash
yarn lint:js app/components/gh-tags-token-input.js
```

✅ No errors.

Followed by:

```bash
yarn test:unit --grep="tag"
```

✅ All tests passed.

The fix was stable, isolated, and ready for a pull request.

## 6\. Pull Request

I created PR [**#25262**](https://github.com/TryGhost/Ghost/pull/25262) with the following commit:

> 🐛 Fixed tag disappearing from dropdown after removal  
> fixes [https://github.com/TryGhost/Ghost/issues/25020](https://github.com/TryGhost/Ghost/issues/25020)

**Description:**  
When editing a post, removing a tag while the dropdown was open caused it to disappear from available options. This happened because Set was comparing object references instead of tag IDs. Fixed by comparing tag IDs instead.

A clear, minimal, and descriptive PR just the way Ghost prefers.

## 7\. Lessons Learned

1. **Reference vs. Value Equality**  
    I’d read about it before, but seeing it break real code made it stick. Objects are compared by reference, primitives by value.
    
2. **Simple Fixes Can Have Big Impact**  
    It wasn’t a critical bug, but it noticeably improved the editor’s user experience.
    
3. **Each Contribution Builds Confidence**  
    My previous Ghost fixes helped me debug and navigate much faster this time.
    
4. **Always Reproduce Before You Fix**  
    Seeing the bug in action provides context no stack trace can match.
    

## 8\. Final Thoughts

This was my third contribution to Ghost, the open-source CMS led by John O'Nolan and Hannah Wolfe. Each fix has deepened my understanding of modern web systems:

* **#24608** UI transitions
    
* **#24706** State and layout consistency
    
* **#25020** Object identity and equality
    

Open source is about learning by doing. Every fix teaches something you can’t get from a tutorial. Somewhere, a writer removed a tag and didn’t have to reload their editor, and that tiny moment of smoothness made it worth it.

## 9\. Resources

* [Ghost GitHub Repository](https://github.com/TryGhost/Ghost)
    
* [Issue #25020](https://github.com/TryGhost/Ghost/issues/25020)
    
* [Pull Request #25262](https://github.com/TryGhost/Ghost/pull/25262)
    
* [MDN: Set.prototype.has()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/has)
    
* [Ghost Contributing Guidelines](https://ghost.org/docs/contributing/)
    
* Previous Fixes: #24608 and #24706
    

Found this helpful? Let’s connect on [GitHub](https://github.com/abdultalha0862) or here on [LinkedIn](https://www.linkedin.com/in/abdul-talha/). I love sharing what I learn while building real things.