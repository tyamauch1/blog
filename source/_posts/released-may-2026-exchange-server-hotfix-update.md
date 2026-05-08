---
title: "2026 年 5 月の Exchange Server の Hotfix 更新プログラムが公開されました"
date: 2026/5/11 15:00
tags:
- Exchange
---
※ この記事は、[Released: May 2026 Exchange Server Hotfix Update](https://techcommunity.microsoft.com/blog/exchange/released-may-2026-exchange-server-hotfix-update/4517516) の抄訳です。最新の情報はリンク先をご確認ください。この記事は Microsoft 365 Copilot および GitHub Copilot を使用して抄訳版の作成が行われています。

Microsoft は、以下の製品向けに Hotfix Update (HU) が公開されました。

- Exchange Server Subscription Edition (SE)

今回の HU は、以下の特定のバージョンの Exchange Server に対して提供されています。

- [Exchange SE RTM](https://www.microsoft.com/download/details.aspx?id=108646)

2026 年 5 月の HU には、新しい Exchange Server のセキュリティ更新プログラムは含まれていませんが、新機能が含まれています。詳細は公開された KB 情報をご確認ください。

#### Exchange のハイブリッド リッチ共存呼び出しを Graph API へ移行する更新

2026 年 5 月の Hotfix 更新には、Exchange Server のハイブリッド リッチ共存で利用する呼び出しを、Exchange Web Services (EWS) から REST ベースの Microsoft Graph API に切り替えられる機能が含まれています。これは、[ハイブリッド展開における Exchange Server のセキュリティ変更](https://jpmessaging.github.io/blog/exchange-server-security-changes-for-hybrid-deployments/) で案内した取り組みの継続となります。

<p style="background: #eeeeeb">注: <a href="https://learn.microsoft.com/troubleshoot/exchange/administration/exchange-2019-2016-end-of-support">Exchange 2016 と 2019 はサポートが終了しています</a>。これらのバージョン向けに、Graph API のハイブリッド呼び出しを利用するための更新プログラムは提供されません (Exchange 2016 / 2019 の <a href="https://jpmessaging.github.io/blog/announcing-period-2-exchange-20162019-extended-security-update-esu-program/">ESU</a> で提供される更新にも、この機能は含まれません)。
現在も Exchange 2016 または 2019 でオンプレミスのメールボックスを運用している場合は、<a href="https://jpmessaging.github.io/blog/exchange-online-ews-your-time-is-almost-up/">2026 年 10 月以降もテナントで EWS の利用を許可</a> する必要があります。さらに、Exchange Online で EWS が無効化される 2027 年 4 月までに、すべてのサーバーを Exchange SE へ<u>必ず</u>アップグレードする必要があります。
これらのサポート対象外バージョンにおけるリッチ共存機能は、2027 年 4 月以降は完全に動作しなくなります。そのため、オンプレミス環境については、できるだけ早急にサポート対象外のバージョンからアップグレードしてください。<I>サポート対象外バージョンの利用は、環境にリスクをもたらす可能性があります。</I></p>

詳細は、[Exchange SE ハイブリッドのオンプレミス リッチ共存を Graph API に移行する方法](https://jpmessaging.github.io/blog/update-your-exchange-se-hybrid-on-premises-rich-coexistence-to-graph/) と [Exchange ハイブリッド専用アプリを展開する](https://learn.microsoft.com/Exchange/hybrid-deployment/deploy-dedicated-hybrid-app) をご確認ください。

#### 更新プログラムのインストール

利用可能な更新パスは以下の通りです。
![](May2026HUpath.jpg)
- [Exchange Server Health Checker スクリプト](https://aka.ms/ExchangeHealthChecker)を使用して、更新が必要な Exchange サーバーのインベントリを作成し、各サーバーの更新状況 (CU、SU、手動対応) を確認してください。
- 最新の CU をインストールします。[Exchange Update Wizard](https://aka.ms/ExchangeUpdateWizard) を利用して、現在の CU と目標 CU を選択し、手順を確認してください。
- 更新プログラムのインストール後に再度 Health Checker を実行し、追加の対応が必要かどうかを確認します。
- セットアップ完了後、サーバーを再起動し、すべての Exchange サービスが正常に起動したことを確認します。一部のサービスが無効状態になっている場合は、更新プログラムのインストールが何らかの理由で中断されたことを示しています。詳細については、[この記事](https://support.microsoft.com/topic/2024-su-a650da30-f8fb-469d-a449-47396cab0a15)の「回避策 1」を参照してください。
- Exchange Server のインストール中やインストール後にエラーが発生した場合は、[SetupAssist スクリプト](https://aka.ms/ExSetupAssist) を実行してください。更新後に問題が発生した場合は、[失敗した Exchange Server の更新プログラムの修復方法](https://learn.microsoft.com/troubleshoot/exchange/client-connectivity/exchange-security-update-issues) や、[ファイル バージョン エラーに関する KB 記事](https://support.microsoft.com/topic/file-version-error-when-you-try-to-install-exchange-server-november-2024-su-a650da30-f8fb-469d-a449-47396cab0a15) も確認してください。

#### Hotfix 更新の FAQ

***なぜこの HU は月初に公開されたのですか。緊急の更新ですか。***  
Hotfix 更新プログラムはセキュリティ更新を含まないため、「Patch Tuesday」の公開スケジュールには連動しません。Exchange の Hotfix Update は任意のものとなります。

***直近のセキュリティ更新プログラムをインストールしました。後から公開された Hotfix 更新プログラムもインストールすべきですか？***  
Exchange Server の HU は *オプションの更新プログラム* ですが、組織にとって有益な機能や修正が含まれている場合があります。詳細については、リリース KB 記事をご確認ください。

***以前のセキュリティ更新プログラムをまだインストールしていません。後からリリースされた HU をインストールする前に、最後に利用可能な SU をインストールする必要がありますか？***  
Exchange の更新プログラム (HU または SU) はすべて [累積更新](https://learn.microsoft.com/exchange/plan-and-deploy/post-installation-tasks/security-best-practices/exchange-server-update-faq?view=exchserver-2019) です。そのため、新しい SU または HU には、以前の古い SU または HU の変更内容も含まれます。古い更新を未適用でも、新しい更新を直接適用して問題ありません。

***私たちの Exchange サーバーは Windows/Microsoft Update を通じて自動的に更新されます。その場合、HU 更新プログラムも自動的にインストールされますか？***  
この HU はサーバー向けの<u>任意の更新</u>です。Microsoft Update Catalog には公開されません。必要な場合は Download Center から入手してください。

***HU でリリースされた新機能や修正は今後の更新プログラムにも含まれますか、それともこの特定の HU をインストールする必要がありますか？***  
この HU に含まれる内容は、今後リリースされる Exchange SE の更新プログラムにも含まれます。

***HU を (必要に応じて) アンインストールすることは可能ですか？***  
はい。HU は SU と同様にアンインストールすることが可能です。

この記事の公開時点では、関連するドキュメントが完全に利用可能でない場合があります。

この記事は今後更新される可能性があります。更新があれば、ここに追記されます。