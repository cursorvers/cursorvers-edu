# Cursorvers_edu_HTML - 教育向けランディングページ

教育・サービス紹介を目的とした静的HTMLサイトです。

---

## 技術スタック

- **フロントエンド**: 静的HTML
- **スタイリング**: Tailwind CSS (CDN)
- **JavaScript**: Vanilla JS
- **ホスティング**: GitHub Pages / Netlify 等

## プロジェクト構造

```
Cursorvers_edu_HTML/
├── index.html              # トップページ
├── services.html           # サービス紹介
├── community.html          # コミュニティ
├── *.html                  # その他のページ
├── css/                   # カスタムスタイル（あれば）
├── js/                    # JavaScript（あれば）
├── images/                # 画像ファイル
└── README.md
```

## 実装パターン

### HTML構造

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cursorvers 教育</title>

  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
  <header>
    <!-- ヘッダー -->
  </header>

  <main>
    <!-- メインコンテンツ -->
  </main>

  <footer>
    <!-- フッター -->
  </footer>

  <script src="/js/main.js"></script>
</body>
</html>
```

### セキュリティ（JavaScript）

#### XSS対策

```javascript
// ❌ Bad: innerHTML でユーザー入力を直接挿入
element.innerHTML = userInput;

// ✅ Good: textContent を使用
element.textContent = userInput;
```

### パフォーマンス最適化

#### Tailwind CSS の本番ビルド（推奨）

**現状**: CDN版を使用（開発用）

**推奨**: 本番環境では minify されたCSSを使用

```bash
npm install -D tailwindcss
npx tailwindcss init

# tailwind.config.js
module.exports = {
  content: ["./**/*.html"],
  theme: { extend: {} },
  plugins: [],
}

# ビルド
npx tailwindcss -i ./src/input.css -o ./css/styles.css --minify
```

**効果**: CSSサイズ 200KB → 20KB（90%削減）

#### 画像の遅延読み込み

```html
<img
  src="placeholder.jpg"
  data-src="actual-image.jpg"
  loading="lazy"
  alt="説明"
>
```

### JavaScript パターン

#### イベント委譲

```javascript
// ✅ Good: 親要素で一括管理
document.addEventListener('click', (e) => {
  if (e.target.matches('.button')) {
    handleClick(e);
  }
});
```

## 開発フロー

1. **HTML作成**: セマンティックなマークアップ
2. **CSS適用**: Tailwind クラス
3. **JavaScript追加**: インタラクション実装
4. **最適化**: 画像圧縮、CSS/JS minify
5. **デプロイ**: GitHub Pages 等

## SEO対策

```html
<head>
  <!-- 基本メタタグ -->
  <meta name="description" content="Cursorvers教育サービス - AI駆動の学習プラットフォーム">
  <meta name="keywords" content="AI, 教育, LINE Bot, 医療">

  <!-- OGP -->
  <meta property="og:title" content="Cursorvers 教育">
  <meta property="og:description" content="AI駆動の教育サービス">
  <meta property="og:image" content="https://example.com/image.jpg">
</head>
```

## 注意事項

- Tailwind CDN は開発用のみ（本番では minify されたCSSを推奨）
- `innerHTML` は XSS リスクがあるため慎重に
- モバイルファーストで設計

## 他プロジェクトとの関係

- **Cursorvers_Inc_HTML**: 同じ静的HTML + Tailwind 構成（スタイル共通化可能）
- **LINE Bot プロジェクト**: サービス紹介の対象

---

## Platform 連携ルール

**システム変更時は `Cursorvers_Platform/docs/system-architecture.md` を更新すること。**

詳細: `/Users/masayuki/Cursorvers_Platform/.claude/CLAUDE.md` の「システム変更時（自動反映ルール）」を参照

---

作成日: 2025-12-21
