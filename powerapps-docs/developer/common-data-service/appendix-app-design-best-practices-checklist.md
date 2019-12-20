---
title: '付録: アプリ設計のベスト プラクティスのチェックリスト (PowerApps) | Microsoft Docs'
description: Power Apps でアプリ設計チェックリストを使用してアプリの設計を評価します。
ms.custom: ''
ms.date: 03/20/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: omarcdoc
ms.author: omarc
manager: AnnBe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 20c2356e61b3ec8c11128d29450bcb39a2099add
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883553"
---
# <a name="appendix-app-design-best-practices-checklist"></a>付録: アプリ設計のベスト プラクティス チェックリスト

次のチェックリストを使用してアプリの設計を評価します。 

<table>
<tbody>
<tr>
<th>S.No</th>
<th>アーティファクト</th>
<th>成功の条件</th>
</tr>
<tr>
<td>1</td>
<td>フォントの均一性</td>
<td><ul>
<li>フォント サイズはソリューション全体で均一です</li>
<li>フォントの色はソリューション全体で均一です</li>
<li>フォントは意図したすべてのデバイスで読み取り可能です</li>
</ul>
</td>
</tr>
<tr>
<td>2</td>
<td>色のユーザー補助</td>
<td>このソリューションで使用される色は、すべてのユーザー グループからアクセスできます。</td>
</tr>
<tr>
<td>3</td>
<td> 色の均一性と設計スキーム </td>
<td>色と UI 設計が統一され整っている</td>
</tr>
<tr>
<td>4</td>
<td>ユーザーのための使いやすさ</td>
<td>ソリューションは直感的であり最小限の指示で使いやすい</td>
</tr>
<tr>
<td>5</td>
<td>ユースケースを満たすのに最小限の画面数</td>
<td>すべてのユースケースを最小限の画面数と手順で達成できます</td>
</tr>
<tr>
<td>6</td>
<td>パフォーマンス</td>
<td>
<ul>
<li>必要な場所でキャッシュが使用されます</li>
<li>必要な列だけがデータベースから取得されます</li>
<li>いずれかを達成するために、サーバーへの呼び出しが最小の回数行われます。</li>
ユースケース。
</ul>
</td>
</tr>
<tr>
<td>7</td>
<td>情報の表示</td>
<td>
<ul>
<li>情報は最もアクセスしやすい形式で表示されます</li>
<li>UI レイアウトは最善の方法で情報を提供するのに適しています</li>
<li>UI レイアウトはソリューションを実行できるすべてのデバイスでシームレスなエクスペリエンスを提供します</li>
</ul>
</td>
</tr>
<tr>
<td>8</td>
<td>応答性</td>
<td>ソリューションは対象のすべてのデバイスでテストされます</td>
</tr>
<tr>
<td>9</td>
<td>アクセス可能なコンテンツ</td>
<td>
<ul>
<li>ソリューションで提供されるコンテンツは、対象のすべてのデバイスに表示される可能性があります。<br/>例: 特定のブラウザで再生できない動画がないようにしてください。<li>
<li>不必要なリダイレクトをしないでください</li>
<li>ユーザーのフローを妨げる割込みをしないでください</li>
<li>設計はタッチ画面に適しています。 対象のデバイスがモバイルまたはタブレットの場合、ソリューションはタッチ画面向けに設計する必要があります</li>
</ul>
</td>
</tr>
<tr>
<td>10</td>
<td>情報の精度</td>
<td>UI で提供される情報は、そのシナリオを達成するために、ユーザーが意図したフローの最小限の中断でユースケースを達成するのに役立ちます。</td>
</tr>
</tbody>
</table>


キャンバス アプリを作成するベスト プラクティスの詳細は、[キャンバス アプリのコード標準とガイドライン](https://aka.ms/powerappscanvasguidelines) を参照してください。

  




  

