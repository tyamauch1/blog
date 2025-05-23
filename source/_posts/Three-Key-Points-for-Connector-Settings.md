---
title: >
  コネクタ設定における 3 つのポイント (送信元  組織のメール サーバー)
date: 2017-12-07
tags: Exchange Online
alias: コネクタ設定における 3 つのポイント (送信元  組織のメール サーバー)/index.html
---
今回は Exchange Online のメール フローにおいて、お客様からしばしばお問い合わせをいただいておりますオンプレミスのサーバー向けにコネクタ設定を行う際の注意点をお伝えします。

Exchange Online は特定の送信元 IP から急激なメール受信量の増加を検知すると、サービスを保護するために当該 IP からのメール受信を自動的に制限し、遅延受信させます。
これは以下の blog でご案内の IP スロットリングの機能ですが、この特定の IP がお客様にて運用されている問題のないサーバーである場合には本機能の動作は不要であり、回避するためには送信元を組織のメール サーバー、送信先を Office 365 とするコネクタの設定が有効です。
&nbsp;
Title: IP スロットリングについて
URL: <a href="https://blogs.technet.microsoft.com/exchangeteamjp/2015/03/23/ip/">https://blogs.technet.microsoft.com/exchangeteamjp/2015/03/23/ip/</a>
&nbsp;
送信元を組織のメール サーバーとするコネクタを設定すると、特定の送信元サーバーからのメールをコネクタが作成されている Office 365 テナントへメールをルーティングする動作となります。
このようなコネクタを作成するときには以下の点について予めご留意いただきますようお願い申し上げます。

&nbsp;
<u><strong>&lt;&lt; Point 1 &gt;&gt; 他テナント宛てのメールも自テナントで受信する</strong></u>
前述のようにコネクタを作成することで対象となるメール サーバーから送信されたメールを Office 365 が受信すると、コネクタのあるテナントへまずメールをルーティングします (後述の Point 2 および 3 でご案内の、コネクタが使用される条件を満たしていることが前提となります)。
そのため、宛先が別の Office 365 テナントのメール (別のお客様にご登録いただいているドメインを含むメール) である場合にも、コネクタのあるテナントでまず受信します。
その後、実際に宛先ドメインが登録されているテナントへメールが中継されます。
これは特別なことではなく、組織のメール サーバーからのメールを受信するように設定されたコネクタが適切に動作した結果です。

そこで注意が必要となるのは、Exchange Online には各テナントごとにメール フローのルール設定 (トランスポート ルール) を行うことができるため、例えば自テナントに登録されていないドメイン宛てのメールはブロックするような設定を行っていると、組織のメール サーバーから他テナント宛てのメールも最終的にブロックされ届かない問題が起きます。
コネクタを設定する際は組織のメール サーバーからのメールは一度、自テナントにて受信し他テナントへ中継される動作となることにご注意ください。

&nbsp;
<u><strong>&lt;&lt; Point 2 &gt;&gt; 証明書ベースのコネクタが効かない場合がある</strong></u>
組織のメール サーバーを送信元とするコネクタには、送信元を識別する方法として送信元メール サーバーが提示する証明書のサブジェクト名 (別名) または送信元 IP アドレスを選ぶことができます。
弊社としては前者の証明書ベースのコネクタを推奨しております。これは以下の Web サイトでご案内のように後者の IP アドレス ベースのコネクタの場合には Office 365 がメールの中継を拒否する場合があるためです。
&nbsp;
 Title: Office 365 の電子メールでコネクタを構成しているお客様への重要なお知らせ
  URL: <a href="https://support.microsoft.com/ja-jp/help/3169958/important-notice-for-office-365-email-customers-who-have-configured-co">https://support.microsoft.com/ja-jp/help/3169958/important-notice-for-office-365-email-customers-who-have-configured-co</a>
