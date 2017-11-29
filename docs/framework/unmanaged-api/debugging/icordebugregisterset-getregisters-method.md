---
title: ICorDebugRegisterSet::GetRegisters-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7edae3d3be1bcfb80b7a1e432fd5f25e119f078f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="21b24-102">ICorDebugRegisterSet::GetRegisters-Methode</span><span class="sxs-lookup"><span data-stu-id="21b24-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="21b24-103">Ruft den Wert jedes Register (auf dem Computer, der Code derzeit ausgeführt wird), die durch die Bitmaske angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="21b24-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b24-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="21b24-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21b24-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="21b24-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="21b24-106">[in] Eine Bitmaske, die angibt, welche Register Werte abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="21b24-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="21b24-107">Jedes Bit entspricht einer registriert wird.</span><span class="sxs-lookup"><span data-stu-id="21b24-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="21b24-108">Wenn ein bit auf 1 festgelegt ist, wird der Wert des Registers abgerufen; Andernfalls ist der Wert des Registers nicht abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="21b24-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="21b24-109">[in] Die Anzahl der Registerwerte abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="21b24-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="21b24-110">[out] Ein Array von `CORDB_REGISTER` Objekte, von denen jede einen Wert eines Registers empfängt.</span><span class="sxs-lookup"><span data-stu-id="21b24-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21b24-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="21b24-111">Remarks</span></span>  
 <span data-ttu-id="21b24-112">Die Größe des Arrays muss gleich der Anzahl von Bits, die auf einen in der Bitmaske festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="21b24-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="21b24-113">Die `regCount` Parameter gibt die Anzahl der Elemente im Puffer, die die Registerwerte erhält.</span><span class="sxs-lookup"><span data-stu-id="21b24-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="21b24-114">Wenn die `regCount` Wert ist zu klein für die angegebene Anzahl von Registern durch die Maske, die höhere nummerierten Register aus dem Satz abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="21b24-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="21b24-115">Wenn die `regCount` Wert ist zu groß ist, der nicht verwendeten `regBuffer` Elemente nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="21b24-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="21b24-116">Wenn die Bitmaske ein Registers angibt, der nicht verfügbar ist, `GetRegisters` gibt einen unbestimmten Wert für, die sich registrieren.</span><span class="sxs-lookup"><span data-stu-id="21b24-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21b24-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="21b24-117">Requirements</span></span>  
 <span data-ttu-id="21b24-118">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21b24-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b24-119">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21b24-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21b24-120">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21b24-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21b24-121">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b24-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b24-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="21b24-122">See Also</span></span>  
 [<span data-ttu-id="21b24-123">ICorDebugRegisterSet-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="21b24-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="21b24-124">ICorDebugRegisterSet2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="21b24-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)