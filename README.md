# 平和ダイス Web版

HTML・CSS・JavaScriptで動く追加版です。公開用ZIPを展開して、その中身を静的サイトとして公開します。公開後の利用者にExpo GoやExpoアカウントは必要ありません。既存のExpo版とWindows APIは引き続き使えます。

公開には`PeacefulDice-Web-0.2.0.zip`を使用してください。本人が選んだ1-Aを反映し、音は初期オフ、振動・点灯維持は対応ブラウザで使う形です。以前の`PeacefulDice-Web-preview.zip`は確認用の試作です。

## GitHub Pagesへ載せる

1. `PeacefulDice-Web-0.2.0.zip`を展開します。
2. GitHubの公開リポジトリに、展開した**フォルダーの中身**を追加します。`index.html`、`app-…js`、`styles-…css`、`shake.wav`などを同じ階層に置きます。ZIPそのものを追加するだけでは公開できません。
3. リポジトリの **Settings → Pages → Build and deployment** で **Deploy from a branch** を選び、アップロードしたブランチと **/(root)** を指定して保存します。
4. 公開が終わったら、Pages画面に表示されたURLを開きます。そのURLを身内へ渡せば使えます。

`https://ユーザー名.github.io/リポジトリ名/`のような場所にも対応しています。HTML内のファイル参照は全て相対指定です。既存のサイトの下へ置く場合も、配布ファイル一式を同じフォルダーに入れてください。隠しファイル`.nojekyll`も含めます。

GitHub Pagesは公開リポジトリならGitHub Freeで利用できます。[GitHub公式説明](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages)・[公開先の設定](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

## その他の無料公開先

| 公開先 | 公開方法 | 無料枠の要点 |
|---|---|---|
| Cloudflare Pages | Direct UploadでZIPまたは展開したフォルダーをドロップ | Freeは月500回の公開、1ファイル25MiBまで |
| Netlify | 展開したフォルダーをドロップ | Freeは月300クレジット。公開やアクセスに応じて消費 |

今回はGitHub Pagesで十分です。ファイルを渡すだけの操作ならCloudflare PagesのDirect Uploadも使えます。Cloudflareは新しい開発にWorkersを推奨していますが、PagesのDirect Uploadも公式に提供されています。Workersの静的ファイル配信にも無料枠があり、設定には別途ツール等を使います。

2026-10-04に公式情報を確認：[Cloudflareのアップロード](https://developers.cloudflare.com/pages/get-started/direct-upload/)・[Pagesの上限](https://developers.cloudflare.com/pages/platform/limits/)・[Cloudflareの方針](https://developers.cloudflare.com/pages/)・[Workersの料金](https://developers.cloudflare.com/workers/static-assets/billing-and-limitations/)・[Netlifyのアップロード](https://docs.netlify.com/deploy/create-deploys/)・[Netlifyの料金](https://www.netlify.com/pricing/)

## 使い方と保存

- 基本画面の「開始」でセットを始め、抽選するたびに出目と履歴を保存します。全てのダイスが自分自身の過去の出目から補正する、採用済みの個別履歴方式です。
- 設定の編集・名前付き保存、ダイス別の次回確率、履歴と回数、グラフ、全ダイスの試し振りと3方式比較を使えます。開始前の通常抽選はセット履歴へ含めません。
- 同じ公開URLを**同じ端末・同じブラウザ**で開き直すと、進行中のセットを再開します。設定と名前付き保存も、そのブラウザのIndexedDBに残ります。
- Expo版、Web版、PC用APIの保存はそれぞれ別です。端末間やブラウザ間で同期する機能はありません。抽選や履歴を公開サーバーへ送る処理もありません。
- 「終了」「リセット」の確認画面を通して履歴を削除します。終了統計と試し振り結果は一時表示で、再読み込み後には残しません。
- 保存に失敗した場合は次の操作を止め、同じ候補結果の保存を再試行します。別のタブが先に保存した場合は上書きせず止めます。その場合は同じURLを開き直して保存済みの状態を読み込んでください。

通常のブラウザで利用してください。シークレット・プライベートブラウズ終了時、サイトデータの削除、ブラウザやOSによる保存領域の整理によってデータが消える場合があります。公開ドメインや設置フォルダーを変えた場合は、以前の保存へアクセスできません。未検証の端末性能を理由に上限を保証するものではありません。[ブラウザ保存の説明](https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria)

## ブラウザの演出

音は初期オフ、アニメーションは初期オン、点灯維持は初期オフです。振動は対応ブラウザで使えます。利用者が変更した設定は保存するため、開き直すたびに音をオフへ戻すことはありません。非対応の振動・点灯維持の操作欄は無効にし、保存済みの設定は保持します。

iPhoneブラウザは標準の振動機能に対応していません。点灯維持は対応ブラウザのHTTPSで使え、省電力設定などで解除される場合があります。音を使う場合も、端末の消音スイッチに必ず従う動作は保証できないため、アプリ内の音オフと端末音量を使ってください。別アプリへの移動や画面非表示で演出を止め、復帰だけでは再演出しません。

[振動の対応情報](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/vibrate)・[点灯維持](https://developer.mozilla.org/en-US/docs/Web/API/Screen_Wake_Lock_API)・[音声再生の制限](https://developer.mozilla.org/en-US/docs/Web/Media/Guides/Autoplay)

## 作成し直す場合

公開するだけなら、この手順は不要です。プロジェクトのソースを変更したときだけ、D:\PeacefulDice内で実行します。

```powershell
.\scripts\setup-web-tools.ps1
.\scripts\verify-web.ps1
.\scripts\package-web.ps1
```

作成済みファイルは`apps/web/dist`、配布ZIPは`release`に出ます。確認用表示は次の手順で開始し、表示されたURLをブラウザで開きます。ローカルファイルを直接ダブルクリックする方法は動作確認の対象にしていません。

```powershell
. .\scripts\stage7-environment.ps1
& $nodePath scripts/preview-web.mjs
```

Web版の確認結果と実機未確認の項目は`WEB_RESULTS.md`に記録します。
