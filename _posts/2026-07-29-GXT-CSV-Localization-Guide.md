---
layout: post
title: "GXT.csv Localization Guide"
date: 2026-07-29 12:00:00 +0530
category: gtamodding
tags: gta3 gtavc gtasa text font modding how_to_guide
---

To read the original GTAForums post, [click here](https://gtaforums.com/topic/1006726-asiiiivcsa-easyfont-v10-ttfotf-font-replacement-system/).
If you like my work and want to support my mods, consider donating to [my Ko-fi page](https://ko-fi.com/abums1210) or my [Patreon](https://patreon.com/cw/abums1210). My mods will always be free to use.

Before starting, ensure that you have already installed both EasyFont and [EasyGXT](https://gtaforums.com/topic/1006231-asiiiivcsa-easygxt-v12/).  
The reason I added the guide here instead of EasyGXT is that without the font hooking, the game is just going to display boxes/empty spaces/random junk.

<!--more-->

Run the game once, and a `.csv` file will be generated in the mod's folder path.

I used Tamil language as an example in below screenshots and documents as it's the only non-English language I'm proficient in.

---

### Editing the CSV

#### For offline editing:
* If you are okay with the commas and long scrolling, Notepad is fine. It supports the Unicode formatting.
* **Excel is not preferred.** The `.csv` file is output with UTF-16LE format by default. Saving it in Excel strips the formatting. If you edit with Excel, save the `.csv` and run the game, you will get mismatched values on your display.
* I edited my `.csv` offline on VS Code (yeah, not kidding). I searched the internet for a stable `.csv` editor and the one I got just froze, unable to handle the thousands of rows.

Below are the row counts of the `.csv` of each game:
* **GTA III**: 2,756 rows
* **GTA VC**: 4,924 rows
* **GTA SA**: 16,616 rows

VS Code has a neat extension called **"CSV"** which was pretty stable and allowed me to edit in a tabular format. It also didn't crash or stutter, though there were jumping issues when I save the file.

![VS Code CSV Editor](https://gtaforums.com/uploads/monthly_2026_07/image.png.fed298d464cc2c7a118a8c341665a7ee.png)

#### For online editing:
I uploaded the `.csv` to Google Drive and edited the `.csv` using Google Sheets. Once I was done with the changes, I downloaded it as `.csv` and put it in the game folder. It worked surprisingly well.

![Google Sheets](https://gtaforums.com/uploads/monthly_2026_07/image.png.76bf1689092c909d73e6a6fdc86bbd5c.png)
---

### Translation

When you open the `.csv` and look, there would be 5 language rows in GTA VC/SA.  
There is an extra language row named as `"english"` in GTA III (from the `.gxt`).

In-game though, generally there are 5 languages supported in III/VC exes. SA's language support depends on the versions. The 1.0 exe I had showed 2 languages only.

Since the language you add is unsupported, you can just use the column name of one of the available languages, and replace the available language with some other. Then you can add a tracking column for your reference — whether you translated or not. You can also use it as a tracking column in case you are collaborating online using Google Sheets.

> **Note**: `KeyName` is not there in GTA SA GXT files. They use the `KeyHash` instead.

#### Manual translation:
To translate each and every row is a tiring process I am sure. If you have all the time in the world — if you are really bored — if you want to dedicate your life to translations — go for it.

#### Refined machine translation:
Unfortunately as someone with a day job, I cannot really spend much time on fully manual translations.

So, I used a mix of Python and a local LLM called **"translategemma"** in Ollama and machine translated all of the 3 games. A translation LLM model is lightweight compared to general use LLMs. I ran this activity in a 6GB VRAM laptop and it ran without any hiccups.

I have uploaded the stuff I used and generated [here](https://drive.google.com/drive/folders/122_QfOWfgXHRvfamOnExBrHnxdBsuR6z?usp=drive_link).

> **Note**: I did try the API key of a general LLM but I quickly exhausted the API request limit. If you have a better subscription you can try.

Most lines of GXT have parsing tokens `~b~`, `~q~`, etc. which are used to format the text in gameplay to be bold, colorful, and so on. So we also need to preserve them during the translation. I made use of 3 Python files to speed up the process:

#### `gxt_translator.py`:
* Before sending text to the LLM, it replaces the GXT tokens with placeholders.
* This reads the `.csv` rows on batches, inputs them as a translation request to "translategemma" as an API request, and writes the response to the `.csv`.
* While doing the batch translation, it saves each translated line on a checkpoint file. If a row translation fails, it's sent to a backlog file.
* Once a full set of rows are translated, you will be offered an option to retranslate the backlog.
* LLMs write formally. A bit too much. This being an offline model, had its own share of flaws. Even when the translation prompt requests to be informal and use street vocabulary, it struggles. Sometimes, it mixes up different language character sets.

#### `output_validator.py`:
* Checks the output `.csv` checkpoint for formal words, unresolved GXT token placeholders, and characters unrelated to the current language.
* If it finds foreign languages, send to backlog. Else, use regex to find and replace the words/parsing token placeholders.
* Once the backlog is finished, you could run `gxt_translator` again with a `--backlog-only` tag. It might fail on some sentences so you might want to run it again and again till it's finished.

#### `add_translated_by_column.py`:
* Just adds the column with text `"machine"` on all rows, right next to the column you specify — indicating it was machine translated. The output is raw on most places.

Now you can use your language skill and refine the output to be more suitable to your needs. Then add your name tag to the lines you translated — easy to find!

Or if you are in a rush, just put the `.csv` in the mod folder (under `"gxt.csv"` name) and the game would run just fine.

> **Note**: You must enable UTF-8 encoding in GTA SA `easygxt.ini` config to allow Unicode characters.

---

If you have any more questions, feel free to ask.
