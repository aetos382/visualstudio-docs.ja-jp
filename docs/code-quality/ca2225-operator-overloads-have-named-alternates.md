---
title: "CA2225: 演算子のオーバー ロードは名前付けされた代替 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 07d15e5ec123e645a7607f16b6020487d4c0fc2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: 演算子オーバーロードには名前付けされた代替が存在します
|||  
|-|-|  
|TypeName|OperatorOverloadsHaveNamedAlternates|  
|CheckId|CA2225|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 演算子のオーバーロードが検出され、予想される名前の代替メソッドが検出されませんでした。  
  
## <a name="rule-description"></a>規則の説明  
 演算子のオーバー ロードは、型の計算を表すシンボルの使用を許可します。 たとえば、加算のプラス記号 (+) をオーバー ロードする型は、代替メンバー 'Add' という名前を通常があります。 名前付きの代替メンバーは、演算子と同じ機能へのアクセスを提供され、オーバー ロードされた演算子をサポートしない言語でプログラミングする開発者向けに提供されます。  
  
 このルールは、次の表に示す演算子を調べます。  
  
|C#|Visual Basic|C++|代替名|  
|---------|------------------|-----------|--------------------|  
|+ (バイナリ)|+|+ (バイナリ)|追加|  
|+=|+=|+=|追加|  
|&|および|&|BitwiseAnd|  
|&=|および =|&=|BitwiseAnd|  
|&#124;|または|&#124;|BitwiseOr|  
|&#124;=|または =|&#124;=|BitwiseOr|  
|--|N/A|--|Decrement|  
|/|/|/|除算|  
|/=|/=|/=|除算|  
|==|=|==|次の値に等しい|  
|^|Xor|^|Xor|  
|^=|Xor =|^=|Xor|  
|>|>|>|比較|  
|>=|>=|>=|比較|  
|++|N/A|++|インクリメント|  
|<>|!=|次の値に等しい|  
|<<|<<|<<|から|  
|<<=|<<=|<<=|から|  
|<|<|<|比較|  
|<=|<=|\<=|比較|  
|&&|N/A|&&|LogicalAnd|  
|&#124;&#124;|N/A|&#124;&#124;|LogicalOr|  
|!|N/A|!|LogicalNot|  
|%|Mod|%|剰余、つまり残りの部分|  
|%=|N/A|%=|Mod|  
|* (バイナリ)|*|*|乗算記号|  
|*=|N/A|*=|乗算記号|  
|~|Not|~|OnesComplement|  
|>>|>>|>>|プロパティ|  
=|N/A|>>=|プロパティ|  
|-(バイナリ)|-(バイナリ)|-(バイナリ)|減算|  
|-=|N/A|-=|減算|  
|TRUE|IsTrue|N/A|IsTrue (プロパティ)|  
|-(単項)|N/A|-|符号反転します。|  
|+ (単項)|N/A|+|プラス|  
|false|IsFalse|False|IsTrue (プロパティ)|  
  
 該当なし = =、選択した言語でオーバー ロードすることはできません。  
  
 ルールは、型の明示的および暗黙的なキャスト演算子も確認 (`SomeType`) という名前のメソッドを確認する`ToSomeType`と`FromSomeType`です。  
  
 C# の場合は、二項演算子をオーバー ロードすると、対応する、代入演算子、存在する場合も暗黙的にオーバー ロードされたできます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、演算子の代替メソッドを実装します。推奨される代替名を使用して名前を付けます。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 共有ライブラリを実装している場合は、この規則による警告は抑制しないでください。 アプリケーションは、この規則による警告を無視することができます。  
  
## <a name="example"></a>例  
 次の例では、この規則に違反する構造体を定義します。 解決するには例では、追加のパブリック`Add(int x, int y)`構造体へのメソッドです。  
  
 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)