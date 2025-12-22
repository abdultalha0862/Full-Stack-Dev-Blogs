---
title: "My First Contribution to Zulip: Fixing Empty Topic Display in Email Notifications (#36689)"
seoTitle: "Fixing Zulip Email Notifications Topics"
seoDescription: "Fixing Zulip email bugs improved user experience and taught debugging, testing, open source contribution, and future involvement lessons"
datePublished: Mon Dec 15 2025 17:00:10 GMT+0000 (Coordinated Universal Time)
cuid: cmj7eg9df000202jsb8w1abcc
slug: my-first-contribution-to-zulip-fixing-empty-topic-display-in-email-notifications-36689
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1765797855365/a808bb0d-27ab-4f86-bda1-e3a48b54cd60.png
tags: github, python, django, opensource, git

---

## 1\. Introduction – Why Zulip, Why This Issue

After contributing to Ghost's open-source codebase and learning the process of distributed collaboration, I wanted to explore a different type of project. Zulip caught my attention because of its unique approach to team communication and its well-documented, beginner-friendly contribution process.

What attracted me to Zulip was its thoughtful architecture – a Django backend with modern frontend tooling, comprehensive testing, and a strong focus on code quality. The project felt mature yet welcoming to newcomers.

I picked issue [#36689](https://github.com/zulip/zulip/pull/37059) because it was labelled as a help-wanted issue and involved email notifications – a feature that directly impacts user experience. The problem was clear: empty topics in digest emails were showing raw HTML instead of the expected "general chat" display.

## 2\. Understanding the Problem

The issue affected users receiving email digest notifications when:

* Messages were posted to topics with empty names
    
* The digest email would display raw HTML like `<span class="empty-topic-display">general chat</span>`
    
* Instead of the clean, localised "general chat" text
    

This created a poor user experience and made Zulip look unprofessional in email clients. The problem occurred specifically in digest emails, not in the web interface, where empty topics displayed correctly.

**Expected behaviour**: Clean "general chat" text.

**Actual behaviour**: Raw HTML markup visible to users

## 3\. Reproducing the Issue Locally

I set up my local Zulip development environment following their excellent documentation:

```bash
./tools/provision
./tools/run-dev
```

To reproduce the issue, I:

* Created messages in topics with empty names
    
* Navigated to [`http://localhost:9991/digest/`](http://localhost:9991/digest/) to preview digest emails
    
* Confirmed the raw HTML was visible in the email preview
    
* Checked both HTML and plain text versions of the digest
    

The issue was clearly visible in the digest preview, making it easy to verify the problem and later test the fix.

## 4\. Visual Evidence: Before and After

### Before Fix - Raw HTML Displayed

| Email Preview | Issue |
| --- | --- |
|  | Raw HTML `<span class="empty-topic-display">general chat</span>` visible to users |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1765798113848/0222897c-786f-4830-bc91-86c4a3719e1e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1765798129478/419f45a9-2766-4cc4-9c8c-e0a16888eb0e.png align="center")

### After Fix - Clean Display

| Email Preview | Fixed |
| --- | --- |
|  | Clean "general chat" text properly rendered |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1765798155030/c8809222-8dd2-4033-9fb1-612970934723.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1765798169726/8849f0c0-a347-4917-9379-5de887efbba8.png align="center")

The difference is immediately apparent - users now see professional, clean email formatting instead of confusing HTML markup.

## 5\. Tracing the Root Cause

At first, I thought this was a simple templating issue in the email templates. I spent time looking through the digest email templates, expecting to find incorrect HTML escaping.

