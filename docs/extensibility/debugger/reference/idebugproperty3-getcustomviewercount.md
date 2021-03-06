---
title: IDebugProperty3::GetCustomViewerCount |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb04a772a9ca2a6bf63861c02e3c65870639da56
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117258"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
このプロパティで使用できる可能性のあるカスタム ビューアーの数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcelt`  
 [out]このプロパティの使用可能なカスタム ビューアーの数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 型のビジュアライザーをサポートするためには、このメソッドはへの呼び出しを転送、 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)メソッドです。 式エバリュエーターは、このプロパティの型のカスタム ビューアーをサポートする場合、このメソッドは、返される値をカスタム ビューアーの数を追加します。  
  
 ビジュアライザーの型とカスタム ビューアーの違いの詳細については、次を参照してください。[型ビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)です。  
  
## <a name="example"></a>例  
 次の例に対して、このメソッドを実装する方法を示しています、 **CProperty**を公開するオブジェクト、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)インターフェイスです。  
  
```cpp  
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)  
{  
    if (pcelt == NULL)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)