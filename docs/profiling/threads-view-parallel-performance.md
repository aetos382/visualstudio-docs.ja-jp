---
title: スレッド ビュー (並行処理のパフォーマンス) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2831dd07bcbb5e909357ebdf89496cf92bb815d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35669250"
---
# <a name="threads-view-parallel-performance"></a>スレッド ビュー (並行処理のパフォーマンス)
**スレッド ビュー**は、同時実行ビジュアライザーで最も詳細かつ豊富な機能を備えたビューです (**[分析]** > **[同時実行ビジュアライザー]** を選択して、同時実行ビジュアライザーを開始します)。 このビューを使用すると、スレッドが実行しているか、それとも同期、I/O、またはその他の何らかの理由のためにブロックしているかを識別できます。  
  
 同時実行ビジュアライザーは、プロファイルの分析中、アプリケーション スレッドごとに、すべてのオペレーティング システムのコンテキスト切り替えイベントを調べます。 コンテキストの切り替えは、次のような理由により発生することがあります。  
  
-   同期プリミティブでスレッドがブロックされた。  
  
-   スレッドのクォンタムの期限が切れた。  
  
-   スレッドがブロックの原因となる I/O 要求を実行した。  
  
 スレッド ビューでは、スレッドが実行を停止したときに、各コンテキストの切り替えにカテゴリが割り当てられます。 カテゴリは、ビューの左下の部分で凡例に表示されます。 同時実行ビジュアライザーは、よく知られているブロック API をスレッドの呼び出し履歴で検索することにより、コンテキストの切り替えイベントを分類します。 呼び出し履歴に一致するものがない場合には、[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] によって提供される待機理由が使用されます。 ただし、[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] のカテゴリは実装の詳細に基づく場合があり、ユーザーの意図を反映しない可能性があります。 たとえば [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] は、ネイティブのスリム リーダー/ ライター ロックでのブロックの待機理由を、同期ではなく I/O として報告します。 多くの場合、コンテキストの切り替えイベントに対応する呼び出し履歴を調べることにより、ブロック イベントの根本原因を識別できます。  
  
 スレッド ビューでは、スレッド間の依存関係も示します。 たとえば、同期オブジェクト上でブロックされているスレッドを見つけた場合、それをブロック解除したスレッドを探すことができます。それが他のスレッドをブロック解除した時点の呼び出し履歴で、スレッドのアクティビティを調べることができます。  
  
 スレッドの実行時に、同時実行ビジュアライザーはサンプルを収集します。 スレッド ビューでは、実行セグメント中に 1 つまたは複数のスレッドによって実行されるコードを分析できます。 ブロックのレポートや、呼び出し履歴のツリーの実行のプロファイルを示すレポートを確認することもできます。  
  
## <a name="usage"></a>使用法  
 スレッド ビューは、次のような目的に使用できます。  
  
-   アプリケーションのユーザー インターフェイス (UI) が特定の実行フェーズ中に応答しない理由を特定します。  
  
-   同期、I/O、ページ フォールト、その他のイベントでのブロックに費やされた時間を識別します。  
  
-   システム上で実行される他のプロセスからの干渉の程度を識別します。  
  
-   並列実行に関する負荷分散の問題を識別します。  
  
-   スケーラビリティが最適でない、またはスケーラビリティがない理由 (たとえば、より多くの論理コアが使用可能な場合に、並列アプリケーションのパフォーマンスが向上しない理由) を特定します。  
  
-   アプリケーションでの同時実行の程度を理解し、並列処理に役立てることができます。  
  
-   ワーカー スレッドと実行のクリティカル パスの間の依存関係を理解します。  
  
## <a name="examine-specific-time-intervals-and-threads"></a>特定の時間間隔とスレッドを調べる  
 スレッド ビューでは、タイムラインを示します。 タイムライン内でズームと手のひらツールを使って、特定の間隔と、アプリケーションのスレッドを調べることができます。 x 軸は時間を示し、y 軸は次のようないくつかのチャネルを示します。  
  
