---
title: Power BI のダッシュボードを構成する | Microsoft Docs
description: Power BI のダッシュボードの概要と構成方法について説明します。
author: ramanasridhar
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 06/22/2020
ms.author: ramanasr
ms.reviewer: nkrb
ms.openlocfilehash: 4ce6832fffb19f62ffeb01ce015392747e0fc840
ms.sourcegitcommit: bd543dccaa38bd63ad576f408c8b669c7e653ca3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "3500838"
---
# <a name="configure-power-bi-dashboards"></a>Power BI のダッシュボードを構成する

高等教育機関の財務危機影響度追跡アプリは、スポンサーの付いた研究プログラムやプロジェクトに関連するデータを収集することを目的としています。 研究者はアプリを使用して、助成金、従業員、給与期間ごとに整理された、予想される失われた労力と損失の理由を提出することができます。

Power BI を使用して、アプリのデータを分析して視覚化できます。 この記事で説明する Power BI のテンプレートは、高等教育機関の財務危機影響度追跡アプリで収集されたデータを取り込みます。

これらのレポートは、各部局、スポンサー、大学や学校に代わって収集されたデータを監視する管理者、学部長、研究管理者が使用することを目的としています。

## <a name="prerequisites"></a>前提条件

高等教育機関の財務危機影響度追跡アプリは、Common Data Service のデータをこの Power BI のテンプレートに取り込み、 Power BI、Dynamics 365、 Power Automateなどの他のビジネス アプリで使用するためのデータを安全に保存、統合、自動化することを可能にします。

この Power BI テンプレートを使用するには、これらの前提条件が必要となります :

