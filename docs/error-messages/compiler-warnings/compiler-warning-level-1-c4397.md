---
title: コンパイラの警告 (レベル 1) C4397
ms.date: 11/04/2016
f1_keywords:
- C4397
helpviewer_keywords:
- C4397
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
ms.openlocfilehash: e9fb7527124d1838c1f900144f1fea943616f384
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162674"
---
# <a name="compiler-warning-level-1-c4397"></a>コンパイラの警告 (レベル 1) C4397

DefaultCharSetAttribute は無視されます

<xref:System.Runtime.InteropServices.DefaultCharSetAttribute> は、Microsoft C++コンパイラでは無視されます。 DLL の文字セットを指定するには、DllImport の CharSet オプションを使用します。 詳細については、「 [Interop (暗黙のC++ PInvoke) の使用](../../dotnet/using-cpp-interop-implicit-pinvoke.md)」を参照してください。

## <a name="example"></a>例

次の例では、C4397 が生成されます。

```cpp
// C4397.cpp
// compile with: /W1 /c /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[module:DefaultCharSetAttribute(CharSet::Unicode)];   // C4397

[DllImport("kernel32", EntryPoint="CloseHandle", CharSet=CharSet::Unicode)]   // OK
extern "C" bool ImportDefault(IntPtr hObject);

public ref class MySettingVC {
public:
   void method() {
      ImportDefault(IntPtr::Zero);
   }
};

[StructLayout(LayoutKind::Explicit)]
public ref struct StructDefault1{};

public ref class ClassDefault1{};
```
