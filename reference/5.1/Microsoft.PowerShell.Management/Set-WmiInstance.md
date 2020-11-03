---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-wmiinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WmiInstance
ms.openlocfilehash: 03288a2ffbef416937b2c92a7d08a5aed49ffb43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203493"
---
# <span data-ttu-id="29598-103">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="29598-103">Set-WmiInstance</span></span>

## <span data-ttu-id="29598-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="29598-104">SYNOPSIS</span></span>
<span data-ttu-id="29598-105">Crée ou met à jour une instance d'une classe WMI (Windows Management Instrumentation) existante.</span><span class="sxs-lookup"><span data-stu-id="29598-105">Creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>

## <span data-ttu-id="29598-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="29598-106">SYNTAX</span></span>

### <span data-ttu-id="29598-107">classe (par défaut)</span><span class="sxs-lookup"><span data-stu-id="29598-107">class (Default)</span></span>

```
Set-WmiInstance [-Class] <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="29598-108">object</span><span class="sxs-lookup"><span data-stu-id="29598-108">object</span></span>

```
Set-WmiInstance -InputObject <ManagementObject> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="29598-109">path</span><span class="sxs-lookup"><span data-stu-id="29598-109">path</span></span>

```
Set-WmiInstance -Path <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="29598-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="29598-110">WQLQuery</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="29598-111">query</span><span class="sxs-lookup"><span data-stu-id="29598-111">query</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="29598-112">list</span><span class="sxs-lookup"><span data-stu-id="29598-112">list</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="29598-113">Description</span><span class="sxs-lookup"><span data-stu-id="29598-113">DESCRIPTION</span></span>
<span data-ttu-id="29598-114">L' `Set-WmiInstance` applet de commande crée ou met à jour une instance d’une classe Windows Management Instrumentation (WMI) existante.</span><span class="sxs-lookup"><span data-stu-id="29598-114">The `Set-WmiInstance` cmdlet creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>
<span data-ttu-id="29598-115">L'instance créée ou mise à jour est écrite dans l'espace de stockage WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-115">The created or updated instance is written to the WMI repository.</span></span>

<span data-ttu-id="29598-116">De nouvelles applets de commande CIM, introduites dans Windows PowerShell 3.0, effectuent les mêmes tâches que les applets de commande WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-116">New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span>
<span data-ttu-id="29598-117">Les applets de commande CIM sont conformes aux normes WS-Management (WSMan) et à la norme Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="29598-117">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard.</span></span>
<span data-ttu-id="29598-118">Cela permet aux cmdlets d’utiliser les mêmes techniques pour gérer les ordinateurs Windows et ceux qui exécutent d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="29598-118">this enables cmdlets to use the same techniques to manage Windows-based computers and those running other operating systems.</span></span>
<span data-ttu-id="29598-119">Au lieu d’utiliser `Set-WmiInstance` , envisagez d’utiliser les applets de commande [Set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) ou [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) .</span><span class="sxs-lookup"><span data-stu-id="29598-119">Instead of using `Set-WmiInstance`, consider using the [Set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) or [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) cmdlets.</span></span>

## <span data-ttu-id="29598-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="29598-120">EXAMPLES</span></span>

### <span data-ttu-id="29598-121">Exemple 1 : définir le niveau de journalisation WMI</span><span class="sxs-lookup"><span data-stu-id="29598-121">Example 1: Set WMI logging level</span></span>

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2}
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

<span data-ttu-id="29598-122">Cette commande affecte la valeur 2 au niveau de journalisation WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-122">This command sets the WMI logging level to 2.</span></span>
<span data-ttu-id="29598-123">La commande passe la propriété à définir et la valeur, ensemble considérée comme une paire de valeurs, dans le paramètre d’argument.</span><span class="sxs-lookup"><span data-stu-id="29598-123">The command passes the property to be set and the value, together considered a value pair, in the argument parameter.</span></span>
<span data-ttu-id="29598-124">Le paramètre accepte une table de hachage qui est définie par la construction @{propriété = valeur}.</span><span class="sxs-lookup"><span data-stu-id="29598-124">The parameter takes a hash table that is defined by the @{property = value} construction.</span></span>
<span data-ttu-id="29598-125">Les informations de classe qui sont retournées reflètent la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="29598-125">The class information that is returned reflects the new value.</span></span>

### <span data-ttu-id="29598-126">Exemple 2 : créer une variable d’environnement et sa valeur</span><span class="sxs-lookup"><span data-stu-id="29598-126">Example 2: Create an environment variable and its value</span></span>

```
PS C:\> Set-WmiInstance -Class win32_environment -Argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}
__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

