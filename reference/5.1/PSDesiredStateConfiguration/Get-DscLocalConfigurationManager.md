---
external help file: Get-DSCLocalConfigurationManager.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscLocalConfigurationManager
ms.openlocfilehash: 162770d8eb3a8953dcfaeb31f30742a46353b33b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203945"
---
# <span data-ttu-id="d6027-103">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d6027-103">Get-DscLocalConfigurationManager</span></span>

## <span data-ttu-id="d6027-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d6027-104">SYNOPSIS</span></span>

<span data-ttu-id="d6027-105">Obtient les paramètres et les États du Configuration Manager local (LCM) pour le nœud.</span><span class="sxs-lookup"><span data-stu-id="d6027-105">Gets Local Configuration Manager (LCM) settings and states for the node.</span></span>

## <span data-ttu-id="d6027-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d6027-106">SYNTAX</span></span>

```
Get-DscLocalConfigurationManager [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## <span data-ttu-id="d6027-107">Description</span><span class="sxs-lookup"><span data-stu-id="d6027-107">DESCRIPTION</span></span>

<span data-ttu-id="d6027-108">L' `Get-DscLocalConfigurationManager` applet de commande obtient les paramètres du gestionnaire de configuration local, la méta-configuration et les États du gestionnaire de configuration local pour le nœud.</span><span class="sxs-lookup"><span data-stu-id="d6027-108">The `Get-DscLocalConfigurationManager` cmdlet gets LCM settings, or meta-configuration, and the states of LCM for the node.</span></span> <span data-ttu-id="d6027-109">Spécifiez les ordinateurs à l'aide de sessions CIM (Common Information Model).</span><span class="sxs-lookup"><span data-stu-id="d6027-109">Specify computers by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="d6027-110">Si vous ne spécifiez pas d'ordinateur cible, l'applet de commande obtient les paramètres de configuration de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d6027-110">If you do not specify a target computer, the cmdlet gets the configuration settings from the local computer.</span></span>

## <span data-ttu-id="d6027-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d6027-111">EXAMPLES</span></span>

### <span data-ttu-id="d6027-112">Exemple 1 : obtenir les paramètres du LCM pour l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="d6027-112">Example 1: Get LCM settings for the local computer</span></span>

```powershell
Get-DscLocalConfigurationManager
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 47edd8c9-2798-4827-839a-b35cc87e69fb
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName
```

<span data-ttu-id="d6027-113">Cette commande obtient les paramètres LCM pour l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d6027-113">This command gets LCM settings for the local computer.</span></span>

<span data-ttu-id="d6027-114">Pour plus d’informations sur les attributs individuels de la sortie, consultez la documentation relative à la [configuration de la Configuration Manager locale](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) .</span><span class="sxs-lookup"><span data-stu-id="d6027-114">For more information on the individual attributes of the output, see the [Configuring the Local Configuration Manager](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) documentation.</span></span>

### <span data-ttu-id="d6027-115">Exemple 2 : obtenir les paramètres du gestionnaire de configuration local pour un ordinateur spécifié</span><span class="sxs-lookup"><span data-stu-id="d6027-115">Example 2: Get LCM settings for a specified computer</span></span>

```powershell
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Get-DscLocalConfigurationManager -CimSession $Session
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 169dfa57-a7f9-43be-a7a5-9dd06587e052
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName                 : Server01
PSComputerName                 : Server01
```

<span data-ttu-id="d6027-116">Cet exemple obtient les paramètres LCM pour un ordinateur spécifié par une session CIM.</span><span class="sxs-lookup"><span data-stu-id="d6027-116">This example gets LCM settings for a computer specified by a CIM session.</span></span>
<span data-ttu-id="d6027-117">L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d6027-117">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="d6027-118">Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d6027-118">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="d6027-119">La première commande crée une session CIM à l’aide de l’applet de commande `New-CimSession` , puis stocke l’objet **CimSession** dans la variable $session.</span><span class="sxs-lookup"><span data-stu-id="d6027-119">The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span> <span data-ttu-id="d6027-120">La commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="d6027-120">The command prompts you for a password.</span></span> <span data-ttu-id="d6027-121">Pour plus d'informations, voir `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="d6027-121">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="d6027-122">La deuxième commande obtient les paramètres de Configuration Manager locaux pour les ordinateurs identifiés par les objets **CimSession** stockés dans la variable $session.</span><span class="sxs-lookup"><span data-stu-id="d6027-122">The second command gets Local Configuration Manager settings for the computers identified by the **CimSession** objects stored in the $Session variable.</span></span> <span data-ttu-id="d6027-123">Dans ce cas, l’ordinateur nommé SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="d6027-123">In this case, the computer named Server01.</span></span>

## <span data-ttu-id="d6027-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d6027-124">PARAMETERS</span></span>

### <span data-ttu-id="d6027-125">-AsJob</span><span class="sxs-lookup"><span data-stu-id="d6027-125">-AsJob</span></span>

<span data-ttu-id="d6027-126">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d6027-126">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="d6027-127">-CimSession</span><span class="sxs-lookup"><span data-stu-id="d6027-127">-CimSession</span></span>

<span data-ttu-id="d6027-128">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="d6027-128">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="d6027-129">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande `New-CimSession` ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="d6027-129">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6027-130">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="d6027-130">-ThrottleLimit</span></span>

<span data-ttu-id="d6027-131">Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d6027-131">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

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

### <span data-ttu-id="d6027-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d6027-132">CommonParameters</span></span>

<span data-ttu-id="d6027-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d6027-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d6027-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d6027-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d6027-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d6027-135">INPUTS</span></span>

## <span data-ttu-id="d6027-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d6027-136">OUTPUTS</span></span>

## <span data-ttu-id="d6027-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d6027-137">NOTES</span></span>

## <span data-ttu-id="d6027-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d6027-138">RELATED LINKS</span></span>

[<span data-ttu-id="d6027-139">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6027-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="d6027-140">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d6027-140">Set-DscLocalConfigurationManager</span></span>](Set-DscLocalConfigurationManager.md)
