---
description: '詳細情報: COleTemplateServer クラス'
title: COleTemplateServer クラス
ms.date: 11/04/2016
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
ms.openlocfilehash: da4351730fe548c83e073d3f6eaa02bc0c88cd0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226624"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer クラス

OLE のビジュアル編集サーバー、オートメーション サーバー、およびリンク コンテナー (埋め込みアイテムへのリンクをサポートするアプリケーションのことです) で使います。

## <a name="syntax"></a>構文

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleTemplateServer:: COleTemplateServer](#coletemplateserver)|`COleTemplateServer` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleTemplateServer:: ConnectTemplate](#connecttemplate)|ドキュメントテンプレートを基になるオブジェクトに接続 `COleObjectFactory` します。|
|[COleTemplateServer:: 登録解除](#unregister)|関連付けられたドキュメントテンプレートの登録を解除します。|
|[COleTemplateServer:: UpdateRegistry](#updateregistry)|ドキュメントの種類を OLE システムレジストリに登録します。|

## <a name="remarks"></a>解説

このクラスは、クラス [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)から派生します。通常は、独自の `COleTemplateServer` クラスを派生するのではなく、直接を使用できます。 `COleTemplateServer` は、 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) オブジェクトを使用してサーバードキュメントを管理します。 `COleTemplateServer`完全なサーバー (スタンドアロンアプリケーションとして実行できるサーバー) を実装する場合は、を使用します。 フルサーバーは通常、マルチドキュメントインターフェイス (MDI) アプリケーションですが、シングルドキュメントインターフェイス (SDI) アプリケーションはサポートされています。 アプリケーションでサポートされている `COleTemplateServer` サーバードキュメントの種類ごとに1つのオブジェクトが必要です。つまり、サーバーアプリケーションでワークシートとグラフの両方がサポートされている場合は、2つのオブジェクトが必要です `COleTemplateServer` 。

`COleTemplateServer``OnCreateInstance`によって定義されたメンバー関数をオーバーライド `COleObjectFactory` します。 このメンバー関数は、適切な型の C++ オブジェクトを作成するためにフレームワークによって呼び出されます。

サーバーの詳細については、「サーバー [: サーバーの実装](../../mfc/servers-implementing-a-server.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>要件

**ヘッダー :** afxdisp.h

## <a name="coletemplateservercoletemplateserver"></a><a name="coletemplateserver"></a> COleTemplateServer:: COleTemplateServer

`COleTemplateServer` オブジェクトを構築します。

```
COleTemplateServer();
```

### <a name="remarks"></a>解説

クラスの使用方法の簡単な説明については、 `COleTemplateServer` 「 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) クラスの概要」を参照してください。

## <a name="coletemplateserverconnecttemplate"></a><a name="connecttemplate"></a> COleTemplateServer:: ConnectTemplate

*PDocTemplate* が指すドキュメントテンプレートを、基になる [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)オブジェクトに接続します。

```cpp
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
テンプレートが要求する OLE クラス ID への参照。

*pDocTemplate*<br/>
ドキュメントテンプレートへのポインター。

*渡し*<br/>
アプリケーションの単一のインスタンスが複数のインスタンス化をサポートできるかどうかを示します。 TRUE の場合、オブジェクトを作成する要求ごとに、アプリケーションの複数のインスタンスが起動されます。

### <a name="remarks"></a>解説

詳細については、Windows SDK の「 [CLSID キー](/windows/win32/com/clsid-key-hklm) 」を参照してください。

## <a name="coletemplateserverunregister"></a><a name="unregister"></a> COleTemplateServer:: 登録解除

関連付けられたドキュメントテンプレートの登録を解除します。

```
BOOL Unregister();
```

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>解説

EnterRemarks

## <a name="coletemplateserverupdateregistry"></a><a name="updateregistry"></a> COleTemplateServer:: UpdateRegistry

ドキュメントテンプレート文字列からファイル型情報を読み込み、その情報を OLE システムレジストリに配置します。

```cpp
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>パラメーター

*nAppType*<br/>
AFXDISP.H で定義されている OLE_APPTYPE 列挙型の値。 次のいずれかの値を指定できます。

- OAT_INPLACE_SERVER サーバーにはサーバーの完全なユーザーインターフェイスがあります。

- OAT_SERVER サーバーでは、埋め込みのみがサポートされます。

- OAT_CONTAINER コンテナーは、埋め込みオブジェクトへのリンクをサポートしています。

- OAT_DISPATCH_OBJECT オブジェクトは `IDispatch` 対応しています。

- OAT_DOC_OBJECT_SERVER サーバーでは、埋め込みとドキュメントオブジェクトコンポーネントモデルの両方がサポートされています。

*rglpszRegister*<br/>
エントリが存在しない場合にのみ、レジストリに書き込まれるエントリの一覧。

*rglpszOverwrite*<br/>
前のエントリが存在するかどうかに関係なく、レジストリに書き込まれるエントリの一覧。

*bRegister*<br/>
クラスを登録するかどうかを決定します。 *Bregister* が TRUE の場合、クラスはシステムレジストリに登録されます。 それ以外の場合は、クラスの登録を解除します。

### <a name="remarks"></a>解説

登録情報は、 [CDocTemplate:: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)を呼び出すことによって読み込まれます。 取得される部分文字列は、 `regFileTypeId` `regFileTypeName` リファレンスページで説明されているように、インデックス、、およびによって識別され `fileNewName` `GetDocString` ます。

`regFileTypeId`部分文字列が空の場合、またはの呼び出しが `GetDocString` その他の理由で失敗した場合、この関数は失敗し、ファイル情報はレジストリに入力されません。

引数 *Rglpszregister* および *Rglpszregister* の情報は、 [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass)を呼び出すことによってレジストリに書き込まれます。 既定の情報は、2つの引数が NULL の場合に登録され、ほとんどのアプリケーションに適しています。 これらの引数の情報の構造については、「」を参照してください `AfxOleRegisterServerClass` 。

詳細については、「 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)」を参照してください。

## <a name="see-also"></a>関連項目

[MFC サンプル HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory クラス](../../mfc/reference/coleobjectfactory-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc クラス](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem クラス](../../mfc/reference/coleserveritem-class.md)
