---
title: CorElementType Enumeration1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorElementType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorElementType
helpviewer_keywords: CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8932e295aa1a6c6cf961e7b3a218e76984da02cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="corelementtype-enumeration1"></a><span data-ttu-id="36898-102">CorElementType Enumeration1</span><span class="sxs-lookup"><span data-stu-id="36898-102">CorElementType Enumeration1</span></span>
<span data-ttu-id="36898-103">Gibt an, eine common Language Runtime <xref:System.Type>, einen Typmodifizierer oder Informationen zu einem Typ in eine Metadatentypsignatur.</span><span class="sxs-lookup"><span data-stu-id="36898-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36898-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="36898-104">Syntax</span></span>  
  
```  
typedef enum CorElementType {  
    ELEMENT_TYPE_END            = 0x0,  
    ELEMENT_TYPE_VOID           = 0x1,  
    ELEMENT_TYPE_BOOLEAN        = 0x2,  
    ELEMENT_TYPE_CHAR           = 0x3,  
    ELEMENT_TYPE_I1             = 0x4,  
    ELEMENT_TYPE_U1             = 0x5,  
    ELEMENT_TYPE_I2             = 0x6,  
    ELEMENT_TYPE_U2             = 0x7,  
    ELEMENT_TYPE_I4             = 0x8,  
    ELEMENT_TYPE_U4             = 0x9,  
    ELEMENT_TYPE_I8             = 0xa,  
    ELEMENT_TYPE_U8             = 0xb,  
    ELEMENT_TYPE_R4             = 0xc,  
    ELEMENT_TYPE_R8             = 0xd,  
    ELEMENT_TYPE_STRING         = 0xe,  
  
    ELEMENT_TYPE_PTR            = 0xf,  
    ELEMENT_TYPE_BYREF          = 0x10,  
  
    ELEMENT_TYPE_VALUETYPE      = 0x11,  
    ELEMENT_TYPE_CLASS          = 0x12,  
    ELEMENT_TYPE_VAR            = 0x13,  
    ELEMENT_TYPE_ARRAY          = 0x14,  
    ELEMENT_TYPE_GENERICINST    = 0x15,  
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,  
  
    ELEMENT_TYPE_I              = 0x18,  
    ELEMENT_TYPE_U              = 0x19,  
    ELEMENT_TYPE_FNPTR          = 0x1B,  
    ELEMENT_TYPE_OBJECT         = 0x1C,  
    ELEMENT_TYPE_SZARRAY        = 0x1D,  
    ELEMENT_TYPE_MVAR           = 0x1e,  
  
    ELEMENT_TYPE_CMOD_REQD      = 0x1F,  
    ELEMENT_TYPE_CMOD_OPT       = 0x20,  
  
    ELEMENT_TYPE_INTERNAL       = 0x21,  
    ELEMENT_TYPE_MAX            = 0x22,  
  
    ELEMENT_TYPE_MODIFIER       = 0x40,  
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,  
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER  
  
} CorElementType;  
```  
  
## <a name="members"></a><span data-ttu-id="36898-105">Member</span><span class="sxs-lookup"><span data-stu-id="36898-105">Members</span></span>  
  
