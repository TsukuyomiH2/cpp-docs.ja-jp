---
title: /EH (例外処理モデル)
description: Visual Studio の Microsoft C++/EH (例外処理モデル) コンパイラオプションのリファレンスガイドです。
ms.date: 08/25/2020
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
no-loc:
- SEH
- try
- catch
- throw
- extern
- finally
- noexcept
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 0d18d0f1d73b1de46b12262deecb2436c34e6176
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898379"
---
# <a name="eh-exception-handling-model"></a>`/EH` (例外処理モデル)

コンパイラによって生成される例外処理モデルのサポートを指定します。 引数 `catch(...)` は、構文を構造化例外と標準 C++ 例外の両方に適用するかどうか、 ** extern "C"** コードが例外と想定されるかどうか、 throw および特定のチェックを最適化するかどうかを指定し **`noexcept`** ます。

## <a name="syntax"></a>構文

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>引数

**`a`**\
標準 C++ スタックアンワインドを有効にします。 構文を使用するときに、構造化された (非同期) 例外と標準 C++ (同期) 例外の両方をキャッチし `catch(...)` ます。 **`/EHa`****`/EHs`** 引数と引数の両方をオーバーライドし **`/EHc`** ます。

**`s`**\
標準 C++ スタックアンワインドを有効にします。 構文を使用する場合は、標準 C++ 例外のみをキャッチ `catch(...)` します。 が指定されていない場合 **`/EHc`** 、コンパイラは、 ** extern "C"** として宣言された関数が throw C++ 例外であると見なします。

**`c`**\
と共に使用する場合 **`/EHs`** 、コンパイラは、 ** extern "c"** として宣言された関数が C++ 例外ではないと見なし throw ます。 と共に使用しても効果はありません **`/EHa`** (つまり、 **`/EHca`** はと同等です **`/EHa`** )。 **`/EHc`****`/EHs`** またはが指定されていない場合、は無視され **`/EHa`** ます。

**`r`**\
すべての関数のランタイム終了チェックを常に生成するようにコンパイラに指示し **`noexcept`** ます。 既定では、 **`noexcept`** コンパイラによって関数が ing 以外の関数のみを呼び出すと判断した場合、のランタイムチェックが最適化されます throw 。 このオプションは、いくつかの追加コードのコストで、厳密な C++ 準拠を提供します。 **`/EHr`****`/EHs`** またはが指定されていない場合、は無視され **`/EHa`** ます。

**`-`**\
前のオプションの引数をクリアします。 たとえば、 **`/EHsc-`** はとして解釈され、 **`/EHs /EHc-`** はに相当し **`/EHs`** ます。

**`/EH`** 引数は、個別に指定することも、組み合わせて任意の順序で指定することもできます。 同じ引数の複数のインスタンスが指定されている場合、最後のインスタンスは以前の1つをオーバーライドします。  たとえば、はと同じであり、と **`/EHr- /EHc /EHs`** **`/EHscr-`** **`/EHscr- /EHr`** 同じ効果があり **`/EHscr`** ます。

## <a name="remarks"></a>注釈

### <a name="default-exception-handling-behavior"></a>既定の例外処理動作

コンパイラは、非同期構造化例外処理 () をサポートするコードを常に生成し SEH ます。 既定では (つまり、、、 **`/EHsc`** またはオプションが指定されていない場合 **`/EHs`** )、 **`/EHa`** コンパイラは SEH ネイティブ C++ 句のハンドラーをサポートし `catch(...)` ます。 ただし、C++ 例外のみを部分的にサポートするコードも生成します。 既定の例外アンワインドコードは、 [`try`](../../cpp/try-throw-and-catch-statements-cpp.md) 例外が原因でスコープ外に出る自動 C++ オブジェクトを破棄しません。 C++ の例外が n の場合、リソースリークと未定義の動作が発生する可能性があり throw ます。

### <a name="standard-c-exception-handling"></a>標準 C++ 例外処理

スタックオブジェクトを安全にアンワインドする標準 C++ 例外処理モデルの完全なコンパイラサポートに **`/EHsc`** は、(推奨)、 **`/EHs`** 、またはが必要です **`/EHa`** 。

またはを使用する場合、 **`/EHs`** **`/EHsc`** 句では `catch(...)` 非同期構造化例外が使用されません catch 。 アクセス違反とマネージ例外はすべて <xref:System.Exception?displayProperty=fullName> キャッチされません。 また、非同期例外が発生した場合、スコープ内のオブジェクトは破棄されません。これは、コードが非同期例外を処理する場合でも同様です。 この動作は、構造化例外が未処理のままになるための引数です。 代わりに、これらの例外を致命的に考慮してください。

またはを使用する場合、 **`/EHs`** **`/EHsc`** コンパイラは、例外が **`throw`** ステートメントまたは関数呼び出しでのみ発生することを前提としています。 この想定により、コンパイラは、多くの unwindable オブジェクトの有効期間を追跡するコードを排除できます。これにより、コードのサイズを大幅に削減できます。 を使用すると **`/EHa`** 、コンパイラがブロックを積極的に最適化しないため、実行可能イメージのサイズと速度が低下する可能性があり **`try`** ます。 また、C++ 例外が発生する可能性のあるコードがコンパイラに表示されない場合でも、ローカルオブジェクトを自動的にクリーンアップする例外フィルターが残さ throw れます。

### <a name="structured-and-standard-c-exception-handling"></a>構造化および標準 C++ 例外処理

