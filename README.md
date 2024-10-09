# 不動産スクレーパーおよび自動投稿システム

**不動産スクレーパーおよび自動投稿システム**のリポジトリへようこそ！このリポジトリには、SUUMOから物件データをスクレイピングし、収集した情報を不動産ポータルサイトに自動投稿するためのツールが含まれています。このツールはデータ収集、リスティング管理、ポータル投稿を自動化し、不動産業界のプロフェッショナルが時間を節約し、精度を向上させるための不可欠なソリューションです。

## 🚀 特徴

- **SUUMOデータスクレイピング**: 指定された検索エリアからSUUMOの詳細な物件情報を自動的に収集（建物の詳細、家賃、特徴、URLなど）。
- **自動物件投稿**: スクレイピングしたデータを使用して、不動産広場などの不動産ポータルに新しいリスティングを自動で投稿。
- **カスタムキャッチコピー生成**: OpenAIのGPT技術を使用して、各物件に魅力的なタイトルやハイライトを生成し、顧客を引き付けます。
- **CSV管理**: 物件データをCSVファイルに保存し、組み込みの関数で簡単に更新・修正が可能。
- **シームレスな統合**: OpenAIのAPIと接続し、Seleniumを使ったブラウザ自動化によりスムーズな物件投稿体験を提供。

## 📋 必要条件

このプロジェクトはGoogle Colab上で実行され、以下のパッケージが必要です：

- Selenium
- BeautifulSoup (bs4)
- Requests
- Pandas
- Numpy
- OpenAI API

## 📥 インストール

まず、このリポジトリをクローンし、次のコマンドを実行して必要な依存関係をインストールします：

```python
from google.colab import drive
!pip install selenium retry numpy pandas requests bs4 urllib3 openai
```

Seleniumを正常に動作させるために`chromium-chromedriver`もインストールしてください：

```sh
!apt-get update
!apt-get install -y chromium-chromedriver
```

## ⚙️ セットアップと使い方

1. **Google Driveのマウント**: CSVファイルをGoogle Driveに保存し、直接アクセスします。Google colabやJupyter Notebookでの実行時はheadlessモードで設定する必要があります。

   ```python
   from google.colab import drive
   drive.mount('/content/drive')

   def web_driver():
    options = webdriver.ChromeOptions()
    options.add_argument('--headless')
    options.add_argument('--no-sandbox')
    options.add_argument('--disable-dev-shm-usage')
    driver = webdriver.Chrome(options=options)
    return driver

   driver = web_driver()
   ```

2. SUUMOデータ収集: 対象エリアとスクレイピングするページ数を設定し、データの収集を開始します。このとき、情報を抽出するページ数と、suumoでの指定エリアの検索結果画面URLを指定してください：

   ```
   max_page = 10  # スクレイピングするページ数

   url = '[https://suumo.jp/](https://suumo.jp/)...'
   ```

3. **物件情報の投稿**: 対象ポータルにログインし、物件情報を簡単に投稿します。ツールがCSVデータをもとに自動でフォームを埋めます。

## 📊 **CSV出力と管理**

スクレイピング後、物件の詳細はCSVファイルとして保存され、さらに処理を行ったりポータルに一括投稿するために使用できます。GPTを使ってプロモーション用の説明を追加することも可能です。

```
df.to_csv(csv_file_path, index=False, encoding='utf-8-sig')
```

## 🤖 OpenAI統合

魅力的なキャッチコピーや物件のハイライトを生成します：

```python
response = openai.chat.completions.create(...)
```

この機能により、リスティングが目立つようなユニークで魅力的な物件説明を自動生成します。

## 🔄 不動産情報入稿自動化フロー

1. **不動産ポータルにログイン**: 認証情報を入力してログインします。
2. **新規物件登録をクリック**: 新しいリスティングの作成に自動でナビゲート。
3. **物件情報の入力**: CSVデータを使用して物件の特徴を自動入力。
4. **仮登録を送信**: 仮登録をクリックし、送信を確認します。

## 🔐 認証情報の管理

ポータルのログイン認証情報やAPIキーなどの機密情報は、安全に管理する必要があります。環境変数やセキュアなクラウドストレージソリューションを利用してこのデータを保護してください。

## 🛠 今後の改善

- **対応ポータルの拡充**: その他の不動産リスティングサイトへの対応を拡大。
- **エラーハンドリングの改善**: 再試行メカニズムを強化し、堅牢性を向上。
- **分析ダッシュボード**: スクレイピングしたデータを可視化し、物件管理に関する意思決定を支援。

## 💡 貢献

貢献は歓迎します！機能や改善点についてアイデアがあれば、リポジトリをフォークしてプルリクエストを送信してください。

## 📧 連絡先

質問や提案がある場合は、\*\*[email@example.com](mailto\:email@example.com)\*\*までご連絡ください。
