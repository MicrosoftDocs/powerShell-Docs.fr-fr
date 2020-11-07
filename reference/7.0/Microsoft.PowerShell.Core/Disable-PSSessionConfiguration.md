---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: 9970c21748d49d258c1704f4a550d0a997a92af8
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346613"
---
# <span data-ttu-id="b2035-103">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2035-103">Disable-PSSessionConfiguration</span></span>

## <span data-ttu-id="b2035-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b2035-104">SYNOPSIS</span></span>
<span data-ttu-id="b2035-105">Désactive les configurations de session sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b2035-105">Disables session configurations on the local computer.</span></span>

## <span data-ttu-id="b2035-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b2035-106">SYNTAX</span></span>

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="b2035-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b2035-107">DESCRIPTION</span></span>

<span data-ttu-id="b2035-108">L' `Disable-PSSessionConfiguration` applet de commande désactive les configurations de session sur l’ordinateur local, ce qui empêche tous les utilisateurs d’utiliser les configurations de session pour créer des sessions gérées par l’utilisateur ( **sessions PSSession** ) sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b2035-108">The `Disable-PSSessionConfiguration` cmdlet disables session configurations on the local computer, which prevents all users from using the session configurations to create a user-managed sessions ( **PSSessions** ) on the local computer.</span></span> <span data-ttu-id="b2035-109">Il s'agit d'une applet de commande avancée conçue pour être utilisée par les administrateurs système pour gérer des configurations de sessions personnalisées pour leurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b2035-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="b2035-110">À compter de PowerShell 3,0, l’applet de commande `Disable-PSSessionConfiguration` définit le paramètre **Enabled** de la configuration de session ( `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` ) sur false.</span><span class="sxs-lookup"><span data-stu-id="b2035-110">Starting in PowerShell 3.0, the `Disable-PSSessionConfiguration` cmdlet sets the **Enabled** setting of the session configuration (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) to False.</span></span>

<span data-ttu-id="b2035-111">Dans PowerShell 2,0, l' `Disable-PSSessionConfiguration` applet de commande ajoute une entrée **Deny_All** au descripteur de sécurité d’une ou plusieurs configurations de session inscrites.</span><span class="sxs-lookup"><span data-stu-id="b2035-111">In PowerShell 2.0, the `Disable-PSSessionConfiguration` cmdlet adds a **Deny_All** entry to the security descriptor of one or more registered session configurations.</span></span>

<span data-ttu-id="b2035-112">Sans paramètres, `Disable-PSSessionConfiguration` désactive la configuration **Microsoft. PowerShell** , la configuration par défaut utilisée pour les sessions.</span><span class="sxs-lookup"><span data-stu-id="b2035-112">Without parameters, `Disable-PSSessionConfiguration` disables the **Microsoft.PowerShell** configuration, the default configuration used for sessions.</span></span> <span data-ttu-id="b2035-113">À moins que l'utilisateur ne spécifie une autre configuration, les utilisateurs locaux et distants ne peuvent pas créer de sessions qui se connectent à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b2035-113">Unless the user specifies a different configuration, both local and remote users are effectively prevented from creating any sessions that connect to the computer.</span></span>

<span data-ttu-id="b2035-114">Pour désactiver toutes les configurations de session sur l’ordinateur, utilisez `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="b2035-114">To disable all session configurations on the computer, use `Disable-PSRemoting`.</span></span>

## <span data-ttu-id="b2035-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b2035-115">EXAMPLES</span></span>

### <span data-ttu-id="b2035-116">Exemple 1 : désactiver la configuration par défaut</span><span class="sxs-lookup"><span data-stu-id="b2035-116">Example 1: Disable the default configuration</span></span>

<span data-ttu-id="b2035-117">Cet exemple désactive la configuration de session Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2035-117">This example disables the Microsoft.PowerShell session configuration.</span></span>

```powershell
Disable-PSSessionConfiguration
```

### <span data-ttu-id="b2035-118">Exemple 2 : désactiver toutes les configurations de sessions inscrites</span><span class="sxs-lookup"><span data-stu-id="b2035-118">Example 2: Disable all registered session configurations</span></span>

<span data-ttu-id="b2035-119">Cet exemple désactive toutes les configurations de session inscrites sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b2035-119">This example disables all registered session configurations on the computer.</span></span>

```powershell
Disable-PSSessionConfiguration -Name *
```

### <span data-ttu-id="b2035-120">Exemple 3 : désactiver les configurations de session par nom</span><span class="sxs-lookup"><span data-stu-id="b2035-120">Example 3: Disable session configurations by name</span></span>

<span data-ttu-id="b2035-121">Cet exemple désactive toutes les configurations de session dont les noms commencent par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b2035-121">This example disables all session configurations that have names that begin with Microsoft.</span></span> <span data-ttu-id="b2035-122">Le paramètre **force** supprime toutes les invites utilisateur de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b2035-122">The **Force** parameter suppresses all user prompts from the cmdlet.</span></span>

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### <span data-ttu-id="b2035-123">Exemple 4 : désactiver les configurations de session à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="b2035-123">Example 4: Disable session configurations by using the pipeline</span></span>

<span data-ttu-id="b2035-124">Cet exemple désactive les configurations de session **MaintenanceShell** et **AdminShell** .</span><span class="sxs-lookup"><span data-stu-id="b2035-124">This example disables the **MaintenanceShell** and **AdminShell** session configurations.</span></span> <span data-ttu-id="b2035-125">L’opérateur de pipeline (|) envoie les résultats d’un `Get-PSSessionConfiguration` à `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="b2035-125">The pipeline operator (|) sends the results of a `Get-PSSessionConfiguration` to `Disable-PSSessionConfiguration`.</span></span>

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### <span data-ttu-id="b2035-126">Exemple 5 : effets de la désactivation d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="b2035-126">Example 5: Effects of disabling a session configuration</span></span>

