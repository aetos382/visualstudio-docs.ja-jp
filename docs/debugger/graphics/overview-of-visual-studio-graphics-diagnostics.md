---
title: "Visual Studio グラフィックス診断の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/09/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddd429d9-ac70-4ac4-9e69-299c6ea2df09
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f713a1ced59ea1ed0eaf01a3d9630aa96e4c6bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Visual Studio グラフィックス診断の概要
Visual Studio*グラフィックス診断*を記録し、Direct3D アプリのレンダリングとパフォーマンスの問題を分析するためのツールのセットです。 グラフィックス診断は、Windows PC でローカルに実行されているアプリ、Windows デバイス エミュレーターで実行されているアプリ、あるいはリモート PC またはデバイスで実行されているアプリに対して使用できます。  
  
## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>グラフィックス診断を使用したレンダリング問題のデバッグ  
 グラフィックを多用したアプリのレンダリングに関する問題のデバッグは、デバッガーを起動してコードをステップ実行するような簡単な作業ではありません。 各フレームでは、状態、データ、パラメーター、およびコードの複雑なセットに応じて、何百何千もの一意のピクセルが生成され、そのような診断対象のうち、問題が発生しているのはほんの少数である場合があります。 さらに複雑なことに、各ピクセルを生成するコードは、何百ものピクセルを並列に処理する特別なハードウェアで実行されます。 スレッドが少ないコードに対してさえ活用が困難な従来のデバッグ ツールおよび方法は、大量のデータに対応するときに役に立ちません。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のグラフィックス診断ツールは、レンダリングに関する問題の特定に役立つように設計されています。まず、問題を示している表示の不具合から開始して、次に、アプリのソース コード内で、関連するシェーダー コード、パイプライン ステージ、描画呼び出し、リソース、およびデバイスの状態だけに注目することにより問題の原因までさかのぼってトレースします。  
  
## <a name="directx-version-compatibility"></a>DirectX のバージョンの互換性  
 グラフィックス診断は Direct3D 10 以上を使用するアプリをサポートし、Direct2D を使用するアプリの制限付きサポートを提供します。 旧バージョンの Direct3D、DirectDraw、または他のグラフィックス API を使用するアプリケーションはサポートしません。  
  
### <a name="windows-10-and-direct3d-12"></a>Windows 10 と Direct3D 12  
 Windows 10 の導入*direct3d12*、これは大幅に異なる direct3d10 と direct3d11 です。 これらの違いは、DirectX を最新のグラフィックス ハードウェアに合わせて調整し、その潜在能力を十分に引き出すために生じたものですが、それによって API にも大幅な変更が必要となり、リソースの有効期間と競合を管理する仕事がこれまで以上にプログラマの責任になりました。 違いは、direct3d12 のグラフィックス診断は、direct 3 d 11.2 のグラフィックス診断に機能パリティを維持します。
  
 Windows 10 では、前のバージョンの Direct3D と、それらに依存するゲームやアプリケーションも引き続きサポートされます。 Visual Studio でのグラフィックス診断は、Windows 10 および Windows 8.1、direct3d10 と direct3d11 をサポートするために続行します。  
  
### <a name="windows-81-and-direct3d-112"></a>Windows 8.1 および Direct3D 11.2  
 [!INCLUDE[win81](../includes/win81_md.md)] では、DirectX 11.2 は新機能を導入しており、ランタイムを通じてグラフィックス情報をキャプチャするためのサポートが含まれています。 [!INCLUDE[win81](../includes/win81_md.md)]新しいランタイムに基づくキャプチャを使用する: と呼ばれる*ロバスト キャプチャ*: 排他的すべてのバージョンの DirectX を[!INCLUDE[win81](../includes/win81_md.md)]をサポートしています。 ロバスト キャプチャは、Direct3D 11.2 の新機能もサポートしています。  
  
### <a name="limited-direct2d-support"></a>Direct2D の制限されたサポート  
 Direct2D は、Direct3D 上に組み込まれているユーザー モード API であるために、Direct2D を使用するアプリのレンダリングに関する問題をデバッグする際に、グラフィックス診断を使用することができます。 ただし、上位レベルの Direct2D イベントの代わりに、基になる Direct3D イベントのみが記録されるため、Direct2D イベントはグラフィックス イベント一覧に表示されません。 また、Direct2D イベントと結果の Direct3D イベントの間の関連性が必ずしも明らかではないため、Direct2D を使用するアプリのレンダリングに関する問題をデバッグするためにグラフィックス診断を使用することは複雑です。 それでも、グラフィックス診断を使用して Direct2D を使用するアプリケーションで発生する低水準のレンダリングに関する問題の情報は取得できます。  
  
