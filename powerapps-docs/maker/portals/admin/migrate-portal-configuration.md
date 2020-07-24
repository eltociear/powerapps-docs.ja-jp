---
title: ポータル構成の移行 | MicrosoftDocs
description: ポータル構成の移行方法を説明します。
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/08/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: eb09a2f8c7045016cb60af0a48ab8853a7492c8d
ms.sourcegitcommit: 2fd873a1ea17f419f6194714efffa47a9bd00c2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "3507718"
---
# <a name="migrate-portal-configuration"></a>ポータル構成の移行

ポータル開発には、ポータル エンド ユーザーのための望ましいエクスペリエンスを実現するための、複数の構成およびカスタマイズが含まれます。

Portal インスタンスの開発または構成が完了した後、最新のポータル構成を、開発環境からテスト環境または運用環境へ移行することを希望する場合があります。 移行には、ソースの Common Data Service 環境からの既存の構成のエクスポートし、その後対象 Common Data Service 環境へのそのデータをインポートすることが含まれています。

構成データをエクスポートするには、Configuration Migration ツールおよびポータル固有の構成スキーマ ファイルを使用する必要があります。 このツールの詳細については、[構成データの管理](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-configuration-data)を参照してください。

> [!NOTE]
> - 最新のバージョンの Configuration Migration ツールの使用を推奨いたします。 構成移行ツールは NuGet からダウンロードすることができます。 ツールのダウンロードについては、 [NuGetからツールをダウンロード](https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget)を参照してください。
> - 構成移行のスキーマ ファイルでサポートされているポータルの最小バージョンのソリューションは、8.4.0.275 です。 ただし、最新バージョンのソリューションを使用することをお勧めします。

スキーマ ファイルは次のポータルの種類に対して使用することができます。