**`/EHa`** コンパイラオプションを使用すると、非同期例外と C++ 例外の両方に対して安全なスタックアンワインドが有効になります。 これは、ネイティブ C++ 句を使用して、標準 C++ と構造化例外の両方の処理をサポートし `catch(...)` ます。 を指定せずにを実装する場合は SEH **`/EHa`** 、、、およびの各構文を使用でき **`__try`** **`__except`** **`__finally`** ます。 詳細については、「 [構造化例外処理](../../cpp/structured-exception-handling-c-cpp.md)」を参照してください。

> [!IMPORTANT]
> を **`/EHa`** 使用してすべての例外を処理するとを指定すると、 try `catch(...)` 危険になる可能性があります。 非同期例外のほとんどが回復不能で、致命的であると見なされます。 こうした例外をキャッチして操作を続行すると、プロセスが破損し、検出して修正するのが難しいバグが発生する可能性があります。
>
> Windows と Visual C++ がサポートされている場合でも SEH 、ISO 標準の C++ 例外処理 (または) を使用することを強くお勧め **`/EHsc`** **`/EHs`** します。 これにより、コードの移植性と柔軟性が向上します。 SEH従来のコードまたは特定の種類のプログラムで使用する必要がある場合もあります。 たとえば、共通言語ランタイム () をサポートするためにコンパイルされたコードで必要に [`/clr`](clr-common-language-runtime-compilation.md) なります。 詳細については、「 [構造化例外処理](../../cpp/structured-exception-handling-c-cpp.md)」を参照してください。
>
> を使用してコンパイルされたオブジェクトファイル **`/EHa`** を、 **`/EHs`** 同じ実行可能モジュールでまたはを使用してコンパイルしたオブジェクトファイルにリンクしないことをお勧め **`/EHsc`** します。 モジュール内の任意の場所でを使用して非同期例外を処理する必要がある場合は **`/EHa`** 、を使用して **`/EHa`** モジュール内のすべてのコードをコンパイルします。 構造化例外処理構文は、を使用してコンパイルされたコードと同じモジュールで使用でき **`/EHs`** ます。 ただし、 SEH **`try`** **`throw`** **`catch`** 同じ関数内で、C++、、およびの構文を混在させることはできません。

**`/EHa`** catch 以外のものによって発生する例外を使用する場合は、を使用し **`throw`** ます。 この例で catch は、構造化例外が生成されます。

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to catch it using catch(...)
    try
    {
        int i = 0, j = 1;
        j /= i;   // This will throw a SE (divide by zero).
        printf("%d", j);
    }
    catch(...)
    {
        // catch block will only be executed under /EHa
        cout << "Caught an exception in catch(...)." << endl;
    }
}

int main()
{
    __try
    {
        fail();
    }

    // __except will only catch an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the catch(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>/Clr での例外処理

**`/clr`** オプションは、 **`/EHa`** (つまり、冗長) を意味し **`/clr /EHa`** ます。 **`/EHs`** または **`/EHsc`** がの後で使用された場合、コンパイラはエラーを生成し **`/clr`** ます。 最適化は、この動作に影響しません。 例外がキャッチされると、コンパイラは、例外と同じスコープ内にあるオブジェクトのクラスデストラクターを呼び出します。 例外がキャッチされない場合、これらのデストラクターは実行されません。

の例外処理の制限事項について **`/clr`** は、「 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)」を参照してください。

### <a name="runtime-exception-checks"></a>ランタイム例外チェック

オプションは、 **`/EHr`** 属性を持つすべての関数のランタイム終了チェックを強制的に実行し **`noexcept`** ます。 既定では、コンパイラのバックエンドによって、関数が * throw ing 以外* の関数のみを呼び出すと判断した場合、ランタイムチェックが最適化されることがあります。 Ing 以外の throw 関数とは、例外を指定しない属性を持つ関数のことです throw 。 これらの関数に **`noexcept`** は、、、 `throw()` `__declspec(nothrow)` 、およびが指定されている場合の関数が含ま **`/EHc`** れ **`extern "C"`** ます。 Ing 以外の関数には、 throw コンパイラが throw 検査によって非 ing であると判断したものも含まれます。 既定の動作は、を使用して明示的に設定でき **`/EHr-`** ます。

Ing 属性以外は、 throw 例外が throw 関数によって n にならないことを保証するものではありません。 関数の動作とは異なり、 **`noexcept`** MSVC コンパイラは throw 、、、またはを使用して宣言された関数によって例外 n を `throw()` `__declspec(nothrow)` 未定義の **`extern "C"`** 動作と見なします。 これら3つの宣言属性を使用する関数は、例外のランタイム終了チェックを強制しません。 オプションを使用すると、 **`/EHr`** 関数をエスケープする未処理の例外のランタイムチェックを生成するようにコンパイラに強制することで、この未定義の動作を識別でき **`noexcept`** ます。

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Visual Studio またはプログラムでオプションを設定する

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ**] [  >  **C/c + +**  >  **コード生成**] を選択します。

1. **[C++ の例外を有効にする]** プロパティを変更します。

   または、 **[C++ の例外を有効にする]** を **[いいえ]** に設定してから **[コマンド ライン]** プロパティ ページをクリックし、 **[追加のオプション]** ボックスにコンパイラ オプションを追加します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)\
[エラーと例外処理](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[例外の指定 ( throw )](../../cpp/exception-specifications-throw-cpp.md)\
[構造化例外処理 (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
