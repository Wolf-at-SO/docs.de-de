---
title: Veraltete CLR-Hostingfunktionen
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9530fecb4f2ca6f59d165e49c282320966fd2fa8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="d150f-102">Veraltete CLR-Hostingfunktionen</span><span class="sxs-lookup"><span data-stu-id="d150f-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="d150f-103">In diesem Abschnitt werden die nicht verwalteten globalen statischen Funktionen beschrieben, die von früheren Versionen der Hosting-API verwendet wurden.</span><span class="sxs-lookup"><span data-stu-id="d150f-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="d150f-104">Mit Ausnahme von Infrastrukturfunktionen (`_Cor*`-Funktionen), die nur von .NET Framework verwendet werden, sind diese Funktionen in [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="d150f-105">Aktivierungsfunktionen</span><span class="sxs-lookup"><span data-stu-id="d150f-105">Activation functions</span></span>  
 [<span data-ttu-id="d150f-106">ClrCreateManagedInstance-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-106">ClrCreateManagedInstance Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="d150f-107">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-107">Deprecated.</span></span> <span data-ttu-id="d150f-108">Erstellt eine Instanz des angegebenen verwalteten Typs.</span><span class="sxs-lookup"><span data-stu-id="d150f-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="d150f-109">CoInitializeCor-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-109">CoInitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 <span data-ttu-id="d150f-110">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-110">Obsolete.</span></span> <span data-ttu-id="d150f-111">Um die common Language Runtime (CLR) zu initialisieren, verwenden Sie entweder [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) oder [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="d150f-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="d150f-112">CoInitializeEE-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-112">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 <span data-ttu-id="d150f-113">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-113">Deprecated.</span></span> <span data-ttu-id="d150f-114">Stellt sicher, dass das CLR-Ausführungsmodul in einen Prozess geladen wird.</span><span class="sxs-lookup"><span data-stu-id="d150f-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="d150f-115">Verwenden der [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) Methode stattdessen.</span><span class="sxs-lookup"><span data-stu-id="d150f-115">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="d150f-116">CorBindToCurrentRuntime-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-116">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 <span data-ttu-id="d150f-117">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-117">Deprecated.</span></span> <span data-ttu-id="d150f-118">Lädt die Common Language Runtime (CLR) in einen Prozess, indem in einer XML-Datei gespeicherte Versionsinformationen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d150f-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="d150f-119">CorBindToRuntime-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-119">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 <span data-ttu-id="d150f-120">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-120">Deprecated.</span></span> <span data-ttu-id="d150f-121">Ermöglicht es nicht verwalteten Hosts, die CLR in einen Prozess zu laden.</span><span class="sxs-lookup"><span data-stu-id="d150f-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="d150f-122">CorBindToRuntimeByCfg-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-122">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="d150f-123">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-123">Deprecated.</span></span> <span data-ttu-id="d150f-124">Lädt die CLR in einen Prozess, indem aus einer XML-Datei gelesene Versionsinformationen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d150f-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="d150f-125">CorBindToRuntimeEx-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-125">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 <span data-ttu-id="d150f-126">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-126">Deprecated.</span></span> <span data-ttu-id="d150f-127">Ermöglicht nicht verwalteten Hosts, die CLR in einen Prozess zu laden, und ermöglicht Ihnen, Flags festzulegen, um das Verhalten der CLR anzugeben.</span><span class="sxs-lookup"><span data-stu-id="d150f-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="d150f-128">CorBindToRuntimeHost-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 <span data-ttu-id="d150f-129">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-129">Deprecated.</span></span> <span data-ttu-id="d150f-130">Ermöglicht Hosts, eine angegebene Version der CLR in einen Prozess zu laden.</span><span class="sxs-lookup"><span data-stu-id="d150f-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="d150f-131">GetCORRequiredVersion-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-131">GetCORRequiredVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 <span data-ttu-id="d150f-132">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-132">Deprecated.</span></span> <span data-ttu-id="d150f-133">Ruft die erforderliche CLR-Versionsnummer ab.</span><span class="sxs-lookup"><span data-stu-id="d150f-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="d150f-134">GetCORSystemDirectory-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-134">GetCORSystemDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 <span data-ttu-id="d150f-135">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-135">Deprecated.</span></span> <span data-ttu-id="d150f-136">Gibt das Installationsverzeichnis der CLR zurück, die in den Prozess geladen wird.</span><span class="sxs-lookup"><span data-stu-id="d150f-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="d150f-137">GetRealProcAddress-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-137">GetRealProcAddress Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 <span data-ttu-id="d150f-138">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-138">Deprecated.</span></span> <span data-ttu-id="d150f-139">Ruft die Adresse der angegebenen Funktion ab, die aus der letzten installierten Version der CLR exportiert wird.</span><span class="sxs-lookup"><span data-stu-id="d150f-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="d150f-140">GetRequestedRuntimeInfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-140">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="d150f-141">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-141">Deprecated.</span></span> <span data-ttu-id="d150f-142">Ruft Version und Verzeichnisinformationen über die CLR ab, die von einer Anwendung angefordert wurden.</span><span class="sxs-lookup"><span data-stu-id="d150f-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="d150f-143">CLR-Versionsfunktionen</span><span class="sxs-lookup"><span data-stu-id="d150f-143">CLR version functions</span></span>  
 <span data-ttu-id="d150f-144">Die Funktionen in diesem Abschnitt geben eine CLR-Version zurück; sie aktivieren nicht die CLR.</span><span class="sxs-lookup"><span data-stu-id="d150f-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="d150f-145">GetCORVersion-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-145">GetCORVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 <span data-ttu-id="d150f-146">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-146">Deprecated.</span></span> <span data-ttu-id="d150f-147">Gibt die Versionsnummer der CLR zurück, die im aktuellen Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d150f-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="d150f-148">GetFileVersion-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-148">GetFileVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 <span data-ttu-id="d150f-149">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-149">Deprecated.</span></span> <span data-ttu-id="d150f-150">Ruft mithilfe des angegebenen Puffers die Versionsinformationen der CLR für die angegebene Datei ab.</span><span class="sxs-lookup"><span data-stu-id="d150f-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="d150f-151">GetRequestedRuntimeVersion-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-151">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 <span data-ttu-id="d150f-152">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-152">Deprecated.</span></span> <span data-ttu-id="d150f-153">Ruft die Versionsnummer der CLR ab, die von der angegebenen Anwendung angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="d150f-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="d150f-154">Wenn diese Version nicht installiert ist, wird die letzte installierte Version vor der angeforderten Version abgerufen.</span><span class="sxs-lookup"><span data-stu-id="d150f-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="d150f-155">GetRequestedRuntimeVersionForCLSID-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="d150f-156">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-156">Deprecated.</span></span> <span data-ttu-id="d150f-157">Ruft die entsprechenden CLR-Versionsinformationen für die Klasse mit der angegebenen CLSID ab.</span><span class="sxs-lookup"><span data-stu-id="d150f-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="d150f-158">GetVersionFromProcess-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-158">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 <span data-ttu-id="d150f-159">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-159">Deprecated.</span></span> <span data-ttu-id="d150f-160">Ruft die Versionsnummer der CLR ab, die dem angegebenen Prozesshandle zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="d150f-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="d150f-161">LockClrVersion-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-161">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 <span data-ttu-id="d150f-162">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-162">Deprecated.</span></span> <span data-ttu-id="d150f-163">Ermöglicht dem Host, zu bestimmen, welche Version der CLR innerhalb des Prozesses verwendet werden soll, bevor die CLR explizit initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="d150f-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="d150f-164">Hostingfunktionen</span><span class="sxs-lookup"><span data-stu-id="d150f-164">Hosting functions</span></span>  
 [<span data-ttu-id="d150f-165">CallFunctionShim-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-165">CallFunctionShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 <span data-ttu-id="d150f-166">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-166">Deprecated.</span></span> <span data-ttu-id="d150f-167">Ruft eine Funktion mit dem angegebenen Namen und den angegebenen Parametern in der angegebenen Bibliothek auf.</span><span class="sxs-lookup"><span data-stu-id="d150f-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="d150f-168">CoEEShutDownCOM-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-168">CoEEShutDownCOM Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 <span data-ttu-id="d150f-169">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-169">Deprecated.</span></span> <span data-ttu-id="d150f-170">Entlädt eine COM-Assembly aus dem Prozess.</span><span class="sxs-lookup"><span data-stu-id="d150f-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="d150f-171">CorExitProcess-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-171">CorExitProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 <span data-ttu-id="d150f-172">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-172">Deprecated.</span></span> <span data-ttu-id="d150f-173">Beendet den aktuellen nicht verwalteten Prozess.</span><span class="sxs-lookup"><span data-stu-id="d150f-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="d150f-174">CorLaunchApplication-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-174">CorLaunchApplication Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 <span data-ttu-id="d150f-175">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-175">Deprecated.</span></span> <span data-ttu-id="d150f-176">Startet die Anwendung im angegebenen Netzwerkpfad, wobei die angegebenen Manifeste und sonstigen Anwendungsdaten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d150f-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="d150f-177">CorMarkThreadInThreadPool-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-177">CorMarkThreadInThreadPool Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="d150f-178">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-178">Deprecated.</span></span> <span data-ttu-id="d150f-179">Markiert den aktuell ausgeführten Thread aus dem Threadpool für die Ausführung von verwaltetem Code.</span><span class="sxs-lookup"><span data-stu-id="d150f-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="d150f-180">Ab .NET Framework Version 2.0 besitzt diese Funktion keine Auswirkungen.</span><span class="sxs-lookup"><span data-stu-id="d150f-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="d150f-181">Sie ist nicht erforderlich und kann aus dem Code entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="d150f-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="d150f-182">CoUninitializeCor-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-182">CoUninitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 <span data-ttu-id="d150f-183">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-183">Obsolete.</span></span> <span data-ttu-id="d150f-184">Die CLR kann nicht aus einem Prozess entladen werden.</span><span class="sxs-lookup"><span data-stu-id="d150f-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="d150f-185">CoUninitializeEE-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-185">CoUninitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 <span data-ttu-id="d150f-186">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="d150f-187">CreateDebuggingInterfaceFromVersion-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-187">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="d150f-188">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-188">Deprecated.</span></span> <span data-ttu-id="d150f-189">Erstellt ein [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) -Objekt auf Grundlage der angegebenen Versionsinformationen.</span><span class="sxs-lookup"><span data-stu-id="d150f-189">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="d150f-190">CreateICeeFileGen-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-190">CreateICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 <span data-ttu-id="d150f-191">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-191">Deprecated.</span></span> <span data-ttu-id="d150f-192">Erstellt ein [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) Objekt.</span><span class="sxs-lookup"><span data-stu-id="d150f-192">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="d150f-193">DestroyICeeFileGen-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-193">DestroyICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 <span data-ttu-id="d150f-194">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-194">Deprecated.</span></span> <span data-ttu-id="d150f-195">Zerstört ein [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) Objekt.</span><span class="sxs-lookup"><span data-stu-id="d150f-195">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="d150f-196">FExecuteInAppDomainCallback-Funktionszeiger</span><span class="sxs-lookup"><span data-stu-id="d150f-196">FExecuteInAppDomainCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="d150f-197">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-197">Deprecated.</span></span> <span data-ttu-id="d150f-198">Zeigt auf eine Funktion, die die CLR zum Ausführen von verwaltetem Code aufruft.</span><span class="sxs-lookup"><span data-stu-id="d150f-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="d150f-199">FLockClrVersionCallback-Funktionszeiger</span><span class="sxs-lookup"><span data-stu-id="d150f-199">FLockClrVersionCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="d150f-200">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-200">Deprecated.</span></span> <span data-ttu-id="d150f-201">Zeigt auf eine Funktion, die die CLR aufruft, um den Host zu benachrichtigen, dass die Initialisierung gestartet oder abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="d150f-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="d150f-202">GetCLRIdentityManager-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-202">GetCLRIdentityManager Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 <span data-ttu-id="d150f-203">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-203">Deprecated.</span></span> <span data-ttu-id="d150f-204">Ruft einen Zeiger auf eine Schnittstelle ab, die es der CLR ermöglicht, Identitäten zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="d150f-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="d150f-205">LoadLibraryShim-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-205">LoadLibraryShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 <span data-ttu-id="d150f-206">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-206">Deprecated.</span></span> <span data-ttu-id="d150f-207">Lädt die angegebene Version einer .NET Framework-DLL.</span><span class="sxs-lookup"><span data-stu-id="d150f-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="d150f-208">LoadStringRC-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-208">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 <span data-ttu-id="d150f-209">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-209">Deprecated.</span></span> <span data-ttu-id="d150f-210">Übersetzt einen HRESULT-Wert in eine Fehlermeldung, wobei die Standardkultur des aktuellen Threads verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d150f-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="d150f-211">LoadStringRCEx-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-211">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 <span data-ttu-id="d150f-212">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-212">Deprecated.</span></span> <span data-ttu-id="d150f-213">Übersetzt einen HRESULT-Wert in eine entsprechende Fehlermeldung für die angegebene Kultur.</span><span class="sxs-lookup"><span data-stu-id="d150f-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="d150f-214">LPOVERLAPPED_COMPLETION_ROUTINE-Funktionszeiger</span><span class="sxs-lookup"><span data-stu-id="d150f-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="d150f-215">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-215">Deprecated.</span></span> <span data-ttu-id="d150f-216">Zeigt auf eine Funktion, die den Host benachrichtigt, wenn eine überlappende (d. h. asynchrone) E/A auf einem Gerät abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="d150f-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="d150f-217">LPTHREAD_START_ROUTINE-Funktionszeiger</span><span class="sxs-lookup"><span data-stu-id="d150f-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="d150f-218">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-218">Deprecated.</span></span> <span data-ttu-id="d150f-219">Zeigt auf eine Funktion, die den Host benachrichtigt, dass eine Threadausführung begonnen hat.</span><span class="sxs-lookup"><span data-stu-id="d150f-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="d150f-220">RunDll32ShimW-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-220">RunDll32ShimW Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 <span data-ttu-id="d150f-221">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-221">Deprecated.</span></span> <span data-ttu-id="d150f-222">Führt den angegebenen Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="d150f-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="d150f-223">WAITORTIMERCALLBACK-Funktionszeiger</span><span class="sxs-lookup"><span data-stu-id="d150f-223">WAITORTIMERCALLBACK Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 <span data-ttu-id="d150f-224">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="d150f-224">Deprecated.</span></span> <span data-ttu-id="d150f-225">Zeigt auf eine Funktion, die den Host benachrichtigt, dass ein Wait-Handle signalisiert wurde oder das Zeitlimit überschritten hat.</span><span class="sxs-lookup"><span data-stu-id="d150f-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="d150f-226">Infrastrukturfunktionen</span><span class="sxs-lookup"><span data-stu-id="d150f-226">Infrastructure functions</span></span>  
 <span data-ttu-id="d150f-227">Die Funktionen in diesem Abschnitt gelten nur für .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d150f-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="d150f-228">_CorDllMain-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-228">_CorDllMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 <span data-ttu-id="d150f-229">Initialisiert die CLR, sucht den verwalteten Einstiegspunkt im CLR-Header der DLL-Assembly und startet die Ausführung.</span><span class="sxs-lookup"><span data-stu-id="d150f-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="d150f-230">_CorExeMain-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-230">_CorExeMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 <span data-ttu-id="d150f-231">Initialisiert die CLR, sucht den verwalteten Einstiegspunkt im CLR-Header der ausführbaren Assembly und startet die Ausführung.</span><span class="sxs-lookup"><span data-stu-id="d150f-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="d150f-232">_CorExeMain2-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-232">_CorExeMain2 Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 <span data-ttu-id="d150f-233">Führt den Einstiegspunkt im angegebenen Speicherabbildcode aus.</span><span class="sxs-lookup"><span data-stu-id="d150f-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="d150f-234">Diese Funktion wird vom Betriebssystemladeprogramm aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="d150f-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="d150f-235">_CorImageUnloading-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-235">_CorImageUnloading Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 <span data-ttu-id="d150f-236">Benachrichtigt das Ladeprogramm, wenn die Images des verwalteten Moduls entladen werden.</span><span class="sxs-lookup"><span data-stu-id="d150f-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="d150f-237">_CorValidateImage-Funktion</span><span class="sxs-lookup"><span data-stu-id="d150f-237">_CorValidateImage Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 <span data-ttu-id="d150f-238">Überprüft Images des verwalteten Moduls, und benachrichtigt das Betriebssystemladeprogramm, nachdem sie geladen wurden.</span><span class="sxs-lookup"><span data-stu-id="d150f-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d150f-239">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d150f-239">See Also</span></span>  
 [<span data-ttu-id="d150f-240">.NET Framework 4 Hosten von globalen statischen Funktionen</span><span class="sxs-lookup"><span data-stu-id="d150f-240">.NET Framework 4 Hosting Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 