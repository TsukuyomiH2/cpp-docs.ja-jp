---
title: コンパイラ エラー C3821
ms.date: 11/04/2016
f1_keywords:
- C3821
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
ms.openlocfilehash: 97d6dc0544176d90b90702a7d1f1648e8e98d756
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686627"
---
# <a name="compiler-error-c3821"></a>コンパイラ エラー C3821

' function ': マネージド型または関数は、アンマネージ関数では使用できません

インラインアセンブリまたは [setjmp](../../c-runtime-library/reference/setjmp.md) を持つ関数には、値型またはマネージクラスを含めることはできません。 このエラーを修正するには、インラインアセンブリを削除する `setjmp` か、マネージオブジェクトを削除します。

C3821 は、vararg 関数で自動ストレージを使用しようとした場合にも発生する可能性があります。  詳細については、「 [変数引数リスト (...)」 (c++/cli)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md) および「 [c++ Stack セマンティクス (参照型](../../dotnet/cpp-stack-semantics-for-reference-types.md))」を参照してください。

## <a name="examples"></a>例

次の例では、C3821 が生成されます。

```cpp
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

次の例では、C3821 が生成されます。

```cpp
// C3821b.cpp
// compile with: /clr
// processor: /x86
ref class A {
   public:
   int i;
};

int main() {
   // cannot use managed classes in this function
   A ^a;

   __asm {
      nop
   }
} // C3821
```