|<span data-ttu-id="36898-106">Member</span><span class="sxs-lookup"><span data-stu-id="36898-106">Member</span></span>|<span data-ttu-id="36898-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="36898-107">Description</span></span>|  
|------------|-----------------|  
|`ELEMENT_TYPE_END`|<span data-ttu-id="36898-108">Wird intern verwendet.</span><span class="sxs-lookup"><span data-stu-id="36898-108">Used internally.</span></span>|  
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="36898-109">Ein void-Typ.</span><span class="sxs-lookup"><span data-stu-id="36898-109">A void type.</span></span>|  
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="36898-110">Einem Boolean-Typ</span><span class="sxs-lookup"><span data-stu-id="36898-110">A Boolean type</span></span>|  
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="36898-111">Ein Zeichentyp.</span><span class="sxs-lookup"><span data-stu-id="36898-111">A character type.</span></span>|  
|`ELEMENT_TYPE_I1`|<span data-ttu-id="36898-112">Ein 1-Byte-Ganzzahl mit Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="36898-112">A signed 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_U1`|<span data-ttu-id="36898-113">Ein unsignierter 1-Byte-Ganzzahltyp.</span><span class="sxs-lookup"><span data-stu-id="36898-113">An unsigned 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_I2`|<span data-ttu-id="36898-114">Eine 2-Byte-Ganzzahl mit Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="36898-114">A signed 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_U2`|<span data-ttu-id="36898-115">Eine 2-Byte-Ganzzahl ohne Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="36898-115">An unsigned 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_I4`|<span data-ttu-id="36898-116">Eine 4-Byte-Ganzzahl mit Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="36898-116">A signed 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_U4`|<span data-ttu-id="36898-117">Eine 4-Byte-Ganzzahl ohne Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="36898-117">An unsigned 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_I8`|<span data-ttu-id="36898-118">Eine 8-Byte-Ganzzahl mit Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="36898-118">A signed 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_U8`|<span data-ttu-id="36898-119">Eine 8-Byte-Ganzzahl ohne Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="36898-119">An unsigned 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_R4`|<span data-ttu-id="36898-120">Eine 4-Byte-Gleitkommazahl.</span><span class="sxs-lookup"><span data-stu-id="36898-120">A 4-byte floating point.</span></span>|  
|`ELEMENT_TYPE_R8`|<span data-ttu-id="36898-121">Eine 8-Byte-Gleitkommazahl.</span><span class="sxs-lookup"><span data-stu-id="36898-121">An 8-byte floating point.</span></span>|  
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="36898-122">Ein Typ System.String.</span><span class="sxs-lookup"><span data-stu-id="36898-122">A System.String type.</span></span>|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="36898-123">Ein Typmodifizierer für einen Zeiger.</span><span class="sxs-lookup"><span data-stu-id="36898-123">A pointer type modifier.</span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="36898-124">Typmodifizierer Verweis.</span><span class="sxs-lookup"><span data-stu-id="36898-124">A reference type modifier.</span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="36898-125">Typmodifizierer Wert.</span><span class="sxs-lookup"><span data-stu-id="36898-125">A value type modifier.</span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="36898-126">Typmodifizierer Klasse.</span><span class="sxs-lookup"><span data-stu-id="36898-126">A class type modifier.</span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="36898-127">Ein Variablentyp Modifizierer der Klasse.</span><span class="sxs-lookup"><span data-stu-id="36898-127">A class variable type modifier.</span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="36898-128">Ein mehrdimensionales Arraytypmodifizierer.</span><span class="sxs-lookup"><span data-stu-id="36898-128">A multi-dimensional array type modifier.</span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="36898-129">Ein Typmodifizierer für generische Typen.</span><span class="sxs-lookup"><span data-stu-id="36898-129">A type modifier for generic types.</span></span>|  
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="36898-130">Ein typisierter Verweis.</span><span class="sxs-lookup"><span data-stu-id="36898-130">A typed reference.</span></span>|  
|`ELEMENT_TYPE_I`|<span data-ttu-id="36898-131">Die Größe einer systemeigenen Ganzzahl.</span><span class="sxs-lookup"><span data-stu-id="36898-131">Size of a native integer.</span></span>|  
|`ELEMENT_TYPE_U`|<span data-ttu-id="36898-132">Die Größe einer systemeigenen Ganzzahl ohne Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="36898-132">Size of an unsigned native integer.</span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="36898-133">Ein Zeiger auf eine Funktion.</span><span class="sxs-lookup"><span data-stu-id="36898-133">A pointer to a function.</span></span>|  
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="36898-134">Ein System.Object-Typ.</span><span class="sxs-lookup"><span data-stu-id="36898-134">A System.Object type.</span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="36898-135">Ein eindimensionales, 0 (null) Typmodifizierer Untergrenze Array.</span><span class="sxs-lookup"><span data-stu-id="36898-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="36898-136">Eine Methode Variablentyp-Modifizierer.</span><span class="sxs-lookup"><span data-stu-id="36898-136">A method variable type modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="36898-137">Eine C#-Sprache erforderlich Modifizierer.</span><span class="sxs-lookup"><span data-stu-id="36898-137">A C language required modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="36898-138">Eine C#-Sprache Optionaler Modifizierer.</span><span class="sxs-lookup"><span data-stu-id="36898-138">A C language optional modifier.</span></span>|  
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="36898-139">Wird intern verwendet.</span><span class="sxs-lookup"><span data-stu-id="36898-139">Used internally.</span></span>|  
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="36898-140">Ein ungültiger Typ.</span><span class="sxs-lookup"><span data-stu-id="36898-140">An invalid type.</span></span>|  
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="36898-141">Wird intern verwendet.</span><span class="sxs-lookup"><span data-stu-id="36898-141">Used internally.</span></span>|  
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="36898-142">Ein Typmodifizierer, der ein Sentinel für eine Liste der eine Variable Anzahl von Parametern ist.</span><span class="sxs-lookup"><span data-stu-id="36898-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|  
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="36898-143">Wird intern verwendet.</span><span class="sxs-lookup"><span data-stu-id="36898-143">Used internally.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36898-144">Hinweise</span><span class="sxs-lookup"><span data-stu-id="36898-144">Remarks</span></span>  
 <span data-ttu-id="36898-145">Der Typmodifizierer bilden die Grundlage für komplexe Typen darstellt.</span><span class="sxs-lookup"><span data-stu-id="36898-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="36898-146">Ein `CorElementType` Typwert-Modifizierer wird angewendet, auf den Wert, der durch den es in der Typsignatur unmittelbar folgt.</span><span class="sxs-lookup"><span data-stu-id="36898-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="36898-147">Der Wert, der `CorElementType` Typwert-Modifizierer kann eine `CorElementType` einfacher Werttyp, ein Metadatentoken, oder ein anderer Wert als in der folgenden Tabelle angegeben.</span><span class="sxs-lookup"><span data-stu-id="36898-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36898-148">Alle Zahlen (*Anzahl*, *Argumentanzahl*, *Metadatentoken*, *Rang*, *Anzahl*, und *gebunden*) werden als komprimierte ganze Zahlen gespeichert.</span><span class="sxs-lookup"><span data-stu-id="36898-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="36898-149">Finden Sie unter [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) auf die ECMA-Website für Details.</span><span class="sxs-lookup"><span data-stu-id="36898-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>  
  
