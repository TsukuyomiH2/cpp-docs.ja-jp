---
description: '詳細情報: IRegistrar インターフェイス'
title: IRegistrar インターフェイス
ms.date: 02/01/2017
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
ms.openlocfilehash: 9a138468ccbf21594c4e9d88d1ed2387a4c1052a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139166"
---
# <a name="iregistrar-interface"></a>IRegistrar インターフェイス

このインターフェイスは atliface で定義され、 [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)などの CAtlModule メンバー関数によって内部的に使用されます。

## <a name="syntax"></a>構文

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>解説

詳細については、「 [置換可能なパラメーター (レジストラーのプリプロセッサ) の使用](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) 」を参照してください。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IRegistrar:: ResourceRegisterSz](#resourceregistersz)|リソースを登録します。 |
|[IRegistrar:: ResourceUnregisterSz](#resourceunregistersz)| リソースの登録を解除します。|
|[IRegistrar:: FileRegister](#fileregister)|ファイルを登録します。|
|[IRegistrar:: FileUnregister 解除](#fileunregister)|ファイルの登録を解除します。|
|[IRegistrar:: StringRegister](#stringregister)|文字列を登録します。|
|[IRegistrar:: StringUnregister 解除](#stringunregister)|文字列の登録を解除します|
|[IRegistrar:: ResourceRegister](#resourceregister)|リソースを登録します。|
|[IRegistrar:: ResourceUnregister 解除](#resourceunregister)|リソースの登録を解除します。|

## <a name="requirements"></a>要件

**ヘッダー:** atlifase

## <a name="iregistrarresourceregistersz"></a><a name="resourceregistersz"></a> IRegistrar:: ResourceRegisterSz

リソースを登録します。

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregistersz"></a><a name="resourceunregistersz"></a> IRegistrar:: ResourceUnregisterSz

リソースの登録を解除します。

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarfileregister"></a><a name="fileregister"></a> IRegistrar:: FileRegister

ファイルを登録します。

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarfileunregister"></a><a name="fileunregister"></a> IRegistrar:: FileUnregister 解除

ファイルの登録を解除します。

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarstringregister"></a><a name="stringregister"></a> IRegistrar:: StringRegister

指定した文字列データを登録します。

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarstringunregister"></a><a name="stringunregister"></a> IRegistrar:: StringUnregister 解除

指定された文字列データの登録を解除します。

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarresourceregister"></a><a name="resourceregister"></a> IRegistrar:: ResourceRegister

リソースを登録します。

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregister"></a><a name="resourceunregister"></a> IRegistrar:: ResourceUnregister 解除

リソースの登録を解除します。

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>関連項目

[置き換え可能パラメーターの使用 (レジストラーのプリプロセッサ)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[モジュールクラス](../../atl/atl-module-classes.md)<br/>
[レジストリ コンポーネント (レジストラー)](../../atl/atl-registry-component-registrar.md)
