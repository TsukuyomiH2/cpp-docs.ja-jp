---
description: '詳細については、「チュートリアル: 軽量タスクを使用するための既存のコードの調整」を参照してください。'
title: 'チュートリアル: 既存のコードを改変して軽量タスクを使用する'
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: 1c3de0f49dc1edc3392a436bb911e005ef84bcf0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271409"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>チュートリアル: 既存のコードを改変して軽量タスクを使用する

ここでは、Windows API を使用する既存のコードを改変して、軽量タスクを使用するスレッドを作成および実行する方法について説明します。

*軽量タスク* は、 [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md)オブジェクトまたは [concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)オブジェクトから直接スケジュールするタスクです。 軽量タスクは、既存のコードを改変してコンカレンシー ランタイムのスケジュール機能を使用する場合に有用です。

## <a name="prerequisites"></a>前提条件

このチュートリアルを開始する前に、「 [タスクスケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)」を参照してください。

## <a name="example"></a>例

Windows API を使用してスレッドを作成および実行する一般的な方法を次の例に示します。 この例では、 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) 関数を使用して、 `MyThreadFunction` 別のスレッドでを呼び出します。

### <a name="initial-code"></a>最初のコード

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
Parameters = 50, 100
```

コンカレンシー ランタイムを使用して同じタスクを実行するようにこのコード例を改変する手順を次に示します。

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>軽量タスクを使用するように例を改変するには

1. ヘッダー ファイル concrt.h の `#include` ディレクティブを追加します。

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. **`using`** 名前空間のディレクティブを追加 `concurrency` します。

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. `MyThreadFunction`呼び出し規約を使用してを返すように、の宣言を変更し **`__cdecl`** **`void`** ます。

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. タスクが `MyData` 完了したことをメインアプリケーションに通知する [concurrency:: event](../../parallel/concrt/reference/event-class.md) オブジェクトを含めるように構造体を変更します。

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. の呼び出しを `CreateThread` [concurrency:: currentscheduler:: scheduletask](reference/currentscheduler-class.md#scheduletask) メソッドの呼び出しに置き換えます。

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. の呼び出しを `WaitForSingleObject` [concurrency:: event:: wait](reference/event-class.md#wait) メソッドの呼び出しに置き換えて、タスクが終了するのを待ちます。

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. `CloseHandle` 呼び出しを削除します。

1. 手順 3. に合わせて、`MyThreadFunction` の定義のシグネチャを変更します。

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

1. 関数の最後で、 `MyThreadFunction` [concurrency:: event:: set](reference/event-class.md#set) メソッドを呼び出して、タスクが終了したことをメインアプリケーションに通知します。

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

1. **`return`** からステートメントを削除 `MyThreadFunction` します。

### <a name="completed-code"></a>完成したコード

次の完成版の例に、軽量タスクを使用して `MyThreadFunction` 関数を呼び出すためのコードを示します。

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

## <a name="see-also"></a>関連項目

[タスク スケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler クラス](../../parallel/concrt/reference/scheduler-class.md)