- **Common Data Service を備えた環境で作成されたポータル**
    - [カスタム ポータル (空白のポータル)](https://go.microsoft.com/fwlink/p/?linkid=2110477)

- **Dynamics 365 のモデル駆動型アプリを含む環境で作成されたポータル**
    - [カスタム ポータル (空白のポータル)](https://go.microsoft.com/fwlink/p/?linkid=2019804)
    - [コミュニティ ポータル](https://go.microsoft.com/fwlink/p/?linkid=2019704)
    - [顧客セルフサービス ポータル](https://go.microsoft.com/fwlink/p/?linkid=2019705)
    - [パートナー ポータル](https://go.microsoft.com/fwlink/p/?linkid=2019803)
    - [従業員セルフサービス ポータル](https://go.microsoft.com/fwlink/p/?linkid=2019802)

既定のスキーマ ファイルには、すべてのポータル エンティティ、関連付け、および各エンティティの一意性の定義に関する情報が含まれています。 詳細については、[ポータル構成データのエクスポート](#export-portal-configuration-data)を参照してください。

組織データをエクスポートした後、ターゲット環境にそれをインポートする必要があります。 詳細については、[ポータル構成データのインポート](#import-portal-configuration-data)を参照してください。

> [!NOTE]
> 構成移行ツールは、スキーマを使用して構成データをエクスポートおよびインポートします。 このツールでは、エンティティまたはエンティティ スキーマは移行されません。 構成データが選択したスキーマと一致しない場合、エンティティやフィールドなどの要素が欠落しているため、移行が失敗することがあります。
>
> エクスポート中に、構成移行ツールのスキーマ ファイルで指定されているポータル エンティティがソース環境に含まれていることを確認します。 スキーマ ファイルを変更し、エンティティ、属性などを追加、削除、変更して、構成データのサブセットを移行できます。
>
> インポート時に、インポート先の環境に、ソリューションとして個別にインポートされたエンティティ、フィールド、フォーム、あるいはビューなどの追加のカスタマイズが既にインストールされているポータルと同じ種類が含まれていることを確認します。


## <a name="export-portal-configuration-data"></a>ポータル構成データのエクスポート

ポータル構成データは、ポータル固有の構成データ スキーマ ファイルを使用して、ソース システムからエクスポートすることができます。

1.  Configuration Migration ツールをダウンロードして目的のフォルダーに解凍することができます。

2.  ユーザーのポータルの種類のために用意された上記のリンクを使用して、ポータル構成スキーマ ファイルをダウンロードします。

3.  **DataMigrationUtility.exe** ファイルを `<your_folder>\Tools\ConfigurationMigration` フォルダーでダブルクリックして、Configuration Migration ツールを実行し、メイン画面から**データのエクスポート**を選択し、**続行**を選択します。
    
    > [!div class=mx-imgBorder]
    > ![構成データのエクスポート](../media/export-config-data.png "構成データのエクスポート")

4.  **ログイン**画面で、認証の詳細を提供し、データのエクスポート元の Common Data Service 環境に接続します。 データのエクスポート元から Common Data Service 環境上に複数の組織を持っている場合、**使用可能な組織のリストを表示する**チェックボックスをオンにして、**ログイン**を選択します。

    > [!div class=mx-imgBorder]
    > ![データのエクスポート元から Common Data Service 環境へ接続するための認証の詳細を提供する](../media/export-config-login.png "データのエクスポート元から  Common Data Service 環境へ接続するための認証の詳細を提供する")

5.  複数の組織があり、**使用可能な組織の一覧を常に表示する**チェック ボックスを前のステップでオンにした場合、次の画面で接続する組織を選択することができます。 接続する Common Data Service 環境を選択します。 

    > [!NOTE]
    > 複数の組織がない場合、この画面は表示されません。

6.  **スキーマ ファイル**では、データのエクスポートに使用するポータル固有の構成スキーマ ファイルを参照して選択します。

7.  **データ ファイルに保存**では、エクスポートするデータ ファイルの名前および場所を指定します。

    > [!div class=mx-imgBorder]
    > ![スキーマと対象ファイルを指定します](../media/export-config-file-name.png "スキーマと対象ファイルを指定します")

8.  **データのエクスポート**を選択します。 クスポートが完了すると、画面の下部に、エクスポートの進行状況とエクスポートされたファイルの場所が表示されます。

    > [!div class=mx-imgBorder]
    > ![構成データのエクスポートの進行状況](../media/export-config-status.png "構成データのエクスポートの進行状況")

9.  **終了**を選択して、ツールを閉じます。

## <a name="import-portal-configuration-data"></a>ポータル構成データのインポート

1.  Configuration Migration ツールを実行してメイン画面で**データのインポート**を選択し、 **続行**を選択します。

    > [!div class=mx-imgBorder]
    > ![構成データのインポート](../media/import-config-data.png "構成データのインポート")

2.  **ログイン**画面で、認証の詳細を提供し、データのエクスポート元の Common Data Service 環境に接続します。 データのエクスポート元から Common Data Service 環境上に複数の組織を持っている場合、**使用可能な組織のリストを表示する**チェックボックスをオンにして、**ログイン**を選択します。

3.  複数の組織があり、**使用可能な組織の一覧を常に表示する**チェック ボックスを前のステップでオンにした場合、次の画面で接続する組織を選択することができます。 接続する Common Data Service 環境を選択します。 

    > [!NOTE]
    > - 複数の組織がない場合、この画面は表示されません。
    > - 構成をインポートする計画がある組織に、ポータル ソリューションがインストール済みであることを確認します。

4.  次の画面で、インポートするデータ ファイル (.zip) を指定するように求められます。 データ ファイルを参照して選択し、**データのインポート**を選択します。 

    > [!div class=mx-imgBorder]
    > ![構成データのインポートの進行状況](../media/import-config-status.png "構成データのインポートの進行状況")

5.  次の画面にレコードのインポートの状態が表示されます。 データのインポートは複数のパスで実行され、最初に依存データのキュー中に基盤データをインポートし、続くパスで依存データをインポートし、データ依存またはリンクを処理します。 これにより、クリーンで一貫性のあるデータ インポートができます。 

6.  **終了**を選択して、ツールを閉じます。 
