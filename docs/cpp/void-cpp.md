---
title: void (C++)
ms.date: 11/04/2016
f1_keywords:
- void_cpp
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
ms.openlocfilehash: 2de019f908942a58b232877fcd9eebc4689d8e22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187480"
---
# <a name="void-c"></a>void (C++)

**Void**キーワードを関数の戻り値の型として使用すると、関数が値を返さないことを指定します。 関数のパラメーターリストで**void**を使用した場合、関数がパラメーターを受け取らないことを指定します。 ポインターの宣言で使用した場合、 **void**はポインターが "universal" であることを指定します。

ポインターの型が**void\*** の場合、ポインターは**const**または**volatile**キーワードで宣言されていない任意の変数を指すことができます。 **Void\*** ポインターは別の型にキャストしない限り、逆参照できません。 **Void\*** ポインターは、他の任意の型のデータポインターに変換できます。

**Void**ポインターは関数を指すことができますが、のC++クラスメンバーには参照できません。

**Void**型の変数を宣言することはできません。

## <a name="example"></a>例

```cpp
// void.cpp
void vobject;   // C2182
void *pv;   // okay
int *pint; int i;
int main() {
   pv = &i;
   // Cast optional in C required in C++
   pint = (int *)pv;
}
```

## <a name="see-also"></a>参照

[キーワード](../cpp/keywords-cpp.md)<br/>
[組み込みの型](../cpp/fundamental-types-cpp.md)
