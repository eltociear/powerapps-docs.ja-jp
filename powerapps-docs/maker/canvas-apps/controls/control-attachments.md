---
title: '添付ファイル コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含む、添付ファイル コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 03/09/2020
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 35e4107934134a229817deb258bacf5e36c9dbb6
ms.sourcegitcommit: a02b20113164acb11955d27ef4ffa421ee0fba9d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "3308224"
---
# <a name="attachments-control-in-power-apps"></a>Power Apps の添付ファイル コントロール
ユーザーがデバイスへのファイルのダウンロードや、SharePoint リストまたは Common Data Service エンティティからのファイルのアップロードや削除ができるようになるコントロール。

## <a name="limitations"></a>制限
添付ファイル コントロールには、次の制限があります:
1. 添付ファイルは SharePoint リストおよび Common Data Service エンティティでサポートされています。

1. アップロードと削除の機能は、フォームの内部でのみ機能します。 添付ファイル コントロールは、編集モードでフォーム内にない場合、無効と表示されます。 ファイルの追加と削除を保存するには、アプリ ユーザーがフォームを保存する必要があります。 この制限のため、添付ファイル コントロールは**挿入**タブからは利用できませんが、SharePoint または Common Data Service フォームで添付ファイル フォーム フィールドが有効である場合はフォームに表示されます。

1. ファイルは 10 MB 以下の場合にのみアップロードできます。  

## <a name="description"></a>内容
**添付ファイル** コントロールにより、SharePoint リストまたは Common Data Service エンティティからのファイルを開いたり、追加したり、削除したりできるようになります。

## <a name="key-properties"></a>主要なプロパティ
**[項目](properties-core.md)** – ダウンロードできるファイルを記述しているソースです。

**MaxAttachments** – コントロールが受け入れるファイルの最大数。

**MaxAttachmentSize** – 新しい添付ファイルごとに許容される最大ファイル サイズ (MB)。  現在、10 MB の制限があります。

**OnAttach** – ユーザーが新しい添付ファイルを追加するときのアプリの応答方法。

**OnRemove** – ユーザーが既存の添付ファイルを削除するときのアプリの応答方法。

**[OnSelect](properties-core.md)** – ユーザーが添付ファイルをクリックしたときのアプリの応答方法。

## <a name="additional-properties"></a>追加のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベル。 添付ファイルの目的を説明する必要があります。

**AddAttachmentText** – 新しい添付ファイルを追加するために使用するリンクのラベル テキスト。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線が**実線**、**破線**、**点線**、または**なし**かどうか。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さ。

**[DisplayMode](properties-core.md)** – コントロールがファイルの追加と削除を許可するかどうか (**編集**)、データの表示のみを許可するか (**表示**)、または無効 (**無効**) にします。

**[FocusedBorderColor](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の色。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールがフォーカスされているときのコントロールの境界線の太さ。

**[高さ](properties-size-location.md)** – コントロールの上端と下端間の距離。

**MaxAttachmentsText** – 許容されるファイルの最大数がコントロールに含まれているときに、"添付ファイル" リンクと置き換えられるテキスト。

**NoAttachmentsText** – 添付ファイルがないときにユーザーに表示される情報テキスト。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序。

**[表示](properties-core.md)** – コントロールが表示されるかどうか。

**[幅](properties-size-location.md)** – コントロールの左端と右端間の距離。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離。


## <a name="example"></a>例
1. アプリにフォームを追加し、そのデータ ソースとして SharePoint リストを設定します。

2. 左側にあるツリー ビュー内の**表示フォーム** コントロールを選択します。 代わりに**編集フォーム**を使用することもできます。

3. 右側のオプション パネルのプロパティ タブで**データ ソース**を選択してから、接続した SharePoint リストを選択します。

4. *フィールド* セクションで**編集フィールド**を選択し、**フィールドの追加**を選択します。 

5. **添付ファイル** フィールドを選択し、**追加**を選択します。

    SharePoint リストに関連付けられている添付ファイル フィールドが、フォームに表示されます。

[コントロールを追加して構成する方法に関する説明](../add-configure-controls.md)


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
次の間には適切な色のコントラストが必要です:
* **ItemColor** と **ItemFill**
* **ItemHoverColor** と **ItemHoverFill**
* **ItemPressedColor** と **ItemPressedFill**
* **AddedItemColor** と **AddedItemFill**
* **RemovedItemColor** と **RemovedItemFill**
* **ItemErrorColor** と **ItemErrorFill**
* **AddAttachmentColor** と**塗りつぶし**
* **MaxAttachmentsColor** と**塗りつぶし**
* **NoAttachmentsColor** と**塗りつぶし**

これは、[標準の色のコントラスト要件](../accessible-apps-color.md) に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダー サポート
次のプロパティが存在する必要があります:
* **[AccessibleLabel](properties-accessibility.md)**
* **AddAttachmentsText**
* **MaxAttachmentsText**
* **NoAttachmentsText**

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** および **[FocusedBorderThickness](properties-color-border.md)** を使用します。
