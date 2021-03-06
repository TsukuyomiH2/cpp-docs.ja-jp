---
title: Visual Studio で CMake のビルド設定をカスタマイズする
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: 9fa1a21b26088482fb64441d0ccf0ad968bd480f
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919268"
---
# <a name="customize-cmake-build-settings"></a>CMake のビルド設定をカスタマイズする

::: moniker range="msvc-160"

Visual Studio 2019 以降では、 **CMake 設定エディター** を使うことにより、構成を追加して、その設定をカスタマイズすることができます。 エディターは *CMakeSettings.json* ファイルを手動で編集するより簡単な代わりの手段として用意されていますが、ファイルを直接編集する方がよい場合は、エディターの右上にある **[JSON の編集]** リンクをクリックできます。

エディターを開くには、メイン ツール バーの **[構成]** ドロップダウンをクリックして、 **[構成の管理]** を選択します。

![CMake 構成ドロップダウン](media/vs2019-cmake-manage-configurations.png)

インストールされている構成が左側に示された **設定エディター** が表示されます。

![CMake 設定エディター](media/cmake-settings-editor.png)

Visual Studio では、1 つの `x64-Debug` 構成が既定で提供されています。 緑色の正符号をクリックすると、追加の構成を加えることができます。 エディターに表示される設定は、選択した構成によって異なる場合があります。

エディターで選択したオプションは、 *CMakeSettings.json* という名前のファイルに書き込まれます。 このファイルで指定されているコマンド ライン引数と環境変数は、プロジェクトをビルドするときに CMake に渡されます。 Visual Studio で *CMakeLists.txt* が自動的に変更されることはありません。 *CMakeSettings.json* を使うことにより、Visual Studio でビルドをカスタマイズしながら、CMake プロジェクト ファイルは変更されないようにして、チームの他のメンバーが任意のツールでそれを使用できるようにすることができます。

## <a name="cmake-general-settings"></a>CMake の全般設定

**[全般]** では、次の設定を使用できます。

### <a name="configuration-name"></a>構成名

**name** の設定に対応します。 この名前は C++ の構成ドロップダウンに表示されます。 `${name}` マクロを使って、パスなどの他のプロパティ値を作成できます。

### <a name="configuration-type"></a>構成のタイプ

**configurationType** の設定に対応します。 選択したジェネレーターのビルド構成の種類を定義します。 現在サポートされている値は、"Debug"、"MinSizeRel"、"Release"、"RelWithDebInfo" です。 [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html) に対応します。

### <a name="toolset"></a>ツールセット

**inheritedEnvironments** の設定に対応します。 選択した構成のビルドに使用されるコンパイラ環境を定義します。 サポートされる値は、構成の種類によって異なります。 カスタム環境を作成するには、設定エディターの右上隅にある **[JSON の編集]** リンクを選択し、 *CMakeSettings.json* ファイルを直接編集します。

### <a name="cmake-toolchain-file"></a>CMake ツールチェーン ファイル

[CMake ツールチェーン ファイル](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html)へのパスです。 このパスは "-DCMAKE_TOOLCHAIN_FILE = \<filepath>" として CMake に渡されます。 ツールチェーン ファイルは、コンパイラとツールチェーン ユーティリティの場所、および他のターゲット プラットフォームとコンパイラに関連する情報を指定します。 既定では、この設定が指定されていない場合、Visual Studio で [vcpkg ツールチェーン ファイル](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake) が使用されます。

### <a name="build-root"></a>ビルド ルート

**buildRoot** に対応します。 [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html) に対応し、CMake キャッシュを作成する場所を指定します。 指定されたフォルダーが存在しない場合は作成されます。

## <a name="command-arguments"></a>コマンド引数

**[コマンド引数]** では、次の設定を使用できます。

### <a name="cmake-command-arguments"></a>CMake コマンド引数

