---
title: クラス ダイアグラムの使用 (クラス デザイナー)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams
- documentation, using class diagrams
- type shapes
- projects [Visual Studio], diagrams
- diagrams, class structure of projects
- class structure
ms.assetid: 37908cb7-f77b-4698-a4f9-3c21e5440fee
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3c099b63bcf73d3a028fb45a8867e672b023e62
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="work-with-class-diagrams-class-designer"></a>クラス ダイアグラムの使用 (クラス デザイナー)

クラス ダイアグラムは、他の開発者が作成した (または自分が以前に作成した) プロジェクトのクラス構造を理解するのに役立ちます。 このダイアグラムを使用すると、プロジェクト情報をカスタマイズして、開発者間で共有および提供できます。

プロジェクト情報を提供するには、まずその情報を表示するためのクラス ダイアグラムを作成します。 詳細については、「[型およびリレーションシップの表示](viewing-types-and-relationships.md)」を参照してください。 プロジェクトのクラス ダイアグラムを複数作成し、それらを使用して、プロジェクト自体のビュー、プロジェクトの型の特定のサブセット、または型のメンバーの特定のサブセットを表示できます。

各クラス ダイアグラムに表示する内容を定義するだけでなく、情報の提供方法を変更することもできます。詳細については、「[方法: クラス ダイアグラムをカスタマイズする](how-to-customize-class-diagrams.md)」を参照してください。

1 つまたは複数のクラス ダイアグラムを微調整した後、それらを Microsoft Office ドキュメント内にコピーして印刷したり、画像ファイルとしてエクスポートしたりできます。 詳細については、「[方法: Microsoft Office ドキュメントにクラス ダイアグラムの要素をコピーする](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md)」、「[方法: クラス ダイアグラムを印刷する](how-to-print-class-diagrams.md)」、「[方法: クラス ダイアグラムをイメージとしてエクスポートする](how-to-export-class-diagrams-as-images.md)」を参照してください。

> [!NOTE]
> クラス デザイナーはソース ファイルの場所を追跡しないので、プロジェクト構造を変更したり、プロジェクト内のソース ファイルを移動したりすると、クラス デザイナーが、特に typedef のソース型、基本クラス、またはアソシエーション型を追跡できなくなる場合があります。 **クラス デザイナーはこの型を表示できません**などのエラーが表示されることがあります。 エラーが発生した場合は、変更または再配置したソース コードをもう一度クラス ダイアグラムにドラッグして再表示します。


## <a name="see-also"></a>関連項目

- [型およびリレーションシップの表示](viewing-types-and-relationships.md)
- [方法: クラス ダイアグラムをカスタマイズする](how-to-customize-class-diagrams.md)
- [方法: クラス ダイアグラムから型シェイプを削除する方法](http://msdn.microsoft.com/ae41897d-d066-4b8c-bb9b-05436e12ff39)