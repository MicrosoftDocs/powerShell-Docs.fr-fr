---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-wmimethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WmiMethod
ms.openlocfilehash: e9743488e86429e5cc3252162e51268a7978b79d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "93205282"
---
# <span data-ttu-id="4e350-103">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="4e350-103">Invoke-WmiMethod</span></span>

## <span data-ttu-id="4e350-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4e350-104">SYNOPSIS</span></span>
<span data-ttu-id="4e350-105">Appelle les méthodes WMI.</span><span class="sxs-lookup"><span data-stu-id="4e350-105">Calls WMI methods.</span></span>

## <span data-ttu-id="4e350-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e350-106">SYNTAX</span></span>

### <span data-ttu-id="4e350-107">classe (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4e350-107">class (Default)</span></span>

```
Invoke-WmiMethod [-Class] <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e350-108">object</span><span class="sxs-lookup"><span data-stu-id="4e350-108">object</span></span>

```
Invoke-WmiMethod -InputObject <ManagementObject> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e350-109">path</span><span class="sxs-lookup"><span data-stu-id="4e350-109">path</span></span>

```
Invoke-WmiMethod -Path <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e350-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="4e350-110">WQLQuery</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e350-111">query</span><span class="sxs-lookup"><span data-stu-id="4e350-111">query</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e350-112">list</span><span class="sxs-lookup"><span data-stu-id="4e350-112">list</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4e350-113">Description</span><span class="sxs-lookup"><span data-stu-id="4e350-113">DESCRIPTION</span></span>

<span data-ttu-id="4e350-114">L' `Invoke-WmiMethod` applet de commande appelle les méthodes des objets Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="4e350-114">The `Invoke-WmiMethod` cmdlet calls the methods of Windows Management Instrumentation (WMI) objects.</span></span>

<span data-ttu-id="4e350-115">Les nouvelles applets de commande Common Information Model (CIM), introduites dans Windows PowerShell 3,0, effectuent les mêmes tâches que les applets de commande WMI.</span><span class="sxs-lookup"><span data-stu-id="4e350-115">New Common Information Model (CIM) cmdlets, introduced in Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="4e350-116">Les applets de commande CIM sont conformes aux normes WS-Management (WSMan) et à la norme CIM, qui permet aux cmdlets d’utiliser les mêmes techniques pour gérer les ordinateurs Windows et ceux qui exécutent d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4e350-116">The CIM cmdlets comply with WS-Management (WSMan) standards and with the CIM standard, which enables the cmdlets to use the same techniques to manage Windows computers and those running other operating systems.</span></span> <span data-ttu-id="4e350-117">Au lieu d’utiliser `Invoke-WmiMethod` , envisagez d’utiliser [Invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md).</span><span class="sxs-lookup"><span data-stu-id="4e350-117">Instead of using `Invoke-WmiMethod`, consider using [Invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md).</span></span>

## <span data-ttu-id="4e350-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4e350-118">EXAMPLES</span></span>

### <span data-ttu-id="4e350-119">Exemple 1 : répertorier l’ordre requis des objets WMI</span><span class="sxs-lookup"><span data-stu-id="4e350-119">Example 1: List the required order of WMI objects</span></span>

```powershell
([wmiclass]'Win32_Volume').GetMethodParameters('Format')
```

```Output
__GENUS           : 2
__CLASS           : __PARAMETERS
__SUPERCLASS      :
__DYNASTY         : __PARAMETERS
__RELPATH         :
__PROPERTY_COUNT  : 6
__DERIVATION      : {}
__SERVER          :
__NAMESPACE       :
__PATH            :
ClusterSize       : 0
EnableCompression : False
FileSystem        : NTFS
Label             :
QuickFormat       : False
Version           : 0
PSComputerName    :
```

<span data-ttu-id="4e350-120">Cette commande répertorie l’ordre requis des objets.</span><span class="sxs-lookup"><span data-stu-id="4e350-120">This command lists the required order of the objects.</span></span> <span data-ttu-id="4e350-121">L’appel de WMI dans PowerShell 3.0 diffère des autres méthodes et nécessite que les valeurs d’objets soient entrées dans un ordre spécifique.</span><span class="sxs-lookup"><span data-stu-id="4e350-121">To invoke WMI in PowerShell 3.0 differs from alternate methods, and requires that object values are entered in a specific order.</span></span>

### <span data-ttu-id="4e350-122">Exemple 2 : démarrer une instance d’une application</span><span class="sxs-lookup"><span data-stu-id="4e350-122">Example 2: Start an instance of an application</span></span>

```powershell
([Wmiclass]'Win32_Process').GetMethodParameters('Create')
```

```Output
__GENUS                   : 2
__CLASS                   : __PARAMETERS
__SUPERCLASS              :
__DYNASTY                 : __PARAMETERS
__RELPATH                 :
__PROPERTY_COUNT          : 3
__DERIVATION              : {}
__SERVER                  :
__NAMESPACE               :
__PATH                    :
CommandLine               :
CurrentDirectory          :
ProcessStartupInformation :
PSComputerName            :
```

```powershell
Invoke-WmiMethod -Path win32_process -Name create -ArgumentList notepad.exe
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 2
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ProcessId        : 11312
ReturnValue      : 0
PSComputerName   :
```

<span data-ttu-id="4e350-123">Cette commande démarre une instance du bloc-notes en appelant la `Create` méthode de la classe **Win32_Process** .</span><span class="sxs-lookup"><span data-stu-id="4e350-123">This command starts an instance of Notepad by calling the `Create` method of the **Win32_Process** class.</span></span>

<span data-ttu-id="4e350-124">La propriété **returnValue** est remplie avec un 0 et la propriété **ProcessID** est remplie avec un entier (numéro d’ID de processus suivant) si la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="4e350-124">The **ReturnValue** property is populated with a 0, and the **ProcessId** property is populated with an integer (the next process ID number) if the command is completed.</span></span>

### <span data-ttu-id="4e350-125">Exemple 3 : renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="4e350-125">Example 3: Rename a file</span></span>

```powershell
Invoke-WmiMethod -Path "CIM_DataFile.Name='C:\scripts\test.txt'" -Name Rename -ArgumentList "C:\scripts\test_bu.txt"
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ReturnValue      : 0
```

<span data-ttu-id="4e350-126">Cette commande renomme un fichier.</span><span class="sxs-lookup"><span data-stu-id="4e350-126">This command renames a file.</span></span> <span data-ttu-id="4e350-127">Elle utilise le paramètre **path** pour référencer une instance de la classe **CIM_Datafile** .</span><span class="sxs-lookup"><span data-stu-id="4e350-127">It uses the **Path** parameter to reference an instance of the **CIM_DataFile** class.</span></span> <span data-ttu-id="4e350-128">Elle applique ensuite la méthode Rename à cette instance particulière.</span><span class="sxs-lookup"><span data-stu-id="4e350-128">Then, it applies the Rename method to that particular instance.</span></span>

<span data-ttu-id="4e350-129">La propriété **returnValue** est remplie avec un 0 si la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="4e350-129">The **ReturnValue** property is populated with a 0 if the command is completed.</span></span>

### <span data-ttu-id="4e350-130">Exemple 4 : passage d’un tableau de valeurs à l’aide de `-ArgumentList`</span><span class="sxs-lookup"><span data-stu-id="4e350-130">Example 4: Passing an array of values using `-ArgumentList`</span></span>

<span data-ttu-id="4e350-131">Exemple utilisant un tableau d’objets `$binSD` suivi d’une `$null` valeur.</span><span class="sxs-lookup"><span data-stu-id="4e350-131">An example using an array of objects `$binSD` followed by a `$null` value.</span></span>

```powershell
$acl = get-acl test.txt
$binSD = $acl.GetSecurityDescriptorBinaryForm()
Invoke-WmiMethod -class Win32_SecurityDescriptorHelper -Name BinarySDToSDDL -ArgumentList $binSD, $null
```

## <span data-ttu-id="4e350-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e350-132">PARAMETERS</span></span>

### <span data-ttu-id="4e350-133">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="4e350-133">-ArgumentList</span></span>

<span data-ttu-id="4e350-134">Spécifie les paramètres à passer à la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="4e350-134">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="4e350-135">La valeur de ce paramètre doit être un tableau d’objets et doit apparaître dans l’ordre requis par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="4e350-135">The value of this parameter must be an array of objects, and they must appear in the order required by the called method.</span></span> <span data-ttu-id="4e350-136">L' `Invoke-CimCommand` applet de commande n’a pas ces limitations.</span><span class="sxs-lookup"><span data-stu-id="4e350-136">The `Invoke-CimCommand` cmdlet does not have these limitations.</span></span>

<span data-ttu-id="4e350-137">Pour déterminer l’ordre dans lequel répertorier ces objets, exécutez la `GetMethodParameters()` méthode sur la classe WMI, comme illustré dans l’exemple 1, à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="4e350-137">To determine the order in which to list those objects, run the `GetMethodParameters()` method on the WMI class, as illustrated in Example 1, near the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e350-138">si la première valeur est un tableau qui contient plusieurs éléments, une seconde valeur $null est requise.</span><span class="sxs-lookup"><span data-stu-id="4e350-138">If the first value is an array that contains more than one element, a second value of $null is required.</span></span> <span data-ttu-id="4e350-139">Sinon, la commande génère une erreur, par exemple « Impossible d’effectuer un cast d’un objet de type ’System.Byte’ en type ’System.Array’ ».</span><span class="sxs-lookup"><span data-stu-id="4e350-139">Otherwise, the command generates an error, such as "Unable to cast object of type 'System.Byte' to type 'System.Array'.".</span></span> <span data-ttu-id="4e350-140">Consultez l’exemple 4 ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="4e350-140">See example 4 above.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: class, object, path
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-141">-AsJob</span><span class="sxs-lookup"><span data-stu-id="4e350-141">-AsJob</span></span>

<span data-ttu-id="4e350-142">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="4e350-142">Indicates that this cmdlet runs the command as a background job.</span></span> <span data-ttu-id="4e350-143">Utilisez ce paramètre pour exécuter des commandes dont l'exécution nécessite beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="4e350-143">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="4e350-144">Quand vous utilisez le paramètre **AsJob** , la commande retourne un objet qui représente la tâche en arrière-plan, puis affiche l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="4e350-144">When you use the **AsJob** parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span> <span data-ttu-id="4e350-145">Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="4e350-145">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="4e350-146">Si `Invoke-WmiMethod` est utilisé sur un ordinateur distant, la tâche est créée sur l’ordinateur local et les résultats des ordinateurs distants sont automatiquement retournés à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4e350-146">If `Invoke-WmiMethod` is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="4e350-147">Pour gérer la tâche, utilisez les applets de commande contenant le nom Job (applets de commande Job).</span><span class="sxs-lookup"><span data-stu-id="4e350-147">To manage the job, use the cmdlets that contain the Job noun (the Job cmdlets).</span></span> <span data-ttu-id="4e350-148">Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="4e350-148">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="4e350-149">pour utiliser ce paramètre avec des ordinateurs distants, les ordinateurs locaux et distants doivent être configurés pour l'accès distant.</span><span class="sxs-lookup"><span data-stu-id="4e350-149">To use this parameter with remote computers, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="4e350-150">En outre, vous devez démarrer Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur dans Windows Vista et les versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="4e350-150">Additionally, you must start Windows PowerShell by using the Run as administrator option in Windows Vista and later versions of Windows.</span></span> <span data-ttu-id="4e350-151">Pour plus d'informations, consultez about_Remote_Requirements.</span><span class="sxs-lookup"><span data-stu-id="4e350-151">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="4e350-152">Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez about_Jobs et about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="4e350-152">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-153">-Authentification</span><span class="sxs-lookup"><span data-stu-id="4e350-153">-Authentication</span></span>

<span data-ttu-id="4e350-154">Spécifie le niveau d’authentification à utiliser avec la connexion WMI.</span><span class="sxs-lookup"><span data-stu-id="4e350-154">Specifies the authentication level to be used with the WMI connection.</span></span> <span data-ttu-id="4e350-155">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="4e350-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4e350-156">-1 : Unchanged</span><span class="sxs-lookup"><span data-stu-id="4e350-156">-1: Unchanged</span></span>
- <span data-ttu-id="4e350-157">0 : Default</span><span class="sxs-lookup"><span data-stu-id="4e350-157">0: Default</span></span>
- <span data-ttu-id="4e350-158">1 : None (Aucune authentification n'est effectuée.)</span><span class="sxs-lookup"><span data-stu-id="4e350-158">1: None (No authentication in performed.)</span></span>
- <span data-ttu-id="4e350-159">2 : Connect (L'authentification est effectuée uniquement lorsque le client établit une relation avec l'application.)</span><span class="sxs-lookup"><span data-stu-id="4e350-159">2: Connect (Authentication is performed only when the client establishes a relationship with the application.)</span></span>
- <span data-ttu-id="4e350-160">3 : Call (L'authentification est effectuée uniquement au début de chaque appel, quand l'application reçoit une demande.)</span><span class="sxs-lookup"><span data-stu-id="4e350-160">3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)</span></span>
- <span data-ttu-id="4e350-161">4 : Packet (L'authentification est effectuée sur toutes les données reçues du client.)</span><span class="sxs-lookup"><span data-stu-id="4e350-161">4: Packet (Authentication is performed on all the data that is received from the client.)</span></span>
- <span data-ttu-id="4e350-162">5 : PacketIntegrity (toutes les données transférées entre le client et l’application sont authentifiées et vérifiées.)</span><span class="sxs-lookup"><span data-stu-id="4e350-162">5: PacketIntegrity (All the data that is transferred between the client and the application is authenticated and verified.)</span></span>
- <span data-ttu-id="4e350-163">6 : PacketPrivacy (Les propriétés des autres niveaux d'authentification sont utilisées, et toutes les données sont chiffrées.)</span><span class="sxs-lookup"><span data-stu-id="4e350-163">6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-164">-Autorité</span><span class="sxs-lookup"><span data-stu-id="4e350-164">-Authority</span></span>

<span data-ttu-id="4e350-165">Spécifie l'autorité à utiliser pour authentifier la connexion WMI.</span><span class="sxs-lookup"><span data-stu-id="4e350-165">Specifies the authority to use to authenticate the WMI connection.</span></span> <span data-ttu-id="4e350-166">Vous pouvez spécifier l’authentification Windows NT LAN Manager (NTLM) ou Kerberos standard.</span><span class="sxs-lookup"><span data-stu-id="4e350-166">You can specify standard Windows NT LAN Manager (NTLM) or Kerberos authentication.</span></span> <span data-ttu-id="4e350-167">Pour utiliser NTLM, affectez au paramètre d'autorité la valeur ntlmdomain:\<DomainName\>, où \<DomainName\> identifie un nom de domaine NTLM valide.</span><span class="sxs-lookup"><span data-stu-id="4e350-167">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span> <span data-ttu-id="4e350-168">Pour utiliser Kerberos, spécifiez Kerberos : \<DomainName\ServerName\> .</span><span class="sxs-lookup"><span data-stu-id="4e350-168">To use Kerberos, specify kerberos:\<DomainName\ServerName\>.</span></span> <span data-ttu-id="4e350-169">Vous ne pouvez pas inclure le paramètre d'autorité lorsque vous vous connectez à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4e350-169">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-170">-Classe</span><span class="sxs-lookup"><span data-stu-id="4e350-170">-Class</span></span>

<span data-ttu-id="4e350-171">Spécifie la classe WMI qui contient une méthode statique à appeler.</span><span class="sxs-lookup"><span data-stu-id="4e350-171">Specifies the WMI class that contains a static method to call.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-172">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4e350-172">-ComputerName</span></span>

<span data-ttu-id="4e350-173">Spécifie, sous forme de tableau de chaînes, les ordinateurs sur lesquels cette applet de commande exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="4e350-173">Specifies, as a string array, the computers that this cmdlet runs the command on.</span></span> <span data-ttu-id="4e350-174">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4e350-174">The default is the local computer.</span></span>

<span data-ttu-id="4e350-175">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ou de plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="4e350-175">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span> <span data-ttu-id="4e350-176">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.</span><span class="sxs-lookup"><span data-stu-id="4e350-176">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="4e350-177">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e350-177">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="4e350-178">Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="4e350-178">You can use the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-179">-Credential</span><span class="sxs-lookup"><span data-stu-id="4e350-179">-Credential</span></span>

<span data-ttu-id="4e350-180">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="4e350-180">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="4e350-181">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="4e350-181">The default is the current user.</span></span> <span data-ttu-id="4e350-182">Tapez un nom d’utilisateur, tel que `User01` , `Domain01\User01` ou `User@Contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="4e350-182">Type a user name, such as `User01`, `Domain01\User01`, or `User@Contoso.com`.</span></span> <span data-ttu-id="4e350-183">Ou entrez un objet **PSCredential** , tel qu’un objet qui est retourné par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="4e350-183">Or, enter a **PSCredential** object, such as an object that is returned by the Get-Credential cmdlet.</span></span> <span data-ttu-id="4e350-184">Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="4e350-184">When you type a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-185">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="4e350-185">-EnableAllPrivileges</span></span>

