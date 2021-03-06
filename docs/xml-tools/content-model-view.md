---
title: XML スキーマ デザイナーのコンテンツ モデル ビュー
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d7f04c482149cbc063a3788dd6be44c643bae6a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751794"
---
# <a name="content-model-view"></a>コンテンツ モデル ビュー

コンテンツ モデル ビューには、単純型、複合型、要素、モデル グループ、属性、属性グループなど、ローカル スキーマ ノードとグローバル スキーマ ノード、およびそのコンポーネントがグラフィック表示されます。 XML のコメントおよび処理命令は、コンテンツ モデル ビューには表示できません。 コンテンツ モデル ビューには、2 つのパネルが含まれています。**ワークスペース**パネル内のノードの一覧を含む、 [XML スキーマ デザイナーのワークスペース](../xml-tools/xml-schema-designer-workspace.md)、およびスキーマのコンテンツ モデルの参照先をデザイン サーフェイスノードで選択されている、**ワークスペース**パネルです。 さらにコンテンツ モデル ビューには、XML スキーマ デザイナーのツール バーおよび階層リンク バーがあります。

 次の図に、**ワークスペース**パネルには、6 つのスキーマ ノードが含まれています。 `purchaseOrder`でノードを選択、**ワークスペース**パネルし、は、デザイン画面に表示されます。

 ![XML スキーマ デザイナーのコンテンツ モデル ビュー](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>[ワークスペース] パネル

 ワークスペースにノードを追加すると、ノードの一覧に表示されます、**ワークスペース**コンテンツ モデル ビューのパネルです。 内のノードを選択すると、**ワークスペース**パネル、コンテンツ モデル ビューのデザイン画面に表示されます。 ワークスペースからノードを削除するには、XSD デザイナーのツールバーを使用して、**ワークスペース**パネルのコンテキスト メニューまたは**削除**キー。

 ノードを追加する方法についてを参照してください「を追加するワークスペースへのノード」 [XML スキーマ デザイナーのワークスペース](../xml-tools/xml-schema-designer-workspace.md)です。

## <a name="design-surface"></a>デザイン画面

 内のノードを選択すると、**ワークスペース**パネルで、ノードの詳細を表示できるコンテンツ モデル ビューのデザイン画面に追加されます。

 ノードのコンテンツ モデルは、展開可能なグラフィカル ツリーによって表現され、要素と属性がツリー ノードとして示されます。 既定では、1 レベルのみを展開できます。 コンポジター、型名、グループ、その他のコンテナーなど、それ以外の情報は、これらに含まれる要素および属性と共に、垂直バーに配置されます (展開時)。 垂直バーをダブルクリックすると、水平になり、ツリーが折りたたまれます。 水平バーをダブルクリックすると、垂直になり、ツリーが展開されます。 垂直バーを選択すると、コンテナー内のすべてのノードを選択します。 要素の展開または折りたたむことができる場合、ノードの右にエキスパンダーが表示されます。

 デザイン サーフェイスが空白の場合、XML エディター、 **XML スキーマ エクスプ ローラー**、され、レベルのウォーターマークが表示されます。 *ウォーターマーク*XSD デザイナーのすべてのビューへのリンクの一覧を示します。 スキーマ セットにエラーがある場合、一覧の最後に "スキーマ セット内のエラーを表示および修正するには、エラー一覧を使用します" というテキストが表示されます。

## <a name="breadcrumb-bar"></a>階層リンク バー

 コンテンツ モデル ビューの下部に表示される階層リンク バーは、選択したノードが存在するスキーマ セットの場所を示します。

## <a name="context-menus"></a>コンテキスト メニュー

 デザイン画面でアイテムを右クリックしたとき、または**ワークスペース**パネル、コンテキスト メニューが表示されます。 コンテンツ モデル ビューのデザイン サーフェイスに使用できるオプションを次の表に示します。

|オプション|説明|
|------------|-----------------|
|**XML スキーマ エクスプ ローラーで表示します。**|スキーマ エクスプローラーにフォーカスを置き、スキーマ セット ノードを強調表示します。|
|**グラフ ビューで表示します。**|グラフ ビューに切り替えます。|
|**サンプル XML を生成します。**|グローバル要素でのみ使用できます。 グローバル要素のサンプル XML ファイルを生成します。|
|**ドキュメントを表示します。**|注釈/ドキュメント ノードのコンテンツの表示と非表示を切り替えます。|
|**イメージとしてダイアグラムをエクスポートします。**|デザイン サーフェイスを XPS ファイルに保存します。|
|**コードの表示**|選択したノードを含むファイルが XML エディターで開きます。 選択されているアイテム、 **XML スキーマ エクスプ ローラー** XML エディターでもオンになっています。|
|**[プロパティ] ウィンドウ**|開く、**プロパティ**ウィンドウ (これがまだ開いていない) 場合。 このウィンドウには、ノードに関する情報が表示されます。|

 次の表で利用可能なオプション、**ワークスペース**パネルです。

|オプション|説明|
|------------|-----------------|
|**XML スキーマ エクスプ ローラーで表示します。**|スキーマ エクスプローラーにフォーカスを置き、スキーマ セット ノードを強調表示します。|
|**グラフ ビューで表示します。**|グラフ ビューに切り替えます。|
|**ワークスペースをクリアします。**|ワークスペースおよびデザイン サーフェイスをクリアします。|
|**ワークスペースからの削除します。**|ワークスペースおよびデザイン サーフェイスから選択したノードを削除します。|
|**ワークスペースからの選択以外はすべて削除します。**|ワークスペースおよびデザイン サーフェイスから選択されていないノードを削除します。|
|**サンプル XML を生成します。**|グローバル要素でのみ使用できます。 グローバル要素のサンプル XML ファイルを生成します。|
|**[すべて選択] します。**|内のすべてのノードを選択、**ワークスペース**パネルです。|
|**コードの表示**|選択したノードを含むファイルが XML エディターで開きます。 選択されているアイテム、 **XML スキーマ エクスプ ローラー** XML エディターでもオンになっています。|
|**[プロパティ] ウィンドウ**|開く、**プロパティ**ウィンドウ (これがまだ開いていない) 場合。 このウィンドウには、ノードに関する情報が表示されます。|

## <a name="properties-window"></a>[プロパティ] ウィンドウ

 開くには最初に、コンテキスト メニューを使用して、**プロパティ**ウィンドウです。 既定では、**プロパティ**Visual Studio の右下隅にウィンドウが表示されます。 そのノードのプロパティが表示されます、コンテンツ モデル ビューに表示されているノードをクリックすると、**プロパティ**ウィンドウです。

## <a name="xsd-designer-toolbar"></a>XSD デザイナーのツールバー

 コンテンツ モデル ビューがアクティブである場合に、次の XSD デザイナーのツール バー ボタンが表示されます。

 ![XML スキーマ デザイナーのツール バー](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|オプション|説明|
|------------|-----------------|
|**スタート ビューを表示します。**|切り替わり、[表示の開始](../xml-tools/start-view.md)です。 このビューは、キーボード ショートカットを使用してアクセスできます: **Ctrl**+**1**です。|
|**コンテンツ モデル ビューを表示します。**|切り替わり、[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)です。 このビューは、キーボード ショートカットを使用してアクセスできます: **Ctrl**+**2**です。|
|**グラフ ビューを表示します。**|切り替わり、[グラフ ビュー](../xml-tools/graph-view.md)です。 このビューは、キーボード ショートカットを使用してアクセスできます: **Ctrl**+**3**です。|
|**ワークスペースをクリアします。**|ワークスペースおよびデザイン サーフェイスをクリアします。|
|**ワークスペースからの削除します。**|ワークスペースおよびデザイン サーフェイスから選択したノードを削除します。|
|**ワークスペースからの選択以外はすべて削除します。**|ワークスペースおよびデザイン サーフェイスから選択されていないノードを削除します。|
|**ドキュメントを表示します。**|注釈/ドキュメント ノードのコンテンツの表示と非表示を切り替えます。|

## <a name="panscroll"></a>パン/スクロール

 デザイン サーフェイスをパンするには、スクロール バーを使用するか、保持している、 **Ctrl**キーをクリックして、マウスをドラッグします。 クリックしてドラッグ デザイン サーフェイスをパンした場合、カーソルは、4 つの方向を指す 4 つの交差矢印に変わります。

## <a name="undoredo"></a>元に戻す/やり直し

 元に戻す/やり直し機能は、コンテンツ モデル ビューの次の操作に対して有効です。

-   ドラッグ アンド ドロップして 1 つのノードを追加する。

-   スキーマ エクスプローラーの検索結果ウィンドウから複数のノードを追加する。

-   スタート ビューからノードを追加する。

-   1 つまたは複数のノードを削除する。

## <a name="zoom"></a>ズーム

 ズームはコンテンツ モデル ビューの右下隅で使用できます。

 ズームは、次の方法で制御できます。

-   押しながら、 **Ctrl**キーとマウスを回転してホイール マウスは、コンテンツ モデル ビューのサーフェイスを置いたときにします。

-   スライダー コントロールを使用する。 スライダーは現在のズーム レベルを示します。

選択して、マウス ポインターを置くか、または使用、ズーム スライダーが不透明である**Ctrl**が透過的なマウスのホイールを拡大する; 他のすべてのタイミングで、します。

## <a name="xml-editor-integration"></a>XML エディターとの統合

 間を切り替えることができます、 **XSD デザイナー**と XML エディター コンテキスト メニューを使用します。

 XML エディターでスキーマ セットに変更を加える場合は、コンテンツ モデル ビューに、変更が同期します。 詳細については、次を参照してください。 [XML エディターとの統合](../xml-tools/integration-with-xml-editor.md)です。

## <a name="see-also"></a>関連項目

- [XML スキーマ デザイナーのワークスペース](../xml-tools/xml-schema-designer-workspace.md)