---
description: '詳細情報: リンク'
title: MSVC リンカーのリファレンス
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: aa4ff82f19ba47fb0fdb9b5c28fe41f9fda1adbe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190940"
---
# <a name="linking"></a>リンク

C++ プロジェクトでは、コンパイラがソースコードをオブジェクトファイル (* .obj) にコンパイルした後に、 *リンク* 手順が実行されます。 リンカー (link.exe) は、オブジェクトファイルを1つの実行可能ファイルに結合します。

リンカーオプションは、Visual Studio の内部または外部で設定できます。 Visual Studio では、 **ソリューションエクスプローラー** のプロジェクトノードを右クリックし、[ **プロパティ** ] を選択してプロパティページを表示することで、リンカーオプションにアクセスします。 左側のウィンドウで [ **リンカー** ] を選択してノードを展開すると、すべてのオプションが表示されます。

## <a name="linker-command-line-syntax"></a>リンカーコマンドライン構文

Visual Studio の外部でリンクを実行する場合、1つまたは複数の方法で入力を指定できます。

- コマンド ライン

- コマンドファイルの使用

- 環境変数

Link 環境変数で指定されている最初のプロセスオプションと、コマンドラインおよびコマンドファイルで指定されている順序でのオプションが含まれます。 オプションが異なる引数で繰り返される場合は、最後に処理されたものが優先されます。

オプションは、ビルド全体に適用されます。特定の入力ファイルにオプションを適用することはできません。

LINK.EXE を実行するには、次のコマンド構文を使用します。

```
LINK arguments
```

`arguments`Include オプションとファイル名を任意の順序で指定できます。 最初にオプションが処理され、次にファイルが処理されます。 1つ以上のスペースまたはタブを使用して、引数を区切ります。

> [!NOTE]
> このツールは、Visual Studio コマンドプロンプトからのみ開始できます。 システム コマンド プロンプトやエクスプローラーからは開始できません。

## <a name="command-line"></a>コマンド ライン

コマンドラインでは、オプション指定子、ダッシュ (-) またはスラッシュ (/)、およびオプションの名前のいずれかで構成されます。 オプション名の省略形は使用できません。 一部のオプションは、コロン (:) の後に指定された引数を受け取ります。 /COMMENT オプションの引用符で囲まれた文字列の中を除き、オプションの指定内でスペースやタブを使用することはできません。 Decimal または C 言語表記で数値引数を指定します。 オプション名とそのキーワードまたはファイル名引数は大文字と小文字が区別されませんが、引数としての識別子は大文字と小文字が区別されます

リンカーにファイルを渡すには、コマンドラインで LINK コマンドの後にファイル名を指定します。 ファイル名には、絶対パスまたは相対パスを指定できます。また、ファイル名にはワイルドカードを使用できます。 ドット (.) とファイル名拡張子を省略した場合、LINK ではファイルを検索するために .obj が使用されます。 リンクはファイル名の拡張子を使用せず、ファイルの内容について推測するためにそれらのファイルが不足しています。ファイルの種類を確認し、それに応じて処理します。

成功した場合、link.exe は0を返します (エラーは発生しません)。  それ以外の場合、リンカーはリンクを停止したエラー番号を返します。  たとえば、リンカーで LNK1104 が生成された場合、リンカーは1104を返します。  これにより、リンカーによってエラーで返されるエラー番号の最小値は1000です。  戻り値128は、オペレーティングシステムまたは .config ファイルの構成の問題を表します。ローダーで link.exe または c2.dll が読み込まれませんでした。

## <a name="link-command-files"></a>LINK コマンド ファイル

コマンドファイルの形式でリンクするコマンドライン引数を渡すことができます。 コマンドファイルをリンカーに指定するには、次の構文を使用します。

> **リンク \@**<em>使い方</em>

*使い方* は、テキストファイルの名前です。 アットマーク ( **\@** ) とファイル名の間にスペースやタブを使用することはできません。 既定の拡張機能はありません。拡張子を含め、完全なファイル名を指定する必要があります。 ワイルドカードは使用できません。 ファイル名を使用して絶対パスまたは相対パスを指定できます。 リンクでは、ファイルの検索に環境変数は使用されません。

コマンドファイルでは、引数はスペースまたはタブで区切ることができます (コマンドラインの場合)。また、改行文字を使用することもできます。

コマンドラインのすべてまたは一部をコマンドファイルで指定できます。 LINK コマンドでは、複数のコマンドファイルを使用できます。 リンクはコマンドファイル入力をコマンドラインで指定されているかのように受け入れます。 コマンドファイルを入れ子にすることはできません。 [/Nologo](nologo-suppress-startup-banner-linker.md)オプションが指定されていない限り、LINK はコマンドファイルの内容をエコーします。

## <a name="example"></a>例

DLL をビルドする次のコマンドでは、オブジェクトファイルとライブラリの名前を個別のコマンドファイルに渡し、3番目のコマンドファイルを使用して、/エクスポートオプションを指定します。

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>環境変数 LINK

LINK ツールでは、次の環境変数を使用します。

- リンクおよび \_ リンク \_ (定義されている場合)。 リンクツールは、リンク環境変数で定義されているオプションと引数を前に付加し、リンク環境変数で定義されているオプションと引数 \_ \_ を、処理前のコマンドライン引数に追加します。

- LIB。定義されている場合。 リンクツールは、コマンドラインまたは [/base](base-base-address.md) オプションで指定されたオブジェクト、ライブラリ、またはその他のファイルを検索するときに、LIB パスを使用します。 また、オブジェクトで指定された .pdb ファイルを検索するときにも LIB パスを使用します。 LIB 変数では、複数のパスをセミコロンで区切って指定できます。 1 つのパスは Visual C++ インストールの \lib サブディレクトリを示す必要があります。

- PATH。ツールが CVTRES を実行する必要があり、LINK 自身と同じディレクトリ内にこのファイルが見つからない場合  (LINK では、.res ファイルをリンクするために CVTRES が必要です)。パスは、Visual C++ インストールの \bin サブディレクトリをポイントする必要があります。

- TMP。OMF ファイルまたは .res ファイルをリンクするときのディレクトリを指定します。

## <a name="see-also"></a>関連項目

[C/c + + ビルドのリファレンス](c-cpp-building-reference.md) 
[MSVC リンカーオプション](linker-options.md) 
[モジュール定義 (.def) ファイル](module-definition-dot-def-files.md) 
[リンカーによる Delay-Loaded dll のサポート](linker-support-for-delay-loaded-dlls.md)
