---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: c6aa8a16bd5ccbeb00252b872e997018b1997181
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346698"
---
# <span data-ttu-id="57ab5-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="57ab5-103">Set-Service</span></span>

## <span data-ttu-id="57ab5-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="57ab5-104">SYNOPSIS</span></span>
<span data-ttu-id="57ab5-105">Démarre, arrête et interrompt un service, puis modifie ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="57ab5-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="57ab5-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="57ab5-106">SYNTAX</span></span>

### <span data-ttu-id="57ab5-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="57ab5-107">Name (Default)</span></span>

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="57ab5-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="57ab5-108">InputObject</span></span>

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="57ab5-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="57ab5-109">DESCRIPTION</span></span>

<span data-ttu-id="57ab5-110">L' `Set-Service` applet de commande modifie les propriétés d’un service, telles que l' **État** , la **Description** , **DisplayName** et **startupType**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType**.</span></span> <span data-ttu-id="57ab5-111">`Set-Service` permet de démarrer, d’arrêter, de suspendre ou de suspendre un service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="57ab5-112">Pour identifier un service, entrez son nom de service ou envoyez un objet de service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="57ab5-113">Ou, envoyez un nom de service ou un objet de service dans le pipeline à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="57ab5-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="57ab5-114">EXAMPLES</span></span>

### <span data-ttu-id="57ab5-115">Exemple 1 : modifier un nom complet</span><span class="sxs-lookup"><span data-stu-id="57ab5-115">Example 1: Change a display name</span></span>

<span data-ttu-id="57ab5-116">Dans cet exemple, le nom complet d’un service est modifié.</span><span class="sxs-lookup"><span data-stu-id="57ab5-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="57ab5-117">Pour afficher le nom d’affichage d’origine, utilisez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="57ab5-118">`Set-Service` utilise le paramètre **Name** pour spécifier le nom du service, **LanmanWorkstation**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation**.</span></span> <span data-ttu-id="57ab5-119">Le paramètre **DisplayName** spécifie le nouveau nom complet, la **station de travail LanMan**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation**.</span></span>

### <span data-ttu-id="57ab5-120">Exemple 2 : modifier le type de démarrage des services</span><span class="sxs-lookup"><span data-stu-id="57ab5-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="57ab5-121">Cet exemple montre comment modifier le type de démarrage d’un service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="57ab5-122">`Set-Service` utilise le paramètre **Name** pour spécifier le nom du service, **bits**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS**.</span></span> <span data-ttu-id="57ab5-123">Le paramètre **startupType** définit le service sur **Automatic**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-123">The **StartupType** parameter sets the service to **Automatic**.</span></span>

<span data-ttu-id="57ab5-124">`Get-Service` utilise le paramètre **Name** pour spécifier le service **bits** et envoie l’objet vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="57ab5-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="57ab5-125">`Select-Object` utilise le paramètre **Property** pour afficher l’état du service **bits** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="57ab5-126">Exemple 3 : modifier la description d’un service</span><span class="sxs-lookup"><span data-stu-id="57ab5-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="57ab5-127">Cet exemple modifie la description du service BITS et affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="57ab5-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="57ab5-128">L' `Get-CimInstance` applet de commande est utilisée car elle retourne un objet **Win32_Service** qui comprend la **Description** du service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description**.</span></span>

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

<span data-ttu-id="57ab5-129">`Get-CimInstance` envoie l’objet dans le pipeline à `Format-List` et affiche le nom et la description du service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="57ab5-130">À des fins de comparaison, la commande est exécutée avant et après la mise à jour de la description.</span><span class="sxs-lookup"><span data-stu-id="57ab5-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="57ab5-131">`Set-Service` utilise le paramètre **Name** pour spécifier le service **bits** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="57ab5-132">Le paramètre **Description** spécifie le texte mis à jour pour la description des services.</span><span class="sxs-lookup"><span data-stu-id="57ab5-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="57ab5-133">Exemple 4 : démarrer un service</span><span class="sxs-lookup"><span data-stu-id="57ab5-133">Example 4: Start a service</span></span>

