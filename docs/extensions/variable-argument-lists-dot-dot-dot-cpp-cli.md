---
description: '詳細情報: 可変個引数リスト (...)(C++/CLI)'
title: 可変個引数リスト (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: fec05a2ce397a0991a4bfd0a5aeb6a8b16d986ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176848"
---
# <a name="variable-argument-lists--ccli"></a>可変個引数リスト (...) (C++/CLI)

この例では、C++/CLI で `...` 構文を使って可変個の引数を持つ関数を実装する方法を示します。

> [!NOTE]
> これは C++/CLI に関するトピックです。 ISO 標準 C++ でのの使用の詳細については `...` 、[後置式](../cpp/postfix-expressions.md)の「[省略記号と可変個引数のテンプレート](../cpp/ellipses-and-variadic-templates.md)」および「省略記号と既定の引数」を参照してください。

`...` を使用するパラメーターは、パラメーター リストの最後のパラメーターにする必要があります。

## <a name="example"></a>例

### <a name="code"></a>コード

```cpp
// mcppv2_paramarray.cpp
// compile with: /clr
using namespace System;
double average( ... array<Int32>^ arr ) {
   int i = arr->GetLength(0);
   double answer = 0.0;

   for (int j = 0 ; j < i ; j++)
      answer += arr[j];

   return answer / i;
}

int main() {
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));
}
```

```Output
3
```

## <a name="code-example"></a>コード例

次の例では、引数の数が可変である Visual C++ の関数を C# から呼び出す方法を示します。

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

たとえば、関数 `f` は、可変個の引数を受け取ることができる関数であるかのように、C# または Visual Basic から呼び出すことができます。

C# では、`ParamArray` パラメーターに渡される引数は、可変個の引数で呼び出すことができます。 C# でのコード例を次に示します。

```csharp
// mcppv2_paramarray3.cs
// compile with: /r:mcppv2_paramarray2.dll
// a C# program

public class X {
   public static void Main() {
      // Visual C# will generate a String array to match the
      // ParamArray attribute
      C myc = new C();
      myc.f("hello", "there", "world");
   }
}
```

Visual C++ の `f` の呼び出しは、初期化された配列または可変長配列を渡すことができます。

```cpp
// mcpp_paramarray4.cpp
// compile with: /clr
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};

int main() {
   C ^ myc = gcnew C();
   myc->f("hello", "world", "!!!");
}
```

## <a name="see-also"></a>関連項目

[配列](arrays-cpp-component-extensions.md)
