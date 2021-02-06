---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: 0c6cac03f1acbda35069780f0c53eaf6685813ff
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598370"
---
# <span data-ttu-id="87b67-102">Set-Service</span><span class="sxs-lookup"><span data-stu-id="87b67-102">Set-Service</span></span>

## <span data-ttu-id="87b67-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="87b67-103">SYNOPSIS</span></span>
<span data-ttu-id="87b67-104">Démarre, arrête et interrompt un service, puis modifie ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="87b67-104">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="87b67-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="87b67-105">SYNTAX</span></span>

### <span data-ttu-id="87b67-106">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="87b67-106">Name (Default)</span></span>

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="87b67-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="87b67-107">InputObject</span></span>

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="87b67-108">Description</span><span class="sxs-lookup"><span data-stu-id="87b67-108">DESCRIPTION</span></span>

<span data-ttu-id="87b67-109">L' `Set-Service` applet de commande modifie les propriétés d’un service, telles que l' **État**, la **Description**, **DisplayName** et **startupType**.</span><span class="sxs-lookup"><span data-stu-id="87b67-109">The `Set-Service` cmdlet changes the properties of a service such as the **Status**, **Description**, **DisplayName**, and **StartupType**.</span></span> <span data-ttu-id="87b67-110">`Set-Service` permet de démarrer, d’arrêter, de suspendre ou de suspendre un service.</span><span class="sxs-lookup"><span data-stu-id="87b67-110">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="87b67-111">Pour identifier un service, entrez son nom de service ou envoyez un objet de service.</span><span class="sxs-lookup"><span data-stu-id="87b67-111">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="87b67-112">Ou, envoyez un nom de service ou un objet de service dans le pipeline à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="87b67-112">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="87b67-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="87b67-113">EXAMPLES</span></span>

### <span data-ttu-id="87b67-114">Exemple 1 : modifier un nom complet</span><span class="sxs-lookup"><span data-stu-id="87b67-114">Example 1: Change a display name</span></span>

<span data-ttu-id="87b67-115">Dans cet exemple, le nom complet d’un service est modifié.</span><span class="sxs-lookup"><span data-stu-id="87b67-115">In this example, a service's display name is changed.</span></span> <span data-ttu-id="87b67-116">Pour afficher le nom d’affichage d’origine, utilisez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="87b67-116">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="87b67-117">`Set-Service` utilise le paramètre **Name** pour spécifier le nom du service, **LanmanWorkstation**.</span><span class="sxs-lookup"><span data-stu-id="87b67-117">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation**.</span></span> <span data-ttu-id="87b67-118">Le paramètre **DisplayName** spécifie le nouveau nom complet, la **station de travail LanMan**.</span><span class="sxs-lookup"><span data-stu-id="87b67-118">The **DisplayName** parameter specifies the new display name, **LanMan Workstation**.</span></span>

### <span data-ttu-id="87b67-119">Exemple 2 : modifier le type de démarrage des services</span><span class="sxs-lookup"><span data-stu-id="87b67-119">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="87b67-120">Cet exemple montre comment modifier le type de démarrage d’un service.</span><span class="sxs-lookup"><span data-stu-id="87b67-120">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="87b67-121">`Set-Service` utilise le paramètre **Name** pour spécifier le nom du service, **bits**.</span><span class="sxs-lookup"><span data-stu-id="87b67-121">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS**.</span></span> <span data-ttu-id="87b67-122">Le paramètre **startupType** définit le service sur **Automatic**.</span><span class="sxs-lookup"><span data-stu-id="87b67-122">The **StartupType** parameter sets the service to **Automatic**.</span></span>

<span data-ttu-id="87b67-123">`Get-Service` utilise le paramètre **Name** pour spécifier le service **bits** et envoie l’objet vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="87b67-123">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="87b67-124">`Select-Object` utilise le paramètre **Property** pour afficher l’état du service **bits** .</span><span class="sxs-lookup"><span data-stu-id="87b67-124">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="87b67-125">Exemple 3 : modifier la description d’un service</span><span class="sxs-lookup"><span data-stu-id="87b67-125">Example 3: Change the description of a service</span></span>

<span data-ttu-id="87b67-126">Cet exemple modifie la description du service BITS et affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="87b67-126">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="87b67-127">L' `Get-CimInstance` applet de commande est utilisée car elle retourne un objet **Win32_Service** qui comprend la **Description** du service.</span><span class="sxs-lookup"><span data-stu-id="87b67-127">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description**.</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

