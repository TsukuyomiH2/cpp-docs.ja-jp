---
description: 詳細については、「コンパイラエラー C3489」を参照してください。
title: コンパイラ エラー C3489
ms.date: 11/04/2016
f1_keywords:
- C3489
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
ms.openlocfilehash: 658fc83476a9fe6f0db3ac27f44a05e1cb1d0c28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315647"
---
# <a name="compiler-error-c3489"></a>コンパイラ エラー C3489

既定のキャプチャ モードが値キャプチャである場合、'var' が必要です

ラムダ式の既定のキャプチャ モードが値渡しであることを指定する場合は、その式の capture 句に値によって変数を渡すことができません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- capture 句に明示的に変数を渡さないでください。

- 既定のキャプチャ モードとして値渡しを指定しないでください。

- 既定のキャプチャ モードとして参照渡しを指定します。

- capture 句に参照によって変数を渡します。 (これにより、ラムダ式の動作が変更される可能性があります。)

## <a name="examples"></a>例

次の例では、既定のモードが値渡しであるラムダ式の capture 句に、変数 `n` が値渡しで出現し、C3489 が生成されます。

```cpp
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

次の例では、C3489 について考えられる 4 つの解決策を示します。

```cpp
// C3489b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass n to the capture clause.
   [=]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-value as the default capture mode.
   [n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-reference as the default capture mode.
   [&, n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by reference to the capture clause.
   [&n]() { return n; } ();
}
```

## <a name="see-also"></a>関連項目

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
