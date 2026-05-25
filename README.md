# Gemini Usage Bar 📊

A premium Chrome extension that embeds a real-time, theme-adaptive usage limits indicator directly into the Google Gemini chat interface. It tracks your remaining limits and automatically refreshes after every prompt completion.

![Gemini Usage Bar Icon](icon.png)

## Features

- 🔄 **Real-Time Updates**: Automatically refreshes your remaining limit percentage the exact moment Gemini finishes generating a response.
- 🎨 **Premium Aesthetics**: Designed with a sleek, glassmorphic layout that synchronizes natively with Gemini's active light or dark themes.
- 📈 **Detailed Dropdown**: Click the pill to expand detailed status bars showing both your **Current Limit** and **Weekly Limit** along with their exact reset times.
- ⚡ **Manual Refresh**: Includes an interactive refresh button inside the dropdown header with custom spin loading animations.
- ⌨️ **Keyboard Shortcut & Toggle**: Press `Alt + U` (or `Option + U` on Mac) to hide or show the indicator. When hidden, an unobtrusive floating eye button appears in the bottom-right corner for quick recovery.
- ↔️ **Dynamic Sidebar Alignment**: Robustly tracks Gemini's sidebar. The pill container automatically and smoothly slides to the right when the sidebar is opened to prevent overlapping any logo or navigation text.
- 🔑 **Auth Detection**: Automatically detects if you are logged out and displays a user-friendly sign-in warning with a direct redirect link.

---

## How It Works under the Hood

1. **CSP & X-Frame-Options Bypass**: Uses Chrome's `declarativeNetRequest` API to dynamically strip restrictive framing headers (`Content-Security-Policy` and `X-Frame-Options`) on requests to `gemini.google.com/usage`.
2. **Dual-Strategy Scraper**:
   - **Strategy 1**: First attempts a high-speed background AJAX `fetch()` request to parse page content.
   - **Strategy 2**: If the page requires dynamic client-side rendering, it falls back to loading the page in a hidden same-origin iframe and polls the `iframe.contentDocument` directly.
3. **Response State Observer**: Utilizes a `MutationObserver` on the document body to monitor Gemini's send/stop buttons and generation indicators. It captures the transition from "active generation" back to "idle" and immediately triggers a refresh.

---

## Installation

Since this extension is in developer mode, you can load it directly into Google Chrome:

1. Clone or download this repository.
2. Open Google Chrome and navigate to `chrome://extensions/`.
3. Enable **Developer mode** using the toggle switch in the top-right corner.
4. Click the **Load unpacked** button in the top-left corner.
5. Select the folder containing these files.
6. Open [Google Gemini](https://gemini.google.com/) and enjoy!

## Keyboard Shortcuts

- **Toggle Visibility**: `Alt + U` (or `Option + U` on macOS).

## License

This project is licensed under the MIT License - see the LICENSE file for details.
