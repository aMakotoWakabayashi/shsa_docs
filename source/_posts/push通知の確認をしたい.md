---
title: push通知の確認をしたい
date: 2019-06-07 10:26:30
tags: 
	- push
	- ios
	- feature
---

h3. Push 通知の確認をしたい

アプリとサーバーでそれぞれ push 用の設定が必要です。

* アプリ
** iOS
Push 通知を有効とした、BundleID が *com.access-company.ios.push.test* のアプリとして作成する必要があります。
プロビジョニングは test_push_dev というものなので、ビルドできる人にアプリの作成を依頼してください。
** Android
Android は jenkins でビルドされている開発用のアプリをそのまま使用できるので、
インストールページよりインストールしてください。
* サーバー
** iOS
push 通知用の com.access-company.ios.push.test の push 証明書を設定する必要があります。
ストア管理画面のアプリの設定項目に「APNs証明書」という項目があるので、そこの「Subject CN」を確認してください。
ここに com.access-company.ios.push.test という文字列があれば、push 通知可能ですが、設定されていない場合は
自身で設定をお願いします。
設定自体は dev サーバーの以下のアプリに設定されています。
"PUSHTEST":https://dev-store000-access-dpe.herokuapp.com/apps/1071724287
このアプリに設定されている「APNs証明書」と「APNs秘密鍵」を試験したいアプリの同じ箇所に
ペーストしてください。
Subject CN が com.access-company.ios.push.test となっていれば準備完了です。
** Android
以下のトークンが試験したいアプリの「FCM API キー」に登録されているかどうか確認してください。
@AIzaSyD1WEC7cE4ZumvwqOSH9LBX77OgJvt6q8s@
登録されている場合は通知されるはずです。

*実際に Push 送信する方法*

サーバーの管理画面から「管理」=> 「APNs/GCM」の画面に遷移。
「タイトル」「メッセージ」を入力して iOS の方は「APNs設定」から、Android は「GCM設定」から
送信したいアプリを選択して送信してください。
スケジュールはそのまま送信しても即時送信されます。
