---
layout: classic-docs
title: クレジットの使用
categories:
  - how-to
description: CircleCI のクレジットの使用方法
version:
  - Cloud
---

このドキュメントでは、CircleCI でのクレジット使用の基本事項について説明します。 CircleCI の従来のコンテナベースのプランを利用している場合は、「[コンテナを使用する]({{site.baseurl}}/ja/2.0/containers)」をご覧ください。 コンテナ使用からクレジット使用への切り替えを希望される場合は、[サポート チケットを作成](https://support.circleci.com/hc/ja/requests/new)してお問い合わせください。

## 概要
{: #overview }

CircleCI のクレジットベースの従量課金制プランでは、チームの CI ソリューションを柔軟にカスタマイズおよびスケールでき、使用量に応じた料金のみが請求されます。 クレジットは分単位で消費され、レートは選択したビルドの構成によって異なります。

チームに最適なプランを検討するときには、以下のような要素を考慮する必要があります。

- チームのユーザー数
- 必要なサポートのレベル (コミュニティによるサポート、標準サポート、プレミアム サポート)
- 複数のマシン タイプへのアクセスの要否
- Docker レイヤー キャッシュ、ビルドの同時処理、ビルド履歴といった機能の要否

例として、Performance プランでクレジットを使用する場合を考えてみましょう。 Performance プランでは以下を利用できます。 この例では、チームが複数のグループに分かれ、それぞれ異なるプロジェクトを進めています。 大規模なプロジェクトもあれば、CI の構成で割り当てるリソースが少なくて済む小規模なプロジェクトもあります。 クレジットを使用すると、リソースを最大化する必要があるマシンと利用時間をピンポイントで指定できます。

たとえば、大規模なプロジェクトのビルドを高速化するためには `large` `resource_class` (vCPU 4 基、RAM 8 GB、20 クレジット/分) を使用できます。 一方、小規模なプロジェクトでコードのリリース頻度が低い場合や、ビルド時間を重視しない場合は `small` `resource_class` (vCPU 1 基、RAM 2 GB、5 クレジット/分) を使用できます。

ご希望のプランを設定するには、CircleCI の Web アプリケーションで [`Settings`] > [`Plan Overview`] を開き、 お客様のニーズに最適なプランを選択します。

## クレジットベース プランの設定
{: #configuring-your-credit-plan }

ご希望のプランを設定するには、CircleCI の Web アプリケーションで [`Settings`] > [`Plan Overview`] を開き、 お客様のニーズに最適なプランを選択します。

## Free プラン
{: #free-plan }

従来の CircleCI のコンテナベース プランと同様に、従量課金制でも無料のプランをご用意しています。 Free プランでも CircleCI の主要機能の多くをご利用いただけます。

- Orb の使用
- ワークスペース
- 依存関係のキャッシュ
- Windows/Linux でのビルド

従量課金制の Free プランでは、週に 2,500 クレジットが提供され、Medium タイプのマシン (vCPU 2 基、RAM 4 GB) で利用することができます。 With this combination, a small number of credits are charged per minute and there is no limit on user seats. Refer to the [Pricing](https://circleci.com/pricing/) page for more information on credit amounts.

## Performance プラン
{: #performance-plan }

Performance プランにアップグレードすると、Free プランの内容に加えて複数のメリットが提供されます。

- すべてのマシン サイズの Docker/Linux ベース マシンへのアクセス
- Medium サイズの macOS マシンへのアクセス
- 無制限のユーザーシート数
- Docker レイヤー キャッシュへのアクセス
- キューイングなし
- サポート

## オープンソース プロジェクトでのクレジット使用
{: #open-source-credit-usage }

Free プランの組織には、毎月 400,000 クレジットが無料で付与され、Linux コンピューティングでのオープンソース プロジェクトのビルドに利用できます。 この特典を受け取るには、Free プランを利用し、リポジトリをパブリックにする必要があります。

CircleCI の Free プランを使用して macOS でビルドを行っている組織にも、毎月 25,000 クレジットが無料で付与され、macOS オープンソース プロジェクトのビルドに利用できます。 ご希望の方は、billing@circleci.com までお問い合わせください。

## Docker レイヤー キャッシュ
{: #docker-layer-caching }

Docker レイヤー キャッシュ (DLC) は 1 回のジョブ実行につき 200 クレジットでご利用いただけます。 DLCはPerformanceプランでのみ利用可能です。 DLC の詳細については、[こちらのドキュメント]({{site.baseurl}}/ja/2.0/docker-layer-caching)をご覧ください。

## トラブルシューティング
{: #troubleshooting }

### Am I charged if my build is "queued" or "preparing"?
{: #am-i-charged-if-my-build-is-queued-or-preparing }

No. If you are notified that a job is "queued", it indicates that your job is waiting due to a **plan** or **concurrency** limit. If your job indicates that it is "preparing", it means that CircleCI is setting up or _dispatching_ your job so that it may run.

If you find that jobs are "preparing" for quite some time, you may be able to reduce it if your jobs use the docker executor; try using more recent docker images to decrease preparation time.

## Questions and comments
{: #questions-and-comments }

ご不明な点がございましたら、まずは「よくあるご質問」の「[料金・支払]({{site.baseurl}}/ja/2.0/faq/#料金支払い)」セクションをご確認ください。 解決しない場合は、お気軽に[サポート チケットを作成](https://support.circleci.com/hc/ja/requests/new)してお問い合わせください。
