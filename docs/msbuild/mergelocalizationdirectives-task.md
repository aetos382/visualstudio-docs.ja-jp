---
title: MergeLocalizationDirectives タスク | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78cf1405cf3a09d43aab21c53e64644db29af0de
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077702"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives タスク
<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> タスクは、1 つ以上の [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] バイナリ形式ファイルのローカリゼーション属性とコメントを、アセンブリ全体で単一のファイルにマージします。  
  
## <a name="task-parameters"></a>タスク パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|必須の **ITaskItem[]** 型のパラメーターです。<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] バイナリ形式の個々のファイルに対するローカリゼーション ディレクティブ ファイルの一覧を指定します。|  
|`OutputFile`|省略可能な **String** 型の出力パラメーターです。<br /><br /> コンパイルされたローカリゼーション ディレクティブ アセンブリの出力パスを指定します。|  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] のコンテンツには、ローカリゼーション属性とコメントを追加できます。 [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] のローカリゼーション サポートを使用すると、ローカリゼーション属性とコメントを取り出し、生成されるアセンブリとは別の *.loc* ファイルに格納できます。 これを行うには、**LocalizationPropertyStorage** 属性を使用します。 ローカリゼーション属性とコメント、および **LocalizationPropertyStorage** の詳細については、「[ローカリゼーション属性とコメント](/dotnet/framework/wpf/advanced/localization-attributes-and-comments)」を参照してください。  
  
## <a name="example"></a>例  
 いくつかの [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] バイナリ形式ファイルのローカリゼーション コメントを単一の *.loc* ファイルにマージする方法を次の例に示します。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
[WPF MSBuild リファレンス](../msbuild/wpf-msbuild-reference.md)  
[WPF MSBuild タスク リファレンス](../msbuild/wpf-msbuild-task-reference.md)  
[MSBuild リファレンス](../msbuild/msbuild-reference.md)  
[MSBuild タスク リファレンス](../msbuild/msbuild-task-reference.md)  
[WPF アプリケーション (WPF) のビルド](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
