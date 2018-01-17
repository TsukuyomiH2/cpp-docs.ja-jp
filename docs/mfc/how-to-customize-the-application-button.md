---
title: "方法: アプリケーション ボタンをカスタマイズ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4a4a150985bd5c552b361620df87e34511ef8027
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-customize-the-application-button"></a>方法: アプリケーション ボタンをカスタマイズする
アプリケーション ボタンをクリックすると、コマンドのメニューが表示されます。 通常、メニューに含まれるファイルに関連するコマンドなど**開く**、**保存**、**印刷**、および**終了**です。  
  
 ![MFC リボン アプリケーション ボタン](../mfc/media/application_button.png "application_button")  
  
 アプリケーション ボタンをカスタマイズするで開く、**プロパティ**ウィンドウで、そのプロパティを変更し、リボン コントロールをプレビューします。  
  
### <a name="to-open-the-application-button-in-the-properties-window"></a>開くには、[プロパティ] ウィンドウで、アプリケーション ボタン  
  
1.  Visual Studio での**ビュー**  メニューのをクリックして**リソース ビュー**です。  
  
2.  **リソース ビュー**、デザイン画面に表示するリボン リソースをダブルクリックします。  
  
3.  デザイン画面で、アプリケーション ボタン メニューを右クリックし、をクリックして**プロパティ**です。  
  
## <a name="application-button-properties"></a>アプリケーション ボタンのプロパティ  
 次の表では、アプリケーション ボタンのプロパティを定義します。  
  
|プロパティ|定義|  
|--------------|----------------|  
|**ボタン**|[アプリケーション] メニューの右下隅に表示される最大 3 つのボタンのコレクションが含まれています。|  
|**[キャプション]**|コントロールのテキストを指定します。 その他のリボン要素とは異なり、アプリケーション ボタンは、キャプションのテキストを表示できません。 代わりに、テキスト ユーザー補助機能が使用されます。|  
|**HDPI Image**|高ドット/インチ (HDPI) アプリケーション ボタンのアイコンの識別子を指定します。 モニターでは高 DPI、アプリケーションの実行時**HDPI Image**の代わりに使用される**イメージ**です。|  
|**HDPI Large Images**|高 DPI 大きいイメージの識別子を指定します。 モニターでは高 DPI、アプリケーションの実行時**HDPI Large Images**の代わりに使用される**Large Images**です。|  
|**HDPI Small Images**|高 DPI 小さいイメージの識別子を指定します。 モニターでは高 DPI、アプリケーションの実行時**HDPI Small Images**の代わりに使用される**Small Images**です。|  
|**ID**|コントロールの識別子を指定します。|  
|**イメージ**|アプリケーション ボタンのアイコンの識別子を指定します。 アイコンは、アルファの透過性のある 32 ビット 26 × 26 ビットマップです。 アイコンの透過的な部分は、アプリケーション ボタンがクリックされるかに置かれているときに強調表示されます。|  
|**キー**|キー ヒント ナビゲーションが有効になっているときに表示される文字列を指定します。 ALT キーを押したときに、キー ヒント ナビゲーションが有効にします。|  
|**大きいイメージ**|一連の 32 x 32 のアイコンを格納する、イメージの識別子を指定します。 アイコンは、Main Items コレクション内のボタンで使用されます。|  
|**メイン アイテム**|[アプリケーション] メニューに表示されるメニュー項目のコレクションを格納します。|  
|**MRU Caption**|最近使用した一覧のパネルに表示されるテキストを指定します。|  
|**小さいイメージ**|一連の 16 x 16 のアイコンを格納する、イメージの識別子を指定します。 アイコンはボタン コレクション内のボタンで使用されます。|  
|**使用します。**|有効または最近のリスト を無効にします。 最近使用した一覧パネルは、[アプリケーション] メニューが表示されます。|  
|**幅**|最近使用した一覧パネルのピクセル単位の幅を指定します。|  
  
 アプリケーションのメニューは、デザイン サーフェイスは表示されません。 これを表示するには、リボンをプレビューかアプリケーションを実行する必要があります。  
  
#### <a name="to-preview-the-ribbon-control"></a>リボン コントロールをプレビューするには  
  
-   **Ribbon エディター ツールバー**をクリックして**Ribbon のテスト**です。  
  
## <a name="see-also"></a>参照  
 [リボン デザイナー (MFC)](../mfc/ribbon-designer-mfc.md)
