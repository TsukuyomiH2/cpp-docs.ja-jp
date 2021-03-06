---
description: '詳細については、次を参照してください: bidirectional_iterator_tag 構造体'
title: bidirectional_iterator_tag 構造体
ms.date: 11/04/2016
f1_keywords:
- xutility/std::bidirectional_iterator_tag
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
ms.openlocfilehash: db8de79c0fa5f9c748d453fcba7443351dcf217d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325560"
---
# <a name="bidirectional_iterator_tag-struct"></a>bidirectional_iterator_tag 構造体

`iterator_category`双方向反復子を表す関数の戻り値の型を提供するクラス。

## <a name="syntax"></a>構文

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>解説

カテゴリ タグ クラスがアルゴリズムの選択にコンパイル タグとして使用されます。 テンプレート関数は、コンパイル時に最も効率的なアルゴリズムを利用できるように、その反復子引数の最も具体的なカテゴリを見つける必要があります。 型 `Iterator` の反復子ごとに、反復子の動作を表す最も具体的なカテゴリ タグとして `iterator_traits`< `Iterator`>:: **iterator_category** を定義する必要があります。

この型は、が \< **Iter**>  `Iter` 双方向反復子として使用できるオブジェクトを表す場合に、iterator:: iterator_category と同じです。

## <a name="example"></a>例

`bidirectional_iterator_tag` の使用方法の例については、「[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)」を参照してください。

## <a name="requirements"></a>要件

**ヘッダー:**\<iterator>

**名前空間:** std

## <a name="see-also"></a>関連項目

[forward_iterator_tag 構造体](../standard-library/forward-iterator-tag-struct.md)\
[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリリファレンス](../standard-library/cpp-standard-library-reference.md)
