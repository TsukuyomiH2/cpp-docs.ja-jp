---
description: '詳細情報: vector &lt; bool &gt; :: reference クラス'
title: vector&lt;bool&gt;::reference クラス
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 4e9e4700f8af269f02f038c37d55460bae3a2a96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280483"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference クラス

クラスは、 `vector<bool>::reference` をシミュレートする [vector \<bool> クラス](../standard-library/vector-bool-class.md) によって提供されるプロキシクラスです `bool&` 。

## <a name="remarks"></a>解説

C++ では、ネイティブにビットを直接参照しないため、シミュレートされた参照が必要です。 `vector<bool>` は、要素ごとに 1 ビットだけ使用します。このビットは、このプロキシ クラスを使用して参照できます。 ただし、参照のシミュレーションは、特定の代入が有効でないため、完全ではありません。 たとえば、オブジェクトのアドレスを取得できないため、を使用しようとして `vector<bool>::reference` いる次のコード `vector<bool>::operator&` は正しくありません。

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|vector 要素のブール値を反転します。|
|[bool 演算子](../standard-library/vector-bool-reference-operator-bool.md)|からへの暗黙の型変換を提供 `vector<bool>::reference` **`bool`** します。|
|[operator =](../standard-library/vector-bool-reference-operator-assign.md)|ブール値をビットに割り当てます。または参照先の要素が保持している値をビットに割り当てます。|

## <a name="requirements"></a>要件

**ヘッダー**: \<vector>

**名前空間:** std

## <a name="see-also"></a>関連項目

[\<vector>](../standard-library/vector.md)\
[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリリファレンス](../standard-library/cpp-standard-library-reference.md)
