## 视频介绍

这些视频是基于Ank2.0制作的，但是2.1的功能大体上是一样的。

- [共享牌组和基本复习](http://www.youtube.com/watch?v=QS2G-k2hQyg&yt:cc=on)
- [调整卡片顺序](http://www.youtube.com/watch?v=DnbKwHEQ1mA&yt:cc=on)
- [美化卡片](http://www.youtube.com/watch?v=F1j1Zx0mXME&yt:cc=on)
- [卡片挖空](http://www.youtube.com/watch?v=5tYObQ3ocrw&yt:cc=on)

如果YouTube在你的国家不能登录，你可以在这里[下载这些视频](https://apps.ankiweb.net/downloads/archive/screencasts/2.0/) 。
## Translations

Volunteers have contributed translations of this manual. The translations may not always be up to date.

- [Bahasa Indonesia](https://apps.ankiweb.net/docs/manual.id.html)
- [Deutsch](http://www.dennisproksch.de/anki)
- [Español](https://apps.ankiweb.net/docs/manual.es.html)
- [Français](https://apps.ankiweb.net/docs/manual.fr.html)
- [Italiano](https://web.archive.org/web/20160423223801/http://192.167.9.6/Anki_ITA/Manual_ITA.htm)
- [Polski](https://apps.ankiweb.net/docs/manual.pl.html)
- [فارسى](http://ankidroid.ir/anki.pdf)
- [日本語](http://wikiwiki.jp/rage2050/?FrontPage)
- [简体中文](http://www.ankichina.net/anki20.html)

If you would like to help translate the manual into a different language, or you would like to look at the translations that are currently in progress, please see the [translating the manual](https://apps.ankiweb.net/docs/manual.html#translatingmanual) section.
## Introduction

Anki is a program which makes remembering things easy. Because it is a lot more efficient than traditional study methods, you can either greatly decrease your time spent studying, or greatly increase the amount you learn.

Anyone who needs to remember things in their daily life can benefit from Anki. Since it is content-agnostic and supports images, audio, videos and scientific markup (via LaTeX), the possibilities are endless. For example:

- learning a language
- studying for medical and law exams
- memorizing people’s names and faces
- brushing up on geography
- mastering long poems
- even practicing guitar chords!

There are two simple concepts behind Anki: *active recall testing* and *spaced repetition*. They are not known to most learners, despite having been written about in the scientific literature for many years. Understanding how they work will make you a more effective learner.
### Active Recall Testing

*Active recall testing* means being asked a question and trying to remember the answer. This is in contrast to *passive study*, where we read, watch or listen to something without pausing to consider if we know the answer. Research has shown that active recall testing is far more effective at building strong memories than passive study. There are two reasons for this:

- The act of recalling something *strengthens* the memory, increasing the chances we’ll be able to remember it again.
- When we’re unable to answer a question, it tells us we need to return to the material to review or relearn it.

You have probably encountered active recall testing in your school years without even realizing it. When good teachers give you a series of questions to answer after reading an article, or make you take weekly progress-check tests, they are not doing it simply to see if you understood the material or not. By testing you, they are increasing the chances you will be able to remember the material in the future.

A good way to integrate active recall testing into your own studies is to use *flashcards*. With traditional paper flashcards, you write a question on one side of a card, and the answer on the other side. By not turning the card over until you’ve thought about the answer, you can learn things more effectively than passive observation allows.
### Use It or Lose It

Our brains are efficient machines, and they rapidly discard information that doesn’t seem useful. Chances are that you don’t remember what you had for dinner on Monday two weeks ago, because this information is not usually useful. If you went to a fantastic restaurant that day and spent the last two weeks telling people about how great it was, however, you’re likely to still remember in vivid detail.

The brain’s “use it or lose it” policy applies to everything we learn. If you spend an afternoon memorizing some science terms, and then don’t think about that material for two weeks, you’ll probably have forgotten most of it. In fact, studies show we forget about 75% of material learnt within a 48 hour period. This can seem pretty depressing when you need to learn a lot of information.

The solution is simple, however: *review*. By reviewing newly-learnt information, we can greatly reduce forgetting.

The only problem is that traditionally review was not very practical. If you are using paper flashcards, it’s easy to flick through all of them if you only have 30 of them to review, but as the number grows to 300 or 3000, it quickly becomes unwieldy.
### Spaced Repetition

The *spacing effect* was reported by a German psychologist in 1885. He observed that we tend to remember things more effectively if we spread reviews out over time, instead of studying multiple times in one session. Since the 1930s there have been a number of proposals for utilizing the spacing effect to improve learning, in what has come to be called *spaced repetition*.

One example is in 1972, when a German scientist called Sebastian Leitner popularized a method of spaced repetition with paper flashcards. By separating the paper cards up into a series of boxes, and moving the cards to a different box on each successful or unsuccessful review, it was possible to see at a glance a rough estimate of how well a card was known and when it should be reviewed again. This was a great improvement over a single box of cards, and it has been widely adopted by computerized flashcard software. It is a rather rough approach however, as it can’t give you an exact date on which you should review something again, and it doesn’t cope very well with material of varying difficulty.

The biggest developments in the last 30 years have come from the authors of SuperMemo, a commercial flashcard program that implements spaced repetition. SuperMemo pioneered the concept of a system that keeps track of the ideal time to review material and optimizes itself based on the performance of the user.

In SuperMemo’s spaced repetition system, every time you answer a question, you tell the program how well you were able to remember it – whether you forgot completely, made a small mistake, remembered with trouble, remembered easily, etc. The program uses this feedback to decide the optimal time to show you the question again. Since a memory gets stronger each time you successfully recall it, the time between reviews gets bigger and bigger – so you may see a question for the first time, then 3 days later, 15 days later, 45 days later, and so on.

This was a revolution in learning, as it meant material could be learnt and retained with the absolute minimum amount of effort necessary. SuperMemo’s slogan sums it up: with spaced repetition, you can *forget about forgetting*.
### Why Anki?

While there is no denying the huge impact SuperMemo has had on the field, it is not without its problems. The program is often criticized for being buggy and difficult to navigate. It only runs on Windows computers. It’s proprietary software, meaning end-users can’t extend it or access the raw data. And while very old versions are made available for free, they are quite limited for modern use.

Anki addresses these issues. There are free clients for Anki available on many platforms, so struggling students and teachers with budgetary constraints are not left out. It’s open source, with an already flourishing library of add-ons contributed by end-users. It’s multi-platform, running on Windows, Mac OSX, Linux/FreeBSD, and some mobile devices. And it’s considerably easier to use than SuperMemo.

Anki’s spaced repetition system is based on an older version of the SuperMemo algorithm called [SM-2](https://apps.ankiweb.net/docs/manual.html#what-algorithm).
## The Basics
## Cards
## Decks
## Notes 
## Card Types
## Note Types
## Collection
## Adding Material
## Downloading Shared Decks
## Adding Cards and Notes
## Adding a Note Type
## Customizing Fields
## Changing Deck / Note Type
## Using Decks Appropriately
## Studying
## Decks
## Study Overview
## Questions
## Learning
## Reviewing
## Due Counts and Time Estimates
## Editing and More
## Display Order
## Siblings and Burying
## Keyboard Shortcuts
## Falling Behind
## Editing
## Features
## Cloze Deletion
## Inputting Foreign Characters and Accents
## Cards and Templates
## Reverse Cards
## Basic Templates
## Checking Your Answer
## Newlines
## Card Styling
## Field Styling
## Hint Fields
## Special Fields
## Card Generation 
## Selective Card Generation
## Media 
## Conditional Replacement
## Cloze Templates
## Other HTML
## Dictionary Links
## HTML Stripping
## Browser Appearance
## RTL (right to left) text
## Platform-Specific CSS
## Installing Fonts
## Night Mode
## Fading and Scrolling
## Profiles 
## Profiles
## Preferences
## Deck Options
## New Cards
## Reviews
## Lapses
## General
## Description
## AnkiWeb and Synchronization
## Setup
## Automatic Syncing
## Media
## Conflicts
## Merging Conflicts
## Firewalls
## Proxies
## Browser
## Sidebar
## Searching
## Card List
## Current Note
## Toolbar
## Find and Replace
## Finding Duplicates
## Other Menu Items
## Filtered Decks 
## Custom Study
## Home Decks
## Creating Manually
## Order
## Steps 
## Counts
## Due Reviews
## Reviewing Ahead
## Rescheduling
## Catching Up
## Leeches
## Waiting
## Deleting
## Editing
## Importing
## Importing text files
## Spreadsheets and UTF-8
## HTML
## Importing Media
## Adding Tags
## Duplicates and Updating
## Exporting
## Exporting Text
## Exporting Packaged Decks
## Managing Files and Your Collection
## Checking Your Collection
## File Locations
## Startup Options
## DropBox and File Syncing
## Network Filesystems
## Running from a Flash Drive
## Backups
## Inaccessible Harddisk
## Permissions of Temp Folder
## Corrupt Collections
## Graphs and Statistics
## Card Info
## Statistics
## Types of Cards
## Today
## The Graphs
## Manual Analysis
## Media
## MathJax support
## LaTeX support
## Installing and Assumed Knowledge
## LaTeX on Web/Mobile
## Example
## LaTeX packages
## LaTeX Conflicts
## Unsafe commands
## Miscellanea
## Menu Shortcuts
## Debug Console
## Add-ons
## Contributing
## Sharing Decks Publicly
## Sharing Decks Privately
## Sharing Add-ons
## Translating the Manual
## Contributing Code
## Translating Anki
## Suggestions 
## Glossary
## Context
## Formatting
## Getting Help
## Testing
## Frequently Asked Questions
## I haven’t studied for a while, and now the next due times are too big!
## Can I do multiple-choice questions?
## Can I link cards together? Add dependencies? How should I handle synonyms?
## Can I give my notes an arbitrary number of fields?
## Can I host my own AnkiWeb?
## Why is the Android version free when the iPhone version isn’t?
## What spaced repetition algorithm does Anki use?
## Why doesn’t Anki use SuperMemo’s latest algorithm?
## What about SM-5?
## Resources