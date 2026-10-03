# soroban-site

Soroban Sensei (日本語は「そろばんの道」。2026-10-03 に Soroban Friends から改名) の公開ページ。App Store Connect の「プライバシーポリシー URL」と「サポート URL」に入れるもの。
アプリの `Legal.swift` (privacyPolicyURL / supportURL) も同じ場所を指す。

| ページ | 役割 |
|---|---|
| `index.html` | アプリの紹介 (マーケティング URL に使える) |
| `privacy.html` | プライバシーポリシー。アプリの中の説明 (`PrivacyView.swift`) と食い違わせない |
| `support.html` | サポート・よくある質問・問い合わせ先 |
| `ja/index.html` `ja/privacy.html` `ja/support.html` | 上の 3 ページの日本語版 (端末の言語が日本語のとき、アプリは `ja/` を開く。ストアの日本語の欄の URL も `ja/`)。どのページにも、もう一方の言語へのリンクがある |
| `img/ja/shot-*.jpg` | 日本語の紹介ページのスクリーンショット (396×860。`store/ja/screenshots/iphone-6.9/` の 01・02・03・04・08 を縮めたもの) |

規約は Apple 標準の EULA を使うので、ここには置かない。

## 公開のしかた (まだ公開していない)

```sh
gh repo create hirokishingu/soroban-site --public --source . --push
gh api -X POST repos/hirokishingu/soroban-site/pages -f 'source[branch]=main' -f 'source[path]=/'
```

数分後に https://hirokishingu.github.io/soroban-site/privacy.html が開く。
アプリ側の `scripts/release-check.sh` が、2 つの URL が 200 を返すことを確かめる。

## 店名を変えたとき

`Soroban Sensei` の表記を全ページで置き換える (`grep -rn "Soroban Sensei" .`)。日本語は `そろばんの道` (`grep -rn "そろばんの道" ja`)。
support.html の「購読の解約」の説明にも、App Store に出る名前が入っている (日本語版にも)。

## 確認のしかた

`open index.html` で見られる。文言を足したら、アプリ内の `PrivacyView.swift` と日付をそろえる。
