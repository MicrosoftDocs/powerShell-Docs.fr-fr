---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 86650f33f376ccb7d1428836c9d0070e749cf0ee
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597158"
---
# <span data-ttu-id="31c72-102">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="31c72-102">Enable-PSSessionConfiguration</span></span>

## <span data-ttu-id="31c72-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="31c72-103">SYNOPSIS</span></span>
<span data-ttu-id="31c72-104">Active les configurations de session sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="31c72-104">Enables the session configurations on the local computer.</span></span>

## <span data-ttu-id="31c72-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="31c72-105">SYNTAX</span></span>

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="31c72-106">Description</span><span class="sxs-lookup"><span data-stu-id="31c72-106">DESCRIPTION</span></span>

<span data-ttu-id="31c72-107">L' `Enable-PSSessionConfiguration` applet de commande active les configurations de session inscrites qui ont été désactivées, par exemple à l’aide des `Disable-PSSessionConfiguration` `Disable-PSRemoting` applets de commande ou, ou le paramètre **AccessMode** de `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="31c72-107">The `Enable-PSSessionConfiguration` cmdlet enables registered session configurations that have been disabled, such as by using the `Disable-PSSessionConfiguration` or `Disable-PSRemoting` cmdlets, or the **AccessMode** parameter of `Register-PSSessionConfiguration`.</span></span> <span data-ttu-id="31c72-108">Il s'agit d'une applet de commande avancée conçue pour être utilisée par les administrateurs système pour gérer des configurations de sessions personnalisées pour leurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="31c72-108">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="31c72-109">Sans paramètres, `Enable-PSSessionConfiguration` active la configuration **Microsoft. PowerShell** , qui est la configuration par défaut utilisée pour les sessions.</span><span class="sxs-lookup"><span data-stu-id="31c72-109">Without parameters, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** configuration, which is the default configuration that is used for sessions.</span></span>

<span data-ttu-id="31c72-110">`Enable-PSSessionConfiguration` supprime le paramètre **Deny_All** du descripteur de sécurité des configurations de session affectées, active l’écouteur qui accepte les demandes sur n’importe quelle adresse IP, puis redémarre le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="31c72-110">`Enable-PSSessionConfiguration` removes the **Deny_All** setting from the security descriptor of the affected session configurations, turns on the listener that accepts requests on any IP address, and restarts the WinRM service.</span></span> <span data-ttu-id="31c72-111">À compter de PowerShell 3,0, `Enable-PSSessionConfiguration` définit également la valeur de la propriété **Enabled** de la configuration de session ( `WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled` ) sur true.</span><span class="sxs-lookup"><span data-stu-id="31c72-111">Beginning in PowerShell 3.0, `Enable-PSSessionConfiguration` also sets the value of the **Enabled** property of the session configuration (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) to True.</span></span> <span data-ttu-id="31c72-112">Toutefois, `Enable-PSSessionConfiguration` ne supprime pas ou ne modifie  pas le `AccessMode=Local` paramètre de descripteur de sécurité Network_Deny_All () qui autorise uniquement les utilisateurs de l’ordinateur local à utiliser la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="31c72-112">However, `Enable-PSSessionConfiguration` does not remove or change the **Network_Deny_All** (`AccessMode=Local`) security descriptor setting that allows only users of the local computer to use to the session configuration.</span></span>

## <span data-ttu-id="31c72-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="31c72-113">EXAMPLES</span></span>

### <span data-ttu-id="31c72-114">Exemple 1 : réactiver la session par défaut</span><span class="sxs-lookup"><span data-stu-id="31c72-114">Example 1: Re-enable the default session</span></span>

