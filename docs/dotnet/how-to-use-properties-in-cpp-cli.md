---
description: '詳細については、「方法: C++/CLI でプロパティを使用する」を参照してください。'
title: '方法: C++/CLI でプロパティを使用する'
ms.date: 07/21/2017
helpviewer_keywords:
- simple properties
- properties [C++], simple
ms.assetid: f5d82547-e214-4f05-9e1b-ddb6d0dc5e4c
ms.openlocfilehash: 4db093e10d40e86723ef4101997f6015f37401be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286268"
---
# <a name="how-to-use-properties-in-ccli"></a>方法: C++/CLI でプロパティを使用する

この記事では、C++/CLI でプロパティを使用する方法について説明します。

## <a name="basic-properties"></a>基本的な性質

基本プロパティ (プライベートデータメンバーを割り当てて取得するだけのプロパティ) では、get および set アクセサー関数を明示的に定義する必要はありません。これは、プロパティのデータ型のみが指定された場合に、コンパイラがそれらを自動的に提供するためです。 このコードは、基本的なプロパティを示しています。

```cpp
// SimpleProperties.cpp
// compile with: /clr
using namespace System;

ref class C {
public:
   property int Size;
};

int main() {
   C^ c = gcnew C;
   c->Size = 111;
   Console::WriteLine("c->Size = {0}", c->Size);
}
```

```Output
c->Size = 111
```

## <a name="static-properties"></a>静的プロパティ

このコードサンプルでは、静的プロパティを宣言して使用する方法を示します。  静的プロパティは、そのクラスの静的メンバーにのみアクセスできます。

```cpp
// mcppv2_property_3.cpp
// compile with: /clr
using namespace System;

ref class StaticProperties {
   static int MyInt;
   static int MyInt2;

public:
   static property int Static_Data_Member_Property;

   static property int Static_Block_Property {
      int get() {
         return MyInt;
      }

      void set(int value) {
         MyInt = value;
      }
   }
};

int main() {
   StaticProperties::Static_Data_Member_Property = 96;
   Console::WriteLine(StaticProperties::Static_Data_Member_Property);

   StaticProperties::Static_Block_Property = 47;
   Console::WriteLine(StaticProperties::Static_Block_Property);
}
```

```Output
96
47
```

## <a name="indexed-properties"></a>インデックス付きプロパティ

インデックス付きプロパティは、通常、添字演算子を使用してアクセスされるデータ構造を公開します。

既定のインデックス付きプロパティを使用する場合は、クラス名を参照するだけでデータ構造にアクセスできますが、ユーザー定義のインデックス付きプロパティを使用する場合は、データ構造にアクセスするためのプロパティ名を指定する必要があります。

C# で記述されたインデクサーを使用する方法については、「 [方法: C# インデクサーを使用する (C++/cli)](./interoperability-with-other-dotnet-languages-cpp-cli.md#consume_indexer)」を参照してください。

このコードサンプルでは、既定のインデックス付きプロパティとユーザー定義のインデックス付きプロパティを使用する方法を示します。

```cpp
// mcppv2_property_2.cpp
// compile with: /clr
using namespace System;
public ref class C {
   array<int>^ MyArr;

public:
   C() {
      MyArr = gcnew array<int>(5);
   }

   // default indexer
   property int default[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }

   // user-defined indexer
   property int indexer1[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }
};

int main() {
   C ^ MyC = gcnew C();

   // use the default indexer
   Console::Write("[ ");
   for (int i = 0 ; i < 5 ; i++) {
      MyC[i] = i;
      Console::Write("{0} ", MyC[i]);
   }

   Console::WriteLine("]");

   // use the user-defined indexer
   Console::Write("[ ");
   for (int i = 0 ; i < 5 ; i++) {
      MyC->indexer1[i] = i * 2;
      Console::Write("{0} ", MyC->indexer1[i]);
   }

   Console::WriteLine("]");
}
```

```Output
[ 0 1 2 3 4 ]
[ 0 2 4 6 8 ]
```

次のサンプルでは、ポインターを使用して既定のインデクサーを呼び出す方法を示し **`this`** ます。

```cpp
// call_default_indexer_through_this_pointer.cpp
// compile with: /clr /c
value class Position {
public:
   Position(int x, int y) : position(gcnew array<int, 2>(100, 100)) {
      this->default[x, y] = 1;
   }

   property int default[int, int] {
      int get(int x, int y) {
         return position[x, y];
      }

      void set(int x, int y, int value) {}
   }

private:
   array<int, 2> ^ position;
};
```

このサンプルでは、を使用し <xref:System.Reflection.DefaultMemberAttribute> て既定のインデクサーを指定する方法を示します。

