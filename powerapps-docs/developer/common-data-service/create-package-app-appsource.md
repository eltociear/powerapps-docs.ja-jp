---
title: '手順 3: アプリの AppSource パッケージを作成する (Common Data Service) | Microsoft Docs'
description: ソリューションおよびデモ データ ファイルをその他必須ファイルと共に含めるにあたって、 AppSource パッケージ (.zip ファイル) を作成する方法を学習します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 43accbf1e1acf8c32e76c5e0c0dab4975cd847a0
ms.sourcegitcommit: f70be39855e4931312fe0035525586a15ed4487b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2019
ms.locfileid: "2922350"
---
# <a name="step-3-create-an-appsource-package-for-your-app"></a>手順3: アプリの AppSource パッケージを作成する

ソリューションおよびデモ データ ファイルを他の必須ファイルと共に含めるにあたって、 AppSource パッケージ (.zip ファイル) を作成する必要があります。 AppSource のパッケージは以下のファイルから構成されます:

|ファイル|説明|
|--|--|
|パッケージ ファイル|ソリューションおよびデモ構成データを複数言語に展開するにあたって Package Deployer ツールが使用するパッケージ ファイル。|
|[Content_Types].xml|AppSource パッケージに含まれるファイル拡張子のMIMEタイプ情報を提供するファイル。 これらは通常、.config、.dll、.exe、.xml、および .zip のファイルの種類ですが、Windows によってサポートされるほとんどすべてのファイルの種類を追加することができます。|
|アイコン ファイル|appsource パッケージ アイコンのイメージ ファイル。サイズは 32x32 ピクセルである必要があります。 有効なイメージ フォーマットは PNG および JPG です。|
|[HTML ファイル]|ライセンス条項含むファイル。|
|input.xml|AppSource パッケージの資産を示すファイル。|


## <a name="create-a-package-file"></a>パッケージ ファイルを作成する

アプリに関連付けられた複数のファイルを同時にバンドルおよび展開することができるパッケージ。 

1. [手順 2: アプリの管理ソリューションを作成する](create-solution-app-appsource.md)で作成したソリューションおよび構成データ ファイルを含める Dynamics 365 パッケージを作成します。 また、パッケージには、パッケージが Common Data Service インスタンスに展開される前、間、または後に実行可能なカスタム コードを含むことができます。 パッケージ ファイルの作成に関する詳細については、 [Dynamics 365 Package Deployerのパッケージを作成する](/dynamics365/customer-engagement/developer/create-packages-package-deployer) を参照してください。

    パッケージを作成すると、パッケージは以下の内容で構成されます。

    - **\<PackageName> フォルダー**: このフォルダーには、パッケージのすべてのソリューション、構成データ、フラット ファイル、および目次が含まれます。 例: **PkgFolder**。  
  
    - **\<PackageName>.dll**: アセンブリには、パッケージのカスタム コードが含まれています。 例: **SamplePackage.dll**。

2. 次に、パッケージに含まれるファイル拡張子のMIMEタイプ情報を提供する **[Content_Types].xml** ファイルを作成します。 これは、 AppSource パッケージに再び含まれるものとは別のものです。 ファイルタイプがリストされた Content_Types.xml ファイルの内容例を次に示します。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="https://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="xml" ContentType="application/octet-stream" />
      <Default Extension="xaml" ContentType="application/octet-stream" />
      <Default Extension="dll" ContentType="application/octet-stream" />
      <Default Extension="zip" ContentType="application/octet-stream" />
      <Default Extension="jpg" ContentType="application/octet-stream" />
      <Default Extension="gif" ContentType="application/octet-stream" />
      <Default Extension="png" ContentType="application/octet-stream" />
      <Default Extension="htm" ContentType="application/octet-stream" />
      <Default Extension="html" ContentType="application/octet-stream" />
      <Default Extension="db" ContentType="application/octet-stream" />
      <Default Extension="css" ContentType="application/octet-stream" />
    </Types>
    ```

3. 以下のファイルを *package.zip* という名前のファイルに圧縮 (zip) します。
   - パッケージ フォルダー (PkgFolder)
   - パッケージ dll (SamplePackage.dll)
   - [Content_Types].xml

     これらのファイルを圧縮するには、これらのファイルが存在する場所のフォルダーを探して、すべてを選択し、右クリックし**送信先** > **圧縮 (zip) フォルダー**の順に選択します。

     ![パッケージ用ファイルを圧縮 (zip)](media/appsource-zip-package.png) 

4. .zip ファイルの名前を **package.zip** に変更します。

## <a name="create-content_typesxml"></a>[Content_Types].xml を作成する

前述の 手順 2 のセクションで作成した **[Content_Types].xml** を再利用することができます。

## <a name="create-an-icon-for-your-appsource-package"></a>AppSource パッケージのアイコンを作成する

Dynamics 365 管理センター ポータルに目的のソリューション名と説明と共に表示する、32x32 サイズのアイコン ファイルを作成します。 有効なファイル フォーマットは PNG および JPG です。

## <a name="create-an-html-file-for-license-terms"></a>ライセンス条項の HTML ファイルを作成する

ライセンス条項を含む HTML ファイルを作成します。 アプリケーションが複数言語をサポートしている場合、ユーザーが選択した言語でライセンス条項を表示するために、言語ごとに HTML ファイルを持つことができます。

## <a name="create-inputxml-file"></a>input.xml ファイルを作成する

パッケージおよびパッケージのコンテンツに関する情報を提供する *input.xml* ファイルを作成します。 これはサンプル ファイル **input.xml** のコンテンツです。各要素は表の後半で説明されます。

```xml
<?xml version="1.0" encoding="utf-8"?>
<PvsPackageData>
  <ProviderName>Microsoft</ProviderName>
  <PackageFile>package.zip</PackageFile>
  <SolutionAnchorName>SampleSolution.zip</SolutionAnchorName>
  <StartDate>12/01/2017</StartDate>
  <EndDate>01/01/2021</EndDate>
  <SupportedCountries>US,CA</SupportedCountries>
  <LearnMoreLink>https://www.microsoft.com</LearnMoreLink>
  <Locales>
    <PackageLocale Code="1033" IsDefault="true">
      <Logo>logo32x32.png</Logo>
      <Terms>
        <PackageTerm File="TermsOfUse.html" />
      </Terms>
    </PackageLocale>
  </Locales>
