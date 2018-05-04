---
title: Visual Studio でのロード テスト結果の概要
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 989ebc629e79194fb6cd4c900b032cb93a090977
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="load-test-results-summary-overview"></a>ロード テスト結果の概要

ロード テストを実行した後、ロード テストの概要を表示して直ちにテスト結果を把握できます。 ロード テストの概要には、主要な結果がわかりやすい形式で簡潔にまとめられています。 ロード テストの概要を印刷することもできます。 これによって利害関係者に結果を伝えるのが容易になります。 前に実行したロード テストからロード テスト結果を開くと、ロード テストの概要が既定のビューになります。 詳細については、「[方法 : ロード テストの結果にアクセスして分析する](../test/how-to-access-load-test-results-for-analysis.md)」を参照してください。

 ![概要ビュー](../test/media/ltest_summaryview.png "LTest_SummaryView")

## <a name="the-load-test-summary"></a>ロード テストの概要

ロード テストの概要は複数のセクションに分かれています。 最初のセクションは概要の上部に位置し、常に表示されます。 ロード テストの概要を表示した場合、先頭には以下の項目があります。

- テストの実行情報

- 全体の結果

- 基本統計: 低速ページ トップ 5

- 基本統計: 低速テスト トップ 5

- 基本統計: 低速 SQL 操作 トップ 5

    > [!NOTE]
    > SQL 操作のセクションは、ロード テストで SQL トレースを有効にした場合のみ表示されます。

終わりのセクションは概要の末尾に位置し、スペースの節約のために折りたたむことができます。 ロード テストの概要の末尾には、以下の項目が表示されます。

- テスト結果

- ページ結果

- トランザクション結果

- テスト リソース下のシステム

- コントローラーおよびエージェント リソース

- エラー

## <a name="test-run-information"></a>テストの実行情報

このセクションには、テストの名前、開始時刻と終了時刻、テストを実行したコントローラーなど、テストの実行に関する一般的な情報が表示されます。 また、ロード テストの実行時に入力した実行の説明も表示されます。

## <a name="overall-results"></a>全体の結果

このセクションには、1 秒あたりの要求数、失敗した要求の総数、平均応答時間、平均ページ時間など、テスト結果の概要が表示されます。

## <a name="key-statistic-top-5-slowest-pages"></a>基本統計: 低速ページ トップ 5

このセクションには、ロード テストで表示速度が遅かったページ上位 5 件が表示されます。 各ページについて、URL と平均ページ読み込み時間が表示されます。 ページは降順に一覧されます。 ページの URL を選択すると、**[ページ]** テーブルが表示され、そのページの詳細を調べることができます。 詳細については、[Web ページ応答を表示する方法](../test/how-to-view-web-page-response-time-in-a-load-test.md)に関するページを参照してください。

**95% ページ時間 (秒)** のパーセンタイル値は、ページの 95% が完了している時間を秒で示します。

## <a name="key-statistic-top-5-slowest-tests"></a>基本統計: 低速テスト トップ 5

このセクションには、ロード テストで実行速度が遅かったテスト上位 5 件が表示されます。 各テストについて、テスト名と平均テスト時間が表示されます。 テストは降順に一覧されます。 テストの名前を選択すると、**[テスト]** テーブルが表示され、そのテストの詳細を調べることができます。 詳細については、[テーブル ビューでのロード テスト結果の分析](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)に関するページを参照してください。

**95% テスト時間 (秒)** のパーセンタイル値は、テストの 95% が完了している時間を秒で示します。

## <a name="key-statistic-top-5-slowest-sql-operations"></a>基本統計: 低速 SQL 操作 トップ 5

ロード テストで SQL トレースを有効にした場合は、このセクションにロード テストで処理速度が遅かったクエリ上位 5 件が表示されます。 各テストについて、操作の名前と実行時間が表示されます。 期間はマイクロ秒 (SQL Server 2005) またはミリ秒 (SQL Server 2000 以前のバージョン) で表示されます。 テストは期間別に降順に一覧表示されます。 操作の名前を選択すると、**[SQL トレース]** テーブルが表示され、その操作の詳細を調べることができます。 詳細については、「[[SQL トレース データ] テーブル](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table)」を参照してください。

## <a name="test-results"></a>テスト結果

