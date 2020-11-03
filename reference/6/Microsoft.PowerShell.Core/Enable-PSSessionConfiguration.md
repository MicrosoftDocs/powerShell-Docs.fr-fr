---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 07c36741991a23f13238e34e93074dfc19ca9580
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204910"
---
# <span data-ttu-id="06d1c-103">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d1c-103">Enable-PSSessionConfiguration</span></span>

## <span data-ttu-id="06d1c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="06d1c-104">SYNOPSIS</span></span>
<span data-ttu-id="06d1c-105">Active les configurations de session sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="06d1c-105">Enables the session configurations on the local computer.</span></span>

## <span data-ttu-id="06d1c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="06d1c-106">SYNTAX</span></span>

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="06d1c-107">Description</span><span class="sxs-lookup"><span data-stu-id="06d1c-107">DESCRIPTION</span></span>

<span data-ttu-id="06d1c-108">L' `Enable-PSSessionConfiguration` applet de commande active les configurations de session inscrites qui ont été désactivées, par exemple à l’aide des `Disable-PSSessionConfiguration` `Disable-PSRemoting` applets de commande ou, ou le paramètre **AccessMode** de `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="06d1c-108">The `Enable-PSSessionConfiguration` cmdlet enables registered session configurations that have been disabled, such as by using the `Disable-PSSessionConfiguration` or `Disable-PSRemoting` cmdlets, or the **AccessMode** parameter of `Register-PSSessionConfiguration`.</span></span> <span data-ttu-id="06d1c-109">Il s'agit d'une applet de commande avancée conçue pour être utilisée par les administrateurs système pour gérer des configurations de sessions personnalisées pour leurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="06d1c-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="06d1c-110">Sans paramètres, `Enable-PSSessionConfiguration` active la configuration **Microsoft. PowerShell** , qui est la configuration par défaut utilisée pour les sessions.</span><span class="sxs-lookup"><span data-stu-id="06d1c-110">Without parameters, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** configuration, which is the default configuration that is used for sessions.</span></span>

<span data-ttu-id="06d1c-111">`Enable-PSSessionConfiguration` supprime le paramètre **Deny_All** du descripteur de sécurité des configurations de session affectées, active l’écouteur qui accepte les demandes sur n’importe quelle adresse IP, puis redémarre le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="06d1c-111">`Enable-PSSessionConfiguration` removes the **Deny_All** setting from the security descriptor of the affected session configurations, turns on the listener that accepts requests on any IP address, and restarts the WinRM service.</span></span> <span data-ttu-id="06d1c-112">À compter de PowerShell 3,0, `Enable-PSSessionConfiguration` définit également la valeur de la propriété **Enabled** de la configuration de session ( `WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled` ) sur true.</span><span class="sxs-lookup"><span data-stu-id="06d1c-112">Beginning in PowerShell 3.0, `Enable-PSSessionConfiguration` also sets the value of the **Enabled** property of the session configuration (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) to True.</span></span> <span data-ttu-id="06d1c-113">Toutefois, `Enable-PSSessionConfiguration` ne supprime pas ou ne modifie **Network_Deny_All** pas le `AccessMode=Local` paramètre de descripteur de sécurité Network_Deny_All () qui autorise uniquement les utilisateurs de l’ordinateur local à utiliser la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d1c-113">However, `Enable-PSSessionConfiguration` does not remove or change the **Network_Deny_All** (`AccessMode=Local`) security descriptor setting that allows only users of the local computer to use to the session configuration.</span></span>

## <span data-ttu-id="06d1c-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="06d1c-114">EXAMPLES</span></span>

### <span data-ttu-id="06d1c-115">Exemple 1 : réactiver la session par défaut</span><span class="sxs-lookup"><span data-stu-id="06d1c-115">Example 1: Re-enable the default session</span></span>

