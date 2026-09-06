# Data Encoding

## Overview

Learn how computer encodes characters, from ASCII to Unicode's UTF.

## What I Learned

ASCII is a 7-bit standard that defines 128 characters covering English letters, digits, and basic punctuation. We also noticed how ASCII, with its seven bits, didn’t have room for characters such as ñ, €, あ, or ب. Using eight bits, extended ASCII tried patching this with regional variants (ISO-8859-1, ISO-8859-2, Windows-1252, among many others), but this caused chaos! For example, if the sender writes and saves Ø using ISO 8859-1 (Latin 1) encoding and the recipient opens and reads the document using ISO 8859-2 (Latin 2) encoding, they will see Ř. Hence, it is clear how opening a document requires us to use the same encoding used when saving it; otherwise, various characters will not be displayed correctly, or even more confusingly, they might be incorrectly replaced.

Unicode is a universal character encoding standard. It assigns unique code points to characters from all modern and historical writing systems worldwide. Unicode supports the interchange, processing, and display of text in diverse languages. In other words, we don’t need to worry about picking a specific encoding standard that is compatible with the language we are using. Furthermore, this makes it easy to use different languages in a single file or message. And most importantly, because this is a standard that fits all, we don’t need to worry about the encoding used by the original author, as they will also be using Unicode.

## Exercises

### Exercise 1 — [ASCII]

**Q1.** What is the ASCII code in decimal for the character @?
**Answer:** 64

**Q2.** What is the character that has the ASCII code of 35 in decimal?
**Answer:** #

**Q2.** What is the name of the character that has the ASCII code of 7?
**Answer:** BEL

### Exercise 2 — [Unicode]

**Q1.** What is the UTF-32 encoding of 😌?
**Answer:** U+0001F60C

**Q2.** What is the UTF-16 encoding of シ? Note that ツ and シ are two different characters.
**Answer:** U+30B7

**Q3.** What is the character that has the following UTF-16 encoding U+2615?
**Answer:** ☕

**Q4.** What is the character that has the following UTF-16 encoding U+2658?
**Answer:** ♘

## Key Takeaways

In this room, we learned about ASCII and its limitations, and about Unicode and three encoding standards: UTF-8, UTF-16, and UTF-32. We explored how Unicode enables us to cover not only the world’s languages but also symbols such as chess pieces and emojis.

## Notes

Nothing