# Voice Calculator

<p>
  <img alt="voice" src="https://img.shields.io/badge/voice-Web%20Speech%20API-ffd43b?labelColor=30363d">
  <img alt="single file" src="https://img.shields.io/badge/page-single-2ea043?labelColor=30363d">
  <img alt="mobile layout" src="https://img.shields.io/badge/layout-fixed%20mobile-1f6feb?labelColor=30363d">
  <br>
  <img alt="no dependencies" src="https://img.shields.io/badge/dependencies-none-3fb950?labelColor=30363d">
  <img alt="no account" src="https://img.shields.io/badge/account-none-3fb950?labelColor=30363d">
  <img alt="MIT license" src="https://img.shields.io/badge/license-MIT-2ea043?labelColor=30363d">
  <img alt="free" src="https://img.shields.io/badge/price-free-2ea043?labelColor=30363d">
</p>

**You talk, it calculates.** A phone-shaped calculator with one screen and no menu: say the sum out loud, the result appears, then everything clears for the next one. The whole project is a single HTML file.

<h3 align="center">
  <a href="https://moonspiid.github.io/voice-calculator/" target="_blank" rel="noopener noreferrer">⬆ View the file</a>
</h3>

<p align="center">
  No account, no server, no build, no dependency — one <code>index.html</code> file, open it and talk.
  <br>
  Nothing leaves the browser: no data sent, no key, no request to a server of ours.
</p>

## Contents

- [Why](#why)
- [Features](#features)
- [Quick start](#quick-start)
- [How it works](#how-it-works)
- [Good to know](#good-to-know)
- [Support this project](#support-this-project)
- [License](#license)

## Why

Typing a sum on a phone keyboard takes time, and both hands. A calculator that listens skips the detour: you say "two plus three times four", you keep doing what you were doing, the result is there. No app to install, no account, no menus — just a calculator screen and one big button.

## Features

- **Fixed mobile calculator layout** — one screen, no menu, the display on top and a 4×5 keypad below; full screen on a phone, centred like a device on a computer.
- **Standard touch keypad** — `AC`, `⌫`, `%`, `±`, `÷ × − +`, decimal point, `=`, with visual feedback on every press and sizes that stay readable from a small phone to a desktop.
- **One big command button** under the keypad — it pulses red while listening and shows the recognised sentence live.
- **Speech becomes an equation** — numbers spelled out (up to millions), `point` for decimals, `plus`, `minus`, `times`, `multiplied by`, `divided by`, `over`, `percent`; "two plus three times four" becomes `2+3*4` = `14`, with operator precedence respected.
- **Result, then reset** — the equation is shown above the result, then the calculator clears itself after 2.8 s for the next sum.
- **Guarded evaluation** — only digits and allowed operators are evaluated (`0-9 + - * / % ( ) .`), the value is rounded to 10 decimals, and an incomplete sum never shows a wrong result.
- **Built for spoken French** — recognition runs on `fr-FR`, with numbers and operators understood the way people actually say them (`dix-sept`, `quatre-vingt-dix`, `deux virgule cinq`).

## Quick start

1. Open [moonspiid.github.io/voice-calculator](https://moonspiid.github.io/voice-calculator/) — that is the whole app, already served over HTTPS.
2. Press the big button, allow the microphone, and say for example **"douze divisé par quatre"**.
3. The equation and the result appear, then the calculator resets by itself.

To run it locally instead, download `index.html` — the whole project — and serve it from `localhost` (the microphone is blocked on `file://`): `python3 -m http.server 8000`, then open `http://localhost:8000`.

## How it works

- `index.html` — the stylesheet, the keypad, the voice button and the logic, all in one file.
- Recognition goes through `SpeechRecognition` / `webkitSpeechRecognition` on `fr-FR`, with interim results shown while you speak.
- `speechToEquation()` cleans the sentence (accents, hyphens in "dix-sept", "virgule"), swaps the operator words, turns spelled-out numbers into digits, then keeps only mathematical characters.
- `safeEval()` evaluates the resulting expression and rounds to 10 decimals; an empty or malformed expression shows nothing.
- `resetAll()` clears the equation, the transcript and the result for the next sum.

## Good to know

- **HTTPS or localhost is required** for the microphone — that is a browser rule. Opened straight from `file://`, the button shows a message instead.
- **Chrome, Edge and recent Safari** support the Web Speech API. Firefox does not: the button then explains that you need another browser.
- Recognition is set to French (`fr-FR`); spelled-out numbers are understood up to millions, and "deux virgule cinq" is accepted.
- Nothing is stored: the sum lives in memory only while it is on screen, then it is gone.

## Support this project

The app is free, has no account, no ads and no tracking, and there is no paid tier to upsell. If it saves you time, a donation pays for the hours behind it and the next features.

**Donate in USDT →** one crypto address, no card, no account, no payment processor in between.

<p align="center">
  <img src="https://raw.githubusercontent.com/moonspiid/ai-agent-multi-model/master/donate-usdt-qr.png" alt="QR code of the EVM donation address" width="200">
  <br>
  <sub>Scan with any wallet app</sub>
</p>

```
0xA2700896E16BE762467D458F2B45260f8FAC9F3E
```

This is a plain EVM address, so **the same address works on every EVM network**. Send USDT on whichever one suits you:

| Network | Token |
| --- | --- |
| BNB Smart Chain (BEP20) | USDT |
| Ethereum (ERC20) | USDT |
| Polygon | USDT |
| Arbitrum One | USDT |
| Base | USDT |
| Optimism | USDT |

Two rules: send **USDT only** (another token sent to this address cannot be recovered), and keep a little of the network's own coin (BNB, ETH, POL) in your wallet to pay the transfer fee. A non-EVM network such as Tron (TRC20) uses a different address format, so nothing sent there reaches this one.

## License

[MIT](LICENSE) © 2026 moonspiid — use it, modify it, ship it.
