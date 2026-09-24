# 🤖 Emoji Steganography Tool

A lightweight, fully client-side web application that lets you inject hidden text (prompts, notes, code, multi-language text) into emojis using **Zero-Width Unicode Characters**, and decode them back to their original form.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![Zero Dependencies](https://img.shields.io/badge/Dependencies-None-brightgreen)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## ✨ Features

- **Bidirectional Tool**: Seamlessly switch between the **Encoder** (Inject Data) and **Decoder** (Extract Data).
- **Full UTF-8 Support**: Encodes and decodes multi-language text (English, Urdu, Arabic, etc.), special characters, programming code, and multiline prompts without data loss.
- **Inbuilt Emoji Palette**: Pre-configured collection of emojis for quick carrier selection, along with support for custom emojis.
- **100% Client-Side & Private**: All encoding and decoding happen directly in the browser using the native Web APIs (`TextEncoder` / `TextDecoder`). No data is sent to external servers.
- **One-Click Testing**: Instant "Send to Decoder" action to verify hidden content immediately.
- **Zero Dependencies**: Plain HTML5, CSS3, and modern JavaScript—no build steps or npm packages required.

---

## 🛠️ How It Works

Under the hood, the tool utilizes **Unicode Zero-Width Characters** that are completely invisible to the human eye when rendered on a screen:

1. **Text to Bytes**: The input string is converted into a UTF-8 byte stream using the standard browser `TextEncoder`.
2. **Bytes to Binary**: Each byte is broken down into 8 individual bits (`0` or `1`).
3. **Binary to Invisible Characters**:
   - `0` is mapped to **Zero-Width Space** (`\u200B`).
   - `1` is mapped to **Zero-Width Non-Joiner** (`\u200C`).
4. **Injection**: The sequence of invisible characters is appended directly to the chosen carrier emoji.
5. **Extraction**: The decoder filters out everything except the specific zero-width characters, reconstructs the bitstream into bytes, and decodes the UTF-8 text using `TextDecoder`.

---

## ⚠️ Important Note on AI Tools & Text Normalization

While the carrier emoji visually appears as an ordinary emoji to humans, please note:
- **LLM Tokenization**: Most Large Language Models (e.g., ChatGPT, Claude, Gemini) and web chat interfaces strip, clean, or tokenize invisible/zero-width characters as raw tokens rather than automatically decoding binary steganography.
- **Communication Use-Case**: This tool is designed for human-to-human text hiding or software-to-software decoding pipelines where both sides have a decoder implementation.

---

## 🚀 Getting Started

### Option 1: Run Locally
1. Clone this repository:
   ```bash
   git clone [https://github.com/mrabr381/Emoji-Steganography-Tool.git](https://github.com/mrabr381/Emoji-Steganography-Tool.git)
   cd Emoji-Steganography-Tool
