---
title: FunctionEnter3WithInfo-Funktion
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3WithInfo
api_location: mscorwks.cll
api_type: COM
f1_keywords: FunctionEnter3WithInfo
helpviewer_keywords: FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 37cdf823cc910dd1cebcb587d2616406a842fef2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="ae7c2-102">FunctionEnter3WithInfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="ae7c2-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="ae7c2-103">Benachrichtigt den Profiler, dass die Steuerung an eine Funktion übergeben wird, und stellt ein Handle, das übergeben werden kann die [ICorProfilerInfo3:: Getfunctionenter3info-Methode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) auf den Stapel und die Funktionsargumente abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae7c2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ae7c2-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae7c2-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="ae7c2-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="ae7c2-106">[in] Der Bezeichner der Funktion an der Steuerelement übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="ae7c2-107">[in] Ein nicht transparentes Handle, das Informationen über einen bestimmten Stapelrahmen entspricht.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="ae7c2-108">Dieses Handle ist nur während des Rückrufs, an den er übergeben ist, gültig.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae7c2-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ae7c2-109">Remarks</span></span>  
 <span data-ttu-id="ae7c2-110">Die `FunctionEnter3WithInfo` Rückrufmethode benachrichtigt den Profiler, wie Funktionen aufgerufen werden, und ermöglicht es dem Profiler zum Verwenden der [ICorProfilerInfo3:: Getfunctionenter3info-Methode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) um Argumentwerte zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="ae7c2-111">Argumentinformationen, den Zugriff auf die `COR_PRF_ENABLE_FUNCTION_ARGS` Flag muss festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="ae7c2-112">Der Profiler kann mithilfe der [ICorProfilerInfo:: SetEventMask-Methode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) die Ereignisflags festlegen und dann mithilfe der [ICorProfilerInfo3:: Setenterleavefunctionhooks3withinfo-Methode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) zum Registrieren Ihrer die Implementierung dieser Funktion.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="ae7c2-113">Die `FunctionEnter3WithInfo` Funktion ist ein Rückruf; Sie müssen ihn implementieren.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="ae7c2-114">Verwenden Sie die Implementierung muss die `__declspec(naked)` Storage-Class-Attribut.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="ae7c2-115">Das Ausführungsmodul werden keine Register gespeichert, vor dem Aufrufen dieser Funktion.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="ae7c2-116">Auf Eintrag müssen Sie alle Register speichern, die Sie, einschließlich die Gleitkommaeinheit (FPU verwenden).</span><span class="sxs-lookup"><span data-stu-id="ae7c2-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="ae7c2-117">Beim Beenden müssen Sie den Stapel wiederherstellen, indem abholen alle Parameter, die durch den Aufrufer weitergegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="ae7c2-118">Die Implementierung der `FunctionEnter3WithInfo` sollte nicht blockiert werden, da es die Garbagecollection verzögert.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="ae7c2-119">Die Implementierung sollten eine Garbagecollection nicht versuchen, da der Stapel möglicherweise nicht in eine Garbage Collection-freundliche-Status.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="ae7c2-120">Wenn eine Garbagecollection versucht wird, wird die Laufzeit blockiert, bis `FunctionEnter3WithInfo` zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="ae7c2-121">Die `FunctionEnter3WithInfo` Funktion muss nicht verwalteten Code aufrufen oder dazu führen, dass eine verwaltete speicherbelegung in keiner Weise.</span><span class="sxs-lookup"><span data-stu-id="ae7c2-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae7c2-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ae7c2-122">Requirements</span></span>  
 <span data-ttu-id="ae7c2-123">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae7c2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae7c2-124">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ae7c2-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ae7c2-125">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae7c2-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae7c2-126">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae7c2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7c2-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ae7c2-127">See Also</span></span>  
 [<span data-ttu-id="ae7c2-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="ae7c2-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)  
 [<span data-ttu-id="ae7c2-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="ae7c2-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="ae7c2-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="ae7c2-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="ae7c2-131">Profilerstellung für globale statische Funktionen</span><span class="sxs-lookup"><span data-stu-id="ae7c2-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)