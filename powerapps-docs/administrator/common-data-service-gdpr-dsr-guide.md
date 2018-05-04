---
title: 顧客作成データの DSR ガイド | Microsoft Docs
description: 顧客作成データの PowerApps DSR ガイド
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/17/2018
ms.author: paulliew
ms.openlocfilehash: cff822e24f1384833caa0baa945a7d3d07a8ee9b
ms.sourcegitcommit: e3a2819c14ad67cc4ca6640b9064550d0f553d8f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-customer-data-in-common-data-service-for-apps"></a>Common Data Service for Apps での顧客データのデータ主体の権利 (DSR) 要求に対する対応

## <a name="introduction-to-dsr-requests"></a>DSR 要求の概要
Microsoft は、パートナーによる EU 一般データ保護規則 (GDPR) への対応への協力の一環として、準備の参考となるようにこのドキュメントを作成しました。 このドキュメントでは、Microsoft が行っている GDPR への準備作業の説明だけでなく、PowerApps、Microsoft Flow、Common Data Service (CDS) for Apps の使用時に GDPR コンプライアンスをサポートするために Microsoft と協力して現在実行できる手順の例を示します。

GDPR は、規制においてデータ主体と呼ばれる人に、雇用主または他の種類の機関や組織 (データ コントローラーまたは単にコントローラーと呼ばれます) によって収集された個人データを管理する権限を与えます。 GDPR での個人データは、識別された自然人または識別可能な自然人に関連するすべてのデータと、非常に幅広く定義されています。 GDPR では、データ主体固有の権限が個人データに付与されます。このような権限には、個人データのコピーの取得、個人データの訂正の要求、個人データの処理の制限、個人データの削除、または別のコントローラーに移動できる電子的な形式での個人データの受け取りが含まれます。 データ主体がコントローラーに対して個人データへの操作を実行するよう正式に要求することを、データ主体の権利 (DSR) 要求と呼びます。

このガイドでは、Microsoft の製品、サービス、管理ツールを使用して、コントローラーである顧客が DSR 要求に対応して個人データを検索および操作する方法について説明します。 具体的には、Microsoft のクラウド内に存在する個人データの検索、アクセス、操作を行う方法が含まれます。 このガイドに記載されているプロセスの概要を次に示します。

1. **検出** — 検索および検出ツールを使用して、DSR 要求の対象である可能性がある顧客データを簡単に検索します。 可能性のある応答ドキュメントが収集されると、以下の手順で説明されている 1 つ以上の DSR アクションを実行して、要求に応答できます。 または、DSR 要求への応答に関する組織のガイドラインを要求が満たしていないと判断する場合もあります。

2. **アクセス** — Microsoft のクラウドに存在する個人データを取得し、要求された場合は、データ主体が使用可能な個人データのコピーを作成します。

3. **修正** — 必要に応じて、個人データを変更するか、個人データに対して他の要求されたアクションを実施します。

4. **制限** — さまざまなオンライン サービスに対するライセンスを削除するか、または可能な場合は目的のサービスをオフにすることで、個人データの処理を制限します。 また、Microsoft のクラウドからデータを削除して、オンプレミスの場所や別の場所にデータを保持することもできます。

5. **削除** — Microsoft のクラウドに存在する個人データを完全に削除します。

6. **エクスポート** — 個人データの (コンピューターが判読できる形式の) 電子コピーを、データ主体に提供します。

このガイドの各セクションでは、Microsoft のクラウド内にある個人データに対する DSR 要求に対応してデータ コントローラー組織が実行できる技術的な手順の概要を説明します。

## <a name="common-data-service-customer-data"></a>Common Data Service の顧客データ

> [!IMPORTANT]
> Common Data Service for Apps と Common Data Service (旧バージョン) の両方に適用されます

Common Data Services (CDS) には CDS for Apps と CDS 旧バージョンの 2 種類があり、個人データに対する処理が異なります。

