---
title: CorDebugEHClause-Struktur
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugEHClause
api_location: mscordbi.dll
api_type: COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 154bbe14a14d34c0d998e3192a70a96b9922f32c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="cff26-102">CorDebugEHClause-Struktur</span><span class="sxs-lookup"><span data-stu-id="cff26-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="cff26-103">[Wird nur in .NET Framework 4.5.2 und neueren Versionen unterstützt]</span><span class="sxs-lookup"><span data-stu-id="cff26-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cff26-104">Stellt eine Ausnahmebehandlung (Exception Handling, EH)-Klausel für einen bestimmten Intermediate Language (IL)-Codeabschnitt dar.</span><span class="sxs-lookup"><span data-stu-id="cff26-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff26-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cff26-105">Syntax</span></span>  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a><span data-ttu-id="cff26-106">Member</span><span class="sxs-lookup"><span data-stu-id="cff26-106">Members</span></span>  
  
|<span data-ttu-id="cff26-107">Member</span><span class="sxs-lookup"><span data-stu-id="cff26-107">Member</span></span>|<span data-ttu-id="cff26-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cff26-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="cff26-109">Ein Bitfeld, das die Ausnahmeinformationen in der EH-Klausel beschreibt.</span><span class="sxs-lookup"><span data-stu-id="cff26-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="cff26-110">Weitere Informationen finden Sie im Abschnitt "Hinweise".</span><span class="sxs-lookup"><span data-stu-id="cff26-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="cff26-111">Der Offset, in Bytes, des `try`-Blocks vom Beginn des Methodentextes.</span><span class="sxs-lookup"><span data-stu-id="cff26-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="cff26-112">Die Länge, in Bytes, des `try`-Blocks.</span><span class="sxs-lookup"><span data-stu-id="cff26-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="cff26-113">Der Speicherort des Handlers für diesen `try`-Block.</span><span class="sxs-lookup"><span data-stu-id="cff26-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="cff26-114">Die Größe des Handlercodes in Bytes.</span><span class="sxs-lookup"><span data-stu-id="cff26-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="cff26-115">Der Metadatentoken für einen typenbasierten Ausnahmehandler.</span><span class="sxs-lookup"><span data-stu-id="cff26-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="cff26-116">Der Offset, in Bytes, vom Beginn des Methodentextes für einen filterbasierten Ausnahmehandler.</span><span class="sxs-lookup"><span data-stu-id="cff26-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cff26-117">Hinweise</span><span class="sxs-lookup"><span data-stu-id="cff26-117">Remarks</span></span>  
 <span data-ttu-id="cff26-118">Ein Array von `CoreDebugEHClause` Werte wird zurückgegeben, durch die [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) Methode.</span><span class="sxs-lookup"><span data-stu-id="cff26-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="cff26-119">Die Informationen der EH-Klausel werden durch die CLI-Spezifikation definiert.</span><span class="sxs-lookup"><span data-stu-id="cff26-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="cff26-120">Weitere Informationen finden Sie unter [Standard ECMA-355: Common Language Infrastructure (CLI), 6. Edition](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="cff26-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="cff26-121">Das `flags`-Feld kann die folgenden Flags enthalten.</span><span class="sxs-lookup"><span data-stu-id="cff26-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="cff26-122">Beachten Sie, dass diese nicht in CorDebug.idl oder CorDebug.h definiert sind.</span><span class="sxs-lookup"><span data-stu-id="cff26-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="cff26-123">Flag</span><span class="sxs-lookup"><span data-stu-id="cff26-123">Flag</span></span>|<span data-ttu-id="cff26-124">Wert</span><span class="sxs-lookup"><span data-stu-id="cff26-124">Value</span></span>|<span data-ttu-id="cff26-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cff26-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="cff26-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="cff26-126">0x00000000</span></span>|<span data-ttu-id="cff26-127">Eine typisierte Ausnahmeklausel.</span><span class="sxs-lookup"><span data-stu-id="cff26-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="cff26-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="cff26-128">0x00000001</span></span>|<span data-ttu-id="cff26-129">Ein Ausnahmefilter und eine Handlerklausel.</span><span class="sxs-lookup"><span data-stu-id="cff26-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="cff26-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="cff26-130">0x00000002</span></span>|<span data-ttu-id="cff26-131">Eine `finally`-Klausel.</span><span class="sxs-lookup"><span data-stu-id="cff26-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="cff26-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="cff26-132">0x00000004</span></span>|<span data-ttu-id="cff26-133">Eine fault-Klausel (eine `finally`-Klausel, die nur aufgerufen wird, wenn eine Ausnahme ausgelöst wird).</span><span class="sxs-lookup"><span data-stu-id="cff26-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cff26-134">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="cff26-134">Requirements</span></span>  
 <span data-ttu-id="cff26-135">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cff26-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff26-136">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cff26-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cff26-137">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cff26-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cff26-138">**.NET Framework-Versionen:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cff26-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff26-139">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cff26-139">See Also</span></span>  
 [<span data-ttu-id="cff26-140">GetEHClauses-Methode</span><span class="sxs-lookup"><span data-stu-id="cff26-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)  
 [<span data-ttu-id="cff26-141">Debuggen von Strukturen</span><span class="sxs-lookup"><span data-stu-id="cff26-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)