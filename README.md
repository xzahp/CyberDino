[English](README.md) | [简体中文](READMEzh-cn.md)

# CyberDino 🦖

**CyberDino** is a shooting mini-game built with Scratch 3.0, paired with its own online leaderboard website. Shoot dino clones with oranges, dodge left and right, climb the ranks — and play it all offline with zero extensions, or online with a full account system and leaderboard.

> 🎯 **Which file to use?** On **official Scratch 3.29.1 → use V3.2**. Want the online leaderboard → use V3.0 with TurboWarp.

## ✨ Features

- 🦖 **Classic arcade shooting** — move up/down, fire oranges at incoming dinosaurs, gain difficulty every 5 kills, 1-second invincibility frames after a hit.
- 🖥️ **Four complete screens** — start page, gameplay, result page, and leaderboard page, each with its own backdrop.
- 📱 **Touch controls** — on-screen ▲ / ▼ / FIRE buttons for phones; keyboard (Space / ↑ / ↓) for desktop.
- 🌐 **Online leaderboard** — automatic online/offline detection; submit scores, view rankings, register and log in.
- 🛡️ **Anti-cheat basics** — score cap, name length limit, per-IP submission cooldown, account-bound scores.
- 🔧 **Fully reproducible** — every version ships with Python build + verification scripts and real-device test evidence.
- 🧩 **Zero-extension offline build** — V3.2 runs directly in official Scratch 3 with no extensions, sounds, or font declarations.
- 🆓 **Free & open source** — MIT licensed, no ads, no trackers.

## 🎮 How to Play

**Official Scratch 3 (recommended):** Open `V3.2/CyberDino-V3.2-官方Scratch兼容版.sb3` and click the green flag. No sign-up, no internet needed. Wait 5–10 seconds for the blue loading overlay to disappear. (The text underneath — "Loading sounds / Loading sprites / Creating blocks" — is just a rotating animation caption, ignore it.)

**Online leaderboard:** Register and log in on the site, then click "Play Online"; or open `V3.0/CyberDino-V3.0.sb3` in TurboWarp.

**Controls:**
- Desktop: `Space` to fire, `↑` / `↓` to dodge.
- Mobile: hold the on-screen ▲ / ▼ / FIRE buttons.
- Rename: use "✎ Rename" at the top-right of the start page; otherwise the default name is used.

Defeat 20 dinosaurs to win. Every 5 kills makes them faster. You have 3 lives, with 1 second of invincibility after a hit.

## 🛠️ How to Run (Website)

The leaderboard website lives in `网站源码/` (a native PHP + MySQL backend).

1. Create a MySQL database and a `rankings` table (see `文档/网站部署说明.md`).
2. Copy the example config and fill in your own values — never commit real credentials:

   ```bash
   cp .env.example .env
   # Edit .env with your DB / FTP / token values, then write them into
   # 网站源码/cyberdino_config.php (place this file OUTSIDE the web root).
   ```

3. Upload `网站源码/wwwroot/` to your web root (e.g. `wwwroot` / `htdocs`).
4. Run the one-time installer, then **delete `install.php` / `_clean.php` immediately** and change the default admin password.
5. Open your domain in a browser and verify `/api/rank.php?action=ping` returns `PONG`.

> ⚠️ The leaderboard API serves both plain text (for Scratch, e.g. `1|name|23;`) and JSON (add `format=json`). Keep the plain-text format if you modify the API.

## 📁 Project Structure

```
CyberDino/
├─ README.md                  ← this file (English)
├─ READMEzh-cn.md             ← 中文版
├─ LICENSE                    ← MIT
├─ .env.example               ← configuration template (no real secrets)
├─ V1.0/ ... V3.2/            ← 5 independent game builds + source & evidence
│   └─ 源码与验证证据/          ← build.py / verify.py / screenshots / test data
├─ 网站源码/                   ← leaderboard site source (PHP)
│   ├─ wwwroot/               ← site root to upload
│   ├─ cyberdino_config.php   ← DB config (keep outside web root)
│   ├─ deploy.py              ← FTP upload helper
│   └─ install.php            ← one-time installer (delete after use)
└─ 文档/                       ← deployment guide, troubleshooting, admin manual
```

Each version folder is self-contained — if one build breaks, an older one still works.

## 📜 Version History

| Version | Date | Highlights |
|---|---|---|
| **V1.0** | 2026-11-11 | Minimal playable prototype (111 blocks, ~5 KB): cat movement, space to fire, dinosaur spawning, hit scoring, damage on collision, win/lose announcements. |
| **V2.0** | 2026-11-11 | Progressive difficulty (+0.6 speed, −0.15s spawn every 5 kills), 1-second invincibility, hit spark effects, 2 sound effects, intro hints, completion timer (189 blocks, ~12 KB). |
| **V3.0** | 2026-11-11 (fixed 2026-11-12) | Redrawn cat, four screens, online leaderboard, 4 sound effects, mobile touch controls, optional rename, online/offline auto-detection (636–675 blocks, ~36 KB). Network extension format, CORS, nginx cache, and play-link issues all fixed. |
| **V3.1** | 2026-11-12 | Zero-extension offline build for official Scratch 3 (648 blocks, ~35 KB). Later found to hang on the loading overlay in old official Scratch 3 due to SVG font declarations — kept for TurboWarp. |
| **V3.2** | 2026-11-13 | **Recommended.** Zero extensions + zero sounds + SVG without font declarations — opens directly in official Scratch 3.29.1 (636 blocks, ~20 KB). A sound-enabled variant (~93 KB, 44.1 kHz) is included for TurboWarp / newer Scratch. |

## 📜 License

Released under the [MIT License](LICENSE). You may freely use, modify, and distribute it, including for commercial purposes, provided you keep the original copyright notice.

## ❤️ Credits

- Built with Scratch 3.0 and Python (standard library only).
- Thanks to WorkBuddy and everyone who beta-tested and gave feedback.
- Made for creators — no scams, no fakes, no violations.

[English](README.md) | [简体中文](READMEzh-cn.md)
