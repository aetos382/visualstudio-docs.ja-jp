---
title: デバッガー イベントの呼び出し |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ae37a6f6ed180d13623a04afd357efcc109039f
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153034"
---
# <a name="call-debugger-events"></a>デバッガー イベントを呼び出す
デバッグ セッションでのイベントは、特定の順序で発生します。  
  
## <a name="discussion"></a>説明  
 デバッグ エンジン (DE) とセッション デバッグ マネージャー (SDM) 間の呼び出しのパターンを理解するには、次は、一般的なデバッグ セッションで発生するイベントの呼び出しの順序を表します。  
  
1.  [アタッチとデタッチをプログラムする](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [デバッガーを起動します。](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [プログラムの終了](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [ブレークポイントの作成](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [ときに、ブレークポイントがバインドまたはバインド解除になります。](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [ブレークポイント エラー](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [ブレークポイントのヒット](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [ブレークポイントの削除](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [中断モード](../../extensibility/debugger/entering-break-mode.md)  
  
10. [中断モードでのステップ実行](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [中断モードでの式の評価](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [例外処理](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>関連項目  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)