</PvsPackageData>
```


これは **input.xml** ファイル内の要素の説明です。

|Element|内容|
|--|--|
|ProviderName|ソリューション プロバイダーの名前。 Microsoft 内部チームが作成する場合、**Microsoft** と指定されます。|
|PackageFile|Package Deployer ツールのパッケージ (.zip ファイル) の名称。 この zip ファイルには、パッケージ アセンブリ、アプリ資産を持つパッケージ フォルダー、および Content_Types.xml ファイルを含める必要があります。 たとえば、[パッケージ ファイルを作成する](#create-a-package-file)セクションで作成された package.zip ファイルです。|
|SolutionAnchorName|ソリューション資産の表示名称と説明に使用される、パッケージ内のソリューションzipファイルの名称。|
|StartDate|AppSourceでアプリが利用可能になった日付。 形式は MM/DD/YYYY です。|
|終了日|AppSourceでアプリが利用できなくなった日付。 形式は MM/DD/YYYY です。|
|SupportedCountries|これはアプリが利用可能な国または地域をコンマで区切ったリストです。 現在この記事を記述している時点で、サポートされる国の一覧は、AE、AL、AM、AO、AR、AT、AU、BA、BB、BD、BE、BG、BH、BM、BN、BO、BR、BY、CA、CH、CI、CL、CM、CO、CR、CV、CW、CY、CZ、DE、DK、DO、DZ、EC、EE、EG、ES、FI、FR、GB、GE、GH、GR、GT、HK、HN、HR、HU、ID、IE、IL、IN、IQ、IS、IT、JM、JO、JP、KE、KG、KN、KR、KW、KY、KZ、LB、LK、LT、LU、LV、LY、MA、MC、MD、ME、MK、MN、MO、MT、MU、MX、MY、NG、NI、NL、NO、NZ、OM、PA、PE、PH、PK、PL、PR、PS、PT、PY、QA、RO、RS、RU、RW、SA、SE、SG、SI、SK、SN、SV、TH、TM、TN、TR、TT、TW、UA、US、UY、UZ、VE、VI、VN、ZA、ZW です|
|LearnMoreLink|このパッケージの詳細情報ページの URL。|
|ロケール|目的のソリューション UI でサポートする各言語のためのこのノードのインスタンス。 このノードには以下の子要素が含まれます。<br/>- **PackageLocale.Code**: このノードの言語の LCID。 例: 米国英語は 1033 です<br/>- **PackageLocale.IsDefault**: 既定の言語を示します。 顧客が選択した言語が利用可能でない場合は、これが代替言語として使用されます。<br/>- **ロゴ**: アプリ パッケージのロゴ。 イメージのサイズは 32x32 である必要があります。 有効なイメージ フォーマットは PNG および JPG です。<br/>- **条項**: 各言語のライセンス条項を含む HTML ファイルの名前。|

## <a name="add-the-items-to-an-appsource-package"></a>AppSource パッケージにアイテムを追加する

最後の手順は、以前作成済みのすべてのコンポーネントを単一の圧縮 (zip) ファイルに追加することです。これはアプリ ソース パッケージになります。

1. パッケージファイル、 [Content_Types].xml、 アイコン、 ライセンス条件ファイル (HTML) が格納されているフォルダに移動します。そのすべてを選択し、右クリックして **送る** > **圧縮(zip形式)フォルダー**を選択します。

    ![AppSource パッケージ](media/appsource-package.png)

    > [!IMPORTANT]
    > ここで説明されているパッケージのコンテンツ構造に正確に従う必要があります。そうしなければパッケージは認証中に失敗します。 認証失敗につながる一般的な問題の一部は、不正確なファイル名または入れ子ファイル構造です。

2. アプリごとにファイルの名前を適切に変更します。 会社名とアプリ名を含めることを推奨します。 例: **Microsoft_SamplePackage.zip**。
 

> [!div class="nextstepaction"]
> [手順 4:  AppSource パッケージ を Azure ストレージに保存する](store-appsource-package-azure-storage.md) 
