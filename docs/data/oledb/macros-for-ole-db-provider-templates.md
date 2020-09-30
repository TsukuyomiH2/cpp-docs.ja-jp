---
title: OLE DB プロバイダー テンプレート用マクロ
ms.date: 02/11/2019
f1_keywords:
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
ms.openlocfilehash: e72204102bfa47a9dd162499030a38c07bbfe46c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504017"
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB プロバイダー テンプレート用マクロ

OLE DB テンプレートプロバイダーマクロは、次のカテゴリの機能を提供します。

## <a name="property-set-map-macros"></a>プロパティセットマップマクロ

| 名前 | 説明 |
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|プロパティセットの先頭をマークします。|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|プロパティセットの先頭をマークします。|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|プロバイダーのスコープ外で非表示にしたり定義したりできるプロパティセットの先頭をマークします。|
|[CHAIN_PROPERTY_SET](#chain_property_set)|プロパティグループを連結します。|
|[END_PROPERTY_SET](#end_property_set)|プロパティセットの終了をマークします。|
|[END_PROPSET_MAP](#end_propset_map)|プロパティセットマップの終了をマークします。|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|プロパティセットの特定のプロパティを既定値に設定します。|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|プロパティセットの特定のプロパティを、ユーザーが指定した値に設定します。 では、フラグとオプションを設定することもできます。|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|プロパティセットの特定のプロパティを、ユーザーが指定した値に設定します。|

## <a name="column-map-macros"></a>列マップマクロ

| 名前 | 説明 |
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|プロバイダー列マップエントリの先頭をマークします。|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|プロバイダーの列マップエントリの末尾をマークします。|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|プロバイダーによってサポートされる特定の列を表します。|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|プロバイダーによってサポートされる特定の列を表します。 列のデータ型を指定できます。|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|プロバイダーによってサポートされる特定の列を表します。 列のサイズ、データ型、有効桁数、小数点以下桁数、およびスキーマ行セット GUID を指定できます。|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|プロバイダーによってサポートされる特定の列を表します。 列のサイズを指定できます。|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|プロバイダーによってサポートされる特定の列を表します。 列の型が文字列であることを前提としています。|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|プロバイダーによってサポートされる特定の列を表します。 PROVIDER_COLUMN_ENTRY_LENGTH と同様に、列のデータ型やサイズを指定することもできます。|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|プロバイダーによってサポートされる特定の列を表します。 列の型が Unicode 文字列であることを前提としています。|

## <a name="schema-rowset-macros"></a>スキーマ行セットマクロ

| 名前 | 説明 |
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|スキーママップの開始をマークします。|
|[END_SCHEMA_MAP](#end_schema_map)|スキーママップの終了をマークします。|
|[SCHEMA_ENTRY](#schema_entry)|GUID をクラスに関連付けます。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

### <a name="begin_property_set"></a><a name="begin_property_set"></a> BEGIN_PROPERTY_SET

プロパティセットマップ内のプロパティセットの先頭をマークします。

#### <a name="syntax"></a>構文

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
からプロパティの GUID。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](#begin_propset_map)」を参照してください。

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX

プロパティセットマップ内のプロパティセットの先頭をマークします。

#### <a name="syntax"></a>構文

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
からプロパティの GUID。

*flags*<br/>
から公開しないプロパティセット、またはプロバイダーのスコープ外で定義されたプロパティを公開するプロバイダーの UPROPSET_PASSTHROUGH を UPROPSET_HIDDEN します。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](#begin_propset_map)」を参照してください。

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a> BEGIN_PROPSET_MAP

プロパティセットのマップエントリの開始をマークします。

#### <a name="syntax"></a>構文

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>パラメーター

*クラス*<br/>
からこのプロパティが設定されているクラス。 プロパティセットは、次の OLE DB オブジェクトで指定できます。

- [データソースオブジェクト](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [セッションオブジェクト](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [コマンド](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>例

プロパティセットマップのサンプルを次に示します。

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a> CHAIN_PROPERTY_SET

このマクロは、プロパティグループを連結します。

#### <a name="syntax"></a>構文

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>パラメーター

*ChainClass*<br/>
からプロパティを連結するクラスの名前。 これは、既にマップ (セッション、コマンド、データソースオブジェクトクラスなど) が含まれている ATL プロジェクトウィザードによって生成されるクラスです。

#### <a name="remarks"></a>注釈

別のクラスのプロパティセットを独自のクラスにチェーンし、クラスから直接プロパティにアクセスすることができます。

> [!CAUTION]
> このマクロは控えめに使用してください。 不適切な使用により、コンシューマーが OLE DB 準拠テストに失敗する可能性があります。

### <a name="end_property_set"></a><a name="end_property_set"></a> END_PROPERTY_SET

プロパティセットの終了をマークします。

#### <a name="syntax"></a>構文

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
からプロパティの GUID。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](#begin_propset_map)」を参照してください。

### <a name="end_propset_map"></a><a name="end_propset_map"></a> END_PROPSET_MAP

プロパティセットのマップエントリの終了をマークします。

#### <a name="syntax"></a>構文

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](#begin_propset_map)」を参照してください。

### <a name="property_info_entry"></a><a name="property_info_entry"></a> PROPERTY_INFO_ENTRY

プロパティ セットの特定のプロパティを表します。

#### <a name="syntax"></a>構文

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>パラメーター

*dwPropID*<br/>
[入力] プロパティ セット GUID と組み合わせて使用してプロパティを特定する [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 値。

#### <a name="remarks"></a>注釈

このマクロは、 `DWORD` 型のプロパティ値を、ATLDB.H で定義された既定値に設定します。 選択した値にプロパティを設定するには、 [PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)を使用します。 `VARTYPE`プロパティのおよび[Dbpropflags](/previous-versions/windows/desktop/ms724342(v=vs.85))を同時に設定するには、 [PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)を使用します。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](#begin_propset_map)」を参照してください。

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX

プロパティ セットの特定のプロパティを表します。

#### <a name="syntax"></a>構文

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>パラメーター

*dwPropID*<br/>
[入力] プロパティ セット GUID と組み合わせて使用してプロパティを特定する [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 値。

*vt*<br/>
[入力] このプロパティ エントリの `VARTYPE`。 (Wtypes. h で定義)

*dwFlags*<br/>
[入力] このプロパティ エントリを記述している [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) 値。

*value*<br/>
[入力] `DWORD`型のプロパティ値。

*options*<br/>
DBPROPOPTIONS_REQUIRED または DBPROPOPTIONS_SETIFCHEAP。 通常、プロバイダーはコンシューマーによって設定されているため、 *オプション* を設定する必要はありません。

#### <a name="remarks"></a>注釈

このマクロでは、オプションとフラグだけでなく、 `DWORD` 型のプロパティの値を直接指定できます。 単にプロパティを ATLDB.H に定義されている既定値に設定するには、 [PROPERTY_INFO_ENTRY](#property_info_entry)を使用します。 オプションやフラグを設定せずに任意の値にプロパティを設定するには、 [PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)を使用します。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](#begin_propset_map)」を参照してください。

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE

プロパティ セットの特定のプロパティを表します。

#### <a name="syntax"></a>構文

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>パラメーター

*dwPropID*<br/>
[入力] プロパティ セット GUID と組み合わせて使用してプロパティを特定する [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 値。

*value*<br/>
[入力] `DWORD`型のプロパティ値。

#### <a name="remarks"></a>注釈

このマクロでは、型のプロパティ値を直接指定でき `DWORD` ます。 ATLDB.H で定義されている既定値にプロパティを設定します。H では、 [PROPERTY_INFO_ENTRY](#property_info_entry)を使用します。 プロパティの値、フラグ、およびオプションを設定するには、 [PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)を使用します。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](#begin_propset_map)」を参照してください。

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP

プロバイダー列マップエントリの先頭をマークします。

#### <a name="syntax"></a>構文

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>パラメーター

*クラス*<br/>
からこのマップが属するクラスの名前。

#### <a name="example"></a>例

プロバイダー列マップの例を次に示します。

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP

プロバイダーの列マップエントリの末尾をマークします。

#### <a name="syntax"></a>構文

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>例

「 [BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)」を参照してください。

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY

プロバイダーによってサポートされる特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
から列名。

*数値*<br/>
から列番号。 列がブックマーク列でない場合は、列番号を0にすることはできません。

*レプリカ*<br/>
から列に対応するのメンバー変数 `dataClass` 。

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED

プロバイダーによってサポートされる特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
から列名。

*数値*<br/>
から列番号。 列がブックマーク列でない場合は、列番号を0にすることはできません。

*dbtype*<br/>
から [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))のデータ型。

*レプリカ*<br/>
からデータを格納するのメンバー変数 `dataClass` 。

#### <a name="remarks"></a>注釈

列のデータ型を指定できます。

#### <a name="example"></a>例

「 [BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)」を参照してください。

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN

プロバイダーによってサポートされる特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
から列名。

*数値*<br/>
から列番号。 列がブックマーク列でない場合は、列番号を0にすることはできません。

*flags*<br/>
からデータの取得方法を指定します。 `dwFlags` [DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))の説明を参照してください。

*colSize*<br/>
から列のサイズ。

*dbtype*<br/>
から値のデータ型を示します。 `wType` [DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))の説明を参照してください。

*有効桁数 (precision)*<br/>
から *DbType* が DBTYPE_NUMERIC または DBTYPE_DECIMAL 場合に、データを取得するときに使用する有効桁数を示します。 `bPrecision` [DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))の説明を参照してください。

*scale*<br/>
からDbType が DBTYPE_NUMERIC または DBTYPE_DECIMAL 場合に、データを取得するときに使用する小数点以下桁数を示します。 `bScale` [DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))の説明を参照してください。

*guid*<br/>
スキーマ行セットの GUID。 スキーマ行セットとその Guid の一覧については、 *OLE DB プログラマーリファレンス*の「 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 」を参照してください。

#### <a name="remarks"></a>注釈

列のサイズ、データ型、有効桁数、小数点以下桁数、およびスキーマ行セット GUID を指定できます。

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH

プロバイダーによってサポートされる特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
から列名。

*数値*<br/>
から列番号。 列がブックマーク列でない場合は、列番号を0にすることはできません。

*size*<br/>
から列のサイズ (バイト単位)。

*レプリカ*<br/>
から `dataClass` 列データを格納するのメンバー変数。

#### <a name="remarks"></a>注釈

列のサイズを指定できます。

#### <a name="example"></a>例

「 [BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)」を参照してください。

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR

プロバイダーによってサポートされる特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
から列名。

*数値*<br/>
から列番号。 列がブックマーク列でない場合は、列番号を0にすることはできません。

*レプリカ*<br/>
からデータを格納するデータクラスのメンバー変数。

#### <a name="remarks"></a>注釈

列データを [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85))と想定する場合は、このマクロを使用します。

#### <a name="example"></a>例

「 [BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)」を参照してください。

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

プロバイダーによってサポートされる特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
から列名。

*数値*<br/>
から列番号。 列がブックマーク列でない場合は、列番号を0にすることはできません。

*dbtype*<br/>
から [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))のデータ型。

*size*<br/>
から列のサイズ (バイト単位)。

*レプリカ*<br/>
からデータを格納するデータクラスのメンバー変数。

#### <a name="remarks"></a>注釈

[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)に似ていますが、列のデータ型やサイズを指定することもできます。

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR

プロバイダーによってサポートされる特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
から列名。

*数値*<br/>
から列番号。 列がブックマーク列でない場合は、列番号を0にすることはできません。

*レプリカ*<br/>
からデータを格納するデータクラスのメンバー変数。

#### <a name="remarks"></a>注釈

このマクロは、列のデータが null で終了した Unicode 文字列 ( [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85))) の場合に使用します。

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP

スキーママップの先頭を示します。

#### <a name="syntax"></a>構文

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>パラメーター

*SchemaClass*<br/>
MAP を含むクラスです。 通常、これは session クラスになります。

#### <a name="remarks"></a>注釈

スキーマ行セットの詳細については、Windows SDK の「 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 」を参照してください。

### <a name="end_schema_map"></a><a name="end_schema_map"></a> END_SCHEMA_MAP

スキーママップの末尾を示します。

#### <a name="syntax"></a>構文

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>解説

詳細については、「 [IDBSchemaRowsetImpl クラス](../../data/oledb/idbschemarowsetimpl-class.md)」を参照してください。

### <a name="schema_entry"></a><a name="schema_entry"></a> SCHEMA_ENTRY

GUID をクラスに関連付けます。

#### <a name="syntax"></a>構文

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
スキーマ行セットの GUID。 スキーマ行セットとその Guid の一覧については、 *OLE DB プログラマーリファレンス*の「 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 」を参照してください。

*rowsetClass*<br/>
スキーマ行セットを表すために作成されるクラス。

#### <a name="remarks"></a>注釈

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) は、guid のリストについてマップを照会できます。また、guid が指定されている場合は、行セットを作成することもできます。 スキーマ行セットの `IDBSchemaRowsetImpl` 作成は、標準 `CRowsetImpl` の派生クラスに似ていますが、 `Execute` 次のシグネチャを持つメソッドを提供する必要があります。

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

この `Execute` 関数は、行セットのデータを設定します。 ATL プロジェクト [ウィザードでは](/previous-versions/windows/desktop/ms713686(v=vs.85)) 、 *OLE DB プログラマーのリファレンス*「」で説明されているように、3つの必須 OLE DB スキーマそれぞれについて、プロジェクトの3つの初期スキーマ行セットを作成します。

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

また、スキーママップには、対応するエントリが3つ追加されます。 ウィザードを使用してプロバイダーを作成する方法の詳細については、「 [OLE DB テンプレートプロバイダーの作成](../../data/oledb/creating-an-ole-db-provider.md) 」を参照してください。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレートに関するページ](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダーテンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[OLE DB プロバイダーの作成](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB プロバイダーテンプレートのリファレンス](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB プロバイダーテンプレートのマクロ](../../data/oledb/macros-for-ole-db-provider-templates.md)
