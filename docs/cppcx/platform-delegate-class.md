---
description: '詳細情報: Platform::D delegate クラス'
title: Platform::Delegate クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
ms.openlocfilehash: 58baedf595d3ee8d9cc4975e787193abf522233c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176107"
---
# <a name="platformdelegate-class"></a>Platform::Delegate クラス

関数オブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
public delegate void delegate_name();
```

### <a name="members"></a>メンバー

Delegate クラスには、 [Platform::Object Class](../cppcx/platform-object-class.md)から派生した Equals()、GetHashCode()、ToString() メソッドがあります。

### <a name="remarks"></a>解説

デリゲートを作成するには [delegate](../extensions/delegate-cpp-component-extensions.md) キーワードを使用します。Platform::Delegate を明示的に使用しないでください。 詳細については、「[デリゲート](../cppcx/delegates-c-cx.md)」を参照してください。 デリゲートを作成および使用する方法の例については、 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)を参照してください。

### <a name="requirements"></a>要件

**サポートされている最低限のクライアント:** Windows 8

**サポートされる最小サーバー:** Windows Server 2012

**名前空間:** Platform

**メタデータ:** platform. winmd

## <a name="see-also"></a>関連項目

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)