|<span data-ttu-id="36898-150">Typmodifizierer</span><span class="sxs-lookup"><span data-stu-id="36898-150">Type modifier</span></span>|<span data-ttu-id="36898-151">Format</span><span class="sxs-lookup"><span data-stu-id="36898-151">Format</span></span>|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="36898-152">ELEMENT_TYPE_PTR < eine `CorElementType` Wert ></span><span class="sxs-lookup"><span data-stu-id="36898-152">ELEMENT_TYPE_PTR <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="36898-153">ELEMENT_TYPE_BYREF < eine `CorElementType` Wert ></span><span class="sxs-lookup"><span data-stu-id="36898-153">ELEMENT_TYPE_BYREF <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="36898-154">ELEMENT_TYPE_VALUETYPE < eine `mdTypeDef` Metadatentoken ></span><span class="sxs-lookup"><span data-stu-id="36898-154">ELEMENT_TYPE_VALUETYPE <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="36898-155">ELEMENT_TYPE_CLASS < eine `mdTypeDef` Metadatentoken ></span><span class="sxs-lookup"><span data-stu-id="36898-155">ELEMENT_TYPE_CLASS <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="36898-156">ELEMENT_TYPE_VAR \<Anzahl ></span><span class="sxs-lookup"><span data-stu-id="36898-156">ELEMENT_TYPE_VAR \<number></span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="36898-157">Einem < eine `CorElementType` Wert > \<Rang > \<count1 > \<bound1 >... \<CountN > \<BoundN ></span><span class="sxs-lookup"><span data-stu-id="36898-157">ELEMENT_TYPE_ARRAY <a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="36898-158">ELEMENT_TYPE_GENERICINST < eine `mdTypeDef` Metadatentoken > \<Argumentanzahl > \<arg1 >... \<ArgN ></span><span class="sxs-lookup"><span data-stu-id="36898-158">ELEMENT_TYPE_GENERICINST <an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="36898-159">ELEMENT_TYPE_FNPTR \<vollständige Signatur für die Funktion, einschließlich Aufrufkonvention ></span><span class="sxs-lookup"><span data-stu-id="36898-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="36898-160">ELEMENT_TYPE_SZARRAY < eine `CorElementType` Wert ></span><span class="sxs-lookup"><span data-stu-id="36898-160">ELEMENT_TYPE_SZARRAY <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="36898-161">ELEMENT_TYPE_MVAR \<Anzahl ></span><span class="sxs-lookup"><span data-stu-id="36898-161">ELEMENT_TYPE_MVAR \<number></span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="36898-162">ELEMENT_TYPE_ < eine `mdTypeRef` oder `mdTypeDef` Metadatentoken ></span><span class="sxs-lookup"><span data-stu-id="36898-162">ELEMENT_TYPE_<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="36898-163">E_T_CMOD_OPT < eine `mdTypeRef` oder `mdTypeDef` Metadatentoken ></span><span class="sxs-lookup"><span data-stu-id="36898-163">E_T_CMOD_OPT <a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36898-164">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="36898-164">Requirements</span></span>  
 <span data-ttu-id="36898-165">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36898-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36898-166">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="36898-166">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="36898-167">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36898-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36898-168">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="36898-168">See Also</span></span>  
 [<span data-ttu-id="36898-169">Metadatenenumerationen</span><span class="sxs-lookup"><span data-stu-id="36898-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)