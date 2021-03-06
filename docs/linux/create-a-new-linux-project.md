---
title: Visual Studio で Linux MSBuild C++ プロジェクトを作成する
ms.date: 10/15/2020
description: Visual Studio で新しい MSBuild ベースの Linux プロジェクトを作成します。
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 458a26408bfd29b714150e5259fd23807c9b2908
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921634"
---
# <a name="create-a-linux-msbuild-c-project-in-visual-studio"></a>Visual Studio で Linux MSBuild C++ プロジェクトを作成する

::: moniker range="msvc-140"

Linux プロジェクトは Visual Studio 2017 以降で使用できます。

::: moniker-end

::: moniker range="msvc-150"

最初に、Visual Studio 対応の **Linux 開発ワークロード** を必ずインストールします。 詳細については、「[Linux ワークロードのダウンロード、インストール、セットアップ](download-install-and-setup-the-linux-development-workload.md)」を参照してください。

クロスプラットフォーム コンパイルの場合は、CMake を使用することをお勧めします。 CMake のサポートは、Visual Studio 2019 の方がより進んでいます。 CMake がオプションではなく、既存の Windows Visual Studio ソリューションがあり Linux 用のコンパイルのために拡張したい場合は、Visual Studio Linux プロジェクトを **共有項目** プロジェクトと共に Windows ソリューションに追加することができます。 共有項目プロジェクトの両方のプラットフォーム間で共有されるコードを配置し、そのプロジェクトへの参照を Windows および Linux プロジェクトから追加します。

## <a name="to-create-a-new-linux-project"></a>新しい Linux プロジェクトを作成するには

Visual Studio 2017 で新しい Linux プロジェクトを作成するには、次のように操作します。

1. Visual Studio で **[ファイル]、[新しいプロジェクト]** の順に選択するか、 **Ctrl + Shift + N** キーを押します。
1. **[Visual C++]、[クロス プラットフォーム]、[Linux]** ノードの順に選択し、作成するプロジェクト タイプを選択します。 **[名前]** と **[場所]** を入力し、 **[OK]** を選択します。

   ![[Visual C++] > [クロス プラットフォーム] > [Linux] が選択され、すべてのプロジェクト タイプが強調され、[名前] および [場所] テキスト ボックスも強調されている [新しいプロジェクト] ダイアログ ボックスを示すスクリーンショット。](media/newproject.png)

   | プロジェクトの種類 | 説明 |
   | ------------ | --- |
   | **点滅 (Raspberry)** | Raspberry Pi デバイスを対象とするプロジェクト。LED を点滅させるようにサンプル コードが記述されています。 |
   | **C++ コンソール アプリケーション (Linux)** | すべての Linux コンピューターを対象とするプロジェクト。コンソールにテキストを出力するようにサンプル コードが記述されています。 |
   | **空のプロジェクト (Linux)** | すべての Linux コンピューターを対象とするプロジェクト。サンプル コードは記述されていません。 |
   | **メイクファイル プロジェクト (Linux)** | 標準のメイクファイル ビルド システムを使用して構築する、すべての Linux コンピューターを対象とするプロジェクト。 |

## <a name="next-steps"></a>次の手順

[MSBuild Linux プロジェクトを構成する](configure-a-linux-project.md)

::: moniker-end

::: moniker range="msvc-160"

最初に、Visual Studio 対応の **Linux 開発ワークロード** を必ずインストールします。 詳細については、「[Linux ワークロードのダウンロード、インストール、セットアップ](download-install-and-setup-the-linux-development-workload.md)」をご覧ください。

Visual Studio で Linux の新しい C++ プロジェクトを作成する場合、Visual Studio のプロジェクトを作成するか、CMake のプロジェクトを作成するか選択することができます。 この記事では、Visual Studio のプロジェクトを作成する方法について説明します。 一般に、オープンソースのコードを含む、またはクロスプラットフォーム開発のためにコンパイルする予定がある新しいプロジェクトでは、Visual Studio で CMake を使用することをお勧めします。 CMake プロジェクトでは、Windows と Linux の両方で同じプロジェクトをビルドしてデバッグできます。 詳細については、[Linux CMake プロジェクトの作成と構成](cmake-linux-project.md)に関する記事を参照してください。

CMake がオプションではなく、既存の Windows Visual Studio ソリューションがあり Linux 用のコンパイルのために拡張したい場合は、Visual Studio Linux プロジェクトを **共有項目** プロジェクトと共に Windows ソリューションに追加することができます。 共有項目プロジェクトの両方のプラットフォーム間で共有されるコードを配置し、そのプロジェクトへの参照を Windows および Linux プロジェクトから追加します。

## <a name="create-a-new-linux-project"></a>新しい Linux プロジェクトを作成する

Visual Studio 2019 で新しい Linux プロジェクトを作成するには、次のように操作します。

1. Visual Studio で **[ファイル]、[新しいプロジェクト]** の順に選択するか、 **Ctrl + Shift + N** キーを押します。[新しいプロジェクトの作成] ダイアログが表示されます。
1. **[テンプレートの検索]** テキストボックスに「 **Linux** 」と入力し、Linux プロジェクトで利用できるテンプレートを一覧表示します。
1. **Console Application** など、作成するプロジェクトの種類を選択し、 **[次へ]** を選択します。 **[名前]** と **[場所]** を入力し、 **[作成]** を選択します。

   ![[新しいプロジェクト] ダイアログ ボックスのスクリーンショット。言語ドロップダウンが [C++] に設定され、プラットフォーム ドロップダウンが [Linux] に設定されています。](media/newproject-vs2019.png)

   | プロジェクトの種類 | 説明 |
   | ------------ | --- |
   | **Raspberry Pi プロジェクト** | Raspberry Pi デバイスを対象とするプロジェクト。LED を点滅させるようにサンプル コードが記述されています。 |
   | **コンソール アプリケーション** | すべての Linux コンピューターを対象とするプロジェクト。コンソールにテキストを出力するようにサンプル コードが記述されています。 |
   | **空のプロジェクト** | すべての Linux コンピューターを対象とするプロジェクト。サンプル コードは記述されていません。 |
   | **メイクファイル プロジェクト** | 標準のメイクファイル ビルド システムを使用して構築する、すべての Linux コンピューターを対象とするプロジェクト。 |
   | **CMake プロジェクト** | CMake ビルド システムを使用して構築する、すべての Linux コンピューターを対象とするプロジェクト。 |

## <a name="next-steps"></a>次の手順

[Linux MSBuild プロジェクトの構成](configure-a-linux-project.md)

::: moniker-end
