---
title: C 代入演算子
ms.date: 06/14/2018
helpviewer_keywords:
- remainder assignment operator (%=)
- '&= operator'
- bitwise-AND assignment operator
- operators [C], assignment
- operators [C], shift
- ^= operator, assignment operators
- += operator
- '>>= operator'
- '|= operator'
- division assignment operator
- subtraction operator
- right shift operators
- subtraction operator, C assignment operators
- = operator, assignment operators
- '*= operator'
- '>> operator'
- '%= operator'
- assignment operators, C
- = operator
- assignment operators
- assignment conversions
- -= operator
- multiplication assignment operator (*=)
- shift operators, right
- /= operator
- operator >>=, C assignment operators
- <<= operator
ms.assetid: 11688dcb-c941-44e7-a636-3fc98e7dac40
ms.openlocfilehash: e8ada96daaec249a05882aceae9b7d9e86b92065
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168800"
---
# <a name="c-assignment-operators"></a>C 代入演算子

代入演算は、右オペランドの値を、左オペランドによって指定されたデータ格納場所に代入します。 したがって、代入演算の左オペランドは変更可能な左辺値である必要があります。 代入の後、代入式は左オペランドの値を持ちますが、代入式は左辺値ではありません。

## <a name="syntax"></a>構文

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*単項式*の代入*演算子*の*代入式*

*assignment-operator*: 次のいずれか<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **=** **\*** **=/=%=** **+=-=** **\<\<** **-=** **=>>=** **&=^=** **&=** **^=** **|=**

C の代入演算子は、1 回の演算で値の変換と値の代入の両方を実行することができます。 C には、次の代入演算子が用意されています。

|[演算子]|実行される演算|
|--------------|-------------------------|
|**=**|単純代入|
|**&#42;=**|乗算代入|
|**/=**|除算代入|
|**%=**|剰余代入|
|**+=**|加算代入|
|**-=**|減算代入|
|**<\<=**|左シフト代入|
|**>>=**|右シフト代入|
|**&=**|ビットごとの AND 代入|
|**^=**|ビットごとの排他的 OR 代入|
|**&#124;=**|ビットごとの包括的 OR/代入|

代入では、右辺値の型は、左辺値の型に変換され、代入が行われた後、値が左オペランドに格納されます。 左オペランドを、配列、関数、または定数にすることはできません。 2 つの型に依存する特定の変換パスについては、「[型変換](../c-language/type-conversions-c.md)」で詳しく説明します。

## <a name="see-also"></a>関連項目

- [代入演算子](../cpp/assignment-operators.md)
