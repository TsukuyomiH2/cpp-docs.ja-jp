---
description: '詳細情報: CMFCCustomColorsPropertyPage クラス'
title: CMFCCustomColorsPropertyPage クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: 9a1e5a83f2dcb291b266c3ef8fcd65422d30135a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193345"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage クラス

色のダイアログボックスでカスタム色を選択できるプロパティページを表します。

## <a name="syntax"></a>構文

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|-|-|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|既定のコンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|-|-|
|`CMFCCustomColorsPropertyPage::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|`CMFCCustomColorsPropertyPage::GetThisClass`|このクラス型に関連付けられている [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCCustomColorsPropertyPage:: Setup](#setup)|プロパティページのカラーコンポーネントを設定します。|

### <a name="remarks"></a>解説

`CMFCColorDialog`クラスは、このクラスを使用して、カスタムカラープロパティページを表示します。 の詳細について `CMFCColorDialog` は、「 [CMFCColorDialog クラス](../../mfc/reference/cmfccolordialog-class.md)」を参照してください。

## <a name="example"></a>例

次の例では、オブジェクトを作成 `CMFCCustomColorsPropertyPage` し、プロパティページのカラーコンポーネントを設定する方法を示します。

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>要件

**ヘッダー:** afxcustomcolorspropertypage

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a> CMFCCustomColorsPropertyPage:: Setup

プロパティページのカラーコンポーネントを設定します。

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>パラメーター

*\R\n\r\n*\
からRGB 値の赤の要素。

*A-g-dl-p*\
からRGB 値の緑の要素。

*B*\
からRGB 値の青の要素。

### <a name="remarks"></a>解説

このメソッドは、プロパティページの現在の RGB および関連する HLS (色合い、明るさ、鮮やかさ) の値を更新します。 [CMFCColorDialog:: SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo)メソッドは、フレームワークが色のダイアログボックスを初期化したとき、またはユーザーがマウスの左ボタンを押したときに、このメソッドを呼び出します。 の詳細について `CMFCColorDialog` は、「 [CMFCColorDialog クラス](../../mfc/reference/cmfccolordialog-class.md)」を参照してください。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog クラス](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage クラス](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
