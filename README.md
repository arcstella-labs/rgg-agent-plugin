# Retro Game Gather

[日本語の説明はこちら](#日本語)

[Retro Game Gather](https://retrogather.com/) (RGG) is a collection manager for retro games released in Japan. It covers over 20,000 titles, from the Famicom era to discontinued platforms such as PS3, 3DS, Wii U and PS Vita.

This plugin connects Claude to your RGG account and adds six skills, so you can look up games and keep your wishlist, library and play records up to date by talking in your own words, in Japanese or English.

## What you can ask

| Skill                 | Use it to                                                                                             | Example                                          |
| --------------------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| `find-games`          | Identify a game by title, nickname, JAN barcode or model number, and get an introduction with sources | "Look up Chrono Trigger for the Super Famicom"   |
| `collect-games`       | Add games to your wishlist or library, record purchase details, check whether you already own a game  | "I bought Super Mario World today for 1,500 yen" |
| `log-play`            | Record play sessions, clears, pauses and replays                                                      | "I played Chrono Trigger for 2 hours today"      |
| `plan-next-game`      | Choose what to play next from your backlog                                                            | "What should I play tonight? I have an hour"     |
| `review-activity`     | Summarize purchases, spending, play time and clears over a period                                     | "Summarize my library by platform"               |
| `organize-collection` | Manage tags, collection goals, owned consoles and their maintenance logs, and custom entries          | "Make a goal to collect every Mother game"       |

Japanese requests work the same way:

- スーパーファミコン版のクロノ・トリガーを検索して。
- プレイ予定のゲームを一覧にして、次に遊ぶ候補を一緒に選んで。
- 所有ゲームを機種別に集計して、コレクションの傾向を教えて。

Claude replies in the language you write in and quotes official titles in Japanese, as registered in RGG.

## Requirements

- A Retro Game Gather account. See [Sign up and log in](https://docs.retrogather.com/getting-started/signup/) (in Japanese).
- A Claude plan that supports plugins.

Tags, owned consoles, collection goals, multiple copies of one game, custom entries and browsing by platform or genre depend on your RGG plan. When a feature is not available, Claude says so once and carries on.

## Install

**Claude (web and desktop apps)**: open **Customize > Plugins**, find **Retro Game Gather** in the directory and add it. Once added, it is also available in the Claude mobile apps.

**Claude Code**: add this repository as a marketplace, then install the plugin.

```bash
claude plugin marketplace add arcstella-labs/rgg-agent-plugin
claude plugin install retro-game-gather@rgg-agent-plugin
```

## Connect your account

After adding the plugin, connect **Retro Game Gather** from the plugin's Connectors tab. Your browser opens RGG's consent screen, where you sign in and choose what Claude may do.

- Permissions are grouped into game information, library and play records, each with view, edit and delete.
- Delete is off by default. Unless you turn it on, Claude cannot delete anything.
- Permissions cannot be changed in place. To change them, disconnect Claude under **User settings > MCP / API > Connected apps** in RGG and connect again.

If you already use the Retro Game Gather connector, the plugin uses the same connection. Step-by-step instructions (in Japanese) are in [Connect AI tools](https://docs.retrogather.com/guides/connect-ai/).

## What this plugin contains and what it accesses

- **Six skills.** Each is a Markdown file of instructions with reference notes about RGG's terms and data. The plugin has no hooks, commands, agents, scripts or executables, and runs nothing on your computer.
- **One remote MCP server**, `https://game.retrogather.com/mcp`, operated by Arcstella Co., Ltd., which is the same server as the Retro Game Gather connector. You sign in with OAuth. Claude sends tool calls to this server, for example a search term or a record to add, and receives your RGG data within the permissions you granted. The plugin sends nothing to any other service.
- **Changes to your data.** When you ask, Claude adds or updates records in your RGG account, such as wishlist entries, library entries and play logs. Deleting needs the delete permission and a confirmation step.
- **Reference links.** When you ask for an introduction to a game, the `find-games` skill tells Claude to open the reference links RGG returns for that game, such as Wikipedia, fan wikis, the Media Arts Database, the Game Preservation Society, IGDB and PULSE, with Claude's own web tools, and to cite the pages it read. If Claude cannot open them, it says so.
- **Documentation links.** For things only the RGG app can do, the skills point you to pages on [docs.retrogather.com](https://docs.retrogather.com/).

## Limitations

- Coverage is games released in Japan for discontinued platforms. Current-generation consoles are out of scope.
- RGG stores records. It cannot launch, stream or emulate games.

## Privacy, terms and support

- [Privacy policy](https://retrogather.com/privacy/) (Japanese)
- [Terms of service](https://retrogather.com/terms/) (Japanese)
- [Support](https://docs.retrogather.com/features/support/)
- [Documentation](https://docs.retrogather.com/), including [what to ask AI tools](https://docs.retrogather.com/guides/ai-examples/)

RGG data that Claude receives is handled under Anthropic's terms for the Claude product you use.

This repository is generated from Arcstella's source for the plugin. Please send questions and feedback through the support page rather than pull requests.

## License

The files in this repository are released under the [MIT License](LICENSE). The license does not cover the Retro Game Gather service, which you use under its terms of service, or the Retro Game Gather name and logo.

---

## 日本語

[Retro Game Gather](https://retrogather.com/)（RGG）は、日本で発売されたレトロゲームのコレクションを管理するサービスです。ファミコンから PS3・3DS・Wii U・PS Vita まで、2 万本以上のタイトルを対象にしています。

このプラグインは、Claude と RGG のアカウントを連携し、6 本のスキルを追加します。会話の中で、ゲームを調べたり、ウィッシュリスト・マイライブラリ・プレイ記録を更新したりできます。

### 頼めること

| スキル                | できること                                                                         | 依頼の例                                         |
| --------------------- | ---------------------------------------------------------------------------------- | ------------------------------------------------ |
| `find-games`          | タイトル・通称・JAN コード・型番からゲームを特定し、出典付きで紹介する             | スーパーファミコン版のクロノ・トリガーを検索して |
| `collect-games`       | ウィッシュリストやマイライブラリへ追加し、購入の情報を記録する                     | 今日スーパーマリオ ワールドを 1,500 円で買った   |
| `log-play`            | プレイログ、クリア、一時停止、もう一周を記録する                                   | 今日クロノ・トリガーを 2 時間遊んだ              |
| `plan-next-game`      | プレイ予定のゲームから、次に遊ぶ候補を選ぶ                                         | 今夜 1 時間で遊べるゲームを選んで                |
| `review-activity`     | 購入金額・プレイ時間・クリア本数を期間で振り返る                                   | 所有ゲームを機種別に集計して                     |
| `organize-collection` | ゲームタグ、マイコレクション、ゲーム機とメンテナンス記録、カスタムデータを管理する | MOTHER シリーズを集めるコレクションを作って      |

### 必要なもの

- Retro Game Gather のアカウント（[アカウント登録とログイン](https://docs.retrogather.com/getting-started/signup/)）
- プラグインを使える Claude のプラン

ゲームタグ、ゲーム機、マイコレクション、所有ソフト、カスタムデータ、機種やジャンルでの絞り込みは、RGG のプランによって使える範囲が変わります。

### 追加する

- **Claude（Web・デスクトップアプリ）**: 「カスタマイズ」→「プラグイン」を開き、一覧から Retro Game Gather を追加します。追加したプラグインはモバイルアプリでも使えます
- **Claude Code**: 上の Install のコマンドで、このリポジトリをマーケットプレイスとして追加します

手順の詳細は「[AIツールと連携する](https://docs.retrogather.com/guides/connect-ai/)」を参照してください。

### 連携と許可

プラグインを追加したら、プラグインの「コネクタ」タブから Retro Game Gather を連携します。ブラウザで RGG の許可画面が開くので、ログインして許可する内容を選びます。

- 許可は「ゲーム情報」「ライブラリ」「プレイ記録」の区分と、「閲覧」「編集」「削除」の操作で選びます
- 削除は初期状態でオフです。オンにしない限り、Claude から削除の操作はできません
- 許可した内容はあとから変更できません。変えるときは、RGG の「ユーザー設定」→「MCP / API」→「連携中のアプリ」で解除し、連携し直します

### プラグインの中身と通信先

- **スキル 6 本**: 手順と参照資料を書いた Markdown です。フック・コマンド・スクリプト・実行ファイルは含まず、利用者のパソコンでは何も実行しません
- **リモート MCP サーバー 1 つ**: `https://game.retrogather.com/mcp`（運営: Arcstella株式会社。Retro Game Gather のコネクタと同じサーバー）。OAuth でログインします。Claude はこのサーバーへ検索語や登録内容を送り、許可した範囲の RGG のデータを受け取ります。ほかのサービスへは何も送りません
- **データの変更**: 依頼に応じて、ウィッシュリスト・マイライブラリ・プレイログなどを追加・更新します。削除には、削除の許可と確認の手順が要ります
- **参照先のリンク**: ゲームの紹介を頼むと、`find-games` は RGG が返した参照先（Wikipedia、ファン Wiki、メディア芸術データベース、ゲーム保存協会、IGDB、PULSE など）を Claude の Web 閲覧機能で開き、読んだページを出典として示します

### できないこと

- 対象は、日本で発売された生産終了機種のゲームです。現行機種は対象外です
- RGG は記録のためのサービスです。ゲームの起動・配信・エミュレーションはできません

### 規約とサポート

- [個人情報保護方針](https://retrogather.com/privacy/)
- [利用規約](https://retrogather.com/terms/)
- [サポート](https://docs.retrogather.com/features/support/)
- [ドキュメント](https://docs.retrogather.com/)

このリポジトリのファイルは [MIT License](LICENSE) で公開しています。Retro Game Gather のサービス（利用規約に従います）と、名称・ロゴは対象外です。
