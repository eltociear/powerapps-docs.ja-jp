---
title: ネイティブ Common Data Service コネクタを使用するようにアップグレードする | Microsoft Docs
description: ''
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/03/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e77bf1304ac7d1083348dce18d7d78189dfef306
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "3308109"
---
# <a name="common-data-service-and-the-improved-data-source-experience"></a>Common Data Service および強化されたデータ ソース エクスペリエンス

## <a name="overview"></a>概要

2019 年 11 月より前に Common Data Service コネクタを使用してキャンバス アプリを作成した場合、Common Data Service の最新バージョンの利点がない可能性があります。 

**強化されたデータ ソース エクスペリエンスおよび Common Data Service ビュー**のオプションには次の利点があります。

1. 大幅な速度向上。
2. 信頼性の向上。
3. Common Data Service **ビュー**および**ファイルと画像フィールドの属性**にアクセスします。

**強化されたデータ ソース エクスペリエンスと Common Data Service ビュー**のオプションが詳細設定セクションに表示されます。

![強化されたデータ ソース エクスペリエンスおよび Common Data Service ビュー](media/use-native-cds-connector/improved-data-source-setting.png)

**リレーショナル データ、オプション セット、および Common Data Service の他の新機能**は、非推奨機能セクションに表示されます。

## <a name="how-do-i-upgrade"></a>アップグレードするには?

機能の設定を調べ、以下の指示に従ってアプリをアップグレードします。

### <a name="improve-data-source-experience-and-common-data-service-views-is-on"></a>*強化されたデータ ソース エクスペリエンスおよび Common Data Service ビュー*がオンになっています。

この機能を使用するようにキャンバス アプリを既に変換しているか、この機能の既定の設定を*オン*にしてアプリを起動しました。 これ以降のアクションは不要です。 

また、**明示的な列の選択**機能を有効にすることもできます。

![明示的な列の選択](media/use-native-cds-connector/explicit-column-selection.png)

