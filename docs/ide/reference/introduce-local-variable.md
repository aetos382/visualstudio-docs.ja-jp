---
title: "Visual Studio でローカル変数を導入する | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 997220d3b1a7305f84f61ee5fd4c205d1157f1b2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Visual Studio でローカル変数を導入する

このコード生成は以下に適用されます。

- C#

- Visual Basic

**機能:** 既存の式を置換するローカル変数をすぐに生成できます。

**条件:** ローカル変数内で使用されていれば、後で簡単に再利用できるコードがあるとき。

**理由:** コードは複数回コピーして貼り付け、さまざまな場所で使用できるが、一度の実行で、結果を 1 つのローカル変数に格納し、そのローカル変数を全体で使用する方が良いため。

## <a name="how-to"></a>方法

1. 新しいローカル変数に割り当てる式を強調表示します。

   - C#: 

    ![強調表示された C# のコード](media/local-highlight-cs.png)

   - Visual Basic: 

    ![強調表示された VB のコード](media/local-highlight-vb.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーします。
   - **マウス**
     - 右クリックして **[クイック アクションとリファクタリング]** メニューを選択します。
     - テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

   ![ローカル導入のプレビュー](media/local-preview-cs.png)

1. ドロップダウン メニューから **['<*式*>' のすべての発生に対してローカルを導入します]** を選択します。

   > [!TIP]
   > プレビュー ウィンドウの下部にある **[変更のプレビュー]** リンクを使うと、選択する前に、行われる[すべての変更を確認する](../../ide/preview-changes.md)ことができます。

   ローカル変数と、その使用法から推論された型が作成されます。 新しいローカル変数に新しい名前を付けます。

   - C#: 

      ![インターフェイスの実装の結果 (C#)](media/local-result-cs.png)

   - Visual Basic: 

      ![インターフェイスの実装の結果 (VB)](media/local-result-vb.png)

   > [!NOTE]
   > **[...のすべての発生に対して]** メニュー オプションを使うと、明示的に強調表示したインスタンスだけでなく、選択した式のすべてのインスタンスを置換できます。

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)