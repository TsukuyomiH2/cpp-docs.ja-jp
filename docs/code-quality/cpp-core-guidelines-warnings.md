---
title: C++コアガイドラインの警告
ms.date: 10/16/2019
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
ms.openlocfilehash: 544c737470a6578e65e82bb3c8cf1824ec93895f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079959"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ Core ガイドライン チェッカーの使用

C++コアガイドラインは、専門家や設計者によってC++ C++作成されたコーディングに関するガイドライン、ルール、およびベストプラクティスの移植可能なセットです。 現在、Visual Studio では、のC++コード分析ツールの一部として、これらのルールのサブセットをサポートしています。 コアガイドラインチェッカーは、visual Studio 2017 および Visual Studio 2019 に既定でインストールされ、 [Visual studio 2015 の NuGet パッケージとして入手でき](#vs2015_corecheck)ます。

## <a name="the-c-core-guidelines-project"></a>C++コアガイドラインプロジェクト

Bjarne Stroustrup によって作成されC++たコアガイドラインは、最新C++の安全かつ効果的に使用するためのガイドです。 このガイドラインでは、静的なタイプセーフとリソースの安全性を重視しています。 これらの例では、言語のエラーが発生しやすい部分を排除または最小化する方法を示し、信頼性の高い方法でコードをより簡単かつ効率的にする方法を提案します。 これらのガイドラインは、Standard C++ Foundation によって管理されています。 詳細については、 [GitHub](https://github.com/isocpp/CppCoreGuidelines)のドキュメントと[ C++コアガイドライン](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)を参照C++し、主要ガイドラインドキュメントプロジェクトファイルにアクセスしてください。

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>コード分析C++のコアチェックガイドラインを有効にする

プロジェクトのコード分析を有効にするには、プロジェクトの **[プロパティページ]** ダイアログの **[コード分析]** セクションで **[ビルド時にコード分析を有効にする]** チェックボックスをオンにします。

![コード分析の全般設定のプロパティページ](../code-quality/media/cppcorecheck_codeanalysis_general.png)

コアC++チェック規則は、コード分析が有効になっているときに実行される既定の規則セットの拡張機能です。 C++コアチェック規則は開発中なので、一部の規則は適切に確立され、一部の規則はすべてのコードで使用する準備ができていなくても、有益な場合があります。 これらのルールは、リリースと試験的の2つのグループに分けられます。 プロジェクトのプロパティで、リリース済みまたは試験的な規則を実行するかどうかを選択できます。

![コード分析拡張機能の設定のプロパティページ](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

C++コアチェック規則セットを有効または無効にするには、プロジェクトの **[プロパティページ]** ダイアログを開きます。 **[構成プロパティ]** で、 **[コード分析]** 、 **[拡張機能]** の順に展開します。 **[コアチェック (リリース) をC++有効]** にする または **[ C++コアチェックを有効にする (試験段階)** ] の横にあるドロップダウンコントロールで、[**はい]** または **[いいえ]** を選択します。 **[OK]** または **[適用]** を選択して、変更を保存します。

## <a name="examples"></a>例

ここでは、 C++主要なチェック規則によって検出される可能性のあるいくつかの問題の例を示します。

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

次の例では、 C++主要なチェックルールで検出できる警告のいくつかを示します。

- C26494 は rule 型です。 5: 常にオブジェクトを初期化します。

- C26485 はルールの境界です。 3: 配列からポインターへの減衰がありません。

- C26481 は rule Bounds です。 1: ポインター演算は使用しないでください。 代わりに `span` を使用してください

このコードC++をコンパイルするときに、コアチェックのコード分析のルールセットがインストールされ、有効になっている場合、最初の2つの警告が出力されますが、3番目の警告は抑制されます。 コード例のビルド出力を次に示します。

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

コードC++をより適切に記述するための主要ガイドラインがあります。 ただし、ルールまたはプロファイルを適用できないインスタンスがある場合は、コード内で直接非表示にするのが簡単です。 `gsl::suppress` 属性を使用して、次C++のコードブロックの規則違反を検出および報告するようにコアチェックを維持することができます。 個々のステートメントをマークして、特定のルールを抑制することができます。 特定のルール番号を含めずに `[[gsl::suppress(bounds)]]` を記述して、境界プロファイル全体を抑制することもできます。

## <a name="supported-rule-sets"></a>サポートされている規則セット

新しいルールがC++コアガイドラインチェッカーに追加されると、既存のコードに対して生成される警告の数が増加する可能性があります。 定義済みの規則セットを使用して、有効にする規則の種類をフィルター処理できます。 Visual Studio 2017 バージョン15.3 の場合、サポートされている規則セットは次のとおりです。

- **所有者ポインターの規則**[は、 C++コアガイドラインから > 所有者\<t に関連するリソース管理のチェックを](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)適用します。

- **定数規則**[は、主要なガイドラインにC++よる const 関連のチェックを](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)適用します。

- **生のポインター規則** [ C++は、主要なガイドラインからの生のポインターに関連するリソース管理のチェックを](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)適用します。

- **一意のポインターの規則**[はC++ 、コアガイドラインから一意のポインターセマンティクスを持つ型に関連するリソース管理チェックを](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)適用します。

- **境界ルール**で[は、 C++コアガイドラインの境界プロファイル](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)が適用されます。

- **型ルール**で[は、 C++コアガイドラインのタイププロファイル](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)が適用されます。

警告を1つまたは複数のグループに制限することを選択できます。 **ネイティブの最小**および**ネイティブで推奨**されるC++規則セットには、他の PREfast チェックに加えて、コアチェック規則が含まれています。 使用可能な規則セットを表示するには、プロジェクトのプロパティ ダイアログボックスを開き、**コード分析** を選択し、**規則セット** コンボボックスでドロップダウンを開き、 **複数の規則セットを選択**します を選択します。 Visual Studio での規則セットの使用方法の詳細については、「[規則C++セットを使用して実行する規則を指定する](using-rule-sets-to-specify-the-cpp-rules-to-run.md)」および「[規則セットを使用したコード分析規則のグループ化](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules)」を参照してください。

## <a name="macros"></a>マクロ

コアC++ガイドラインチェッカーには、コード内の警告のカテゴリ全体を簡単に抑制できるようにするマクロを定義するヘッダーファイルが付属しています。

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

これらのマクロは、ルールセットに対応し、警告番号のスペース区切りの一覧に展開されます。 適切なプラグマコンストラクトを使用すると、プロジェクトまたはコードのセクションにとって興味深いルールの有効なセットを構成できます。 次の例では、不足している定数修飾子についてのみ、コード分析によって警告が表示されます。

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>属性

Microsoft C++コンパイラでは、gsl 抑制属性のサポートが制限されています。 関数内の expression ステートメントおよび block ステートメントの警告を抑制するために使用できます。

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>コマンドラインオプションを使用した分析の抑制

#Pragmas の代わりに、ファイルの [プロパティ] ページのコマンドラインオプションを使用して、プロジェクトまたは1つのファイルの警告を非表示にすることができます。 たとえば、ファイルの警告 C26400 を無効にするには、次のようにします。

1. でファイルを右クリックし**ソリューションエクスプローラー**

1. [プロパティ] を選択します。 **C/C++|コマンドライン**

1. **[追加オプション]** ウィンドウで、`/wd26400`を追加します。

[コマンドライン] オプションを使用すると、`/analyze-`を指定することによって、ファイルのすべてのコード分析を一時的に無効にすることができます。 これにより、' */analyze ' を '/analyze e-' でオーバーライド*する警告 D9025 が生成されます。これにより、後でコード分析を再度有効にするように通知されます。

## <a name="enabling-the-c-core-guidelines-checker-on-specific-project-files"></a><a name="corecheck_per_file"></a>特定のC++プロジェクトファイルに対する主要なガイドラインチェッカーの有効化

場合によっては、フォーカスのあるコード分析を行っても、Visual Studio IDE を活用すると役立つことがあります。 次に示すのは、大規模なプロジェクトでビルド時間を節約し、結果をフィルター処理しやすくするために使用できるサンプルシナリオです。

1. コマンドシェルで、`esp.extension` と `esp.annotationbuildlevel` 環境変数を設定します。
1. コマンドシェルから Visual Studio を開き、これらの変数を継承します。
1. プロジェクトを読み込み、そのプロパティを開きます。
1. コード分析を有効にし、適切な規則セットを選択します。ただし、コード分析の拡張機能は有効にしません。
1. C++コアガイドラインチェッカーを使用して分析するファイルにアクセスし、そのプロパティを開きます。
1. **[C/C++\ コマンドラインオプション]** を選択し、`/analyze:plugin EspXEngine.dll` を追加します。
1. プリコンパイル済みヘッダーの使用を無効にします (**C//C++プリコンパイル済みヘッダー**)。 これは、拡張エンジンがプリコンパイル済みヘッダーから内部情報を読み取ることができ、後者が既定のプロジェクトオプションを使用してコンパイルされた場合、互換性がないために必要です。
1. プロジェクトをリビルドします。 共通の PREFast チェックはすべてのファイルで実行する必要があります。 C++コアガイドラインチェッカーは既定では有効になっていないため、これを使用するように構成されているファイルでのみ実行する必要があります。

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Visual Studio の外部C++での主要なガイドラインチェッカーの使用方法

自動ビルドのC++主要なガイドラインチェックを使用できます。

### <a name="msbuild"></a>MSBuild

ネイティブコード分析チェッカー (PREfast) は、カスタムターゲットファイルによって MSBuild 環境に統合されています。 プロジェクトのプロパティを使用して有効にし、 C++コアガイドラインチェッカー (PREfast に基づく) を追加することができます。

```xml
<PropertyGroup>
  <EnableCppCoreCheck>true</EnableCppCoreCheck>
  <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>
  <RunCodeAnalysis>true</RunCodeAnalysis>
</PropertyGroup>
```

これらのプロパティは、必ず、Microsoft .Cpp. .targets ファイルをインポートする前に追加してください。 特定の規則セットを選択するか、カスタム規則セットを作成するか、他の PREfast チェックを含む既定の規則セットを使用することができます。

コアチェッカーはC++ 、[前述](#corecheck_per_file)の方法と同じ方法を使用して、指定したファイルに対してのみ実行できますが、MSBuild ファイルを使用します。 環境変数は、`BuildMacro` 項目を使用して設定できます。

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

プロジェクトファイルを変更しない場合は、コマンドラインで次のようにプロパティを渡すことができます。

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>MSBuild 以外のプロジェクト

MSBuild に依存しないビルドシステムを使用する場合でも、引き続きチェッカーを実行できますが、コード分析エンジンの構成の一部について理解しておく必要があります (これは今後サポートされるとは限りません)。

いくつかの環境変数を設定し、コンパイラに適切なコマンドラインオプションを使用する必要があります。 "ネイティブツールコマンドプロンプト" 環境で作業することをお勧めします。これにより、コンパイラの特定のパス、インクルードディレクトリなどを検索する必要がなくなります。

1. **環境変数**
   - `set esp.extensions=cppcorecheck.dll`、 C++コアガイドラインモジュールを読み込むようにエンジンに指示します。
   - `set esp.annotationbuildlevel=ignore` すると、SAL 注釈を処理するロジックが無効になります。 注釈は、 C++コアガイドラインチェッカーのコード分析には影響しませんが、処理には時間がかかります (時間がかかることがあります)。 この設定は省略可能ですが、強くお勧めします。
   - `set caexcludepath=%include%` 標準ヘッダーで起動する警告を無効にすることを強くお勧めします。 ここでは、プロジェクトの共通ヘッダーへのパスなど、さらにパスを追加できます。
1. **コマンドラインオプション**
   - `/analyze` により、コード分析が可能になります (/analyze: only と/analyze: quiet も使用することを検討してください)。
   - このオプション `/analyze:plugin EspXEngine.dll`、PREfast にコード分析拡張エンジンを読み込みます。 次に、このエンジンはC++コアガイドラインチェッカーを読み込みます。

## <a name="use-the-guideline-support-library"></a>ガイドラインサポートライブラリを使用する

ガイドラインサポートライブラリは、主要なガイドラインに従うことができるように設計されています。 GSL には、エラーが発生しやすい構造を代替として置き換えることができる定義が含まれています。 たとえば、`T*, length` のパラメーターのペアを `span<T>` 型に置き換えることができます。 GSL は[https://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl)で入手できます。 ライブラリはオープンソースであるため、ソースの表示、コメントの作成、または投稿を行うことができます。 プロジェクトは[https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)にあります。

## <a name="use-the-c-core-check-guidelines-in-visual-studio-2015-projects"></a><a name="vs2015_corecheck"></a>Visual Studio C++ 2015 プロジェクトのコアチェックガイドラインを使用する

Visual Studio 2015 を使用する場合、 C++コアチェックのコード分析規則セットは既定ではインストールされません。 Visual Studio 2015 のコアチェックコード分析ツールを有効C++にするには、いくつかの追加の手順を実行する必要があります。 Microsoft では、Nuget パッケージを使用して Visual Studio 2015 プロジェクトのサポートを提供しています。 パッケージは CppCoreCheck という名前で、 [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck)で入手できます。 このパッケージには、少なくとも Visual Studio 2015 with Update 1 がインストールされている必要があります。

また、パッケージは、ヘッダーのみのガイドラインサポートライブラリ (GSL) である依存関係として別のパッケージをインストールします。 GSL は、 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)で GitHub から入手することもできます。

コード分析規則の読み込み方法によっては、Visual Studio 2015 内で確認する各C++プロジェクトに CppCoreCheck NuGet パッケージをインストールする必要があります。

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Visual Studio 2015 でプロジェクトに CppCoreCheck パッケージを追加するには

1. **ソリューションエクスプローラー**で、右クリックして、パッケージを追加するソリューション内のプロジェクトのコンテキストメニューを開きます。 [ **Nuget**パッケージの管理] を選択して、 **nuget パッケージマネージャー**を開きます。

1. **[NuGet パッケージマネージャー]** ウィンドウで、CppCoreCheck を検索します。

    ![Nuget パッケージマネージャーウィンドウに CppCoreCheck パッケージが表示されます](../code-quality/media/cppcorecheck_nuget_window.png)

1. CppCoreCheck パッケージを選択し、 **[インストール]** をクリックして、プロジェクトに規則を追加します。

   NuGet パッケージは、プロジェクトに対してコード分析を有効にしたときに呼び出される追加の MSBuild. .targets ファイルをプロジェクトに追加します。 この .targets ファイルは、Visual C++ Studio コード分析ツールに追加の拡張機能としてコアチェック規則を追加します。 パッケージがインストールされている場合は、[プロパティページ] ダイアログボックスを使用して、リリースおよび試験的な規則を有効または無効にすることができます。
