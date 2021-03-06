---
title: '**`CStringT`** 講義'
description: Microsoft ATL クラスの API リファレンス **`CStringT`**
ms.date: 12/06/2020
f1_keywords:
- CStringT
- CSTRINGT/ATL::CStringT
- CSTRINGT/ATL::CStringT::CStringT
- CSTRINGT/ATL::CStringT::AllocSysString
- CSTRINGT/ATL::CStringT::AnsiToOem
- CSTRINGT/ATL::CStringT::AppendFormat
- CSTRINGT/ATL::CStringT::Collate
- CSTRINGT/ATL::CStringT::CollateNoCase
- CSTRINGT/ATL::CStringT::Compare
- CSTRINGT/ATL::CStringT::CompareNoCase
- CSTRINGT/ATL::CStringT::Delete
- CSTRINGT/ATL::CStringT::Find
- CSTRINGT/ATL::CStringT::FindOneOf
- CSTRINGT/ATL::CStringT::Format
- CSTRINGT/ATL::CStringT::FormatMessage
- CSTRINGT/ATL::CStringT::FormatMessageV
- CSTRINGT/ATL::CStringT::FormatV
- CSTRINGT/ATL::CStringT::GetEnvironmentVariable
- CSTRINGT/ATL::CStringT::Insert
- CSTRINGT/ATL::CStringT::Left
- CSTRINGT/ATL::CStringT::LoadString
- CSTRINGT/ATL::CStringT::MakeLower
- CSTRINGT/ATL::CStringT::MakeReverse
- CSTRINGT/ATL::CStringT::MakeUpper
- CSTRINGT/ATL::CStringT::Mid
- CSTRINGT/ATL::CStringT::OemToAnsi
- CSTRINGT/ATL::CStringT::Remove
- CSTRINGT/ATL::CStringT::Replace
- CSTRINGT/ATL::CStringT::ReverseFind
- CSTRINGT/ATL::CStringT::Right
- CSTRINGT/ATL::CStringT::SetSysString
- CSTRINGT/ATL::CStringT::SpanExcluding
- CSTRINGT/ATL::CStringT::SpanIncluding
- CSTRINGT/ATL::CStringT::Tokenize
- CSTRINGT/ATL::CStringT::Trim
- CSTRINGT/ATL::CStringT::TrimLeft
- CSTRINGT/ATL::CStringT::TrimRight
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.openlocfilehash: f9ec5c02aa1ed9377a38d30d9a4152af5e164d58
ms.sourcegitcommit: 7b131db4ed39bddb4a456ebea402f47c5cbd69d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2020
ms.locfileid: "96776545"
---
# <a name="cstringt-class"></a>`CStringT` クラス

このクラスは、 **`CStringT`** オブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>パラメーター

*`BaseType`*\
文字列クラスの文字型。 以下のいずれかを指定できます。

- **`char`** (ANSI 文字列の場合)。

- **`wchar_t`** (Unicode 文字列の場合)。

- **`TCHAR`** (ANSI 文字列と Unicode 文字列の両方)。

*`StringTraits`*\
文字列クラスが C Run-Time (CRT) ライブラリをサポートする必要があるかどうか、および文字列リソースが配置されているかどうかを判断します。 以下のいずれかを指定できます。

- **`StrTraitATL<wchar_t | char | TCHAR, ChTraitsCRT<wchar_t | char | TCHAR>>`**

   クラスは、CRT のサポートを必要とし、 `m_hInstResource` (アプリケーションのモジュールクラスのメンバー) によって指定されたモジュール内のリソース文字列を検索します。

- **`StrTraitATL<wchar_t | char | TCHAR, ChTraitsOS<wchar_t | char |TCHAR>>`**

   クラスは、CRT のサポートを必要とせず、 `m_hInstResource` (アプリケーションのモジュールクラスのメンバー) によって指定されたモジュール内のリソース文字列を検索します。

- **`StrTraitMFC<wchar_t | char | TCHAR, ChTraitsCRT<wchar_t | char | TCHAR>>`**

   クラスは、CRT のサポートを必要とし、標準の MFC 検索アルゴリズムを使用してリソース文字列を検索します。

