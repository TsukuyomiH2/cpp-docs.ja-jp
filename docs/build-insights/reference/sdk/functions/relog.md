---
title: Relog
description: C++ Build Insights SDK の Relog 関数のリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 628f60042a10cf80c0b077d28387ed75466e925b
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922752"
---
# <a name="relog"></a>Relog

::: moniker range="<=msvc-140"

C++ Build Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio **Version** セレクター コントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。 このページの目次の一番上にあります。

::: moniker-end
::: moniker range=">=msvc-150"

`Relog` 関数は、Event Tracing for Windows (ETW) トレースから MSVC イベントを読み取り、それを新しい変更された ETW トレースに書き込むために使用されます。

## <a name="syntax"></a>構文

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>パラメーター

*TAnalyzerGroupMembers*\
このパラメーターは常に推測されます。

*TReloggerGroupMembers*\
このパラメーターは常に推測されます。

*inputLogFile*\
イベントの読み取り元の入力 ETW トレース。

*outputLogFile*\
新しいイベントを書き込むファイル。

*numberOfAnalysisPasses*\
入力トレースに対して実行する分析パスの数。 トレースは、指定されたアナライザー グループを通して、分析パスごとに 1 回渡されます。

*systemEventsRetentionFlags*\
再ログ記録されたトレースに保持するシステム ETW イベントを指定するビットマスク。 詳細については、「[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)」を参照してください。

*analyzerGroup*\
再ログ記録セッションの分析フェーズに使用されるアナライザー グループ。 アナライザー グループを作成するには、[MakeStaticAnalyzerGroup](make-static-analyzer-group.md) を呼び出します。 [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md) から取得された動的アナライザー グループを使用するには、最初に、そのアドレスを `MakeStaticAnalyzerGroup` に渡すことによって、静的なアナライザー グループ内にそれをカプセル化します。

*reloggerGroup*\
*outputLogFile* で指定されているトレース ファイルにイベントを再ログ記録するリロガー グループ。 リロガー グループを作成するには、[MakeStaticReloggerGroup](make-static-relogger-group.md) を呼び出します。 [MakeDynamicAnalyzerGroup](make-dynamic-relogger-group.md) から取得された動的リロガー グループを使用するには、最初に、そのアドレスを `MakeStaticReloggerGroup` に渡すことによって、静的リロガー グループ内にそれをカプセル化します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md) 列挙型の結果コード。

### <a name="remark"></a>注記

入力トレースは、アナライザー グループを通して *numberOfAnalysisPasses* 回渡されます。 再ログ記録パスには同様のオプションはありません。 トレースは、すべての分析パスの完了後に、リロガー グループを通して 1 回だけ渡されます。

CPU サンプルなどのシステム イベントをリロガー クラス内から再ログ記録することはサポートされていません。 出力トレースに保持するシステム イベントを決定するには、 *systemEventsRetentionFlags* パラメーターを使用します。

::: moniker-end
