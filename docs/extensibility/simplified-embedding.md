---
title: 埋め込みを簡略化 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 01b06a0a63059c39035d15221feb201d3674d4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142933"
---
# <a name="simplified-embedding"></a>埋め込み簡素化されます。
簡略化された埋め込みが有効になって、エディターでそのドキュメント ビュー オブジェクトの親 (つまり、実行の子) になれるとき[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、および<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>そのウィンドウのコマンドを処理するインターフェイスを実装します。 簡略化された埋め込みエディターには、アクティブなコントロールをホストできません。 簡略化された埋め込みエディターを作成するために使用オブジェクトは、次の図に表示されます。  
  
 ![簡略化された埋め込みエディター グラフィック](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
簡略化された埋め込みエディター  
  
> [!NOTE]
>  のみ、この図では、オブジェクトの`CYourEditorFactory`標準のファイル ベースのエディターを作成するオブジェクトが必要です。 カスタム エディターを作成する場合は、実装する必要はありません<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>エディター、独自のプライベートの永続化メカニズムがないため、します。 非カスタム エディターに対し、ただし、行う必要がありますようにします。  
  
 すべてのインターフェイスを簡素化された埋め込みエディターを作成するために実装が含まれている、`CYourEditorDocument`オブジェクト。 ただし、ドキュメント データの複数のビューをサポートするために分割データとビューの個別のオブジェクトに、インターフェイス、次の表に記載されています。  
  
|Interface|インターフェイスの場所|使用|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|表示|親ウィンドウへの接続を提供します。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|表示|コマンドを処理します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|表示|ステータス バーを更新できるようにします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|表示|により、**ツールボックス**項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|データ|ファイルが変更されたときに、通知を送信します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|データ|ファイルの種類の名前を付けて保存機能を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|データ|ドキュメントの永続性を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|データ|再読み込みをトリガーするなど、ファイルの変更イベントの抑制を使用できます。|