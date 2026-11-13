---
layout: post
title: "How I came across this community project of translating GTASA to Chinese and Japanese?"
date: 2026-11-11 12:00:00 +0530
category: gtamodding
tags: gtasa translation localization modding
---

If you like my work and want to support my mods, consider donating to [my Ko-fi page](https://ko-fi.com/abums1210) or my [Patreon](https://patreon.com/cw/abums1210). My mods will always be free to use.

TLDR: Big thanks to GTAForums user [AsukaXVB](https://gtaforums.com/profile/1260921-asukaxvb/) for testing the language support and [kagikn](https://gtaforums.com/profile/938109-kagikn/) who also released a [plugin for adding japanese character support](https://kagikn.com/gtasa-jpn-loader-asi/) back in 2019. And the various unknown contributors of this localization project which ran on Google Sheets back in 2019 as well. I don't have write access so I don't know the names of the people who contributed to it, but it's a fantastic job. Maybe it's kagikn who led the localization project as well? ([Better Kanji GXT](https://kagikn.com/gtasa-better-kanji-gxt/))

Click [here](https://drive.google.com/drive/folders/1pkgiBTeVLi00uqb8Lxtm3nA8jUNq0jce?usp=sharing) to download the combined Chinese/Japanese csv compatible with EasyGXT, based on above sources.

<!--more-->

It was on a fine Monday night in August, a week after I had released this mod EasyFont on NexusMods. I opened the mod page and checked if anyone had provided feedback on the release.

And there was a user named "BVXakusA", who reported an issue with the line wrapping being broken in chinese and japanese texts, owing to the lack of spacing. As an expert on neither, it was a good feedback, something I had never considered. As a person who is a native Tamil speaker and a decently fluent speaker of English, I have always grown up to the concept of spacing between words to differentiate each one while writing. While speaking, I believe all kinds of languages do use pauses and fillers to be understandable to the listeners.

But does the same thing apply for writing? In the case of the languages I knew, it does. Punctuation, spacing, accent marks etc. are used to represent the sounds and make the text readable and understandable as if someone is reading the content into your ear.

While Chinese is something I knew barely nothing about, apart from the greeting and the famous John Cena eating ice cream meme, Japanese was something I listened a lot via the anime I used to watch from my college days. It piqued my interest enough for me to download Duolingo and get stuck in learning limbo for a few years before I eventually gave up. I did pay decent money to learn Kanji - the symbols used to represent words, via an android app. That app is still in my app drawer, having barely made progress. 

These app makers were kind enough to split sentences into readable chunks for learning the words. Perhaps this is where I learned incorrectly that it must be the same in general use as well - that the words and symbols are seperated in public writing. Via anime though, I learned something even crazy, that they write vertically and from right to left on gridded papers. All that horizontal left to right was on digital and print media I suppose.

Enough wallowing in the past - the point is, various misleading factors in my life had led me into this very assumption while making the mod that I didn't even think once about this. A mod which aims to bring localization of multiple languages under one umbrella, which failed on the basic task of word wrapping. So, I would be very thankful to "BVXakusA" for pointing this out via the comments at the early stage.

In the next few days, we had a single comment discussion every day, with me trying to narrow out the possible issues and where they occur. It was during this time that they shared 2 links to blog posts written by a Japanese author named "kagikn" ([gtasa-jpn-loader-asi](https://kagikn.com/gtasa-jpn-loader-asi/) and [gtasa-better-kanji-gxt](https://kagikn.com/gtasa-better-kanji-gxt/)). I knew that native translations were available in Japanese to these games, and yet it was a mystery to me as to why this mod was made. I opened the blog post to find everything was in Japanese. I couldn't read that, and the translator wasn't doing a great job of translating the blog, so I left it for later.

On August 7, I got a Discord chat request from "AsukaXVB". I was wondering where did I meet with them before for them to send a request. Then it clicked to me - they were the same person sending the diagnoses on NexusMods comments section, and the username was basically reversed on NexusMods due to unknown policy rules about usernames.

There, they shared with me 2 links to Excel sheets containing a massive list of retranslated GXT keys from the game.

Below are the links to the Excel sheets. Both of them are read-only and require permission to modify:

- **Japanese**: [Google Spreadsheet](https://docs.google.com/spreadsheets/d/1Xdz2-geabANUcB3CdITb15VPhf9O3Y9mG6MjUlh_D3M/edit)
- **Chinese**: [Google Spreadsheet](https://docs.google.com/spreadsheets/d/1L4R3UxW79aOwH-PT50RIbDOYgcMaoGFNPfnGqFkok58/edit?usp=sharing)

From the file creation date, I came to know these where created way back in 2019, but I don't have an idea of when it finished. GTASA has over 16000 GXT entries, so it's a big job to retranslate and fit it to Japanese dialects (that's what kagikn mentioned).

I myself had already started a small self translation effort using local AI and was doing recorrection by myself for Vice City - my favourite GTA get's first preference. When compared to it, their effort was well organized and designed for collaboration a lot better. But mine was based on the output sheet of EasyGXT. Inorder to use their translation sheet with my mod, I had to reformat it into a complete .csv file with all the keys and values in a single sheet. With the help of Gemini, I quickly got a Python script to automate this whole process. Sooner or later, I got a complete CSV file for both Chinese and Japanese which I could just drop into the EasyGXT folder and get it working.

So, now I can finally focus on the core of the issue. My idea with line wrapping in Latin character sets and my own language is that they use spaces to distinguish words. So if we are wrapping a sentence to fit a certain character limit, we should ensure that the wrapped sentence still reads legibly without breaking the words in the middle for maintaining the character count. To overcome this, the simpler solution would be to write a condition for CJK (Chinese-Japanese-Korean) character sets to wrap on any character. Right?

That was wrong. During the research, I came across [Line breaking rules for these languages](https://en.wikipedia.org/wiki/Line_breaking_rules_in_East_Asian_languages). In Japanese, they called in Kinsoku Shori (basically translated as prohibition rules). To summarize, these languages have certain rules that prohibit the sentences from ending or starting in certain characters or symbols. I don't want to dive much into this, but I managed to set up the rules and conditionals into the code and tested it at my end.

After various rounds of testing, I finally got it to work at my end. Problem solved! Or so I thought. I understood that I had done the second mistaken assumption that the system locale that I use, and the one that Native Chinese/Japanese/Korean use must be the same. It was wrong, obviously.

Back in early lockdown, around 2020, I was quite invested in playing all the available titles in the Sci-ADV franchise, known for the popular anime "Steins Gate". It's like the MCU of Japan with various games of different storylines with converging characters. Almost all the popular titles were available except the first one, Chaos;Head. It was region locked to Japan, and from the Reddit sources, I learnt that the only way to play it legitimately is to obtain a copy of it from Japan, change the system locale and pray it works. I didn't wanna put that much effort of acquiring the copy, so I just watched a playthrough on Youtube and was done with it. And I had forgotten about this events until I came across this locale issue again.

I had shared the working copy with AsukaXVB, hoping that the issue was resolved and they should be able to get the correct display of sentences with proper wrapping. When they replied back with the screenshots of the issue they had, the situation had become unclear. The wrapping was working fine, but the characters at the end of sentence were repeating, and there were question marks in the middle of sentences.

I assumed it was the locale, and suggested them to change it. Then they showed me the edited .csv file, and I noticed the encoding as UTF-16 LE BOM. The .csv file generated by EasyGXT encodes it as UTF-16 LE by default. This encoding supports wide characters and naturally supports a lot of languages. GTASA does use UTF-8 only, but EasyGXT will do the job of char conversion on its end. The only caveat is the encoding shouldn't have BOM (Byte Order Marks). Based on my research, it was used on UTF-8 but not really needed in UTF-16. So I provided my own file to them. Still they had the issue.

I was pondering. I felt I had tried all the possible avenues.

After sometime, they came back to me with the info that they had indeed tried changing the locale to English (US) and the mod had worked. But this was not a long term solution. As system locale is tied with a lot of things that could affect everyday computer usage, so having to change it everytime you play the game? That doesn't suit the intention and the naming of this mod. The purpose was to drop in the files and play the game without any hiccups.

Later I learnt that they were playing on Steam Deck, and there was actually an option to enable UTF-8 support for rendering languages across the world. They enabled it, and were pleased to report that the mod was now working fine.

So once again, I would like to thank AsukaXVB for reporting and testing these issues that helped me not only to solve the issues, but also break the assumptions and learn more about how languages are being handled across the world. I would also like to thank kagikn who originally worked on the localization efforts based on which we managed to create the working .csv file.