﻿---
title: ストレージ クラス (C++)
description: C++ では、静的、extern、およびthread_localキーワードは、変数または関数の有効期間、リンケージ、およびメモリの位置を指定します。
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: 75ccb11689b4863d2d0df5edd6d066be6bd3858c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365347"
---
# <a name="storage-classes"></a>ストレージ クラス

C++ 変数宣言のコンテキストで*のストレージ クラス*は、オブジェクトの有効期間、リンケージ、およびメモリの場所を制御する型指定子です。 特定のオブジェクトはストレージ クラスを 1 つのみ持つことができます。 ブロック内で定義された変数は **、extern**、 **static**、 または**thread_local**指定子を使用して指定しない限り、自動ストレージを持っています。 自動オブジェクトおよび変数にはリンケージがないため、ブロックの外側のコードには不可視です。 実行がブロックに入ると、メモリは自動的に割り当てられ、ブロックが終了すると割り当てが解除されます。

**メモ**

1. [mutable](../cpp/mutable-data-members-cpp.md)キーワードは、ストレージ クラス指定子と見なされます。 ただし、クラス定義のメンバー一覧でのみ使用できます。

1. **ビジュアル スタジオ 2010 以降:****auto**キーワードは C++ ストレージ・クラス指定子ではなく **、register**キーワードは非推奨です。 **Visual Studio 2017 バージョン 15.7 以降:** [(/std:c++17](../build/reference/std-specify-language-standard-version.md)で利用可能):**レジスタ**キーワードは C++ 言語から削除されます。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a>静的

**static**キーワードを使用すると、グローバル スコープ、名前空間スコープ、およびクラス スコープで変数と関数を宣言できます。 静的変数は、ローカル スコープでも宣言できます。

静的存続期間は、オブジェクトまたは変数がプログラム起動時に割り当てられ、プログラムの終了時に解放されることを意味します。 外部リンケージは、変数が宣言されたファイルの外部から変数名が参照できることを意味します。 逆に、内部リンケージは、変数が宣言されたファイルの外部でその名前を参照できないことを意味します。 既定では、グローバル名前空間で定義されたオブジェクトまたは変数には静的存続期間と外部リンケージがあります。 **static**キーワードは、次の状況で使用できます。

1. ファイル スコープ (グローバルスコープまたは名前空間スコープ) で変数または関数を宣言する場合 **、static**キーワードは、変数または関数が内部リンケージを持っていることを指定します。 変数を宣言すると、変数は静的存続期間が設定され、コンパイラによって 0 に初期化されます (別の値を指定していない場合)。

1. 関数で変数を宣言する場合 **、static**キーワードは、その関数の呼び出しの間に変数の状態を保持することを指定します。

1. クラス宣言でデータ メンバーを宣言する場合 **、static**キーワードは、メンバーの 1 つのコピーがクラスのすべてのインスタンスで共有されることを指定します。 静的データ メンバーはファイル スコープで定義する必要があります。 **定数静的**として宣言する整数データ メンバーは、初期化子を持つことができます。

1. クラス宣言でメンバー関数を宣言する場合 **、static**キーワードは、その関数がクラスのすべてのインスタンスで共有されることを指定します。 静的メンバー関数は、**暗黙的なこの**ポインターを持たないため、インスタンス メンバーにアクセスできません。 インスタンス メンバーにアクセスするには、インスタンスのポインターまたは参照であるパラメーターを受け取る関数を宣言します。

1. 共用体のメンバーを static として宣言することはできません。 ただし、グローバルに宣言された匿名共用体は、明示的に**static**として宣言する必要があります。

この例では、関数内で**static**と宣言された変数が、その関数の呼び出し間で状態を保持する方法を示します。

```cpp
// static1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void showstat( int curr ) {
   static int nStatic;    // Value of nStatic is retained
                          // between each function call
   nStatic += curr;
   cout << "nStatic is " << nStatic << endl;
}

int main() {
   for ( int i = 0; i < 5; i++ )
      showstat( i );
}
```

```Output
nStatic is 0
nStatic is 1
nStatic is 3
nStatic is 6
nStatic is 10
```

この例では、クラスでの**static**の使用を示します。

```cpp
// static2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CMyClass {
public:
   static int m_i;
};

int CMyClass::m_i = 0;
CMyClass myObject1;
CMyClass myObject2;

int main() {
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject1.m_i = 1;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject2.m_i = 2;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   CMyClass::m_i = 3;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;
}
```

```Output
0
0
1
1
2
2
3
3
```

この例では、メンバー関数で**static**として宣言されたローカル変数を示します。 静的変数は、プログラム全体で使用できます。型のすべてのインスタンスは、静的変数の同じコピーを共有します。

```cpp
// static3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
struct C {
   void Test(int value) {
      static int var = 0;
      if (var == value)
         cout << "var == value" << endl;
      else
         cout << "var != value" << endl;

      var = value;
   }
};

int main() {
   C c1;
   C c2;
   c1.Test(100);
   c2.Test(100);
}
```

```Output
var != value
var == value
```

C++11 以降では、静的ローカル変数の初期化はスレッド セーフであることが保証されています。 この機能は、*マジック・スタティックと*呼ばれることもあります。 ただし、マルチスレッド アプリケーションでは、後続の割り当てはすべて同期する必要があります。 スレッド セーフな静的初期化機能は、CRT への依存関係を回避するために[/Zc:threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)フラグを使用して無効にすることができます。

## <a name="extern"></a><a name="extern"></a>Extern

