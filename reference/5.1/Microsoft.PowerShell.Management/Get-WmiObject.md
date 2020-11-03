---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WmiObject
ms.openlocfilehash: ed759ff3d0dd35cd55f9dac5a2d76e36eac4dc6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203982"
---
# <span data-ttu-id="8f81a-103">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="8f81a-103">Get-WmiObject</span></span>

## <span data-ttu-id="8f81a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8f81a-104">SYNOPSIS</span></span>
<span data-ttu-id="8f81a-105">Obtient des instances de classes WMI (Windows Management Instrumentation) ou des informations sur les classes disponibles.</span><span class="sxs-lookup"><span data-stu-id="8f81a-105">Gets instances of Windows Management Instrumentation (WMI) classes or information about the available classes.</span></span>

## <span data-ttu-id="8f81a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8f81a-106">SYNTAX</span></span>

### <span data-ttu-id="8f81a-107">requête (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8f81a-107">query (Default)</span></span>

```
Get-WmiObject [-Class] <String> [[-Property] <String[]>] [-Filter <String>] [-Amended] [-DirectRead]
 [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="8f81a-108">list</span><span class="sxs-lookup"><span data-stu-id="8f81a-108">list</span></span>

```
Get-WmiObject [[-Class] <String>] [-Recurse] [-Amended] [-List] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="8f81a-109">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="8f81a-109">WQLQuery</span></span>

```
Get-WmiObject [-Amended] [-DirectRead] -Query <String> [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="8f81a-110">class</span><span class="sxs-lookup"><span data-stu-id="8f81a-110">class</span></span>

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="8f81a-111">path</span><span class="sxs-lookup"><span data-stu-id="8f81a-111">path</span></span>

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

## <span data-ttu-id="8f81a-112">Description</span><span class="sxs-lookup"><span data-stu-id="8f81a-112">DESCRIPTION</span></span>

<span data-ttu-id="8f81a-113">À compter de PowerShell 3,0, cette applet de commande a été remplacée par `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="8f81a-113">Starting in PowerShell 3.0, this cmdlet has been superseded by `Get-CimInstance`.</span></span>

<span data-ttu-id="8f81a-114">L' `Get-WmiObject` applet de commande obtient des instances de classes WMI ou des informations sur les classes WMI disponibles.</span><span class="sxs-lookup"><span data-stu-id="8f81a-114">The `Get-WmiObject` cmdlet gets instances of WMI classes or information about the available WMI classes.</span></span> <span data-ttu-id="8f81a-115">Pour spécifier un ordinateur distant, utilisez le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="8f81a-115">To specify a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="8f81a-116">Si le paramètre **List** est spécifié, l'applet de commande obtient des informations sur les classes WMI qui sont disponibles dans un espace de noms spécifié.</span><span class="sxs-lookup"><span data-stu-id="8f81a-116">If the **List** parameter is specified, the cmdlet gets information about the WMI classes that are available in a specified namespace.</span></span> <span data-ttu-id="8f81a-117">Si le paramètre **Query** est spécifié, l'applet de commande exécute une instruction utilisant le langage de requêtes WMI (WQL).</span><span class="sxs-lookup"><span data-stu-id="8f81a-117">If the **Query** parameter is specified, the cmdlet runs a WMI query language (WQL) statement.</span></span>

<span data-ttu-id="8f81a-118">L' `Get-WmiObject` applet de commande n’utilise pas la communication à distance Windows PowerShell pour effectuer des opérations distantes.</span><span class="sxs-lookup"><span data-stu-id="8f81a-118">The `Get-WmiObject` cmdlet does not use Windows PowerShell remoting to perform remote operations.</span></span>
<span data-ttu-id="8f81a-119">Vous pouvez utiliser le paramètre **ComputerName** de l' `Get-WmiObject` applet de commande même si votre ordinateur n’est pas conforme à la configuration requise pour la communication à distance Windows PowerShell ou n’est pas configuré pour la communication à distance dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f81a-119">You can use the **ComputerName** parameter of the `Get-WmiObject` cmdlet even if your computer does not meet the requirements for Windows PowerShell remoting or is not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="8f81a-120">À compter de Windows PowerShell 3,0, la propriété **__Server** de l’objet `Get-WmiObject` retourné par a un alias **PSComputerName** .</span><span class="sxs-lookup"><span data-stu-id="8f81a-120">Beginning in Windows PowerShell 3.0, the **__Server** property of the object that `Get-WmiObject` returns has a **PSComputerName** alias.</span></span> <span data-ttu-id="8f81a-121">Vous pouvez ainsi inclure plus facilement le nom de l'ordinateur source dans la sortie et dans les rapports.</span><span class="sxs-lookup"><span data-stu-id="8f81a-121">This makes it easier to include the source computer name in output and reports.</span></span>

