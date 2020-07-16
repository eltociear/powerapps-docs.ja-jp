---
title: ''
description: ''
author: iaanw
manager: shellha
ms.service: powerapps
ms.topic: conceptual
ms.custom: ce06122020
ms.reviewer: tapanm
ms.date: 6/12/2020
ms.author: iawilt
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 84938440150bb4b36fdbd39e8604c05f7cfd6858
ms.sourcegitcommit: a94b56525667015d4439a082873c2262a61b25a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2020
ms.locfileid: "3455832"
---
# <a name="add-geospatial-components-to-your-app-preview"></a>アプリに地理空間コンポーネントを追加する (プレビュー版)

[!INCLUDE [cc-beta-prerelease-disclaimer.md](../../includes/cc-beta-prerelease-disclaimer.md)]

キャンバス アプリに地理空間コンポーネントをいくつか追加して、場所や住所のマッピングを含むシナリオに対応することができます。

コンポーネントは、特定のシナリオのニーズに応えることができるコントロールのグループです。 [Power Apps 開発者ライブラリ](/powerapps/developer/component-framework/custom-controls-overview) にて、コンポーネントの詳細と独自のビルド方法を解説しています。

以下の事前構築済みコンポーネントは、地理空間とマッピングのシナリオに使用できます :

- [インタラクティブ マップ](geospatial-component-map.md)
- [住所入力](geospatial-component-input-address.md)

## <a name="prerequisites"></a>前提条件

1. 管理者は、環境の [Power Platform管理センターで地理空間機能を有効にする](#enable-the-geospatial-features-for-the-environment)必要があります。 そのためには、特定の利用規約を確認し、同意する必要があります。
2. [各アプリの地理空間機能を有効にします](#enable-the-geospatial-features-for-each-app)。
    
    >[!IMPORTANT]
    >コンポーネントには、既定の **組織** のデータ ソースが存在することを必要とします。 このデータソースは、コンポーネントをアプリに挿入する際に必ず含まれますが、手動で削除した場合は、コンポーネントが動作する前に追加する必要があります。
    >1. コンポーネントを選択した状態で、サイド ナビゲーション メニューの**データソース**タブに移動します。
    >2. 検索フィールドに **組織**と入力し、表示されるデータ ソースを選択します。 これによって、コンポーネントに追加されます。


>[!NOTE]
> これらの地理空間コンポーネントは現在、実験的なプレビュー機能であり、[Power Appsプレビュープログラム環境](/power-platform/admin/preview-environments) の [https://preview.create.powerapps.com](https://preview.create.powerapps.com) でのみ利用できます。

### <a name="enable-the-geospatial-features-for-the-environment"></a>環境で地理空間機能を有効にします

アプリで地理空間機能を使用する前に、管理者はアプリを作成する環境の機能へのアクセスを有効にする必要があります。

地理空間機能には追加の利用規約が必要となるため、これを確認し、同意する必要があります。

1. [Power Platform 管理センター](https://admin.powerplatform.microsoft.com)を開きます。

1. **環境**タブで、アプリに使用する環境を選択してから、トップメニューから**設定**を選択します。

    ![Power Platform 管理センターで、環境を選択する](./media/geospatial/ppac-environment.png "Power Platform 管理センターで、環境を選択する")

1. **製品**を展開し、**機能**を選択します。

    ![機能の選択がハイライト表示された環境設定のスクリーンショット](./media/geospatial/ppac-settings.png "機能の選択がハイライト表示された環境設定のスクリーンショット")

1. **地理空間サービス (プレビュー版)** 配下で、スイッチを**オン**に切替えます。 利用規約のお知らせが表示されます。 利用規約を読み、同意する場合はチェックボックス**サービス規約に同意します**を選択し、続いて**有効にする**を選択します。

    ![利用規約のスクリーンショット](./media/geospatial/ppac-tos.png "利用規約のスクリーンショット")

    >[!IMPORTANT]
    >地理空間機能を使用するには、利用規約を読んで同意する必要があります。 利用規約は以下を参照してください :  
    >  
    >これらの機能は、サードパーティの TomTom(tm) が提供するマッピング機能を使用しており、テナントの地理的な地域、コンプライアンスの境界、またはナショナル クラウド インスタンスの外部で動作します。  
    >
    >Microsoft は住所と場所のクエリを TomTom(tm) と共有します。 クエリを入力した顧客、またはエンドユーザーの名前は共有されません。
    >
    >この機能はどの地域でも同様で、ユーザーが提供するクエリは、マイクロソフトまたはそのサブプロセッサが営業活動を行う、米国またはその他の国で保存および処理される場合があります。
    >
    >この機能を有効にするには、追加のライセンス要件が必要な場合があります。  

    ![地理空間サービスのトグルスイッチをオンにするスクリーンショット](./media/geospatial/ppac-geo-on.png "地理空間サービスのトグルスイッチをオンにするスクリーンショット")

1. 設定ページ下部にある **保存** を選択します。

    ![保存ボタンのスクリーンショット](./media/geospatial/ppac-save.png "保存ボタンのスクリーンショット")

### <a name="enable-the-geospatial-features-for-each-app"></a>各アプリの地理空間機能を有効化します

1. [https://create.powerapps.com](https://create.powerapps.com) の Power Apps Studio で編集するアプリを開きます。

2. トップ メニューから、**ファイル**を選択します。

    ![ファイルの選択](./media/augmented-overview/augmented-overview-file.png "ファイルの選択")

3. **設定**タブに移動し、**高度な設定**を選択します。下方向にスクロールして、**地理空間機能**オプションを見つけてください。 オプションを**オン**に設定します。

    ![地理空間機能スイッチをオンに設定する](./media/geospatial/enable-geo.png "地理空間機能スイッチをオンに設定する")

4. 戻り矢印アイコンを選択して、アプリの編集に戻ります。

    ![戻り矢印アイコンを選択します](./media/augmented-overview/augmented-overview-back.png "戻り矢印アイコンを選択します")

5. **挿入**ペインを開き、地理空間コンポーネントを確認します。
    - **住所入力**は、**入力**の下にあります
    - **地図**は**メディア**の下にあります

    ![住所入力コンポーネントを参照する](./media/geospatial/insert-address-input.png "住所入力コンポーネントを参照する")  

    ![メディアの下のマップ コンポーネントを参照する](./media/geospatial/insert-map.png "メディアの下のマップ コンポーネントを参照する")

### <a name="next-steps"></a>次の手順

アプリへのコンポーネントのインストールを開始します:

- **[インタラクティブ マップ](geospatial-component-map.md)** コンポーネントを使用して、位置データを視覚化して解釈します。
- **[住所入力](geospatial-component-input-address.md)** コンポーネントを使用して入力すると、住所の動的な提案が表示されます。
