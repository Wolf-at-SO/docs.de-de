---
title: ICorDebugType::GetType-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20e2a1415d5dda9c4097d984af46942ebcf2365a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="9707c-102">ICorDebugType::GetType-Methode</span><span class="sxs-lookup"><span data-stu-id="9707c-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="9707c-103">Ruft einen CorElementType-Wert, den systemeigenen Typ der common Language Runtime (CLR) beschreibt <xref:System.Type> ICorDebugType dargestellt.</span><span class="sxs-lookup"><span data-stu-id="9707c-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9707c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9707c-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9707c-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="9707c-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="9707c-106">[out] Ein Zeiger auf einen Wert von der `CorElementType` -Enumeration, die die CLR gibt <xref:System.Type> , die von diesem `ICorDebugType` darstellt.</span><span class="sxs-lookup"><span data-stu-id="9707c-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9707c-107">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9707c-107">Remarks</span></span>  
 <span data-ttu-id="9707c-108">Wenn der Wert der `ty` ELEMENT_TYPE_CLASS oder ELEMENT_TYPE_VALUETYPE, ist die [ICorDebugType:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) Methode kann aufgerufen werden, um den nicht instanziierten Typ für einen generischen Typ abzurufen, rufen Sie Sie andernfalls nicht `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="9707c-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9707c-109">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="9707c-109">Requirements</span></span>  
 <span data-ttu-id="9707c-110">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9707c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9707c-111">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9707c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9707c-112">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9707c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9707c-113">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9707c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>