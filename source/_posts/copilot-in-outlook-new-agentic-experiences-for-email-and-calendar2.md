---
title: "Copilot in Outlook: メールと予定表の新しいエージェント体験 Part 2"
date: 2026/04/30 10:00:00
tags: 
- New Outlook
- Copilot
---
※ この記事は、[Copilot in Outlook: New agentic experiences for email and calendar](https://techcommunity.microsoft.com/blog/outlook/copilot-in-outlook-new-agentic-experiences-for-email-and-calendar/4514601) の抄訳です。最新の情報はリンク先をご確認ください。この記事は Microsoft 365 Copilot および GitHub Copilot を使用して抄訳版の作成が行われています。

Outlook はこれまで、皆さまが作業する場所でした。これからは Copilot が皆さまの代わりに動く場所にもなります。

これまでの Copilot in Outlook は、目の前の作業を支援していました。例えば、メールの下書き、長いスレッドの要約、会議のスケジュールの調整などです。どれも便利ですが、最も大変な部分ではありません。つい後回しになってしまうフォローアップ、対応が必要なメッセージの見極め、そして一日の始まりから次々と積み重なっていくスケジュール変更など、日々の運用が負担になりがちです。

今回の更新では、ここが大きく変わります。Copilot in Outlook が受信トレイと予定表の運用を継続的に担う「エージェント型」へ進化しました。メールの優先度付け、競合する予定の再調整、重要事項の提示まで、依頼する前に自動的に支援できるようになります。

## Copilot で受信トレイを管理する
<iframe width="100%" height="480" src="https://medius.microsoft.com/Embed/video-nc/943a12a7-fa20-43f8-951d-eabce33531e5" title="Scenario 1 - Email" allowfullscreen="allowfullscreen" allow="fullscreen; picture-in-picture" sandbox="allow-scripts allow-same-origin allow-forms"></iframe>
<div style="text-align: center;">
<i>デモ用のため、一部を省略しています。</i>
</div>

受信トレイの管理は、単にメールを読んで返信することだけではありません。物事を滞りなく進めていくための継続的な作業でもあります。Copilot in Outlook はこの運用を支援し、メールの優先度付け、返信が必要なメールの抽出、フォローメールの下書き、そして受信トレイを整理された状態に保つためのルール設定まで行います。

必要なことを Copilot に伝えると、処理を進めながら、その処理内容を随時確認できるため、必要に応じて調整したり途中で介入したりできます。

**プロンプト例:**

- **フォローアップの対応を手伝う:** *メール送信後 24 時間たっても返信がない相手を特定し、重要度の高い順に並べて、丁寧なフォローメールの下書きを作成してください。*
- **複雑なメールを下書きする:** *過去 1 週間の [project name] の最新情報を収集し、その内容をもとに機密扱いかつ重要度高で、上司向けの進捗報告メールを下書きしてください。*
- **重要メールを見逃さないようにする:** *上司から届く新着メールのうち、宛先 (To:) に自分が含まれるものすべてに "High Priority" カテゴリを付与する受信トレイルールを作成してください。*
- **休暇後のキャッチアップを手伝う:** *休暇から戻ったところです。見逃した内容を要約し、最優先の事項を示し、簡潔な報告メールの下書きを作成してください。また、安全にアーカイブできるメールと、最初に取り組むべき 1-2 件のタスクを提案してください。*

**提供時期:** 4 月 27 日より、Outlook の全エンドポイントにおいて、[Frontier](https://www.microsoft.com/microsoft-365-copilot/frontier-program) プログラム経由で提供されます。

## Copilot に予定表管理を任せる

会議を設定すること自体は難しくありませんが、優先順位の見直し、重複する予定の解消、準備時間の確保に手間がかかります。

Copilot in Outlook は、予定表でも継続的に支援します。スケジュールのずれを防ぎ、日々の変更対応を行い、重要な業務に時間を合わせやすくします。

### プロアクティブに予定を監視・管理する
<iframe width="100%" height="480" src="https://medius.microsoft.com/Embed/video-nc/8ef5c0c8-6f42-45e0-8186-bbd59facfd75" title="Scenario 2 - Calendar Managed Events" allowfullscreen="allowfullscreen" allow="fullscreen; picture-in-picture" sandbox="allow-scripts allow-same-origin allow-forms"></iframe>
<div style="text-align: center;">
<i>デモ用のため、一部を省略しています。</i>
</div>

Copilot は、ユーザーの設定に基づき、プロアクティブに予定表を管理することができます。会議出席依頼への応答、1 対 1 の予定が重複した場合には再スケジュールを行ったり、必要に応じたフォーカス時間の確保にも対応します。

自分で変更を行いたい場合も、Copilot がチャットまたは会議フォーム上から支援をします。会議の再調整やキャンセル、詳細情報の更新、さらに目的や参加者、文体に合わせたアジェンダの下書き作成が可能です。

**プロンプト例:**

- **Copilot による 1:1 会議を設定する:** *上長との週次 1:1 会議を毎週月曜の午後に設定してください。競合が発生した場合は再調整してください。*
- **自分の時間を守る:** *勤務時間外の大規模会議は、上位管理職からの招待を除き、すべて自動的に「フォロー (参加せずに追跡)」してください。*
- **スケジュールの調整:** *来週予定している部下との 1:1 会議を、その週の金曜午後にすべて再調整してください。*
- **アジェンダの作成:** *明日の製品導入スタンドアップ向けにアジェンダを作成してください。未解決のブロッカー、担当者の割り当て、Go/No-Go 判断に焦点を当ててください。*

**提供時期:** 4 月 27 日より、Frontier プログラム経由で Windows 版 Outlook (訳者注：新しい Outlook) と Outlook on the web で提供されます。

### 優先事項に合わせて時間を調整する
<iframe width="100%" height="480" src="https://medius.microsoft.com/Embed/video-nc/cb4a1d60-d0fb-4863-be65-27c3d90da487" title="Scenario 3 - Calendar Layers" allowfullscreen="allowfullscreen" allow="fullscreen; picture-in-picture" sandbox="allow-scripts allow-same-origin allow-forms"></iframe>
<div style="text-align: center;">
<i>デモ用のため、一部を省略しています。</i>
</div>

仕事において、自分の時間がどこに使われているのかは、必ずしも明確とは限りません。Copilot は一歩引いて状況を見直し、最も重要なことに基づいてスケジュールを調整するのを支援します。これにより自身の優先事項を把握し、予定が過密になっている箇所やタスクの切り替えが多すぎる状況を見つけ、必要な準備を整えたうえで、重要な会議の前に集中する時間を確保できるようになります。

**プロンプト例:**

- **時間の優先順位付け:** *来週の予定表を確認し、アウトプットの質を維持しながら会議の負荷を下げられるように、辞退・フォロー参加・委任・非同期化すべき会議を提案してください。*
- **会議の準備:** *明日の [customer name] との会議に向けて準備を手伝ってください。把握しておくべき情報、確認すべき質問、注意すべきリスクを整理してください。*

**提供時期:** 4 月 27 日より、Frontier プログラム経由で従来の Outlook for Windows と Outlook on the web で提供されます。

## 今すぐ始める

Copilot in Outlook は、受信トレイと予定表を横断した日々の運用を支援できるようになりました。新機能をいち早く試したい場合は、[Frontier](https://www.microsoft.com/microsoft-365-copilot/frontier-program) プログラムに参加し、新しいエージェント体験の改善にぜひご協力ください。