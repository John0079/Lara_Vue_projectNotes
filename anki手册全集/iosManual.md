## Help & Bugs

There’s a dedicated [support site](https://anki.tenderapp.com/) for questions, suggestions and bug reports.

## Introduction

Thank you for buying AnkiMobile! Anki development would not be able to continue without your support, so it is greatly appreciated.

As mentioned on the app store page, AnkiMobile is currently intended to be used in conjunction with Anki on your computer. While it is possible to download shared decks, study, and edit the content of your notes, certain actions are currently only possible on the computer version. While this is expected to change over time, for now please ensure you have access to a computer in order to perform some of the operations mentioned below.

Some basic concepts covered in the [computer manual](https://apps.ankiweb.net/docs/manual.html) are not repeated here, so please check it out if you have not already done so.

## Searching

If you are looking for something in particular in this manual, most web browsers will allow you to find particular words and phrases.

**On a phone/iPad**, type the word you wish to search for in the location bar at the top, and when a list of possible matches appears, choose the "Find on page" option at the bottom to search through this page.

**On a computer**, choose Find from the Edit menu in most browsers.

## Privacy

No data you store in AnkiMobile is shared with us or other Anki users by default. If you use the optional synchronization feature, please see [AnkiWeb’s privacy policy](https://ankiweb.net/account/privacy).

## Adding Decks

To start using AnkiMobile, we need to add some cards to study. We can either download card decks that other people have shared, or add existing decks from the computer.

### Shared Decks

To download a shared deck directly to your mobile device:

1. Ensure you’re connected to the internet.
2. Tap **Add/Export** on the bottom left.
3. Choose **Shared Deck List**. AnkiWeb will open.
4. Select a category, or type in a search.
5. Tap on a deck you’d like to study.
6. Scroll down and tap **Download**.
7. Safari will start downloading the file
8. When it’s done, it will display a button near the top right labeled **Open in Anki**. Tap this button.
9. When the import completes, your deck should be ready to study.

Information on reviewing is available further below.

### Cloud Sync

Anki has a free cloud synchronization service called AnkiWeb that makes it easy to keep your card decks in sync between mobile devices and your computer.

To sync with AnkiWeb, you’ll first need to create an account. If you have used AnkiWeb in the past, you can skip this step.

1. Visit [https://ankiweb.net](https://ankiweb.net/) and click the **Sign Up** button.
2. Type in your email address and a password of your choice.

If you have decks on your computer and would like them to be synced to AnkiMobile:

1. Open the computer version and click the sync button at the top right of the Anki window.
2. If prompted to upload or download, choose *upload* to send your cards to AnkiWeb.
3. Tap Synchronize in AnkiMobile and then *download* to grab the cards from AnkiWeb.

If you have decks in your phone/iPad and would like them to be synced to the computer version:

1. Tap Synchronize in AnkiMobile and then *upload* to send the cards to AnkiWeb.
2. Open the computer version and click the sync button at the top right of the Anki window.
3. If prompted to upload or download, choose *download* to grab your cards from AnkiWeb.

If you have a lot of sounds or images on your cards, the first sync may take some time.

After the first synchronization has completed, you can click the synchronize button again any time you wish to synchronize your changes to the cloud. Only changes made since the previous sync will be sent, so subsequent syncs are a lot faster.

If you add some new cards on the desktop computer and want to sync them to AnkiMobile, you’d repeat the same process: sync on desktop (or close the program, as it syncs automatically on close by default), and then tap the sync button on AnkiMobile.

### iTunes Import/Export

If you don’t have regular internet access, it’s still possible to copy decks back and forth to your device, by using iTunes.

The iTunes import/export works by importing or exporting **all your decks at once**, in a special file called collection.apkg or .colpkg. This means that unlike syncing via AnkiWeb, you can’t make changes from two locations at once and then merge them - you need to make sure you’ve imported any recent changes from your other device before you make changes, or you’ll end up losing the changes made on one device.

Thus the workflow you would typically use is to export your collection from your mobile device and import it into the computer version, make modifications (such as importing a shared deck you downloaded to your computer), and then export your collection and import it back into your mobile device.

AnkiMobile can’t directly import text files. If you wish to do that, you’ll need to do that with the computer program, and then import your collection into AnkiMobile.

#### From computer to mobile device

On your computer:

1. Open the computer version of Anki.
2. Choose File>Export from the menu.
3. Click the *Export…* button. Make sure to leave "all decks" selected, and "Include scheduling information" must also remain checked.
4. Anki will automatically create a collection.apkg or .colpkg file on your desktop. If the file is named something else like *deckname.apkg*, please see the previous step again.
5. Connect your Apple device to your computer via the USB cable, or wi-fi if you have wi-fi syncing set up in iTunes.
6. Open iTunes if it doesn’t open automatically.
7. Locate Anki’s file sharing section with [Apple’s instructions](http://support.apple.com/kb/HT4094).
8. Drag the collection.apkg or .colpkg file from your desktop into iTunes.
9. Click the sync button inside iTunes.

Then in AnkiMobile, in the deck list screen:

1. Tap the Add/Export button on the bottom left.
2. Choose **Import from iTunes**, then confirm the replacement.
3. If you receive a message about "No file found to import", please read the "on the computer" section above again.

Once complete, the decks on your device will have been replaced with the decks from your desktop.

When you import a collection.apkg or .colpkg file, Anki will avoid copying any sounds or images if they already exist on your mobile device, and are the same file size. This will make imports after the first one considerably faster if you have a lot of media files.

#### From mobile device to computer

On AnkiMobile:

1. Tap the Add/Export button on the bottom left.
2. Choose **Export to iTunes**, and tap **Export**

Then on your computer:

1. Connect your Apple device to your computer via the USB cable.
2. Open iTunes if it doesn’t open automatically.
3. Locate Anki’s file sharing section with [Apple’s instructions](http://support.apple.com/kb/HT4094).
4. Drag the collection.apkg or .colpkg file from iTunes to your desktop.
5. If you’re still using Anki 2.0 on your computer, rename the file to *collection.apkg*. This step is not required if you’re using the Anki 2.1.
6. Use File>Import in Anki to import the file.
7. Confirm you wish to replace, so that the deck from your mobile device overwrites the old data on your desktop.
8. After importing, you can delete the file on your desktop if you wish.

## The Deck List

The deck list is the screen you see when you start AnkiMobile. It displays a list of your card decks, and provides buttons for performing various actions.

Next to each deck, two numbers are displayed. The top, green number corresponds to how many cards are due to be reviewed again today. On a deck you’ve never studied before, there won’t be any cards waiting for review. The second, blue number, corresponds to how many new cards you have to learn today. Anki will introduce 20 new cards a day by default, and you can customize this number in the deck options if you’d like.

To study cards in a deck, simply tap on the deck, and AnkiMobile will switch to study mode.

If you wish to rename or delete a deck, swipe your finger from right to left over it, and buttons will appear.

At the top of the screen, you’ll see four buttons.

- The question mark opens this help page
- The graph icon opens the deck statistics screen.
- The magnifying glass opens the card browser.
- The gear/cog opens the preferences screen.

On the bottom of the screen, there are two more buttons. **Add/Export** allows you to download shared decks, add/create an empty deck, and import/export .apkg files from iTunes. **Synchronize** synchronizes your cards with the cloud.

The synchronize button will change color if you have made changes that need to be synchronized to AnkiWeb, or if changes are waiting on AnkiWeb that need to be synchronized to the device. One of the changes that Anki synchronizes to other clients is the current deck, so tapping on a deck will change the button color, even if you do not study any cards.

## The Study Screen

If you have not used Anki on a computer before, please have a look at the first [intro video](https://apps.ankiweb.net/docs/manual.html#_intro_videos) before reading on, as it explains the basic review process.

When you tap on a deck in the deck list, the study screen will load, and if any cards are waiting to be studied, a card’s question will be shown to you.

If you wish to change to a different deck, you can do so by tapping the top left button. The next three buttons allow you to add cards, edit the current card, and search/browse all cards.

The gear/cog in the bottom right will open up the [tools screen](https://apps.ankiweb.net/docs/am-manual.html#tools).

On the bottom of the screen you’ll see three numbers. From the left, these correspond to new cards, learning cards, and cards to review. These are explained in more detail in the intro videos for the desktop program, so please [check them out](https://apps.ankiweb.net/docs/manual.html#_intro_videos) if you haven’t already.

When you’ve looked at a card’s question and remembered the answer, or decided you don’t know it, tap anywhere in the card area in order to show the answer. When you do, the bottom area will change to display 2-4 answer buttons, depending on how you’ve answered the card previously. The buttons will display the time a card will next be shown, so 10m means "10 minutes" and "5d" means "5 days". You can tap directly on these buttons to choose a particular answer.

To make reviewing faster, you can also tap on the card in order to answer it. For more information on the available taps and how to customize them, please see the [taps](https://apps.ankiweb.net/docs/am-manual.html#taps) section.

If you are studying content for which it is useful to sketch something before showing the answer on the card (e.g., characters in a foreign language), AnkiMobile provides a feature called the *scratchpad* (the analogous feature is called the *whiteboard* in AnkiDroid). You can enable the scratchpad by tapping on the tools button, then "Scratchpad".

When you’ve finished the cards that are due to be studied today, you’ll be shown a congratulations message. If you have other decks, you can tap the top left button to return to the decks list and select a different one.

You can tap the home button to close Anki and save your progress at any time, whether you have completed the day’s reviews or not.

If you wish to keep studying the same cards after the congratulations message is displayed, please see the [filtered deck](https://apps.ankiweb.net/docs/am-manual.html#filtered) section.

If you have a bluetooth keyboard, you can use the keyboard to review. Space will show the answer or answer Good, and 1-4 will choose the answer buttons. You can also press *r* to repeat the audio on the current card.

## The Tools Screen

The tools screen will open when you tap on the gear/cog icon in the study screen.

On the top right, there are buttons that will adjust the text size on your cards.

The "Frequent Actions" section contains some commonly used actions. You can rearrange the actions there or remove actions by holding your finger on a button for a second or so.

Below the "Frequent Actions" section is a list of all available actions in AnkiMobile. You can add these actions to the "Frequent Actions" section by long-pressing on them.

### Action List

The following actions can be run from the tools button, or by assigning them to a tap, swipe, or the top bar in the preferences.

- Add

  Opens a new window to add cards to the deck.

- Answer "Again"

  When the answer screen is shown, choose the red button, indicating you wish to review the card again soon. This is useful when you forgot a card or wish to review it more frequently.

- Answer "Hard"

  When the answer screen is shown and there are four buttons, choose the second button from the left, indicating you found the card hard to remember.

- Answer "Good"

  When the answer screen is shown, choose the green button. This is the button you should end up using the most.

- Answer "Easy"

  When the answer screen is shown, choose the button on the right, indicating you found the card too easy to remember and would like a much longer delay.

- Auto Advance

  Allows you to automatically reveal the answer, and automatically rate or bury cards. You can customize the behaviour in the preferences screen.

- Bottom Bar

  Hides or shows the bottom bar, where the answer buttons and card counts are shown.

- Browse

  Opens the card browser, where you can search for and modify cards.

- Bury Card

  Hides the current card from review. It will be shown again the next day, or when you manually unbury cards.

- Bury Note

  Hides the current note from review. It will be shown again the next day, or when you manually unbury cards.

- Card Info

  Shows information about the current card.

- Card Template

  Allows you to edit the card template, changing which fields are shown on the front and back of the card, and the card styling.

- Current Audio +5s

  Jump forward 5 seconds in the currently playing audio.

- Current Audio -5s

  Jump backward 5 seconds in the currently playing audio.

- Custom Study

  Allows you to study outside of the normal schedule. Please see the documentation of the computer version for more information on custom study presets.

- Deck Statistics

  Shows graphs and statistics about your deck or collection.

- Decks

  Returns to the deck list.

- Delete Note

  Deletes the currently shown note and all of its cards. If you’re not studying in multiple directions, this will just delete a single card.

- Edit

  Edits the current card.

- Empty

  Removes all cards from the current filtered deck.

- Filter/Cram

  Allows you to create a temporary deck based on search criteria such as "tag:hard". Please see the documentation of the computer version for more information on filtered decks.

- Flag 1 - 4

  Sets or clears the card’s flag. Flagging cards allows you to find them easily in the browse screen later.

- Mark

  Adds a tag called "Marked" to the current note, so it can be easily found in a search.

- Mark & Bury

  Marks the card, then buries it.

- Mark & Suspend

  Marks the card, then suspends it.

- Night Mode

  Switch the interface between light and dark mode. On iOS 13, use the system dark mode setting instead.

- Off

  Don’t do anything. Useful if you want to disable certain swipes, tap zones and so on. Not shown in the tools screen.

- Pause Audio

  Temporarily stops or restarts the currently playing audio file.

- Rebuild

  When in a filtered or custom study deck, rerun the search to fetch any cards that may newly match the criteria.

- Record Voice

  Allows you to create a temporary recording of your voice, to compare it to audio that you have on your card.

- Replay Audio

  Replay the card’s audio. You can customize whether the audio in the question is replayed while the answer is shown in the computer Anki.

- Reset Card

  Turn the current card back into a new card.

- Scratchpad

  Show or hide the writing pad, allowing you to practice writing characters during review. Anki will remember the on/off state for each card type. You can tap once on the undo button to undo a stroke, or hold on it for a second to clear all strokes. On devices that support pressure sensitivity (iPhone 6S, iPad w/ Apple Pencil), the stroke width will depend on how hard you press.

- Scratchpad Size

  Alters the size of the scratchpad window.

- Set Due Date

  Make the card a review card if it is not already one, and make it due in the number of days you specify. If you choose 0 days, the card will be ready to review immediately.

- Show Answer

  Reveals the answer when a card’s question is shown.

- Study Options

  Show the study options screen.

- Suspend Card

  Prevent current card from being shown during review until you unsuspend it via the search action.

- Suspend Note

  Prevent all cards of current note from being shown during review until you unsuspend them via the search action.

- Top bar

  Show or hide the bar at the top of the screen.

- Tools

  Show the tools screen.

- Unbury Deck

  Makes any buried cards in the current deck ready for review again.

- Undo

  Undoes the last review.

## Study Options

The study options can be accessed from the [tools](https://apps.ankiweb.net/docs/am-manual.html#tools) screen. Almost all the options available in the computer version can also be adjusted in AnkiMobile. For a description of what everything does, please see the [computer documentation](https://apps.ankiweb.net/docs/manual.html#deckoptions). While some of the options have different wording, the behaviour is the same as the computer version.

## Preferences

The preferences screen can be accessed by tapping on the gear icon at the top right of the deck list. It allows you to customize various application settings and how AnkiMobile appears.

The Preferences screen is divided up into different sections, which are covered below.

### Syncing

The syncing screen allows you to customize cloud synchronization with AnkiWeb. For more information on syncing with the cloud, please see [this section](https://apps.ankiweb.net/docs/am-manual.html#ankiweb).

- Sync Sounds & Images

  By default, AnkiMobile will sync sounds and images as well as your cards and review history. If you disable this option, sounds and images will not be synced by AnkiMobile.

- Full Sync

  The full sync button allows you to force a full upload or download of your cards. This is useful if you accidentally deleted some cards and want to revert to the local or remote version, instead of having those deletions propagate to other devices. After tapping the button, you’ll be given a choice of whether you want to upload your collection or download it from AnkiWeb. Please note this option only affects how cards, notes and review history is transferred - it does not change how sounds and images are synced.

### Review

The review screen allows you to customize how AnkiMobile behaves when you’re reviewing cards.

- Feedback Ticks

  Flash a tick or cross in the top right to confirm your answer choice.

- Tools Overlay Button

  Show the gear/cog icon on the study screen. If you prefer not to see it, you can assign the tools action to the top bar instead.

- Tools Overlay Position

  Allows you to put the tools button on the left.

- Audio Buttons

  Allows you to hide the play button that appears for each audio file you’ve placed on the card. Useful if you’d rather replay audio via the "Replay Audio" action bound to a swipe or tap.

- Always Duck + Ignore Mute

  When enabled, AnkiMobile will quieten any music you have playing in the background, and will automatically play audio even when the mute/vibrate/silent switch is turned on.

- Answer Keeps Zoom

  By default, if you have zoomed in on a card, the screen will zoom out when you reveal the answer. If you enable this option, AnkiMobile will not zoom out.

- Never Type Answer

  If you have set up your cards to ask you to type in the answer (as explained in [this section](https://apps.ankiweb.net/docs/manual.html#templates) of the desktop manual), AnkiMobile will display a keyboard on such cards and allow you to check your answer. If you find typing on a mobile device inconvenient, you can use this option to disable the keyboard for all cards.

- Shake Action

  Allows you to customize what happens when you shake your device. The default action is to undo the previous answer.

- Double Tap Prevention

  This option ignores a second tap when two taps are made in quick succession, so that you don’t accidentally reveal the answer or advance to the next card. If you review your cards very quickly, you may wish to select a shorter detection time.

### Review: Scheduling

These options affect the way Anki schedules cards in all decks.

- New/Review Order

  Whether Anki should introduce new cards before, after, or together with review cards.

- Day Starts

  Controls when a new day starts and new cards become available. Default is 04:00, which means new cards become available at 4AM.

- Learn Ahead Minutes

  The number of minutes to look ahead when the only cards remaining to review with a next repetition time in the future. The default is 20 minutes, which means cards due to show in 10 minutes will be shown immediately if nothing else is available to show.

### Review: Notifications

When enabled, Anki will display an alert at the selected time of day, reminding you to study and telling you how many reviews are waiting.

### Review: Top Bar

You can assign frequently used actions to the top bar for convenient access. For an explanation of the available actions, please see the [actions list](https://apps.ankiweb.net/docs/am-manual.html#actions).

### Review: Bottom Bar

- Show Bottom Bar

  Hides or shows the bottom area that shows the answer buttons and card counts.

- Remaining Count

  Whether to show the card counts when the question side of a card is being shown.

- Answer Buttons

  Whether to show the answer buttons on the answer side of a card.

- Next Times

  Whether to show the next study time above each of the answer buttons.

### Review: Taps

When you’re reviewing, you can tap on different parts of a card in order to trigger different actions.

Anki divides the screen into 9 sections:

| Top Left    | Top Center    | Top Right    |
| ----------- | ------------- | ------------ |
| Mid Left    | Mid Center    | Mid Right    |
| Bottom Left | Bottom Center | Bottom Right |

Each section can have a different action assigned to it if you wish, and the taps when the question is shown are also different from the taps when the answer is shown.

By default, AnkiMobile responds as follows when the question in shown:

| Show Answer | Show Answer | Show Answer |
| ----------- | ----------- | ----------- |
| Show Answer | Show Answer | Show Answer |
| Show Answer | Show Answer | Show Answer |

In other words, tapping anywhere on the screen will show the answer.

When the answer is shown, by default AnkiMobile responds as follows:

| Answer "Again" | Off  | Answer "Good" |
| -------------- | ---- | ------------- |
| Answer "Again" | Off  | Answer "Good" |
| Answer "Again" | Off  | Answer "Good" |

This allows you to tap on the left side of the screen to trigger the red button, and the right side of the screen to trigger the green button. Taps near the middle of the screen will be ignored.

You can assign frequently used actions to taps for convenient access. For an explanation of the available actions, please see the [actions list](https://apps.ankiweb.net/docs/am-manual.html#actions).

### Review: Swipes

You can also swipe up, down, left or right across a card to trigger an action.

To ensure swipes don’t interfere with your ability to scroll on a large card or select text, a swipe must begin from the far left or right side of the screen. Begin by placing your finger on the left or right side of the screen, and then move it up, down, left or right to trigger the relevant swipe.

With the default settings:

- Swiping left displays the tools window
- Swiping right returns to the deck list

You can assign frequently used actions to swipes for convenient access. For an explanation of the available actions, please see the [actions list](https://apps.ankiweb.net/docs/am-manual.html#actions).

### Review: Scratchpad

- Ignore Fingers

  When enabled, the scratchpad will only respond to the Apple Pencil.

- Undo Clears All

  Reverses the behaviour of the undo button, so a quick tap clears everything, and a long press clears the last stroke.

- Scratchpad Below Buttons

  Whether the scratchpad should be placed above or below the bottom bar.

### Review: Auto Advance

- Wait for Audio

  Don’t advance until the current audio stops playing.

- Answer Action

  Whether to bury the card, answer it, show a popup reminder, or do nothing.

### Review: Gamepads

From AnkiMobile 2.0.53+, you can control the study screen with a game controller on iOS 13+. The controller must be supported by iOS, and already paired with your iOS device. Please see the following page for supported controllers, and how to set them up:

https://support.apple.com/en-au/HT210414

The gamepads section of the preferences allows you to configure which actions are triggered when each button is pressed. You can assign an action to each direction on the d-pad, but the analog thumbpads can not be customized - they will always scroll the card up or down.

### General

- Legacy Editor

  When enabled, Anki uses an older editor that has fewer features. It is provided for users stuck on iOS 12 or earlier, who use right-to-left languages. If you are on iOS 13 or don’t use a right-to-left language, the regular editor is a better choice.

### Theme

The theme screen allows you to customize the bar colours AnkiMobile uses. The available options will depend on whether night mode or iOS 13’s dark mode is enabled.

To customize the appearance of your cards, you’ll need to alter your card templates. You can do this using the Card Template action in the tools screen, or by using the computer version. For more info, please see http://www.youtube.com/watch?v=F1j1Zx0mXME&yt:cc=on

### Profiles

Profiles allow multiple users to study with the same device. You can add profiles from the settings screen. To rename or remove a profile, swipe to the left on it.

Each profile needs to be synced with its own AnkiWeb account. Please be careful not to sync two profiles with the same AnkiWeb ID, as this could lead to data loss.

### Backups

AnkiMobile will automatically create backups of your collection for you. The backups include all your cards and statistics, but do not include sounds or images, since they take up a lot of space.

The backup is taken in the background when you return to your device’s home screen, or switch to another app. A backup will only happen if more than an hour has elapsed since the last time a backup was created. AnkiMobile will store the last 15 backups.

To restore from a backup, open the Backups section in the preferences, and tap on the backup you wish to restore to.

It is also possible to customize the frequency and amount of backups that are created, via the settings at the top of the backups section. You can change 15 to a different number to adjust the number of backups - set it to zero to disable backups completely.

If you’re unable to get AnkiMobile to start due to a serious error, you can still retrieve the backups from the iTunes file sharing area:

1. Connect your Apple device to your computer via the USB cable.
2. Open iTunes if it doesn’t open automatically.
3. Locate Anki’s file sharing section with [Apple’s instructions](http://support.apple.com/kb/HT4094).
4. Drag the your backup files from iTunes to your desktop.
5. With the computer version of Anki, create a new, empty profile via File>Switch Profile, and then File>Import the latest backup apkg from within that profile to confirm that it’s ok. If it is corrupt, you can try a previous backup.

### Check Database

This will check your collection for a number of possible errors and fix them if possible.

It also will remove any tags that are no longer used by any cards.

### Check Media

This scans all your notes for references to sounds and images, and then checks to make sure that the sounds and images are available. It will display a report letting you know of any sounds or images that are missing, and any sounds or images that are not used by any cards. If you tap the delete button, the unused sounds or images will be deleted.

## Adding Material

To add cards to a deck, tap the "Add" button while reviewing.

The "Type" button at the top allows you to select the type of note you’d like to add. For more information about note types, please see the introduction in the [computer version’s manual](https://apps.ankiweb.net/docs/manual.html#basics).

When you tap on a field, a keyboard will come up, allowing you to type in information. You can use the next and previous buttons to move between fields.

The toolbar has the following icons:

- B I U

  Mark the text as bold, italics or underline.

- Fx

  Remove formatting.

- Paintbrush

  Only available in iOS 13+. Sets the text color.

- Paperclip/Camera

  Allows you to add media files from the camera, microphone, photo library or from a file. On iPads, the mic button is shown separately.

- Pen

  Only available on iPads on iOS 13+. Allows you to draw an image and attach it to the card. You can later edit a drawn image by holding two fingers on it.

- Square root

  Only available in iOS 13+. Shortcuts to subscript/superscript, and [MathJax](https://apps.ankiweb.net/docs/am-manual.html#mathjax).

- Eye

  Shows a preview of how the card will appear when reviewed.

- </>

  Reveals the underlying HTML that fields are comprised of.

When you’ve typed in the content of a note, hit the save button to add it to your collection.

## Editing

To edit a note, tap the "Edit" button while reviewing.

The edit screen is similar to the adding screen mentioned above, with some key differences:

- There is no note type selection button or deck selection button. If you want to change the type of an existing note, you currently need to do so with the computer version of Anki.
- There is a "Tools" button at the top of the screen. Tapping on it will allow you to perform actions on the current card or note. Please see the [action descriptions](https://apps.ankiweb.net/docs/am-manual.html#actions) for more information on what each action does.

## Browsing

You can search or browse your deck by tapping the "Browse" button while reviewing.

The browse screen will show all the cards in the current deck by default.

You can type text into the search box in order to limit the cards further. If you only wanted to show cards in the current deck that contain the text "hello" for example, you’d modify the text so it says deck:current hello and then tap return. If you wish to search across multiple decks, you can remove the deck:current part.

AnkiMobile supports all the search strings that the desktop version of Anki does, allowing you to perform quite complex searches. Some examples:

- tag:marked

  show cards that with the tag "marked"

- is:due

  show only cards that are waiting for review

- front:rabbit

  show only cards where the front field is exactly "rabbit"

For a full list of the possibilities, please see the section in the [desktop manual](https://apps.ankiweb.net/docs/manual.html#searching).

Tapping the Filter button will reveal a list of filters you can apply, like the side bar in the computer version. Tapping on a line will replace the current search; you can also swipe on a line to add to the existing search instead.

The Options button will allow you to change what is shown in the left and right columns, and change the order cards are shown in.

The Select button allows you to select multiple cards at once, and then perform actions on them like changing their deck, or suspending them.

## Filtered Decks

Anki is designed to optimize the learning process, so that you study the minimum amount necessary to remember the majority of your cards. Once the congratulations screen is reached, further study becomes a case of diminishing returns: the amount of extra time spent going over the same cards again is generally not worth the moderate increase in retention you’ll see.

That said, if you have a test looming, or simply want to pass some time, it’s possible to keep reviewing once the congratulations screen is reached.

A *filtered deck* is a temporary deck that contains cards based on various criteria, such as "forgotten today", "is tagged *hard*", and so on. After studying cards in a filtered deck, or when the filtered deck is deleted, the cards are automatically returned to their original deck.

The easiest way to create a filtered deck is by using the "custom study" feature. A custom study link will appear when you’ve finished all waiting cards in a deck. You can also access custom study ahead of time by clicking the tools button, and then choosing "Custom Study".

Advanced users can create a filtered deck manually, by clicking the tools button, then choosing "More" and then "Filter/Cram".

For further information on filtered decks, please see the [computer version’s documentation](https://apps.ankiweb.net/docs/manual.html#filtered).

## Advanced Features

### Text to Speech

AnkiMobile 2.0.56+ supports using TTS tags in card templates. Please see [the computer manual](https://apps.ankiweb.net/docs/manual.html#text-to-speech) for more information.

To get the best quality sound, please go to the iOS Settings app, then:

- Tap on Accessibility
- Tap on VoiceOver
- Tap on Speech
- Tap on Voice
- Tap on the voice you want to use
- If there is an (Enhanced) version available, download it.

Please note that Apple limit Siri to their own apps, so you will need to pick a voice other than Siri.

The Voice section will only show options for your current language. To add voices for other languages, tap on "Rotor Languages", and after selecting another language, you will have a chance to download voices.

Like regular audio, text to speech will not play automatically when your device’s mute/vibrate switch is enabled.

### Custom Fonts

AnkiMobile allows you to use non-system fonts on your cards. To set them up, the desktop client is required. Please see [the section in the desktop manual](https://apps.ankiweb.net/docs/manual.html#installingfonts) for more information.

Please note that AnkiMobile has to load the entire font into memory in order to use it, and fonts for Asian languages can be quite large. If you have an older device and notice AnkiMobile crashing frequently after installing a font, you may have exceeded your device’s memory limits.

### Night Mode Styling

By using the Edit Card Template action, it is possible to customize how cards appear when night mode/dark mode is enabled.

If you wanted a grey background instead of black, you could use something like:

```
.card.nightMode { background-color: #555; }
```

If you have a *myclass* style, the following would show the text in yellow when night mode is enabled:

```
.nightMode .myclass { color: yellow; }
```

### URL schemes

AnkiMobile supports URL schemes for opening third party dictionaries, and for adding content to AnkiMobile from other applications.

#### AnkiMobile’s URL Scheme

A *URL Scheme* is like a link to a website, but it instead links to an app. A simple example is:

```
anki://
```

If you type this into Safari on your device, you’ll see AnkiMobile open up.

From 2.0.30 onwards, AnkiMobile provides a scheme for adding new notes to your collection. This can be used with dictionary apps that support calling other apps via URL schemes, and with automation apps like Workflow.

The scheme to add cards looks like this:

```
anki://x-callback-url/addnote?profile=User 1&type=Basic&deck=Default&fldFront=front text&fldBack=back text
```

The first part must always be there:

anki://x-callback-url/addnote?

After the first part, keys and values are separated by an ampersand. The following keys must always be provided:

- profile=<profile name>
- type=<note type name>
- deck=<deck name>

Fields are entered by prefixing their name with "fld". So if your first field is called "Text", the key would be "fldText". The field text is interpreted as HTML, so if you wanted a newline in the text you’d use something like "line 1<br>line 2".

Special characters in the URL must be escaped. For example, if you have spaces in a field, they must be represented with %20. If you’re using the Shortcuts app, there is a URL encode action which you may find useful.

The remaining keys are optional:

- tags=<tags separated by space>
- dupes=1 - if provided, allow a note to be added even if the same content is on an existing note.
- x-success=<url scheme for another app> - use to automatically return to another app after the note is added.

If a field you provide is a link to an image or audio file, AnkiMobile will automatically download that media and place a link to it in the field. Eg:

```
fldFront=http://example.com/image.jpg
```

The link will only be downloaded if it ends with a recognized file extension. If your link is to a dynamic webpage, you can add a fake argument with the extension at the end, eg http://example.com/getImage?imgID=1234&fakePath=foo.jpg. Be careful to escape the URL before including it in the URL scheme, as otherwise ? and & characters will be interpreted as part of the URL scheme instead of the URL.

#### Dictionary Links

The desktop version of Anki provides the ability to open a web page based on the contents of a field, for easily creating a link to an online dictionary site. This is documented [in this section](https://apps.ankiweb.net/docs/manual.html#_dictionary_links) of the manual, though please start from the [cards & templates](https://apps.ankiweb.net/docs/manual.html#templates) section as the above link assumes you have read it.

Like the desktop, AnkiMobile supports links to dictionary websites. In addition to that, you can also link to different dictionary apps that you have installed on your device using a URL scheme.

Some dictionary apps provide a URL scheme that allows you to provide a particular phrase to search for. For example, an app called iDict+ allows the following type of URL:

```
idictplus://?search=mysearchtext
```

If you have iDict+ installed and type that into Safari, iDict+ should open up and immediately search for "mysearchtext".

iDict+ also supports passing a return link. We can replace the above with:

```
idictplus://?search=txt&scheme=anki://
```

If you type that into Safari, it will search for "mysearchtext" like before, but will also provide a "return" button that when pressed will open up Anki.

By taking that text and combining it with the instructions for the desktop version linked above, it’s possible to have a link on your cards that searches for a word in another app, and then allows you to return to Anki when you’re done.

Unfortunately, there is no standard for URL schemes: some apps implement them, some don’t, and the way they implement them can different. For example, in the app called "Kotoba!", the URL scheme is:

```
kotoba://dictionary?word=mysearchtext
```

Note how not only the app name differs but also the text after it, and how Kotoba! doesn’t provide the ability to automatically return to the app that opened it, meaning that you need to double tap the home button and manually return to AnkiMobile.

Some dictionary apps publish their URL scheme in their documentation. If you’re using a dictionary app that doesn’t, please contact the authors and ask them for more information.

### MathJax

AnkiMobile supports MathJax out of the box. Simply place something like the following on your card:

```
This is some text \(x^2\) with an inline equation.
An equation block:

\[\sqrt{-1}\]
```

### Javascript

The [warnings](https://apps.ankiweb.net/docs/manual.html#javascript) that apply to the computer version also apply to AnkiMobile.

In addition to the above, another thing to be aware of in AnkiMobile is that your code also needs to play nicely with AnkiMobile’s tap detection. Taps on A/BUTTON elements, or elements that have an onclick handler should work as you expect.

If you have other elements that must receive tap events, give them the class *tappable* to tell AnkiMobile 2.0.39 or later that it should pass taps through to the element.

### Furigana

When combining the furigana/kanji/kana filters provided by the Japanese Support add-on with cloze or hint fields, the cloze or hint fields must come second in your template.

The following will work for example:

```
{{furigana:cloze:Text}}
{{kanji:hint:HintField}}
```

The following will not work in AnkiMobile before 2.0.39:

```
{{cloze:Furigana:Text}}
```

### Play Buttons

You can change the size of the play buttons by placing the following in your card template, adjusting 32 to suit.

```
img.playImage { width: 32px; height: 32px; }
```

### Image Resizing

When you attach an image from the photo gallery it is automatically resized to have a maximum length of 1024 along its longest edge.

As of 2.0.39, you can customize this limit. For example, to set it to 2048, run the following in the computer version’s [debug console](https://apps.ankiweb.net/docs/manual.html#debug-console) then sync to AnkiMobile:

```
mw.col.conf["amImageMaxSize"] = 2048
mw.col.setMod()
mw.col.save()
```

### Debug Log

If you’re encountering a problem with Anki and we’ve asked you to provide a debug log, please follow the following steps:

1. Connect your device via USB.
2. Open iTunes if it doesn’t open automatically.
3. Locate Anki’s file sharing section with [Apple’s instructions](http://support.apple.com/kb/HT4094).
4. Drag the debug.log file on to your desktop, then attach it to your support ticket.

## Translating AnkiMobile

If you’d like to help translate AnkiMobile into your native language, your help would be most appreciated! Please drop us a line on the [support site](https://anki.tenderapp.com/discussions/private), indicating which language(s) you’d like to translate, and we can send you an invite.

### Suggestions & Copyright

The translation site we use provides automatic suggestions for translations based on the text people have entered into other projects. This makes writing translations easier, but also requires us to contribute any translations we make back to other projects as well. For this reason, we ask that you release any contributions you make on the translation site into the public domain.

### Glossary

When you open the translations site, you should see two items to translate: "glossary", and "interface". The "glossary" is a small list of important terms that are frequently used in Anki’s interface, and the "interface" contains all the text used in AnkiMobile.

It’s best to start on the glossary first, as it’s small, and the terms are frequently used. The glossary contains terms like:

```
deck

Context: From "card deck" - a group of cards.
```

You only need to translate the word or phrase at the top - please do not translate the context part.

Once the glossary is done, you can start on the interface. Any glossary terms that appear in the interface will be underlined, and you can click on them to insert the glossary translation. This helps keep translations consistent.

### Context

For each phrase that requires translation, you can see some context to help understand where the phrase will be used. For example, for the phrase "A big thanks to everyone who has provided translations, bug reports, and suggestions", the context might appear as:

```
src/i18n/en.lproj/Localizable.strings
thanks-contributors
About Screen
```

- The first line can be ignored.
- The second line may be the same as the phrase, or may be a short summary.
- The third line lists the parts of AnkiMobile the phrase is used in, and may sometimes include extra comments to help.

Some parts that may need more explanation:

- Actions, Actions Manager

  These are the various functions you can access from the tools screen, or by assigning them to a tap, swipe or the top bar. Actions have a normal description, and a short description that is used when they are placed in the top bar - for example, Show Answer becomes S.Ans when shown in its short form. When translating, please try to use a translation that is about the same length.

- Edit Screen

  The screen shown when using the Add and Edit actions.

- Standard Models

  Note types like "Basic (and reversed card)"

- Syncer

  Part of the sync feature.

- Utils

  Utilities used by various parts of AnkiMobile’s code.

### Formatting

When translating, some phrases contain special markers in the text, which indicate extra text will be put in the marker’s place. For example, a string like Cards: %d or Error: %@ means that the %d/%@ part will be replaced with some other value, such as Cards: 10, or Error: file not found. When writing your translation, please leave the special markers as they are, such as カード: %d.

Sometimes the text will contain more than one replacement marker, like %1$d of %2$d to represent something like 2 of 5. You can reorder the markers if it makes more sense in your language, eg %2$dの%1$d to represent something like 5の2.

In some languages, words change depending on the associated number, such as "1 dog" vs "2 dogs". You may be prompted to enter different words for "one" and "many" for some phrases.

When translating numbered/plural items, please translate all cases, or none. If you partially translate a numbered item, it will cause problems.

The ampersand symbol (&) needs to be written as &nbsp;.

### Getting Help

If you’re not sure how something should be translated, there are a couple of things you can do:

- Clicking on "TM and MT suggestions" will show how similar text has been translated in other projects on the translation site in the past. If the text looks correct, you can click on it to automatically add it as a translation.
- If the text has been translated in another language already, you can click on "Other Languages" to see how it was translated in the other language.
- If your browser window is wide enough, there is a comments section on the right, where you can post questions, and see what other people have said.

### Testing

Each time a new AnkiMobile beta is released, it will include any translation changes that were made since the last time. Please give the betas a try, so you can see how your translations appear in the app. If you’re not already a beta tester, a signup link will be included with the invite to the beta testing site.

When translating, please try to keep the translations about the same length as the original English text. If it is not possible, and you find that text is not appearing properly in a beta (such as two labels overlapping), please report the issue on the support site.

When testing the betas, if you notice that some text is not translatable, please report this on the support site so it can be fixed.

Thank you again for your help!



------

Apple, the Apple logo, iPhone, iPad and iPod Touch are trademarks of Apple Inc., registered in the U.S. and other countries. App Store is a service mark of Apple Inc.