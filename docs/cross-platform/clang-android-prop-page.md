---
title: Clang のプロジェクトのプロパティ (Android C++)
ms.date: 10/23/2017
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- VC.Project.VCClangCompilerTool.AdditionalOptionsPage
ms.openlocfilehash: 11e8a7f1ea264b26b9092d4834525541e098a5e1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2020
ms.locfileid: "79470227"
---
# <a name="clang-project-properties-android-c"></a>Clang のプロジェクトのプロパティ (Android C++)

| プロパティ | 説明 | 選択 |
|--|--|--|
| 追加のインクルード ディレクトリ | インクルード パスに追加するディレクトリを 1 つ以上指定します。複数指定する場合には、セミコロンで区切ってください。 (-I*path*)。 |
| デバッグ情報の形式 | コンパイラによって生成されるデバッグ情報の種類を指定します。 | **なし** - デバッグ情報が生成されないため、コンパイルが高速になる可能性があります。<br>**完全なデバッグ情報 (DWARF2)** - DWARF2 デバッグ情報を生成します。<br>**行番号情報** - 行番号の情報のみを生成します。<br> |
| オブジェクト ファイル名 | 既定のオブジェクト ファイル名をオーバーライドする名前を指定します。ファイル名またはディレクトリ名を指定できます。 (/Fo*name*)。 |
| [警告レベル] | コード エラーに対するコンパイラの警告レベルを指定します。  その他のフラグは追加オプションに直接追加してください。 (/w、/Weverything)。 | **すべての警告を非表示にする** - すべてのコンパイラ警告を無効にします。<br>**Enableallwarnings** -既定で無効になっているすべての警告を含む、すべての警告を有効にします。<br> |
| 警告をエラーとして処理 | コンパイラ警告をすべてエラーとして扱います。 新しいプロジェクトの場合、すべてのコンパイルで /WX を使用することをお勧めします。すべての警告を解決することで、コードの欠陥を見逃す可能性が低くなります。 |
| 詳細モードを有効にする | 実行するコマンドを表示して、詳細出力を使用します。 |
| Optimization | アプリケーションの最適化レベルを指定します。 | **カスタム** - カスタムの最適化。<br>**無効** - 最適化を無効にします。<br>**サイズの最小化** - サイズを最適化します。<br>**実行速度の最大化** - 速度を最適化します。<br>**最大限の最適化** - 高価な最適化。<br> |
| 厳密なエイリアス | 厳密なエイリアスのルールを想定します。  1つの型のオブジェクトは、異なる型オブジェクトと同じアドレスにあるとは見なされません。 |
| フレーム ポインターを省略する | 呼び出し履歴にフレーム ポインターが作成されなくなります。 |
| C++ の例外を有効にする | コンパイラで使用する例外処理のモデルを指定します。 | **いいえ** - 例外処理を無効にします。<br>**はい** - 例外処理を有効にします。<br>**アンワインドテーブル**-必要な静的データが生成されますが、生成されるコードには影響しません。<br> |
| 関数レベルでリンクする | コンパイラが個々の関数をパッケージ関数 (COMDAT) の形式でパッケージ化できるようになります。 エディット コンティニュの機能に必要です。     (ffunction セクション)。 |
| データ レベルのリンクを有効にします。 | データ項目ごとにセクションを別にすることで、未使用データを削除するリンカー最適化を有効にします。 |
| 高度な SIMD (Neon) を有効にします。 | NEON の浮動小数点演算ハードウェアのコード生成を有効にします。 ARM アーキテクチャにのみ適用されます。 |
| ABI の浮動小数点 | ABI の浮動小数点を選ぶ選択肢。 | **Soft** - "Soft" は、浮動小数点演算のライブラリ呼び出しを含む出力をコンパイラに生成させます。<br>**SoftFP** - "SoftFP" では、ハードウェアの浮動小数点命令を使用したコード生成が可能になりますが、soft-float 呼び出し規約が使用されます。<br>**Hard** - "Hard" では、浮動小数点命令の生成が可能になり、FPU 固有の呼び出し規約が使用されます。<br> |
| セキュリティ チェック | セキュリティ チェックでは、プログラムのセキュリティに対する一般的な攻撃であるスタックバッファー オーバーランを検出できます。 (fstack プロテクター)。 | **セキュリティ チェックを無効にします** - セキュリティ チェックを無効にします。<br>**セキュリティ チェックを有効にします** - セキュリティ チェックを有効にします。 (fstack プロテクター)<br> |
| 位置独立コード | 共有ライブラリで使用する位置独立コード (PIC) を生成します。 |
| 簡単な列挙型を使用します | 列挙型は、入力された使用できる値に必要なバイト数と同じバイト数を使用します。 |
| ランタイム型情報を有効にする | 実行時に C++ のオブジェクト型をチェックするコードを追加します (ランタイム型情報)。     (frtti、fno-rtti) |
| C 言語標準 | C 言語標準を決定します。 | **[Default]**<br>**C89** - C89 言語標準。<br>**C99** - C99 言語標準。<br>**C11** - C11 言語標準。<br>**C99 (GNU 言語)** - C99 (GNU 言語) 言語標準。<br>**C11 (GNU 言語)** - C11 (GNU 言語) 言語標準。<br> |
| C++ 言語標準 | C++ 言語標準を決定します。 | **[Default]**<br>**C++03** - C++03 言語標準。<br>**C++11** - C++11 言語標準。<br>**C++14** - C++14 言語標準。<br>**C++03 (GNU 言語)** - C++03 (GNU 言語) 言語標準。<br>**C++11 (GNU 言語)** - C++11 (GNU 言語) 言語標準。<br>**C++14 (GNU 言語)** - C++14 (GNU 言語) 言語標準。<br> |
| プリプロセッサの定義 | ソース ファイルの前処理シンボルを定義します。 (-D) |
| 指定したプリプロセッサ定義の無効化 | プリプロセッサに対して1つ以上の未定義を指定します。  (-U*マクロ*) |
| すべてのプリプロセッサ定義の無効化 | すべてのプリプロセッサの定義済み定義を無効にします。  (-undef) |
| インクルード ファイルの表示 | コンパイラ出力を持つインクルード ファイルのリストを生成します。  (-H) |
| プリコンパイル済みヘッダー オプション | プリコンパイル済みヘッダーの作成/使用: ビルド時にプリコンパイル済みヘッダーの作成または使用を有効にします。 | **使用** - プリコンパイル済みヘッダーを使用します。<br>**プリコンパイル済みヘッダーを使用しない** - プリコンパイル済みヘッダーを使用しません。<br> |
| プリコンパイル済みヘッダー ファイル | プリコンパイル済みヘッダー ファイルに使用するヘッダー ファイル名を指定します。 このファイルは、ビルド時に ' 強制インクルードファイル ' にも追加されます。 |
| プリコンパイル済みヘッダーの出力ファイルディレクトリ | 生成されたプリコンパイル済みヘッダー用のディレクトリを指定します。 このディレクトリは、ビルド中に ' 追加のインクルードディレクトリ ' にも追加されます。 |
| プリコンパイル済みヘッダーのコンパイル言語の選択 | プリコンパイル済みヘッダー ファイルのコンパイル言語オプションを選択します (-x c-header、-x c++-header)。 | **C コードとしてコンパイル** - C コードとしてコンパイルします。<br>**C++ コードとしてコンパイル** - C++ コードとしてコンパイルします。<br> |
| コンパイル言語の選択 | *`.c`* および *`.cpp`* ファイルの [コンパイル言語] オプションを選択します。  ' Default ' は *`.c`* または *`.cpp`* の拡張機能に基づいて検出されます。 (-x c、-x c++) | **既定** - 既定。<br>**C コードとしてコンパイル** - C コードとしてコンパイルします。<br>**C++ コードとしてコンパイル** - C++ コードとしてコンパイルします。<br> |
| 必ず使用されるインクルード ファイル | 1 つ以上の必ず使用されるインクルード ファイル。     (-include*名*) |
| 複数プロセッサによるコンパイル | 複数プロセッサによるコンパイルです。 |
| 追加オプション | その他のオプションです。 |