<span data-ttu-id="29598-127">Cette commande crée la variable d’environnement testvar qui a la valeur TestValue.</span><span class="sxs-lookup"><span data-stu-id="29598-127">This command creates the testvar environment variable that has the value testvalue.</span></span>
<span data-ttu-id="29598-128">Pour ce faire, il crée une nouvelle instance de la classe **Win32_Environment** WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-128">It does this by creating a new instance of the **Win32_Environment** WMI class.</span></span>
<span data-ttu-id="29598-129">Cette opération nécessite des informations d’identification appropriées et vous devrez peut-être redémarrer Windows PowerShell pour afficher la nouvelle variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="29598-129">This operation requires appropriate credentials and that you may have to restart Windows PowerShell to see the new environment variable.</span></span>

### <span data-ttu-id="29598-130">Exemple 3 : définir le niveau de journalisation WMI pour plusieurs ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="29598-130">Example 3: Set WMI logging level for several remote computers</span></span>

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2} -Computername "system01", "system02", "system03"
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

<span data-ttu-id="29598-131">Cette commande affecte la valeur 2 au niveau de journalisation WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-131">This command sets the WMI logging level to 2.</span></span>
<span data-ttu-id="29598-132">La commande passe la propriété à définir et la valeur, ensemble considérée comme une paire de valeurs, dans le paramètre d’argument.</span><span class="sxs-lookup"><span data-stu-id="29598-132">The command passes the property to be set and the value, together considered a value pair, in the argument parameter.</span></span>
<span data-ttu-id="29598-133">Le paramètre accepte une table de hachage qui est définie par la construction @{propriété = valeur}.</span><span class="sxs-lookup"><span data-stu-id="29598-133">The parameter takes a hash table that is defined by the @{property = value} construction.</span></span>
<span data-ttu-id="29598-134">L'information de classe retournée reflète la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="29598-134">The returned class information reflects the new value.</span></span>

## <span data-ttu-id="29598-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="29598-135">PARAMETERS</span></span>

### <span data-ttu-id="29598-136">-Arguments</span><span class="sxs-lookup"><span data-stu-id="29598-136">-Arguments</span></span>
<span data-ttu-id="29598-137">Spécifie le nom de la propriété à modifier et la nouvelle valeur pour cette propriété.</span><span class="sxs-lookup"><span data-stu-id="29598-137">Specifies the name of the property to be changed and the new value for that property.</span></span>
<span data-ttu-id="29598-138">Le nom et la valeur doivent être une paire nom-valeur.</span><span class="sxs-lookup"><span data-stu-id="29598-138">The name and value must be a name-value pair.</span></span>
<span data-ttu-id="29598-139">La paire nom-valeur est passée sur la ligne de commande en tant que table de hachage.</span><span class="sxs-lookup"><span data-stu-id="29598-139">The name-value pair is passed on the command line as a hash table.</span></span>
<span data-ttu-id="29598-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="29598-140">For example:</span></span>

