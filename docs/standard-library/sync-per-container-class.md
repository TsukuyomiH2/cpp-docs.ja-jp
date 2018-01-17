---
title: "sync_per_container クラス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
dev_langs: C++
helpviewer_keywords: sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7864b6367d716ff7504982c4a8cbbed55f7784c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="syncpercontainer-class"></a>sync_per_container クラス
アロケーター オブジェクトごとに個別のキャッシュ オブジェクトを提供する[同期フィルター](../standard-library/allocators-header.md)を記述します。  
  
## <a name="syntax"></a>構文  
  
```
template <class Cache>  
class sync_per_container
 : public Cache
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`Cache`|同期フィルターに関連付けられているキャッシュの型。 これは、[cache_chunklist](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md)、[cache_suballoc](../standard-library/cache-suballoc-class.md) のいずれかです。|  
  
### <a name="member-functions"></a>メンバー関数  
  
|||  
|-|-|  
|[equals](#equals)|2 つのキャッシュが等しいかどうかを比較します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** \<allocators>  
  
 **名前空間:** stdext  
  
##  <a name="equals"></a>  sync_per_container::equals  
 2 つのキャッシュが等しいかどうかを比較します。  
  
```
bool equals(const sync_per_container<Cache>& Other) const;
```  
  
### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`Cache`|同期フィルターのキャッシュ オブジェクト。|  
|`Other`|等しいかどうかを比較するキャッシュ オブジェクト。|  
  
### <a name="return-value"></a>戻り値  
 このメンバー関数は常に `false` を返します。  
  
### <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [\<allocators>](../standard-library/allocators-header.md)


