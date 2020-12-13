---
description: '詳細については、次を参照してください: variant_alternative 構造体'
title: variant_alternative 構造体
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant_alternative
helpviewer_keywords:
- variant_alternative struct
ms.openlocfilehash: bbad42afa517c7f6ad46561a85c1b73e71041a57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337846"
---
# <a name="variant_alternative-struct"></a>variant_alternative 構造体

Variant オブジェクトを支援します。

## <a name="syntax"></a>構文

```cpp
template <size_t I, class T>
    struct variant_alternative; // not defined
template <size_t I, class T>
    struct variant_alternative<I, const T>;
template <size_t I, class T>
    struct variant_alternative<I, volatile T>;
template <size_t I, class T>
    struct variant_alternative<I, const volatile T>;
template <size_t I, class T>
    using variant_alternative_t = typename variant_alternative<I, T>::type;
template <size_t I, class... Types>
    struct variant_alternative<I, variant<Types...>>;
```