-  無料版  [Power BI Desktop](https://powerbi.microsoft.com/desktop/)  アプリをダウンロードします。

-   [Power BI サービス](https://powerbi.microsoft.com/get-started/) にサインアップします。

-  ポータルにアクセスするための作成者権限と、エンティティ内のデータにアクセスするための読み取り権限を持つ Common Data Service 環境を作成します。

Power BI ダッシュボードは以下の 2 つの方法で構成できます :

* [空白のレポート キャンバスを使用する](#configure-from-blank-report-canvas)
* [Power BI テンプレートを使用する](#using-power-bi-template)

## <a name="configure-a-power-bi-report-by-using-a-blank-report-canvas"></a>空のレポートキャンバスを使用して Power BI レポートを構成する<a name="configure-from-blank-report-canvas"></a>

空のレポートキャンバスを使用して Power BI レポートを構成する方法 :

1. Power BI Desktop を開きます。 それ以外の場合は、職場または学校のアカウントを使用して、Power BI サービスに **サインイン** が求められる場合があります。

   > [!div class="mx-imgBorder"]
   > ![Power BI Desktop](./media/powerbidesktop.png "Power BI Desktop")

2. **データの取得** > **Power Platform** > **Common Data Service** を選択し、続いて**接続**を選択します。
  
   > [!div class="mx-imgBorder"]
   > ![[データの取り出し]](./media/pbigetdata1.png "データの取得")

   > [!div class="mx-imgBorder"]
   > ![[データの取り出し]](./media/pbigetdata.png "データの取得")

3. ご利用の Common Data Service 環境に固有となる **サーバーの URL** を入力してください。 Common Data Service 環境の URL を取得するには、次の手順を実行してください :

   1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) を開き、接続する環境を選択し、右上隅の **設定** を選択し、続いて **高度な設定**を選択します。

   2. 開いた新しいブラウザタブで、URL のルート部分をコピーします。 これは、環境固有の URL です。 URL の形式は次のようになります : <https://yourenvironmentid.crm.dynamics.com/> 残りの URL はコピーしないでください。

    > [!div class="mx-imgBorder"]
    > ![Common Data Service 環境](./media/cdsenvironment.png "Common Data Service 環境")

    > [!div class="mx-imgBorder"]
    > ![サービス URL](./media/ppserviceurl.png "サービス URL")

4. 環境に正常に接続すると、**ナビゲーター**内に**エンティティ**、**システム**のフォルダが表示されます。 **エンティティ**を展開し、次のエンティティのチェック ボックスをオンにします :

   - 取引先企業 

   - 取引先担当者 

   - msft_Campus

   - msft_College

   - msft_Department

   - msft_EmployeeCompensation

   - msft_Grant

   - msft_LossReason

   - msft_PayPeriod

   - msft_SponsoredProgram


    > [!div class="mx-imgBorder"]
    > ![エンティティの選択](./media/chooseentities.png "エンティティの選択")

5. エンティティのリストを選択してから、**データの変換**を選択します。 クエリ エディターのウィンドウが開き、選択したテーブルとデータが読み込まれます。
  
   > [!div class="mx-imgBorder"]
   > ![テーブルの選択](./media/selecttables.png "テーブルの選択")

6. 各エンティティごとに、リボンで**列の選択**を選択してコンソールを開き、データ モデルとレポートで使用するフィールドを選択します。<!--Please note that images should never include information that isn't also available in text, either the main content or alt text.  This is an accessibility requirement. Unfortunately, some of these lists are too long for alt text (which has a maximum of 220 characters), so I've converted them to lists. I'd appreciate your double-checking that they're accurate.-->

   > [!div class="mx-imgBorder"]
   > ![列の選択](./media/choosecolumn.png "列の選択")

   - 以下が連絡先エンティティに推奨されるフィールドです :
      - msft_annualbasesalary
      - msft_annualbasesalary_base
      - msft_annualtuitionreimbursement
      - msft_annualtuitionreimbursement_base
      - msft_contacttype
      - msft_department
      - msft_employmentclass
      - msft_showwelcomemessage
      - msft_userid

   - 以下が msft_Campus エンティティに推奨されるフィールドです :
      - msft_campusdescription
      - msft_campusid
      - msft_campusname

   - 以下が msft_College エンティティに推奨されるフィールドです :
      - msft_campus
      - msft_collegedescription
      - msft_collegeid
      - msft_collegename

   - 以下が msft_Department エンティティに推奨されるフィールドです :
      - msft_college
      - msft_departmentdescription
      - msft_departmentid
      - msft_departmentname

   - 以下が msft_EmployeeCompensation エンティティに推奨されるフィールドです :
      - msft_effortamount
      - msft_effortamount_base
      - msft_effortpercentage
      - msft_employee
      - msft_employeecompensationid
      - mstf_fte
      - msft_lossamount
      - msft_lossamount_base
      - msft_losspercentage
      - msft_lossreason
      - msft_name
      - msft_paygroup
      - msft_paygroup_display
      - msft_payperiod
      - msft_payrate
      - msft_payrate_base
      - msft_sponsoredprogram

   - 以下が msft_Grant エンティティに推奨されるフィールドです :
      - msft_enddate
      - msft_grantdescription
      - msft_grantid
      - msft_grantnumber
      - msft_grantstatus
      - msft_grantstatus_display
      - msft_granttitle
      - msft_principalinvestigator
      - msft_startdate

   - 以下が msft_LossReason エンティティに推奨されるフィールドです :
      - msft_lossreasoncode
      - msft_lossreasondescription
      - msft_lossreasonid

   - 以下が msft_PayPeriod エンティティに推奨されるフィールドです :
      - msft_enddate
      - msft_payperiodcode
      - msft_payperioddescription
      - msft_payperiodid
      - msft_startdate

   - 以下が msft_SponsoredProgram エンティティに推奨されるフィールドです :
      - msft_availablebalance
      - msft_availablebalance_base
      - msft_awardamount
      - msft_awardamount_base
      - msft_coprincipalinvestigator
      - msft_department
      - msft_effortlossimpactamount
      - msft_effortlossimpactamount_base
      - msft_effortlossimpactamount_date
      - msft_effortlossimpactamount_state
      - msft_effortlossimpactpercentage
      - msft_grant
      - msft_primesponsorname
      - msft_sponsoredprogramdescription
      - msft_sponsoredprogramid
      - msft_sponsoredprogramnumber
      - msft_sponsorname

<!--
 - Here are suggested fields for each Entity:

     - Contact
      > [!div class="mx-imgBorder"]
      > ![Contact](./media/contact.png "Contact")

     - msft_Campus
      > [!div class="mx-imgBorder"]
      > ![Campus](./media/msftcampus.png "Campus")

     - msft_College
       > [!div class="mx-imgBorder"]
       > ![College](./media/msftcollege.png "College")

     - msft_Department
       > [!div class="mx-imgBorder"]
       > ![Department](./media/msftdepartment.png "Department")

     - msft_EmployeeCompensation
       > [!div class="mx-imgBorder"]
       > ![Employee Compensation](./media/msftemployeecomp.png "Employee Compensation")

    - msft_Grant

     ![Grant](./media/msftgrant.png)

    - msft_LossReason
      > [!div class="mx-imgBorder"]
      > ![Loss Reason](./media/msftlossreason.png "Loss Reason")

    - msft_PayPeriod
      > [!div class="mx-imgBorder"]
      > ![Pay Period](./media/msftpayperiod.png "Pay period")

    - msft_SponsoredProgram
      > [!div class="mx-imgBorder"]
      > ![Sponsored Program](media/msftsponsoredprogram.png "Sponsored Program")
-->

7. **閉じて適用**を選択してクエリ エディターを閉じ、行った変更を適用します。

8. Power BI レポート キャンバスに次の画面が表示されます。 クエリの実行には数分かかる場合があります。

   > [!div class="mx-imgBorder"]
   > ![閉じて適用する](./media/closeandapply.png "閉じて適用する")

9. 変更が適用された後、Power BI レポート キャンバスは、ページ右側のパネル上の**フィールド**に一覧表示されるテーブルを含めて、次のスクリーンショットのように表示されます。

   > [!div class="mx-imgBorder"]
   > ![適用されたレポート](./media/appliedreport.png "適用されたレポート")

10. ページの左側にあるアイコンを選択して、**モデル**ビューを開きます。 選択したテーブルが表示されます。 右下隅のスライダーを使用して、ビューのサイズを調整します。

    > [!div class="mx-imgBorder"]
    > ![モデル ビューを開く](./media/clickleft.png "モデル ビューを開く")

    > [!div class="mx-imgBorder"]
    > ![テーブル](./media/tables.png "テーブル")

11. **ホーム**タブを開き、**関連付けを管理する**を選択して、エンティティ間で新たな関連付けを作成するコンソールを開きます。

    > [!div class="mx-imgBorder"]
    > ![レポート名のホーム](./media/reporthome.png "レポート名のホーム")

    エンティティ間で関連付けを作成、または編集する際は、関連付けに使用する**濃度**と**クロス フィルター**の方向性に加えて、結合するテーブルとカラムを選択します。

    > [!div class="mx-imgBorder"]
    > ![関連付けの作成](./media/createrelationship.png "関連付けの作成")

13. Power BI のテンプレートに関連付けられた Common Data Service の推奨フィールドを使用する場合、テーブル間の関連付けのマッピングは以下のようになります。

     |関連付け元 : テーブル | 関連付け先 : テーブル | 
     |---|---|---|
     | msft_College (msft_campus) | msft_Campus (msft_campusid) |
     | msft_Department (msft_college) | msft_College (msft_collegeid) |
     | msft_EmployeeCompensation (msft_lossreason) | msft_LossReason (msft_lossreasonid) |
     | msft_EmployeeCompensation (msft_payperiod) | msft_PayPeriod (msft_payperiodid) |
     | msft_EmployeeCompensation (msft_sponsoredprogram) | msft_SponsoredProgram (msft_sponsoredprogramid) |
     | msft_SponsoredProgram (msft_coprincipalinvestigator) | Contact (contactid) |
     | msft_SponsoredProgram (msft_department) | msft_Department (msft_departmentid) |
     | msft_SponsoredProgram (msft_grant) | msft_Grant (msft_grantid) |

    > [!div class="mx-imgBorder"]
    > ![関連付けの管理](./media/managerelationship.png "関連付けの管理")

次のスクリーンショットは、モデル ビューのエンティティの関係図を示しています。

  > [!div class="mx-imgBorder"]
  > ![エンティティの関連付け](./media/entityrelationshipdiagram.png "エンティティの関連付け")

## <a name="configure-a-power-bi-report-by-using-a-power-bi-template"></a>Power BI テンプレートを使用して Power BI レポートを構成する<a name="using-power-bi-template"></a>

Power BI のテンプレートには、.pbixファイル形式のサンプル データとインタラクティブ グラフィックが含まれており、さらに Power BI Desktop で編集と更新が可能です。 [GitHub](https://github.com/microsoft/powerapps-tools/blob/master/Apps/CrisisFinancialImpactTracker/PBITemplate.pbix) からテンプレートをダウンロードします。

### <a name="open-the-power-bi-template"></a>Power BI テンプレートを開く

テンプレートを開くと、Power BIスプラッシュ スクリーンが表示されます。 または、職場や学校のアカウントを使用して、Power BI サービスに **サインイン** が求められる場合があります。

Power BI のテンプレートを開くと、レポートの下部に以下一連のタブが表示されます :

- **法的** : Microsoft の法的免責事項が含まれています。
- **ホーム**: 好みに応じて変更可能なサンプル テキストを収録しています。 
- **情報** : 一般的な情報が含まれています。
- **FAQ** : よく寄せられる質問が含まれています。
- **提出物** : **提出レポート**ページを開きます。

- **スポンサー** : **スポンサー レポートによる影響**ページを開きます。

- **部門** : **部門**ビューを開きます。

組織は、ページに画像を挿入し、他のページにコピーすることにより、テンプレート内のすべてのページにそのロゴを追加することができます。 詳細 : [レポートの視覚化をコピーして貼り付ける](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-copy-paste)

## <a name="connect-to-common-data-service"></a>Common Data Service への接続

高等教育機関の財務危機影響度追跡アプリが収集した独自のデータを使用するには、テンプレート内のデータ接続を更新する必要があります。 詳細 : [Common Data Service コネクタを使用して Power BI レポートを作成する](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-powerbi-connector)

データ ソースを変更するには、**データの変換**を選択してクエリ エディターを開きます。 クエリ エディターの**適用されたステップ**で、エンティティごとに**ソース**を変更します。 Common Data Service 環境の URL を使用します。 

## <a name="issues-and-feedback"></a>問題とフィードバック 

- Higher Education Crisis Financial Impact Tracker アプリの問題を報告するには、<https://aka.ms/crisis-financial-impact-tracker-issues> にアクセスしてください。
- Higher Education Crisis Financial Impact Tracker アプリに関するフィードバックについては、<https://aka.ms/crisis-financial-impact-tracker-feedback> にアクセスしてください。


