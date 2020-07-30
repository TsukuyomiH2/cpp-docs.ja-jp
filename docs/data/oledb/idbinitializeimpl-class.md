---
title: IDBInitializeImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl::IDBInitializeImpl
- Initialize
- IDBInitializeImpl::Initialize
- IDBInitializeImpl.Initialize
- IDBInitializeImpl.Uninitialize
- Uninitialize
- IDBInitializeImpl::Uninitialize
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
- ATL::IDBInitializeImpl<T>::m_pCUtlPropInfo
- m_pCUtlPropInfo
- IDBInitializeImpl::m_pCUtlPropInfo
- ATL.IDBInitializeImpl.m_pCUtlPropInfo
- IDBInitializeImpl<T>::m_pCUtlPropInfo
- IDBInitializeImpl.m_pCUtlPropInfo
- ATL::IDBInitializeImpl::m_pCUtlPropInfo
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
ms.openlocfilehash: 511d67586a7adc2b26cc6acbdf39beff78f9c38a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218326"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl クラス

[IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85))インターフェイスの実装を提供します。

## <a name="syntax"></a>構文

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>パラメーター

*T*<br/>
から派生したクラス `IDBInitializeImpl` 。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|コンストラクターです。|

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[初期化する](#initialize)|プロバイダーを起動します。|
|[解除](#uninitialize)|プロバイダーを停止します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_dwStatus](#dwstatus)|データソースフラグ。|
|[m_pCUtlPropInfo](#pcutlpropinfo)|DB プロパティ情報の実装へのポインター。|

## <a name="remarks"></a>解説

データソースオブジェクトの必須インターフェイスであり、列挙子のオプションのインターフェイスです。

## <a name="idbinitializeimplidbinitializeimpl"></a><a name="idbinitializeimpl"></a>IDBInitializeImpl:: IDBInitializeImpl

コンストラクターです。

### <a name="syntax"></a>構文

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>解説

すべてのデータメンバーを初期化します。

## <a name="idbinitializeimplinitialize"></a><a name="initialize"></a>IDBInitializeImpl:: Initialize

プロパティサポートを準備して、データソースオブジェクトを初期化します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>解説

*OLE DB プログラマーリファレンス*の「 [IDBInitialize:: Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85)) 」を参照してください。

## <a name="idbinitializeimpluninitialize"></a><a name="uninitialize"></a>IDBInitializeImpl:: 初期化解除

プロパティサポートなどの内部リソースを解放することによって、データソースオブジェクトを初期化されていない状態で配置します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>解説

*OLE DB プログラマーのリファレンス*にある「 [IDBInitialize:: の初期化](/previous-versions/windows/desktop/ms719648(v=vs.85))を解除する」を参照してください。

## <a name="idbinitializeimplm_dwstatus"></a><a name="dwstatus"></a>IDBInitializeImpl:: m_dwStatus

データソースフラグ。

### <a name="syntax"></a>構文

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>解説

これらのフラグは、データソースオブジェクトのさまざまな属性の状態を指定または示します。 次の値が1つ以上含まれてい **`enum`** ます。

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|初期化されていない状態の復元を有効にするマスク。|
|`DSF_PERSIST_DIRTY`|データソースオブジェクトが永続化を必要とする場合 (つまり、変更があった場合) に設定します。|
|`DSF_INITIALIZED`|データソースが初期化されている場合に設定します。|

## <a name="idbinitializeimplm_pcutlpropinfo"></a><a name="pcutlpropinfo"></a>IDBInitializeImpl:: m_pCUtlPropInfo

DB プロパティ情報の実装オブジェクトへのポインター。

### <a name="syntax"></a>構文

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレートに関するページ](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダーテンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)
