---
title: Excel の接続の概要 | Microsoft Docs
description: ワークブックをクラウド ストレージ アカウントに保存し、アプリからデータに接続することによって、Excel でデータを表示および更新します。
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/02/2016
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba582906c34b2831fffbfedcf645a00bd7cdb7d6
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "3306430"
---
# <a name="connect-to-excel-from-power-apps"></a>Power Apps から Excel に接続する
![Excel](./media/connection-excel/excelicon.png)

Excel は接続の*種類*です。 アプリで Excel データを表示するには:

1. [Excel データをテーブルとして書式設定](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664) します。
2. Excel ファイルをクラウド ストレージ アカウント (Box, Dropbox、Google Drive、OneDrive、および OneDrive for Business など) に保存します。
3. [クラウド ストレージ アカウントに接続](../add-manage-connections.md) し、データ ソースとして Excel テーブルを追加します。
4. [アプリを自動的に生成する](../get-started-create-from-data.md) か、または**ギャラリー** コントロールなどを追加して構成することにより、アプリでこの情報を表示します。

> [!NOTE]
> Power Apps から Excel テーブルに接続すると、**\_PowerAppsId_** という列が作成され、Excel テーブルの各行には一意の ID が付けられます。

「[クラウド ストレージ接続の概要](cloud-storage-blob-connections.md)」では、接続を追加し、データ ソースとして Excel テーブルを追加して、アプリで Excel のデータを使う方法が示されています。

他の種類のデータに接続する方法については、[Power Apps の接続の一覧](../connections-list.md) をご覧ください。

### <a name="known-limitations"></a>既知の制限
組織内の Excel データを共有する方法の詳細については、[これらの制限を確認する](cloud-storage-blob-connections.md#sharing-excel-tables) をご覧ください。

