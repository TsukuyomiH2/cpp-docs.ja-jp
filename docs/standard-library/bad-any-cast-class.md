---
title: bad_any_cast クラス
ms.date: 04/04/2019
f1_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
helpviewer_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
ms.openlocfilehash: b47ca4f615c6f317f17ce64e8388ae5d698185ea
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844588"
---
# <a name="bad_any_cast-class"></a>bad_any_cast クラス

によってスローされたオブジェクトが失敗しました `any_cast` 。

## <a name="syntax"></a>構文

```cpp
class bad_any_cast
```

### <a name="member-functions"></a>メンバー関数

|名前|説明|
|-|-|
|[結果](#what)|型を返します。|

## <a name="what"></a><a name="what"></a> 結果

型を返します。

```cpp
const char* what() const noexcept override;
```