-   システム上のディスク ドライブごとに 2 つの I/O チャネル。1 つのチャネルは読み取り用で、もう 1 つは書き込み用です。  
  
-   プロセス内の各スレッドのチャネル。  
  
-   マーカー チャネル (トレースにマーカー イベントがある場合)。 マーカー チャネルは、それらのイベントを生成したスレッド チャネルの下に最初に表示されます。  
  
-   GPU チャネル。  
  
 スレッド ビューの例を次に示します。  
  
 ![スレッド ビュー](../profiling/media/threadsviewnarrowing.png "スレッド ビューの絞り込み")  
スレッド ビュー  
  
 最初にスレッドは、メイン アプリケーション スレッドが先頭になるように、作成された順に並べられます。 ビューの左上隅にある並べ替えオプションを使用すると、別の条件 (たとえば、実行作業の多い順) でスレッドを並べ替えることができます。  
  
 左側の列内で名前を選択してから、ツール バーで **[選択したスレッドを非表示にします]** ボタンを選択することにより、作業を実行していないスレッドを非表示にすることができます。 統計が無関係で、レポートの邪魔になるために完全にブロックされているスレッドは、非表示にするようお勧めします。  
  
 アクティブな凡例の中で、さらに非表示にするスレッドを識別するには、**[プロファイル レポート]** タブで **[スレッド別の概要]** レポートを選択します。実行ブレークダウン グラフが表示され、現在選択されている時間間隔についてスレッドの状態を確認できます。 ズーム レベルよっては、一部のスレッドは表示されないことがあります。 そのような場合は、右側に省略記号が表示されます。  
  
 時間の間隔とその中のいくつかのスレッドを選択すると、パフォーマンス分析を開始できます。  
  
## <a name="analysis-tools"></a>分析ツール  
 このセクションでは、レポートおよびその他の分析ツールについて説明します。  
  
### <a name="thread-blocking-details"></a>スレッドのブロックの詳細  
 スレッドの特定の領域でブロック イベントについての情報を取得するには、その領域にポインターを置いて、ヒントを表示します。 それには、カテゴリ、領域の開始時刻、ブロックの期間、ブロックしている API (存在する場合) などの情報が含まれています。 ブロックしている領域を選択すると、ヒントに表示される情報に加え、その時点の履歴が下部ウィンドウに表示されます。 呼び出し履歴を確認することにより、スレッドをブロックするイベントの根本原因を確認できます。 セグメントを選択し、[現在] タブを調べることによって、その他のプロセスとスレッドの情報を確認できます。  
  
 実行のパスには、複数のブロック イベントが含まれる場合があります。 こうしたイベントをブロック カテゴリごとに調べると、問題のある領域をより迅速に見つけることができます。 そのためには、左側の凡例のブロック カテゴリのいずれかを選択します。  
  
### <a name="dependencies-between-threads"></a>スレッド間の依存関係  
 同時実行ビジュアライザーでは、プロセス内のスレッド間の依存関係を確認できます。ブロックされたスレッドが何を実行しようとしていたかを判断し、他のどのスレッドがその実行を可能にしたかを知ることができます。 どのスレッドが別のスレッドをブロック解除したのかを確認するには、関連するブロック セグメントを選択します。 同時実行ビジュアライザーがブロック解除スレッドを判断できた場合、ブロック解除スレッドと、ブロック セグメントに続く実行セグメントが、線で結ばれます。 さらに、**[ブロック解除スタック]** タブには、関連する呼び出し履歴が示されます。  
  
### <a name="thread-execution-details"></a>スレッド実行の詳細  
 スレッドのタイムライン グラフで、緑のセグメントは、いつスレッドがコードを実行していたかを示します。 実行セグメントに関するさらに詳細な情報を取得できます。  
  
 実行セグメントでポイントを選択すると、同時実行ビジュアライザーは、関連する呼び出し履歴でその時点を検索し、実行セグメント内の選択したポイントの上に黒いキャレットを表示して、呼び出し履歴そのものを **[現在のスタック]** タブに表示します。実行セグメント上の複数のポイントを選択できます。  
  