<span data-ttu-id="87b67-128">`Get-CimInstance` envoie l’objet dans le pipeline à `Format-List` et affiche le nom et la description du service.</span><span class="sxs-lookup"><span data-stu-id="87b67-128">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="87b67-129">À des fins de comparaison, la commande est exécutée avant et après la mise à jour de la description.</span><span class="sxs-lookup"><span data-stu-id="87b67-129">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="87b67-130">`Set-Service` utilise le paramètre **Name** pour spécifier le service **bits** .</span><span class="sxs-lookup"><span data-stu-id="87b67-130">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="87b67-131">Le paramètre **Description** spécifie le texte mis à jour pour la description des services.</span><span class="sxs-lookup"><span data-stu-id="87b67-131">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="87b67-132">Exemple 4 : démarrer un service</span><span class="sxs-lookup"><span data-stu-id="87b67-132">Example 4: Start a service</span></span>

<span data-ttu-id="87b67-133">Dans cet exemple, un service est démarré.</span><span class="sxs-lookup"><span data-stu-id="87b67-133">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="87b67-134">`Set-Service` utilise le paramètre **Name** pour spécifier le service, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="87b67-134">`Set-Service` uses the **Name** parameter to specify the service, **WinRM**.</span></span> <span data-ttu-id="87b67-135">Le paramètre **Status** utilise la valeur **en cours d’exécution** pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="87b67-135">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="87b67-136">Le paramètre **PassThru** génère un objet **ServiceController** qui affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="87b67-136">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="87b67-137">Exemple 5 : suspendre un service</span><span class="sxs-lookup"><span data-stu-id="87b67-137">Example 5: Suspend a service</span></span>

<span data-ttu-id="87b67-138">Cet exemple utilise le pipeline pour suspendre le service.</span><span class="sxs-lookup"><span data-stu-id="87b67-138">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="87b67-139">`Get-Service` utilise le paramètre **Name** pour spécifier le service de **planification** et envoie l’objet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="87b67-139">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="87b67-140">`Set-Service` utilise le paramètre **Status** pour définir le service comme étant **suspendu**.</span><span class="sxs-lookup"><span data-stu-id="87b67-140">`Set-Service` uses the **Status** parameter to set the service to **Paused**.</span></span>

### <span data-ttu-id="87b67-141">Exemple 6 : arrêter un service</span><span class="sxs-lookup"><span data-stu-id="87b67-141">Example 6: Stop a service</span></span>

<span data-ttu-id="87b67-142">Cet exemple utilise une variable pour arrêter un service.</span><span class="sxs-lookup"><span data-stu-id="87b67-142">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="87b67-143">`Get-Service` utilise le paramètre **Name** pour spécifier le service, **Schedule**.</span><span class="sxs-lookup"><span data-stu-id="87b67-143">`Get-Service` uses the **Name** parameter to specify the service, **Schedule**.</span></span> <span data-ttu-id="87b67-144">L’objet est stocké dans la variable, `$S` .</span><span class="sxs-lookup"><span data-stu-id="87b67-144">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="87b67-145">`Set-Service` utilise le paramètre **InputObject** et spécifie l’objet stocké `$S` .</span><span class="sxs-lookup"><span data-stu-id="87b67-145">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="87b67-146">Le paramètre **Status** définit le service sur **Stopped**.</span><span class="sxs-lookup"><span data-stu-id="87b67-146">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="87b67-147">Exemple 7 : arrêter un service sur un système distant</span><span class="sxs-lookup"><span data-stu-id="87b67-147">Example 7: Stop a service on a remote system</span></span>