**extern**として宣言されたオブジェクトと変数は、別の変換単位または外側のスコープで外部リンケージを持つものとして定義されているオブジェクトを宣言します。 詳細については、「 [extern](extern-cpp.md) 」 および[「 変換単位とリンケージ](program-and-linkage-cpp.md)」を参照してください。

## <a name="thread_local-c11"></a><a name="thread_local"></a>thread_local (C++11)

**thread_local**指定子で宣言された変数は、その変数が作成されたスレッドでのみアクセス可能です。 変数は、スレッドが作成されるときに作成され、スレッドが破棄されるときに破棄されます。 各スレッドには、それ自体の変数のコピーがあります。 Windows では **、thread_local**は、Microsoft 固有の[__declspec ( thread ) 属性](../cpp/thread.md)と機能的に同等です。

```cpp
thread_local float f = 42.0; // Global namespace. Not implicitly static.

struct S // cannot be applied to type definition
{
    thread_local int i; // Illegal. The member must be static.
    thread_local static char buf[10]; // OK
};

void DoSomething()
{
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;
}
```

**thread_local**指定子について注意する必要があります。

- DLL 内で動的に初期化されたスレッド ローカル変数は、呼び出し元のスレッドすべてに対して正しく初期化されない場合があります。 詳細については、[スレッド](thread.md) に関するページを参照してください。

- **thread_local**指定子は **、静的**または**extern**と組み合わせることができる。

- **thread_local**は、データ宣言と定義にのみ適用できます。**thread_local**関数宣言または定義では使用できません。

- 静的な保存期間を持つデータ項目に対してのみ**thread_local**を指定できます。 これには、グローバル データ オブジェクト (**静的**および**extern**の両方)、ローカルの静的オブジェクト、およびクラスの静的データ メンバーが含まれます。 thread_local**宣言された**ローカル変数は、他のストレージ クラスが指定されていない場合は暗黙的に静的です。つまり、ブロック スコープ**ではthread_local**と同じ`thread_local static`になります。

- 宣言と定義が同じファイルまたは別々のファイルのどちらで行われるかにかかわらず、スレッド ローカル オブジェクトの宣言と定義の両方に**thread_local**を指定する必要があります。

Windows では **、thread_local**は **、__declspec(thread) を**型定義に適用できる点を除いて、__declspec [(スレッド)](../cpp/thread.md)と機能的に同等であり、C コードで有効です。 可能な場合は必ず **、thread_local**使用します。

## <a name="register"></a><a name="register"></a>登録

**Visual Studio 2017 バージョン 15.3 以降** [(/std:c++17](../build/reference/std-specify-language-standard-version.md)で利用可能):**レジスタ**キーワードはサポートされていないストレージ クラスです。 キーワードは、今後の使用のために標準で予約されています。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>例: 自動初期化と静的初期化

ローカル自動オブジェクトまたは変数が、制御フローが定義に到達するたびに初期化されます。 ローカル静的オブジェクトまたは変数が、最初に制御フローが定義に到達すると初期化されます。

オブジェクトの初期化と破棄をログに記録するクラスを定義し、`I1`、`I2`、および `I3` の 3 つのオブジェクトを定義する、次の例を考えます。

```cpp
// initialization_of_objects.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>
using namespace std;

// Define a class that logs initializations and destructions.
class InitDemo {
public:
    InitDemo( const char *szWhat );
    ~InitDemo();

private:
    char *szObjName;
    size_t sizeofObjName;
};

// Constructor for class InitDemo
InitDemo::InitDemo( const char *szWhat ) :
    szObjName(NULL), sizeofObjName(0) {
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {
        // Allocate storage for szObjName, then copy
        // initializer szWhat into szObjName, using
        // secured CRT functions.
        sizeofObjName = strlen( szWhat ) + 1;

        szObjName = new char[ sizeofObjName ];
        strcpy_s( szObjName, sizeofObjName, szWhat );

        cout << "Initializing: " << szObjName << "\n";
    }
    else {
        szObjName = 0;
    }
}

// Destructor for InitDemo
InitDemo::~InitDemo() {
    if( szObjName != 0 ) {
        cout << "Destroying: " << szObjName << "\n";
        delete szObjName;
    }
}

// Enter main function
int main() {
    InitDemo I1( "Auto I1" ); {
        cout << "In block.\n";
        InitDemo I2( "Auto I2" );
        static InitDemo I3( "Static I3" );
    }
    cout << "Exited block.\n";
}
```

```Output
Initializing: Auto I1
In block.
Initializing: Auto I2
Initializing: Static I3
Destroying: Auto I2
Exited block.
Destroying: Auto I1
Destroying: Static I3
```

この例では、オブジェクト 、、`I1``I2`および`I3`オブジェクトが初期化されるタイミングと、オブジェクトが破棄されるタイミングを示します。

プログラムについて注意すべき点がいくつかあります。

- 最初に、制御フローが `I1` と `I2` を定義しているブロックを終了すると、これらは自動的に破棄されます。

- 次に、C++ では、ブロックの先頭でオブジェクトや変数を宣言する必要はありません。 さらに、これらのオブジェクトは、制御フローが定義に到達した場合にのみ初期化されます  (`I2`および`I3`そのような定義の例です。出力は、初期化された正確なタイミングを示します。

- 最後に、`I3` などの静的ローカル変数は、プログラム実行中は値が保持されますが、プログラムが終了すると破棄されます。

## <a name="see-also"></a>関連項目

[宣言と定義](../cpp/declarations-and-definitions-cpp.md)
