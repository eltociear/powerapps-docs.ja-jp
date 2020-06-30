---
title: Power Apps におけるモデル駆動型アプリ フォームの最適化 | MicrosoftDocs
description: フォームの読み込みが遅くなる原因となるフォーム設計を避ける方法を学習します
ms.custom: ''
ms.date: 04/24/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: 59cfa5e6-638a-437f-a462-fddfd26fb07d
caps.latest.revision: 8
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e67db84c047754eed6bfc2588c5e59d83ea4674a
ms.sourcegitcommit: 82fa1758e29fe302f9a252fd9943ace03b7aada0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "3427087"
---
# <a name="optimize-model-driven-app-form-performance"></a>モデル駆動型アプリ フォーム パフォーマンスを最適化する

読み込みが遅いフォームでは、生産性とユーザーの導入が低下する可能性があります。 フォームの読み込みを最大限に高めるには、これらの推奨に従ってください。 これらの推奨事項の多くは、開発者が組織のフォーム スクリプトをどのように実装できるかについてです。 フォームのフォーム スクリプトを作成する開発者といっしょに、これらの推奨事項を必ず検討してください。  
  
<a name="BKMK_FormDesign"></a>   
## <a name="form-design"></a>フォームの設計  
 ユーザーとフォームとの間のやり取りと、フォームに表示する必要のあるデータの量を検討してください。  
  
 **フィールド数を最低限に維持**  
 フォームにより多くのフィールドを組み込むと、各レコードを表示するために、インターネットまたはイントラネットによってより多くのデータを転送する必要があります。
 
 **パフォーマンスのための設計**  
 フォームとページを設計するときは、最も重要なものを一番上に配置して、ユーザーが簡単にアクセスできるようにします。 使用頻度の低いコンポーネントをフォーム上の他のタブに移動し、コンポーネントの表示と非表示の代わりにロールベースのフォームを使用し、異なるワークフローに専用のダッシュボードとビューがあることを確認します。 セクションを使用してコントロールを整理してください。これによりフォームが遅くなることはありません。
 
<a name="BKMK_FormScripts"></a>   
## <a name="form-scripts"></a>フォーム スクリプト  
 フォーム スクリプトを使用したカスタマイズが存在するとき、パフォーマンスを向上するためのこれらのストラテジーを開発者が理解していることを確認してください。  
  
**同期要求を使用しない**  
同期要求により、ページの読み込みに時間がかかったり、フォームが応答しなくなることがあります。 [代わりに非同期要求を使用する](https://docs.microsoft.com/powerapps/developer/model-driven-apps/best-practices/business-logic/interact-http-https-resources-asynchronously)。 その他の例については、[このブログの投稿](https://powerapps.microsoft.com/en-us/blog/turbocharge-your-model-driven-apps-by-transitioning-away-from-synchronous-requests/) を参照してください。
  
**不要な JavaScript Web リソース ライブラリの組み込みの回避**  
フォームにより多くのスクリプトを追加すると、それらをダウンロードする時間が余計にかかります。 通常、スクリプトは最初に読み込まれた後、ブラウザーにキャッシュされますが、フォームを最初に表示するときのパフォーマンスがきわめて強い印象を与えます。  
  
**Onload イベントでのすべてのスクリプトの読み込みの回避**  
フィールドの `OnChange` イベント、または `OnSave` イベントのみをサポートするコードがある場合は、`OnLoad` イベントの代わりに、これらのイベントのイベント ハンドラーを使用して、スクリプト ライブラリを設定するようにしてください。 このように、フォームを読み込むとき、これらのライブラリの読み込みを延期することができるし、パフォーマンスを向上させることもあります。  
  
 **折りたたまれたタブを使用して Web リソースの読み込みを延期**  
 Web リソースと IFRAME が折りたたみまれたタブ内のセクションに含まれているとき、タブが折りたたまれている場合、Web リソースと IFRAME は読み込まれません。 Web リソースと IFRAME は、タブが展開されているときに読み込まれます。 タブの状態が変化すると、`TabStateChange` イベントが発生します。 折りたたまれたタブ内で Web リソースまたは IFRAME をサポートするのに必要なすべてのコードが、**TabStateChange** イベントのイベント ハンドラーを使用して、別の方法では `OnLoad` イベントで発生した可能性のあるコードを減らすことができます。  
  
**既定の表示オプションの設定**  
フォーム要素を非表示にする、`OnLoad` イベントのフォーム スクリプトの使用を避けてください。 代わりに、表示されていない場合もあるフォーム要素の既定の表示オプションを設定して、フォーム読み込み時に既定で表示されないようにします。 次に、`OnLoad` イベントのスクリプトを使用して、表示対象のフォーム要素を表示させます。  
  
<a name="BKMK_CommandBar"></a>   
## <a name="command-bar-or-ribbon"></a>コマンド バーまたはリボン  
 コマンド バーまたはリボンを編集するときは、これらの推奨事項に留意してください。  
  
 **コントロール数を最低限に維持**  
 フォームのリボン コマンド内またはバー内で、必要なコントロールを評価し、必要でないコントロールを非表示にします。 表示される各コントロールは、ブラウザーにダウンロードする必要のあるリソースを増加させます。
 
 **カスタム ルールで非同期ネットワーク要求を使用する**  
 統一インターフェイスでネットワーク要求を行うカスタム ルールを使用する場合、[非同期ルール評価を使用します](https://docs.microsoft.com/powerapps/developer/model-driven-apps/define-ribbon-enable-rules#custom-rule)。
  
## <a name="next-steps"></a>次のステップ  
 [フォームの作成および設計](create-design-forms.md)    
    
 
