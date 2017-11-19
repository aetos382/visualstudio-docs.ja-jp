---
title: "プロジェクトおよびソリューションのプロパティの管理 | Microsoft Docs"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 8871ab002a94a9c0bbc0063a25b4dea9cb271142
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="managing-project-and-solution-properties"></a>プロジェクトおよびソリューションのプロパティの管理

## <a name="project-options"></a>プロジェクト オプション

プロジェクト オプションは各プロジェクトに固有の設定で、プロジェクトの作成、ビルド、実行に影響があります。 これは、Visual Studio for Mac のユーザー固有のオプションを設定するユーザー設定や、ソリューション全体のオプションを設定するソリューション オプションとは対照的です。 プロジェクト オプションはプロジェクト ファイル (.csproj) に保存されるので、他の開発者がプロジェクトを正しくビルドし、実行することができます。 また、多数の開発者が正しいファイルの書式で同じドキュメントを編集できます。

Visual Studio for Mac のプロジェクト オプションを起動するには、プロジェクト名をダブルクリックするか、右クリックしてコンテキスト メニューを開き、**[オプション]** を選択します。

 ![コンテキスト メニューの [オプション]](media/projects-and-solutions-image2.png)

編集可能なオプションとして、ソース コードのビルド、実行、および設定のオプションと、バージョン管理のオプションがあります。

[プロジェクト オプション] は、次の機能を持つ 5 つのカテゴリに分かれています。

* **全般** - 名前、説明、既定の名前空間などのプロジェクト情報と、プロジェクトの場所を設定できます。
* **ビルド** - ポータブル クラス ライブラリの PCL プロファイルを設定または変更できます。 また、カスタム コマンド、構成、コンパイラのオプションを設定できます。 出力パスとアセンブリ名も設定できます。
* **実行** - プロジェクトごとにカスタムの実行構成を作成できます。
* **ソース コード** - さまざまなファイルの種類と名前付け規則の書式を制御できます。 また、名前付けポリシーと既定のヘッダー スタイルも設定できます。
* **バージョン管理** - プロジェクトでバージョン管理を使用するときのコミット メッセージのスタイルを編集できます。

各プロジェクトには、プラットフォームごとに異なるプロジェクト オプションを含めることもできます。 たとえば、次の図のような Xamarin.Android プロジェクトの場合、Android ビルドに関連するオプション (リンカー オプションなど) や、アプリケーションに関連するオプション (アクセス許可など) があります。

 ![Android プロジェクトのオプション](media/projects-and-solutions-image5.png)

Xamarin.iOS には、バンドルの署名に関連するオプション (使用する必須のプロビジョニング プロファイルなど) や、IPA パッケージ オプションに関連するオプションがあります。

 ![iOS プロジェクトのオプション](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>ソリューション オプション 

ソリューション オプションは、プロジェクト オプションと似ていますが、スコープはソリューション全体です。 ソリューション オプションでは、作成者情報、ビルド設定、コードの書式スタイル、バージョン管理を設定できます。また、ソリューションのスタートアップ プロジェクトを割り当てることもできます。  [ソリューション オプション] ダイアログには、**[プロジェクト] > [ソリューション オプション]** メニュー項目、ソリューション パッドの [ソリューション] のコンテキスト メニュー項目である **[オプション]**、または Solution Pad の [ソリューション] のダブルクリックでアクセスできます。

 ![ソリューション オプション](media/projects-and-solutions-image7.png)