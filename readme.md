<div align="center">

![NVDA Logo](https://www.nvaccess.org/files/nvda/documentation/userGuide/images/nvda.ico)

# AbsoluteType

Hear exactly what you typed, hear exactly what you fixed, and feel every keystroke with a satisfying typing sound.

**author:** chai chaimee  
**url:** [https://github.com/chaichaimee/AbsoluteType](https://github.com/chaichaimee/AbsoluteType)

</div>

---

### Introduction

AbsoluteType improves the way NVDA gives you feedback while you type. It does two things:

**1. Smarter spoken feedback for typed words.** When you finish a word, NVDA normally reads it back using its own idea of where a word begins and ends. AbsoluteType instead reads the text that is really in the document, taken directly from the editor. This means that when you correct a mistake, you hear the corrected result and not a confusing mixture of old and new letters.

**2. typeFX typing sounds.** As you press keys, AbsoluteType plays a short sound, much like the keyboard click on a mobile phone. Separate sounds are used for normal keys, the Space bar and the Backspace key. You can choose from many sound packs and set the volume.

Everything can be controlled from a settings panel inside the NVDA Settings dialog, or quickly with a single shortcut key.

---

### Hot Keys

> **NVDA+Windows+W**  
> **Single Tap :** Open the AbsoluteType settings panel  
> **Double Tap :** Turn typeFX typing sounds on or off (NVDA says "typeFX on" or "typeFX off")

**How the tap detection works:**  
When you press the key once, the add-on waits half a second (500 milliseconds) to see whether you press it a second time. If you do not, the settings panel opens. If you do press it again within that time, the pending settings panel is cancelled and typeFX is switched instead. The new on/off state is saved immediately.

> [!NOTE]
> You can change this shortcut in NVDA's Input Gestures dialog, under the category **AbsoluteType**.

---

### Features

#### 1. Settings Panel

AbsoluteType adds its own category named **AbsoluteType** to the NVDA Settings dialog. You can open it with the single tap hot key above, or by opening NVDA Settings and choosing the AbsoluteType category. The panel contains the following controls:

- **Announce only the corrected part after a fix** (check box, on by default)  
  Turns on the correction echo described in feature 2.

- **Announce the full last sentence** (check box, on by default)  
  Makes NVDA read the complete last typed text from the document, as described in feature 3.

- **Play a typing sound (typeFX) as keys are pressed** (check box, on by default)  
  Turns the typing sounds on or off.

- **Only play typeFX sound for letter keys** (check box, off by default)  
  Limits the typing sounds, as described in feature 4.

- **typeFX sound pack** (drop-down list, default: Pixel)  
  Lets you pick the set of sounds used for typing.

- **typeFX volume** (drop-down list, default: 50%)  
  Lets you pick a volume from 0% to 100% in steps of 5%.

- **Type here to test the selected sound** (edit field)  
  Lets you try the chosen sound pack and volume before saving. See feature 5.

Your choices are stored when you press OK or Apply in the NVDA Settings dialog.

---

#### 2. Correction Echo (Announce only the corrected part after a fix)

When you press Backspace to fix a mistake and then keep typing, this option makes NVDA read only the part of the word you have just corrected, together with what you typed after it, once you finish the word.

**Step by step:**

- **Step 1:** You type a word and notice a mistake.
- **Step 2:** You press Backspace. The add-on notices this key press (the normal Backspace key, not a key on the extended keypad area) and remembers that you have started a correction.
- **Step 3:** You type the first replacement character. At this moment the add-on looks at where the caret is, steps back past the character you just typed, and marks the start of the word at that position.
- **Step 4:** You continue typing and then press Space or a punctuation mark to finish the word.
- **Step 5:** NVDA reads the text from the marked starting point up to the caret, instead of the whole word.

**Example:** You type "recieve", realize the mistake, press Backspace a few times and retype the ending. When you press Space, you hear the corrected text from the point of the fix, so you can confirm that the correction is right.

If the marked starting point can no longer be found in the document, the add-on safely falls back to reading the last typed word as described in feature 3.

Moving the caret with the arrow keys or other caret movement commands cancels any correction in progress, so an old correction is never announced by mistake.

> [!NOTE]
> If you did not use Backspace before finishing a word, this option reads the last typed word in the same way as feature 3. When both options are on and a correction has been made, the correction echo takes priority.

---

#### 3. Reading the Last Typed Word from the Document (Announce the full last sentence)

With this option on, when you finish a word, NVDA does not rely on the letters it counted while you typed. Instead it asks the editor for the real text before the caret and reads that.

**Step by step:**

- **Step 1:** You press Space or a punctuation mark after typing.
- **Step 2:** The add-on goes back from the caret one character at a time until it finds a space or the beginning of the text.
- **Step 3:** Everything in between is read out as one piece. A punctuation mark you have just typed at the very end is left out of what is spoken.
- **Step 4:** If the text found is only blank space, nothing is spoken.

**Example:** If you type "well-known" and press Space, the whole of "well-known" is read, because the search for the start only stops at spaces.

If you press Enter without having typed any character since the last caret movement, nothing is announced.

> [!NOTE]
> The label of this option mentions a "sentence", but based on the way the add-on works, the text it reads is the text back to the previous space, which is the last typed word.

---

#### 4. typeFX Typing Sounds

While typeFX is on, a sound is played every time you press a key that types a character, and also when you press Backspace. Three kinds of sound are used:

- **Typing :** for normal character keys
- **Space :** for the Space bar
- **Delete :** for the Backspace key

Each sound pack is a folder that contains one sound file for each of these three kinds. The sounds are played in the background, so they do not slow down your typing or delay NVDA's speech.

**Only play typeFX sound for letter keys**  
When this option is on, the typing sound is played only for the letter keys A to Z. The Space bar and the Backspace key still play their own sounds. Numbers and punctuation characters stay silent.

**Sound packs**  
The list of sound packs is built from the folders found in the add-on's effects folder, in alphabetical order. If no folders are found, a built-in list of names is shown instead: `Android`, `Android_(SwiftKey)`, `Blip_(SwiftKey)`, `Huawei`, `Infinix`, `MIUI`, `Modern_(SwiftKey)`, `OnePlus`, `Oppo`, `Perkin`, `Pixel`, `Pixel_New`, `Samsung_Calm`, `Samsung_Fun`, `Samsung_Galaxy`, `Samsung_Retro`, `Surface_(SwiftKey)`, `Traditional_(SwiftKey)`, `Vivo`, `Vivo_new`, `iPhone` and `techno`. The default is `Pixel`.

**Volume**  
The volume can be set from 0% to 100% in steps of 5%, and the default is 50%. At 100% the original sound file is played. At lower values the add-on creates a quieter copy of the sound the first time it is needed and stores it in a cache folder, so later key presses use the ready-made copy. If a quieter copy cannot be created, the original sound is played instead.

---

#### 5. Sound Test Field

The settings panel includes an edit field where you can try your chosen sound pack and volume before you save anything.

- **Step 1:** Choose a sound pack and a volume in the panel.
- **Step 2:** Move to the field named **Type here to test the selected sound**.
- **Step 3:** Type, press Space and press Backspace to hear the typing, space and delete sounds.

While this field has focus, the normal global typing sound is paused, so you hear each sound only once. The test uses the pack and volume currently selected in the panel, even before you press OK or Apply.

---

#### 6. Where It Works

The improved word announcements are active in standard editing areas. These are fields that NVDA identifies as a document, an editable text field or a terminal, as well as these window types: `Edit`, `RichEdit`, `RichEdit20`, `REComboBox20W`, `RICHEDIT50W`, `RichEditD2DPT`, `Scintilla`, `TScintilla`, `AkelEditW`, `AkelEditA`, `_WwG`, `_WwN`, `_WwO`, `SALFRAME` and `ConsoleWindowClass`.

The add-on still follows your NVDA keyboard settings:

- Words are read only if **Speak typed words** is enabled in NVDA.
- Typed characters are read only if **Speak typed characters** is enabled in NVDA.
- Nothing is spoken for words or characters while typing is protected, such as in a password field.
- Read-only fields are not announced as typed text.
- If NVDA's spelling error alert for typing is enabled, the previous word is checked for spelling errors when you finish it.
- The Caps Lock warning beep for lowercase typing works as set in NVDA.

---

#### 7. Saved Settings

Your choices are kept in a file named `settings.json` inside the `ChaiChaimee\AbsoluteType` folder in your NVDA configuration folder.

- When the file is saved, the previous version is kept as a backup copy with the extension `.bak`.
- If the file is missing the first time the add-on starts, any older AbsoluteType settings found in NVDA's own configuration are copied over, and the new file is created.
- If the file cannot be read, the default values are used.

**Default values:** corrected-part announcement on, last typed word announcement on, typeFX on, sound pack Pixel, volume 50%, letters-only off.

---

## Support Me

If this tool has made your life easier, consider fueling the next update with a small donation.

[![Support me](https://img.shields.io/badge/Donate-Support%20Me-blue?style=for-the-badge&logo=stripe)](https://buy.stripe.com/dRm9AU1xQ3Ds22N6VK1VK01)

Your support means the world. Let's build something great together.

---

&copy; 2026 Chai Chaimee NVDA Add-on Released under GNU GPL