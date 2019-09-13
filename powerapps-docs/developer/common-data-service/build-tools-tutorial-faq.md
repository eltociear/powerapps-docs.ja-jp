---
title: 構築ツールのチュートリアルと、よく寄せられる質問| Microsoft Docs
description: 'PowerApps 構築ツールは、PowerApps固有の Azure DevOps 構築タスクの集合です。これにより PowerApps の開発管理において、スクリプトを手動でダウンロードする必要がなくなります。 このトピックでは、これらのツールの詳細情報を提供するチュートリアルとFAQについて説明します。 '
ms.custom: ''
ms.date: 07/21/2019
ms.reviewer: Dean-Haas
ms.service: powerapps
ms.topic: article
author: mikkelsen2000
ms.author: pemikkel
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-and-faq"></a>チュートリアルとよく寄せられる質問


[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]
Azure DevOps に向けた PowerApps 構築ツールの詳細については、チュートリアルとFAQを参照してください。 

## <a name="hands-on-lab"></a>ハンズオン ラボ

ハンズオン ラボは、 [こちらで](https://github.com/microsoft/PowerApps-Samples/tree/master/azure/build-tools)使用することができます。

このハンズオン ラボでは、以下のシナリオの構築方法を段階的に説明するチュートリアルを提供します:

1. 開発環境、ビルド環境、本番環境を設定します。
2. サンプル アプリを構築します。
3. 開発環境からサンプル アプリケーション含むソリューションをエクスポートします。
4. ソリューションを展開します。
5. ソリューションをソース (リポジトリ) にコミットします。
6. 管理されていないソリューションをインポートして、環境を構築します。
7. 構築アーティファクト (管理対象のソリューション) 生成します。
8. ダウンストリーム環境にソリューションを展開します。

> [!NOTE]
> ハンズオン ラボは、 Azure DevOpsにてパイプラインを構築する方法を学びたい Azure DevOps の新規ユーザーにハンズオン エクスペリエンスを提供しています。 パイプラインは、構築をすることもできますが、チュートリアルからダウンロードすることも可能となっています。これによって環境変数、ソースフォルダ/ターゲットフォルダ、リポジトリなどを微調整するだけで、そのまま使用することができます。  

## <a name="frequently-asked-question-faq"></a>よくあるご質問 (FAQ)

**PowerApps の構築ツール PowerApps のみで動作しますか?**  

*PowerApps の構築ツールは Customer Engagement の PowerApps と Dynamics CRM の両方で機能します (Dynamics 365 CE Apps はモデル駆動型の PowerAppsです)。また、他の構構築タスクを Microsoft Dynamics for Finance and Operations で使用することができます*

**FlowとCanvasアプリを含めることはできますか?**

*はい、Flows と Canvas アプリはソリューションに対応しているため、ソリューションに追加をすることでアプリのライフサイクルに登録することができます。ただし、一部の手順では手動設定が必要となります。これについては、今年の後半に環境変数とコネクタの導入をする際に同時に対応する予定です。*

**PowerApps 構築ツールの価格を教えてください**

*PowerAppsの構築ツールは無料で使用することができます。ただし、構築ツールを使用するためは Azure DevOps の有効なサブスクリプションが必要となります。詳細については [こちら](https://azure.microsoft.com/en-us/pricing/details/devops/azure-devops-services/)を参照してください。*

**拡張機能が表示されますが、それをインストールするオプションがないのはなぜですか?**

***インストール** オプション (以下のスクリーンショットに概要を表示しています) が表示されていない場合は、 Azure DevOps で必要なインストール権限が付与されていないことが考えられます。詳細については [こちら](https://docs.microsoft.com/en-us/azure/devops/marketplace/how-to/grant-permissions?view=azure-devops)を参照してください*。

![タスクの構築画面](media/build-tasks.png)