## <a name="graphics-diagnostics-features-in-visual-studio"></a>Visual Studio のグラフィックス診断機能  
 グラフィックス診断専用のインターフェイスの Graphics Analyzer ウィンドウのレンダリングの問題の診断が Visual Studio のインターフェイスにもいくつかのツールを追加します。  
  
### <a name="the-graphics-toolbar-visual-studio"></a>[グラフィックス] ツール バー (Visual Studio)  
 [グラフィックス] ツール バーを使用すると、グラフィックス診断コマンドにすばやくアクセスできます。  
  
 **診断の開始**ボタンは、グラフィックス診断の下でアプリを実行します。 アプリがグラフィックス診断の下で実行されている場合、**次の描画フレームをキャプチャ**ボタンが有効にします。  
  
### <a name="diagnostics-capture-interface"></a>診断キャプチャのインターフェイス  
 グラフィックス診断の下でアプリを実行すると、Visual Studio には診断セッションのインターフェイスが表示され、フレームをキャプチャする際に使用したり、現在の CPU および GPU の負荷を表示したりできます。 CPU と GPU の負荷を表示すると、キャプチャしようとしているフレームがレンダリングのエラーではなくパフォーマンス特性のために問題を起こしているかどうかを識別できます。  
  
 フレームをキャプチャする方法はほかにもあります。 プログラムによるキャプチャ インターフェイスや、キャプチャを行うコマンド ライン プログラム dxcap.exe を使用して、フレームをキャプチャすることもできます。  
  
 参照してください[グラフィックス情報のキャプチャ](capturing-graphics-information.md)詳細についてはします。  
  
### <a name="gpu-usage"></a>GPU 使用率  
 グラフィックス診断では、Direct3D アプリのパフォーマンスのプロファイリングを行うこともできます。 グラフィックス イベントを詳細に記録している間は正確なプロファイリング データを取得できないことがあるため、この診断は Graphics Analyzer による調査で使用するフレームのキャプチャとは別個に行います。  
  
 参照してください[GPU 使用率](gpu-usage.md)詳細についてはします。  
  
### <a name="directx-control-panel"></a>DirectX コントロール パネル  
 DirectX コントロール パネルは、DirectX の動作を変更するために使用できる、DirectX のコンポーネントです。たとえば、DirectX のランタイム コンポーネントのデバッグ バージョンを有効にする、報告されるデバッグ メッセージの種類を選択する、および処理能力の低いハードウェアをエミュレートするために一部のグラフィックス ハードウェア機能が使用されないようにすることができます。 DirectX に対するこのレベルの制御は、DirectX アプリケーションのデバッグとテストに役立ちます。 Visual Studio から DirectX コントロール パネルにアクセスできます。  
  
#### <a name="to-open-the-directx-control-panel"></a>DirectX コントロール パネルを開くには  
  
-   メニュー バーで、次のように選択します。**デバッグ**、**グラフィックス**、 **DirectX コントロール パネル**です。  
  