<span data-ttu-id="31c72-115">Cet exemple réactive la configuration de session **Microsoft. PowerShell** par défaut sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="31c72-115">This example re-enables the **Microsoft.PowerShell** default session configuration on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration
```

### <span data-ttu-id="31c72-116">Exemple 2 : réactiver les sessions spécifiées</span><span class="sxs-lookup"><span data-stu-id="31c72-116">Example 2: Re-enable specified sessions</span></span>

<span data-ttu-id="31c72-117">Cet exemple réactive les configurations de session **MaintenanceShell** et **AdminShell** sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="31c72-117">This example re-enables the **MaintenanceShell** and **AdminShell** session configurations on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### <span data-ttu-id="31c72-118">Exemple 3 : réactiver toutes les sessions</span><span class="sxs-lookup"><span data-stu-id="31c72-118">Example 3: Re-enable the all sessions</span></span>

<span data-ttu-id="31c72-119">Cet exemple réactive toutes les configurations de session sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="31c72-119">This example re-enables all session configurations on the computer.</span></span> <span data-ttu-id="31c72-120">Ces commandes sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="31c72-120">These commands are equivalent.</span></span>
<span data-ttu-id="31c72-121">Par conséquent, vous pouvez utiliser l’une ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="31c72-121">Therefore, you can use either.</span></span>

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

<span data-ttu-id="31c72-122">`Enable-PSSessionConfiguration` ne génère pas d’erreur si vous activez une configuration de session déjà activée.</span><span class="sxs-lookup"><span data-stu-id="31c72-122">`Enable-PSSessionConfiguration` does not generate an error if you enable a session configuration that is already enabled.</span></span>

### <span data-ttu-id="31c72-123">Exemple 4 : réactiver une session et spécifier un nouveau descripteur de sécurité</span><span class="sxs-lookup"><span data-stu-id="31c72-123">Example 4: Re-enable a session and specify a new security descriptor</span></span>

<span data-ttu-id="31c72-124">Cet exemple réactive la configuration de session **MaintenanceShell** et spécifie un nouveau descripteur de sécurité pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="31c72-124">This example re-enables the **MaintenanceShell** session configuration and specifies a new security descriptor for the configuration.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## <span data-ttu-id="31c72-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="31c72-125">PARAMETERS</span></span>

### <span data-ttu-id="31c72-126">-Force</span><span class="sxs-lookup"><span data-stu-id="31c72-126">-Force</span></span>

<span data-ttu-id="31c72-127">Indique que l’applet de commande ne vous invite pas à confirmer et à redémarrer le service WinRM sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="31c72-127">Indicates that the cmdlet does not prompt you for confirmation, and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="31c72-128">Le redémarrage du service permet d'appliquer la modification de configuration.</span><span class="sxs-lookup"><span data-stu-id="31c72-128">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="31c72-129">Pour éviter un redémarrage et supprimer l'invite de redémarrage, utilisez le paramètre **NoServiceRestart**.</span><span class="sxs-lookup"><span data-stu-id="31c72-129">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="31c72-130">-Name</span><span class="sxs-lookup"><span data-stu-id="31c72-130">-Name</span></span>

<span data-ttu-id="31c72-131">Spécifie les noms des configurations de session à activer.</span><span class="sxs-lookup"><span data-stu-id="31c72-131">Specifies the names of session configurations to enable.</span></span> <span data-ttu-id="31c72-132">Entrez un ou plusieurs noms de configurations.</span><span class="sxs-lookup"><span data-stu-id="31c72-132">Enter one or more configuration names.</span></span>
<span data-ttu-id="31c72-133">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="31c72-133">Wildcard characters are permitted.</span></span>

<span data-ttu-id="31c72-134">Vous pouvez également diriger une chaîne qui contient un nom de configuration ou un objet de configuration de session vers `Enable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="31c72-134">You can also pipe a string that contains a configuration name or a session configuration object to `Enable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="31c72-135">Si vous omettez ce paramètre, `Enable-PSSessionConfiguration` active la configuration de session **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="31c72-135">If you omit this parameter, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** session configuration.</span></span>

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

### <span data-ttu-id="31c72-136">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="31c72-136">-NoServiceRestart</span></span>

<span data-ttu-id="31c72-137">Indique que l’applet de commande ne redémarre pas le service.</span><span class="sxs-lookup"><span data-stu-id="31c72-137">Indicates that the cmdlet does not restart the service.</span></span>

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

### <span data-ttu-id="31c72-138">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="31c72-138">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="31c72-139">Spécifie un descripteur de sécurité avec lequel cette applet de commande remplace le descripteur de sécurité dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="31c72-139">Specifies a security descriptor with which this cmdlet replaces the security descriptor on the session configuration.</span></span>

<span data-ttu-id="31c72-140">Si vous omettez ce paramètre, `Enable-PSSessionConfiguration` supprime uniquement l’élément refuser tout du descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="31c72-140">If you omit this parameter, `Enable-PSSessionConfiguration` only deletes the deny all item from the security descriptor.</span></span>

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

### <span data-ttu-id="31c72-141">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="31c72-141">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="31c72-142">Indique que cette applet de commande active la configuration de session lorsque l’ordinateur se trouve sur un réseau public.</span><span class="sxs-lookup"><span data-stu-id="31c72-142">Indicates that this cmdlet enables the session configuration when the computer is on a public network.</span></span> <span data-ttu-id="31c72-143">Ce paramètre active une règle de pare-feu pour les réseaux publics. Celle-ci n'autorise l'accès à distance qu'à partir d'ordinateurs du même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="31c72-143">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="31c72-144">Par défaut, `Enable-PSSessionConfiguration` échoue sur un réseau public.</span><span class="sxs-lookup"><span data-stu-id="31c72-144">By default, `Enable-PSSessionConfiguration` fails on a public network.</span></span>

<span data-ttu-id="31c72-145">Ce paramètre est conçu pour les versions clientes du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="31c72-145">This parameter is designed for client versions of the Windows operating system.</span></span> <span data-ttu-id="31c72-146">Les versions serveur du système d’exploitation Windows ont une règle de pare-feu de sous-réseau local pour les réseaux publics.</span><span class="sxs-lookup"><span data-stu-id="31c72-146">Server versions of the Windows operating system have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="31c72-147">Toutefois, si la règle de pare-feu de sous-réseau local est désactivée sur une version serveur du système d’exploitation Windows, ce paramètre la réactive.</span><span class="sxs-lookup"><span data-stu-id="31c72-147">However, if the local subnet firewall rule is disabled on a server version of the Windows operating system, this parameter re-enables it.</span></span>

<span data-ttu-id="31c72-148">Pour supprimer la restriction de sous-réseau local et activer l’accès à distance à partir de tous les emplacements sur les réseaux publics, utilisez l' `Set-NetFirewallRule` applet de commande dans le module netsecurity.</span><span class="sxs-lookup"><span data-stu-id="31c72-148">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="31c72-149">Pour plus d’informations, consultez `Enable-PSRemoting`.</span><span class="sxs-lookup"><span data-stu-id="31c72-149">For more information, see `Enable-PSRemoting`.</span></span>

<span data-ttu-id="31c72-150">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31c72-150">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="31c72-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="31c72-151">-Confirm</span></span>

<span data-ttu-id="31c72-152">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31c72-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="31c72-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="31c72-153">-WhatIf</span></span>

<span data-ttu-id="31c72-154">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31c72-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="31c72-155">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="31c72-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="31c72-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="31c72-156">CommonParameters</span></span>

<span data-ttu-id="31c72-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="31c72-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="31c72-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="31c72-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="31c72-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="31c72-159">INPUTS</span></span>

### <span data-ttu-id="31c72-160">Microsoft. PowerShell. Commands. PSSessionConfigurationCommands # PSSessionConfiguration, System. String</span><span class="sxs-lookup"><span data-stu-id="31c72-160">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="31c72-161">Vous pouvez diriger un objet de configuration de session ou une chaîne qui contient le nom d’une configuration de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31c72-161">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="31c72-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="31c72-162">OUTPUTS</span></span>

### <span data-ttu-id="31c72-163">None</span><span class="sxs-lookup"><span data-stu-id="31c72-163">None</span></span>

<span data-ttu-id="31c72-164">Cette applet de commande ne retourne pas d'objets.</span><span class="sxs-lookup"><span data-stu-id="31c72-164">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="31c72-165">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="31c72-165">NOTES</span></span>

<span data-ttu-id="31c72-166">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="31c72-166">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="31c72-167">Pour utiliser cette applet de commande, vous devez démarrer PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="31c72-167">To use this cmdlet, you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="31c72-168">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="31c72-168">RELATED LINKS</span></span>

[<span data-ttu-id="31c72-169">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="31c72-169">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="31c72-170">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="31c72-170">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="31c72-171">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="31c72-171">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="31c72-172">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="31c72-172">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="31c72-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="31c72-173">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="31c72-174">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="31c72-174">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="31c72-175">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="31c72-175">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="31c72-176">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="31c72-176">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="31c72-177">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="31c72-177">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="31c72-178">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="31c72-178">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="31c72-179">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="31c72-179">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
