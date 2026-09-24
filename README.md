# 🤖 Emoji Steganography Tool (WhatsApp & Web Compatible)

A lightweight, fully client-side web application that lets you inject hidden text (prompts, notes, code, multi-language text) into emojis using **WhatsApp-safe Zero-Width Unicode Characters**, and decode them back to their original form.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![Zero Dependencies](https://img.shields.io/badge/Dependencies-None-brightgreen)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## ✨ Features

- **WhatsApp & Messenger Compatible**: Uses Zero-Width Joiners (ZWJ) and Non-Joiners (ZWNJ) that are not stripped by WhatsApp or modern chat sanitizers.
- **Big-Emoji Prevention**: Wraps emojis with a discrete carrier format (`[🤖]`) to prevent chat platforms from converting single emojis into stripped image stickers.
- **Bidirectional Tool**: Seamlessly switch between the **Encoder** (Inject Data) and **Decoder** (Extract Data).
- **Full UTF-8 Support**: Encodes and decodes multi-language text (English, Urdu, Arabic, etc.), special characters, programming code, and multiline prompts without data loss.
- **Backward Compatibility**: Automatically detects and decodes legacy zero-width payloads (`\u200B`) as well as WhatsApp-safe payloads.
- **Inbuilt Emoji Palette**: Pre-configured collection of emojis for quick carrier selection, along with support for custom emojis.
- **100% Client-Side & Private**: All encoding and decoding happen directly in your browser using native Web APIs (`TextEncoder` / `TextDecoder`). No data is sent to any external server.
- **One-Click Testing**: Instant "Send to Decoder" action to verify hidden content immediately.
- **Zero Dependencies**: Plain HTML5, CSS3, and modern JavaScript—no build steps or npm packages required.

---

## 🛠️ How It Works (Technical Overview)

Traditional zero-width steganography often uses `\u200B` (Zero-Width Space), which chat apps like WhatsApp actively strip to prevent spam and chat crashes. This tool solves that by using **Unicode characters essential to script rendering and emoji sequences**:

1. **Text to Bytes**: The input string is converted into a UTF-8 byte stream using the standard browser `TextEncoder`.
2. **Bytes to Binary**: Each byte is broken down into 8 individual bits (`0` or `1`).
3. **WhatsApp-Safe Invisible Mapping**:
   - `0` is mapped to **Zero-Width Joiner (ZWJ)** (`\u200D`) — preserved by apps for composite emoji combinations.
   - `1` is mapped to **Zero-Width Non-Joiner (ZWNJ)** (`\u200C`) — preserved by apps for proper Perso-Arabic and Indic typography.
4. **Injection & Enveloping**: The sequence of invisible characters is attached to the carrier emoji inside brackets (e.g. `[🤖]`), preventing the message from rendering as an isolated sticker.
5. **Extraction**: The decoder extracts the bitstream, identifies the character set, reconstructs the original byte array, and decodes the UTF-8 text using `TextDecoder`.

---

## ⚠️ Platform Compatibility & AI Disclaimer

| Platform / Channel | Status | Note |
| :--- | :---: | :--- |
| **WhatsApp Web / Desktop** | ✅ Works | Reliably copies and sends zero-width characters |
| **WhatsApp Mobile** | ✅ Works | Copy via standard message selection or bubble copy |
| **Telegram / Discord** | ✅ Works | Preserves Unicode characters completely |
| **Email / Plain Text** | ✅ Works | 100% compatible |
| **AI Chatbots (ChatGPT / Claude / Gemini)** | ⚠️ Manual Only | AI tokenizers clean or ignore raw zero-width sequences; they cannot auto-decode binary steganography without a decoding script |

---

## 🚀 Getting Started

### Option 1: Run Locally
1. Clone this repository:
   ```bash
   git clone [https://github.com/mrabr381/Emoji-Steganography-Tool.git](https://github.com/mrabr381/Emoji-Steganography-Tool.git)
   cd Emoji-Steganography-Tool
