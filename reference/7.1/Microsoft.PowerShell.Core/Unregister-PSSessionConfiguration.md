---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: d56d71dccc54c07154a6f3302634b84779c00129
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205666"
---
# <span data-ttu-id="23016-103">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23016-103">Unregister-PSSessionConfiguration</span></span>

## <span data-ttu-id="23016-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="23016-104">SYNOPSIS</span></span>
<span data-ttu-id="23016-105">Supprime les configurations de sessions inscrites de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="23016-105">Deletes registered session configurations from the computer.</span></span>

## <span data-ttu-id="23016-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="23016-106">SYNTAX</span></span>

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="23016-107">Description</span><span class="sxs-lookup"><span data-stu-id="23016-107">DESCRIPTION</span></span>

<span data-ttu-id="23016-108">L' `Unregister-PSSessionConfiguration` applet de commande supprime les configurations de session inscrites de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="23016-108">The `Unregister-PSSessionConfiguration` cmdlet deletes registered session configurations from the computer.</span></span> <span data-ttu-id="23016-109">Cette applet de commande est conçue pour permettre aux administrateurs système de gérer les configurations de session personnalisées pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="23016-109">This cmdlet is designed for system administrators to manage customized session configurations for users.</span></span>

<span data-ttu-id="23016-110">Pour que la modification prenne effet, `Unregister-PSSessionConfiguration` redémarre le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="23016-110">To make the change effective, `Unregister-PSSessionConfiguration` restarts the **WinRM** service.</span></span> <span data-ttu-id="23016-111">Pour empêcher le redémarrage, spécifiez le paramètre **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="23016-111">To prevent the restart, specify the **NoServiceRestart** parameter.</span></span>

<span data-ttu-id="23016-112">Si vous supprimez accidentellement les configurations de session **Microsoft. PowerShell** ou **Microsoft. powershell32** par défaut, utilisez l' `Enable-PSRemoting` applet de commande pour les restaurer.</span><span class="sxs-lookup"><span data-stu-id="23016-112">If you accidentally delete the default **Microsoft.PowerShell** or **Microsoft.PowerShell32** session configurations, use the `Enable-PSRemoting` cmdlet to restore them.</span></span> <span data-ttu-id="23016-113">Pour plus d’informations, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="23016-113">For more information, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="23016-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="23016-114">EXAMPLES</span></span>

### <span data-ttu-id="23016-115">Exemple 1 : supprimer une configuration de session</span><span class="sxs-lookup"><span data-stu-id="23016-115">Example 1: Delete a session configuration</span></span>

<span data-ttu-id="23016-116">Cet exemple supprime la configuration de session **MaintenanceShell** de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="23016-116">This example deletes the **MaintenanceShell** session configuration from the computer.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### <span data-ttu-id="23016-117">Exemple 2 : supprimer une configuration de session et redémarrer le service WinRM</span><span class="sxs-lookup"><span data-stu-id="23016-117">Example 2: Delete a session configuration and restart the WinRM service</span></span>

<span data-ttu-id="23016-118">Dans cet exemple, nous supprimons la configuration **MaintenanceShell** et redémarrons le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="23016-118">In this example, we delete the **MaintenanceShell** configuration and restart the WinRM service.</span></span> <span data-ttu-id="23016-119">Le paramètre **force** supprime tous les messages utilisateur pour redémarrer le service **WinRM** sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="23016-119">The **Force** parameter suppresses all user messages to restart the **WinRM** service without prompting.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### <span data-ttu-id="23016-120">Exemple 3 : supprimer toutes les configurations de session</span><span class="sxs-lookup"><span data-stu-id="23016-120">Example 3: Delete all session configurations</span></span>

