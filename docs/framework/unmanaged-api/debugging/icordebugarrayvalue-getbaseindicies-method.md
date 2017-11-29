---
title: ICorDebugArrayValue::GetBaseIndicies-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetBaseIndicies
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c8705e31e99effd8741029f9709f3982e097a693
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="e733a-102">ICorDebugArrayValue::GetBaseIndicies-Methode</span><span class="sxs-lookup"><span data-stu-id="e733a-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="e733a-103">Ruft den Basis Index jeder Dimension im Array ab.</span><span class="sxs-lookup"><span data-stu-id="e733a-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e733a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e733a-104">Syntax</span></span>  
  
```  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e733a-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="e733a-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="e733a-106">[in] Die Anzahl der Dimensionen dieses `ICorDebugArrayValue` Objekt.</span><span class="sxs-lookup"><span data-stu-id="e733a-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="e733a-107">Dieser Wert ist auch die Größe der `indicies` Arrays, da seine Größe gleich der Anzahl der Dimensionen des ist die `ICorDebugArrayValue` Objekt.</span><span class="sxs-lookup"><span data-stu-id="e733a-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="e733a-108">[out] Ein Array von Ganzzahlen, von denen jede der Basisindex (d. h. den Startindex) einer Dimension dieses wird `ICorDebugArrayValue` Objekt.</span><span class="sxs-lookup"><span data-stu-id="e733a-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e733a-109">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e733a-109">Requirements</span></span>  
 <span data-ttu-id="e733a-110">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e733a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e733a-111">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e733a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e733a-112">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e733a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e733a-113">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e733a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>