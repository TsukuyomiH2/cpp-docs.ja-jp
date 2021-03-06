---
description: '詳細情報: IDispEventSimpleImpl クラス'
title: IDispEventSimpleImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
ms.openlocfilehash: 4b581f4e5714f595a29fb27bd6dbd45c7d5e401c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139504"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl クラス

このクラスは、 `IDispatch` タイプライブラリから型情報を取得せずに、メソッドの実装を提供します。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>パラメーター

*nID*<br/>
ソースオブジェクトの一意の識別子。 `IDispEventSimpleImpl`が複合コントロールの基底クラスである場合は、このパラメーターに対して目的のコントロールのリソース ID を使用します。 それ以外の場合は、任意の正の整数を使用します。

*T*<br/>
から派生したユーザーのクラス `IDispEventSimpleImpl` 。

*pdiid*<br/>
このクラスによって実装されるイベントディスパッチインターフェイスの IID へのポインター。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IDispEventSimpleImpl:: Advise](#advise)|既定のイベントソースとの接続を確立します。|
|[IDispEventSimpleImpl::D ispEventAdvise](#dispeventadvise)|イベントソースとの接続を確立します。|
|[IDispEventSimpleImpl::D ispEventUnadvise](#dispeventunadvise)|イベントソースとの接続を解除します。|
|[IDispEventSimpleImpl:: Idispatch.getidsofnames](#getidsofnames)|E_NOTIMPL を返します。|
|[IDispEventSimpleImpl:: GetTypeInfo](#gettypeinfo)|E_NOTIMPL を返します。|
|[IDispEventSimpleImpl:: GetTypeInfoCount](#gettypeinfocount)|E_NOTIMPL を返します。|
|[IDispEventSimpleImpl:: Invoke](#invoke)|イベントシンクマップに一覧表示されているイベントハンドラーを呼び出します。|
|[IDispEventSimpleImpl:: アドバイズ](#unadvise)|既定のイベントソースとの接続を解除します。|

## <a name="remarks"></a>解説

`IDispEventSimpleImpl` インターフェイスのすべてのメソッド/イベントに対して実装コードを指定することなく、イベントディスパッチインターフェイスを実装する方法を提供します。 `IDispEventSimpleImpl` メソッドの実装を提供 `IDispatch` します。 必要なのは、処理するイベントの実装を指定することだけです。

`IDispEventSimpleImpl` は、クラスのイベントシンクマップと連携して、適切なハンドラー関数にイベントをルーティングします。 このクラスを使用するには:

- 処理する各オブジェクトの各イベントについて、イベントシンクマップに [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) マクロを追加します。

- 各エントリのパラメーターとして [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) 構造体へのポインターを渡すことによって、各イベントの型情報を指定します。 X86 プラットフォームでは、 `_ATL_FUNC_INFO.cc` 値は __stdcall のコールバック関数の呼び出しメソッドで CC_CDECL する必要があります。

- [Dispeventadvise](#dispeventadvise)を呼び出して、ソースオブジェクトと基本クラスの間の接続を確立します。

- [Dispeventunadvise](#dispeventunadvise)を呼び出して、接続を切断します。

`IDispEventSimpleImpl`イベントを処理する必要があるオブジェクトごとに、( *nID* に一意の値を使用して) から派生する必要があります。 1つのソースオブジェクトに対して unadvising で基底クラスを再利用し、別のソースオブジェクトに対してアドバイズすることができますが、一度に1つのオブジェクトによって処理できるソースオブジェクトの最大数は、基本クラスの数によって制限され `IDispEventSimpleImpl` ます。

`IDispEventSimplImpl` は [IDispEventImpl](../../atl/reference/idispeventimpl-class.md)と同じ機能を提供しますが、タイプライブラリからインターフェイスに関する型情報を取得しない点が異なります。 ウィザードでは、にのみ基づいたコードが生成され `IDispEventImpl` ますが、手動でコードを追加すること `IDispEventSimpleImpl` によってを使用できます。 `IDispEventSimpleImpl`イベントインターフェイスを記述するタイプライブラリがない場合、またはタイプライブラリの使用に関連するオーバーヘッドを回避する場合は、を使用します。

> [!NOTE]
> `IDispEventImpl` と `IDispEventSimpleImpl` `IUnknown::QueryInterface` は、各 `IDispEventImpl` または `IDispEventSimpleImpl` 基本クラスが個別の com id として機能できるようにするための独自の実装を提供しながら、メイン com オブジェクトのクラスメンバーに直接アクセスできるようにします。

CE ATL の ActiveX イベントシンクの実装では、イベントハンドラーメソッドから HRESULT 型または void 型の戻り値のみがサポートされます。その他の戻り値はサポートされておらず、その動作は未定義です。

詳細については、「 [IDispEventImpl のサポート](../../atl/supporting-idispeventimpl.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>要件

**ヘッダー:** atlcom. h

## <a name="idispeventsimpleimpladvise"></a><a name="advise"></a> IDispEventSimpleImpl:: Advise

このメソッドを呼び出して、 *pUnk* によって表されるイベントソースとの接続を確立します。

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>パラメーター

*パンク*<br/>
から `IUnknown` イベントソースオブジェクトのインターフェイスへのポインター。

### <a name="return-value"></a>戻り値

S_OK または失敗の HRESULT 値。

### <a name="remarks"></a>解説

接続が確立されると、 *pUnk* から発生したイベントは、イベントシンクマップを使用してクラス内のハンドラーにルーティングされます。

> [!NOTE]
> クラスが複数のクラスから派生している場合は `IDispEventSimpleImpl` 、対象となる特定の基本クラスを使用して呼び出しのスコープを設定することによって、このメソッドの呼び出しを明確にする必要があります。

`Advise` 既定のイベントソースとの接続を確立します。これは、 [Atlgetobjectsourceinterface](composite-control-global-functions.md#atlgetobjectsourceinterface)によって決定されるオブジェクトの既定のイベントソースの IID を取得します。

## <a name="idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a> IDispEventSimpleImpl::D ispEventAdvise

このメソッドを呼び出して、 *pUnk* によって表されるイベントソースとの接続を確立します。

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>パラメーター

*パンク*<br/>
から `IUnknown` イベントソースオブジェクトのインターフェイスへのポインター。

*piid*<br/>
イベントソースオブジェクトの IID へのポインター。

### <a name="return-value"></a>戻り値

S_OK または失敗の HRESULT 値。

### <a name="remarks"></a>解説

その後、 *pUnk* から発生したイベントは、イベントシンクマップを使用してクラス内のハンドラーにルーティングされます。

> [!NOTE]
> クラスが複数のクラスから派生している場合は `IDispEventSimpleImpl` 、対象となる特定の基本クラスを使用して呼び出しのスコープを設定することによって、このメソッドの呼び出しを明確にする必要があります。

`DispEventAdvise` で指定されたイベントソースとの接続を確立 `pdiid` します。

## <a name="idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a> IDispEventSimpleImpl::D ispEventUnadvise

*PUnk* によって表されるイベントソースとの接続を解除します。

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>パラメーター

*パンク*<br/>
から `IUnknown` イベントソースオブジェクトのインターフェイスへのポインター。

*piid*<br/>
イベントソースオブジェクトの IID へのポインター。

### <a name="return-value"></a>戻り値

S_OK または失敗の HRESULT 値。

### <a name="remarks"></a>解説

接続が切断されると、イベントシンクマップに示されているハンドラー関数にイベントがルーティングされなくなります。

> [!NOTE]
> クラスが複数のクラスから派生している場合は `IDispEventSimpleImpl` 、対象となる特定の基本クラスを使用して呼び出しのスコープを設定することによって、このメソッドの呼び出しを明確にする必要があります。

`DispEventAdvise` で指定されたイベントソースを使用して確立された接続を切断 `pdiid` します。

## <a name="idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a> IDispEventSimpleImpl:: Idispatch.getidsofnames

のこの実装は `IDispatch::GetIDsOfNames` E_NOTIMPL を返します。

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>解説

Windows SDK の「 [IDispatch:: idispatch.getidsofnames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 」を参照してください。

## <a name="idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a> IDispEventSimpleImpl:: GetTypeInfo

のこの実装は `IDispatch::GetTypeInfo` E_NOTIMPL を返します。

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>解説

Windows SDK の「 [IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) 」を参照してください。

## <a name="idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a> IDispEventSimpleImpl:: GetTypeInfoCount

のこの実装は `IDispatch::GetTypeInfoCount` E_NOTIMPL を返します。

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>解説

Windows SDK の「 [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) 」を参照してください。

## <a name="idispeventsimpleimplinvoke"></a><a name="invoke"></a> IDispEventSimpleImpl:: Invoke

このの実装は `IDispatch::Invoke` 、イベントシンクマップに一覧表示されているイベントハンドラーを呼び出します。

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```

### <a name="remarks"></a>解説

「 [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)」を参照してください。

## <a name="idispeventsimpleimplunadvise"></a><a name="unadvise"></a> IDispEventSimpleImpl:: アドバイズ

*PUnk* によって表されるイベントソースとの接続を解除します。

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>パラメーター

*パンク*<br/>
から `IUnknown` イベントソースオブジェクトのインターフェイスへのポインター。

### <a name="return-value"></a>戻り値

S_OK または失敗の HRESULT 値。

### <a name="remarks"></a>解説

接続が切断されると、イベントシンクマップに示されているハンドラー関数にイベントがルーティングされなくなります。

> [!NOTE]
> クラスが複数のクラスから派生している場合は `IDispEventSimpleImpl` 、対象となる特定の基本クラスを使用して呼び出しのスコープを設定することによって、このメソッドの呼び出しを明確にする必要があります。

`Unadvise` で指定された既定のイベントソースを使用して確立された接続を切断 `pdiid` します。

`Unavise` 既定のイベントソースとの接続を解除します。これは、 [Atlgetobjectsourceinterface](composite-control-global-functions.md#atlgetobjectsourceinterface)によって決定されるオブジェクトの既定のイベントソースの IID を取得します。

## <a name="see-also"></a>関連項目

[_ATL_FUNC_INFO 構造体](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl クラス](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl クラス](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
