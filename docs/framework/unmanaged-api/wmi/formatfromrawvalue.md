---
title: FormatFromRawValue-Funktion (Referenz zur nicht verwalteten API)
description: FormatFromRawValue-Funktion konvertiert rohleistungsdaten mehr in einem angegebenen Format.
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95ef445d41672c5c2895bd7115afb6a73a57e8f9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086136"
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue-Funktion
Konvertiert einen Rohdatenleistungswert in das angegebene Format oder zwei Rohdatenleistungswerte, wenn die Formatkonvertierung zeitabhängig ist.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntax  
  
```  
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```  

## <a name="parameters"></a>Parameter

`dwCounterType`  
[in] Der Leistungsindikator-Typ. Eine Liste der Indikatortypen, finden Sie unter [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType` kann jeder Typ Leistungsindikator, mit Ausnahme von sein `PERF_LARGE_RAW_FRACTION` und `PERF_LARGE_RAW_BASE`. 

`dwFormat`  
[in] Das Format, die die unformatierte Leistungsdaten konvertiert werden soll. Es kann eine der folgenden Werte sein:

|Konstante  |Wert  |Beschreibung |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Geben Sie den berechneten Wert als einen Gleitkommawert mit doppelter Genauigkeit zurück. | 
| `PDH_FMT_LARGE` | 0x00000400 | Geben Sie den berechneten Wert als eine 64-Bit-Ganzzahl zurück. |
| `PDH_FMT_LONG` | 0x00000100 | Geben Sie den berechneten Wert als eine 32-Bit-Ganzzahl zurück. |

Die vorherigen Werte kann ORed mit einem der folgenden Flags, die Skalierung möglich:

|Konstante  |Wert  |Beschreibung |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Skalierungsfaktoren des Zählers werden nicht angewendet werden. |
| `PDH_FMT_1000` | 0x00002000 | Multiplizieren Sie den endgültigen Wert von 1.000 ein. | 

`pTimeBase`  
[in] Ein Zeiger auf die Basis, bei Bedarf für die formatkonvertierung. Wenn Basis Uhrzeitinformationen nicht für die formatkonvertierung erforderlich ist, wird der Wert dieses Parameters ignoriert.

`pRawValue1` [in] Ein Zeiger auf eine [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) -Struktur, die einen rohleistung-Wert darstellt.

`pRawValue2` [in] Ein Zeiger auf eine [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) Struktur, die einen zweiten rohleistung-Wert darstellt. Dieser Parameter sollte sein, wenn Sie ein zweiter rohleistung bei der Wert nicht erforderlich ist, `null`.

`pFmtValue` [out] Ein Zeiger auf eine [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) Struktur, die dem Wert für die formatierte empfängt.

## <a name="return-value"></a>Rückgabewert

Die folgenden Werte werden von dieser Funktion zurückgegeben:

|Konstante  |Wert  |Beschreibung  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | Der Funktionsaufruf ist erfolgreich. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Ein erforderliches Argument ist nicht vorhanden oder falsch. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Das Handle ist kein gültiges PDH-Objekt. |
  
## <a name="remarks"></a>Hinweise

Diese Funktion umschließt einen Aufruf der [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) Funktion.

## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Bibliothek:** "PerfCounter.dll"  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Siehe auch  
[WMI und Leistungsindikatoren (Referenz zur nicht verwalteten API)](index.md)