<span data-ttu-id="4e350-186">Indique que cette applet de commande active tous les privilèges de l’utilisateur actuel avant que la commande effectue l’appel WMI.</span><span class="sxs-lookup"><span data-stu-id="4e350-186">Indicates that this cmdlet enables all the privileges of the current user before the command makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-187">-Emprunt d’identité</span><span class="sxs-lookup"><span data-stu-id="4e350-187">-Impersonation</span></span>

<span data-ttu-id="4e350-188">Spécifie le niveau d'emprunt d'identité à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4e350-188">Specifies the impersonation level to use.</span></span> <span data-ttu-id="4e350-189">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="4e350-189">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4e350-190">0 : Default (Lit le Registre local pour connaître le niveau d'emprunt d'identité par défaut, qui a généralement la valeur « 3 : Impersonate ».)</span><span class="sxs-lookup"><span data-stu-id="4e350-190">0: Default (Reads the local registry for the default impersonation level, which is usually set to "3: Impersonate".)</span></span>
- <span data-ttu-id="4e350-191">1 : Anonymous (Masque les informations d'identification de l'appelant.)</span><span class="sxs-lookup"><span data-stu-id="4e350-191">1: Anonymous (Hides the credentials of the caller.)</span></span>
- <span data-ttu-id="4e350-192">2 : Identify (Permet aux objets d'interroger les informations d'identification de l'appelant.)</span><span class="sxs-lookup"><span data-stu-id="4e350-192">2: Identify (Allows objects to query the credentials of the caller.)</span></span>
- <span data-ttu-id="4e350-193">3 : Impersonate (Permet aux objets d'utiliser les informations d'identification de l'appelant.)</span><span class="sxs-lookup"><span data-stu-id="4e350-193">3: Impersonate (Allows objects to use the credentials of the caller.)</span></span>
- <span data-ttu-id="4e350-194">4 : Delegate (Permet aux objets d'autoriser d'autres objets à utiliser les informations d'identification de l'appelant.)</span><span class="sxs-lookup"><span data-stu-id="4e350-194">4: Delegate (Allows objects to permit other objects to use the credentials of the caller.)</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-195">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4e350-195">-InputObject</span></span>

<span data-ttu-id="4e350-196">Spécifie un objet **ManagementObject** à utiliser comme entrée.</span><span class="sxs-lookup"><span data-stu-id="4e350-196">Specifies a **ManagementObject** object to use as input.</span></span> <span data-ttu-id="4e350-197">Quand ce paramètre est utilisé, tous les autres paramètres, à l’exception des paramètres **Flag** et **argument** , sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="4e350-197">When this parameter is used, all other parameters except the **Flag** and **Argument** parameters are ignored.</span></span>

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-198">Paramètres régionaux</span><span class="sxs-lookup"><span data-stu-id="4e350-198">-Locale</span></span>

<span data-ttu-id="4e350-199">Spécifie les paramètres régionaux par défaut pour les objets WMI.</span><span class="sxs-lookup"><span data-stu-id="4e350-199">Specifies the preferred locale for WMI objects.</span></span> <span data-ttu-id="4e350-200">Spécifiez la valeur du paramètre **locale** sous la forme d’un tableau au `MS_<LCID>` format dans l’ordre de préférence.</span><span class="sxs-lookup"><span data-stu-id="4e350-200">Specify the value of the **Locale** parameter as an array in the `MS_<LCID>` format in the preferred order.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-201">-Name</span><span class="sxs-lookup"><span data-stu-id="4e350-201">-Name</span></span>

<span data-ttu-id="4e350-202">Spécifie le nom de la méthode à appeler.</span><span class="sxs-lookup"><span data-stu-id="4e350-202">Specifies the name of the method to be invoked.</span></span> <span data-ttu-id="4e350-203">Ce paramètre est obligatoire et ne peut ni avoir la valeur Null ni être vide.</span><span class="sxs-lookup"><span data-stu-id="4e350-203">This parameter is mandatory and cannot be null or empty.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-204">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="4e350-204">-Namespace</span></span>

<span data-ttu-id="4e350-205">Lorsqu’il est utilisé avec le paramètre **Class** , ce paramètre spécifie l’espace de noms de l’espace de stockage WMI dans lequel se trouve la classe ou l’objet WMI référencé.</span><span class="sxs-lookup"><span data-stu-id="4e350-205">When used with the **Class** parameter, this parameter specifies the WMI repository namespace where the referenced WMI class or object is located.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-206">-Path</span><span class="sxs-lookup"><span data-stu-id="4e350-206">-Path</span></span>

<span data-ttu-id="4e350-207">Spécifie le chemin d’accès de l’objet WMI d’une classe WMI, ou spécifie le chemin d’accès de l’objet WMI d’une instance d’une classe WMI.</span><span class="sxs-lookup"><span data-stu-id="4e350-207">Specifies the WMI object path of a WMI class, or specifies the WMI object path of an instance of a WMI class.</span></span> <span data-ttu-id="4e350-208">La classe ou l’instance que vous spécifiez doit contenir la méthode spécifiée dans le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="4e350-208">The class or the instance that you specify must contain the method that is specified in the **Name** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-209">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="4e350-209">-ThrottleLimit</span></span>

<span data-ttu-id="4e350-210">Spécifie une valeur de limitation pour le nombre d’opérations WMI qui peuvent être exécutées simultanément.</span><span class="sxs-lookup"><span data-stu-id="4e350-210">Specifies a throttle value for the number of WMI operations that can be executed simultaneously.</span></span>
<span data-ttu-id="4e350-211">Ce paramètre est utilisé conjointement avec le paramètre **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="4e350-211">This parameter is used together with the **AsJob** parameter.</span></span> <span data-ttu-id="4e350-212">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4e350-212">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-213">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4e350-213">-Confirm</span></span>

<span data-ttu-id="4e350-214">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e350-214">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-215">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4e350-215">-WhatIf</span></span>

<span data-ttu-id="4e350-216">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e350-216">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4e350-217">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4e350-217">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e350-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e350-218">CommonParameters</span></span>

<span data-ttu-id="4e350-219">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e350-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e350-220">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4e350-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e350-221">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4e350-221">INPUTS</span></span>

### <span data-ttu-id="4e350-222">Aucun</span><span class="sxs-lookup"><span data-stu-id="4e350-222">None</span></span>

<span data-ttu-id="4e350-223">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="4e350-223">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="4e350-224">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4e350-224">OUTPUTS</span></span>

### <span data-ttu-id="4e350-225">Aucun</span><span class="sxs-lookup"><span data-stu-id="4e350-225">None</span></span>

<span data-ttu-id="4e350-226">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="4e350-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4e350-227">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4e350-227">NOTES</span></span>

## <span data-ttu-id="4e350-228">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4e350-228">RELATED LINKS</span></span>

[<span data-ttu-id="4e350-229">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4e350-229">Get-WSManInstance</span></span>](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[<span data-ttu-id="4e350-230">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="4e350-230">Invoke-WSManAction</span></span>](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[<span data-ttu-id="4e350-231">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4e350-231">New-WSManInstance</span></span>](../Microsoft.WsMan.Management/New-WSManInstance.md)

[<span data-ttu-id="4e350-232">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="4e350-232">Remove-WSManInstance</span></span>](../Microsoft.WsMan.Management/Remove-WSManInstance.md)

[<span data-ttu-id="4e350-233">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="4e350-233">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="4e350-234">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="4e350-234">Remove-WmiObject</span></span>](Remove-WmiObject.md)

[<span data-ttu-id="4e350-235">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="4e350-235">Set-WmiInstance</span></span>](Set-WmiInstance.md)