<span data-ttu-id="23016-121">Cet exemple montre deux façons de supprimer toutes les configurations de session sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="23016-121">This examples show two ways to delete all the session configurations on the computer.</span></span> <span data-ttu-id="23016-122">Les deux commandes ont le même effet et peuvent être utilisées indifféremment.</span><span class="sxs-lookup"><span data-stu-id="23016-122">Both commands have the same effect and can be used interchangeably.</span></span>

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### <span data-ttu-id="23016-123">Exemple 4 : annuler l’inscription sans redémarrage</span><span class="sxs-lookup"><span data-stu-id="23016-123">Example 4: Unregister without a restart</span></span>

<span data-ttu-id="23016-124">Cet exemple montre l’effet de l’utilisation du paramètre **NoServiceRestart** pour empêcher le redémarrage d’un service qui perturberait les sessions sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="23016-124">This example shows the effect of using the **NoServiceRestart** parameter to prevent a service restart that would disrupt any sessions on the computer.</span></span>

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

<span data-ttu-id="23016-125">`Unregister-PSSessionConfiguration`Supprime la configuration de session **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="23016-125">The `Unregister-PSSessionConfiguration` deletes the **MaintenanceShell** session configuration.</span></span>
<span data-ttu-id="23016-126">Toutefois, étant donné que la commande utilise le paramètre **NoServiceRestart** , le service **WinRM** n’est pas redémarré et la modification n’est pas encore totalement effective.</span><span class="sxs-lookup"><span data-stu-id="23016-126">However, because the command uses the **NoServiceRestart** parameter, the **WinRM** service is not restarted and the change is not yet completely effective.</span></span>

<span data-ttu-id="23016-127">Ensuite, `Get-PSSessionConfiguration` tente d’accéder à la session **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="23016-127">Next, the `Get-PSSessionConfiguration` tries to get the **MaintenanceShell** session.</span></span> <span data-ttu-id="23016-128">Étant donné que la session a été supprimée de la table de ressources WS-Management, `Get-PSSessionConfiguration` ne peut pas la retourner.</span><span class="sxs-lookup"><span data-stu-id="23016-128">Because the session has been removed from the WS-Management resource table, `Get-PSSessionConfiguration` cannot return it.</span></span>

<span data-ttu-id="23016-129">L' `New-PSSession` applet de commande crée une session à l’aide de la configuration **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="23016-129">The `New-PSSession` cmdlet creates a session using the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="23016-130">La commande a réussi.</span><span class="sxs-lookup"><span data-stu-id="23016-130">The command succeeds.</span></span> <span data-ttu-id="23016-131">Ensuite, redémarrez le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="23016-131">Next, we restart the **WinRM** service.</span></span>

<span data-ttu-id="23016-132">Enfin, l' `New-PSSession` applet de commande tente de créer une session qui utilise la configuration **MaintenanceShell** .</span><span class="sxs-lookup"><span data-stu-id="23016-132">Finally, the `New-PSSession` cmdlet tries to create a session that uses the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="23016-133">Cette fois-ci, la session échoue car la configuration **MaintenanceShell** a été supprimée lors du redémarrage du service WinRM.</span><span class="sxs-lookup"><span data-stu-id="23016-133">This time, the session fails because the **MaintenanceShell** configuration was deleted when the WinRM service restarted.</span></span>

## <span data-ttu-id="23016-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="23016-134">PARAMETERS</span></span>

### <span data-ttu-id="23016-135">-Force</span><span class="sxs-lookup"><span data-stu-id="23016-135">-Force</span></span>

<span data-ttu-id="23016-136">Indique que l’applet de commande ne vous invite pas à confirmer et à redémarrer le service **WinRM** sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="23016-136">Indicates that the cmdlet does not prompt you for confirmation, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="23016-137">Le redémarrage du service permet d'appliquer la modification de configuration.</span><span class="sxs-lookup"><span data-stu-id="23016-137">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="23016-138">Pour éviter un redémarrage et supprimer l'invite de redémarrage, utilisez le paramètre **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="23016-138">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="23016-139">-Name</span><span class="sxs-lookup"><span data-stu-id="23016-139">-Name</span></span>