```cpp
// specify_default_indexer.cpp
// compile with: /LD /clr
using namespace System;
[Reflection::DefaultMember("XXX")]
public ref struct Squares {
   property Double XXX[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
};
```

次のサンプルでは、前の例で作成したメタデータを使用します。

```cpp
// consume_default_indexer.cpp
// compile with: /clr
#using "specify_default_indexer.dll"
int main() {
   Squares ^ square = gcnew Squares();
   System::Console::WriteLine("{0}", square[3]);
}
```

```Output
9
```

## <a name="virtual-properties"></a>仮想プロパティ

このコードサンプルでは、仮想プロパティを宣言して使用する方法を示します。

```cpp
// mcppv2_property_4.cpp
// compile with: /clr
using namespace System;
interface struct IEFace {
public:
   property int VirtualProperty1;
   property int VirtualProperty2 {
      int get();
      void set(int i);
   }
};

// implement virtual events
ref class PropImpl : public IEFace {
   int MyInt;
public:
   virtual property int VirtualProperty1;

   virtual property int VirtualProperty2 {
      int get() {
         return MyInt;
      }
      void set(int i) {
         MyInt = i;
      }
   }
};

int main() {
   PropImpl ^ MyPI = gcnew PropImpl();
   MyPI->VirtualProperty1 = 93;
   Console::WriteLine(MyPI->VirtualProperty1);

   MyPI->VirtualProperty2 = 43;
   Console::WriteLine(MyPI->VirtualProperty2);
}
```

```Output
93
43
```

## <a name="abstract-and-sealed-properties"></a>抽象プロパティと sealed プロパティ

[Abstract](../extensions/abstract-cpp-component-extensions.md)キーワードと[sealed](../extensions/sealed-cpp-component-extensions.md)キーワードは、ECMA C++/cli 仕様の中で有効として指定されていますが、Microsoft C++ コンパイラでは、自明なプロパティや、自明でないプロパティのプロパティ宣言では指定できません。

Sealed プロパティまたは abstract プロパティを宣言するには、単純なプロパティを定義してから **`abstract`** 、 **`sealed`** get および set アクセサー関数でまたはキーワードを指定する必要があります。

```cpp
// properties_abstract_sealed.cpp
// compile with: /clr
ref struct A {
protected:
   int m_i;

public:
   A() { m_i = 87; }

   // define abstract property
   property int Prop_1 {
      virtual int get() abstract;
      virtual void set(int i) abstract;
   }
};

ref struct B : A {
private:
   int m_i;

public:
   B() { m_i = 86; }

   // implement abstract property
   property int Prop_1 {
      virtual int get() override { return m_i; }
      virtual void set(int i) override { m_i = i; }
   }
};

ref struct C {
private:
   int m_i;

public:
   C() { m_i = 87; }

   // define sealed property
   property int Prop_2 {
      virtual int get() sealed { return m_i; }
      virtual void set(int i) sealed { m_i = i; };
   }
};

int main() {
   B b1;
   // call implementation of abstract property
   System::Console::WriteLine(b1.Prop_1);

   C c1;
   // call sealed property
   System::Console::WriteLine(c1.Prop_2);
}
```

```Output
86
87
```

## <a name="multidimensional-properties"></a>多次元プロパティ

多次元プロパティを使用して、標準以外の数のパラメーターを受け取るプロパティアクセサーメソッドを定義できます。

```cpp
// mcppv2_property_5.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(0) {}
   property double MultiDimProp[int, int, int] {
      double get(int, int, int) {
         return d;
      }
      void set(int i, int j, int k, double l) {
         // do something with those ints
         d = l;
      }
   }

   property double MultiDimProp2[int] {
      double get(int) {
         return d;
      }
      void set(int i, double l) {
         // do something with those ints
         d = l;
      }
   }

};

int main() {
   X ^ MyX = gcnew X();
   MyX->MultiDimProp[0,0,0] = 1.1;
   System::Console::WriteLine(MyX->MultiDimProp[0, 0, 0]);
}
```

```Output
1.1
```

## <a name="overloading-property-accessors"></a>プロパティアクセサーのオーバーロード

次の例は、インデックス付きプロパティをオーバーロードする方法を示しています。

```cpp
// mcppv2_property_6.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(0.0) {}
   property double MyProp[int] {
      double get(int i) {
         return d;
      }

      double get(System::String ^ i) {
         return 2*d;
      }

      void set(int i, double l) {
         d = i * l;
      }
   }   // end MyProp definition
};

int main() {
   X ^ MyX = gcnew X();
   MyX->MyProp[2] = 1.7;
   System::Console::WriteLine(MyX->MyProp[1]);
   System::Console::WriteLine(MyX->MyProp["test"]);
}
```

```Output
3.4
6.8
```

## <a name="see-also"></a>関連項目

[property](../extensions/property-cpp-component-extensions.md)
