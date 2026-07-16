# forge_neo-prompt-reformatter

Stable Diffusion WebUI Forge のグリッド画像メタデータから `Template` と `Negative Template` を抽出し、改行を復元して整形するブラウザツールです。

sd-dynamic-prompts 等でワイルドカードが置換される前の元テンプレートを取り出したいときに使います。

## 機能

- メタデータ文字列から **Template**（プロンプト）と **Negative Template**（ネガティブプロンプト）を自動抽出
- エスケープされた改行（`\n`）や引用符（`\"`）をデコードして読みやすい形式に復元
- 入力と同時に変換（貼り付けた瞬間から結果を表示）
- 抽出結果をワンクリックでクリップボードにコピー

## 使い方

1. https://keiarues.github.io/forge_neo-prompt-reformatter/ にアクセス
2. 「整形前のメタデータ (Raw Parameters)」欄に貼り付ける
3. 自動で変換される。必要に応じて「変換」ボタンを押す
4. 抽出された Template / Negative Template を「コピー」ボタンで取得する

## 起動方法

ビルドやサーバーは不要です。`index.html` をダブルクリックするか、ブラウザにドラッグ＆ドロップするだけで動作します。

```bash
# 任意: ローカルサーバーで開く場合
npx serve .
# または
python -m http.server
```

## 対応フォーマット

メタデータ内に次の形式のフィールドがあることを想定しています。

```
Template: "..."
Negative Template: "..."
```

値はダブルクォートで囲まれた文字列で、内部の `\n` や `\"` などのエスケープシーケンスを解釈します。

## 技術構成

- 単一 HTML ファイル（`index.html`）
- [Tailwind CSS](https://tailwindcss.com/)（CDN）
- 外部依存なし・オフラインでも利用可能（Tailwind CDN 除く）

## ライセンス

未設定