- **`StrTraitMFC<wchar_t | char | TCHAR, ChTraitsOS<wchar_t | char | TCHAR>>`**

   クラスは、標準の MFC 検索アルゴリズムを使用して、CRT のサポートを必要とせず、リソース文字列を検索します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[`CStringT::CStringT`](#cstringt)|**`CStringT`** さまざまな方法でオブジェクトを構築します。|
|[`CStringT::~CStringT`](#_dtorcstringt)|オブジェクトを破棄 **`CStringT`** します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[`CStringT::AllocSysString`](#allocsysstring)|`BSTR`データからを割り当て **`CStringT`** ます。|
|[`CStringT::AnsiToOem`](#ansitooem)|ANSI 文字セットから OEM 文字セットへのインプレース変換を行います。|
|[`CStringT::AppendFormat`](#appendformat)|既存のオブジェクトに書式付きデータを追加 **`CStringT`** します。|
|[`CStringT::Collate`](#collate)|2つの文字列を比較します (大文字と小文字を区別し、ロケール固有の情報を使用します)。|
|[`CStringT::CollateNoCase`](#collatenocase)|2つの文字列を比較します (大文字と小文字は区別しません。はロケール固有の情報を使用します)。|
|[`CStringT::Compare`](#compare)|2つの文字列を比較します (大文字と小文字は区別されます)。|
|[`CStringT::CompareNoCase`](#comparenocase)|2つの文字列を比較します (大文字と小文字は区別しません)。|
|[`CStringT::Delete`](#delete)|1つ以上の文字を文字列から削除します。|
|[`CStringT::Find`](#find)|大きな文字列内の文字または部分文字列を検索します。|
|[`CStringT::FindOneOf`](#findoneof)|セットから最初に一致する文字を検索します。|
|[`CStringT::Format`](#format)|文字列をそのように書式設定し `sprintf` ます。|
|[`CStringT::FormatMessage`](#formatmessage)|メッセージ文字列の書式を設定します。|
|[`CStringT::FormatMessageV`](#formatmessagev)|可変個引数リストを使用してメッセージ文字列を書式設定します。|
|[`CStringT::FormatV`](#formatv)|引数の変数リストを使用して文字列を書式設定します。|
|[`CStringT::GetEnvironmentVariable`](#getenvironmentvariable)|指定された環境変数の値に文字列を設定します。|
|[`CStringT::Insert`](#insert)|文字列内の指定したインデックス位置に1つの文字または部分文字列を挿入します。|
|[`CStringT::Left`](#left)|文字列の左側の部分を抽出します。|
|[`CStringT::LoadString`](#loadstring)|**`CStringT`** Windows リソースから既存のオブジェクトを読み込みます。|
|[`CStringT::MakeLower`](#makelower)|この文字列のすべての文字を小文字に変換します。|
|[`CStringT::MakeReverse`](#makereverse)|文字列を反転させます。|
|[`CStringT::MakeUpper`](#makeupper)|この文字列のすべての文字を大文字に変換します。|
|[`CStringT::Mid`](#mid)|文字列の中間部分を抽出します。|
|[`CStringT::OemToAnsi`](#oemtoansi)|OEM 文字セットから ANSI 文字セットへのインプレース変換を行います。|
|[`CStringT::Remove`](#remove)|文字列から指定された文字を削除します。|
|[`CStringT::Replace`](#replace)|指定された文字を他の文字に置き換えます。|
|[`CStringT::ReverseFind`](#reversefind)|大きい文字列内の文字を検索します。最後から開始します。|
|[`CStringT::Right`](#right)|文字列の右側の部分を抽出します。|
|[`CStringT::SetSysString`](#setsysstring)|`BSTR`オブジェクトのデータを使用して、既存のオブジェクトを設定 **`CStringT`** します。|
|[`CStringT::SpanExcluding`](#spanexcluding)|文字列から、で識別される文字のセットに含まれていない文字を抽出し `pszCharSet` ます。|
|[`CStringT::SpanIncluding`](#spanincluding)|セット内の文字のみを含む部分文字列を抽出します。|
|[`CStringT::Tokenize`](#tokenize)|対象の文字列内の指定されたトークンを抽出します。|
|[`CStringT::Trim`](#trim)|文字列から先頭と末尾の空白文字をすべてトリミングします。|
|[`CStringT::TrimLeft`](#trimleft)|文字列から先頭の空白文字をトリミングします。|
|[`CStringT::TrimRight`](#trimright)|文字列から末尾の空白文字をトリミングします。|

### <a name="operators"></a>演算子

|名前|説明|
|-|-|
|[`CStringT::operator =`](#operator_eq)|オブジェクトに新しい値を割り当て **`CStringT`** ます。|
|[`CStringT::operator +`](#operator_add)|2つの文字列、または1つの文字と文字列を連結します。|
|[`CStringT::operator +=`](#operator_add_eq)|新しい文字列を既存の文字列の末尾に連結します。|
|[`CStringT::operator ==`](#operator_eq_eq)|2つの文字列が論理的に等しいかどうかを判断します。|
|[`CStringT::operator !=`](#operator_neq)|2つの文字列が論理的に等価でないかどうかを判断します。|
|[`CStringT::operator <`](#operator_lt)|演算子の左辺の文字列が右辺の文字列より小さいかどうかを判断します。|
|[`CStringT::operator >`](#operator_gt)|演算子の左辺の文字列が右側の文字列より大きいかどうかを判断します。|
|[`CStringT::operator <=`](#operator_lt_eq)|演算子の左辺の文字列が右側の文字列以下であるかどうかを判断します。|
|[`CStringT::operator >=`](#operator_gt_eq)|演算子の左辺の文字列が、右側の文字列以上かどうかを判断します。|

## <a name="remarks"></a>注釈

**`CStringT`**[CSimpleStringT クラス](../../atl-mfc-shared/reference/csimplestringt-class.md)から継承します。 文字操作、順序付け、検索などの高度な機能は、によって実装され **`CStringT`** ます。

> [!NOTE]
> **`CStringT`** オブジェクトは例外をスローできます。 これは、 **`CStringT`** 何らかの理由でオブジェクトのメモリが不足した場合に発生します。

オブジェクトは、 **`CStringT`** 可変長の文字シーケンスで構成されます。 **`CStringT`** Basic と同様の構文を使用して、関数と演算子を提供します。 連結演算子と比較演算子を使用すると、メモリ管理が簡素化さ **`CStringT`** れ、通常の文字配列よりもオブジェクトを簡単に使用できるようになります。

> [!NOTE]
> 埋め込まれた null 文字を含むインスタンスを作成することもでき **`CStringT`** ますが、それに対しては使用しないことをお勧めします。 Null 文字が埋め込まれているオブジェクトに対してメソッドと演算子を呼び出すと、 **`CStringT`** 意図しない結果が生じる可能性があります。

パラメーターとパラメーターのさまざまな組み合わせを使用することにより `BaseType` `StringTraits` 、 **`CStringT`** オブジェクトは、ATL ライブラリによって事前定義されている次の型になります。

ATL アプリケーションでを使用する場合:

`CString`、 `CStringA` 、および `CStringW` は、ユーザー dll からではなく、MFC dll (MFC90.DLL) からエクスポートされます。 これは、が **`CStringT`** 複数回定義されるのを防ぐために行われます。

> [!NOTE]
> 「 [CStringT を使用した文字列クラスのエクスポート](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md)」で説明されているリンカーエラーの回避策がコードに含まれている場合は、そのコードを削除する必要があります。 これは不要になりました。

MFC ベースのアプリケーションでは、次の文字列型を使用できます。

|CStringT の種類|宣言|
|-------------------|-----------------|
|`CStringA`|CRT をサポートする ANSI 文字型の文字列。|
|`CStringW`|CRT をサポートする Unicode 文字型の文字列。|
|`CString`|CRT をサポートする ANSI と Unicode の両方の文字型。|

次の文字列型は、が定義されているプロジェクトで使用でき `ATL_CSTRING_NO_CRT` ます。

|CStringT の種類|宣言|
|-------------------|-----------------|
|`CAtlStringA`|CRT をサポートしていない ANSI 文字型の文字列。|
|`CAtlStringW`|CRT をサポートしない Unicode 文字型の文字列。|
|`CAtlString`|ANSI と Unicode の両方の文字型は、CRT をサポートしていません。|

次の文字列型は、が `ATL_CSTRING_NO_CRT` 定義されていないプロジェクトで使用できます。

|CStringT の種類|宣言|
|-------------------|-----------------|
|`CAtlStringA`|CRT をサポートする ANSI 文字型の文字列。|
|`CAtlStringW`|CRT をサポートする Unicode 文字型の文字列。|
|`CAtlString`|CRT をサポートする ANSI と Unicode の両方の文字型。|

`CString` オブジェクトには、次の特性もあります。

- **`CStringT`** オブジェクトは、連結操作によって拡張できます。

- **`CStringT`** オブジェクトは "値のセマンティクス" に従います。 オブジェクトは、 **`CStringT`** 文字列へのポインターとしてではなく、実際の文字列と考えることができます。

- 関数の引数には、オブジェクトを自由に置き換えることができ **`CStringT`** `PCXSTR` ます。

- 文字列バッファーのカスタムメモリ管理。 詳細については、「 [メモリ管理と CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)」を参照してください。

## <a name="cstringt-predefined-types"></a>CStringT の定義済みの型

で **`CStringT`** は、テンプレート引数を使用してサポートされる文字型 ( [wchar_t](../../c-runtime-library/standard-types.md) または [char](../../c-runtime-library/standard-types.md)) が定義されているため、メソッドパラメーターの型が複雑になることがあります。 この問題を簡単にするために、定義済みの型のセットがクラス全体で定義および使用され **`CStringT`** ます。 次の表に、さまざまな種類の一覧を示します。

|名前|説明|
|----------|-----------------|
|`XCHAR`|**`wchar_t`** **`char`** オブジェクトと同じ文字型の単一の文字 (または) **`CStringT`** 。|
|`YCHAR`|オブジェクトとは逆の文字型を持つ単一の文字 ( **`wchar_t`** または **`char`** ) **`CStringT`** 。|
|`PXSTR`|* * * * * * **`wchar_t`** **`char`** オブジェクトと同じ文字型を持つ文字列 (または) へのポインター `CStringT` 。|
|`PYSTR`|**`wchar_t`** **`char`** オブジェクトとは逆の文字型を持つ文字列 (または) へのポインター **`CStringT`** 。|
|`PCXSTR`|**`const`** **`wchar_t`** **`char`** オブジェクトと同じ文字型を持つ文字列 (または) へのポインター **`CStringT`** 。|
|`PCYSTR`|**`const`** **`wchar_t`** **`char`** オブジェクトとは逆の文字型を持つ文字列 (または) へのポインター **`CStringT`** 。|

> [!NOTE]
> のドキュメントに記載されていないメソッド (など) を以前に使用していたコードは `CString` `AssignCopy` 、の次の文書化されたメソッド (やなど) を使用するコードに置き換える必要があり **`CStringT`** `GetBuffer` `ReleaseBuffer` ます。 これらのメソッドは、から継承され `CSimpleStringT` ます。

## <a name="inheritance-hierarchy"></a>継承階層

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

**`CStringT`**

## <a name="requirements"></a>必要条件

|ヘッダー|用途|
|------------|-------------|
|cstringt|MFC 専用の文字列オブジェクト|
|atlstr .h|非 MFC 文字列オブジェクト|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a> `CStringT::AllocSysString`

型のオートメーション互換の文字列を割り当て、 `BSTR` オブジェクトの内容を、 **`CStringT`** 終端の null 文字も含めて、その文字列にコピーします。

```cpp
BSTR AllocSysString() const;
```

### <a name="return-value"></a>戻り値

新しく割り当てられた文字列。

### <a name="remarks"></a>注釈

MFC プログラムでは、十分なメモリが存在しない場合、 [CMemoryException クラス](../../mfc/reference/cmemoryexception-class.md) がスローされます。 ATL プログラムでは、 [CAtlException](../../atl/reference/catlexception-class.md) がスローされます。 通常、この関数は、オートメーション用の文字列を返すために使用されます。

通常、この文字列がパラメーターとして COM 関数に渡される場合は、 `[in]` 呼び出し元が文字列を解放する必要があります。 これは、Windows SDK で説明されているように、 [Sysfreestring](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)を使用して行うことができます。 詳細については、「 [BSTR 用のメモリの割り当てと解放](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)」を参照してください。

Windows での OLE 割り当て関数の詳細については、Windows SDK の「 [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) 」を参照してください。

### <a name="example"></a>例

次の例は、`CStringT::AllocSysString` の使い方を示しています。

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a> `CStringT::AnsiToOem`

このオブジェクトのすべての文字を **`CStringT`** ANSI 文字セットから OEM 文字セットに変換します。

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>注釈

関数 `_UNICODE` は、が定義されている場合は使用できません。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a> `CStringT::AppendFormat`

既存のオブジェクトに書式付きデータを追加 **`CStringT`** します。

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>パラメーター

*`pszFormat`*\
書式指定文字列。

*`nFormatID`*\
書式制御文字列を含む文字列リソース識別子。

*`argument`*\
省略可能な引数。

### <a name="remarks"></a>注釈

この関数は、に一連の文字と値を書式設定して追加し **`CStringT`** ます。 各省略可能な引数 (存在する場合) は、の対応する書式指定に従って変換され、によって識別される *`pszFormat`* 文字列リソースから追加され *`nFormatID`* ます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a> `CStringT::Collate`

汎用テキスト関数を使用して2つの文字列を比較し `_tcscoll` ます。

```cpp
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>パラメーター

*`psz`*\
比較に使用されるもう1つの文字列。

### <a name="return-value"></a>戻り値

文字列が同一の場合は 0 **`CStringT`** 。このオブジェクトがより小さい場合は 0 *`psz`* を <、この **`CStringT`** オブジェクトがより大きい場合は0を > *`psz`* します。

### <a name="remarks"></a>注釈

`_tcscoll`TCHAR で定義されている汎用テキスト関数。H は、 `strcoll` `wcscoll` `_mbscoll` コンパイル時に定義された文字セットに応じて、、、またはのいずれかにマップされます。 各関数は、現在使用中のコードページに従って、大文字と小文字を区別して文字列を比較します。 詳細については、「 [strcoll 系、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)」を参照してください。

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a> `CStringT::CollateNoCase`

汎用テキスト関数を使用して2つの文字列を比較し `_tcscoll` ます。

```cpp
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>パラメーター

*`psz`*\
比較に使用されるもう1つの文字列。

### <a name="return-value"></a>戻り値

文字列が同一である場合は 0 (大文字と小文字を区別しない)、このオブジェクトがより小さい場合は 0 (大文字と小文字を区別しない)、 **`CStringT`** *`psz`* またはこの **`CStringT`** オブジェクトがより大きい *`psz`* (大文字と小文字を区別しない) 場合 > は0を < ます。

### <a name="remarks"></a>注釈

`_tcscoll`TCHAR で定義されている汎用テキスト関数。H は、 `stricoll` `wcsicoll` `_mbsicoll` コンパイル時に定義された文字セットに応じて、、、またはのいずれかにマップされます。 各関数は、現在使用中のコードページに従って、文字列の大文字と小文字を区別しない比較を行います。 詳細については、「 [strcoll 系、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a> `CStringT::Compare`

2つの文字列を比較します (大文字と小文字は区別されます)。

```cpp
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>パラメーター

*`psz`*\
比較に使用されるもう1つの文字列。

### <a name="return-value"></a>戻り値

文字列が同一の場合は 0 **`CStringT`** 。このオブジェクトがより小さい場合は 0 *`psz`* を <、この **`CStringT`** オブジェクトがより大きい場合は0を > *`psz`* します。

### <a name="remarks"></a>注釈

`_tcscmp`TCHAR で定義されている汎用テキスト関数。H は、 `strcmp` `wcscmp` `_mbscmp` コンパイル時に定義された文字セットに応じて、、、またはのいずれかにマップされます。 各関数は、文字列の大文字と小文字を区別した比較を行い、ロケールの影響を受けません。 詳細については、「 [strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)」を参照してください。

文字列に埋め込まれた null が含まれている場合、比較のために、文字列は最初の埋め込み null 文字で切り捨てられると見なされます。

### <a name="example"></a>例

次の例は、`CStringT::Compare` の使い方を示しています。

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a> `CStringT::CompareNoCase`

2つの文字列を比較します (大文字と小文字は区別しません)。

```cpp
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>パラメーター

*`psz`*\
比較に使用されるもう1つの文字列。

### <a name="return-value"></a>戻り値

文字列が同一である場合は 0 (大文字と小文字を区別しない)、このオブジェクトがより小さい場合は 0 (大文字と小文字を区別しない)、 **`CStringT`** *`psz`* またはこの **`CStringT`** オブジェクトがより大きい *`psz`* (大文字と小文字を区別しない) 場合 >は0を <ます。

### <a name="remarks"></a>注釈

`_tcsicmp`TCHAR で定義されている汎用テキスト関数。H は `_stricmp` 、 `_wcsicmp` `_mbsicmp` コンパイル時に定義された文字セットに応じて、、またはのいずれかにマップされます。 各関数は、文字列の大文字と小文字を区別しない比較を行います。 比較は、ロケールの LC_CTYPE の側面に依存しますが、LC_COLLATE はありません。 詳細については、「 [_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a> `CStringT::CStringT`

オブジェクトを構築 **`CStringT`** します。

```cpp
CStringT() throw() :
    CThisSimpleString(StringTraits::GetDefaultManager());

explicit CStringT(IAtlStringMgr* pStringMgr) throw() :
    CThisSimpleString( pStringMgr);

CStringT(const VARIANT& varSrc);

CStringT(const VARIANT& varSrc, IAtlStringMgr* pStringMgr);

CStringT(const CStringT& strSrc) :
    CThisSimpleString( strSrc);

operator CSimpleStringT<
                    BaseType,
                    !_CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                    :: c_bIsMFCDLLTraits> &()

template <bool bMFCDLL>
CStringT(const CSimpleStringT<BaseType, bMFCDLL>& strSrc) :
    CThisSimpleString( strSrc);

template <class SystemString>
CStringT(SystemString^ pString) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(const YCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(LPCSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CStringT(LPCWSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(const unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

/*CSTRING_EXPLICIT*/ CStringT(char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const unsigned char* pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(char ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength) :
    CThisSimpleString( pch, nLength, StringTraits::GetDefaultManager());

CStringT(const YCHAR* pch, int nLength) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength, AtlStringMgr* pStringMgr) :
    CThisSimpleString( pch, nLength, pStringMgr);

CStringT(const YCHAR* pch, int nLength, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);
```

### <a name="parameters"></a>パラメーター

*`pch`*\
長さが *n* の文字の配列へのポインターであり、null で終了するものではありません。

*`nLength`*\
*Pch* 内の文字数のカウント。

*`ch`*\
1文字。

*`pszSrc`*\
このオブジェクトにコピーされる null で終わる文字列 **`CStringT`** 。

*`pStringMgr`*\
オブジェクトのメモリマネージャーへのポインター **`CStringT`** 。 とのメモリ管理の詳細について `IAtlStringMgr` **`CStringT`** は、「 [CStringT を使用したメモリ管理](../../atl-mfc-shared/memory-management-with-cstringt.md)」を参照してください。

*`strSrc`*\
**`CStringT`** このオブジェクトにコピーされる既存のオブジェクト **`CStringT`** 。 およびの詳細については、「 `CThisString` `CThisSimpleString` 解説」を参照してください。

*`varSrc`*\
このオブジェクトにコピーされるバリアントオブジェクト **`CStringT`** 。

*`BaseType`*\
文字列クラスの文字型。 以下のいずれかを指定できます。

**`char`** (ANSI 文字列の場合)。

**`wchar_t`** (Unicode 文字列の場合)。

`TCHAR` (ANSI 文字列と Unicode 文字列の両方)。

*`bMFCDLL`*\
プロジェクトが MFC DLL () であるかどうか () を指定するブール値です `TRUE` `FALSE` 。

*`SystemString`*\
はである必要があり、 `System::String` プロジェクトはでコンパイルされる必要があり `/clr` ます。

*`pString`*\
オブジェクトのハンドル **`CStringT`** 。

### <a name="remarks"></a>注釈

コンストラクターは、割り当てられた新しいストレージに入力データをコピーするので、メモリ例外が発生する可能性があります。 これらのコンストラクターの一部は、変換関数として機能します。 これにより、たとえば、 **`LPTSTR`** オブジェクトが必要とされるを置き換えることができ **`CStringT`** ます。

- **`CStringT`**( `LPCSTR` `lpsz` ): **`CStringT`** ANSI 文字列から Unicode を構築します。 また、次の例に示すように、このコンストラクターを使用して文字列リソースを読み込むこともできます。

- `CStringT(``LPCWSTR` `lpsz` ): **`CStringT`** Unicode 文字列からを構築します。

- **`CStringT`**( `const unsigned char*` `psz` ): へのポインターからを構築できます **`CStringT`** **`unsigned char`** 。

> [!NOTE]
> ANSI 文字列 `_CSTRING_DISABLE_NARROW_WIDE_CONVERSION` と Unicode 文字列の間の暗黙的な文字列変換を無効にするマクロを定義します。 マクロは、変換をサポートするコンパイルコンストラクターから除外されます。

*`strSrc`* パラメーターに **`CStringT`** は、オブジェクトまたはオブジェクトを指定でき `CThisSimpleString` ます。 の場合は **`CStringT`** 、既定のインスタンス化 (、、または) のいずれかを使用します。 `CString` `CStringA` の場合は、 `CStringW` `CThisSimpleString` ポインターを使用し **`this`** ます。 `CThisSimpleString`[CSimpleStringT クラス](../../atl-mfc-shared/reference/csimplestringt-class.md)のインスタンスを宣言します。これは、クラスよりも機能が少ない、より小さな文字列クラスです **`CStringT`** 。

オーバーロード演算子は、 `CSimpleStringT<>&()` **`CStringT`** 宣言からオブジェクトを構築し `CSimpleStringT` ます。

> [!NOTE]
> 埋め込まれた null 文字を含むインスタンスを作成することもでき **`CStringT`** ますが、それに対しては使用しないことをお勧めします。 Null 文字が埋め込まれているオブジェクトに対してメソッドと演算子を呼び出すと、 **`CStringT`** 意図しない結果が生じる可能性があります。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a> `CStringT::~CStringT`

オブジェクトを破棄 **`CStringT`** します。

```cpp
~CStringT() throw();
```

### <a name="remarks"></a>注釈

オブジェクトを破棄 **`CStringT`** します。

## <a name="cstringtdelete"></a><a name="delete"></a> `CStringT::Delete`

指定したインデックス位置にある文字で始まる文字列から1つ以上の文字を削除します。

```cpp
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>パラメーター

*`iIndex`*\
削除するオブジェクト内の最初の文字の0から始まるインデックス **`CStringT`** 。

*`nCount`*\
削除する文字数。

### <a name="return-value"></a>戻り値

変更された文字列の長さ。

### <a name="remarks"></a>注釈

*`nCount`* が文字列より長い場合は、文字列の残りの部分が削除されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a> `CStringT::Find`

文字または部分文字列の最初の一致をこの文字列で検索します。

```cpp
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>パラメーター

*`pszSub`*\
検索する部分文字列。

*`iStart`*\
検索を開始する文字列内の文字のインデックス。最初から開始する場合は0。

*`ch`*\
検索対象の単一の文字。

### <a name="return-value"></a>戻り値

要求された部分文字列または文字と一致する、このオブジェクトの最初の文字の0から始まるインデックス番号。 **`CStringT`** 部分文字列または文字が見つからない場合は-1。

### <a name="remarks"></a>注釈

関数は、(実行時の関数と同様に) 1 つの文字 `strchr` と文字列 (に似ています) の両方を受け入れるようにオーバーロードされてい `strstr` ます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a> `CStringT::FindOneOf`

この文字列で、に格納されている任意の文字と一致する最初の文字を検索し *`pszCharSet`* ます。

```cpp
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>パラメーター

*`pszCharSet`*\
一致する文字を含む文字列。

### <a name="return-value"></a>戻り値

この文字列内の最初の文字の0から始まるインデックス。 *`pszCharSet`* 一致するものがない場合は、-1。

### <a name="remarks"></a>注釈

内のいずれかの文字が最初に出現する位置を検索 *`pszCharSet`* します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a> `CStringT::Format`

は、 **`CStringT`** データを C スタイルの文字配列に書式設定 [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) のと同じ方法で、書式付きデータをに書き込みます。

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>パラメーター

*`nFormatID`*\
書式制御文字列を含む文字列リソース識別子。

*`pszFormat`*\
書式指定文字列。

*`argument`*\
省略可能な引数。

### <a name="remarks"></a>注釈

この関数は、一連の文字と値の書式を設定し、に格納し **`CStringT`** ます。 省略可能な各引数 (存在する場合) は、の対応する書式指定に従って変換され、に *`pszFormat`* よって識別される文字列リソースから出力され *`nFormatID`* ます。

文字列オブジェクト自体がへのパラメーターとして提供されている場合、呼び出しは失敗し `Format` ます。 たとえば、次のコードでは、予期しない結果が発生します。

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

詳細については、「[書式指定構文: printf 関数と wprintf 関数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)」をご覧ください。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a> `CStringT::FormatMessage`

メッセージ文字列の書式を設定します。

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>パラメーター

*`nFormatID`*\
書式設定されていないメッセージテキストを含む文字列リソース識別子。

*`pszFormat`*\
は、書式指定文字列を指します。 挿入がスキャンされ、それに応じて書式設定されます。 書式指定文字列は、パラメーターが任意の順序で挿入されることを除いて、ランタイム関数の *printf* 形式の書式指定文字列に似ています。

*`argument`*\
省略可能な引数。

### <a name="remarks"></a>注釈

関数には、入力としてメッセージ定義が必要です。 メッセージ定義は、によって識別される文字列リソースによって決定され *`pszFormat`* *`nFormatID`* ます。 関数は、書式設定されたメッセージテキストをオブジェクトにコピーし **`CStringT`** 、要求された場合は埋め込み挿入シーケンスを処理します。

> [!NOTE]
> `FormatMessage` 新しく書式設定された文字列のシステムメモリの割り当てを試みます。 この試行が失敗した場合は、メモリ例外が自動的にスローされます。

各挿入に *`pszFormat`* は、パラメーターまたはパラメーターの後に対応するパラメーターが必要 *`nFormatID`* です。 メッセージテキスト内では、メッセージを動的に書式設定するために複数のエスケープシーケンスがサポートされています。 詳細については、Windows SDK の「Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) 関数」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a> `CStringT::FormatMessageV`

可変個引数リストを使用してメッセージ文字列を書式設定します。

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>パラメーター

*`pszFormat`*\
は、書式指定文字列を指します。 挿入がスキャンされ、それに応じて書式設定されます。 書式指定文字列は、 `printf` パラメーターが任意の順序で挿入されることを除いて、ランタイムの関数形式の書式指定文字列に似ています。

*`pArgList`*\
引数のリストへのポインター。

### <a name="remarks"></a>注釈

関数は、によって決定される、入力としてのメッセージ定義を必要とし *`pszFormat`* ます。 関数は、書式設定されたメッセージテキストと引数の変数リストをオブジェクトにコピーし **`CStringT`** 、要求された場合は埋め込み挿入シーケンスを処理します。

> [!NOTE]
> `FormatMessageV` 新しく書式設定された文字列にシステムメモリを割り当てようとする、 [CStringT:: FormatMessage](#formatmessage)を呼び出します。 この試行が失敗した場合は、メモリ例外が自動的にスローされます。

詳細については、Windows SDK の「Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) 関数」を参照してください。

## <a name="cstringtformatv"></a><a name="formatv"></a> `CStringT::FormatV`

可変個引数リストを使用してメッセージ文字列を書式設定します。

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>パラメーター

*`pszFormat`*\
は、書式指定文字列を指します。 挿入がスキャンされ、それに応じて書式設定されます。 書式指定文字列は、 `printf` パラメーターが任意の順序で挿入されることを除いて、ランタイムの関数形式の書式指定文字列に似ています。

*`args`*\
引数のリストへのポインター。

### <a name="remarks"></a>注釈

**`CStringT`** `vsprintf_s` C スタイルの文字配列にデータを書式設定するのと同じ方法で、書式設定された文字列と引数の変数リストを文字列に書き込みます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a> `CStringT::GetEnvironmentVariable`

指定された環境変数の値に文字列を設定します。

```cpp
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>パラメーター

*`pszVar`*\
環境変数を指定する null で終わる文字列へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>注釈

呼び出し元プロセスの環境ブロックから、指定された変数の値を取得します。 値は、null で終わる文字列の形式で指定します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a> `CStringT::Insert`

文字列内の指定したインデックス位置に1つの文字または部分文字列を挿入します。

```cpp
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>パラメーター

*`iIndex`*\
挿入が行われる前の文字のインデックス。

*`psz`*\
挿入する部分文字列へのポインター。

*`ch`*\
挿入する文字。

### <a name="return-value"></a>戻り値

変更された文字列の長さ。

### <a name="remarks"></a>注釈

パラメーターは、 *`iIndex`* 文字または部分文字列用の領域を確保するために移動される最初の文字を識別します。 *NIndex* が0の場合は、文字列全体の前に挿入が行われます。 *NIndex* が文字列の長さよりも大きい場合、関数は、現在の文字列と、またはのいずれかによって提供された新しいマテリアルを連結 *`ch`* *`psz`* します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a> `CStringT::Left`

このオブジェクトから左端の文字を抽出し、抽出した *`nCount`* **`CStringT`** 部分文字列のコピーを返します。

```cpp
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>パラメーター

*`nCount`*\
このオブジェクトから抽出する文字数 **`CStringT`** 。

### <a name="return-value"></a>戻り値

**`CStringT`** 指定した文字範囲のコピーを格納しているオブジェクト。 返される **`CStringT`** オブジェクトは空でもかまいません。

### <a name="remarks"></a>注釈

が *`nCount`* 文字列の長さを超えた場合、文字列全体が抽出されます。 `Left` は、Basic `Left` 関数に類似します。

マルチバイト文字セット (MBCS) の場合、では *`nCount`* 各8ビットシーケンスが1つの文字として扱われるので、は *`nCount`* 2 で乗算されたマルチバイト文字の数を返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a> `CStringT::LoadString`

*NID* によって識別される Windows 文字列リソースを既存の **`CStringT`** オブジェクトに読み込みます。

```cpp
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>パラメーター

*`hInstance`*\
モジュールのインスタンスへのハンドル。

*`nID`*\
Windows 文字列リソース ID。

*`wLanguageID`*\
文字列リソースの言語。

### <a name="return-value"></a>戻り値

リソースの読み込みが成功した場合は0以外の場合は。それ以外の場合は0です。

### <a name="remarks"></a>注釈

指定された言語 (*wlanguage*) を使用して、指定されたモジュール (*hInstance*) から文字列リソース (*nID*) を読み込みます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a> `CStringT::MakeLower`

オブジェクトを **`CStringT`** 小文字の文字列に変換します。

```cpp
CStringT& MakeLower();
```

### <a name="return-value"></a>戻り値

結果として得られる小文字の文字列。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a> `CStringT::MakeReverse`

オブジェクト内の文字の順序を反転させ **`CStringT`** ます。

```cpp
CStringT& MakeReverse();
```

### <a name="return-value"></a>戻り値

結果の逆順の文字列。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a> `CStringT::MakeUpper`

オブジェクトを **`CStringT`** 大文字の文字列に変換します。

```cpp
CStringT& MakeUpper();
```

### <a name="return-value"></a>戻り値

結果として得られる大文字の文字列。

### <a name="remarks"></a>解説

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a> `CStringT::Mid`

*`nCount`* **`CStringT`** 位置 (0 から始まる) を開始位置として、このオブジェクトから長さの文字の部分文字列を抽出し *`iFirst`* ます。

```cpp
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>パラメーター

*`iFirst`*\
抽出された **`CStringT`** 部分文字列に含める、このオブジェクト内の最初の文字の0から始まるインデックス。

*`nCount`*\
このオブジェクトから抽出する文字数 **`CStringT`** 。 このパラメーターを指定しない場合は、文字列の残りの部分が抽出されます。

### <a name="return-value"></a>戻り値

**`CStringT`** 指定した文字範囲のコピーを格納しているオブジェクト。 返される **`CStringT`** オブジェクトは空でもかまいません。

### <a name="remarks"></a>注釈

関数は、抽出された部分文字列のコピーを返します。 `Mid` は、基本的な Mid 関数に似ています (ただし、Basic のインデックスは1から始まる)。

マルチバイト文字セット (MBCS) の場合、は *`nCount`* 各8ビット文字を参照します。つまり、1つのマルチバイト文字の先頭バイトと末尾バイトは2文字としてカウントされます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a> `CStringT::OemToAnsi`

このオブジェクトのすべての文字を **`CStringT`** OEM 文字セットから ANSI 文字セットに変換します。

```cppcpp
void OemToAnsi();
```

### <a name="remarks"></a>注釈

この関数 `_UNICODE` は、が定義されている場合は使用できません。

### <a name="example"></a>例

「 [CStringT:: AnsiToOem](#ansitooem)」の例を参照してください。

## <a name="cstringtoperator-"></a><a name="operator_eq"></a> `CStringT::operator =`

文字列に新しい値を割り当てます。

```cpp
CStringT& operator=(const CStringT& strSrc);

template<bool bMFCDLL>
CStringT& operator=(const CSimpleStringT<BaseType, bMFCDLL>& str);
CStringT& operator=(PCXSTR pszSrc);
CStringT& operator=(PCYSTR pszSrc);
CStringT& operator=(const unsigned char* pszSrc);
CStringT& operator=(XCHAR ch);
CStringT& operator=(YCHAR ch);
CStringT& operator=(const VARIANT& var);
```

### <a name="parameters"></a>パラメーター

*`strSrc`*\
**`CStringT`** この文字列に代入する。

*`str`*\
`CThisSimpleString` オブジェクトへの参照です。

*`bMFCDLL`*\
プロジェクトが MFC DLL であるかどうかを指定するブール値です。

*`BaseType`*\
文字列基本型。

*`var`*\
この文字列に代入するバリアントオブジェクト。

*`ch`*\
文字列に割り当てる ANSI 文字または Unicode 文字。

*`pszSrc`*\
割り当てられている元の文字列へのポインター。

### <a name="remarks"></a>注釈

代入演算子は、別の **`CStringT`** オブジェクト、文字ポインター、または1つの文字を受け入れます。 新しいストレージを割り当てることができるため、この演算子を使用するたびにメモリ例外が発生する可能性があります。

の詳細については `CThisSimpleString` 、「 [cstringt:: cstringt](#cstringt)」の「解説」を参照してください。

> [!NOTE]
> 埋め込まれた null 文字を含むインスタンスを作成することもでき **`CStringT`** ますが、それに対しては使用しないことをお勧めします。 Null 文字が埋め込まれているオブジェクトに対してメソッドと演算子を呼び出すと、 **`CStringT`** 意図しない結果が生じる可能性があります。

## <a name="cstringtoperator-"></a><a name="operator_add"></a> `CStringT::operator +`

2つの文字列、または1つの文字と文字列を連結します。

```cpp
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```

### <a name="parameters"></a>パラメーター

*`ch1`*\
文字列と連結する ANSI または Unicode 文字。

*`ch2`*\
文字列と連結する ANSI または Unicode 文字。

*`str1`*\
**`CStringT`** 文字列または文字と連結する。

*`str2`*\
**`CStringT`** 文字列または文字と連結する。

*`psz1`*\
文字列または文字と連結する、null で終わる文字列へのポインター。

*`psz2`*\
文字列または文字と連結する文字列へのポインター。

### <a name="remarks"></a>注釈

関数には、7つのオーバーロード形式があり `CStringT::operator+` ます。 最初のバージョンでは、2つの既存のオブジェクトを連結 **`CStringT`** します。 次の2つは、 **`CStringT`** オブジェクトと null で終わる文字列を連結したものです。 次の2つは、オブジェクトと ANSI 文字を連結したもの **`CStringT`** です。 最後の2つは、オブジェクトと Unicode 文字を連結したもの **`CStringT`** です。

> [!NOTE]
> 埋め込まれた null 文字を含むインスタンスを作成することもでき **`CStringT`** ますが、それに対しては使用しないことをお勧めします。 Null 文字が埋め込まれているオブジェクトに対してメソッドと演算子を呼び出すと、 **`CStringT`** 意図しない結果が生じる可能性があります。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a> `CStringT::operator +=`

文字列の末尾に文字を連結します。

```cpp
CStringT& operator+=(const CThisSimpleString& str);

template<bool bMFCDLL>
CStringT& operator+=(const const CSimpleStringT<BaseType, bMFCDLL>& str);

template<int t_nSize>
CStringT& operator+=(const CStaticString<XCHAR, t_nSize>& strSrc);
CStringT& operator+=(PCXSTR pszSrc);
CStringT& operator+=(PCYSTR pszSrc);
CStringT& operator+=(char ch);
CStringT& operator+=(unsigned char ch);
CStringT& operator+=(wchar_t ch);
CStringT& operator+=(const VARIANT& var);
```

### <a name="parameters"></a>パラメーター

*`str`*\
`CThisSimpleString` オブジェクトへの参照です。

*`bMFCDLL`*\
プロジェクトが MFC DLL であるかどうかを指定するブール値です。

*`BaseType`*\
文字列基本型。

*`var`*\
この文字列に連結するバリアントオブジェクト。

*`ch`*\
文字列と連結する ANSI または Unicode 文字。

*`pszSrc`*\
連結されている元の文字列へのポインター。

*`strSrc`*\
**`CStringT`** この文字列に連結する。

### <a name="remarks"></a>注釈

演算子は、別の **`CStringT`** オブジェクト、文字ポインター、または1つの文字を受け入れます。 この連結演算子を使用すると、このオブジェクトに追加された文字に対して新しいストレージを割り当てることができるため、メモリ例外が発生する可能性があり **`CStringT`** ます。

の詳細については `CThisSimpleString` 、「 [cstringt:: cstringt](#cstringt)」の「解説」を参照してください。

> [!NOTE]
> 埋め込まれた null 文字を含むインスタンスを作成することもでき **`CStringT`** ますが、それに対しては使用しないことをお勧めします。 Null 文字が埋め込まれているオブジェクトに対してメソッドと演算子を呼び出すと、 **`CStringT`** 意図しない結果が生じる可能性があります。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a> `CStringT::operator ==`

2つの文字列が論理的に等しいかどうかを判断します。

```cpp
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>パラメーター

*`ch1`*\
比較のための ANSI 文字または Unicode 文字。

*`ch2`*\
比較のための ANSI 文字または Unicode 文字。

*`str1`*\
**`CStringT`** 比較対象の。

*`str2`*\
**`CStringT`** 比較対象の。

*`psz1`*\
Null で終わる比較対象の文字列へのポインター。

*`psz2`*\
Null で終わる比較対象の文字列へのポインター。

### <a name="remarks"></a>注釈

左側の文字列または文字が右側の文字列または文字と等しいかどうかをテストし、それに `TRUE` 応じて、またはを返し `FALSE` ます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a> `CStringT::operator !=`

2つの文字列が論理的に等しくないかどうかを判断します。

```cpp
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>パラメーター

*`ch1`*\
文字列と連結する ANSI または Unicode 文字。

*`ch2`*\
文字列と連結する ANSI または Unicode 文字。

*`str1`*\
**`CStringT`** 比較対象の。

*`str2`*\
**`CStringT`** 比較対象の。

*`psz1`*\
Null で終わる比較対象の文字列へのポインター。

*`psz2`*\
Null で終わる比較対象の文字列へのポインター。

### <a name="remarks"></a>注釈

左側の文字列または文字が右側の文字列または文字と等しくないかどうかをテストします。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_lt"></a> `CStringT::operator <`

演算子の左辺の文字列が右辺の文字列より小さいかどうかを判断します。

```cpp
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>パラメーター

*`str1`*\
**`CStringT`** 比較対象の。

*`str2`*\
**`CStringT`** 比較対象の。

*`psz1`*\
Null で終わる比較対象の文字列へのポインター。

*`psz2`*\
Null で終わる比較対象の文字列へのポインター。

### <a name="remarks"></a>注釈

文字列間の辞書式比較 (文字単位)。

- 2 つの対応する文字が等しくない場合、比較の結果は文字列間の比較の結果として取得されます。

- 不等が見つからなくても、1 つの文字列に他より多くの文字がある場合、短い文字列は長い文字列より小さいと見なされます。

- 不等が見つからず、各文字列の文字数が同じである場合、文字列が等しくなります。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_gt"></a> `CStringT::operator >`

演算子の左辺の文字列が右側の文字列より大きいかどうかを判断します。

```cpp
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>パラメーター

*`str1`*\
**`CStringT`** 比較対象の。

*`str2`*\
**`CStringT`** 比較対象の。

*`psz1`*\
Null で終わる比較対象の文字列へのポインター。

*`psz2`*\
Null で終わる比較対象の文字列へのポインター。

### <a name="remarks"></a>注釈

文字列間の辞書式比較 (文字単位)。

- 2 つの対応する文字が等しくない場合、比較の結果は文字列間の比較の結果として取得されます。

- 不等が見つからなくても、1 つの文字列に他より多くの文字がある場合、短い文字列は長い文字列より小さいと見なされます。

- 不等が見つからず、各文字列の文字数が同じである場合、文字列が等しくなります。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_lt_eq"></a> `CStringT::operator <=`

演算子の左側の文字列が右側の文字列以下であるかどうかを判断します。

```cpp
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>パラメーター

*`str1`*\
**`CStringT`** 比較対象の。

*`str2`*\
**`CStringT`** 比較対象の。

*`psz1`*\
Null で終わる比較対象の文字列へのポインター。

*`psz2`*\
Null で終わる比較対象の文字列へのポインター。

### <a name="remarks"></a>注釈

文字列間の辞書式比較 (文字単位)。

- 2 つの対応する文字が等しくない場合、比較の結果は文字列間の比較の結果として取得されます。

- 不等が見つからなくても、1 つの文字列に他より多くの文字がある場合、短い文字列は長い文字列より小さいと見なされます。

- 不等が見つからず、各文字列の文字数が同じである場合、文字列が等しくなります。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_gt_eq"></a> `CStringT::operator >=`

演算子の左辺の文字列が、右側の文字列以上かどうかを判断します。

```cpp
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>パラメーター

*`str1`*\
**`CStringT`** 比較対象の。

*`str2`*\
**`CStringT`** 比較対象の。

*`psz1`*\
比較対象の文字列へのポインター。

*`psz2`*\
比較対象の文字列へのポインター。

### <a name="remarks"></a>注釈

文字列間の辞書式比較 (文字単位)。

- 2 つの対応する文字が等しくない場合、比較の結果は文字列間の比較の結果として取得されます。

- 不等が見つからなくても、1 つの文字列に他より多くの文字がある場合、短い文字列は長い文字列より小さいと見なされます。

- 不等が見つからず、各文字列の文字数が同じである場合、文字列が等しくなります。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a> `CStringT::Remove`

指定した文字のすべてのインスタンスを文字列から削除します。

```cpp
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>パラメーター

*`chRemove`*\
文字列から削除する文字。

### <a name="return-value"></a>戻り値

文字列から削除された文字の数。 文字列が変更されない場合は0。

### <a name="remarks"></a>注釈

文字の比較では大文字と小文字が区別されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a> `CStringT::Replace`

には、2つのバージョンがあり `Replace` ます。 最初のバージョンでは、別の部分文字列を使用して部分文字列の1つ以上のコピーを置き換えます。 両方の部分文字列が null で終了します。 2番目のバージョンでは、別の文字を使用して文字の1つ以上のコピーを置き換えます。 どちらのバージョンも、に格納されている文字データに対して動作 **`CStringT`** します。

```cpp
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>パラメーター

*`pszOld`*\
によって置換される、null で終わる文字列へのポインター *`pszNew`* 。

*`pszNew`*\
を置き換える null で終わる文字列へのポインター *`pszOld`* 。

*`chOld`*\
に置き換えられる文字 *`chNew`* 。

*`chNew`*\
を置き換える文字 *`chOld`* 。

### <a name="return-value"></a>戻り値

文字または部分文字列の置換されたインスタンスの数を返します。文字列が変更されていない場合は0を返します。

### <a name="remarks"></a>注釈

`Replace` では文字列の長さを変更でき *`pszNew`* *`pszOld`* ます。同じ長さである必要はなく、古い部分文字列の複数のコピーを新しいものに変更できるためです。 関数では、大文字と小文字が区別されます。

インスタンスの例として、、、など **`CStringT`** が `CString` `CStringA` `CStringW` あります。

の場合 `CStringA` 、は `Replace` ANSI またはマルチバイト (MBCS) の文字を使用します。 の場合 `CStringW` 、は `Replace` ワイド文字を使用します。

では `CString` 、次の表の定数が定義されているかどうかに基づいて、コンパイル時に文字データ型が選択されます。

|定義済み定数|Character データ型|
|----------------------|-------------------------|
|`_UNICODE`|ワイド文字|
|`_MBCS`|複数バイト文字|
|どちらもオフ|1バイト文字|
|両方|未定義。|

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a> `CStringT::ReverseFind`

この **`CStringT`** オブジェクトで、文字の最後の一致を検索します。

```cpp
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>パラメーター

*`ch`*\
検索対象の文字。

### <a name="return-value"></a>戻り値

要求された文字と一致するこのオブジェクトの最後の文字の0から始まるインデックス番号 **`CStringT`** 。文字が見つからない場合は-1。

### <a name="remarks"></a>注釈

関数は、ランタイム関数に似てい `strrchr` ます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a> `CStringT::Right`

このオブジェクトから最後 (つまり右端) の文字を抽出し、抽出された *`nCount`* **`CStringT`** 部分文字列のコピーを返します。

```cpp
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>パラメーター

*`nCount`*\
このオブジェクトから抽出する文字数 **`CStringT`** 。

### <a name="return-value"></a>戻り値

**`CStringT`** 指定した文字範囲のコピーを格納しているオブジェクト。 返される **`CStringT`** オブジェクトは空にすることができます。

### <a name="remarks"></a>注釈

が *`nCount`* 文字列の長さを超えた場合、文字列全体が抽出されます。 `Right` は基本的な関数に似てい `Right` ます (ただし、basic のインデックスは0から始まります)。

マルチバイト文字セット (MBCS) の場合、は *`nCount`* 各8ビット文字を参照します。つまり、1つのマルチバイト文字の先頭バイトと末尾バイトは2文字としてカウントされます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a> `CStringT::SetSysString`

が指すを再割り当て **`BSTR`** *`pbstr`* し、NULL 文字を含むオブジェクトの内容を **`CStringT`** そのオブジェクトにコピーします。

```cpp
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>パラメーター

*`pbstr`*\
文字列へのポインター。

### <a name="return-value"></a>戻り値

新しい文字列。

### <a name="remarks"></a>注釈

オブジェクトの内容によっては、 **`CStringT`** **`BSTR`** によって参照されるの値が変更される *`pbstr`* ことがあります。 メモリが不足している場合、関数はをスローし `CMemoryException` ます。

通常、この関数は、オートメーションで参照によって渡される文字列の値を変更するために使用されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a> `CStringT::SpanExcluding`

文字列から、で識別される文字のセットに含まれていない文字を抽出し *`pszCharSet`* ます。

```cpp
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>パラメーター

*`pszCharSet`*\
文字のセットとして解釈される文字列。

### <a name="return-value"></a>戻り値

内に存在しない文字列の文字を格納する部分文字列。文字列内の最初の文字から始まり、にある文字列内の最初の文字で *`pszCharSet`* 終わり *`pszCharSet`* ます (つまり、文字列の最初の文字から始まり、見つかった文字列の最初の文字を除く最大の文字 *`pszCharSet`* )。 文字列内に文字が見つからない場合は、文字列全体が返され *`pszCharSet`* ます。

### <a name="remarks"></a>注釈

`SpanExcluding` から文字が最初に出現する位置の前にあるすべての文字を抽出して返し *`pszCharSet`* ます (つまり、からの文字 *`pszCharSet`* と、文字列内のその後のすべての文字は返されません)。 *`pszCharSet`* 文字列内に文字が見つからない場合、は `SpanExcluding` 文字列全体を返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a> `CStringT::SpanIncluding`

文字列から、で識別される文字のセットに含まれる文字を抽出し *`pszCharSet`* ます。

```cpp
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>パラメーター

*`pszCharSet`*\
文字のセットとして解釈される文字列。

### <a name="return-value"></a>戻り値

内の文字列内の文字を格納している部分文字列。文字列内の *`pszCharSet`* 最初の文字から始まり、に含まれていない文字列に文字が見つかったときに終了し *`pszCharSet`* ます。 `SpanIncluding` 文字列の最初の文字が指定されたセット内にない場合は、空の部分文字列を返します。

### <a name="remarks"></a>注釈

文字列の最初の文字が文字セットに含まれていない場合、は `SpanIncluding` 空の文字列を返します。 それ以外の場合は、セット内の連続する文字のシーケンスを返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a> `CStringT::Tokenize`

対象の文字列内の次のトークンを検索します。

```cpp
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>パラメーター

*`pszTokens`*\
トークン区切り記号を格納している文字列。 これらの区切り記号の順序は重要ではありません。

*`iStart`*\
検索を開始する位置を示す0から始まるインデックス。

### <a name="return-value"></a>戻り値

**`CStringT`** 現在のトークン値を格納しているオブジェクト。

### <a name="remarks"></a>注釈

関数は、 `Tokenize` ターゲット文字列内の次のトークンを検索します。 *Psztokens* の文字セットは、検索するトークンの有効な区切り記号を指定します。 `Tokenize`関数が呼び出されるたびに、は *`iStart`* 先頭の区切り記号をスキップし、 **`CStringT`** 現在のトークンを含むオブジェクトを返します。これは、次の区切り文字までの文字の文字列です。 の値は、 *`iStart`* 末尾の区切り文字の後の位置に更新されます。文字列の末尾に到達した場合は-1 になります。 を `Tokenize` 使用して、 *`iStart`* 次のトークンが読み込まれる文字列内の位置を追跡するために、を使用して、ターゲット文字列の残りの部分よりも多くのトークンを分割できます。 トークンがこれ以上ない場合、関数は空の文字列を返し、 *`iStart`* -1 に設定されます。

のような CRT トークン化関数とは異なり、は [`strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l`](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md) `Tokenize` ターゲット文字列を変更しません。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

この例の出力は次のとおりです。

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a> `CStringT::Trim`

文字列から先頭と末尾の文字をトリミングします。

```cpp
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>パラメーター

*`chTarget`*\
トリミングされる対象の文字。

*`pszTargets`*\
トリミングされる対象の文字を格納している文字列へのポインター。 内の文字の先頭および末尾の出現箇所 *`pszTargets`* はすべて、オブジェクトから削除され **`CStringT`** ます。

### <a name="return-value"></a>戻り値

トリミングされた文字列を返します。

### <a name="remarks"></a>注釈

次のいずれかの先頭および末尾の出現箇所をすべて削除します。

- で指定された文字 *`chTarget`* 。

- で指定された文字列内のすべての文字 *`pszTargets`* 。

- 前後.

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

この例の出力は次のとおりです。

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a> `CStringT::TrimLeft`

文字列から先頭の文字をトリミングします。

```cpp
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>パラメーター

*`chTarget`*\
トリミングされる対象の文字。

*`pszTargets`*\
トリミングされる対象の文字を格納している文字列へのポインター。 で先頭に出現する文字 *`pszTargets`* はすべて、オブジェクトから削除され **`CStringT`** ます。

### <a name="return-value"></a>戻り値

結果のトリミングされた文字列。

### <a name="remarks"></a>注釈

次のいずれかの先頭および末尾の出現箇所をすべて削除します。

- で指定された文字 *`chTarget`* 。

- で指定された文字列内のすべての文字 *`pszTargets`* 。

- 前後.

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a> `CStringT::TrimRight`

文字列の末尾の文字をトリミングします。

```cpp
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>パラメーター

*`chTarget`*\
トリミングされる対象の文字。

*`pszTargets`*\
トリミングされる対象の文字を格納している文字列へのポインター。 内のすべての文字の末尾の出現箇所 *`pszTargets`* は、オブジェクトから削除され **`CStringT`** ます。

### <a name="return-value"></a>戻り値

**`CStringT`** トリミングされた文字列を含むオブジェクトを返します。

### <a name="remarks"></a>注釈

次のいずれかの後続の出現箇所を削除します。

- で指定された文字 *`chTarget`* 。

- で指定された文字列内のすべての文字 *`pszTargets`* 。

- 前後.

バージョンは、 `CStringT& TrimRight(XCHAR chTarget)` 1 つの文字パラメーターを受け取り、文字列データの末尾からその文字のすべてのコピーを削除し **`CStringT`** ます。 文字列の末尾から開始し、前方に向かって機能します。 別の文字が検出されたとき、またはが **`CStringT`** 文字データを使い果たしたときに停止します。

バージョンでは、 `CStringT& TrimRight(PCXSTR pszTargets)` 検索するすべての異なる文字を含む、null で終わる文字列を受け入れます。 オブジェクト内のこれらの文字のコピーをすべて削除 **`CStringT`** します。 文字列の末尾から開始し、前方に向かって機能します。 対象の文字列に含まれていない文字が見つかった場合、またはが文字データを使い果たした場合に停止し **`CStringT`** ます。 ターゲット文字列全体をの末尾の部分文字列と一致させようとしません **`CStringT`** 。

バージョンでは `CStringT& TrimRight()` パラメーターは必要ありません。 文字列の末尾から空白文字をすべてトリミング **`CStringT`** します。 空白文字は、改行、スペース、またはタブにすることができます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)\
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)\
[CSimpleStringT クラス](../../atl-mfc-shared/reference/csimplestringt-class.md)