## <a name="graphics-analyzer"></a>Graphics Analyzer  
 Visual Studio Graphics Analyzer は、あらかじめキャプチャしたフレームからレンダリングとパフォーマンスの問題を調べるための専用のインターフェイスです。 Graphics Analyzer には、アプリのレンダリング動作を探索して理解するために役立ついくつかのツールがあります。 各ツールは、調査対象のフレームについて異なる種類の情報を明らかにします。それらのツールは、連携して使用し、フレームバッファーの外観から始めて、レンダリングの問題の原因を直感的に絞り込んでいくように設計されています。  
  
 Graphics Analyzer のツールの一般的なレイアウトを次の図に示します。  
  
 ![すべてのグラフィックス デバッガー ウィンドウ](media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")  
  
### <a name="the-graphics-toolbar-graphics-analyzer"></a>[グラフィックス] ツール バー (Graphics Analyzer)  
 [グラフィックス] ツール バーを使用すると、Graphics Analyzer のツール ウィンドウにすばやくアクセスできます。  
  
 ![グラフィックス診断モードの [グラフィックス] ツールバー](media/vsg_toolbar.png "vsg_toolbar")  
  
### <a name="graphics-log-document"></a>グラフィックス ログ ドキュメント  
 Graphics Analyzer の中で、グラフィックス ログ ドキュメントはいちばん目立つツール ウィンドウです。 このウィンドウは、グラフィックス診断の下でアプリを実行してキャプチャしたすべてのフレームを表します。 このウィンドウでは、調査する別のフレームを選択したり、調査する特定のピクセルをピクセル履歴ツールを使用して選択したりできます。 このドキュメントに表示されるフレームバッファー イメージは、現在選択されているイベントを反映して変更されるので、時間の経過と共にそのイベントがフレームバッファーに与える影響を確認できます。  
  
 [グラフィックス ログ ドキュメント](graphics-log-document.md)もを支援するフレーム分析ツールへのエントリ ポイントのパフォーマンスを理解フレームは、レンダリングの特定の要素の構成方法を変更してベンチマーク結果を提供します。オリジナルを比較します。  
  
### <a name="event-list"></a>イベント一覧  
 グラフィックのイベントは、各 Direct3D API 呼び出しとユーザー定義のイベントをマークします。  
  
 [イベント一覧](graphics-event-list.md)すべてのフレームを調査している間に記録されたグラフィックス イベントを示しています。 重要な要素を見つけやすくするため、イベント一覧は階層的に表示することができます。たとえば、後続の描画呼び出しの下に最新の状態変化を表示したり、タイムラインとして表示したりできます。 さらに、イベントはどのキューに属しているかに基づいて色分け表示され、調査したいイベントだけを表示するように一覧をフィルター処理することもできます。  
  
 一覧から 1 つのイベントを選択すると、グラフィックス分析ツールの残りの部分は、そのイベントの時点でのフレームの状態を反映して表示されます。 このようにして、GPU 上での任意のイベントの影響を確認できます。 たとえば、後続の描画呼び出しによって覆い隠されてしまう場合でも、フレームバッファー上での任意の描画呼び出しの直接的な効果を見ることができます。 また、一部のイベントにはハイパーリンクが付けられ、そのパラメーターの詳細や関連するリソース オブジェクトを参照することができます。  
  
### <a name="pipeline-stages"></a>パイプライン ステージ  
 アプリ内の各描画呼び出しは、Direct3D によって提供されるグラフィックス パイプラインを通ります。 パイプライン内の各ステージでは、前のステージからの出力がシェーダーと呼ばれる小さなプログラムによって変換されて次のステージに渡され、画面が最終的にレンダリングされるまでこれが続きます。 多くのレンダリング エラーは、パイプラインのステージ間の境界で出力形式が次のステージが想定しているものと違っていたり、いずれか 1 つのステージで単に間違った結果が生成されたりした場合に発生します。 通常は、画面に表示される最終的な結果だけを見ているため、パイプラインの中のどこでエラーが発生しているかを簡単に識別することはできません。  
  
 [パイプライン ステージ](graphics-pipeline-stages.md)ウィンドウ視覚化個別に各ステージの結果されていない、レンダリングの問題が最初に表示されますどのステージをより簡単に判断できるようにします。 それがどのステージであるかを判別した後は、[バイブライン ステージ] ウィンドウのその場所からシェーダーのデバッグを開始できます。  
  
### <a name="graphics-state"></a>グラフィックスの状態  
 レンダリング操作は、通常、複数のオブジェクトに分散した多数の状態に依存して決まります。 多くの種類のレンダリングの問題は、状態が正しく構成されないことが原因で発生します。  
  
 [状態](graphics-state.md)ウィンドウを検索しやすくしても前の後に発生した状態の変更の重要なポイントの描画呼び出しように各描画呼び出しが 1 か所でまとめてに関連する状態情報を収集します。  
  
### <a name="pixel-history"></a>ピクセル履歴  
 複雑なシーンでは、1 つのフレーム内で 1 つのピクセルが複数回にわたってシェーダーで処理されることも珍しくありません。 以前の色を上書きするだけの場合もあれば、色が結合されて透明などの効果を実現する場合もあります。 そのすべてを組み合わせた結果が正しい外観にならない場合、いずれか 1 つの色が間違っているのか、色を結合する方法が間違っているのかを識別するのは困難です。 場合によっては、ピクセルに対する色の適用が何らかの理由で拒否されたため、オブジェクトが欠落しているように見えることがあります。  
  
 [ピクセル履歴](graphics-pixel-history.md) ウィンドウの視覚化の適用を拒否されたを含む、フレームのすべてのピクセル シェーダーの完全な履歴。 適用を拒否された色については、未加工のシェーダーの結果と、以前の色に新しい各色が結合される様子が表示されます。 この情報を見ると、シェーダーの結果を混ぜ合わせたピクセルの間違いの原因を比較的簡単に見つけたり、レンダリングされたオブジェクトが欠落している原因がピクセルへの色の適用を不適切に拒否されたことにあると判別したりできます。  
  
### <a name="event-call-stack"></a>イベント呼び出し履歴  
 Direct3D アプリのレンダリングに関する問題は、シェーダー コードが唯一の原因ではありません。時には、アプリのソース コードが間違ったパラメーターを渡したり、Direct3D を適切に構成していなかったりする場合があります。 前に説明したピクセル履歴の機能を使用して判別できる 1 つの種類のエラーは、レンダリングしたオブジェクトのすべてのピクセルが拒否されたために、そのオブジェクトが欠落しているというケースです。 この種のエラーは、通常、設定を適切に構成していない場合に発生します。たとえば、深度テストの実行を制御する構成が適切でない場合は、欠落しているオブジェクトの描画呼び出しの呼び出し履歴内に間違いが見つかることがよくあります。  
  
 [イベント呼び出し履歴](graphics-event-call-stack.md)ウィンドウ イベント一覧で、すべてのグラフィックス イベント呼び出し履歴を表示して、ソース コードのデバッグ情報が利用可能な場合、アプリにジャンプすることさえできます。 これは、エラーが最初に発見された GPU 上の場所から跡をたどり、アプリのソース コードに戻って問題の発生場所を突き止めることのできる強力なツールです。  
  
### <a name="object-table"></a>オブジェクト テーブル  
 アプリでレンダリングするすべてのフレームの背後には、おそらく数百、あるいは数千ものリソース オブジェクトが存在します。 たとえば、バック バッファー、レンダー ターゲット、テクスチャ、頂点バッファー、インデックス バッファー、汎用バッファーなど、Direct3D が記憶しているほとんどすべてのものがオブジェクトです。  
  
 [オブジェクト テーブル](graphics-object-table.md)すべて選択したグラフィックス イベントの時点で存在するオブジェクト、イベントの一覧が表示されます。 標準的なアプリのほとんどのオブジェクトはテクスチャであるため、イベントの一覧は、画像に関連する詳細が一目で分かるように最適化されています。 [種類] の列には、各行が表しているオブジェクトの種類が示され、[形式] の列には、下位の種類やオブジェクトのバージョンが示されます。 その他の詳細も表示されます。 一部のオブジェクトには、より専門的なビューアーでオブジェクトを表示するためのハイパーリンクが表示されます。たとえば、テクスチャであれば、テクスチャを画像として表示することができます。また、バッファーであれば、バッファーのフォーマットを定義することにより、バッファー ビューアーが未加工のバッファー バイトを解析して表示する方法を選択できます。  
  
### <a name="frame-analysis"></a>フレーム分析  
 アプリのグラフィックスだけ入れなくて正しい - すぎるで高速である必要があります。 統合型グラフィックスを搭載したノート PC や、携帯電話など、性能が限られたデバイスでも、高速に表示される必要があります。 しかも、美しく表示される必要があります。  
  
 [フレーム分析](graphics-frame-analysis.md)ツールは、アプリが Direct3D を使用する方法を自動的に変更して、比較のベンチマークの結果を提供することにより、潜在的なパフォーマンスを最適化します。 たとえば、フレーム分析では、すべてのテクスチャに対して MIP マッピングを有効にして、そのテクスチャが MIP マッピングからメリットを得られるかどうかを明らかにできますが、現在その機能は有効にされていません。 また、ハードウェアがサポートしている場合、フレーム分析では、GPU のパフォーマンス カウンターから収集した情報を提示できます。このレベルの情報があれば、多数のテクスチャのフェッチ停止やキャッシュ ミスなど、ハードウェア レベルのパフォーマンスの問題を識別できます。  
  
 フレーム分析が高速移動されていないあらゆる - について最小限の画質を提供中にできるほとんどのパフォーマンスを得ることがします。 時には、大きなディスプレイで優れた効果を発揮する高負荷の処理が、携帯電話のような小さな画面で見るとそれほど効果を発揮しないことがあります。その場合、バッテリを消費しないように低負荷の処理にしたほうが適切であると考えられます。 自動的な変更とベンチマーク グラフィックス分析を提供することは、範囲のデバイス間で、アプリの適切なバランスを見つけるの向上に役立ちます。  
  
## <a name="see-also"></a>関連項目  
 [コマンド ライン キャプチャ ツール](command-line-capture-tool.md)   
 [HLSL デバッガー](hlsl-shader-debugger.md)