<span data-ttu-id="57ab5-134">Dans cet exemple, un service est démarré.</span><span class="sxs-lookup"><span data-stu-id="57ab5-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="57ab5-135">`Set-Service` utilise le paramètre **Name** pour spécifier le service, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM**.</span></span> <span data-ttu-id="57ab5-136">Le paramètre **Status** utilise la valeur **en cours d’exécution** pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="57ab5-137">Le paramètre **PassThru** génère un objet **ServiceController** qui affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="57ab5-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="57ab5-138">Exemple 5 : suspendre un service</span><span class="sxs-lookup"><span data-stu-id="57ab5-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="57ab5-139">Cet exemple utilise le pipeline pour suspendre le service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="57ab5-140">`Get-Service` utilise le paramètre **Name** pour spécifier le service de **planification** et envoie l’objet dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="57ab5-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="57ab5-141">`Set-Service` utilise le paramètre **Status** pour définir le service comme étant **suspendu**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-141">`Set-Service` uses the **Status** parameter to set the service to **Paused**.</span></span>

### <span data-ttu-id="57ab5-142">Exemple 6 : arrêter un service</span><span class="sxs-lookup"><span data-stu-id="57ab5-142">Example 6: Stop a service</span></span>

<span data-ttu-id="57ab5-143">Cet exemple utilise une variable pour arrêter un service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="57ab5-144">`Get-Service` utilise le paramètre **Name** pour spécifier le service, **Schedule**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule**.</span></span> <span data-ttu-id="57ab5-145">L’objet est stocké dans la variable, `$S` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="57ab5-146">`Set-Service` utilise le paramètre **InputObject** et spécifie l’objet stocké `$S` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="57ab5-147">Le paramètre **Status** définit le service sur **Stopped**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-147">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="57ab5-148">Exemple 7 : arrêter un service sur un système distant</span><span class="sxs-lookup"><span data-stu-id="57ab5-148">Example 7: Stop a service on a remote system</span></span>

