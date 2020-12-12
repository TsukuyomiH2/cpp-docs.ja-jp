---
description: 詳細については、「ウィザードを使用せずにコンシューマーを作成する」を参照してください。
title: ウィザードを使用しないコンシューマーの作成
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 4c642e0b346bd9825d590f54c3de3f6536722d01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323262"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>ウィザードを使用しないコンシューマーの作成

次の例は、既存の ATL プロジェクトに OLE DB コンシューマーのサポートを追加していることを前提としています。 MFC アプリケーションに OLE DB コンシューマーのサポートを追加する場合は、**MFC アプリケーション ウィザード** を実行する必要があります。このウィザードが必要なすべてのサポートを作成し、アプリケーションを実行するために必要な MFC ルーチンを呼び出します。

**ATL OLE DB コンシューマー ウィザード** を使用せずに OLE DB コンシューマーのサポートを追加するには:

- *.Pch* ファイルで、次のステートメントを追加します `#include` 。

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

プログラムでは、コンシューマーは通常、次の一連の操作を実行します。

1. ローカル変数に列をバインドするユーザー レコード クラスを作成します。 この例では、`CMyTableNameAccessor` がユーザー レコード クラスです (「[ユーザー レコード](../../data/oledb/user-records.md)」を参照)。 このクラスには、列マップとパラメーター マップが含まれています。 列マップで指定するフィールドごとにユーザー レコード クラスのデータ メンバーを宣言します。また、これらのデータ メンバーのそれぞれについて、ステータスのデータ メンバーと長さのデータ メンバーを宣言します。 詳細については、「[ウィザードで生成されたアクセサーのフィールド ステータスのデータ メンバー](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)」を参照してください。

    > [!NOTE]
    > 独自のコンシューマーを作成する場合、データ変数は、ステータス変数と長さ変数よりも前に記述する必要があります。

- データ ソースとセッションをインスタンス化します。 使用するアクセサーと行セットの型を決めたら、[CCommand](../../data/oledb/ccommand-class.md) または [CTable](../../data/oledb/ctable-class.md) を使用して行セットをインスタンス化します。

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- `CoInitialize` を呼び出して COM を初期化します。 これは、メインのコードで呼び出されます。 次に例を示します。

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- [CDataSource::Open](./cdatasource-class.md#open) またはそのバリエーションの 1 つを呼び出します。

- データ ソースへの接続を開き、セッションを開き、行セットを開いて初期化します (さらに、コマンドの場合はそれを実行します)。

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- 必要に応じて、`CDBPropSet::AddProperty` を使用して行セットのプロパティを設定し、それらをパラメーターとして `rs.Open` に渡します。 これを行う方法の例については、「[コンシューマー ウィザードで生成されたメソッド](../../data/oledb/consumer-wizard-generated-methods.md)」の `GetRowsetProperties` を参照してください。

- これで、行セットを使用してデータを取得/操作できるようになりました。

- アプリケーションが完了したら、接続、セッション、および行セットを閉じます。

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   コマンドを使用している場合は、`Close` の後に `ReleaseCommand` を呼び出すことができます。 [CCommand::Close](./ccommand-class.md#close) のコード例で、`Close` と `ReleaseCommand` を呼び出す方法を示しています。

- `CoUnInitialize` を呼び出して COM を初期化前の状態に戻します。 これは、メインのコードで呼び出されます。

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>関連項目

[OLE DB コンシューマーの作成](../../data/oledb/creating-an-ole-db-consumer.md)