`@{Setting1=1; Setting2=5; Setting3="test"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: class, object, path
Aliases: Args, Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29598-141">-AsJob</span><span class="sxs-lookup"><span data-stu-id="29598-141">-AsJob</span></span>
<span data-ttu-id="29598-142">Indique que ce cmdket s’exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="29598-142">Indicates that this cmdket runs as a background job.</span></span>
<span data-ttu-id="29598-143">Utilisez ce paramètre pour exécuter des commandes dont l'exécution nécessite beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="29598-143">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="29598-144">Lorsque vous spécifiez le paramètre *AsJob* , la commande retourne un objet qui représente la tâche en arrière-plan, puis affiche l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="29598-144">When you specify the *AsJob* parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span>
<span data-ttu-id="29598-145">Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="29598-145">You can continue to work in the session while the job finishes.</span></span>
<span data-ttu-id="29598-146">Si **Set-WmiInstance** est utilisé pour un ordinateur distant, la tâche est créée sur l’ordinateur local et les résultats des ordinateurs distants sont automatiquement retournés à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="29598-146">If **Set-WmiInstance** is used for a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="29598-147">Pour gérer le travail, utilisez les applets de commande qui contiennent le nom du **travail** (les applets de commande **Job** ).</span><span class="sxs-lookup"><span data-stu-id="29598-147">To manage the job, use the cmdlets that contain the **Job** noun (the **Job** cmdlets).</span></span>
<span data-ttu-id="29598-148">Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="29598-148">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="29598-149">Pour utiliser ce paramètre avec des ordinateurs distants, les ordinateurs locaux et distants doivent être configurés pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="29598-149">To use this parameter together with remote computers, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="29598-150">En outre, vous devez démarrer Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur dans Windows Vista et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="29598-150">Additionally, you must start Windows PowerShell by using the Run as administrator option in Windows Vista and later versions of the Windows operating system.</span></span>
<span data-ttu-id="29598-151">Pour plus d'informations, consultez about_Remote_Requirements.</span><span class="sxs-lookup"><span data-stu-id="29598-151">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="29598-152">Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez about_Jobs et about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="29598-152">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="29598-153">-Authentification</span><span class="sxs-lookup"><span data-stu-id="29598-153">-Authentication</span></span>
<span data-ttu-id="29598-154">Spécifie le niveau d’authentification qui doit être utilisé avec la connexion WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-154">Specifies the authentication level that must be used with the WMI connection.</span></span>
<span data-ttu-id="29598-155">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="29598-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="29598-156">-1 : inchangé.</span><span class="sxs-lookup"><span data-stu-id="29598-156">-1: Unchanged.</span></span>
- <span data-ttu-id="29598-157">0 : Default.</span><span class="sxs-lookup"><span data-stu-id="29598-157">0: Default.</span></span>
- <span data-ttu-id="29598-158">1 : aucune.</span><span class="sxs-lookup"><span data-stu-id="29598-158">1: None.</span></span>
<span data-ttu-id="29598-159">Aucune authentification n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="29598-159">No authentication in performed.</span></span>
- <span data-ttu-id="29598-160">2 : se connecter.</span><span class="sxs-lookup"><span data-stu-id="29598-160">2: Connect.</span></span>
<span data-ttu-id="29598-161">L’authentification est effectuée uniquement lorsque le client établit une relation avec l’application.</span><span class="sxs-lookup"><span data-stu-id="29598-161">Authentication is performed only when the client establishes a relationship with the application.</span></span>
- <span data-ttu-id="29598-162">3 : appeler.</span><span class="sxs-lookup"><span data-stu-id="29598-162">3: Call.</span></span>
<span data-ttu-id="29598-163">L’authentification est effectuée uniquement au début de chaque appel lorsque l’application reçoit la demande.</span><span class="sxs-lookup"><span data-stu-id="29598-163">Authentication is performed only at the start of each call when the application receives the request.</span></span>
- <span data-ttu-id="29598-164">4 : paquet.</span><span class="sxs-lookup"><span data-stu-id="29598-164">4: Packet.</span></span>
<span data-ttu-id="29598-165">L’authentification est effectuée sur toutes les données reçues du client.</span><span class="sxs-lookup"><span data-stu-id="29598-165">Authentication is performed on all the data that is received from the client.</span></span>
- <span data-ttu-id="29598-166">5 : PacketIntegrity.</span><span class="sxs-lookup"><span data-stu-id="29598-166">5: PacketIntegrity.</span></span>
<span data-ttu-id="29598-167">Toutes les données transférées entre le client et l’application sont authentifiées et vérifiées.</span><span class="sxs-lookup"><span data-stu-id="29598-167">All the data that is transferred between the client and the application is authenticated and verified.</span></span>
- <span data-ttu-id="29598-168">6 : PacketPrivacy.</span><span class="sxs-lookup"><span data-stu-id="29598-168">6: PacketPrivacy.</span></span>
<span data-ttu-id="29598-169">Les propriétés des autres niveaux d’authentification sont utilisées, et toutes les données sont chiffrées.</span><span class="sxs-lookup"><span data-stu-id="29598-169">The properties of the other authentication levels are used, and all the data is encrypted.</span></span>

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

### <span data-ttu-id="29598-170">-Autorité</span><span class="sxs-lookup"><span data-stu-id="29598-170">-Authority</span></span>
<span data-ttu-id="29598-171">Spécifie l'autorité à utiliser pour authentifier la connexion WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-171">Specifies the authority to use to authenticate the WMI connection.</span></span>
<span data-ttu-id="29598-172">Vous pouvez spécifier l'authentification Kerberos ou NTLM standard.</span><span class="sxs-lookup"><span data-stu-id="29598-172">You can specify standard NTLM or Kerberos authentication.</span></span>
<span data-ttu-id="29598-173">Pour utiliser NTLM, affectez au paramètre d'autorité la valeur ntlmdomain:\<DomainName\>, où \<DomainName\> identifie un nom de domaine NTLM valide.</span><span class="sxs-lookup"><span data-stu-id="29598-173">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span>
<span data-ttu-id="29598-174">Pour utiliser Kerberos, spécifiez Kerberos : \<DomainName\> \\ \<ServerName\> .</span><span class="sxs-lookup"><span data-stu-id="29598-174">To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>.</span></span>
<span data-ttu-id="29598-175">Vous ne pouvez pas inclure le paramètre d'autorité lorsque vous vous connectez à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="29598-175">You cannot include the authority setting when you connect to the local computer.</span></span>

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

### <span data-ttu-id="29598-176">-Classe</span><span class="sxs-lookup"><span data-stu-id="29598-176">-Class</span></span>
<span data-ttu-id="29598-177">Spécifie le nom d'une classe WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-177">Specifies the name of a WMI class.</span></span>

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

### <span data-ttu-id="29598-178">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="29598-178">-ComputerName</span></span>
<span data-ttu-id="29598-179">Spécifie le nom de l’ordinateur sur lequel cette applet de commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="29598-179">Specifies the name of the computer on which this cmdlet runs.</span></span>
<span data-ttu-id="29598-180">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="29598-180">The default is the local computer.</span></span>

<span data-ttu-id="29598-181">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ou de plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="29598-181">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span>
<span data-ttu-id="29598-182">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.</span><span class="sxs-lookup"><span data-stu-id="29598-182">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="29598-183">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29598-183">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="29598-184">Vous pouvez utiliser le paramètre *ComputerName* même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="29598-184">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

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

### <span data-ttu-id="29598-185">-Credential</span><span class="sxs-lookup"><span data-stu-id="29598-185">-Credential</span></span>
<span data-ttu-id="29598-186">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="29598-186">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="29598-187">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="29598-187">The default is the current user.</span></span>

<span data-ttu-id="29598-188">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="29598-188">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="29598-189">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="29598-189">If you type a user name, this cmdlet prompts for a password.</span></span>

<span data-ttu-id="29598-190">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec le paramètre n’est pas pris en charge par les fournisseurs installés avec Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29598-190">This parameter is not supported by any providers installed with parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="29598-191">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="29598-191">-EnableAllPrivileges</span></span>
<span data-ttu-id="29598-192">Indique que cette applet de commande active toutes les autorisations de l’utilisateur actuel avant la commande qu’il effectue l’appel WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-192">Indicates that this cmdlet enables all the permissions of the current user before the command it makes the WMI call.</span></span>

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

### <span data-ttu-id="29598-193">-Emprunt d’identité</span><span class="sxs-lookup"><span data-stu-id="29598-193">-Impersonation</span></span>
<span data-ttu-id="29598-194">Spécifie le niveau d'emprunt d'identité à utiliser.</span><span class="sxs-lookup"><span data-stu-id="29598-194">Specifies the impersonation level to use.</span></span>
<span data-ttu-id="29598-195">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="29598-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="29598-196">0 : Default.</span><span class="sxs-lookup"><span data-stu-id="29598-196">0: Default.</span></span>
<span data-ttu-id="29598-197">Lit le registre local pour le niveau d’emprunt d’identité par défaut, qui est généralement défini sur 3 : Impersonate.</span><span class="sxs-lookup"><span data-stu-id="29598-197">Reads the local registry for the default impersonation level, which is usually set to 3: Impersonate.</span></span>
- <span data-ttu-id="29598-198">1 : Anonymous.</span><span class="sxs-lookup"><span data-stu-id="29598-198">1: Anonymous.</span></span>
<span data-ttu-id="29598-199">Masque les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="29598-199">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="29598-200">2 : Identify.</span><span class="sxs-lookup"><span data-stu-id="29598-200">2: Identify.</span></span>
<span data-ttu-id="29598-201">Permet aux objets d'interroger les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="29598-201">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="29598-202">3 : Impersonate.</span><span class="sxs-lookup"><span data-stu-id="29598-202">3: Impersonate.</span></span>
<span data-ttu-id="29598-203">Permet aux objets d'utiliser les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="29598-203">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="29598-204">4 : Delegate.</span><span class="sxs-lookup"><span data-stu-id="29598-204">4: Delegate.</span></span>
<span data-ttu-id="29598-205">Permet aux objets d'autoriser d'autres objets à utiliser les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="29598-205">Allows objects to permit other objects to use the credentials of the caller.</span></span>

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

### <span data-ttu-id="29598-206">-InputObject</span><span class="sxs-lookup"><span data-stu-id="29598-206">-InputObject</span></span>
<span data-ttu-id="29598-207">Spécifie un objet **ManagementObject** à utiliser comme entrée.</span><span class="sxs-lookup"><span data-stu-id="29598-207">Specifies a **ManagementObject** object to use as input.</span></span>
<span data-ttu-id="29598-208">Lorsque ce paramètre est utilisé, tous les autres paramètres, à l’exception du paramètre *arguments* , sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="29598-208">When this parameter is used, all other parameters ,except the *Arguments* parameter, are ignored.</span></span>

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

### <span data-ttu-id="29598-209">Paramètres régionaux</span><span class="sxs-lookup"><span data-stu-id="29598-209">-Locale</span></span>
<span data-ttu-id="29598-210">Spécifie les paramètres régionaux par défaut pour les objets WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-210">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="29598-211">Les paramètres *régionaux* sont spécifiés dans un tableau au format MS_ \<LCID\> dans l’ordre par défaut.</span><span class="sxs-lookup"><span data-stu-id="29598-211">The *Locale* parameter is specified in an array in the MS_\<LCID\> format in the preferred order.</span></span>

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

### <span data-ttu-id="29598-212">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="29598-212">-Namespace</span></span>
<span data-ttu-id="29598-213">Spécifie l’espace de noms de l’espace de stockage WMI dans lequel se trouve la classe WMI référencée lorsqu’elle est utilisée avec le paramètre de *classe* .</span><span class="sxs-lookup"><span data-stu-id="29598-213">Specifies the WMI repository namespace where the referenced WMI class is located when it is used with the *Class* parameter.</span></span>

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

### <span data-ttu-id="29598-214">-Path</span><span class="sxs-lookup"><span data-stu-id="29598-214">-Path</span></span>
<span data-ttu-id="29598-215">Spécifie un chemin d’accès d’objet WMI de l’instance que vous souhaitez créer ou mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="29598-215">Specifies a WMI object path of the instance that you want to create or update.</span></span>

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

### <span data-ttu-id="29598-216">-PutType</span><span class="sxs-lookup"><span data-stu-id="29598-216">-PutType</span></span>
<span data-ttu-id="29598-217">Indique s’il convient de créer ou de mettre à jour l’instance WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-217">Indicates whether to create or update the WMI instance.</span></span>
<span data-ttu-id="29598-218">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="29598-218">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="29598-219">UpdateOnly.</span><span class="sxs-lookup"><span data-stu-id="29598-219">UpdateOnly.</span></span>
<span data-ttu-id="29598-220">met à jour une instance WMI existante.</span><span class="sxs-lookup"><span data-stu-id="29598-220">Updates an existing WMI instance.</span></span>
- <span data-ttu-id="29598-221">CreateOnly.</span><span class="sxs-lookup"><span data-stu-id="29598-221">CreateOnly.</span></span>
<span data-ttu-id="29598-222">crée une instance WMI.</span><span class="sxs-lookup"><span data-stu-id="29598-222">Creates a new WMI instance.</span></span>
- <span data-ttu-id="29598-223">UpdateOrCreate.</span><span class="sxs-lookup"><span data-stu-id="29598-223">UpdateOrCreate.</span></span>
<span data-ttu-id="29598-224">met à jour l'instance WMI si elle existe, ou crée une instance s'il n'existe aucune instance.</span><span class="sxs-lookup"><span data-stu-id="29598-224">Updates the WMI instance if it exists or creates a new instance if an instance does not exist.</span></span>

```yaml
Type: System.Management.PutType
Parameter Sets: (All)
Aliases:
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29598-225">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="29598-225">-ThrottleLimit</span></span>
<span data-ttu-id="29598-226">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="29598-226">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="29598-227">Ce paramètre est utilisé conjointement avec le paramètre *AsJob* .</span><span class="sxs-lookup"><span data-stu-id="29598-227">This parameter is used together with the *AsJob* parameter.</span></span>
<span data-ttu-id="29598-228">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29598-228">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="29598-229">-Confirm</span><span class="sxs-lookup"><span data-stu-id="29598-229">-Confirm</span></span>
<span data-ttu-id="29598-230">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="29598-230">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="29598-231">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="29598-231">-WhatIf</span></span>
<span data-ttu-id="29598-232">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="29598-232">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="29598-233">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="29598-233">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="29598-234">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="29598-234">CommonParameters</span></span>
<span data-ttu-id="29598-235">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="29598-235">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="29598-236">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="29598-236">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="29598-237">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="29598-237">INPUTS</span></span>

### <span data-ttu-id="29598-238">Aucun</span><span class="sxs-lookup"><span data-stu-id="29598-238">None</span></span>
<span data-ttu-id="29598-239">Cette applet de commande n'accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="29598-239">This cmdlet does not accept input.</span></span>

## <span data-ttu-id="29598-240">SORTIES</span><span class="sxs-lookup"><span data-stu-id="29598-240">OUTPUTS</span></span>

### <span data-ttu-id="29598-241">Aucun</span><span class="sxs-lookup"><span data-stu-id="29598-241">None</span></span>
<span data-ttu-id="29598-242">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="29598-242">This cmdlet does not generate output.</span></span>

## <span data-ttu-id="29598-243">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="29598-243">NOTES</span></span>

## <span data-ttu-id="29598-244">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="29598-244">RELATED LINKS</span></span>

[<span data-ttu-id="29598-245">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="29598-245">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="29598-246">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="29598-246">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="29598-247">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="29598-247">Remove-WmiObject</span></span>](Remove-WmiObject.md)
