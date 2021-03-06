---
description: '詳細については、次を参照してください: make_public プラグマ'
title: make_public プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: 327a9882e13f9c51182e0673443566b56177d320
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333411"
---
# <a name="make_public-pragma"></a>make_public プラグマ

ネイティブ型はパブリック アセンブリのアクセシビリティが必要であることを示します。

## <a name="syntax"></a>構文

> **#pragma make_public (** *型* **)**

### <a name="parameters"></a>パラメーター

*type*\
パブリックアセンブリのアクセシビリティを設定する型の名前。

## <a name="remarks"></a>解説

**make_public** は、参照するネイティブ型が、変更できないヘッダーファイルからのものである場合に便利です。 パブリック関数のシグネチャでネイティブ型を使用する場合は、公開されている型のアセンブリの参照可能範囲を使用する必要があります。または、ネイティブ型にパブリックアセンブリのアクセシビリティがあること、またはコンパイラが警告を発行する必要があります。

グローバルスコープで **make_public** を指定する必要があります。 これは、ソースコードファイルの末尾までを通じて宣言されているポイントからのみ有効です。

ネイティブ型は、暗黙的または明示的にプライベートにすることができます。 詳細については、「 [型の可視性](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)」を参照してください。

## <a name="examples"></a>例

次の例は、2つのネイティブ構造体の定義を含むヘッダーファイルの内容を示しています。

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

次のコードサンプルでは、ヘッダーファイルを使用します。 **Make_public** を使用してネイティブ構造体をパブリックとして明示的にマークしない限り、パブリックなマネージ型のパブリック関数のシグネチャでネイティブ構造体を使用しようとすると、コンパイラは警告を生成します。

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>関連項目

[プラグマ ディレクティブと __pragma キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