<span data-ttu-id="06d1c-116">Cet exemple réactive la configuration de session **Microsoft. PowerShell** par défaut sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="06d1c-116">This example re-enables the **Microsoft.PowerShell** default session configuration on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration
```

### <span data-ttu-id="06d1c-117">Exemple 2 : réactiver les sessions spécifiées</span><span class="sxs-lookup"><span data-stu-id="06d1c-117">Example 2: Re-enable specified sessions</span></span>

<span data-ttu-id="06d1c-118">Cet exemple réactive les configurations de session **MaintenanceShell** et **AdminShell** sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="06d1c-118">This example re-enables the **MaintenanceShell** and **AdminShell** session configurations on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### <span data-ttu-id="06d1c-119">Exemple 3 : réactiver toutes les sessions</span><span class="sxs-lookup"><span data-stu-id="06d1c-119">Example 3: Re-enable the all sessions</span></span>

<span data-ttu-id="06d1c-120">Cet exemple réactive toutes les configurations de session sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="06d1c-120">This example re-enables all session configurations on the computer.</span></span> <span data-ttu-id="06d1c-121">Ces commandes sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="06d1c-121">These commands are equivalent.</span></span>
<span data-ttu-id="06d1c-122">Par conséquent, vous pouvez utiliser l’une ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="06d1c-122">Therefore, you can use either.</span></span>

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

<span data-ttu-id="06d1c-123">`Enable-PSSessionConfiguration` ne génère pas d’erreur si vous activez une configuration de session déjà activée.</span><span class="sxs-lookup"><span data-stu-id="06d1c-123">`Enable-PSSessionConfiguration` does not generate an error if you enable a session configuration that is already enabled.</span></span>

### <span data-ttu-id="06d1c-124">Exemple 4 : réactiver une session et spécifier un nouveau descripteur de sécurité</span><span class="sxs-lookup"><span data-stu-id="06d1c-124">Example 4: Re-enable a session and specify a new security descriptor</span></span>

<span data-ttu-id="06d1c-125">Cet exemple réactive la configuration de session **MaintenanceShell** et spécifie un nouveau descripteur de sécurité pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="06d1c-125">This example re-enables the **MaintenanceShell** session configuration and specifies a new security descriptor for the configuration.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## <span data-ttu-id="06d1c-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="06d1c-126">PARAMETERS</span></span>

### <span data-ttu-id="06d1c-127">-Force</span><span class="sxs-lookup"><span data-stu-id="06d1c-127">-Force</span></span>

<span data-ttu-id="06d1c-128">Indique que l’applet de commande ne vous invite pas à confirmer et à redémarrer le service WinRM sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="06d1c-128">Indicates that the cmdlet does not prompt you for confirmation, and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="06d1c-129">Le redémarrage du service permet d'appliquer la modification de configuration.</span><span class="sxs-lookup"><span data-stu-id="06d1c-129">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="06d1c-130">Pour éviter un redémarrage et supprimer l'invite de redémarrage, utilisez le paramètre **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="06d1c-130">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="06d1c-131">-Name</span><span class="sxs-lookup"><span data-stu-id="06d1c-131">-Name</span></span>

<span data-ttu-id="06d1c-132">Spécifie les noms des configurations de session à activer.</span><span class="sxs-lookup"><span data-stu-id="06d1c-132">Specifies the names of session configurations to enable.</span></span> <span data-ttu-id="06d1c-133">Entrez un ou plusieurs noms de configurations.</span><span class="sxs-lookup"><span data-stu-id="06d1c-133">Enter one or more configuration names.</span></span>
<span data-ttu-id="06d1c-134">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="06d1c-134">Wildcard characters are permitted.</span></span>

<span data-ttu-id="06d1c-135">Vous pouvez également diriger une chaîne qui contient un nom de configuration ou un objet de configuration de session vers `Enable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="06d1c-135">You can also pipe a string that contains a configuration name or a session configuration object to `Enable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="06d1c-136">Si vous omettez ce paramètre, `Enable-PSSessionConfiguration` active la configuration de session **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="06d1c-136">If you omit this parameter, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** session configuration.</span></span>

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

### <span data-ttu-id="06d1c-137">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="06d1c-137">-NoServiceRestart</span></span>

<span data-ttu-id="06d1c-138">Indique que l’applet de commande ne redémarre pas le service.</span><span class="sxs-lookup"><span data-stu-id="06d1c-138">Indicates that the cmdlet does not restart the service.</span></span>

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

### <span data-ttu-id="06d1c-139">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="06d1c-139">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="06d1c-140">Spécifie un descripteur de sécurité avec lequel cette applet de commande remplace le descripteur de sécurité dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="06d1c-140">Specifies a security descriptor with which this cmdlet replaces the security descriptor on the session configuration.</span></span>

<span data-ttu-id="06d1c-141">Si vous omettez ce paramètre, `Enable-PSSessionConfiguration` supprime uniquement l’élément refuser tout du descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="06d1c-141">If you omit this parameter, `Enable-PSSessionConfiguration` only deletes the deny all item from the security descriptor.</span></span>

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

### <span data-ttu-id="06d1c-142">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="06d1c-142">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="06d1c-143">Indique que cette applet de commande active la configuration de session lorsque l’ordinateur se trouve sur un réseau public.</span><span class="sxs-lookup"><span data-stu-id="06d1c-143">Indicates that this cmdlet enables the session configuration when the computer is on a public network.</span></span> <span data-ttu-id="06d1c-144">Ce paramètre active une règle de pare-feu pour les réseaux publics. Celle-ci n'autorise l'accès à distance qu'à partir d'ordinateurs du même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="06d1c-144">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="06d1c-145">Par défaut, `Enable-PSSessionConfiguration` échoue sur un réseau public.</span><span class="sxs-lookup"><span data-stu-id="06d1c-145">By default, `Enable-PSSessionConfiguration` fails on a public network.</span></span>

<span data-ttu-id="06d1c-146">Ce paramètre est conçu pour les versions clientes du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="06d1c-146">This parameter is designed for client versions of the Windows operating system.</span></span> <span data-ttu-id="06d1c-147">Les versions serveur du système d’exploitation Windows ont une règle de pare-feu de sous-réseau local pour les réseaux publics.</span><span class="sxs-lookup"><span data-stu-id="06d1c-147">Server versions of the Windows operating system have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="06d1c-148">Toutefois, si la règle de pare-feu de sous-réseau local est désactivée sur une version serveur du système d’exploitation Windows, ce paramètre la réactive.</span><span class="sxs-lookup"><span data-stu-id="06d1c-148">However, if the local subnet firewall rule is disabled on a server version of the Windows operating system, this parameter re-enables it.</span></span>

<span data-ttu-id="06d1c-149">Pour supprimer la restriction de sous-réseau local et activer l’accès à distance à partir de tous les emplacements sur les réseaux publics, utilisez l' `Set-NetFirewallRule` applet de commande dans le module netsecurity.</span><span class="sxs-lookup"><span data-stu-id="06d1c-149">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="06d1c-150">Pour plus d'informations, consultez `Enable-PSRemoting`.</span><span class="sxs-lookup"><span data-stu-id="06d1c-150">For more information, see `Enable-PSRemoting`.</span></span>

<span data-ttu-id="06d1c-151">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="06d1c-151">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="06d1c-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="06d1c-152">-Confirm</span></span>

<span data-ttu-id="06d1c-153">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="06d1c-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="06d1c-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="06d1c-154">-WhatIf</span></span>

<span data-ttu-id="06d1c-155">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="06d1c-155">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="06d1c-156">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="06d1c-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="06d1c-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="06d1c-157">CommonParameters</span></span>

<span data-ttu-id="06d1c-158">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="06d1c-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="06d1c-159">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="06d1c-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="06d1c-160">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="06d1c-160">INPUTS</span></span>

### <span data-ttu-id="06d1c-161">Microsoft. PowerShell. Commands. PSSessionConfigurationCommands # PSSessionConfiguration, System. String</span><span class="sxs-lookup"><span data-stu-id="06d1c-161">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="06d1c-162">Vous pouvez diriger un objet de configuration de session ou une chaîne qui contient le nom d’une configuration de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="06d1c-162">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="06d1c-163">SORTIES</span><span class="sxs-lookup"><span data-stu-id="06d1c-163">OUTPUTS</span></span>

### <span data-ttu-id="06d1c-164">Aucun</span><span class="sxs-lookup"><span data-stu-id="06d1c-164">None</span></span>

<span data-ttu-id="06d1c-165">Cette applet de commande ne retourne pas d'objets.</span><span class="sxs-lookup"><span data-stu-id="06d1c-165">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="06d1c-166">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="06d1c-166">NOTES</span></span>

<span data-ttu-id="06d1c-167">Pour utiliser cette applet de commande, vous devez démarrer PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="06d1c-167">To use this cmdlet, you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="06d1c-168">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="06d1c-168">RELATED LINKS</span></span>

[<span data-ttu-id="06d1c-169">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d1c-169">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="06d1c-170">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d1c-170">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="06d1c-171">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="06d1c-171">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="06d1c-172">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="06d1c-172">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="06d1c-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d1c-173">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="06d1c-174">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d1c-174">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="06d1c-175">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="06d1c-175">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="06d1c-176">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="06d1c-176">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="06d1c-177">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="06d1c-177">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="06d1c-178">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="06d1c-178">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="06d1c-179">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="06d1c-179">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
