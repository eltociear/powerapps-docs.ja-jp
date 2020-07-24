---
title: Acceleration、App、Compass、Connection、および Location 信号 | Microsoft Docs
description: Power Apps での Acceleration、App、Compass、Connection、および Location センサーの構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1cd90e345b41f8316e8cd8c50f4077ee1f64ee91
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "3308661"
---
# <a name="acceleration-app-compass-connection-and-location-signals-in-power-apps"></a>Power Apps での Acceleration、App、Compass、Connection、および Location 信号

ユーザーが世界のどこにいて、どのスクリーンが表示されているかなど、アプリの環境に関する情報を返します。

## <a name="description-and-syntax"></a>説明および構文

信号は、ユーザーがアプリをどのように操作しているかとは無関係の、いつでも変更できる値です。 信号に基づく数式は、これらの値が変化するときに自動的に再計算します。

通常、信号は情報の[レコード](../working-with-tables.md#records) を返します。 この情報を、レコードとして使用および保存したり、または **.** を使用して個々のプロパティを抽出することができます [演算子](operators.md)。

> [!NOTE]
> **Acceleration** および **Compass** 関数は、iOS または Android などのネイティブ プレーヤーで正確な値を返しますが、ブラウザーでアプリを作成または変更するとき、これらの関数はゼロ値を返します。

### <a name="acceleration"></a>Acceleration

**Acceleration** 信号は、デバイスのスクリーンに基づいて 3 次元でデバイスの加速度を返します。 加速度は *g* 単位で 9.81 m/秒<sup>2</sup> または 32.2 ft/秒<sup>2</sup> (地球が重力によって地表でオブジェクトに与える加速度) で測られます。

| プロパティ | 内容 |
| --- | --- |
| **Acceleration.X** |左右。  右は正数です。 |
| **Acceleration.Y** |前後。  前は正数です。 |
| **Acceleration.Z** |上下。  上は正数です。 |

### <a name="app"></a>App

他のプロパティの中で、**アプリ** オブジェクトには、どのスクリーンが表示されているかを示す信号が含まれています。

| プロパティ | 内容 |
| --- | --- |
| **App.ActiveScreen** |表示されているスクリーン。 スクリーンのプロパティを参照したり、または別のスクリーンと比較してどのスクリーンが表示しているかを確認するのに使用できるスクリーン オブジェクトを返します。 **[Back](function-navigate.md)** または **[Navigate](function-navigate.md)** 関数を使用して、表示しているスクリーンを変更することができます。 |

詳細: [**アプリ** オブジェクト](object-app.md) ドキュメント。

### <a name="compass"></a>Compass
**Compass** 信号はスクリーンの上部のコンパス方位を返します。 方位は磁北に基づきます。

| プロパティ | 内容 |
| --- | --- |
| **Compass.Heading** |度数で示す方位。  0 を北として、0 から 360 の数値を返します。 |

### <a name="connection"></a>Connection
**Connection** 信号は、ネットワークの接続に関する情報を返します。 従量制課金接続では、ネットワークを介して送受信するデータ量を制限したい場合があります。

| プロパティ | 内容 |
| --- | --- |
| **Connection.Connected** |デバイスがネットワークに接続されているかどうかを示すブール値の **true** または **false** の値を返します。 |
| **Connection.Metered** |接続が従量制課金であるかどうかを示すブール値の **true** または **false** の値を返します。 |

### <a name="location"></a>場所
**Location** 信号は、グローバル ポジショニング システム (GPS) および携帯電話基地局通信および IP アドレスなどの他のデバイス情報に基づいて、デバイスの場所を返します。

ユーザーが初めて場所情報にアクセスするとき、デバイスはそのユーザーにこの情報へのアクセスを許可するよう求める場合があります。

場所が変更すると、場所への依存関係は継続的に再計算され、デバイスのバッテリから電力が消費されます。 バッテリの寿命を節約するため、**[Enable](function-enable-disable.md)** および **[Disable](function-enable-disable.md)** 関数を使用して場所の更新をオンおよびオフすることができます。 表示されているスクリーンが場所情報に依存していない場合は、場所が自動的にオフになります。

| プロパティ | 内容 |
| --- | --- |
| **Location.Altitude** |フィートで測定された海抜の高度を示す数値を返します。 |
| **Location.Latitude** |赤道からの度数で測定される緯度を示す –90 から 90 の数値を返します。 正数は、赤道の北にある場所を示します。 |
| **Location.Longitude** |イギリスのグリニッジからの度数で測定される経度を示す –180 から 180 の数値を返します。  正数は、グリニッジの東にある場所を示します。 |

## <a name="examples"></a>例
野球場で、ピッチャーがピッチャー マウンドからホーム ベースのキャッチャーに電話を投げます。 電話は地面に対して平らに置かれており、スクリーンの上部はキャッチャーに向いていて、ピッチャーは回転を加えません。 この場所で、電話は従量制課金の携帯ネットワーク サービスを利用できますが、WiFi は利用できません。 **PlayBall** スクリーンは表示されています。   

| 計算式 | 内容 | 結果 |
| --- | --- | --- |
| **Location.Latitude** |現在の場所の緯度を返します。 フィールドは、マップ座標 47.591 N, 122.333 W にあります。 |47.591<br><br>ボールがピッチャーからキャッチャーまでを移動する間、緯度は継続的に変更されます。 |
| **Location.Longitude** |現在の場所の経度を返します。 |122.333<br><br>ボールがピッチャーからキャッチャーまでを移動する間、経度は継続的に変更されます。 |
| **場所** |現在の場所の緯度および経度をレコードとして返します。 |{&nbsp;Latitude:&nbsp;47.591, Longitude:&nbsp;122.333&nbsp;} |
| **Compass.Heading** |スクリーン上部のコンパスの方位を返します。 このフィールドで、ホーム ベースは、ピッチャー マウンドからおおよそ南西にあります。 |230.25 |
| **Acceleration.X** |デバイスの左右の加速度を返します。 ピッチャーは、電話をスクリーンの上部に対してまっすぐに投げるので、デバイスは左右の加速していません。 |0 |
| **Acceleration.Y** |デバイスの前後の加速度を返します。 ピッチャーはデバイスを投げるとき、最初に大きな加速度を与え、0.5 秒で1 時間当たり 0 から 90 マイル (1 秒あたり 132 フィート) に達します。 デバイスが空中にあると、空気の摩擦を無視し、デバイスがそれ以降加速することはありません。 デバイスはキャッチャーがキャッチすると減速し、停止します。 |ピッチャーがデバイスを投げている間は 8.2 です。<br><br>デバイスが空中にある間は 0 です。<br><br>キャッチャーがデバイスをキャッチするときは、-8.2 です。 |
| **Acceleration.Z** |デバイスの加速度をの上下に返します。 空中にある間、デバイスは重力の影響を受けます。 |ピッチャーがデバイスを投げる前は 0 です。<br><br>デバイスが空中にある間は 1 です。<br><br>キャッチャーがデバイスをキャッチした後は 0 です。 |
| **Acceleration** |レコードとして加速度を返します。 |ピッチャーがデバイスを投げるときは {X: 0, Y: 264, Z: 0} です。 |
| **Connection.Connected** |デバイスがネットワークに接続されているかどうかを示すブール値を返します |**True** |
| **Connection.Metered** |接続が従量制課金であるかどうかを示すブール値を返します |**True** |
| **App.ActiveScreen = PlayBall** |**PlayBall** が表示されているかどうかを示すブール値を返します。 |**True** |
| **App.ActiveScreen.Fill** |表示されているスクリーンのバックグラウンド色を返します。 |**Color.Green** |

