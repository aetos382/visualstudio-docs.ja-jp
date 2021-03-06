---
title: クライアント ブロック用のフック関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 837307ac97cf52ff8d7073eaab54ec934d446eab
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279311"
---
# <a name="client-block-hook-functions"></a>Client ブロック用のフック関数
`_CLIENT_BLOCK` 型のブロックに格納されているデータの内容を検証したりレポートしたりするために、専用の関数を作成できます。 作成する関数には、CRTDBG.H で定義されている次のようなプロトタイプが必要です。  
  
```cpp
void YourClientDump(void *, size_t)  
  
```  
  
 つまり、独自のフック関数が受け入れる必要があります、 **void**と共に割り当てブロックの先頭を指すポインター、 **size_t**割り当てのサイズを示す値を入力し、返す`void`. それ以外の内容については、自由に決定できます。  
  
 フック関数を使用して、インストールすると[_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)、毎回呼び出されます、`_CLIENT_BLOCK`ブロックをダンプします。 使用することができますし、 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)型またはダンプされたブロックに情報を取得します。  
  
 渡す、関数へのポインター`_CrtSetDumpClient`の種類は **_CRT_DUMP_CLIENT**CRTDBG で定義されている、します。H:  
  
```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>関連項目  
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 サンプル](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)
