---
title: ICorProfilerInfo2::GetClassLayout-Methode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b826e9c30fbf7007ac6b0093608ab7d926cc499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459152"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout-Methode
Ruft aus dem Arbeitsspeicher Informationen über das Layout der Felder ab, die durch die angegebene Klasse definiert sind . Das heißt, diese Methode ruft die Offsets der Felder der Klasse ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a>Parameter  
 `classID`  
 [in] Die ID der Klasse, für das Layout abgerufen werden soll.  
  
 `rFieldOffset`  
 [in, out] Ein Array von [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) Strukturen, von denen jede die Tokens und Offsets der Klassenfelder enthält.  
  
 `cFieldOffset`  
 [in] Die Größe des `rFieldOffset`-Arrays.  
  
 `pcFieldOffset`  
 [out] Ein Zeiger auf die Gesamtzahl der verfügbaren Elemente. Wenn `cFieldOffset` gleich 0 ist, gibt dieser Wert gibt die Anzahl von benötigten Elementen an.  
  
 `pulClassSize`  
 [out] Ein Zeiger auf einen Speicherort, der die Größe der Klasse in Bytes enthält.  
  
## <a name="remarks"></a>Hinweise  
 Die `GetClassLayout`-Methode gibt nur die von der Klasse selbst definierten Felder zurück. Wenn die übergeordnete Klasse der Klasse ebenfalls Felder definiert hat, muss der Profiler die `GetClassLayout`-Methode für die übergeordnete Klasse aufrufen, um diese Felder abzurufen.  
  
 Wenn Sie `GetClassLayout` mit Zeichenfolgenklassen verwenden, schlägt die Methode mit dem Fehlercode E_INVALIDARG fehl. Verwendung [ICorProfilerInfo2:: GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) beim Abrufen von Informationen über das Layout einer Zeichenfolge. Die `GetClassLayout`-Methode schlägt auch fehl, wenn sie mit einer Arrayklasse aufgerufen wird.  
  
 Nachdem `GetClassLayout` abgeschlossen ist, müssen Sie sicherstellen, dass der `rFieldOffset`-Puffer groß genug war, um alle verfügbaren `COR_FIELD_OFFSET`-Strukturen aufzunehmen. Vergleichen Sie hierzu den Wert, auf den `pcFieldOffset` verweist, mit der Größe von `rFieldOffset` dividiert durch die Größe einer `COR_FIELD_OFFSET`-Struktur. Wenn `rFieldOffset` nicht groß genug ist, weisen Sie einen größeren `rFieldOffset`-Puffer zu, aktualisieren Sie `cFieldOffset` mit der neuen Größe, und rufen Sie `GetClassLayout` erneut auf.  
  
 Alternativ können Sie zuerst `GetClassLayout` mit einem `rFieldOffset`-Puffer der Länge 0 (null) aufrufen, um die richtige Puffergröße zu ermitteln. Sie können die Puffergröße dann auf den Wert festlegen, der von `pcFieldOffset` zurückgegeben wurde, und `GetClassLayout` erneut aufrufen.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ICorProfilerInfo-Schnittstelle](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2-Schnittstelle](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Profilerstellungsschnittstellen](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilerstellung](../../../../docs/framework/unmanaged-api/profiling/index.md)