## <span data-ttu-id="8f81a-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8f81a-122">EXAMPLES</span></span>

### <span data-ttu-id="8f81a-123">Exemple 1 : récupérer des processus sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="8f81a-123">Example 1: Get processes on the local computer</span></span>

<span data-ttu-id="8f81a-124">Cet exemple obtient les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8f81a-124">This example get the processes on the local computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Process
```

### <span data-ttu-id="8f81a-125">Exemple 2 : obtenir des services sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="8f81a-125">Example 2: Gets services on a remote computer</span></span>

<span data-ttu-id="8f81a-126">Cet exemple obtient les services sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-126">This example gets the services on a remote computer.</span></span> <span data-ttu-id="8f81a-127">Le paramètre **ComputerName** spécifie l’adresse IP d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-127">The **ComputerName** parameter specifies the IP address of a remote computer.</span></span> <span data-ttu-id="8f81a-128">Par défaut, le compte d’utilisateur actuel doit être membre du groupe **administrateurs** sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-128">By default, the current user account must be a member of the **Administrators** group on the remote computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName 10.1.4.62
```

### <span data-ttu-id="8f81a-129">Exemple 3 : récupération des classes WMI dans l’espace de noms racine ou par défaut de l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="8f81a-129">Example 3: Get WMI classes in the root or default namespace of the local computer</span></span>

<span data-ttu-id="8f81a-130">Cet exemple obtient les classes WMI dans l’espace de noms racine ou par défaut de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8f81a-130">This example gets the WMI classes in the root or default namespace of the local computer.</span></span>

```powershell
Get-WmiObject -Namespace "root/default" -List
```

### <span data-ttu-id="8f81a-131">Exemple 4 : obtenir un service nommé sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="8f81a-131">Example 4: Get a named service on multiple computers</span></span>

<span data-ttu-id="8f81a-132">Cet exemple obtient le service WinRM sur les ordinateurs spécifiés par la valeur du paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="8f81a-132">This example gets the WinRM service on the computers specified by the value of the **ComputerName** parameter.</span></span>

```powershell
Get-WmiObject -Query "select * from win32_service where name='WinRM'" -ComputerName Server01, Server02 |
  Format-List -Property PSComputerName, Name, ExitCode, Name, ProcessID, StartMode, State, Status
```

```Output
PSComputerName : SERVER01
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 844
StartMode      : Auto
State          : Running
Status         : OK

PSComputerName : SERVER02
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 932
StartMode      : Auto
State          : Running
Status         : OK
```

<span data-ttu-id="8f81a-133">Un opérateur de pipeline (|) envoie la sortie vers l'applet de commande `Format-List`, laquelle ajoute la propriété **PSComputerName** à la sortie par défaut.</span><span class="sxs-lookup"><span data-stu-id="8f81a-133">A pipeline operator (|) sends the output to the `Format-List` cmdlet, which adds the **PSComputerName** property to the default output.</span></span> <span data-ttu-id="8f81a-134">**PSComputerName** est un alias de la propriété **__Server** des objets `Get-WmiObject` retournées par.</span><span class="sxs-lookup"><span data-stu-id="8f81a-134">**PSComputerName** is an alias of the **__Server** property of the objects that `Get-WmiObject` returns.</span></span> <span data-ttu-id="8f81a-135">Cet alias a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8f81a-135">This alias was introduced in PowerShell 3.0.</span></span>

### <span data-ttu-id="8f81a-136">Exemple 5 : arrêter un service sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="8f81a-136">Example 5: Stop a service on a remote computer</span></span>

<span data-ttu-id="8f81a-137">Cet exemple arrête le service WinRM sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-137">This example stops the WinRM service on a remote computer.</span></span> <span data-ttu-id="8f81a-138">`Get-WmiObject` Obtient l’instance de l’objet de service WinRM sur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8f81a-138">`Get-WmiObject` gets the instance of the WinRM service object on Server01.</span></span> <span data-ttu-id="8f81a-139">Ensuite, il appelle la méthode **StopService** de la classe **Win32_Service** WMI sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="8f81a-139">Then, it invokes the **StopService** method of the **Win32_Service** WMI class on that object.</span></span>

```powershell
(Get-WmiObject -Class Win32_Service -Filter "name='WinRM'" -ComputerName Server01).StopService()
```

