﻿---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: 0f6b58896cbcb11901721125f9b1a32a99acb357
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227141"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>構文

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>解説

クラスメンバーのリストを前に指定すると、キーワードは、 **`public`** これらのメンバーが任意の関数からアクセスできることを指定します。 これは、次のアクセス指定子またはクラスの末尾までで宣言されているすべてのメンバーに適用されます。

基底クラスの名前を前に付けた場合、キーワードは、 **`public`** 基底クラスのパブリックメンバーとプロテクトメンバーが、それぞれ派生クラスのパブリックメンバーとプロテクトメンバーであることを指定します。

クラスのメンバーの既定のアクセスはプライベートです。 構造体または共用体のメンバーの既定のアクセスはパブリックです。

基底クラスの既定のアクセスは、クラスの場合はプライベートで、構造体の場合はパブリックです。 共用体に基底クラスを設定することはできません。

詳細については、「 [private](../cpp/private-cpp.md)」、「 [protected](../cpp/protected-cpp.md)」、「 [Friend](../cpp/friend-cpp.md)」、および「[クラスメンバーへのアクセスの制御](member-access-control-cpp.md)」のメンバーアクセステーブルを参照してください。

## <a name="clr-specific"></a>/clr 固有

CLR 型では、C++ アクセス指定子キーワード ( **`public`** 、 **`private`** 、および) は、 **`protected`** アセンブリに関して型およびメソッドの可視性に影響を与える可能性があります。 詳細については、「[メンバー Access Control](member-access-control-cpp.md)」を参照してください。

> [!NOTE]
> [/LN](../build/reference/ln-create-msil-module.md)でコンパイルされたファイルは、この動作の影響を受けません。 この場合、すべてのマネージド クラス (パブリックかプライベート) が表示されます。

## <a name="end-clr-specific"></a>END /clr 固有

## <a name="example"></a>例

```cpp
// keyword_public.cpp
class BaseClass {
public:
   int pubFunc() { return 0; }
};

class DerivedClass : public BaseClass {};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   aBase.pubFunc();       // pubFunc() is accessible
                          //    from any function
   aDerived.pubFunc();    // pubFunc() is still public in
                          //    derived class
}
```

## <a name="see-also"></a>関連項目

[クラス メンバーへのアクセス制御](member-access-control-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)
