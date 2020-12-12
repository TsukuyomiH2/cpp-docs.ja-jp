---
description: 詳細については、「コンパイラエラー C3492」を参照してください。
title: コンパイラ エラー C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: bceeded1de628604c29ef124adacc23ded72f15b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113156"
---
# <a name="compiler-error-c3492"></a>コンパイラ エラー C3492

'var': 匿名共用体のメンバーをキャプチャすることはできません

無名の共用体のメンバーをキャプチャすることはできません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- 共用体に名前を付け、ラムダ式のキャプチャの一覧に、完全な共用体の構造体を渡します。

## <a name="examples"></a>例

次の例では、匿名共用体のメンバーをキャプチャするために C3492 が生成されます。

```cpp
// C3492a.cpp

int main()
{
   union
   {
      char ch;
      int x;
   };

   ch = 'y';
   [&x](char ch) { x = ch; }(ch); // C3492
}
```

次の例では、共用体に名前を付け、ラムダ式のキャプチャの一覧に完全な共用体の構造を渡すことによって、C3492 が解決されます。

```cpp
// C3492b.cpp

int main()
{
   union
   {
      char ch;
      int x;
   } u;

   u.ch = 'y';
   [&u](char ch) { u.x = ch; }(u.ch);
}
```

## <a name="see-also"></a>関連項目

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