> [!NOTE]
>  同時実行ビジュアライザーは、実行セグメント上の選択を解決できないことがあります。 通常、このエラーは、セグメントの期間が 1 ミリ秒未満である場合に発生します。  
  
 現在選択されている時間の範囲内で使用可能な (隠されていない) すべてのスレッドの実行プロファイルを取得するには、アクティブな凡例で **[実行]** ボタンを選択します。  
  
### <a name="timeline-graph"></a>タイムライン グラフ  
 タイムライン グラフは、プロセス内のすべてのスレッドのアクティビティと、ホスト コンピューター上のすべての物理ディスク デバイスを示します。 GPU アクティビティとマーカー イベントも表示されます。  拡大してさらに詳細な情報を表示することも、ズーム アウトしてさらに長い時間間隔を表示することもできます。 グラフ上のポイントを選択して、カテゴリ、開始時刻、存続期間、呼び出し履歴の状態に関する詳細を表示することもできます。  
  
 タイムライン グラフでは、色は特定の時点でのスレッドの状態を示します。 たとえば、緑のセグメントは実行されていたもの、赤いセグメントは同期のためにブロックされたもの、黄色のセグメントは優先処理によりブロックされたもの、紫色のセグメントはデバイスの I/O で占有されていたものです。 このビューを使用すると、並列ループまたは同時実行タスクに関係しているスレッド間での、作業負荷のバランスを確認できます。 あるスレッドが他のスレッドよりも完了に長い時間がかかっている場合、作業負荷がアンバランスになっている可能性があります。 この情報を使用して、スレッド間で作業負荷を均等に分散することにより、プログラムのパフォーマンスを向上させることができます。  
  
 ある時点で緑 (実行中) のスレッドが 1 つしかない場合、アプリケーションがシステム上の同時実行を十分に活用できていない可能性があります。 タイムラインのグラフを使用して、スレッド間の依存関係や、ブロックの原因となっているスレッドとブロックされるスレッドとの時間的な関係を確認できます。 スレッドを再配置するには、スレッドを選択してから、ツールバーで上矢印または下矢印ボタンをクリックします。 スレッドを非表示にするには、スレッドを選択し、**[スレッドを隠す]** ボタンをクリックします。  
  
### <a name="profile-reports"></a>プロファイル レポート  
 タイムライン グラフの下には、タイムライン プロファイルと、さまざまなレポートのタブを持つウィンドウがあります。 レポートは、スレッド ビューを変更すると、自動的に更新されます。 大規模なトレースの場合、更新が計算されている間はレポート ウィンドウを利用できないことがあります。 各レポートには、[不要項目の非表示] と [マイ コードのみ] という 2 つのフィルター調整があります。 [不要項目の非表示] を使用すると、時間をほとんど消費しないコール ツリー エントリが除外されます。 既定のフィルター値は 2% ですが、0% から 99% の範囲で調整できます。 自分のコードのコール ツリーのみを表示するには、**[マイ コードのみ]** チェック ボックスをオンします。 すべてのコール ツリーを表示するには、それをオフにします。  
  
#### <a name="profile-report"></a>プロファイル レポート  
 このタブには、アクティブな凡例内のエントリに対応するレポートが表示されます。 レポートを表示するには、エントリのいずれかを選択します。  
  
#### <a name="current-stack"></a>現在のスタック  
 このタブでは、タイムライン グラフ内のスレッド セグメントについて、選択した時点の呼び出し履歴が表示されます。 自分のプログラムに関連のあるアクティビティだけが表示されるように、呼び出し履歴は縮小表示されます。  
  
#### <a name="unblocking-stack"></a>ブロック解除スタック  
 選択されたスレッドをどのスレッドが、どのコード行でブロック解除したかを確認するには、**[ブロック解除スタック]** タブをクリックします。  
  
