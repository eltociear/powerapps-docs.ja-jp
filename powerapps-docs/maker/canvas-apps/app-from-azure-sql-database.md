---
title: Azure SQL Database からキャンバス アプリを作成する | Microsoft Docs
description: Azure SQL Database のデータからキャンパス アプリを作成する方法について説明します
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/03/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 546746797ae02dce85cb0f2c161f4a7787938056
ms.sourcegitcommit: 37afeec92b1cda4f00c3e0071d82dd5259fc8278
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "3436530"
---
# <a name="preview-create-a-canvas-app-from-azure-sql-database"></a>プレビュー: Azure SQL Database からキャンバス アプリを作成する

[この記事はプレリリース ドキュメントであり、変更されることがあります。]

この記事では、Power Apps でAzure SQL データベースのデータを使用して簡単にアプリを作成する方法を説明します。 データを使用して完全に機能するアプリを使用して、ビジネス ニーズに適合してカスタマイズし、および任意のデバイスで共有できます。

> [!IMPORTANT]
> - これはプレビュー機能です。
> - プレビュー機能では、可用性が限られ、機能が制限されている場合があります。 公式リリースの前にプレビュー機能を利用できます。こうすることで、顧客が一足先にアクセスしてフィードバックを提供することができます。

## <a name="prerequisites"></a>前提条件

