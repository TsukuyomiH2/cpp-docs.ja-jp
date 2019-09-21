---
title: Visual Studio での C++ ビルド システムの [フォルダーを開く] のサポート
ms.date: 08/20/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 78b1c00b07423e9d02f585c707156a1c843bea6f
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69976017"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Visual Studio での C++ ビルド システムの [フォルダーを開く] のサポート

::: moniker range="vs-2015"

フォルダーを開く機能は、Visual Studio 2017 以降で使用できます。

::: moniker-end

::: moniker range=">=vs-2017"

Visual Studio 2017 以降で "フォルダーを開く" 機能を使うと、ソース ファイルのフォルダーを開き、IntelliSense、参照、リファクタリング、デバッグなどのサポートを利用してコーディングをすぐに始めることができます。 ファイルを編集、作成、移動、または削除すると、Visual Studio は自動的に変更を追跡し、IntelliSense インデックスを継続的に更新します。 .sln または .vcxproj ファイルは読み込まれません。必要な場合は、カスタム タスクを指定し、簡単な .json ファイルを使ってパラメーターをビルドして起動できます。 この機能を使用すると、任意のサードパーティ製ビルドシステムを Visual Studio に統合できます。 [フォルダーを開く] に関する詳細については、「[プロジェクトまたはソリューションを使用せずに Visual Studio でコードを開発する](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions)」を参照してください。

## <a name="cmake-and-qt"></a>CMake と Qt