どちらの種類の CDS 環境を使用しているかを確認するには、[PowerApps サイト](https://web.powerapps.com)から以下の手順のようにします。

1.  [環境] ドロップダウン リストから**環境**を選びます。
2.  **[データ]** > **[エンティティ]** に移動します。

    以下のエンティティが表示される場合は、お使いの環境は CDS for Apps です。

    ![PowerApps のエンティティ一覧](./media/common-data-service-gdpr-dsr-guide/powerapps-entities-list.png)

    以下のエンティティが表示される場合は、お使いの環境は CDS 旧バージョンです。

    ![PowerApps レガシのエンティティ一覧](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-list.png)

使っている CDS 環境の種類を特定した後は、このドキュメントの対応するセクションに従って、個人データを識別できます。

> [!NOTE]
> CDS for Apps の環境と CDS (旧バージョン) の環境が混在する場合があり、そのときは組織内の環境ごとに以下のプロセスを繰り返す必要があります。

## <a name="user-personal-data-in-common-data-service-for-apps"></a>Common Data Service for Apps 内のユーザー個人データ

### <a name="prerequisites"></a>前提条件
ユーザーは、Office 365 管理センターから作成され、CDS にアクセスするための適切な Common Data Service ユーザー ライセンスを割り当てられている必要があります。  ユーザーが Common Data Service の使用を始めるには、事前にセキュリティ ロールも必要です。

ユーザーの個人データは、Office 365 管理センターと、CDS システム ユーザー エンティティに保持されています。  標準のユーザー個人データの特定のセットが、Office 365 管理センターで保持および管理されています (ユーザー名、ユーザー ID、電話番号、メール アドレス、住所など)。 ユーザー個人データのこのセットは、すべての環境で CDS システム ユーザー エンティティに同期されます。  システム管理者は、Office 365 管理センターでのみこの個人データ セットを更新でき、これらの属性は CDS for Apps に自動的に同期されます。 また、システム管理者は、カスタム属性を作成して、CDS システム ユーザー エンティティ内で追加のユーザー個人データをキャプチャすることもできます。  これらのカスタム属性は、CDS 内でシステム管理者が手動で保持および管理します。

ユーザーが Office 365 管理センターから削除された場合でも、CDS システム ユーザー エンティティからユーザー レコードは自動的に削除されません。これは、組織の運営にとって重要なビジネス アプリケーションが中断しないようにするためです。  CDS のシステム管理者は、アプリケーションを使用して、CDS からユーザー個人データを探して削除する必要があります。

Office 365 の全体管理者の役割と CDS のシステム管理者セキュリティ ロールを持つユーザーだけが、以下で説明する検出、修正、エクスポート、削除のアクションを実行できます。

### <a name="discover"></a>Discover

システム管理者は、複数の CDS インスタンスを作成できます。  これらのインスタンスは、試用、開発、または運用に使用できます。   これらの各インスタンスが、システム管理者によって追加されたカスタム属性を含むシステム ユーザー エンティティのコピーと、Office 365 管理センターから同期されたユーザー個人データを保持しています。

システム管理者は、PowerApps 管理センターから Dynamics 365 管理センターに移動することで、すべての CDS インスタンスの一覧を検索できます。

[PowerApps 管理センター](https://admin.powerapps.com/)から次のようにします。

1.  [環境] タブに移動します。
2.  [環境] の一覧から、環境を選びます。
3.  [Dynamics 365 管理センター] のリンクをクリックします。

    ![PowerApps 環境の詳細](./media/common-data-service-gdpr-dsr-guide/powerapps-environment-details.png)

    すべてのインスタンスの一覧が表示されます。

    ![PowerApps インスタンス ピッカー](./media/common-data-service-gdpr-dsr-guide/powerapps-instance-picker.png)

CDS のユーザーからの個人データは、次の場所にあります。

|個人データが含まれるリソース | 目的 | Web サイトのアクセス | プログラムによるアクセス
| --- | --- | --- | ---
| エンティティ レコード | システム ユーザー エンティティ | [PowerApps 管理センター](https://admin.powerapps.com) | [Web API 経由](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)
| 監査履歴 | ユーザーがエンティティ レベルで作成、アクセス、変更、または削除したリソースを、顧客が識別できるようにします。 | [PowerApps 管理センター](https://admin.powerapps.com) | [Web API 経由](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)

#### <a name="user"></a>User
Office 365 管理センターで保持および管理されるユーザー個人データは、Azure Active Directory に格納されます。  この個人データは、Office 365 管理センターで管理され、すべての CDS 環境に自動的に同期されます。  システム管理者は、ユーザーがアクティブになっている間は、CDS 内で個人データを直接更新することはできません。Office 365 管理センターで直接更新する必要があります。  追加の個人データ (カスタム属性など) を、CDS に直接追加することができます。追加データは、システム管理者が手動で維持および管理する必要があります。

CDS システム管理者は、次の手順に従って、ユーザーを探し、特定のユーザーに関連付けられている個人データを検索することができます。

[PowerApps 管理センター](https://admin.powerapps.com/)から次のようにします。

1.  [環境] タブに移動します。
2.  [環境] の一覧から、環境を選びます。
3.  [Dynamics 365 管理センター] のリンクをクリックします。
4.  環境の名前をクリックします。
5.  **[開く]** ボタンをクリックします。
6.  **[設定]** > **[セキュリティ]** に移動します。
7.  **[ユーザー]** をクリックします。
8.  **[検索]** 入力ボックスにユーザーを入力します。
9.  **[検索]** ボタンをクリックします。
10. ユーザーをダブルクリックします。

    ![PowerApps のユーザー フォーム](./media/common-data-service-gdpr-dsr-guide/powerapps-user-form.png)

#### <a name="audit-history"></a>監査履歴
Common Data Service でエンティティの[監査の追跡が有効になっている](https://docs.microsoft.com/dynamics365/customer-engagement/admin/audit-data-user-activity)と、ユーザー個人データはユーザーが実行していたイベントと共に監査履歴に記録されます。

### <a name="rectify"></a>修正

データ主体から組織のデータに存在する個人データの修正を要求された場合、管理者と組織は要求に応えるのが適切かどうかを判断する必要があります。  データの修正には、ドキュメントまたは他の種類のアイテムに含まれる個人データの編集、改訂、削除などの操作が含まれる場合があります。

Azure Active Directory を使用して、Common Data Service for Apps のエンド ユーザーの ID (個人データ) を管理できます。 企業の顧客は、特定の Microsoft サービスの特性に応じて編集機能を制限するなど、DSR 修正要求を管理することができます。  データ プロセッサとしての Microsoft は、システムによって生成されたログを修正する機能を提供していません。ログは実際のアクティビティを反映しており、Microsoft のサービス内でのイベントの履歴レコードを構成しているためです。 詳しくは、「[GDPR: Data Subject Requests (DSRs)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)」(GDPR: データ主体の要求 (DSR)) をご覧ください。

Azure Active Directory からユーザー レコードが削除されると、システム管理者はすべてのインスタンスから残っているユーザーの個人データ (追加したカスタム属性など) を削除できます。  

### <a name="export"></a>エクスポート

#### <a name="system-user"></a>システム ユーザー
システム ユーザー エンティティに格納されているユーザー個人データは、ポータルのユーザー一覧から Excel にエクスポートできます。

[PowerApps 管理センター](https://admin.powerapps.com/)から次のようにします。

1.  [環境] タブに移動します。
2.  [環境] の一覧から、環境を選びます。
3.  [Dynamics 365 管理センター] のリンクをクリックします。
4.  環境の名前をクリックします。
5.  [開く] ボタンをクリックします。[設定] > [セキュリティ] に移動します。
6.  [有効なユーザー] ビューを選びます。
7.  [Excel に​​エクスポート] ボタンをクリックします。

#### <a name="audit-history"></a>監査履歴
次の手順を実行し、アプリケーションから監査履歴のスクリーンショットをキャプチャしてコピーできます。
[PowerApps 管理センター](https://admin.powerapps.com/)から次のようにします。
1.  [環境] タブに移動します。
2.  [環境] の一覧から、環境を選びます。
3.  [Dynamics 365 管理センター] のリンクをクリックします。
4.  環境の名前をクリックします。
5.  [開く] ボタンをクリックします。
6.  [設定] > [監査] に移動します。

    ![PowerApps の監査履歴メニュー](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-menu.png)

7.  [監査概要ビュー] をクリックします。
8.  ユーザー監査レコードを探します。

    ![PowerApps の監査履歴の詳細](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-details.png)

9.  Alt + PrtScn キーを押して、スクリーンショットを取得します。
10. スクリーンショットをファイルに保存します。
11. その後、DSR の要求元にファイルを送信できます。

### <a name="delete"></a>削除

#### <a name="user"></a>User
ユーザーが Office 365 管理センターから削除された場合、CDS ではユーザーの状態が無効に設定されます。ただし、組織の運営にとって重要なビジネス アプリケーションが中断しないようにするため、ユーザ個人データが自動的に削除されることはありません。
CDS からユーザー個人データを削除するには、システム管理者が手動で無効になっているユーザーの個人データを削除する必要があります。

#### <a name="remove-user-personal-data-via-user-form"></a>ユーザー フォームからユーザー個人データを削除する
Azure Active Directory からユーザー レコードが削除されると、ユーザー フォームに次のメッセージが表示されます。
このユーザーの情報は、Office 365 では管理されなくなっています。 このレコードを更新し、このユーザーに関連付けられているすべての個人データを削除または置換することにより、DSR 要求に応えることができます。

[PowerApps 管理センター](https://admin.powerapps.com/)から次のようにします。
1.  [環境] タブに移動します。
2.  [環境] の一覧から、環境を選びます。
3.  [Dynamics 365 管理センター] のリンクをクリックします。
4.  環境の名前をクリックします。
5.  **[開く]** ボタンをクリックします。
6.  **[設定]** > **[セキュリティ]** > **[ユーザー]** の順にクリックします。
7.  **[無効なユーザー]** ビューを選びます。
8.  **[レコードの検索]** にユーザー名を入力して、**[検索]** ボタンをクリックします。
9.  検索結果でユーザー名をダブルクリックします。
10. すべての個人データを削除し、**[保存]** をクリックします。

#### <a name="remove-user-personal-data-via-excel-importexport"></a>Excel のインポート/エクスポートを使用してユーザー個人データを削除する
1.  **[設定]** > **[セキュリティ]** > **[ユーザー]** の順にクリックします。
2.  **[無効なユーザー]** ビューを選びます。
3.  ユーザー個人データの更新する列をすべて含む Excel テンプレートを作成します。
4.  **[ファイルのダウンロード]** をクリックします。
5.  ダウンロードした Excel ファイルを開き、更新を行って、ファイルを保存します。
6.  [無効なユーザー] ビュー ウィンドウに戻り、[データのインポート] をクリックします。
7.  [データ ファイルのアップロード] ダイアログ ボックスで、更新した Excel ファイルを選びます。
8.  [フィールドのマップ] ウィンドウで、すべての必要な変更を行います。
9.  [次へ]、[送信] の順にクリックします。

Excel テンプレートの使用については、[Excel の追加情報](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/analyze-your-data-with-excel-templates)に関するページをご覧ください。


#### <a name="remove-audit-history-via-the-audit-summary-view-form"></a>[監査概要ビュー] フォームを使用して監査履歴を削除する

[PowerApps 管理センター](https://admin.powerapps.com/)から次のようにします。
1.  [環境] タブに移動します。
2.  [環境] の一覧から、環境を選びます。
3.  [Dynamics 365 管理センター] のリンクをクリックします。
4.  環境の名前をクリックします。
5.  [開く] ボタンをクリックします。
6.  [設定] > [監査] の順にクリックします。
7.  [監査概要ビュー] を選択します。
8.  ユーザーが実行した変更履歴を探します。
9.  行のチェック ボックスをオンにします。
10. [変更履歴を削除します] アイコンをクリックします。

## <a name="personal-data-stored-in-common-data-service-for-apps-databases"></a>Common Data Service for Apps データベースに格納される個人データ

### <a name="prerequisites"></a>前提条件
個別ユーザー (自分の顧客など) からの個人データを CDS エンティティの内容に保存することができます。  

個人が組織に DSR 要求を送信した場合、CDS のシステム管理者は、個別ユーザーがアプリケーション内で参照される可能性があるすべてのエンティティを見つける必要があります。  CDS 管理者は、個別ユーザーからの DSR 要求に対応できるように、使用しているさまざまなエンティティ内で個人データが格納されている場所のインベントリを管理する責任があります。

そうすれば、製品内の機能を使って、コンテンツ内の個人データをエンティティでエクスポート、修正、削除することができます。  

### <a name="discover"></a>Discover
CDS 管理者は、個別ユーザーから DSR 要求を受け取ったら、その個別ユーザーからの個人データが含まれる環境/CDS インスタンスを識別する必要があります。  コンテンツ内に保存した個人データを識別しやすいように、個別ユーザーからの個人データを格納する環境、インスタンス、およびエンティティのインベントリを維持するポリシーと手順を作成する必要があります。

個人データが格納されている環境、インスタンス、エンティティ、フィールドのインベントリを使用すると、個人データを検出するように CDS 検索エンジンを構成することができます。  CDS 管理者は、検索エンティティやフィールドを構成できます。詳しくは、「[組織の関連性検索の構成](https://go.microsoft.com/fwlink/?linkid=872506)」をご覧ください。
その後、CDS 管理者は CDS 環境にアクセスして、検索を実行できます。

1.  **[検索]** アイコンをクリックします。
2.  **[関連性の検索]** を選択します

    ![PowerApps の [関連性の検索] メニュー](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-menu.png)

3.  [検索] ボックスに個別ユーザーの個人データを入力します。
4.  [検索] ボタンをクリックします。

    ![PowerApps の関連性検索の結果](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-results.png)

通常、コンテンツの個人データは、アカウント、連絡先、リード、営業案件などの主要なエンティティに格納されますが、個別ユーザーの個人データを格納する場所のインベントリを維持するのは、管理者の責任です。

### <a name="rectify"></a>修正
CDS のシステム管理者は、関連性検索の結果のリストを使用して、個別ユーザーの個人データを更新できます。  ただし、この個別ユーザーの個人データが他のカスタム エンティティにも格納されている場合があります。  CDS システム管理者は、これらの他のカスタム エンティティのインベントリを維持し、個別ユーザーの個人データを適切に更新する責任があります。

関連性検索の結果から:

1.  個別ユーザーの個人データが見つかった項目をクリックします。
2.  必要に応じて、個別ユーザーの個人データを更新します。
3.  [保存] をクリックします

    ![PowerApps アカウントの詳細](./media/common-data-service-gdpr-dsr-guide/powerapps-account-details.png)

### <a name="export"></a>エクスポート
次の手順を実行して、データのスクリーンショットをキャプチャし、DSR の要求元と共有できます。

[PowerApps 管理センター](https://admin.powerapps.com/)から次のようにします。
1.  [環境] タブに移動します。
2.  [環境] の一覧から、環境を選びます。
3.  [Dynamics 365 管理センター] のリンクをクリックします。
4.  環境の名前をクリックします。
5.  **[検索]** アイコンをクリックします。
6.  [関連性の検索] を選択します。
7.  [検索] ボックスに個別ユーザーの個人データを入力します。
8.  [検索] ボタンをクリックします。
9.  項目を探してダブルクリックします。
10. <alt> + <PrtScn> キーを押して、スクリーンショットを取得します。
11. スクリーンショットをファイルに保存します。
12. その後、DSR の要求元にファイルを送信できます。

### <a name="delete"></a>削除

CDS の管理者は、個別ユーザーの個人データを、そのデータが格納されているレコードから削除できます。  CDS 管理者は、(1) 個人データが格納されているレコードを削除するか、(2) レコードから個人データの内容を削除するかを選択できます。  

> [!NOTE]
> CDS 管理者は、レコードがエンティティから削除されないように、環境をカスタマイズできます。 このように構成されている場合は、レコード自体を削除するのではなく、レコードから個人データの内容を削除する必要があります。

関連性検索の結果から:
1.  個別ユーザーの個人データが見つかった項目をクリックします。
2.  リボンの [削除] アイコンをクリックします (注: レコードを削除できない場合、このアイコンは無効になっています)。

    ![PowerApps アカウントの削除](./media/common-data-service-gdpr-dsr-guide/powerapps-account-delete.png)

## <a name="personal-data-stored-in-common-data-service-previous-version-databases"></a>Common Data Service (旧バージョン) データベースに格納される個人データ

### <a name="prerequisites"></a>前提条件

個別ユーザー (自分の顧客やユーザーなど) からの個人データを CDS エンティティの内容に保存することができます。  

個人が組織に DSR 要求を送信した場合、CDS のシステム管理者は、個別ユーザーがアプリケーション内で参照される可能性があるすべてのエンティティを見つける必要があります。  CDS 管理者は、個別ユーザーからの DSR 要求に対応できるように、使用しているさまざまなエンティティ内で個人データが格納されている場所のインベントリを管理する責任があります。

そうすれば、製品内の機能を使って、コンテンツ内の個人データをエンティティでエクスポート、修正、削除することができます。  

### <a name="discover"></a>Discover
CDS 管理者は、個別ユーザーから DSR 要求を受け取ったら、その個別ユーザーからの個人データが含まれる環境/CDS インスタンスを識別する必要があります。  コンテンツ内に保存した個人データを識別しやすいように、個別ユーザーからの個人データを格納する環境、インスタンス、およびエンティティのインベントリを維持するポリシーと手順を作成する必要があります。

個別ユーザーからの個人データは、次の場所にあります。

|個人データが含まれるリソース | 目的 | Web サイトのアクセス |    プログラムによるアクセス
| --- | --- | --- | ---
|エンティティ レコード | それぞれのビジネス エンティティでビジネス トランザクションをキャプチャする。 | PowerApps 作成者ポータル |    いいえ

#### <a name="entity-records"></a>エンティティ レコード
個別ユーザーの個人データは、任意のビジネス エンティティに格納できます。
このバージョンの Common Data Service には、独自のデータベース スキーマとインフラストラクチャが含まれます。  独自のエンティティがあり、これらのエンティティの管理は [PowerApps サイト](http://web.powerapps.com/)を使用して行われます。

エンティティの一覧を表示するには:

1.  環境を選択します

    ![PowerApps レガシ エンティティ](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2.  **[データ]** > **[エンティティ]** タブに移動します。
3.  アカウント エンティティなどのエンティティを選択します。

    ![PowerApps レガシ エンティティの詳細一覧](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

4.  エンティティをクリックします。
5.  **[データ]** タブをクリックします。エンティティのレコードの一覧が表示されます。

    ![PowerApps レガシ アカウントのデータ](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

6.  **[データのエクスポート]** アイコンをクリックします。
7.  エクスポートが完了したら、Excel ワークシートを開きます。
8.  [編集を有効にする] ボックスをクリックします。
9.  検索アイコンをクリックします。
10. 検索する個人情報を入力します。
通常、コンテンツの個人データは、アカウント、連絡先、リード、営業案件、作業者などの主要なエンティティに格納されますが、個別ユーザーの個人データを格納する場所のインベントリを維持するのは、管理者の責任です。
11. 個人データが格納されているエンティティのインベントリ リストを使用し、**ビジネス エンティティごとに上記の手順を繰り返して、個別ユーザーの個人データを探索します**。

### <a name="rectify"></a>修正
データ主体から組織のデータに存在する個人データの修正を要求された場合、管理者と組織は要求に応えるのが適切かどうかを判断する必要があります。  データの修正には、ドキュメントまたは他の種類のアイテムに含まれる個人データの編集、改訂、削除などの操作が含まれる場合があります。

Azure Active Directory を使用して、Common Data Service for Apps のエンド ユーザーの ID (個人データ) を管理できます。 企業の顧客は、特定の Microsoft サービスの特性に応じて編集機能を制限するなど、DSR 修正要求を管理することができます。  データ プロセッサとしての Microsoft は、システムによって生成されたログを修正する機能を提供していません。ログは実際のアクティビティを反映しており、Microsoft のサービス内でのイベントの履歴レコードを構成しているためです。  

詳しくは、「[GDPR: Data Subject Requests (DSRs)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)」(GDPR: データ主体の要求 (DSR)) をご覧ください。

CDS 環境に存在する個人データを修正するには、エンティティ データを Excel ワークシートにエクスポートし、更新した後、インポートしてデータベースに戻すことができます。
CDS 管理者は、個別ユーザーの個人データが格納されているすべてのエンティティを識別し、各エンティティに対して以下の手順を繰り返す責任があります。

[PowerApps サイト](http://web.powerapps.com/)から:

1.  **[データ]** > **[エンティティ]** の順にクリックします。
2.  エンティティをクリックします ( アカウントなど)。
3.  **[データ]** オプションをクリックします。
4.  **[データのエクスポート]** アイコンをクリックします。
5.  **[Excel で開く]** アイコンをクリックします (エクスポートが完了したとき)。
6.  Excel ワークシートで**編集を有効**にして、個人データを更新します。
7.  更新したワークシートを **[保存]** します (ファイルの場所がわかるように **[名前を付けて保存]** を行います)。

    ![PowerApps レガシ アカウントのデータ](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

8.  個人データに必要な更新を行います
9.  更新を保存します
10. [データ] > [エンティティ] > [アカウント] フォームで、[データのインポート] アイコンをクリックします。
11. [検索] ボックスをクリックします。
12. 更新が含まれるファイルを選択します。
13. [開く] ボックスをクリックします。
14. [インポート] ボタンをクリックします。

### <a name="export"></a>エクスポート

各エンティティの個人データを表示して、Excel ワークシートにエクスポートできます。

[PowerApps サイト](http://web.powerapps.com/)から:

1.  **[データ]** > **[エンティティ]** に移動します。
2.  表示してデータをエクスポートする**エンティティ**を選びます。
3.  **[データ]** オプションをクリックします。
4.  **[データのエクスポート]** アイコンをクリックします。 このエクスポート操作はバックグラウンドで実行され、終わると通知されます。
5. エクスポートされたデータを表示するには、[Excel で開く] アイコンをクリックします。

### <a name="delete"></a>削除
データのエクスポート/インポート機能を使って、エンティティに格納されている個人データを削除できます。

CDS 管理者は、個別ユーザーの個人データを含むすべてのエンティティを識別し、各エンティティに対して以下の手順を繰り返す責任があります。

[PowerApps サイト](http://web.powerapps.com/)から:

1.  **[データ]** > **[エンティティ]** の順にクリックします。
2.  **エンティティ**の一覧を下にスクロールし、個人データを削除するエンティティを探します。
3.  エンティティをクリックします。
4.  **[データ]** オプションをクリックします。
5.  **[データのエクスポート]** アイコンをクリックします。
6.  **[Excel で開く]** アイコンをクリックします (エクスポートが完了したとき)。
7.  Excel ワークシートで**編集を有効**にします。
8.  更新したワークシートを **[保存]** します (ファイルの場所がわかるように [名前を付けて保存] を選択します)。
9.  削除する個人データ レコードの行を削除します。
10. 更新を保存します
11. **[エンティティ]** フォームで、**[データのインポート]** アイコンをクリックします。
12. **[検索]** ボックスをクリックします。
13. 更新が含まれるファイルを選択します。
14. **[開く]** ボックスをクリックします。
15. [インポート] ボタンをクリックします。