---
title: ICorDebugProcess::ReadMemory-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ReadMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33345ada6606bc1a43a630340251d3ba1404b2f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="0df5f-102">ICorDebugProcess::ReadMemory-Methode</span><span class="sxs-lookup"><span data-stu-id="0df5f-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="0df5f-103">Liest einen angegebenen Bereich des Arbeitsspeichers für diesen Prozess.</span><span class="sxs-lookup"><span data-stu-id="0df5f-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0df5f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0df5f-104">Syntax</span></span>  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0df5f-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="0df5f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="0df5f-106">[in] Ein `CORDB_ADDRESS` Wert, der die Basisadresse des Arbeitsspeichers zu lesende angibt.</span><span class="sxs-lookup"><span data-stu-id="0df5f-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="0df5f-107">[in] Die Anzahl der Bytes, die aus dem Arbeitsspeicher gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="0df5f-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0df5f-108">[out] Ein Puffer, der den Inhalt des Arbeitsspeichers empfängt.</span><span class="sxs-lookup"><span data-stu-id="0df5f-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="0df5f-109">[out] Ein Zeiger auf die Anzahl der Bytes, die in den angegebenen Puffer übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="0df5f-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0df5f-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0df5f-110">Remarks</span></span>  
 <span data-ttu-id="0df5f-111">Die `ReadMemory` -Methode ist hauptsächlich von Interop-Debuggen verwendet werden, um Speicherbereiche zu überprüfen, die durch den nicht verwalteten Teil der zu debuggenden Komponente verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0df5f-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="0df5f-112">Diese Methode kann auch verwendet werden, um Microsoft intermediate Language (MSIL)-Code und den systemeigenen JIT-kompilierten Code lesen.</span><span class="sxs-lookup"><span data-stu-id="0df5f-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="0df5f-113">Alle verwalteten Haltepunkte aus den Daten, die in zurückgegeben werden, entfernt werden die `buffer` Parameter.</span><span class="sxs-lookup"><span data-stu-id="0df5f-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="0df5f-114">Ohne Korrekturen durchgeführt werden, für die systemeigene Haltepunkte festlegen, indem Sie [ICorDebugProcess2:: SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="0df5f-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="0df5f-115">Keine der Prozessspeicher zwischengespeichert.</span><span class="sxs-lookup"><span data-stu-id="0df5f-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0df5f-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0df5f-116">Requirements</span></span>  
 <span data-ttu-id="0df5f-117">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0df5f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0df5f-118">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0df5f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0df5f-119">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0df5f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0df5f-120">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0df5f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>