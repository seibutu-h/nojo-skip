# ノジョ水切り

クリスタルノジョさんを海に投げて、水切りでどこまで飛ばせるかを競うブラウザゲームです。

## ▶ [ここから遊べます](https://seibutu-h.github.io/nojo-skip/)

PC・スマホのブラウザで、そのまま遊べます（インストール不要）。

## 遊び方

1. 投げる角度とノジョさんの体の傾きを決める
2. タイミングよく投げる
3. 低く投げて、背中から水面に当てるとよく跳ねます。波の形によっては止まることも
4. 結果は X にポストできます。距離・水切り回数・プレイ回数のランキングもあります

実績は全100個。集めるほどノジョさんのオーラが燃え上がります（隠し実績もあります）。

## 技術スタック

| 分野 | 使っているもの |
|---|---|
| 3D描画 | [three.js](https://threejs.org/) r160（WebGL）。importmap で CDN（jsDelivr）から読み込み、ビルド不要 |
| ポストエフェクト | EffectComposer ＋ UnrealBloomPass ＋ OutputPass |
| 海 | 自作シェーダー：Gerstner 波、屈折（シーンの色と深度を使用）、吸収・散乱、フレネル反射、泡 |
| 海底 | コースティクス（光の揺らぎ）、砂の風紋、深さによる減衰 |
| 空 | CC0 の HDRI（[Poly Haven「Promenade de Vidy」](https://polyhaven.com/a/promenade_de_vidy)）を晴れに加工し、RGBE の PNG にして GPU で復元 |
| 物理 | 自作：波と同じ式で水面の高さ・法線を求め、入射角と体の傾きで跳ね返りを計算（1秒240ステップ） |
| モデル | 自作のクリスタルノジョ（glTF。JSON に埋め込んで GLTFLoader で読み込み） |
| 効果音 | Web Audio API でその場で合成（音声ファイルなし） |
| ランキング | Google Apps Script（ウェブアプリ）＋ Google スプレッドシート |
| 保存 | localStorage（ベスト記録・実績・設定） |
| 公開 | GitHub Pages |
| 共有 | X のポスト（intent）、OGP / Twitter Card |

## ファイル構成

```
index.html          ゲーム本体（HTML / CSS / JavaScript を1ファイルに）
crystal_nojo.json   クリスタルノジョの3Dモデル
sky_hdr.png         空の HDRI
card.png            X のリンクカード画像
```

## クレジット

- 空の HDRI：[Poly Haven](https://polyhaven.com/)（CC0）
- 3D ライブラリ：[three.js](https://threejs.org/)（MIT License）

## お断り

このゲームは、VTuber 富士葵さんのファンが個人で作った非公式の二次創作です。
富士葵さんおよび関係者の皆さまとは関係ありません。

## 更新履歴

### 2026-10-03
- 実績の判定を見直しました（画面の表示と判定がずれていたものを修正）
- 一部の実績の数え方を調整しました
- 一部の隠し実績にヒントを追加しました
- 実績を遊び尽くした人向けのお楽しみを追加しました
- 細かい不具合を修正しました
