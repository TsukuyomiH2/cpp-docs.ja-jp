---
title: helpfile (C++ COM 属性) |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9a498cefce01d5a22df5211d0f7bb2f64e3a7b79
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792090"
---
# <a name="helpfile"></a>helpfile

タイプ ライブラリのヘルプ ファイルの名前を設定します。

## <a name="syntax"></a>構文

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
ヘルプ トピックを含むファイルの名前。

## <a name="remarks"></a>Remarks

**Helpfile** C++ 属性と同じ機能を持つ、 [helpfile](/windows/desktop/Midl/helpfile) MIDL 属性。

## <a name="example"></a>例

例をご覧ください[モジュール](module-cpp.md)を使用する方法の例については**helpfile**します。

## <a name="requirements"></a>要件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**インターフェイス**、 **typedef**、**クラス**、メソッド、**プロパティ**|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、次を参照してください。[属性コンテキスト](cpp-attributes-com-net.md#contexts)します。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)  