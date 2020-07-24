---
title: ポータルの Web ページ バインドの作成および管理 | MicrosoftDocs
description: ポータルの Web ページ バインドの作成および管理方法に関する説明 | MicrosoftDocs
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/12/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: 36447aaa098fcae926b936a64f3ac18bd2787148
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3491317"
---
# <a name="create-and-manage-website-bindings"></a>Web サイトのバインドの作成および管理

ポータルでは、Web サイトを選択する既定のメソッドは、特定のポータルの web.config ファイルで定義された Web サイトの名前を照合することにより Web サイトを検索することです。 Web サイト バインドには、適切な Web サイトを選択するためのポータルまたは要求のパスを読み込むときに、ホスト名を使用して Web サイトを選択する代替メソッドが用意されています。 これにより、特定の Web サイトの各バージョンに対して個別の web.config ファイルを変更する必要がなくなります。 これにより、さまざまな開発、ステージング、および生産環境でのポータルの展開を簡素化します。 さらに、複数の Web サイトを運用するための共通ポータル コードベースが許可されます。

## <a name="manage-website-bindings"></a>Web サイト バインドの管理

Web サイト バインドは Power Apps ポータル内で作成、編集、および削除することができます。 

1. [ポータル管理アプリ](configure-portal.md)を開きます。

2. **ポータル** > **Web サイト バインド**の順に移動します。

3. 新しい Web サイト バインドを作成するには、**新規**を選択します。

4. 既存の Web サイト バインドを編集するには、Web サイトのバインド名を選択します。

5. フィールドに適切な値を入力します。

6. **保存して閉じる**を選択します。

### <a name="website-binding-attributes"></a>Web サイト バインドの属性

これらはすべてのバインドに共通する属性です。

|名前|説明|
|-----|----------|
|名前| レコードを表示するときに Web サイト バインドを識別するためのタイトルです。|
|Web サイト|ポータルが選択する必要がある [Web サイト](websites.md)です。|
|リリース日|Web サイトの選択をいつ許可されるか決定する日付です。|
|有効期限|Web サイトの選択をいつ停止するか決定する日付です。|
|||

#### <a name="application-settings"></a>アプリケーションの設定

アプリケーション レベル バインドのためにこれらの属性の値を指定します。 バインドは IIS Web サイトまたはアプリケーションに基づきマップします。

|名前|説明|
|-----|----------|
|サイト名|IIS Web サイトの名前です。|
|仮想パス|Web サイト内の IIS アプリケーションの名前です。|
|||

Azure Web サイトおよびクラウド サービスの場合、サイト名および仮想パスは **ServiceDefinition.csdef** ファイルの <Site> および <VirtualApplication> ノードで決定されます。

```
<ServiceDefinition>
  <WebRole>
    <Sites>
      <Site name=Dynamics Portals>
        <VirtualApplication name=customer-portal/>
```

### <a name="see-also"></a>関連項目
[Web サイトの作成および管理](websites.md)