<span data-ttu-id="8f81a-140">Cela équivaut à utiliser l’applet de commande `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="8f81a-140">This is equivalent to using the `Stop-Service` cmdlet.</span></span>

### <span data-ttu-id="8f81a-141">Exemple 6 : récupération du BIOS sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="8f81a-141">Example 6: Get the BIOS on the local computer</span></span>

<span data-ttu-id="8f81a-142">Cet exemple obtient les informations du BIOS de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8f81a-142">This example gets the BIOS information from the local computer.</span></span> <span data-ttu-id="8f81a-143">Le paramètre **Property** de l' `Format-List` applet de commande est utilisé pour afficher toutes les propriétés de l’objet retourné dans une liste.</span><span class="sxs-lookup"><span data-stu-id="8f81a-143">The **Property** parameter of the `Format-List` cmdlet is used to display all properties of the returned object in a list.</span></span> <span data-ttu-id="8f81a-144">Par défaut, seul le sous-ensemble de propriétés défini dans le `Types.ps1xml` fichier de configuration s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8f81a-144">By default, only the subset of properties defined in the `Types.ps1xml` configuration file are displayed.</span></span>

```powershell
Get-WmiObject -Class Win32_Bios | Format-List -Property *
```

```Output
Status                : OK
Name                  : Phoenix ROM BIOS PLUS Version 1.10 A05
Caption               : Phoenix ROM BIOS PLUS Version 1.10 A05
SMBIOSPresent         : True
__GENUS               : 2
__CLASS               : Win32_BIOS
__SUPERCLASS          : CIM_BIOSElement
__DYNASTY             : CIM_ManagedSystemElement
__RELPATH             : Win32_BIOS.Name="Phoenix ROM BIOS PLUS Version 1.10
__PROPERTY_COUNT      : 27
__DERIVATION          : {CIM_BIOSElement, CIM_SoftwareElement, CIM_LogicalElement,
__SERVER              : Server01
__NAMESPACE           : root\cimv2
__PATH                : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
BiosCharacteristics   : {7, 9, 10, 11...}
BIOSVersion           : {DELL   - 15, Phoenix ROM BIOS PLUS Version 1.10 A05}
BuildNumber           :
CodeSet               :
CurrentLanguage       : en|US|iso8859-1
Description           : Phoenix ROM BIOS PLUS Version 1.10 A05
IdentificationCode    :
InstallableLanguages  : 1
InstallDate           :
LanguageEdition       :
ListOfLanguages       : {en|US|iso8859-1}
Manufacturer          : Dell Inc.
OtherTargetOS         :
PrimaryBIOS           : True
ReleaseDate           : 20101103000000.000000+000
SerialNumber          : 8VDM9P1
SMBIOSBIOSVersion     : A05
SMBIOSMajorVersion    : 2
SMBIOSMinorVersion    : 6
SoftwareElementID     : Phoenix ROM BIOS PLUS Version 1.10 A05
SoftwareElementState  : 3
TargetOperatingSystem : 0
Version               : DELL   - 15
Scope                 : System.Management.ManagementScope
Path                  : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
Options               : System.Management.ObjectGetOptions
ClassPath             : \\JUNE-PC\root\cimv2:Win32_BIOS
Properties            : {BiosCharacteristics, BIOSVersion, BuildNumber, Caption...}
SystemProperties      : {__GENUS, __CLASS, __SUPERCLASS, __DYNASTY...}
Qualifiers            : {dynamic, Locale, provider, UUID}
Site                  :
Container             :
```

### <span data-ttu-id="8f81a-145">Exemple 7 : obtenir les services sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="8f81a-145">Example 7: Get the services on a remote computer</span></span>

<span data-ttu-id="8f81a-146">Cet exemple utilise le paramètre **Credential** de l' `Get-WmiObject` applet de commande pour obtenir les services sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-146">This example uses the **Credential** parameter of the `Get-WmiObject` cmdlet to get the services on a remote computer.</span></span> <span data-ttu-id="8f81a-147">La valeur du paramètre **Credential** est un nom de compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8f81a-147">The value of the **Credential** parameter is a user account name.</span></span> <span data-ttu-id="8f81a-148">L'utilisateur est invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8f81a-148">The user is prompted for a password.</span></span>

```powershell
Get-WmiObject Win32_Service -Credential FABRIKAM\administrator -ComputerName Fabrikam
```

> [!NOTE]
> <span data-ttu-id="8f81a-149">Les informations d’identification ne peuvent pas être utilisées lors du ciblage de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8f81a-149">Credentials cannot be used when targeting the local computer.</span></span>

## <span data-ttu-id="8f81a-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8f81a-150">PARAMETERS</span></span>

### <span data-ttu-id="8f81a-151">-Modifié</span><span class="sxs-lookup"><span data-stu-id="8f81a-151">-Amended</span></span>

<span data-ttu-id="8f81a-152">Obtient ou définit une valeur qui indique si les objets retournés par WMI doivent contenir des informations modifiées.</span><span class="sxs-lookup"><span data-stu-id="8f81a-152">Gets or sets a value that indicates whether the objects that are returned from WMI should contain amended information.</span></span> <span data-ttu-id="8f81a-153">En général, les informations modifiées sont des informations localisables jointes à l'objet WMI (descriptions de propriété et d'objet, par exemple).</span><span class="sxs-lookup"><span data-stu-id="8f81a-153">Typically, amended information is localizable information, such as object and property descriptions, that is attached to the WMI object.</span></span>

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

### <span data-ttu-id="8f81a-154">-AsJob</span><span class="sxs-lookup"><span data-stu-id="8f81a-154">-AsJob</span></span>

<span data-ttu-id="8f81a-155">Exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="8f81a-155">Runs the command as a background job.</span></span> <span data-ttu-id="8f81a-156">Utilisez ce paramètre pour exécuter des commandes dont l'exécution nécessite beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="8f81a-156">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="8f81a-157">Quand vous utilisez le paramètre **AsJob** , la commande retourne un objet qui représente la tâche en arrière-plan, puis affiche l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="8f81a-157">When you use the **AsJob** parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span> <span data-ttu-id="8f81a-158">Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="8f81a-158">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="8f81a-159">Si `Get-WmiObject` est utilisé sur un ordinateur distant, la tâche est créée sur l’ordinateur local et les résultats des ordinateurs distants sont automatiquement retournés à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8f81a-159">If `Get-WmiObject` is used on a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="8f81a-160">Pour gérer la tâche, utilisez les applets de commande contenant les applets de commande Job.</span><span class="sxs-lookup"><span data-stu-id="8f81a-160">To manage the job, use the cmdlets that contain the Job cmdlets.</span></span> <span data-ttu-id="8f81a-161">Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="8f81a-161">To get the job results, use the `Receive-Job` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="8f81a-162">pour utiliser ce paramètre avec des ordinateurs distants, les ordinateurs locaux et distants doivent être configurés pour l'accès distant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-162">To use this parameter with remote computers, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="8f81a-163">En outre, vous devez démarrer Windows PowerShell en utilisant l'option « Exécuter en tant qu'administrateur » dans Windows Vista et les versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="8f81a-163">Additionally, you must start Windows PowerShell by using the "Run as administrator" option in Windows Vista and later versions of Windows.</span></span> <span data-ttu-id="8f81a-164">Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f81a-164">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="8f81a-165">Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="8f81a-165">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="8f81a-166">-Authentification</span><span class="sxs-lookup"><span data-stu-id="8f81a-166">-Authentication</span></span>

<span data-ttu-id="8f81a-167">Spécifie le niveau d’authentification à utiliser avec la connexion WMI.</span><span class="sxs-lookup"><span data-stu-id="8f81a-167">Specifies the authentication level to be used with the WMI connection.</span></span>
<span data-ttu-id="8f81a-168">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="8f81a-168">Valid values are:</span></span>

- <span data-ttu-id="8f81a-169">-1 : Unchanged</span><span class="sxs-lookup"><span data-stu-id="8f81a-169">-1: Unchanged</span></span>
- <span data-ttu-id="8f81a-170">0 : Default</span><span class="sxs-lookup"><span data-stu-id="8f81a-170">0: Default</span></span>
- <span data-ttu-id="8f81a-171">1 : None (Aucune authentification n'est effectuée.)</span><span class="sxs-lookup"><span data-stu-id="8f81a-171">1: None (No authentication in performed.)</span></span>
- <span data-ttu-id="8f81a-172">2 : Connect (L'authentification est effectuée uniquement lorsque le client établit une relation avec l'application.)</span><span class="sxs-lookup"><span data-stu-id="8f81a-172">2: Connect (Authentication is performed only when the client establishes a relationship with the application.)</span></span>
- <span data-ttu-id="8f81a-173">3 : Call (L'authentification est effectuée uniquement au début de chaque appel, quand l'application reçoit une demande.)</span><span class="sxs-lookup"><span data-stu-id="8f81a-173">3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)</span></span>
- <span data-ttu-id="8f81a-174">4 : Packet (L'authentification est effectuée sur toutes les données reçues du client.)</span><span class="sxs-lookup"><span data-stu-id="8f81a-174">4: Packet (Authentication is performed on all the data that is received from the client.)</span></span>
- <span data-ttu-id="8f81a-175">5 : PacketIntegrity (toutes les données transférées entre le client et l’application sont authentifiées et vérifiées.)</span><span class="sxs-lookup"><span data-stu-id="8f81a-175">5: PacketIntegrity (All the data that is transferred between the client and the application is authenticated and verified.)</span></span>
- <span data-ttu-id="8f81a-176">6 : PacketPrivacy (Les propriétés des autres niveaux d'authentification sont utilisées, et toutes les données sont chiffrées.)</span><span class="sxs-lookup"><span data-stu-id="8f81a-176">6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-177">-Autorité</span><span class="sxs-lookup"><span data-stu-id="8f81a-177">-Authority</span></span>

<span data-ttu-id="8f81a-178">Spécifie l'autorité à utiliser pour authentifier la connexion WMI.</span><span class="sxs-lookup"><span data-stu-id="8f81a-178">Specifies the authority to use to authenticate the WMI connection.</span></span> <span data-ttu-id="8f81a-179">Vous pouvez spécifier l'authentification Kerberos ou NTLM standard.</span><span class="sxs-lookup"><span data-stu-id="8f81a-179">You can specify standard NTLM or Kerberos authentication.</span></span> <span data-ttu-id="8f81a-180">Pour utiliser NTLM, affectez au paramètre d’autorité la valeur `ntlmdomain:<DomainName>` , où `<DomainName>` identifie un nom de domaine NTLM valide.</span><span class="sxs-lookup"><span data-stu-id="8f81a-180">To use NTLM, set the authority setting to `ntlmdomain:<DomainName>`, where `<DomainName>` identifies a valid NTLM domain name.</span></span> <span data-ttu-id="8f81a-181">Pour utiliser Kerberos, spécifiez `kerberos:<DomainName>\<ServerName>` .</span><span class="sxs-lookup"><span data-stu-id="8f81a-181">To use Kerberos, specify `kerberos:<DomainName>\<ServerName>`.</span></span> <span data-ttu-id="8f81a-182">Vous ne pouvez pas inclure le paramètre d'autorité lorsque vous vous connectez à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8f81a-182">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-183">-Classe</span><span class="sxs-lookup"><span data-stu-id="8f81a-183">-Class</span></span>

<span data-ttu-id="8f81a-184">Spécifie le nom d'une classe WMI.</span><span class="sxs-lookup"><span data-stu-id="8f81a-184">Specifies the name of a WMI class.</span></span> <span data-ttu-id="8f81a-185">Lors de l'utilisation de ce paramètre, l'applet de commande récupère des instances de la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="8f81a-185">When this parameter is used, the cmdlet retrieves instances of the WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: query, list
Aliases: ClassName

Required: True (query), False (list)
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-186">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="8f81a-186">-ComputerName</span></span>

<span data-ttu-id="8f81a-187">Spécifie l'ordinateur cible pour l'opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="8f81a-187">Specifies the target computer for the management operation.</span></span> <span data-ttu-id="8f81a-188">Entrez un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="8f81a-188">Enter a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="8f81a-189">Lorsque l'ordinateur distant se trouve dans un domaine différent de celui de l'ordinateur local, le nom de domaine complet est requis.</span><span class="sxs-lookup"><span data-stu-id="8f81a-189">When the remote computer is in a different domain than the local computer, the fully qualified domain name is required.</span></span>

<span data-ttu-id="8f81a-190">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8f81a-190">The default is the local computer.</span></span> <span data-ttu-id="8f81a-191">Pour spécifier l'ordinateur local, par exemple dans une liste de noms d'ordinateur, utilisez « localhost », le nom de l'ordinateur local ou un point (.).</span><span class="sxs-lookup"><span data-stu-id="8f81a-191">To specify the local computer, such as in a list of computer names, use "localhost", the local computer name, or a dot (.).</span></span>

<span data-ttu-id="8f81a-192">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell, laquelle utilise le service Gestion des services Web.</span><span class="sxs-lookup"><span data-stu-id="8f81a-192">This parameter does not rely on Windows PowerShell remoting, which uses WS-Management.</span></span> <span data-ttu-id="8f81a-193">Vous pouvez utiliser le paramètre **ComputerName** de `Get-WmiObject` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes WS-Management.</span><span class="sxs-lookup"><span data-stu-id="8f81a-193">You can use the **ComputerName** parameter of `Get-WmiObject` even if your computer is not configured to run WS-Management remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-194">-Credential</span><span class="sxs-lookup"><span data-stu-id="8f81a-194">-Credential</span></span>

<span data-ttu-id="8f81a-195">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="8f81a-195">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="8f81a-196">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="8f81a-196">The default is the current user.</span></span> <span data-ttu-id="8f81a-197">Tapez un nom d’utilisateur, tel que « User01 », « Domaine01\utilisateur01 » ou User@Contoso.com .</span><span class="sxs-lookup"><span data-stu-id="8f81a-197">Type a user name, such as "User01", "Domain01\User01", or User@Contoso.com.</span></span> <span data-ttu-id="8f81a-198">Vous pouvez également entrer un objet **PSCredential** , tel qu'un objet qui est retourné par l'applet de commande `Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="8f81a-198">Or, enter a **PSCredential** object, such as an object that is returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="8f81a-199">Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8f81a-199">When you type a user name, you are prompted for a password.</span></span> <span data-ttu-id="8f81a-200">Les informations d’identification ne peuvent pas être utilisées lors du ciblage de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8f81a-200">Credentials cannot be used when targeting the local computer.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-201">-DirectRead</span><span class="sxs-lookup"><span data-stu-id="8f81a-201">-DirectRead</span></span>

<span data-ttu-id="8f81a-202">Spécifie si l'accès direct au fournisseur WMI est demandé pour la classe spécifiée, quelles que soient ses classes de base ou ses classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="8f81a-202">Specifies whether direct access to the WMI provider is requested for the specified class without any regard to its base class or to its derived classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: query, WQLQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-203">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="8f81a-203">-EnableAllPrivileges</span></span>

<span data-ttu-id="8f81a-204">Active tous les privilèges de l'utilisateur actuel avant que la commande ne passe l'appel WMI.</span><span class="sxs-lookup"><span data-stu-id="8f81a-204">Enables all the privileges of the current user before the command makes the WMI call.</span></span>

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

### <span data-ttu-id="8f81a-205">-Filter</span><span class="sxs-lookup"><span data-stu-id="8f81a-205">-Filter</span></span>

<span data-ttu-id="8f81a-206">Spécifie une clause **Where** à utiliser comme filtre.</span><span class="sxs-lookup"><span data-stu-id="8f81a-206">Specifies a **Where** clause to use as a filter.</span></span> <span data-ttu-id="8f81a-207">Utilise la syntaxe du langage de requêtes WMI (WQL).</span><span class="sxs-lookup"><span data-stu-id="8f81a-207">Uses the syntax of the WMI Query Language (WQL).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f81a-208">n'incluez pas le mot clé **Where** dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="8f81a-208">Do not include the **Where** keyword in the value of the parameter.</span></span> <span data-ttu-id="8f81a-209">Par exemple, les commandes suivantes retournent uniquement les disques logiques dont le paramètre **DeviceID** a la valeur « c: » et les services ayant pour nom « WinRM », sans utiliser le mot clé **Where** .</span><span class="sxs-lookup"><span data-stu-id="8f81a-209">For example, the following commands return only the logical disks that have a **DeviceID** of 'c:' and services that have the name 'WinRM' without using the **Where** keyword.</span></span>

`Get-WmiObject Win32_LogicalDisk -filter "DeviceID = 'c:' "`

`Get-WmiObject win32_service -filter "name='WinRM'"`

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-210">-Emprunt d’identité</span><span class="sxs-lookup"><span data-stu-id="8f81a-210">-Impersonation</span></span>

<span data-ttu-id="8f81a-211">Spécifie le niveau d'emprunt d'identité à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8f81a-211">Specifies the impersonation level to use.</span></span>

<span data-ttu-id="8f81a-212">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="8f81a-212">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8f81a-213">0 : Default.</span><span class="sxs-lookup"><span data-stu-id="8f81a-213">0: Default.</span></span> <span data-ttu-id="8f81a-214">Lit le registre local pour le niveau d’emprunt d’identité par défaut.</span><span class="sxs-lookup"><span data-stu-id="8f81a-214">Reads the local registry for the default impersonation level.</span></span> <span data-ttu-id="8f81a-215">La valeur par défaut est généralement définie sur **emprunter l’identité** .</span><span class="sxs-lookup"><span data-stu-id="8f81a-215">The default is usually set to **Impersonate** .</span></span>
- <span data-ttu-id="8f81a-216">1 : Anonymous.</span><span class="sxs-lookup"><span data-stu-id="8f81a-216">1: Anonymous.</span></span> <span data-ttu-id="8f81a-217">Masque les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-217">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="8f81a-218">2 : Identify.</span><span class="sxs-lookup"><span data-stu-id="8f81a-218">2: Identify.</span></span> <span data-ttu-id="8f81a-219">Permet aux objets d'interroger les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-219">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="8f81a-220">3 : Impersonate.</span><span class="sxs-lookup"><span data-stu-id="8f81a-220">3: Impersonate.</span></span> <span data-ttu-id="8f81a-221">Permet aux objets d'utiliser les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-221">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="8f81a-222">4 : Delegate.</span><span class="sxs-lookup"><span data-stu-id="8f81a-222">4: Delegate.</span></span> <span data-ttu-id="8f81a-223">Permet aux objets d'autoriser d'autres objets à utiliser les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-223">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-224">-List</span><span class="sxs-lookup"><span data-stu-id="8f81a-224">-List</span></span>

<span data-ttu-id="8f81a-225">Obtient les noms des classes WMI figurant dans l'espace de noms de l'espace de stockage WMI spécifié par le paramètre **Namespace** .</span><span class="sxs-lookup"><span data-stu-id="8f81a-225">Gets the names of the WMI classes in the WMI repository namespace that is specified by the **Namespace** parameter.</span></span>

<span data-ttu-id="8f81a-226">Si vous spécifiez le paramètre **List** , mais pas le paramètre **namespace** , `Get-WmiObject` utilise l’espace de noms **Root\Cimv2** par défaut.</span><span class="sxs-lookup"><span data-stu-id="8f81a-226">If you specify the **List** parameter, but not the **Namespace** parameter, `Get-WmiObject` uses the **Root\Cimv2** namespace by default.</span></span> <span data-ttu-id="8f81a-227">Cette applet de commande n’utilise pas l’entrée de Registre **par défaut** de l’espace de noms dans la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` clé de Registre pour déterminer l’espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="8f81a-227">This cmdlet does not use the **Default Namespace** registry entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` registry key to determine the default namespace.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-228">Paramètres régionaux</span><span class="sxs-lookup"><span data-stu-id="8f81a-228">-Locale</span></span>

<span data-ttu-id="8f81a-229">Spécifie les paramètres régionaux par défaut pour les objets WMI.</span><span class="sxs-lookup"><span data-stu-id="8f81a-229">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="8f81a-230">Entrez une valeur au format MS_\<LCID\>.</span><span class="sxs-lookup"><span data-stu-id="8f81a-230">Enter a value in MS_\<LCID\> format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-231">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="8f81a-231">-Namespace</span></span>

<span data-ttu-id="8f81a-232">Lorsqu'il est utilisé avec le paramètre **Class** , le paramètre **Namespace** spécifie l'espace de noms de l'espace de stockage WMI dans lequel figure la classe WMI spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8f81a-232">When used with the **Class** parameter, the **Namespace** parameter specifies the WMI repository namespace where the specified WMI class is located.</span></span> <span data-ttu-id="8f81a-233">Lorsqu'il est utilisé avec le paramètre **List** , il spécifie l'espace de noms dans lequel collecter les informations sur la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="8f81a-233">When used with the **List** parameter, it specifies the namespace from which to gather WMI class information.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-234">-Propriété</span><span class="sxs-lookup"><span data-stu-id="8f81a-234">-Property</span></span>

<span data-ttu-id="8f81a-235">Spécifie les propriétés de classe WMI à partir desquelles cette applet de commande obtient des informations.</span><span class="sxs-lookup"><span data-stu-id="8f81a-235">Specifies the WMI class properties that this cmdlet gets information from.</span></span> <span data-ttu-id="8f81a-236">Entrez les noms des propriétés.</span><span class="sxs-lookup"><span data-stu-id="8f81a-236">Enter the property names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: query
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-237">-Query</span><span class="sxs-lookup"><span data-stu-id="8f81a-237">-Query</span></span>

<span data-ttu-id="8f81a-238">Exécute l'instruction utilisant le langage de requêtes WMI (WQL) spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8f81a-238">Runs the specified WMI Query Language (WQL) statement.</span></span> <span data-ttu-id="8f81a-239">Ce paramètre ne prend pas en charge les requêtes d'événement.</span><span class="sxs-lookup"><span data-stu-id="8f81a-239">This parameter does not support event queries.</span></span>

```yaml
Type: System.String
Parameter Sets: WQLQuery
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-240">-Recurse</span><span class="sxs-lookup"><span data-stu-id="8f81a-240">-Recurse</span></span>

<span data-ttu-id="8f81a-241">Recherche l'espace de noms actuel et tous les autres espaces de noms pour le nom de classe spécifié par le paramètre **Class** .</span><span class="sxs-lookup"><span data-stu-id="8f81a-241">Searches the current namespace and all other namespaces for the class name that is specified by the **Class** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f81a-242">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="8f81a-242">-ThrottleLimit</span></span>

<span data-ttu-id="8f81a-243">Spécifie le nombre maximal d'opérations WMI pouvant être exécutées simultanément.</span><span class="sxs-lookup"><span data-stu-id="8f81a-243">Specifies the maximum number of WMI operations that can be executed simultaneously.</span></span> <span data-ttu-id="8f81a-244">Ce paramètre est valide uniquement lorsque le paramètre **AsJob** est utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="8f81a-244">This parameter is valid only when the **AsJob** parameter is used in the command.</span></span>

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

### <span data-ttu-id="8f81a-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8f81a-245">CommonParameters</span></span>

<span data-ttu-id="8f81a-246">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8f81a-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8f81a-247">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8f81a-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8f81a-248">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8f81a-248">INPUTS</span></span>

### <span data-ttu-id="8f81a-249">Aucun</span><span class="sxs-lookup"><span data-stu-id="8f81a-249">None</span></span>

<span data-ttu-id="8f81a-250">Vous ne pouvez pas diriger d’entrée vers `Get-WmiObject` .</span><span class="sxs-lookup"><span data-stu-id="8f81a-250">You cannot pipe input to `Get-WmiObject`.</span></span>

## <span data-ttu-id="8f81a-251">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8f81a-251">OUTPUTS</span></span>

### <span data-ttu-id="8f81a-252">PSObject ou System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="8f81a-252">PSObject or System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="8f81a-253">Lorsque vous utilisez le paramètre **AsJob** , l'applet de commande retourne un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="8f81a-253">When you use the **AsJob** parameter, the cmdlet returns a job object.</span></span> <span data-ttu-id="8f81a-254">Dans le cas contraire, l’objet `Get-WmiObject` retourné dépend de la valeur du paramètre **Class** .</span><span class="sxs-lookup"><span data-stu-id="8f81a-254">Otherwise, the object that `Get-WmiObject` returns depends on the value of the **Class** parameter.</span></span>

## <span data-ttu-id="8f81a-255">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8f81a-255">NOTES</span></span>

<span data-ttu-id="8f81a-256">Pour accéder aux informations se rapportant à WMI sur un ordinateur distant, l'applet de commande doit s'exécuter sous un compte qui est membre du groupe des administrateurs locaux sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8f81a-256">To access WMI information on a remote computer, the cmdlet must run under an account that is a member of the local administrators group on the remote computer.</span></span> <span data-ttu-id="8f81a-257">Le contrôle d'accès par défaut sur l'espace de noms WMI de l'espace de stockage distant peut également être modifié afin d'octroyer des droits d'accès à d'autres comptes.</span><span class="sxs-lookup"><span data-stu-id="8f81a-257">Or, the default access control on the WMI namespace of the remote repository can be changed to give access rights to other accounts.</span></span>

<span data-ttu-id="8f81a-258">Seules quelques propriétés de chaque classe WMI sont affichées par défaut.</span><span class="sxs-lookup"><span data-stu-id="8f81a-258">Only some of the properties of each WMI class are displayed by default.</span></span> <span data-ttu-id="8f81a-259">Le jeu de propriétés affichées pour chaque classe WMI est spécifié dans le fichier de configuration Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="8f81a-259">The set of properties that is displayed for each WMI class is specified in the Types.ps1xml configuration file.</span></span> <span data-ttu-id="8f81a-260">Pour obtenir toutes les propriétés d’un objet WMI, utilisez `Get-Member` les `Format-List` applets de commande ou.</span><span class="sxs-lookup"><span data-stu-id="8f81a-260">To get all properties of a WMI object, use the `Get-Member` or `Format-List` cmdlets.</span></span>

## <span data-ttu-id="8f81a-261">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8f81a-261">RELATED LINKS</span></span>

[<span data-ttu-id="8f81a-262">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="8f81a-262">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="8f81a-263">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="8f81a-263">Remove-WmiObject</span></span>](Remove-WmiObject.md)

[<span data-ttu-id="8f81a-264">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="8f81a-264">Set-WmiInstance</span></span>](Set-WmiInstance.md)

[<span data-ttu-id="8f81a-265">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8f81a-265">Get-WSManInstance</span></span>](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[<span data-ttu-id="8f81a-266">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="8f81a-266">Invoke-WSManAction</span></span>](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[<span data-ttu-id="8f81a-267">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8f81a-267">New-WSManInstance</span></span>](../Microsoft.WsMan.Management/New-WSManInstance.md)

[<span data-ttu-id="8f81a-268">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8f81a-268">Remove-WSManInstance</span></span>](../Microsoft.WsMan.Management/Remove-WSManInstance.md)
