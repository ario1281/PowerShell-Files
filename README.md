# PowerShell-Files

PowerShell でファイル整理や変換を行うための小さなユーティリティ集です。  
画像・PDF・WebP の変換や、連番リネーム、ファイル名先頭の数字削除をまとめています。

## 含まれているスクリプト

### `convert img 2 pdf.ps1`
- 同じフォルダ内の `webp / jpg / jpeg / png` を名前順で取得
- ImageMagick (`magick`) を使って 1 つの PDF に変換
- 出力名は実行フォルダ名と同じ `フォルダ名.pdf`

### `convert pdf 2 cbz.ps1`
- 同じフォルダ内の PDF を検索
- Ghostscript (`gswin64c`) で各ページを PNG に展開
- ZIP 圧縮後に `.cbz` へ変更
- 変換成功時は作業フォルダと元 PDF を削除

### `convert img 2 cbz .ps1`
- 画像から PDF を作成
- その後 PDF から CBZ へ変換
- `convert img 2 pdf.ps1` と `convert pdf 2 cbz.ps1` を順番に実行

### `convert webp 2  gif.ps1`
- アニメーション WebP のみを GIF に変換
- 静止 WebP はスキップ
- 変換後は元の WebP を削除

### `rename file.ps1`
- 指定した拡張子のファイルを対象に一時拡張子へ変更
- 任意の接頭辞 + 4 桁ゼロ埋め連番でリネーム
- 必要に応じて拡張子も変更可能

### `num delete.ps1`
- WebP ファイル名先頭の指定桁数を削除
- 区切り文字付きの名前にも対応

## 必要環境

- Windows PowerShell または PowerShell
- [ImageMagick](https://imagemagick.org/)  
  - 使用コマンド: `magick`
- [Ghostscript](https://www.ghostscript.com/)  
  - 使用コマンド: `gswin64c`

> `convert pdf 2 cbz.ps1` と `convert img 2 cbz .ps1` を使う場合は Ghostscript が必要です。  
> `convert img 2 pdf.ps1` と `convert webp 2  gif.ps1` を使う場合は ImageMagick が必要です。

## 使い方

1. 対象ファイルを各スクリプトと同じフォルダに置きます
2. PowerShell を開いてそのフォルダへ移動します
3. 目的のスクリプトを実行します

```powershell
.\rename file.ps1
.\num delete.ps1
.\convert webp 2  gif.ps1
.\convert img 2 pdf.ps1
.\convert pdf 2 cbz.ps1
.\convert img 2 cbz .ps1
```

## 注意事項

- 多くのスクリプトは変換後に元ファイルを削除します
- 実行前にバックアップを取ることをおすすめします
- スクリプト名に空白が含まれるため、PowerShell では `.\` を付けて実行してください