&nbsp;
Office 365 は外部からメールを受信すると、全テナントのコネクタに設定されている証明書のサブジェクト名と、送信元メール サーバーが提示した証明書のサブジェクト名 (別名) を照らし合わせ、合致するコネクタを抽出します。
合致するコネクタがあると、そのコネクタに設定されているサブジェクト名がそもそもコネクタのあるテナントに登録されているドメインであるかチェックします (※ 1)。
証明書のサブジェクト名がテナントに登録されていないドメインである場合は、代わりに送信者 (差出人) もしくは受信者のメール ドメインがテナントに登録されているドメインかをチェックします。
チェックを通過したメールはコネクタ設定のあるテナントへルーティングされます。

(※ 1) ワイルドカードも考慮されるため、例えばコネクタの設定が *.contoso.com であり、テナントに登録されているドメインが contoso.com や jpn.contoso.com といった場合も有効です。

コネクタのサブジェクト名と証明書のサブジェクト名だけを合わせテナントに登録されているドメインとは合致しない場合には、送信者 (差出人) または受信者のメール ドメインも登録されていないドメインであると、コネクタが使用されないことをご注意ください。

この点につきましては、下記 TechNet でもご案内しております。
&nbsp;
Title: Office 365 と独自の電子メール サーバーの間のメールをルーティングするようにコネクタを設定する
URL: <a href="https://technet.microsoft.com/ja-jp/library/dn751020(v=exchg.150).aspx">https://technet.microsoft.com/ja-jp/library/dn751020(v=exchg.150).aspx</a>
- パート 1:Office 365 から電子メール サーバーにメールが流れるように構成する (該当箇所を以下に抜粋)
Office 365 の承認済みドメインと一致するサブジェクト名で構成されている証明書を使用する。証明書の共通名、またはサブジェクトの別名を組織のプライマリ SMTP ドメインと一致させることをお勧めします。

&nbsp;
<u><strong>&lt;&lt; Point 3 &gt;&gt; コネクタがあってもメールが届かない場合がある</strong></u>
送信元を組織のメール サーバーとするコネクタを設定すると、これまで述べてきたようにコネクタのあるテナントでまずメールを受信します。
証明書ベースのコネクタの場合には、Point 2 でご案内の動作により証明書のサブジェクト名 (別名)、コネクタのサブジェクト名、テナントのドメインの 3 つの条件にすべて合致することで、送受信者のメール ドメインがテナントのドメインに登録されていない場合にも有効にコネクタが動作することを説明しました。

一方、IP アドレス ベースのコネクタの場合には証明書のサブジェクト名による情報がないため、全テナントから送信元 IP の設定と合致するコネクタが抽出された後、送信者 (差出人) または受信者のメール ドメインがコネクタのあるテナントに登録されているドメインかどうかのみチェックされます。

ここで注意が必要となるのが、送信者 (差出人) のドメインがテナントに登録されていないケースです。
その場合は受信者のメール ドメインがコネクタのあるテナントに登録されているドメインかどうかがチェックされますが、送信元メール サーバーが単一の SMTP セッションの中で複数のメール ドメインを受信者として送信 (※ 2) すると、Office 365 はどのドメインをコネクタの検証用に使用すればよいか判断できず中継が拒否されます。

本記事執筆時点 (2017 年 12 月 6 日) では、複数の宛先メール ドメインが、同じコネクタのあるテナントにいずれも登録されており複数テナントにまたがっていなかったとしても中継が拒否されることをご注意ください。

(※ 2) 例えば以下のように RCPT TO コマンドで複数のメール ドメインが受信者として指定される場合です。
MAIL FROM: user01@contoso.com
RCPT TO: user01@adatum.com
RCPT TO: user01@fabrikam.com

&nbsp;
今回のご案内は以上となります。
Office 365 とお客様のメール サーバーとを円滑にご連携いただく際の注意点としてお役に立てていただけますと幸いです。
&nbsp;
※本情報の内容は作成日時点でのものであり、予告なく変更される場合があります。