#### <a name="execution"></a>実行  
 実行レポートは、アプリケーションが実行に費やした時間の内訳を示します。  
  
 実行時間が費やされたコード行を検索するには、コール ツリーを展開してから、コール ツリー エントリのショートカット メニューで、**[ソースの表示]** または **[呼び出しサイトの表示]** を選択します。 **[ソースの表示]** では、実行されたコード行を検索します。 **[呼び出しサイトの表示]** では、実行されたコード行を呼び出したコード行を検索します。 呼び出しサイトが 1 つしか存在しない場合は、そのコード行が強調表示されます。 呼び出しサイトが複数存在する場合は、表示されるダイアログ ボックスで、1 つを選択できます。次に、**[ソースへ移動]** ボタンをクリックして、呼び出しサイト コードを強調表示します。 多くの場合、インスタンスが最も多い、または最も多くの時間を費やしている、あるいはそれら両方に当てはまる呼び出しサイト検索することが役立ちます。 詳細については、「[実行プロファイル レポート](../profiling/execution-profile-report.md)」を参照してください。  
  
#### <a name="synchronization"></a>同期  
 同期化レポートは、同期ブロックの原因となっている呼び出しと、各呼び出し履歴のブロック時間の総計を示します。 詳細については、「[同期時間](../profiling/synchronization-time.md)」を参照してください。  
  
#### <a name="io"></a>I/O  
 I/O レポートは、I/O ブロックの原因となっている呼び出しと、各呼び出し履歴のブロック時間の総計を示します。 詳細については、「[I/O 時間 (スレッド ビュー)](../profiling/i-o-time-threads-view.md)」を参照してください。  
  
#### <a name="sleep"></a>Sleep  
 スリープ レポートは、スリープ ブロックの原因となっている呼び出しと、各呼び出し履歴のブロック時間の総計を示します。 詳細については、「[スリープ時間](../profiling/sleep-time.md)」を参照してください。  
  
#### <a name="memory-management"></a>メモリ管理  
 メモリ管理レポートは、メモリ管理ブロックが発生した呼び出しと、各呼び出し履歴のブロック時間の総計を示します。 この情報を使用して、過剰なページングやガベージ コレクションの問題がある領域を特定できます。  詳細については、「[メモリ管理時間](../profiling/memory-management-time.md)」を参照してください。  
  
#### <a name="preemption"></a>優先  
 優先レポートは、システム上のプロセスが現在のプロセスよりも優先処理されたインスタンスと、現在のプロセス内のスレッドに取って代わった個々のスレッドを示します。 この情報を使用して、優先処理の主な原因となったプロセスとスレッドを特定できます。 詳細については、「[優先時間](../profiling/preemption-time.md)」を参照してください。  
  
#### <a name="ui-processing"></a>UI 処理  
 UI 処理レポートは、UI 処理ブロックの原因となっている呼び出しと、各呼び出し履歴のブロック時間の総計を示します。 詳細については、「[UI 処理時間](../profiling/ui-processing-time.md)」を参照してください。  
  
#### <a name="per-thread-summary"></a>スレッド別の概要  
 このタブでは、各スレッドが実行、ブロック、I/O、その他の状態にあった時間の総計を、色分けされた列で示します。 各列は、下部にラベルが付けられます。 タイムライン グラフでズーム レベルを調整すると、このタブは自動的に更新されます。 ズーム レベルよっては、一部のスレッドは表示されないことがあります。 そのような場合は、右側に省略記号が表示されます。 必要なスレッドが表示されない場合は、他のスレッドを非表示にすることができます。 詳細については、「[スレッド別の概要レポート](../profiling/per-thread-summary-report.md)」を参照してください。  
  
#### <a name="disk-operations"></a>ディスク操作  
 このタブでは、現在のプロセスのために、ディスク I/O に関与したプロセスとスレッド、それによって影響を受けたファイル (読み込まれた DLL など)、読み取られたバイト数、その他の情報を示します。 このレポートを使用して、実行中にファイルへのアクセスに費やされる時間を評価できます (特に、I/O バウンドなプロセスと思われる場合に役立ちます)。 詳細については、「[ディスク操作レポート](../profiling/disk-operations-report-threads-view.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [同時実行ビジュアライザー](../profiling/concurrency-visualizer.md)