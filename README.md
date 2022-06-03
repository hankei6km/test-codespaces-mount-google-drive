# test-codespaces-mount-google-drive

Codespaces の dev container から Google Drive をマウント。

あとで Zenn に記事を作る予定。とりあえずの簡単使い方。

## Standard authorization

デスクトップ環境(Codespace と同一の環境である必要はないです)で一旦認証を遠しマウントする。
マウントできたら `${HOME}/.gdfuse/<label>` ディレクトリーが作成されるので、`config` と `state` の内容を確認する。
その内容を使って Codespaces 用の SECRET に `GDFUSE_CONFIG` `GDFUSE_STATE` を作成。
Codespace を作成すると毎開始時に `${HOME}/gdrive` にサービスアカウントのドライブがマウントされる。


ブラウザーが使えない環境の場合は以下の記事が参考になります。

https://qiita.com/boss_ape/items/74bcad7441417c331205


## Service Account

サービスアカウントを作成し、`gcloud iam service-accounts keys` などで鍵ファイルを作成。
その内容を使って Codespaces 用の SECRET に `GDFUSE_SA` を作成。
Codespace を作成すると毎開始時に `${HOME}/gdrive` にサービスアカウントのドライブがマウントされる。

その他の設定は https://github.com/astrada/google-drive-ocamlfuse/wiki/Service-Accounts を参照。