> [!NOTE]
> **強化されたデータ ソース エクスペリエンスおよび Common Data Service ビュー**は、[Windows 用 Power Apps](https://www.microsoft.com/p/power-apps/9nblggh5z8f3) ではサポートされていません。 Windows 用 Power Apps を使用する際には、この機能を*オフ*にする必要があります。

### <a name="relational-data-option-sets-and-other-new-features-for-common-data-service-is-off"></a>*リレーショナル データ、オプション セット、Common Data Service のその他の新機能*はオフになっています。

*非推奨機能*セクションの下にある*詳細設定*を確認してください。  *オフ*に設定されている場合、変換の最初のステップとして次の手順に進みます。 

> [!IMPORTANT]
> *詳細設定*にある**リレーショナル データ、オプション セット、Common Data Service のその他の新機能**が表示されない場合、または既に*オン*になっている場合は、以下の手順をスキップして[次のセクション](#improve-data-source-experience-and-common-data-service-views-is-off)に進みます。

- **ステップ 1**: **表示名の使用**機能を**オン**にします。
    
    1. **表示名の使用**機能を*オン*にします。
    1. ヘルス モニターがアプリの分析を完了するまで待ちます。
    1. アプリを保存し、閉じて、再度開きます。
    1. すべての数式エラーを解決します。
    1. アプリを保存し、閉じて、再度開きます。
    
    *考えられるエラーと提案*:
    
    新しく表示された表示名の一部が、他のエンティティ、フィールド、またはコントロールの表示名と競合する可能性があります。 たとえば、同じ名前のコントロールとフィールドがあるとします。 修正する一意の値でコントロールの名前を変更できます。
    
    フィールドとエンティティの表示名の競合については、エンティティを想定しながらもローカル スコープのフィールド名に解決される式が表示される場合があります。

    角かっこと **@** 記号を使用してグローバル スコープを示し、エンティティに解決するようにします。たとえば、**[@entityName]** などです。
    
    
- **Step 2**: **リレーショナル データ、オプション セット、Common Data Service のその他の新機能**および**文字列の代わりに GUID データ型を使用する**の機能を**オン**にします。
    
    1. **リレーショナル データ、オプション セット、Common Data Service のその他の新機能**を*オン*にします。
    1. **文字列の代わりに GUID データ型を使用する**機能を*オン*にします。
    1. ヘルス モニターがアプリの分析を完了するまで待ちます。
    1. すべての数式エラーを解決します。
    1. アプリを保存し、閉じて、再度開きます。  
    
    *考えられるエラーと提案*:
    
    オプション セット フィールドまたはハードコーディングされた GUID テキスト値を使用している場合、この段階でエラーが発生する可能性があります。  <br><br> 
    
    - *オプション セットの値*: オプション セット値のテキスト識別子を含むオプション セット フィールドを使用している場合は、代わりにドット表記を使用してオプション セット値を参照してください。 たとえば、`Patch(Accounts, OptionSet1 = “12345”)` を `Patch(Accounts, OptionSet.Item1)` に変更します。ここで、`Item1` は `12345` 値に対応します。 <br>
    詳細については、[詳細例](#detailed-examples)のセクションを参照してください。
    - *GUID*: `015e45e1044e49f388115be07f2ee116` などの静的 GUID 文字列を使用している場合は、たとえば `GUID(“015e45e1044e49f388115be07f2ee116”)` など、GUID オブジェクトを返す関数に変換します。 
    - *ルックアップ*: Lookup 関数を使用して、`Lookup(Contacts, ‘contactID’ = ThisItem.ContactID”)` などの第 1 レベルのルックアップ値を取得する場合は、代わりに `ThisItem.PrimaryContacts` (PrimaryContacts がエンティティの名前) を使用することを検討してください。

### <a name="improve-data-source-experience-and-common-data-service-views-is-off"></a>*データ ソース エクスペリエンスおよび Common Data Service ビューの向上*がオフになっています。

次の手順に従って、**強化されたデータ ソース エクスペリエンスおよび Common Data Service ビュー**の機能を*オン*にします。

1. 既存の Common Data Service データ ソース接続を削除します。 
1. **強化されたデータ ソース エクスペリエンスおよび Common Data Service ビュー**の機能を*オン*にします。
1. 新しいデータ ソース選択エクスペリエンスを使用して、Common Data Service 接続を追加します。
1. アプリケーションを保存します。

> [!NOTE]
> アプリケーションが非常に大きい場合は、データ ソース接続を元に戻すのにしばらく時間がかかることがあります。 このプロセス中はアプリケーションを閉じないでください。

## <a name="converting-canvas-apps-with-the-dynamics-365-connector"></a>Dynamics 365 Connector を使用したキャンバス アプリの変換

Dynamics 365 Connector を使用するアプリを変換するには、データ ソースへの接続を削除して追加する必要があります。 以下の手順を使用して、接続をデータ ソースに変換します。

1. **強化されたデータ ソース エクスペリエンスおよび Common Data Service ビュー**の機能が*オン*になっていることを確認してください。
2. 既存の Dynamics 365 データ ソース接続を削除します。
3. 新しいデータ ソース選択エクスペリエンスを使用して、データ ソースへの接続を Common Data Service に追加します。 

    > [!NOTE] 
    > 他の環境 (現在の環境以外) に接続している場合は、*エンティティ* カテゴリ、次に*詳細* (...) オプションを選択して環境を変更します。 次に、別の環境からエンティティを選択して、アプリケーションに追加します。 クロステナント接続は、改善されたネイティブ コネクタでは機能しません。 データのクロステナントにアクセスするには、データ統合を使用する必要があります。
4.  アプリケーションを保存します。

*考えられるエラーと提案*:

表示名を使用していない、GUID 文字列を使用している、またはオプション セット フィールドを使用している場合、変換時にエラーが発生する可能性があります。

- コントロール名が競合する場合は、コントロール名を異なる一意の名前に変更してください。 
- フィールドとエンティティの表示名の競合については、エンティティを想定しながらもローカル スコープのフィールド名に解決される式が表示される場合があります。 角かっこと *@* 記号を使用してグローバル スコープを示し、エンティティに解決するようにします。たとえば、**[@entityName]** などです。
- *オプション セットの値*: オプション セット値のテキスト識別子を含むオプション セット フィールドを使用している場合は、代わりにドット表記を使用してオプション セット値を参照してください。 たとえば、`Patch(Accounts, OptionSet1 = “12345”)` を `Patch(Accounts, OptionSet.Item1)` に変更します。ここで、`Item1` は `12345` 値に対応します。 <br>
詳細については、[詳細例](#detailed-examples)のセクションを参照してください。
- *GUID*: `015e45e1044e49f388115be07f2ee116` などの静的 GUID 文字列を使用している場合は、たとえば `GUID(“015e45e1044e49f388115be07f2ee116”)` など、GUID オブジェクトを返す関数に変換します。 
- *ルックアップ*: Lookup 関数を使用して、`Lookup(Contacts, ‘contactID’ = ThisItem.ContactID”)` などの第 1 レベルのルックアップ値を取得する場合は、代わりに `ThisItem.PrimaryContacts` (PrimaryContacts がエンティティの名前) を使用することを検討してください。
- ポリモーフィック参照については、以下の詳細例のセクションを参照してください。 

## <a name="detailed-examples"></a>詳細例

アプリを変換して新しい**オプション セット**と **2 つのオプション**のデータ型をサポートするコントロールで使用すると、アプリをアップグレードして*強化されたデータ ソース エクスペリエンスと Common Data Service ビュー*の機能を使用するのが困難になる場合があります。

### <a name="option-sets"></a>オプション セット

以前のオプション セットでは、個別の `_myfield` と `_myfield_label` フィールドが使用されていました。 現在、ロケールに依存しない比較とロケール固有のラベル取得の両方に使用できる単一の `myfield` があります。

#### <a name="removing-and-adding-option-set-data-cards"></a>オプション セット データ カードの削除と追加

既存のデータ カードを削除し、オプション セットで使用するよう再度追加することをお勧めします。 たとえば、取引先企業エンティティとカテゴリ オプション セットを使用している場合は、`_accountcategorycode_label` に設定されているデータ カードの *DataField* プロパティが表示されます。 フィールド リストで、データ カードのタイプが*文字列*であることがわかります。

![古いスタイル名の OptionSet](./media/use-native-cds-connector/OptionSet-with-old-style-name.png)

新しい*強化されたデータ ソース エクスペリエンスと Common Data Service ビュー*の機能がある場合、`_accountcategorycode_label` は表示されません。 `accountcategorycode` に置き換えられます。 カードが**カスタム**としてマークされ、エラーが表示されます。 古いデータ カードを取り外し、*オプション セット* を再度追加します。 新しいデータ カードは*オプション セット*対応です。

![古いスタイル名の OptionSet](./media/use-native-cds-connector/OptionSet-with-new-style-name.png)

#### <a name="editing-the-option-set-filter-expressions-to-use-new-syntax"></a>新しい構文を使用するためのオプション セット フィルター式の編集

以前は、フィルター式でオプション セット値を使用したい場合は、*値*フィールドが必要でした。 たとえば、次のようなものです。

```powerapps-dot
Filter(Account,'Category Value' = "1")
```

この式を編集する必要があります。 オプション セット テキスト識別子は値に使用されなくなりました。 この式は、以下を検索するように更新する必要があります。

```powerapps-dot
Filter(Account, Category= ‘Category (Accounts)’.’Preferred Customer’)
```

'Category(Accounts)' は、取引先企業エンティティのカテゴリ フィールドに使用される列挙値の名前です。 これはローカル オプション セットです。  ローカルおよびグローバル オプション セットの詳細については、[グローバル オプション セット](https://docs.microsoft.com/powerapps/maker/common-data-service/create-edit-global-option-sets) を参照してください。

#### <a name="editing-option-set-patch-statements-to-use-new-syntax"></a>新しい構文を使用するためのオプション セット パッチ ステートメントの編集

以下は、以前のオプション セットのパッチ ステートメントの例です。

```powerapps-dot
Patch( Accounts, First(Accounts), { ‘Category Value’: 1 } ) )
```

このフォームに従うようにステートメントを更新する必要があります。

```powerapps-dot
Patch( Accounts, First(Accounts), { Category: ‘Category (Accounts)’.’Preferred Customer’ } )
```

#### <a name="option-set-disambiguation"></a>オプション セットの曖昧性除去

オプション セット **フィールド**の表示名とオプション セットの名前が同じ場合、数式の曖昧性を解消する必要があります。 取引先企業カテゴリ コードの例を引き続き使用するには、**@** は、フィールドではなくオプション セットを使用することを意味します。

```powerapps-dot
Filter(Accounts, 'Category Code' = [@’Category Code’].'Preferred Customer')
```

### <a name="two-options"></a>2 つのオプション

#### <a name="removing-and-adding-two-option-set-data-cards"></a>2 つのオプション セット データ カードの削除と追加

既存のデータ カードを削除し、2 つのオプション セットを使用するよう再度追加することをお勧めします。 データ型は、以前は単純なブール値として認識されていました - たとえば、ラベルなしの true/on や false/off などです。

![2 つのオプション セット - 古いスタイル](./media/use-native-cds-connector/TwoOptionSet-Old.png)

新しい*強化されたデータ ソース エクスペリエンスと Common Data Service ビュー*機能では、カードは**カスタム**とマークされ、エラーが表示されます。  古いデータ カードを取り外し、オプション セットを再度追加します。 追加すると、既定で 2 つのオプションを持つ編集コントロールが表示されます。

![TwoOptionSet-New](./media/use-native-cds-connector/TwoOptionSet-New.png)

ブール値のフィールドにトグル スイッチを使用する場合は、データ カードのロックを解除して、データ カードのコントロールをトグルに置き換えます。  また、トグルでこれらのプロパティを設定する必要があります。

```powerapps-dot
Toggle1.Default = ThisItem.’Do not allow Bulk Emails’
Toggle1.TrueText = ‘Do not allow Bulk Emails (Accounts)’.’Do Not Allow’
Toggle1.FalseText = ‘Do not allow Bulk Emails (Accounts)’.Allow
DataCard.Value = If( Toggle1.Value,
    ‘Do not allow Bulk Emails (Accounts)’.’Do Not Allow’,
    ‘Do not allow Bulk Emails (Accounts)’.Allow )
```

![2 つのオプション トグル スイッチ](./media/use-native-cds-connector/TwoOption-Toggle.png)

#### <a name="refining-two-option-patch-statements"></a>2 つのオプション パッチ ステートメントの絞り込み

[Patch](./functions/function-patch.md) 関数を 2 つのオプションと共に使用すると、そのまま動作します。 ブール値と同様に、true と false を直接使用できます。 唯一の違いは、true および false を示す値を以前の Label コントロールに配置した場合、代わりに 2 つのオプション ラベルが表示されることです。

### <a name="polymorphic-lookups"></a>ポリモーフィック ルックアップ

次のガイドラインは、[ポリモーフィック](working-with-references.md) フィールドを参照している場合に、アプリケーションをアップグレードするのに役立ちます。 同じフィールドからのポリモーフィック ルックアップは、制限された複数のエンティティのセットへの参照をサポートします。  他の言語の参照と同様に、レコード参照は、特定のエンティティの特定のレコードへのポインターです。 レコード参照にはエンティティ情報が含まれているため、他の複数のエンティティのレコードを参照することができます。これは、1つのエンティティのレコードのみを参照することができる通常の検索とは異なります。  

#### <a name="access-set-and-filter-on-the-owner-field-of-a-record"></a>レコードの所有者フィールドでのアクセス、設定、およびフィルター

たとえば、エンティティの所有者フィールドは、ユーザー エンティティまたはチーム エンティティのレコードを参照できます。 異なるレコードの同じ検索フィールドは、異なるエンティティのレコードを参照できます。
 
![ポリモーフィック所有者フィールド](./media/use-native-cds-connector/Polymorphic1.png)
 
##### <a name="polymorphic-with-filter-and-patch"></a>フィルターとパッチを持つポリモーフィック

レコード参照は、完全なレコードと同じように使用できます。

```powerapps-dot
Filter( Accounts, Owner = First( Teams ) )
Patch( Accounts, First( Accounts ), { Owner: First( Users ) })
```

##### <a name="polymorphic-with-a-gallery-displaying-owner-name"></a>所有者名を表示するギャラリーを持つポリモーフィック

参照は異なるエンティティを指すことができるので、具体的にする必要があります。 **チーム** エンティティの名前フィールドが**チーム名**であり、**ユーザー** エンティティの名前フィールドが**氏名**であるため、**ThisItem.Owner.Name** は使用できません。 Power Apps は、アプリを実行するまで、参照しているルックアップのタイプを認識しません。

この問題を解決するには、以下を行います。 

1. 所有者がなり得るエンティティの種類のデータ ソースを追加します。現在の例では、ユーザーとチームです)。
2. 追加の関数を使用して、意図を明確にします。

使用できる 2 つの新しい関数があります。

- IsType – レコード参照が特定のエンティティの種類であるかどうかを確認します。
- AsType – レコード参照を特定のエンティティの種類にキャストします。

これらの関数を使用すると、所有者のエンティティの種類に基づいて、2 つの異なる名前のフィールドから取得した所有者の名前を表示する式を記述できます。

```powerapps-dot
If( IsType( ThisItem.Owner,  [@Teams]), 
    AsType( ThisItem.Owner, [@Teams]).'Team Name', 
    AsType( ThisItem.Owner, [@Users]).'Full Name' )
```

![AsType を持つギャラリー](./media/use-native-cds-connector/Polymorphic-And-AsType-in-Gallery.png)

`[@Teams]` と `[@Users]` のグローバル曖昧性除去演算子を使用して、グローバル エンティティの種類を参照するようにします。 この場合は必須ではありませんが、常に明確にすることをお勧めします。 一対多のリレーションシップは、ギャラリーのレコード スコープで競合することがよくありますが、この操作を行うことで混乱を回避できます。
 
#### <a name="access-and-set-the-company-name-field-a-customer-data-type-of-the-contacts-entity"></a>取引先担当者エンティティの会社名フィールド (顧客データ型) にアクセスして設定する

顧客検索フィールドは、所有者に類似した別のポリモーフィック ルックアップです。 各エンティティには所有者フィールドを 1 つのみ設定できます。 ただし、エンティティには 0、1、またはそれ以上の顧客検索フィールドを含めることができます。 取引先担当者システム エンティティには、顧客検索フィールドである会社名フィールドが含まれています。 詳細については、[顧客フィールドを表示する](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#show-the-fields-of-a-customer)を参照してください。
 
#### <a name="access-and-set-the-regarding-field-of-activity-entities-such-as-faxes-phone-calls-email-messages"></a>FAX、電話、電子メール メッセージなどの活動エンティティの関連フィールドにアクセスして設定する

ポリモーフィック ルックアップは、取引先企業と取引先担当者に限定されません。 エンティティのリストは、カスタム エンティティで拡張できます。 たとえば、FAX エンティティには、取引先企業、取引先担当者、およびその他のエンティティを参照できるポリモーフィック関連検索フィールドがあります。 データ ソースが FAX に設定されているギャラリーを使用している場合は、次の数式を使用して、関連検索フィールドに関連付けられている名前を表示できます。 
 
 ```powerapps-dot
If( IsBlank( ThisItem.Regarding ), "",
    IsType( ThisItem.Regarding, [@Accounts] ),
        "Account: " & AsType( ThisItem.Regarding, [@Accounts] ).'Account Name',
    IsType( ThisItem.Regarding, [@Contacts] ),
        "Contacts: " & AsType( ThisItem.Regarding, [@Contacts] ).'Full Name',
    "" )
```

![関連付けギャラリー](./media/use-native-cds-connector/Polymorphic-With-Regarding.png)
 
詳細については、[検索フィールドに関して](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#understand-regarding-lookup-fields)および[リレーションシップに関して](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#understand-regarding-relationships)を参照してください。

#### <a name="access-the-list-of-all-activities-for-a-record"></a>レコードのすべての活動のリストにアクセスする

Common Data Service では、FAX、タスク、電子メール、メモ、電話、レター、チャットなどは、[活動](https://docs.microsoft.com/powerapps/developer/common-data-service/activity-entities)として指定されます。 独自の[カスタム活動エンティティ](https://docs.microsoft.com/powerapps/developer/common-data-service/custom-activities)を作成することもできます。

特定の種類の活動 (FAX や税金など)、または取引先企業などのエンティティに関連付けられているすべての活動を表示できます。 活動エンティティと、キャンバス アプリに表示する予定のデータを持つその他の個々のエンティティを追加します。

(たとえば、タスク エンティティに) レコードを追加するたびに、すべての活動エンティティに共通のフィールドを持つ活動エンティティのレコードが作成されます。 詳細については、[活動エンティティ](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#activity-entity)を参照してください。

次の例は、取引先企業を選択すると、その取引先企業に関連付けられているすべての活動が表示されることを示しています。
 
![ポリモーフィック活動](./media/use-native-cds-connector/Polymorphic-Activities.png) 
 
レコードは、活動エンティティから表示されています。 ただし、[IsType](./functions/function-astype-istype.md) 関数を使用して、それらがどのような種類の活動であるかを識別することができます。 この場合も、エンティティの種類で IsType を使用する前に、必要なデータ ソースを追加する必要があります。
 
この式を使用すると、ギャラリー内のラベル コントロールにレコードの種類を表示できます。

 ```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown")
```

 ![ポリモーフィック - IsType](./media/use-native-cds-connector/Polymorphic-IsType.png)

#### <a name="access-the-list-of-notes-for-a-record"></a>レコードのすべてのメモのリストにアクセスする

エンティティを作成する際に、添付ファイルを有効にできます。 添付ファイルを有効にするためのチェックボックスをオンにすると、次の図が取引先企業エンティティを示すように、メモ エンティティとの関連リレーションシップが作成されます。

![メモフィールド](./media/use-native-cds-connector/Notes-Field.png)

##### <a name="filtering"></a>フィルタリング

関連フィールドに基づいて読み取りまたはフィルター処理することはできません。 ただし、メモの一対多の逆の関係を使用できます。 取引先企業エンティティに関連付けられているすべてのメモを一覧表示するには、次の数式を使用します。

```powerapps-dot
First( Accounts ).Notes
```

##### <a name="patch"></a>Patch

パッチを使用してエンティティのメモ フィールドを設定することはできません。 エンティティのメモ テーブルにレコードを追加するには、Relate 関数を使用します。 この例のように、最初にメモを作成します。

```powerapps-dot
Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note", isdocument:'Is Document (Notes)'.No } ) )
```

## <a name="next-steps"></a>次の手順

- [数式のリファレンス](https://docs.microsoft.com/powerapps/maker/canvas-apps/formula-reference)
- [コントロールのリファレンス](https://docs.microsoft.com/powerapps/maker/canvas-apps/reference-properties)

### <a name="see-also"></a>関連項目

[Common Data Service とは?](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)
