 http://localhost:3000/manual/anki#profiles 





## The Basics

### Cards

A question and answer pair is called a *card*. This is based on a paper flashcard with a question on one side and the answer on the back. In Anki a card doesn’t actually look like a physical card, and when you show the answer the question remains visible by default. For example, if you’re studying basic chemistry, you might see a question like:

```
Q: Chemical symbol for oxygen?
```

After thinking about it, and deciding the answer is O, you click the show answer button, and Anki shows you:

```
Q: Chemical symbol for oxygen?
A: O
```

After confirming that you are correct, you can tell Anki how well you remembered, and Anki will choose a next time to show you again.

### Card Types

In order for Anki to create cards based on our notes, we need to give it a blueprint that says which fields should be displayed on the front or back of each card. This blueprint is called a *card type*. Each type of note can have one or more card types; when you add a note, Anki will create one card for each card type.

Each card type has two *templates*, one for the question and one for the answer. In the above French example, we wanted the recognition card to look like this:

```
Q: Bonjour
A: Hello
   Page #12
```

To do this, we can set the question and answer templates to:

```
Q: {{French}}
A: {{English}}<br>
   Page #{{Page}}
```

By surrounding a field name in double curly brackets, we tell Anki to replace that section with the actual information in the field. Anything not surrounded by curly brackets remains the same on each card. (For instance, we don’t have to type “Page #” into the Page field when adding material – it’s added automatically to every card.) <br> is a special code that tells Anki to move to the next line; more details are available in the [templates](https://apps.ankiweb.net/docs/manual.html#templates) section.

The production card templates work in a similar way:

```
Q: {{English}}
A: {{French}}<br>
   Page #{{Page}}
```

Once a card type has been created, every time you add a new note, a card will be created based on that card type. Card types make it easy to keep the formatting of your cards consistent and can greatly reduce the amount of effort involved in adding information. They also mean Anki can ensure related cards don’t appear too close to each other, and they allow you to fix a typing mistake or factual error once and have all the related cards updated at once.

To add and edit card types, click the “Cards…” button while adding or editing notes. For more information on card types, please see the [Cards and Templates](https://apps.ankiweb.net/docs/manual.html#templates) section.

### Note Types

Anki allows you to create different types of notes for different material. Each type of note has its own set of fields and card types. It’s a good idea to create a separate note type for each broad topic you’re studying. In the above French example, we might create a note type called “French” for that. If we wanted to learn capital cities, we could create a separate note type for that as well, with fields such as “Country” and “Capital City”.

When Anki checks for duplicates, it only compares other notes of the same type. Thus if you add a capital city called “Orange” using the capital city note type, you won’t see a duplicate message when it comes time to learn how to say “orange” in French.

When you create a new collection, Anki automatically adds some standard note types to it. These note types are provided to make Anki easier for new users, but in the long run it’s recommended you define your own note types for the content you are learning. The standard note types are as follows:

- Basic

  Has Front and Back fields, and will create one card. Text you enter in Front will appear on the front of the card, and text you enter in Back will appear on the back of the card.

- Basic (and reversed card)

  Like Basic, but creates two cards for the text you enter: one from front→back and one from back→front.

- Basic (optional reversed card)

  This is a front→back card, and optionally a back→front card. To do this, it has a third field called “Add Reverse.” If you enter any text into that field, a reverse card will be created. More information about this is available in the [Cards and Templates](https://apps.ankiweb.net/docs/manual.html#templates) section.

- Cloze

  A note type which makes it easy to select text and turn it into a cloze deletion (e.g., “Man landed on the moon in […]” → “Man landed on the moon in 1969”). More information is available in the [cloze deletion](https://apps.ankiweb.net/docs/manual.html#cloze) section.

To add your own note types and modify existing ones, you can use Tools → Manage Note Types from the main Anki window.

| Note | Notes and note types are common to your whole collection rather than limited to an individual deck. This means you can use many different types of notes in a particular deck, or have different cards generated from a particular note in different decks. When you add notes using the Add window, you can select what note type to use and what deck to use, and these choices are completely independent of each other. You can also change the note type of some notes [after you’ve already created them](https://apps.ankiweb.net/docs/manual.html#browsermisc). |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

### Collection

Your *collection* is all the material stored in Anki – your cards, notes, decks, note types, deck options, and so on.