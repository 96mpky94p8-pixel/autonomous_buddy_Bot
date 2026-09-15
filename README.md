# 🤖 Autonomous Buddy Bot（自律型Discordおしゃべり相棒Bot）

「話しかけたら答える」だけの受動的なBotから、**「自分から話しかけてくれる自律的な相棒」**へ。

一定間隔でタイマーを回し、気まぐれな確率判定を行いながら、自発的に日常の呟きやお誘いメッセージを投稿してくれるDiscord Botのベースコードです。

---

## ✨ 主な特徴

- **自律おしゃべり機能**：ユーザーからの呼びかけがなくても、定期的に自発的なメッセージを投稿します。
- **気まぐれ度（確率）の調整**：毎回決まった時間に喋る「時報bot」にならず、ふと思い立ったように呟くランダム性を実装。
- **LLM連携に対応**：プロンプトを差し替えるだけで、お好みのAIモデル（Google Gemini / OpenAIなど）の人格を持たせることができます。

---

## 🛠 必要な環境・ライブラリ

- Python 3.10 以上
- `discord.py`

### ライブラリのインストール
```bash
pip install -U discord.py
🚀 セットアップ手順
**1. Discord Developer Portal での設定**

1. Discord Developer Portal にアクセスし、Botを作成します。

2. Bot タブの「Privileged Gateway Intents」にある MESSAGE CONTENT INTENT を ON にします。

3. Reset Token を押して、Botのトークンをコピーします。

**2. コードの設定**
⁠autonomous_buddy.py⁠ を開き、以下の2箇所をご自身の環境に合わせて書き換えます。

 1. あなたのBotトークンを貼り付け
DISCORD_BOT_TOKEN = "ここにコピーしたトークン"

 2. メッセージを送信したいDiscordチャンネルのID（数字）
TALK_CHANNEL_ID = 123456789012345678
(※チャンネルIDは、Discordの開発者モードをONにしてチャンネル名を右クリック「チャンネルIDをコピー」で取得できます)

**3. Botの起動**
ターミナルまたはコマンドプロンプトで以下を実行します。
python autonomous_buddy.py
コンソールに ⁠ログイン完了しました⁠ と表示されれば準備完了です！

⚙️ カスタマイズ
おしゃべりAIの人格やセリフを変えたい
⁠generate_buddy_message()⁠ 内のシステムプロンプトやサンプルセリフを書き換えることで、自分好みの相棒に育てることができます。

⁠autonomous_buddy.py⁠ の以下の数値を調整してください。

# チェックの間隔（分単位）
@tasks.loop(minutes=30)

# おしゃべりする確率（0.4 = 40%の確率で喋る、0.6にするともっとおしゃべりに！）
if random.random() > 0.4:
    return

 📝 開発者メモ・今後の展望
 会話の文脈に合わせた自律スタンプ送信機能
 思考監査モニター・キルスイッチ判定機能の実装