<span data-ttu-id="b2035-127">Cet exemple montre les autorisations avant et après l’exécution `Disable-PSSessionConfiguration` et l’effet de la désactivation d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="b2035-127">This example shows the permissions before and after running `Disable-PSSessionConfiguration` and the effect of disabling a session configuration.</span></span>

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> <span data-ttu-id="b2035-128">La désactivation de la configuration ne vous empêche pas de modifier la configuration à l’aide de l’applet de commande `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="b2035-128">Disabling the configuration does not prevent you from changing the configuration using the `Set-PSSessionConfiguration` cmdlet.</span></span> <span data-ttu-id="b2035-129">Elle empêche uniquement l’utilisation de la configuration.</span><span class="sxs-lookup"><span data-stu-id="b2035-129">It only prevents use of the configuration.</span></span>

## <span data-ttu-id="b2035-130">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="b2035-130">PARAMETERS</span></span>

### <span data-ttu-id="b2035-131">-Force</span><span class="sxs-lookup"><span data-stu-id="b2035-131">-Force</span></span>

<span data-ttu-id="b2035-132">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b2035-132">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="b2035-133">-Name</span><span class="sxs-lookup"><span data-stu-id="b2035-133">-Name</span></span>

<span data-ttu-id="b2035-134">Spécifie un tableau de noms de configurations de session à désactiver.</span><span class="sxs-lookup"><span data-stu-id="b2035-134">Specifies an array of names of session configurations to disable.</span></span> <span data-ttu-id="b2035-135">Entrez un ou plusieurs noms de configurations.</span><span class="sxs-lookup"><span data-stu-id="b2035-135">Enter one or more configuration names.</span></span> <span data-ttu-id="b2035-136">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="b2035-136">Wildcard characters are permitted.</span></span> <span data-ttu-id="b2035-137">Vous pouvez également diriger une chaîne qui contient un nom de configuration ou un objet de configuration de session vers `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="b2035-137">You can also pipe a string that contains a configuration name or a session configuration object to `Disable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="b2035-138">Si vous omettez ce paramètre, `Disable-PSSessionConfiguration` désactive la configuration de session Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2035-138">If you omit this parameter, `Disable-PSSessionConfiguration` disables the Microsoft.PowerShell session configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="b2035-139">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="b2035-139">-NoServiceRestart</span></span>

<span data-ttu-id="b2035-140">Utilisé pour empêcher le redémarrage du service WSMan.</span><span class="sxs-lookup"><span data-stu-id="b2035-140">Used to prevent the restart of the WSMan service.</span></span> <span data-ttu-id="b2035-141">Il n’est pas nécessaire de redémarrer le service pour désactiver la configuration.</span><span class="sxs-lookup"><span data-stu-id="b2035-141">It is not necessary to restart the service to disable the configuration.</span></span>

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

### <span data-ttu-id="b2035-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b2035-142">-Confirm</span></span>

<span data-ttu-id="b2035-143">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b2035-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b2035-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b2035-144">-WhatIf</span></span>

<span data-ttu-id="b2035-145">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b2035-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b2035-146">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="b2035-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b2035-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2035-147">CommonParameters</span></span>

<span data-ttu-id="b2035-148">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b2035-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b2035-149">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b2035-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b2035-150">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b2035-150">INPUTS</span></span>

### <span data-ttu-id="b2035-151">Microsoft. PowerShell. Commands. PSSessionConfigurationCommands # PSSessionConfiguration, System. String</span><span class="sxs-lookup"><span data-stu-id="b2035-151">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="b2035-152">Vous pouvez diriger un objet de configuration de session ou une chaîne qui contient le nom d’une configuration de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b2035-152">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="b2035-153">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b2035-153">OUTPUTS</span></span>

### <span data-ttu-id="b2035-154">Aucun</span><span class="sxs-lookup"><span data-stu-id="b2035-154">None</span></span>

<span data-ttu-id="b2035-155">Cette applet de commande ne retourne pas d'objets.</span><span class="sxs-lookup"><span data-stu-id="b2035-155">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="b2035-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b2035-156">NOTES</span></span>

<span data-ttu-id="b2035-157">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="b2035-157">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="b2035-158">Pour exécuter cette applet de commande, vous devez démarrer PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="b2035-158">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="b2035-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b2035-159">RELATED LINKS</span></span>

[<span data-ttu-id="b2035-160">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2035-160">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="b2035-161">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2035-161">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="b2035-162">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="b2035-162">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="b2035-163">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2035-163">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="b2035-164">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2035-164">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="b2035-165">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="b2035-165">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="b2035-166">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2035-166">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="b2035-167">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="b2035-167">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="b2035-168">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="b2035-168">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="b2035-169">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="b2035-169">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