CMake は、 C++デスクトップワークロードのコンポーネントとして VISUAL Studio IDE に統合されています。 CMake のワークフローは、この記事で説明されているワークフローと同一ではありません。 CMake を使用している場合は、「 [Visual Studio での cmake プロジェクト](cmake-projects-in-visual-studio.md)」を参照してください。 CMake を使用して Qt プロジェクトをビルドすることもできます。または、visual Studio 2015 または Visual Studio 2017 用に[Qt Visual Studio 拡張機能](https://download.qt.io/development_releases/vsaddin/)を使用することもできます。

## <a name="other-build-systems"></a>その他のビルドシステム

メインメニューから直接サポートされていないビルドシステムまたはコンパイラツールセットを使用して Visual Studio IDE を使用するには、[ファイル |] を選択します。 **を開く |フォルダー**または**Ctrl + Shift + Alt + O**キーを押します。ソースコードファイルが格納されているフォルダーに移動します。 プロジェクトをビルドし、IntelliSense を構成し、デバッグパラメーターを設定するには、次の3つの JSON ファイルを追加します。

| | |
|-|-|
|CppProperties.json|参照のためのカスタム構成情報を指定します。 必要な場合は、ルート プロジェクト フォルダーにこのファイルを作成します。 (CMake プロジェクトで使用されません。)|
|tasks.vs.json|カスタムビルドコマンドを指定します。 指定するには、**ソリューション エクスプローラー**のコンテキスト メニュー項目 **[タスクの構成]** を使用します。|
|launch.vs.json|デバッガーのコマンド ライン引数を指定します。 指定するには、**ソリューション エクスプローラー**のコンテキスト メニュー項目 **[デバッグ設定と起動設定]** を使用します。|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>CppProperties を使用したコードナビゲーションの構成

IntelliSense と参照の動作 ( **[定義へ移動**] など) を正しく動作させるには、Visual Studio で、使用しているコンパイラ、システムヘッダーの場所、およびその他のインクルードファイルが配置されている場所を指定する必要があります。開いたフォルダー (ワークスペースフォルダー)。 構成を指定するには、メインツールバーのドロップダウンから **[構成の管理]** を選択します。

![構成の管理ドロップダウン](media/manage-configurations-dropdown.png)

現在、Visual Studio では、次の4つの既定C++の構成が提供されています。すべて Microsoft コンパイラ用です。

![既定の構成](media/default-configurations.png)

たとえば、 **[x64-デバッグ]** を選択すると、Visual Studio はルートプロジェクトフォルダーに*cppproperties. json*という名前のファイルを作成し、次のように設定します。

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```

この構成は、Visual Studio [x64 開発者コマンドプロンプト](building-on-the-command-line.md)の環境変数を "継承" します。 これらの変数の 1 `INCLUDE`つはで、 `${env.INCLUDE}`マクロを使用してここで参照できます。 プロパティ`includePath`は、IntelliSense に必要なすべてのソースを検索する場所を Visual Studio に指示します。 この場合、"INCLUDE 環境変数で指定されたすべてのディレクトリと、現在の作業フォルダーツリー内のすべてのディレクトリを検索" と表示されます。 `name`プロパティは、ドロップダウンに表示される名前で、任意の名前を指定できます。 プロパティ`defines`は、条件付きコンパイルブロックが検出されたときに IntelliSense にヒントを提供します。 プロパティ`intelliSenseMode`は、コンパイラの種類に基づいていくつかの追加のヒントを提供します。 MSVC、GCC、Clang では、いくつかのオプションを使用できます。

## <a name="example-configuration-for-gcc"></a>GCC の構成例

Microsoft C++以外のコンパイラを使用している場合は、カスタム構成と環境を*cppproperties. json*で作成する必要があります。 次の例は、MSYS2 インストールで GCC を使用するための1つのカスタム構成を含む完全な*Cppproperties. json*ファイルを示しています。

```json
{
  "configurations": [
   {
      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "8.3.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
   }
}
```

ブロックに`environments`注意してください。 環境変数と同様に動作するプロパティを定義します。このプロパティは、 *Cppproperties. json*ファイルだけでなく、その他の構成ファイルであるという*タスク*でも使用できます。 構成`Mingw64` `mingw_w64`は環境を継承し、その`INCLUDE`プロパティを使用しての`includePath`値を指定します。 必要に応じて、この配列プロパティに他のパスを追加することができます。

> [!WARNING]
> 現在、に`INCLUDE` `environments`指定された値が`includePath`プロパティに正しく渡されないという既知の問題があります。 この問題を回避するには、完全なリテラルインクルードパスを`includePath`配列に追加します。

`intelliSenseMode`プロパティは、GCC に適した値に設定されます。 これらすべてのプロパティの詳細については、「 [Cppproperties スキーマリファレンス](cppproperties-schema-reference.md)」を参照してください。

すべてが正常に動作している場合は、型にマウスポインターを合わせると、GCC ヘッダーから IntelliSense が表示されます。

![GCC IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>IntelliSense 診断を有効にする

IntelliSense が表示されない場合は、**ツール** >  **オプション** > **テキストエディター** >  **CC++** 、詳細設定の順に移動して、トラブルシューティングを行うことができます。 > "**ログを有効**にする" を**true**に設定します。 最初に、**ログ記録レベル**を5に設定し、フィルターを8に**ログ記録**するようにします。

![診断ログ](media/diagnostic-logging.png)

出力は**出力ウィンドウ**にパイプ処理され、* *[出力元の表示] を選択すると表示されます。ビジュアルC++ログ*。 出力には、IntelliSense が使用しようとしている実際のインクルードパスの一覧が含まれます。 パスが*Cppproperties. json*のパスと一致しない場合は、フォルダーを閉じて、キャッシュされた参照データを含む*vs*サブフォルダーを削除してみてください。

### <a name="define-build-tasks-with-tasksvsjson"></a>tasks.vs.json でビルド タスクを定義する

IDE でタスクとして直接実行することで、現在のワークスペースにあるファイルに対してビルド スクリプトやその他の外部操作を自動化できます。 ファイルまたはフォルダーを右クリックし、 **[タスクの構成]** を選択すると、新しいタスクを構成できます。

!["フォルダーを開く" のタスクの構成](media/configure-tasks.png)

これにより、Visual Studio によってルートプロジェクトフォルダー内に作成される vs フォルダーに、*タスクと json*ファイルが作成されます (または開きます)。 このファイルで任意のタスクを定義し、**ソリューション エクスプローラー**のコンテキスト メニューから呼び出すことができます。 GCC の例を続行するために、次のスニペットは、 *g + + .exe*を呼び出してプロジェクトをビルドする単一のタスクとしての完全な*タスクと json*ファイルを示しています。 プロジェクトに*hello*という名前のファイルが1つ含まれているとします。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "build hello",
      "appliesTo": "/",
      "type": "default",
      "command": "g++",
      "args": [
        "-g",
        "-o",
        "hello",
        "hello.cpp"
      ]
    }
  ]
}

```

JSON ファイルは、**ソリューションエクスプローラー**の上部にある **[すべてのファイルを表示]** ボタンをクリックすると表示される vs サブフォルダーに配置されます *。* このタスクを実行するには**ソリューションエクスプローラー**のルートノードを右クリックし、**ビルド** hello の順に選択します。 タスクが完了すると、**ソリューションエクスプローラー**に新しいファイルが表示されます。

さまざまな種類のタスクを定義できます。 次の例は、1つのタスクを定義する*tasks と json ファイル*を示しています。 `taskLabel` では、コンテキスト メニューに表示される名前を定義します。 `appliesTo` では、コマンドを実行できるファイルを定義します。 プロパティ`command`は、コンソールのパス (Windows の場合は*cmd.exe* ) を識別する COMSPEC 環境変数を参照します。 CppProperties.json または CMakeSettings.json で宣言されている環境変数を参照することもできます。 `args` プロパティでは、呼び出すコマンド ラインを指定します。 `${file}` マクロは、**ソリューション エクスプローラー**で選択したファイルを取得します。 次の例では、現在選択されている .cpp ファイルのファイル名が表示されます。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

*タスク*を保存した後、フォルダー内の *.cpp*ファイルを右クリックし、コンテキストメニューから **[Echo filename]** を選択すると、出力ウィンドウに表示されるファイル名を確認できます。

詳細については、「[Tasks.vs.json schema reference](tasks-vs-json-schema-reference-cpp.md)」 (Tasks.vs.json スキーマ リファレンス) を参照してください。

### <a name="configure-debugging-parameters-with-launchvsjson"></a>launch.vs.json でデバッグ パラメーターを構成する

プログラムのコマンドライン引数とデバッグ手順をカスタマイズするには、**ソリューションエクスプローラー**で実行可能ファイルを右クリックし、 **[デバッグと起動の設定]** を選択します。 これにより、既存の*起動と json*ファイルが開きます。存在しない場合は、最小の起動設定のセットを含む新しいファイルが作成されます。 まず、どの種類のデバッグセッションを構成するかを選択します。 MinGw mingw-w64 プロジェクトをデバッグする場合は、 **MinGGW/cygwin (gdb) に対して C/C++ Launch**を選択します。 これにより、 *gdb*を使用して既定値についての何らかの推測を行うための起動構成が作成されます。 これらの既定値の 1 `MINGW_PREFIX`つはです。 次に示すようにリテラルパスを置き換えることも、 `MINGW_PREFIX` *cppproperties. json*でプロパティを定義することもできます。

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "cppdbg",
      "name": "hello.exe",
      "project": "hello.exe",
      "cwd": "${workspaceRoot}",
      "program": "${debugInfo.target}",
      "MIMode": "gdb",
      "miDebuggerPath": "c:\\msys64\\usr\\bin\\gdb.exe",
      "externalConsole": true
    }
  ]
}

