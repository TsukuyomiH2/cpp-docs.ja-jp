---
title: ActivatableClass マクロ
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
ms.openlocfilehash: 7d38db9e7d3fa94c89195b6379e14692f26f7ee5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037595"
---
# <a name="activatableclass-macros"></a>ActivatableClass マクロ

指定したクラスのインスタンスを作成できるファクトリを含む内部キャッシュを設定します。

## <a name="syntax"></a>構文

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>パラメーター

*クラス名*<br/>
作成するクラスの名前です。

*factory*<br/>
指定したクラスのインスタンスを作成するファクトリ。

*サーバー名*<br/>
モジュールのファクトリのサブセットを指定する名前。

## <a name="remarks"></a>Remarks

これらのマクロで使わないクラシック COM を使用しない限り、`#undef`ことを確認するディレクティブ、`__WRL_WINRT_STRICT__`マクロ定義が削除されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Module クラス](module-class.md)