<span data-ttu-id="57ab5-149">Cet exemple arrête un service sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="57ab5-149">This example stops a service on a remote computer.</span></span>
<span data-ttu-id="57ab5-150">Pour plus d’informations, consultez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="57ab5-150">For more information, see [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

<span data-ttu-id="57ab5-151">`Get-Credential` demande un nom d’utilisateur et un mot de passe, puis stocke les informations d’identification dans la `$Cred` variable.</span><span class="sxs-lookup"><span data-stu-id="57ab5-151">`Get-Credential` prompts for a username and password, and stores the credentials in the `$Cred` variable.</span></span> <span data-ttu-id="57ab5-152">`Get-Service` utilise le paramètre **Name** pour spécifier le service de **planification** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-152">`Get-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="57ab5-153">L’objet est stocké dans la variable, `$S` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-153">The object is stored in the variable, `$S`.</span></span>

<span data-ttu-id="57ab5-154">`Invoke-Command` utilise le paramètre **ComputerName** pour spécifier un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="57ab5-154">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer.</span></span> <span data-ttu-id="57ab5-155">Le paramètre **Credential** utilise la `$Cred` variable pour se connecter à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="57ab5-155">The **Credential** parameter uses the `$Cred` variable to sign on to the computer.</span></span> <span data-ttu-id="57ab5-156">Le **scriptblock** appelle `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-156">The **ScriptBlock** calls `Set-Service`.</span></span> <span data-ttu-id="57ab5-157">Le paramètre **InputObject** spécifie l’objet de service stocké `$S` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-157">The **InputObject** parameter specifies the service object stored `$S`.</span></span> <span data-ttu-id="57ab5-158">Le paramètre **Status** définit le service sur **Stopped**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-158">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="57ab5-159">Exemple 8 : modifier les informations d’identification d’un service</span><span class="sxs-lookup"><span data-stu-id="57ab5-159">Example 8: Change credential of a service</span></span>

<span data-ttu-id="57ab5-160">Cet exemple modifie les informations d’identification utilisées pour gérer un service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-160">This example changes the credentials that are used to manage a service.</span></span>

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

<span data-ttu-id="57ab5-161">`Get-Credential` demande un nom d’utilisateur et un mot de passe, puis stocke les informations d’identification dans la `$credential` variable.</span><span class="sxs-lookup"><span data-stu-id="57ab5-161">`Get-Credential` prompts for a username and password, and stores the credentials in the `$credential` variable.</span></span> <span data-ttu-id="57ab5-162">`Set-Service` utilise le paramètre **Name** pour spécifier le service de **planification** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-162">`Set-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="57ab5-163">Le paramètre **Credential** utilise la `$credential` variable et met à jour le service de **planification** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-163">The **Credential** parameter uses the `$credential` variable and updates the **Schedule** service.</span></span>

### <span data-ttu-id="57ab5-164">Exemple 9 : modifier le SecurityDescriptor d’un service</span><span class="sxs-lookup"><span data-stu-id="57ab5-164">Example 9: Change the SecurityDescriptor of a service</span></span>

<span data-ttu-id="57ab5-165">Cet exemple modifie le **SecurityDescriptor** d’un service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-165">This example changes a service's **SecurityDescriptor**.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

<span data-ttu-id="57ab5-166">Le **SecurityDescriptor** est stocké dans la `$SDDL` variable.</span><span class="sxs-lookup"><span data-stu-id="57ab5-166">The **SecurityDescriptor** is stored in the `$SDDL` variable.</span></span> <span data-ttu-id="57ab5-167">`Set-Service` utilise le paramètre **Name** pour spécifier le service **bits** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-167">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="57ab5-168">Le paramètre **SecurityDescriptorSddl** utilise `$SDDL` pour modifier le **SecurityDescriptor** du service **bits** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-168">The **SecurityDescriptorSddl** parameter uses `$SDDL` to change the **SecurityDescriptor** for the **BITS** service.</span></span>

## <span data-ttu-id="57ab5-169">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="57ab5-169">PARAMETERS</span></span>

### <span data-ttu-id="57ab5-170">-Confirm</span><span class="sxs-lookup"><span data-stu-id="57ab5-170">-Confirm</span></span>

<span data-ttu-id="57ab5-171">Vous invite à confirmer l’exécution `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-171">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="57ab5-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="57ab5-172">-Credential</span></span>

<span data-ttu-id="57ab5-173">Spécifie le compte utilisé par le service comme [compte d’ouverture de session du service](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="57ab5-173">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="57ab5-174">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-174">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="57ab5-175">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="57ab5-175">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="57ab5-176">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="57ab5-176">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="57ab5-177">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="57ab5-177">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="57ab5-178">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="57ab5-178">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="57ab5-179">Description</span><span class="sxs-lookup"><span data-stu-id="57ab5-179">-Description</span></span>

<span data-ttu-id="57ab5-180">Spécifie une nouvelle description pour le service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-180">Specifies a new description for the service.</span></span>

<span data-ttu-id="57ab5-181">La description du service s’affiche dans gestion de l' **ordinateur, services**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-181">The service description appears in **Computer Management, Services**.</span></span> <span data-ttu-id="57ab5-182">La **Description** n’est pas une propriété de l' `Get-Service` objet **ServiceController** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-182">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="57ab5-183">Pour afficher la description du service, utilisez `Get-CimInstance` qui retourne un objet **Win32_Service** qui représente le service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-183">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

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

### <span data-ttu-id="57ab5-184">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="57ab5-184">-DisplayName</span></span>

<span data-ttu-id="57ab5-185">Spécifie le nouveau nom d'affichage du service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-185">Specifies a new display name for the service.</span></span>

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

### <span data-ttu-id="57ab5-186">-Force</span><span class="sxs-lookup"><span data-stu-id="57ab5-186">-Force</span></span>

<span data-ttu-id="57ab5-187">Spécifie le mode d’arrêt du service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-187">Specifies the Stop mode of the service.</span></span> <span data-ttu-id="57ab5-188">Ce paramètre fonctionne uniquement lorsque `-Status Stopped` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="57ab5-188">This parameter only works when `-Status Stopped` is used.</span></span> <span data-ttu-id="57ab5-189">S' `Set-Service` il est activé, arrête les services dépendants avant l’arrêt du service cible.</span><span class="sxs-lookup"><span data-stu-id="57ab5-189">If enabled, `Set-Service` stops the dependent services before the target service is stopped.</span></span> <span data-ttu-id="57ab5-190">Par défaut, les exceptions sont levées quand d’autres services en cours d’exécution dépendent du service cible.</span><span class="sxs-lookup"><span data-stu-id="57ab5-190">By default, exceptions are raised when other running services depend on the target service.</span></span>

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

### <span data-ttu-id="57ab5-191">-InputObject</span><span class="sxs-lookup"><span data-stu-id="57ab5-191">-InputObject</span></span>

<span data-ttu-id="57ab5-192">Spécifie un objet **ServiceController** qui représente le service à modifier.</span><span class="sxs-lookup"><span data-stu-id="57ab5-192">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="57ab5-193">Entrez une variable qui contient l’objet ou tapez une commande ou une expression qui obtient l’objet, par exemple une `Get-Service` commande.</span><span class="sxs-lookup"><span data-stu-id="57ab5-193">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="57ab5-194">Vous pouvez utiliser le pipeline pour envoyer un objet de service à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-194">You can use the pipeline to send a service object to `Set-Service`.</span></span>

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

### <span data-ttu-id="57ab5-195">-Name</span><span class="sxs-lookup"><span data-stu-id="57ab5-195">-Name</span></span>

<span data-ttu-id="57ab5-196">Spécifie le nom du service à modifier.</span><span class="sxs-lookup"><span data-stu-id="57ab5-196">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="57ab5-197">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="57ab5-197">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="57ab5-198">Vous pouvez utiliser le pipeline pour envoyer un nom de service à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-198">You can use the pipeline to send a service name to `Set-Service`.</span></span>

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

### <span data-ttu-id="57ab5-199">-PassThru</span><span class="sxs-lookup"><span data-stu-id="57ab5-199">-PassThru</span></span>

<span data-ttu-id="57ab5-200">Retourne un objet **ServiceController** qui représente les services qui ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="57ab5-200">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="57ab5-201">Par défaut, `Set-Service` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="57ab5-201">By default, `Set-Service` doesn't generate any output.</span></span>

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

### <span data-ttu-id="57ab5-202">-StartupType</span><span class="sxs-lookup"><span data-stu-id="57ab5-202">-StartupType</span></span>

<span data-ttu-id="57ab5-203">Spécifie le mode de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-203">Specifies the start mode of the service.</span></span>

<span data-ttu-id="57ab5-204">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="57ab5-204">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="57ab5-205">**Automatique** -le service est démarré ou a été démarré par le système d’exploitation au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="57ab5-205">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="57ab5-206">Si un service démarré automatiquement dépend d'un service démarré manuellement, le service démarré manuellement est également démarré automatiquement au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="57ab5-206">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="57ab5-207">**AutomaticDelayedStart** -démarre peu après le démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="57ab5-207">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="57ab5-208">**Désactivé** : le service est désactivé et ne peut pas être démarré par un utilisateur ou une application.</span><span class="sxs-lookup"><span data-stu-id="57ab5-208">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="57ab5-209">**InvalidValue** -n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="57ab5-209">**InvalidValue** - Has no effect.</span></span> <span data-ttu-id="57ab5-210">L’applet de commande ne retourne pas d’erreur, mais le StartupType du service n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="57ab5-210">The cmdlet does not return an error but the StartupType of the service is not changed.</span></span>
- <span data-ttu-id="57ab5-211">**Manuel** : le service est démarré uniquement manuellement, par un utilisateur, à l’aide du gestionnaire de contrôle des services ou par une application.</span><span class="sxs-lookup"><span data-stu-id="57ab5-211">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

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

### <span data-ttu-id="57ab5-212">-État</span><span class="sxs-lookup"><span data-stu-id="57ab5-212">-Status</span></span>

<span data-ttu-id="57ab5-213">Spécifie l’état du service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-213">Specifies the status for the service.</span></span>

<span data-ttu-id="57ab5-214">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="57ab5-214">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="57ab5-215">**Suspendu**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-215">**Paused**.</span></span> <span data-ttu-id="57ab5-216">suspend le service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-216">Suspends the service.</span></span>
- <span data-ttu-id="57ab5-217">**Exécution en cours**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-217">**Running**.</span></span> <span data-ttu-id="57ab5-218">démarre le service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-218">Starts the service.</span></span>
- <span data-ttu-id="57ab5-219">**Arrêté**.</span><span class="sxs-lookup"><span data-stu-id="57ab5-219">**Stopped**.</span></span> <span data-ttu-id="57ab5-220">arrête le service.</span><span class="sxs-lookup"><span data-stu-id="57ab5-220">Stops the service.</span></span>

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

### <span data-ttu-id="57ab5-221">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="57ab5-221">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="57ab5-222">Spécifie le **SecurityDescriptor** du service au format **SDDL** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-222">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

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

### <span data-ttu-id="57ab5-223">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="57ab5-223">-WhatIf</span></span>

<span data-ttu-id="57ab5-224">Montre ce qui se passe si `Set-Service` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="57ab5-224">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="57ab5-225">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="57ab5-225">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="57ab5-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="57ab5-226">CommonParameters</span></span>

<span data-ttu-id="57ab5-227">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="57ab5-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="57ab5-228">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="57ab5-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="57ab5-229">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="57ab5-229">INPUTS</span></span>

### <span data-ttu-id="57ab5-230">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="57ab5-230">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="57ab5-231">Vous pouvez utiliser le pipeline pour envoyer un objet de service ou une chaîne qui contient un nom de service à `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-231">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="57ab5-232">SORTIES</span><span class="sxs-lookup"><span data-stu-id="57ab5-232">OUTPUTS</span></span>

### <span data-ttu-id="57ab5-233">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="57ab5-233">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="57ab5-234">Par défaut, `Set-Service` ne retourne aucun objet.</span><span class="sxs-lookup"><span data-stu-id="57ab5-234">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="57ab5-235">Utilisez le paramètre **PassThru** pour générer un objet **ServiceController** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-235">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="57ab5-236">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="57ab5-236">NOTES</span></span>

<span data-ttu-id="57ab5-237">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="57ab5-237">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="57ab5-238">`Set-Service` requiert des autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="57ab5-238">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="57ab5-239">Utilisez l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-239">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="57ab5-240">`Set-Service` ne peut contrôler des services que si l’utilisateur actuel dispose des autorisations nécessaires pour gérer les services.</span><span class="sxs-lookup"><span data-stu-id="57ab5-240">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="57ab5-241">Si une commande ne fonctionne pas correctement, vous ne disposez peut-être pas des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="57ab5-241">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="57ab5-242">Pour rechercher le nom de service ou le nom d’affichage d’un service, utilisez `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="57ab5-242">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="57ab5-243">Les noms de service figurent dans la colonne **nom** et les noms complets sont dans la colonne **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="57ab5-243">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="57ab5-244">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="57ab5-244">RELATED LINKS</span></span>

[<span data-ttu-id="57ab5-245">Get-Service</span><span class="sxs-lookup"><span data-stu-id="57ab5-245">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="57ab5-246">New-Service</span><span class="sxs-lookup"><span data-stu-id="57ab5-246">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="57ab5-247">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="57ab5-247">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="57ab5-248">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="57ab5-248">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="57ab5-249">Start-Service</span><span class="sxs-lookup"><span data-stu-id="57ab5-249">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="57ab5-250">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="57ab5-250">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="57ab5-251">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="57ab5-251">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="57ab5-252">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="57ab5-252">Remove-Service</span></span>](Remove-Service.md)