```

デバッグを開始するには、[デバッグ] ドロップダウンで実行可能ファイルを選択し、緑色の矢印をクリックします。

![デバッガーを起動する](media/launch-debugger-gdb.png)

**[初期化デバッガー]** ダイアログボックスが表示され、その後、プログラムを実行している外部コンソールウィンドウが表示されます。

詳細については、「 [launch. json スキーマリファレンス](launch-vs-schema-reference-cpp.md)」を参照してください。

## <a name="launching-other-executables"></a>その他の実行可能ファイルの起動

コンピューター上の実行可能ファイルの起動設定を定義できます。 次の例では、 *7za*を起動し、追加の引数を`args` JSON 配列に追加することによって指定します。

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CPP\\7zip\\Bundles\\Alone\\O\\7za.exe",
      "name": "7za.exe list content of helloworld.zip",
      "args": [ "l", "d:\\sources\\helloworld.zip" ]
    }
  ]
}
```

このファイルを保存すると、[デバッグ ターゲット] ドロップダウンに新しい構成が表示され、名前を選択してデバッガーを起動できるようになります。 必要に応じて、任意の数の実行可能ファイルに対し、デバッグ構成をいくつでも作成できます。 ここで **F5** キーを押すと、デバッガーが起動し、既に設定してあるブレークポイントにヒットします。 使い慣れたすべてのデバッガー ウィンドウとそれらの機能を使用できるようになりました。

::: moniker-end