- ブラウザーでポップアップを有効にする必要があります。
- Azure サブスクリプションが必要です。 </br>Azure サブスクリプションがない場合は、[無料アカウントを作成します](https://azure.microsoft.com/free/)。
- 既存の SQL Database にアクセスする必要があります。 </br> 既存の SQL Database がない場合は、[新しいデータベースを作成してください](https://docs.microsoft.com/azure/sql-database/sql-database-single-database-get-started?tabs=azure-portal)。
- ファイア ウォール設定で、[Azure サービス](#app-access-to-sql-database-server)の SQL データベース サーバーへのアクセスを許可する必要があります。
- SQL Database テーブルには、テキスト データ型の列が少なくとも 1 つ必要となります。

## <a name="create-an-app-from-azure-portal"></a>Azure portal からアプリを作成する

> [!TIP]
> [Power Apps](https://make.powerapps.com) から Azure SQL データベースを使用するアプリを作成することもできます。 詳細については、[Power Apps 用の SQL Server コネクタ](https://docs.microsoft.com/powerapps/maker/canvas-apps/connections/connection-azure-sqldatabase) をお読みください。

1. [Azure ポータル](https://portal.azure.com)にサインインします。
1. SQL データベースに移動します。
1. **Power Apps** を選択します。
    
    ![SQL Database オプションの Power Apps オプション](./media/app-from-azure-sql-database/powerapps-link-azure-portal.png "SQL データベース内の Power Apps オプション")

1. **始める** を選択します。

1. アプリ名は自動入力されますが、必要に応じて変更可能です。
    

1. SQL の認証パスワードを入力し、必要に応じて、自動入力されたユーザー名を変更します。
    
    > [!NOTE]
    > Azure SQL データベースで SQL 認証の代わりに Azure AD 統合認証を使用する場合は、代わりに [Power Apps](https://make.powerapps.com) からアプリを作成し、[SQL Server コネクタ](https://docs.microsoft.com/powerapps/maker/canvas-apps/connections/connection-azure-sqldatabase) を使用します。

1. ドロップダウン リストから使用するテーブルを選択してアプリを作成します。

1. **作成**を選びます。

    ![アプリの情報を指定する](./media/app-from-azure-sql-database/powerapps-create-page-azure-portal.png "アプリの情報を指定する")

    [Power Apps Studio](https://create.powerapps.com/studio/) は、新しいタブで開きます。ポップアップがブロックされている場合は、ブラウザーを更新してポップアップを許可し、やり直してください。 作成すると、SQL データベースのデータを含む 3 ページのアプリができます。

## <a name="accessing-your-app"></a>アプリにアクセスする

作成したアプリに再度アクセスするには、[Power Apps](https://make.powerapps.com) に移動します。

## <a name="app-environment-and-region"></a>アプリの環境およびリージョン

このメソッドで作成するアプリは、テナントの[既定の環境](https://docs.microsoft.com/power-platform/admin/environments-overview#the-default-environment) を使用し、この環境のリージョンに展開します。 [管理センター](https://docs.microsoft.com/power-platform/admin/regions-overview#how-do-i-find-out-where-my-app-is-deployed) から展開されたアプリのリージョンまたはテナントの既定の環境を検索できます。 特定の環境のすべてのアプリを確認するには、[Power Apps](https://make.powerapps.com) に移動し、リボンから**環境**を選択し、続いて左側の**アプリ**を選択します。

## <a name="app-access-to-sql-database-server"></a>SQL データベース サーバーへのアプリのアクセス

Azure ポータルまたはストアド プロシージャ *sp_set_firewall_rule* を使用して、Power Apps の Azure SQL データベースサーバーへのアクセスを構成できます。

Azure portal を使用してアクセスを構成するには、[Azure ポータル](https://portal.azure.com/)にサインインし、**SQL サーバー**に移動します。 **ファイアウォールおよびバーチャル ネットワーク**を選択し、**Azure サービスおよびリソースがこのサーバーにアクセスすることを許可する**コントロールを**オン**に設定します。 **保存**を選択し、変更を送信します。

ストアド プロシージャ [sp_set_firewall_rule](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database?view=azuresqldb-current) を使用して Azure サービスを Azure SQL サーバーにアクセスできるようにするには、IP アドレスに **0.0.0.0** を使用します。

## <a name="limitations"></a>制限

- アプリ名には、文字、数字、ハイフン、かっこ、またはアンダースコアのみを含めることができます。
- Azure portal からアプリを作成するには、SQL 認証が必要です。
- Azure portal からキャンバス アプリを作成しているときは、1 つのテーブルしか選択できません。 さらにデータ接続を追加してテーブルおよびその他のデータ ソースを追加する場合は、アプリの作成後にアプリをカスタマイズします。
- Power Apps では、VNet サービス エンドポイントを使用して SQL Database に接続することはできません。 詳細については、[VNet サービス エンドポイントを使用してアクセスを許可](https://docs.microsoft.com/azure/sql-database/sql-database-vnet-service-endpoint-rule-overview) をお読みください。

## <a name="other-considerations"></a>その他の考慮事項

- SQL Database へのアプリのアクセスは、[このアプリを共有する](share-app.md) すべてのユーザーと暗黙的に共有されます。 SQL 認証資格情報に、データの読み取りおよび書き込みのための適切なアクセス権があることを確認します。 </br> たとえば、異なる SQL 認証資格情報で同じ SQL データベースに接続する別のアプリを作成し、読み取りおよび読み取り/書き込みアクセスを分離できます。
- スロットリング制限、デリゲート可能な機能および操作、既知の問題、および、この機能がパフォーマンスの考慮事項のために使用する [SQL Database](https://docs.microsoft.com/connectors/sql/) コネクタの制限をレビューします。
- SQL Database のデータを利用して、デフォルトではない環境とテナントの異なるリージョンのアプリを作成する必要がある場合、[Power Apps](https://make.powerapps.com) からアプリを作成します。

## <a name="next-steps"></a>次の手順

次の手順として、[Power Apps](https://make.powerapps.com) スタジオを使用して、ビジネス ニーズに合わせて追加のコントロール、画像、およびロジックを追加してアプリをカスタマイズします。

> [!div class="nextstepaction"]
> [Power Apps でキャンバス アプリのインターフェイスを設計する](add-configure-controls.md)

## <a name="see-also"></a>関連項目

- [Power Apps でキャンバス アプリを共有する](share-app.md) </br>
- [Power Apps でキャンバス アプリにデータの接続を追加する](add-data-connection.md#add-data-source)</br>
- [Microsoft Learn: Power Apps でキャンバス アプリをカスタマイズする](https://docs.microsoft.com/learn/modules/customize-apps-in-powerapps/)
