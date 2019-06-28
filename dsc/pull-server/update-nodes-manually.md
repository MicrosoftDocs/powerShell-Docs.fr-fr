---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Mettre à jour des nœuds à partir d’un serveur Pull
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079096"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="4fdda-103">Mettre à jour des nœuds à partir d’un serveur Pull</span><span class="sxs-lookup"><span data-stu-id="4fdda-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="4fdda-104">Les sections ci-dessous supposent que vous avez déjà configuré un serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="4fdda-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="4fdda-105">Si vous n’avez pas configuré votre serveur Pull, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="4fdda-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="4fdda-106">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="4fdda-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="4fdda-107">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="4fdda-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="4fdda-108">Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état.</span><span class="sxs-lookup"><span data-stu-id="4fdda-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="4fdda-109">Cet article montre comment charger des ressources afin qu’elles soient disponibles pour être téléchargées, et comment configurer les clients pour télécharger automatiquement des ressources.</span><span class="sxs-lookup"><span data-stu-id="4fdda-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="4fdda-110">Lorsque le nœud reçoit une configuration attribuée, via un serveur **Pull** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la configuration depuis l’emplacement spécifié dans le gestionnaire de configuration local (LCM).</span><span class="sxs-lookup"><span data-stu-id="4fdda-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="4fdda-111">Utilisation de l’applet de commande Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="4fdda-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="4fdda-112">À compter de PowerShell 5.0, l’applet de commande [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) force un nœud à mettre à jour sa configuration à partir du serveur Pull configuré dans le gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="4fdda-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="4fdda-113">Utilisation d’Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="4fdda-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="4fdda-114">Dans PowerShell 4.0, vous pouvez forcer manuellement un client Pull à mettre à jour sa configuration à l’aide d’[Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="4fdda-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="4fdda-115">L’exemple suivant crée une session CIM avec les informations d’identification spécifiées, appelle la méthode CIM appropriée, puis supprime la session.</span><span class="sxs-lookup"><span data-stu-id="4fdda-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="4fdda-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fdda-116">See Also</span></span>

[<span data-ttu-id="4fdda-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="4fdda-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
