# Cockroach Run: ads

This public repo is the game's "backend". It has no server, just files:

| File | What it is |
| --- | --- |
| `config.json` | The live ad settings. The game reads this file every minute, so changes show up in players' games within a minute or two. |
| `index.html` | The **admin panel**. Open it on GitHub Pages: <https://nokabir.github.io/cockroach-run-ads/> |
| `privacy.html` | The privacy policy to link from the Play Store listing: <https://nokabir.github.io/cockroach-run-ads/privacy.html> |

Don't edit `config.json` by hand; use the admin panel.

## Using the admin panel

1. Make a GitHub token: [new fine-grained token](https://github.com/settings/personal-access-tokens/new).
   Under **Repository access**, choose **Only select repositories** and pick this repo.
   Under **Permissions → Repository permissions**, set **Contents** to **Read and write**.
2. Open the admin panel, paste the token and press **Connect and load**.
3. Add SVG ads to the spots, fill in your AdMob IDs, then press **Publish to the game**.

### Ad spots

| Spot | Shape (width : height) | Suggested viewBox |
| --- | --- | --- |
| Cockroach back | 1 : 1 sticker | `0 0 400 400` |
| Police backs | 0.85 : 1 patch | `0 0 340 400` |
| Barricades | 4 : 1 strip | `0 0 800 200` |
| Road banners | 6 : 1 banner | `0 0 1200 200` |
| Street billboards | 2 : 1 board | `0 0 800 400` |

SVGs are drawn as images, so scripts and links in them never run, and files they link to on the internet don't load. Embed any pictures inside the SVG, and keep each one under 300 KB.

## AdMob

- Until your app is live, keep **Google's test IDs** (the admin panel has a button for them). Never tap your own real ads.
- The **ad unit IDs** (banner, interstitial, rewarded) change in the game within a minute.
- The **App ID** is built into the Android app. After changing it, rebuild the app in the game repo: Actions → *Android app* → *Run workflow*.
- **app-ads.txt:** AdMob wants this file at the root of the website on your Play Store listing. The admin panel shows its one line. To host it on GitHub, create a public repo named `nokabir.github.io` and put `app-ads.txt` in it; your website is then `https://nokabir.github.io`.