**cmakeCommandArgs** に対応します。 CMake.exe に渡される追加の[コマンド ライン オプション](https://cmake.org/cmake/help/latest/manual/cmake.1.html)を指定します。

### <a name="build-command-arguments"></a>ビルド コマンド引数

**buildCommandArgs** に対応します。 基礎となるビルド システムに渡される追加スイッチを指定します。 たとえば、Ninja ジェネレーターの使用時に `-v` を渡すと、コマンド ラインの出力が Ninja に強制されます。

### <a name="ctest-command-arguments"></a>CTest コマンド引数

**ctestCommandArgs** に対応します。 テストの実行中に CTest に渡す追加の[コマンド ライン オプション](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html)を指定します。

## <a name="general-settings-for-remote-builds"></a>リモート ビルドの全般設定

リモート ビルドを使う Linux などの構成では、次の設定も使用できます。

### <a name="rsync-command-arguments"></a>rsync コマンド引数

[rsync](https://download.samba.org/pub/rsync/rsync.html) に渡される追加のコマンド ライン オプションであり、高速で多用途のファイル コピー ツールです。

## <a name="cmake-variables-and-cache"></a>CMake 変数とキャッシュ

これらの設定を使うと、CMake 変数を設定し、それらを *CMakeSettings.json* に保存できます。 それらはビルド時に CMake に渡され、 *CMakeLists.txt* ファイルの値はすべてそれらによってオーバーライドされます。 CMakeGUI と同じ方法でこのセクションを使用し、編集できるすべての CMake 変数の一覧を表示できます。 **[Save and generate cache]\(キャッシュの保存と生成\)** ボタンをクリックして、高度な変数 (CMakeGUI ごと) を含む編集可能なすべての CMake 変数の一覧を表示します。 変数名で一覧をフィルター処理できます。

**variables** に対応します。 **-D** *_name_=_value_* として CMake に渡される CMake 変数の名前と値のペアを含みます。 CMake プロジェクトのビルド命令で CMake キャッシュ ファイルに直接変数を追加するように指定している場合は、代わりにここで追加することをお勧めします。

## <a name="advanced-settings"></a>詳細設定

### <a name="cmake-generator"></a>CMake ジェネレーター

**generator** に対応します。 CMake **-G** スイッチに対応し、使用する [CMake ジェネレーター](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)を指定します。 他のプロパティ値を作成するときに、このプロパティをマクロ `${generator}` として使うこともできます。 現在、Visual Studio では次の CMake ジェネレーターがサポートされています。

- "Ninja"
- "Unix Makefiles"
- "Visual Studio 16 2019"
- "Visual Studio 16 2019 Win64"
- "Visual Studio 16 2019 ARM"
- "Visual Studio 15 2017"
- "Visual Studio 15 2017 Win64"
- "Visual Studio 15 2017 ARM"
- "Visual Studio 14 2015"
- "Visual Studio 14 2015 Win64"
- "Visual Studio 14 2015 ARM"
  
Ninja は柔軟性や機能ではなく、ビルド速度が速いことを目的に設計されているため、既定値としてこれが設定されます。 ただし、CMake プロジェクトによっては、Ninja を使うと正しくビルドできないことがあります。 そのような場合は、代わりに Visual Studio プロジェクトを生成するように CMake に指示できます。

### <a name="intellisense-mode"></a>IntelliSense モード

IntelliSense エンジンによって使用される IntelliSense モード。 モードが選択されないと、Visual Studio では指定されたツールセットから継承されます。  

### <a name="install-directory"></a>インストール ディレクトリ

CMake によってターゲットがインストールされるディレクトリです。 [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html) に対応します。

### <a name="cmake-executable"></a>CMake 実行可能ファイル

CMake プログラムの実行可能ファイルへの完全なパス。ファイル名と拡張子を含めます。 これにより、Visual Studio でカスタム バージョンの CMake を使用できます。 リモート ビルドの場合は、リモート マシン上の CMake の場所を指定します。

リモート ビルドを使う Linux などの構成では、次の設定も使用できます。

### <a name="remote-cmakeliststxt-root"></a>リモート CMakeLists.txt ルート

ルート *CMakeLists.txt* ファイルが含まれるリモート マシン上のディレクトリです。

### <a name="remote-install-root"></a>リモート インストール ルート

CMake によってターゲットがインストールされるリモート マシン上のディレクトリです。 [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html) に対応します。

### <a name="remote-copy-sources"></a>ソースのリモート コピー

ソース ファイルをリモート マシンにコピーするかどうかを指定し、rsync または sftp を使用するかどうかを指定できます。

## <a name="directly-edit-cmakesettingsjson"></a>CMakeSettings.json を直接編集する

*CMakeSettings.json* を直接編集して、カスタム構成を作成することもできます。 **設定エディター** の右上には **[JSON の編集]** ボタンがあり、編集用にファイルを開くことができます。

次の例では、作業を始めるときに使用できるサンプルの構成を示します。

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

JSON の IntelliSense は、 *CMakeSettings.json* ファイルの編集を支援します。

   ![CMake の JSON の IntelliSense](media/cmake-json-intellisense.png "CMake の JSON の IntelliSense")

JSON エディターでは、互換性のない設定を選択したときも通知されます。

ファイルの各プロパティについて詳しくは、「[CMakeSettings.json スキーマ リファレンス](cmakesettings-reference.md)」をご覧ください。

::: moniker-end

::: moniker range="<=msvc-150"

Visual Studio 2017 では、特定のプロジェクトの CMake キャッシュを作成するために CMake.exe が呼び出される方法を定義する複数の CMake 構成が用意されています。 新しい構成を追加するには、ツール バーの [構成] ドロップダウンをクリックして **[構成の管理]** を選択します。

   ![CMake の構成の管理](media/cmake-manage-configurations.png)

定義済みの構成のリストから選択できます。

   ![CMake の定義済み構成](media/cmake-configurations.png)

初めて構成を選択すると、Visual Studio によって *CMakeSettings.json* ファイルがプロジェクトのルート フォルダー内に作成されます。 このファイルは、たとえば **クリーン** 操作の後などに、CMake キャッシュ ファイルを再作成するために使われます。

追加の構成を加えるには、 *CMakeSettings.json* を右クリックして、 **[構成の追加]** を選択します。

   ![CMake の [構成の追加]](media/cmake-add-configuration.png "CMake の [構成の追加]")

**CMake の設定エディター** を使用してファイルを編集することもできます。 **ソリューション エクスプローラー** で *CMakeSettings.json* を右クリックして、 **[CMake 設定の編集]** を選択します。 または、エディター ウィンドウの上部にある構成ドロップダウンから **[構成の管理]** を選択します。

*CMakeSettings.json* を直接編集して、カスタム構成を作成することもできます。 次の例では、作業を始めるときに使用できるサンプルの構成を示します。

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

JSON の IntelliSense は、 *CMakeSettings.json* ファイルの編集を支援します。

   ![CMake の JSON の IntelliSense](media/cmake-json-intellisense.png "CMake の JSON の IntelliSense")

ファイルの各プロパティについて詳しくは、「[CMakeSettings.json スキーマ リファレンス](cmakesettings-reference.md)」をご覧ください。

::: moniker-end

## <a name="see-also"></a>関連項目

[Visual Studio の CMake プロジェクト](cmake-projects-in-visual-studio.md)<br/>
[Linux CMake プロジェクトを構成する](../linux/cmake-linux-project.md)<br/>
[リモートの Linux コンピューターに接続する](../linux/connect-to-your-remote-linux-computer.md)<br/>
[CMake デバッグ セッションを構成する](configure-cmake-debugging-sessions.md)<br/>
[Linux プロジェクトの配置、実行、デバッグ](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 定義済み構成リファレンス](cmake-predefined-configuration-reference.md)
