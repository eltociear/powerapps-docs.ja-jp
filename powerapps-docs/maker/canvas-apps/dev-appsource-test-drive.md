---
title: AppSource で顧客がキャンバス アプリを体験できるようにする | Microsoft Docs
description: AppSource を使用して、顧客とキャンバス アプリを共有し、潜在顧客を創出します。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/08/2017
ms.author: litran
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 324c7880643a6e06bc147d1bbafb1b9638b8f2ec
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3305648"
---
# <a name="let-customers-test-drive-your-canvas-app-on-appsource"></a>AppSource で顧客がキャンバス アプリを体験できるようにする

Power Apps でのキャンバス アプリの作成に関心がありますか? キャンバス アプリを顧客と共有したいですか? [AppSource.com](https://appsource.microsoft.com) は顧客とアプリを共有し、潜在顧客を創出する手段として、Power Apps 体験版ソリューションをサポートしています。

## <a name="what-is-a-test-drive-solution"></a>体験版ソリューションとは何ですか?

体験版ソリューションを使用すると、顧客は Power Apps プランにサインアップしたり、アプリケーションをインストールしたりせずに、実際のアプリを試すことができます。 顧客は、Azure Active Directory (AAD) アカウントを使用して AppSource.com にサインインして、Web ブラウザーでアプリを実行するだけです。 体験版がなければ、顧客はアプリに関する説明を読んだり、ビデオを見たりするしかありません。 体験版を使用すると、ソリューションの内容やアプリの機能についてよく理解することができます。 そして、アプリを実際に使用する経験を持つことができます。 顧客がアプリの内部の構築方法を見ることはできないため、無体財産権は保護されます。 体験版アプリを起動するユーザーについて、潜在顧客の情報を収集して共有し、ビジネスの成長に役立てます。

AppSource.com の[アプリ一覧](https://go.microsoft.com/fwlink/?linkid=848867)の例です。

![サンプル AppSource 一覧 ](./media/dev-appsource-test-drive/sample-app-source-listing.png)

**無料試用版**リンクを上のアプリ一覧から選択すると、関連付けられた Power Apps 体験版アプリがユーザーのブラウザーで直接起動されます。

![サンプル アプリ Web プレーヤー](./media/dev-appsource-test-drive/sample-app-web-player.png)

## <a name="how-do-i-build-a-test-drive-solution"></a>体験版ソリューションを構築するにはどうすればよいですか?
体験版ソリューション用のアプリの構築は、Power Apps でアプリを構築する方法と同じですが、外部データ接続の代わりに埋め込みデータを使用します。 埋め込みデータを使用すると、アプリを顧客に展開する際の障壁が軽減されるため、顧客が試してみる際の摩擦がなくなります。最終的に顧客に配布する完全なソリューションには、通常、データ接続が含まれますが、埋め込みデータは、体験版ソリューションに適しています。

Power Apps では、埋め込みデータによるアプリの構築がネイティブにサポートされるため、アプリで使用するサンプル データのみが必要になります。 このデータは Excel ファイルに 1 つ以上のテーブルとしてキャプチャする必要があります。 Power Apps は、外部接続を介する代わりに、Excel テーブルからデータをアプリに取得して処理します。 この後の 3 つの手順のプロセスで、アプリにデータを取得して使用する方法を説明します。

### <a name="step-1-import-data-into-the-app"></a>手順 1: アプリにデータをインポートする
2 つのテーブル **SiteInspector** と **SitePhotos** を含む Excel ファイルがあるとします。

![インポートする Excel テーブル](./media/dev-appsource-test-drive/excel-file.png)

オプション **静的データをアプリに追加します**を使用して、これら 2 つのテーブルを Power Apps にインポートします。

![静的データをアプリに追加します](./media/dev-appsource-test-drive/static-data.png)

これでアプリのデータ ソースとしてテーブルが追加されました。

![データ ソースとしてインポートされた Excel テーブル](./media/dev-appsource-test-drive/data-sources.png)

### <a name="step-2-handling-read-only-and-read-write-scenarios"></a>手順 2: 読み取り専用シナリオと読み取り/書き込みシナリオを扱う
インポートしたデータは、*静的*つまり読み取り専用です。 アプリが読み取り専用の場合 (ユーザーへのデータの表示のみを行うアプリなど)、アプリ内でテーブルを直接参照します。 たとえば、**SiteInspector** テーブルの**タイトル** フィールドにアクセスする場合、式で **SiteInspector.Title** を使用します。

アプリが読み取り/書き込みの場合は、最初に各テーブルのデータを*コレクション*に取得します。これは Power Apps の表形式データ構造です。 その後、テーブルではなくコレクションを処理します。 **SiteInspector** テーブルと **SitePhotos** テーブルから **SiteInspectorCollect** コレクションと **SitePhotosCollect** コレクションにデータを取得するには、次のようにします。

```powerapps-dot
ClearCollect( SiteInspectorCollect, SiteInspector ); 
ClearCollect( SitePhotosCollect, SitePhotos )
```

この式では、両方のコレクションがクリアされてから、各テーブルのデータが対応するコレクションに収集されます。

* アプリのどこかでこの式を呼び出して、データを読み込みます。
* アプリのすべてのコレクションを表示するには、**ファイル** > **コレクション**に移動します。
* 詳細については、[アプリのコレクションの作成と更新](../canvas-apps/create-update-collection.md)を参照してください。

ここで、**タイトル** フィールドにアクセスする場合は、式で **SiteInspectorCollect.Title** を使用します。

### <a name="step-3-add-update-and-delete-data-in-your-app"></a>手順 3: アプリのデータを追加、更新、削除する
これまで、データを直接読み取る方法とコレクションから読み取る方法を説明しました。次は、コレクションのデータの追加、更新、削除を行う方法について説明します。

**行をコレクションに追加する**には、[Collect( DataSource, Item, ... )](../canvas-apps/functions/function-clear-collect-clearcollect.md) を使用します。

```powerapps-dot
Collect( SiteInspectorCollect,
    {
        ID: Value( Max( SiteInspectorCollect, ID ) + 1 ),
        Title: TitleText.Text,
        SubTitle: SubTitleText.Text,
        Description: DescriptionText.Text
    }
)
```

**コレクションの行を更新する**には、[UpdateIf( DataSource, Condition1, ChangeRecord1 [, Condition2, ChangeRecord2, ...] )](../canvas-apps/functions/function-update-updateif.md) を使用します。

```powerapps-dot
UpdateIf( SiteInspectorCollect,
    ID = record.ID,
    {
        Title: TitleEditText.Text,
        SubTitle: SubTitleEditText.Text,
        Description: DescriptionEditText.Text
    }
)
```

**コレクションから行を削除する**には、[RemoveIf( DataSource, Condition [, ...] )](../canvas-apps/functions/function-remove-removeif.md) を使用します。

```powerapps-dot
RemoveIf( SiteInspectorCollect, ID = record.ID )
```

> [!NOTE]
> コレクションにデータが保持されるのはアプリが実行している間だけです。アプリが終了すると、すべての変更は破棄されます。

要約すると、埋め込みデータを使用してアプリのバージョンを作成できます。これは、外部データに接続するアプリのエクスペリエンスをシミュレーションします。 データを埋め込んだら、そのアプリを体験版ソリューションとして AppSource.com に公開する準備が整いました。

## <a name="how-do-i-list-my-test-drive-solution-on-appsourcecom"></a>体験版ソリューションを AppSource.com に登録する方法
以上でアプリの準備が整ったので、AppSource.com に公開します。 このプロセスを開始するには、Power Apps.com にある[アプリケーション フォーム](https://powerapps.microsoft.com/partners/get-listed/)に必要事項を入力してください。

申し込みの完了後は、AppSource.com でアプリを公開する送信手順が記載された電子メールが届きます。 また、すべての過程を詳しく説明しているオンボーディング ドキュメントは、[こちらから](https://go.microsoft.com/fwlink/?linkid=851031)ダウンロードできます。

