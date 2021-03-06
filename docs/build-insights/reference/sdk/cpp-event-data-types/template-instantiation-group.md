---
title: TemplateInstantiationGroup クラス
description: C++ Build Insights SDK の TemplateInstantiationGroup クラスのリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bacd48fbf15bfbbd768b527f42587425fb0932e6
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922968"
---
# <a name="templateinstantiationgroup-class"></a>TemplateInstantiationGroup クラス

::: moniker range="<=msvc-140"

C++ Build Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio **Version** セレクター コントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。 このページの目次の一番上にあります。

::: moniker-end
::: moniker range=">=msvc-150"

`TemplateInstantiationGroup` クラスは、[MatchEventStack](../functions/match-event-stack.md) および [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) 関数と共に使用されます。 [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) イベントのグループを照合するために使用します。

## <a name="syntax"></a>構文

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>メンバー

その基底クラス [EventGroup\<TemplateInstantiation\>](event-group.md) から継承されたメンバーに加えて、`TemplateInstantiationGroup` クラスには以下のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[TemplateInstantiationGroup](#template-instantiation-group)

## <a name="templateinstantiationgroup"></a><a name="template-instantiation-group"></a> TemplateInstantiationGroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>パラメーター

*group*\
[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) イベントのグループ。

::: moniker-end