このセクションには、ロード テストに含まれるテストおよびシナリオの一覧があります。 テストの名前、シナリオ、テストの実行回数、失敗した回数、および平均テスト時間が表示されます。 テストの名前を選択すると、**[テスト]** テーブルが表示され、そのテストの詳細を調べることができます。 詳細については、[テーブル ビューでのロード テスト結果とエラーの分析](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)に関するページを参照してください。

> [!NOTE]
> このセクションは、セクション タイトルの左側の矢印を選択して折りたたんだり展開したりできます。

## <a name="page-results"></a>ページ結果

このセクションには、ロード テストに含まれる Web ページの一覧があります。 URL、シナリオ、テストの名前、平均ページ時間、およびカウントが表示されます。 ページの URL を選択すると、**[ページ]** テーブルが表示され、そのページの詳細を調べることができます。 詳細については、[Web ページ応答を表示する方法](../test/how-to-view-web-page-response-time-in-a-load-test.md)に関するページを参照してください。

> [!NOTE]
> このセクションは、セクション タイトルの左側の矢印を選択して折りたたんだり展開したりできます。

## <a name="transaction-results"></a>トランザクション結果

このセクションには、ロード テストに含まれるトランザクションの一覧があります。 トランザクションの名前、シナリオ、テスト、応答時間、経過時間、およびカウントが表示されます。 トランザクションの名前を選択すると、**[トランザクション]** テーブルが表示され、そのトランザクションの詳細を調べることができます。 詳細については、[テーブル ビューでのロード テスト結果とエラーの分析](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)に関するページを参照してください。

> [!NOTE]
> このセクションは、セクション タイトルの左側の矢印を選択して折りたたんだり展開したりできます。

次のトランザクション情報がパーセンタイル値でレポートされます。

-   トランザクション合計の 90% が \<time> 秒未満で完了した。

-   トランザクション合計の 95% が \<time> 秒未満で完了した。

## <a name="system-under-test-resources"></a>テスト リソース下のシステム

このセクションには、負荷の生成対象となるコンピューターの一覧があります。 この一覧には、エージェントやコントローラーを除き、カウンター セットの収集元となるすべてのコンピューターが含まれます。 コンピューター名、プロセッサ時間の割合、およびメモリの容量が表示されます。 コンピューター名を選択すると、**[テスト下のシステム]** グラフが表示され、時間の経過によるリソース使用率の変化を確認できます。 詳細については、「[グラフ ビューでのロード テスト結果の分析](../test/analyze-load-test-results-in-the-graphs-view.md)」を参照してください。

> [!NOTE]
> このセクションは、セクション タイトルの左側の矢印を選択して折りたたんだり展開したりできます。

## <a name="controller-and-agent-resources"></a>コントローラーおよびエージェント リソース

このセクションには、テストの実行に使用したコンピューターの一覧があります。 コンピューター名、プロセッサ時間の割合、およびメモリの容量が表示されます。 コンピューター名を選択すると、**[コントローラーおよびエージェント]** グラフが表示され、時間の経過によるリソース使用率の変化を確認できます。 詳細については、「[グラフ ビューでのロード テスト結果の分析](../test/analyze-load-test-results-in-the-graphs-view.md)」を参照してください。

> [!NOTE]
> このセクションは、セクション タイトルの左側の矢印を選択して折りたたんだり展開したりできます。

## <a name="errors"></a>エラー

このセクションには、ロード テストの実行中に発生したエラーの一覧があります。 エラーのタイプとサブタイプ、カウント、および最後のメッセージが表示されます。 エラーを選択すると、**[エラー]** テーブルが表示され、そのエラーの詳細を調べることができます。 詳細については、「[Analyze Load Test Results and Errors in the Tables View](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)」(テーブル ビューでのロード テスト結果とエラーの分析) と「[方法: カウンター パネルを使用してエラーを分析する](../test/how-to-analyze-errors-using-the-counters-panel.md)」を参照してください。

> [!NOTE]
> このセクションは、セクション タイトルの左側の矢印を選択して折りたたんだり展開したりできます。

## <a name="printing-a-summary"></a>概要の印刷

ロード テストの概要を印刷するには、概要ページを右クリックし、ショートカット メニューの **[印刷]** を選択します。 印刷プレビューを表示するには、概要ページを右クリックし、ショートカット メニューの **[印刷プレビュー]** を選択します。 プレビュー画面からそのまま印刷を開始することもできます。

## <a name="see-also"></a>関連項目

- [しきい値規則違反の分析](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)