After reading through the codebase more carefully, I realised the issue was deeper in the email notification logic. The problem was in `zerver/lib/email_`[`notifications.py`](http://notifications.py) in the `digest_block_header` function.

The actual root cause was a type annotation issue. The code was creating `Markup` objects inconsistently:

* For empty topics: using `Markup().format()` with proper escaping
    
* For non-empty topics: directly wrapping in `Markup()` without escaping
    

This inconsistency meant the type checker couldn't properly validate the code, and the HTML rendering behaved differently for empty vs non-empty topics.

## 6\. The Fix (What I Changed and Why)

I needed to ensure both empty and non-empty topics were created `Markup` objects consistently while maintaining proper HTML escaping.

The solution was to:

1. Use `escape()` to safely handle user input for topic names
    
2. Create `Markup` objects consistently for both cases
    
3. Maintain the special styling for empty topics with the CSS class
    

I chose this approach because:

* It maintains security by properly escaping user input
    
* It fixes the type annotation issues
    
* It keeps the existing functionality for empty topic styling
    
* It's minimal and doesn't change the overall architecture
    

The key insight was that `Markup().format()` auto-escapes parameters, but directly wrapping strings in `Markup()` bypasses escaping – a potential XSS vulnerability.

## 7\. Testing the Fix

I tested the fix thoroughly:

**Manual testing:**

* Verified digest preview at [`http://localhost:9991/digest/`](http://localhost:9991/digest/) displayed correctly
    
* Checked both HTML and plain text versions
    
* Tested with various topic names, including edge cases
    

**Automated testing:**

```bash
./tools/lint --skip=gitlint zerver/lib/email_notifications.py
./tools/test-backend zerver/tests/test_email_notifications.py
./tools/run-mypy
```

I also added a specific test case `test_empty_topic_display_in_digest_email` to ensure this regression wouldn't happen again.

**Edge cases verified:**

* Empty topic names
    
* Topics with special characters
    
* Topics with potential HTML content
    

## 8\. Submitting the Pull Request

I submitted [**PR #37059**](https://github.com/zulip/zulip/pull/37059) with a clear description following Zulip's guidelines:

* Explained the problem and solution
    
* Included testing steps
    
* Referenced the original issue #36689
    

The PR went through Zulip's automated checks:

* Linting passed
    
* Type checking passed
    
* All tests passed
    
* Security review flagged an initial XSS concern
    

I quickly addressed the security feedback with a second commit, properly escaping the user input before wrapping it in `Markup()`.

**Pull Request Link**: [https://github.com/zulip/zulip/pull/37059](https://github.com/zulip/zulip/pull/37059)

## 9\. What I Learned

**Technical Learnings:**

* How Django's `Markup` class works and its security implications
    
* The importance of consistent type annotations in large codebases
    
* Zulip's comprehensive testing approach and tooling
    
* The difference between auto-escaping and manual escaping in templates
    

**Non-Technical Learnings:**

* How to read and understand large, well-organised codebases
    
* The value of thorough local testing before submitting
    
* How security-conscious open source projects operate
    
* The importance of clear, focused commits and PR descriptions
    

The most valuable lesson was understanding that good open source contributions aren't just about fixing bugs – they're about maintaining code quality, security, and consistency across the entire project.

## 10\. Final Thoughts

This contribution gave me confidence that I can meaningfully contribute to large, complex projects. The Zulip community's focus on mentoring new contributors and maintaining high standards created an excellent learning environment.

I'm excited to continue contributing to Zulip, potentially tackling more complex issues as I become more familiar with the codebase. The experience reinforced that open source contribution is as much about learning and collaboration as it is about coding.

For anyone considering their first Zulip contribution: the documentation is excellent, the community is welcoming, and the codebase is well-organised. Don't hesitate to dive in!

## 11\. Resources

* **Zulip Repository**: [https://github.com/zulip/zulip](https://github.com/zulip/zulip)
    
* **Original Issue**: [https://github.com/zulip/zulip/issues/36689](https://github.com/zulip/zulip/issues/36689)
    
* **My Pull Request**: [https://github.com/zulip/zulip/pull/37059](https://github.com/zulip/zulip/pull/37059)
    
* **Zulip Development Documentation**: [https://zulip.readthedocs.io/en/latest/development/overview.html](https://zulip.readthedocs.io/en/latest/development/overview.html)
    
* **Zulip Contributing Guide**: [https://github.com/zulip/zulip/blob/main/CONTRIBUTING.md](https://github.com/zulip/zulip/blob/main/CONTRIBUTING.md)