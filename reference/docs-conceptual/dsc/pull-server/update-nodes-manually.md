---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Mettre à jour des nœuds à partir d’un serveur Pull
description: Cet article explique comment mettre à jour des nœuds gérés par DSC à partir d’un serveur Pull
ms.openlocfilehash: 7256a0e1fdfaa8e56150c4f7299640bc95b82cee
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656754"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="b20ae-104">Mettre à jour des nœuds à partir d’un serveur Pull</span><span class="sxs-lookup"><span data-stu-id="b20ae-104">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="b20ae-105">Les sections ci-dessous supposent que vous avez déjà configuré un serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="b20ae-105">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="b20ae-106">Si vous n’avez pas configuré votre serveur Pull, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="b20ae-106">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="b20ae-107">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="b20ae-107">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b20ae-108">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="b20ae-108">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="b20ae-109">Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état.</span><span class="sxs-lookup"><span data-stu-id="b20ae-109">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="b20ae-110">Cet article montre comment charger des ressources afin qu’elles soient disponibles pour être téléchargées, et comment configurer les clients pour télécharger automatiquement des ressources.</span><span class="sxs-lookup"><span data-stu-id="b20ae-110">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="b20ae-111">Lorsque le nœud reçoit une configuration attribuée, via un serveur **Pull** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la configuration depuis l’emplacement spécifié dans le gestionnaire de configuration local (LCM).</span><span class="sxs-lookup"><span data-stu-id="b20ae-111">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="b20ae-112">Utilisation de l’applet de commande Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="b20ae-112">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="b20ae-113">À compter de PowerShell 5.0, l’applet de commande [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) force un nœud à mettre à jour sa configuration à partir du serveur Pull configuré dans le gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="b20ae-113">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="b20ae-114">Utilisation d’Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="b20ae-114">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="b20ae-115">Dans PowerShell 4.0, vous pouvez forcer manuellement un client Pull à mettre à jour sa configuration à l’aide d’[Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="b20ae-115">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="b20ae-116">L’exemple suivant crée une session CIM avec les informations d’identification spécifiées, appelle la méthode CIM appropriée, puis supprime la session.</span><span class="sxs-lookup"><span data-stu-id="b20ae-116">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="b20ae-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b20ae-117">See Also</span></span>

[<span data-ttu-id="b20ae-118">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="b20ae-118">PerformRequiredConfigurationChecks</span></span>](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
