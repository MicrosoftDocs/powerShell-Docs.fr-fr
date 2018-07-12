---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.topic: conceptual
contributor: vaibch
title: Échec des applets de commande du Gestionnaire de commutateur réseau
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893152"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="2cfce-103">Échec des applets de commande du Gestionnaire de commutateur réseau</span><span class="sxs-lookup"><span data-stu-id="2cfce-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="2cfce-104">Les applets de commande du Gestionnaire de commutateur réseau peuvent être utilisées pour gérer les commutateurs réseau via WSMAN.</span><span class="sxs-lookup"><span data-stu-id="2cfce-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="2cfce-105">Quelques applets de commande de ce module peuvent accepter des valeurs provenant de pipelines.</span><span class="sxs-lookup"><span data-stu-id="2cfce-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="2cfce-106">Dans WMF 5.1 Preview, l’exécution des applets de commande qui peuvent accepter une valeur provenant d’un pipeline échoue quand les valeurs ne sont pas passées via des pipelines.</span><span class="sxs-lookup"><span data-stu-id="2cfce-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="2cfce-107">Si le paramètre « InputObject » n’est pas utilisé, l’applet de commande doit continuer à s’exécuter sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="2cfce-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="2cfce-108">Voici la liste des applets de commande affectées (ces applets de commande peuvent accepter une valeur pour le paramètre « InputObject » provenant d’un pipeline).</span><span class="sxs-lookup"><span data-stu-id="2cfce-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="2cfce-109">Si cette valeur n’est pas passée depuis un pipeline, l’exécution de l’applet de commande échoue.</span><span class="sxs-lookup"><span data-stu-id="2cfce-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="2cfce-110">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="2cfce-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="2cfce-111">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="2cfce-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="2cfce-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="2cfce-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="2cfce-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="2cfce-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="2cfce-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="2cfce-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="2cfce-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="2cfce-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="2cfce-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="2cfce-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="2cfce-117">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="2cfce-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="2cfce-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="2cfce-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="2cfce-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="2cfce-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="2cfce-120">Solution</span><span class="sxs-lookup"><span data-stu-id="2cfce-120">Resolution</span></span>

<span data-ttu-id="2cfce-121">Les applets de commande fonctionnent correctement quand la valeur du paramètre InputObject leur est passée via un pipeline.</span><span class="sxs-lookup"><span data-stu-id="2cfce-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="2cfce-122">Voici quelques exemples qui fonctionnent pour les applets de commande ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="2cfce-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```