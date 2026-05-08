---
title: メールボックスのインポート/エクスポート用 Microsoft Graph API の一般提供開始
date: 2026/05/08 11:00
tags: Exchange Online
---

※ この記事は、[Announcing general availability of the mailbox import and export Microsoft Graph APIs](https://devblogs.microsoft.com/microsoft365dev/announcing-general-availability-of-the-mailbox-import-and-export-microsoft-graph-apis/) の抄訳です。最新の情報はリンク先をご確認ください。この記事は Microsoft 365 Copilot および GitHub Copilot を使用して抄訳版の作成が行われています。

メールボックスのインポートおよびエクスポート用 Microsoft Graph API が、一般提供 (GA) になりました。パブリック プレビューを経て、本番環境で利用できる状態になり、組織や開発者は Microsoft Graph を通じて Exchange Online のメールボックス データをより効率的に管理、移行、統合できるようになります。

昨年、従来の Exchange Web Services (EWS) API に代わる、モダンで堅牢な選択肢としてメールボックスのインポート / エクスポート API のパブリック プレビューを公開しました。EWS の廃止が予定されている中で、Exchange Online のメールボックス データを完全な忠実度でインポートおよびエクスポートできる、安全でスケーラブルな将来志向のソリューションが求められていました。プレビュー期間中には多くのフィードバックが寄せられ、本番環境向けに API の改善と強化が行われました。

## 一般提供で利用できる主な機能

- **メールボックス階層の探索**: メールボックス構造をたどり、フォルダーやサブフォルダーにアクセスし、個々のメールボックス アイテムを列挙できます。
- **メールボックス アイテムの完全な忠実度でのサポート**: IPM サブツリー内で、メッセージ、連絡先、予定表アイテムを含むあらゆる種類のメールボックス アイテムにアクセスできます。
- **フォルダー管理**: メールボックス フォルダーの作成、更新、削除を行い、必要に応じてメールボックス コンテンツを整理できます。
- **拡張プロパティ**: フォルダーやアイテムに対して単一値および複数値の拡張プロパティを利用でき、標準の Microsoft Graph メタデータでは表現できない独自のデータ シナリオに対応できます。
- **きめ細かなアクセス許可スコープ**: アプリケーションやユーザーが必要な範囲でのみメールボックス データを読み取り、エクスポート、インポートできるように、細かい制御を適用できます。

## サポート対象

初期の GA リリースでは、次のメールボックス タイプがサポートされます。

- プライマリ メールボックス
- 共有メールボックス

一方で、初期の GA リリースには次のメールボックス タイプは含まれていません。

- アーカイブ メールボックス
- パブリック フォルダー
- グループ メールボックス

これらのメールボックス タイプも重要であることは認識されており、特に EWS からの移行を計画している組織やパートナーにとっては関心の高い項目です。これらの領域の対応は引き続き進められており、今後の進捗は別途案内される予定です。

また、エクスポートされるアイテム形式は、汎用的なデータ交換形式として使うことを目的としたものではなく、アイテムの忠実度を維持するために意図的に不透明な形式になっています。つまり、サポートされる正しい利用パターンは、アイテムをエクスポートし、返されたストリームを保持したうえで、それを Exchange Online メールボックスへ再インポートするために使うことです。

<div style="margin:1.25em;border-left:4px solid #f85149;padding:.5em">
<div style="margin:0 0 16px 0;display:flex;align-items:center;line-height:1;color:#f85149">
<svg viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true" style="margin-right:8px">
<path fill="#f85149" d="M4.47.22A.749.749 0 0 1 5 0h6c.199 0 .389.079.53.22l4.25 4.25c.141.14.22.331.22.53v6a.749.749 0 0 1-.22.53l-4.25 4.25A.749.749 0 0 1 11 16H5a.749.749 0 0 1-.53-.22L.22 11.53A.749.749 0 0 1 0 11V5c0-.199.079-.389.22-.53Zm.84 1.28L1.5 5.31v5.38l3.81 3.81h5.38l3.81-3.81V5.31L10.69 1.5ZM8 4a.75.75 0 0 1 .75.75v3.5a.75.75 0 0 1-1.5 0v-3.5A.75.75 0 0 1 8 4Zm0 8a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg>
訳者注
</div>
本機能はエクスポート / インポートを目的とした機能であり、メールボックスのバックアップ リストア等を目的とした機能ではございません。
</div>


## スロットリング、可搬性、本番利用時の考え方

メールボックスのインポート/エクスポート API では、Microsoft Graph の他の Outlook リソースと同じ標準の [Outlook resource limits](https://learn.microsoft.com/graph/throttling-limits?view=graph-rest-beta#outlook-service-limits) が適用されます。

## 詳細情報と利用開始

プレビュー段階で API を評価していた場合、API モデルは大きく変わっていないため、プライマリ メールボックスや共有メールボックスのシナリオでは GA 版への移行は比較的スムーズです。これから使い始める場合は、まず Microsoft Learn の [Use the mailbox import and export APIs in Microsoft Graph](https://learn.microsoft.com/graph/api/resources/mailbox-import-export-api-overview) を参照し、その後で自分のシナリオに対応するインポートおよびエクスポート メソッドを確認してください。