<span data-ttu-id="87b67-148">Cet exemple arrête un service sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="87b67-148">This example stops a service on a remote computer.</span></span>
<span data-ttu-id="87b67-149">Pour plus d’informations, consultez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="87b67-149">For more information, see [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

<span data-ttu-id="87b67-150">`Get-Credential` demande un nom d’utilisateur et un mot de passe, puis stocke les informations d’identification dans la `$Cred` variable.</span><span class="sxs-lookup"><span data-stu-id="87b67-150">`Get-Credential` prompts for a username and password, and stores the credentials in the `$Cred` variable.</span></span> <span data-ttu-id="87b67-151">`Get-Service` utilise le paramètre **Name** pour spécifier le service de **planification** .</span><span class="sxs-lookup"><span data-stu-id="87b67-151">`Get-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="87b67-152">L’objet est stocké dans la variable, `$S` .</span><span class="sxs-lookup"><span data-stu-id="87b67-152">The object is stored in the variable, `$S`.</span></span>

<span data-ttu-id="87b67-153">`Invoke-Command` utilise le paramètre **ComputerName** pour spécifier un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="87b67-153">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer.</span></span> <span data-ttu-id="87b67-154">Le paramètre **Credential** utilise la `$Cred` variable pour se connecter à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="87b67-154">The **Credential** parameter uses the `$Cred` variable to sign on to the computer.</span></span> <span data-ttu-id="87b67-155">Le **scriptblock** appelle `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="87b67-155">The **ScriptBlock** calls `Set-Service`.</span></span> <span data-ttu-id="87b67-156">Le paramètre **InputObject** spécifie l’objet de service stocké `$S` .</span><span class="sxs-lookup"><span data-stu-id="87b67-156">The **InputObject** parameter specifies the service object stored `$S`.</span></span> <span data-ttu-id="87b67-157">Le paramètre **Status** définit le service sur **Stopped**.</span><span class="sxs-lookup"><span data-stu-id="87b67-157">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="87b67-158">Exemple 8 : modifier les informations d’identification d’un service</span><span class="sxs-lookup"><span data-stu-id="87b67-158">Example 8: Change credential of a service</span></span>

<span data-ttu-id="87b67-159">Cet exemple modifie les informations d’identification utilisées pour gérer un service.</span><span class="sxs-lookup"><span data-stu-id="87b67-159">This example changes the credentials that are used to manage a service.</span></span>

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

<span data-ttu-id="87b67-160">`Get-Credential` demande un nom d’utilisateur et un mot de passe, puis stocke les informations d’identification dans la `$credential` variable.</span><span class="sxs-lookup"><span data-stu-id="87b67-160">`Get-Credential` prompts for a username and password, and stores the credentials in the `$credential` variable.</span></span> <span data-ttu-id="87b67-161">`Set-Service` utilise le paramètre **Name** pour spécifier le service de **planification** .</span><span class="sxs-lookup"><span data-stu-id="87b67-161">`Set-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="87b67-162">Le paramètre **Credential** utilise la `$credential` variable et met à jour le service de **planification** .</span><span class="sxs-lookup"><span data-stu-id="87b67-162">The **Credential** parameter uses the `$credential` variable and updates the **Schedule** service.</span></span>

### <span data-ttu-id="87b67-163">Exemple 9 : modifier le SecurityDescriptor d’un service</span><span class="sxs-lookup"><span data-stu-id="87b67-163">Example 9: Change the SecurityDescriptor of a service</span></span>

<span data-ttu-id="87b67-164">Cet exemple modifie le **SecurityDescriptor** d’un service.</span><span class="sxs-lookup"><span data-stu-id="87b67-164">This example changes a service's **SecurityDescriptor**.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

<span data-ttu-id="87b67-165">Le **SecurityDescriptor** est stocké dans la `$SDDL` variable.</span><span class="sxs-lookup"><span data-stu-id="87b67-165">The **SecurityDescriptor** is stored in the `$SDDL` variable.</span></span> <span data-ttu-id="87b67-166">`Set-Service` utilise le paramètre **Name** pour spécifier le service **bits** .</span><span class="sxs-lookup"><span data-stu-id="87b67-166">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="87b67-167">Le paramètre **SecurityDescriptorSddl** utilise `$SDDL` pour modifier le **SecurityDescriptor** du service **bits** .</span><span class="sxs-lookup"><span data-stu-id="87b67-167">The **SecurityDescriptorSddl** parameter uses `$SDDL` to change the **SecurityDescriptor** for the **BITS** service.</span></span>

## <span data-ttu-id="87b67-168">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="87b67-168">PARAMETERS</span></span>

### <span data-ttu-id="87b67-169">-Confirm</span><span class="sxs-lookup"><span data-stu-id="87b67-169">-Confirm</span></span>

<span data-ttu-id="87b67-170">Vous invite à confirmer l’exécution `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="87b67-170">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="87b67-171">-Credential</span><span class="sxs-lookup"><span data-stu-id="87b67-171">-Credential</span></span>

<span data-ttu-id="87b67-172">Spécifie le compte utilisé par le service comme [compte d’ouverture de session du service](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="87b67-172">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="87b67-173">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="87b67-173">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="87b67-174">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="87b67-174">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="87b67-175">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="87b67-175">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="87b67-176">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="87b67-176">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="87b67-177">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="87b67-177">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="87b67-178">Description</span><span class="sxs-lookup"><span data-stu-id="87b67-178">-Description</span></span>

<span data-ttu-id="87b67-179">Spécifie une nouvelle description pour le service.</span><span class="sxs-lookup"><span data-stu-id="87b67-179">Specifies a new description for the service.</span></span>

<span data-ttu-id="87b67-180">La description du service s’affiche dans gestion de l' **ordinateur, services**.</span><span class="sxs-lookup"><span data-stu-id="87b67-180">The service description appears in **Computer Management, Services**.</span></span> <span data-ttu-id="87b67-181">La **Description** n’est pas une propriété de l' `Get-Service` objet **ServiceController** .</span><span class="sxs-lookup"><span data-stu-id="87b67-181">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="87b67-182">Pour afficher la description du service, utilisez `Get-CimInstance` qui retourne un objet **Win32_Service** qui représente le service.</span><span class="sxs-lookup"><span data-stu-id="87b67-182">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

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

### <span data-ttu-id="87b67-183">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="87b67-183">-DisplayName</span></span>

<span data-ttu-id="87b67-184">Spécifie le nouveau nom d'affichage du service.</span><span class="sxs-lookup"><span data-stu-id="87b67-184">Specifies a new display name for the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87b67-185">-Force</span><span class="sxs-lookup"><span data-stu-id="87b67-185">-Force</span></span>

<span data-ttu-id="87b67-186">Spécifie le mode d’arrêt du service.</span><span class="sxs-lookup"><span data-stu-id="87b67-186">Specifies the Stop mode of the service.</span></span> <span data-ttu-id="87b67-187">Ce paramètre fonctionne uniquement lorsque `-Status Stopped` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="87b67-187">This parameter only works when `-Status Stopped` is used.</span></span> <span data-ttu-id="87b67-188">S' `Set-Service` il est activé, arrête les services dépendants avant l’arrêt du service cible.</span><span class="sxs-lookup"><span data-stu-id="87b67-188">If enabled, `Set-Service` stops the dependent services before the target service is stopped.</span></span> <span data-ttu-id="87b67-189">Par défaut, les exceptions sont levées quand d’autres services en cours d’exécution dépendent du service cible.</span><span class="sxs-lookup"><span data-stu-id="87b67-189">By default, exceptions are raised when other running services depend on the target service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87b67-190">-InputObject</span><span class="sxs-lookup"><span data-stu-id="87b67-190">-InputObject</span></span>

<span data-ttu-id="87b67-191">Spécifie un objet **ServiceController** qui représente le service à modifier.</span><span class="sxs-lookup"><span data-stu-id="87b67-191">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="87b67-192">Entrez une variable qui contient l’objet ou tapez une commande ou une expression qui obtient l’objet, par exemple une `Get-Service` commande.</span><span class="sxs-lookup"><span data-stu-id="87b67-192">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="87b67-193">Vous pouvez utiliser le pipeline pour envoyer un objet de service à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="87b67-193">You can use the pipeline to send a service object to `Set-Service`.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="87b67-194">-Name</span><span class="sxs-lookup"><span data-stu-id="87b67-194">-Name</span></span>

<span data-ttu-id="87b67-195">Spécifie le nom du service à modifier.</span><span class="sxs-lookup"><span data-stu-id="87b67-195">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="87b67-196">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="87b67-196">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="87b67-197">Vous pouvez utiliser le pipeline pour envoyer un nom de service à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="87b67-197">You can use the pipeline to send a service name to `Set-Service`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="87b67-198">-PassThru</span><span class="sxs-lookup"><span data-stu-id="87b67-198">-PassThru</span></span>

<span data-ttu-id="87b67-199">Retourne un objet **ServiceController** qui représente les services qui ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="87b67-199">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="87b67-200">Par défaut, `Set-Service` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="87b67-200">By default, `Set-Service` doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87b67-201">-StartupType</span><span class="sxs-lookup"><span data-stu-id="87b67-201">-StartupType</span></span>

<span data-ttu-id="87b67-202">Spécifie le mode de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="87b67-202">Specifies the start mode of the service.</span></span>

<span data-ttu-id="87b67-203">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="87b67-203">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="87b67-204">**Automatique** -le service est démarré ou a été démarré par le système d’exploitation au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="87b67-204">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="87b67-205">Si un service démarré automatiquement dépend d'un service démarré manuellement, le service démarré manuellement est également démarré automatiquement au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="87b67-205">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="87b67-206">**AutomaticDelayedStart** -démarre peu après le démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="87b67-206">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="87b67-207">**Désactivé** : le service est désactivé et ne peut pas être démarré par un utilisateur ou une application.</span><span class="sxs-lookup"><span data-stu-id="87b67-207">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="87b67-208">**InvalidValue** -n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="87b67-208">**InvalidValue** - Has no effect.</span></span> <span data-ttu-id="87b67-209">L’applet de commande ne retourne pas d’erreur, mais le StartupType du service n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="87b67-209">The cmdlet does not return an error but the StartupType of the service is not changed.</span></span>
- <span data-ttu-id="87b67-210">**Manuel** : le service est démarré uniquement manuellement, par un utilisateur, à l’aide du gestionnaire de contrôle des services ou par une application.</span><span class="sxs-lookup"><span data-stu-id="87b67-210">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases: StartMode, SM, ST, StartType
Accepted values: Automatic, AutomaticDelayedStart, Disabled, InvalidValue, Manual

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87b67-211">-État</span><span class="sxs-lookup"><span data-stu-id="87b67-211">-Status</span></span>

<span data-ttu-id="87b67-212">Spécifie l’état du service.</span><span class="sxs-lookup"><span data-stu-id="87b67-212">Specifies the status for the service.</span></span>

<span data-ttu-id="87b67-213">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="87b67-213">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="87b67-214">**Suspendu**.</span><span class="sxs-lookup"><span data-stu-id="87b67-214">**Paused**.</span></span> <span data-ttu-id="87b67-215">suspend le service.</span><span class="sxs-lookup"><span data-stu-id="87b67-215">Suspends the service.</span></span>
- <span data-ttu-id="87b67-216">**Exécution en cours**.</span><span class="sxs-lookup"><span data-stu-id="87b67-216">**Running**.</span></span> <span data-ttu-id="87b67-217">démarre le service.</span><span class="sxs-lookup"><span data-stu-id="87b67-217">Starts the service.</span></span>
- <span data-ttu-id="87b67-218">**Arrêté**.</span><span class="sxs-lookup"><span data-stu-id="87b67-218">**Stopped**.</span></span> <span data-ttu-id="87b67-219">arrête le service.</span><span class="sxs-lookup"><span data-stu-id="87b67-219">Stops the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87b67-220">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="87b67-220">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="87b67-221">Spécifie le **SecurityDescriptor** du service au format **SDDL** .</span><span class="sxs-lookup"><span data-stu-id="87b67-221">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87b67-222">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="87b67-222">-WhatIf</span></span>

<span data-ttu-id="87b67-223">Montre ce qui se passe si `Set-Service` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="87b67-223">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="87b67-224">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="87b67-224">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="87b67-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="87b67-225">CommonParameters</span></span>

<span data-ttu-id="87b67-226">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="87b67-226">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="87b67-227">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="87b67-227">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="87b67-228">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="87b67-228">INPUTS</span></span>

### <span data-ttu-id="87b67-229">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="87b67-229">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="87b67-230">Vous pouvez utiliser le pipeline pour envoyer un objet de service ou une chaîne qui contient un nom de service à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="87b67-230">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="87b67-231">SORTIES</span><span class="sxs-lookup"><span data-stu-id="87b67-231">OUTPUTS</span></span>

### <span data-ttu-id="87b67-232">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="87b67-232">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="87b67-233">Par défaut, `Set-Service` ne retourne aucun objet.</span><span class="sxs-lookup"><span data-stu-id="87b67-233">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="87b67-234">Utilisez le paramètre **PassThru** pour générer un objet **ServiceController** .</span><span class="sxs-lookup"><span data-stu-id="87b67-234">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="87b67-235">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="87b67-235">NOTES</span></span>

<span data-ttu-id="87b67-236">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="87b67-236">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="87b67-237">`Set-Service` requiert des autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="87b67-237">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="87b67-238">Utilisez l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="87b67-238">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="87b67-239">`Set-Service` ne peut contrôler des services que si l’utilisateur actuel dispose des autorisations nécessaires pour gérer les services.</span><span class="sxs-lookup"><span data-stu-id="87b67-239">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="87b67-240">Si une commande ne fonctionne pas correctement, vous ne disposez peut-être pas des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="87b67-240">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="87b67-241">Pour rechercher le nom de service ou le nom d’affichage d’un service, utilisez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="87b67-241">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="87b67-242">Les noms de service figurent dans la colonne **nom** et les noms complets sont dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="87b67-242">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="87b67-243">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="87b67-243">RELATED LINKS</span></span>

[<span data-ttu-id="87b67-244">Get-Service</span><span class="sxs-lookup"><span data-stu-id="87b67-244">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="87b67-245">New-Service</span><span class="sxs-lookup"><span data-stu-id="87b67-245">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="87b67-246">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="87b67-246">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="87b67-247">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="87b67-247">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="87b67-248">Start-Service</span><span class="sxs-lookup"><span data-stu-id="87b67-248">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="87b67-249">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="87b67-249">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="87b67-250">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="87b67-250">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="87b67-251">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="87b67-251">Remove-Service</span></span>](Remove-Service.md)