<span data-ttu-id="23016-140">Spécifie les noms des configurations de sessions à supprimer.</span><span class="sxs-lookup"><span data-stu-id="23016-140">Specifies the names of the session configurations to delete.</span></span> <span data-ttu-id="23016-141">Entrez un nom de configuration de session ou un modèle de nom de configuration.</span><span class="sxs-lookup"><span data-stu-id="23016-141">Enter one session configuration name or a configuration name pattern.</span></span> <span data-ttu-id="23016-142">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="23016-142">Wildcard characters are permitted.</span></span> <span data-ttu-id="23016-143">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="23016-143">This parameter is required.</span></span>

<span data-ttu-id="23016-144">Vous pouvez également diriger une configuration de session vers `Unregister-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="23016-144">You can also pipe a session configurations to `Unregister-PSSessionConfiguration`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="23016-145">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="23016-145">-NoServiceRestart</span></span>

<span data-ttu-id="23016-146">Indique que cette applet de commande ne redémarre pas le service **WinRM** et supprime l’invite de redémarrage du service.</span><span class="sxs-lookup"><span data-stu-id="23016-146">Indicates that this cmdlet does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="23016-147">Par défaut, lorsque vous exécutez une `Unregister-PSSessionConfiguration` commande, vous êtes invité à redémarrer le service **WinRM** pour que la modification prenne effet.</span><span class="sxs-lookup"><span data-stu-id="23016-147">By default, when you run an `Unregister-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the change effective.</span></span> <span data-ttu-id="23016-148">Tant que le service **WinRM** n’est pas redémarré, les utilisateurs peuvent toujours utiliser la configuration de session non inscrite, même si `Get-PSSessionConfiguration` ne la trouve pas.</span><span class="sxs-lookup"><span data-stu-id="23016-148">Until the **WinRM** service is restarted, users can still use the unregistered session configuration, even though `Get-PSSessionConfiguration` does not find it.</span></span>

<span data-ttu-id="23016-149">Pour redémarrer le service **WinRM** sans demander confirmation, spécifiez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="23016-149">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="23016-150">Pour redémarrer manuellement le service **WinRM** , utilisez l' `Restart-Service` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="23016-150">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="23016-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="23016-151">-Confirm</span></span>

<span data-ttu-id="23016-152">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="23016-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="23016-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="23016-153">-WhatIf</span></span>

<span data-ttu-id="23016-154">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="23016-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="23016-155">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="23016-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="23016-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23016-156">CommonParameters</span></span>

<span data-ttu-id="23016-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23016-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23016-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="23016-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="23016-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="23016-159">INPUTS</span></span>

### <span data-ttu-id="23016-160">Microsoft. PowerShell. Commands. PSSessionConfigurationCommands # PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23016-160">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

<span data-ttu-id="23016-161">Vous pouvez diriger un objet de configuration de session de `Get-PSSessionConfiguration` vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="23016-161">You can pipe a session configuration object from `Get-PSSessionConfiguration` to this cmdlet.</span></span>

## <span data-ttu-id="23016-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="23016-162">OUTPUTS</span></span>

### <span data-ttu-id="23016-163">Aucun</span><span class="sxs-lookup"><span data-stu-id="23016-163">None</span></span>

<span data-ttu-id="23016-164">Cette applet de commande ne retourne pas d'objets.</span><span class="sxs-lookup"><span data-stu-id="23016-164">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="23016-165">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="23016-165">NOTES</span></span>

<span data-ttu-id="23016-166">Pour exécuter cette applet de commande, vous devez démarrer PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="23016-166">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="23016-167">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="23016-167">RELATED LINKS</span></span>

[<span data-ttu-id="23016-168">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23016-168">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="23016-169">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23016-169">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="23016-170">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23016-170">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="23016-171">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="23016-171">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="23016-172">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="23016-172">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="23016-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23016-173">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="23016-174">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23016-174">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="23016-175">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="23016-175">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="23016-176">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="23016-176">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="23016-177">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="23016-177">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="23016-178">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="23016-178">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="23016-179">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="23016-179">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)

