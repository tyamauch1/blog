---
title: "Exchange Online における POP / IMAP のレガシー TLS とエンドポイント廃止のお知らせ"
date: 2026/05/01
lastupdate: 2026/05/01 00:00
tags: Exchange Online
---

※ この記事は、[Deprecating Legacy TLS and Endpoints for POP and IMAP in Exchange Online](https://techcommunity.microsoft.com/blog/exchange/deprecating-legacy-tls-and-endpoints-for-pop-and-imap-in-exchange-online/4515201) の抄訳です。最新の情報はリンク先をご確認ください。この記事は Microsoft 365 Copilot および GitHub Copilot を使用して抄訳版の作成が行われています。

インターネットのセキュリティは絶えず進化しており、古い暗号化プロトコルはもはや現在のセキュリティ要件を満たすことができなくなっています。お客様のメール環境をセキュアに保つための継続的な取り組みの一環として、Exchange Online 接続の最新化を引き続き進めています。

#### 変更内容

Exchange Online への **POP3 および IMAP4 接続**に対する**レガシー TLS バージョン (TLS 1.0 および TLS 1.1) のサポートを完全に廃止**する計画です。これらの古い TLS バージョンはすでに業界では以前から非推奨となっており、現在では安全とは見なされなくなっています。

最新のメール クライアントおよびライブラリはすでに **TLS 1.2 以上**をサポートしており、現在 Exchange Online への POP および IMAP トラフィックの大多数がこれらの新しいプロトコルを使用しています。

数年前より、古いバージョンのブロックを開始していますが、[オプトインすることで引き続きの利用を許可していました](https://techcommunity.microsoft.com/blog/exchange/new-opt-in-endpoint-for-pop3imap4-clients-that-need-legacy-tls/3710395)。今回、これらのサポートを完全に廃止します。*今回発表する廃止の影響を受けるのは、[レガシー エンドポイント](https://learn.microsoft.com/exchange/clients-and-mobile-in-exchange-online/opt-in-exchange-online-endpoint-for-legacy-tls-using-pop3-or-imap4)の利用を明示的にオプトインしているお客様のみ*と想定しています。

#### お客様が取るべきアクション

Exchange Online で POP または IMAP を使用している場合は、以下をご確認ください。

- メール クライアント、アプリケーション、およびライブラリが **TLS 1.2 以降**をサポートしており、[レガシー エンドポイント](https://learn.microsoft.com/exchange/clients-and-mobile-in-exchange-online/opt-in-exchange-online-endpoint-for-legacy-tls-using-pop3-or-imap4)を使用してサービスに接続していないこと
- カスタムまたは組み込み型のアプリケーション (デバイスやレガシー サービスなど) が適切に更新されていること

レガシー バージョンを使用しているかどうかが不明な場合は、POP および IMAP クライアントの構成をご確認ください。もし使用している場合は、通常、アプリケーションまたはデバイスのベンダーにて TLS のサポート状況の確認やアップグレードに関する案内を受けることができます。

#### 今後の予定

2026 年 7 月より、レガシー バージョンによる接続のブロックを開始する予定です。

従来どおり、これらの移行については予測可能で十分に周知された形で進めることを目指すとともに、Microsoft 365 全体のセキュリティ強化を継続してまいります。

