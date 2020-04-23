---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource Log dans DSC
ms.openlocfilehash: 0a2f12793357fdf10bd4a2f6003f9dc2276b173c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870759"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="2fddb-103">Ressource Log dans DSC</span><span class="sxs-lookup"><span data-stu-id="2fddb-103">DSC Log Resource</span></span>

> <span data-ttu-id="2fddb-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="2fddb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="2fddb-105">La ressource **Log** dans DSC (Desired State Configuration) Windows PowerShell fournit un mécanisme permettant d’écrire des messages dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="2fddb-105">The **Log** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fddb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fddb-106">Syntax</span></span>

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="2fddb-107">Par défaut, seuls les journaux des opérations relatifs à DSC sont activés.</span><span class="sxs-lookup"><span data-stu-id="2fddb-107">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="2fddb-108">Pour que le journal d’analyse soit disponible ou visible, il doit être activé.</span><span class="sxs-lookup"><span data-stu-id="2fddb-108">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="2fddb-109">Pour plus d’informations, consultez [Où se trouvent les journaux des événements DSC ?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="2fddb-109">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="2fddb-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2fddb-110">Properties</span></span>

| <span data-ttu-id="2fddb-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="2fddb-111">Property</span></span> |                                                   <span data-ttu-id="2fddb-112">Description</span><span class="sxs-lookup"><span data-stu-id="2fddb-112">Description</span></span>                                                    |
| -------- | ---------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="2fddb-113">Message</span><span class="sxs-lookup"><span data-stu-id="2fddb-113">Message</span></span>  | <span data-ttu-id="2fddb-114">Indique le message à écrire dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="2fddb-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="2fddb-115">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="2fddb-115">Common properties</span></span>

|       <span data-ttu-id="2fddb-116">Propriété</span><span class="sxs-lookup"><span data-stu-id="2fddb-116">Property</span></span>       |                                                                                                                                                          <span data-ttu-id="2fddb-117">Description</span><span class="sxs-lookup"><span data-stu-id="2fddb-117">Description</span></span>                                                                                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="2fddb-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2fddb-118">DependsOn</span></span>            | <span data-ttu-id="2fddb-119">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="2fddb-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2fddb-120">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2fddb-120">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
| <span data-ttu-id="2fddb-121">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="2fddb-121">PsDscRunAsCredential</span></span> | <span data-ttu-id="2fddb-122">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="2fddb-122">Sets the credential for running the entire resource as.</span></span>                                                                                                                                                                                                                                                                        |

> [!NOTE]
> <span data-ttu-id="2fddb-123">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="2fddb-123">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="2fddb-124">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="2fddb-124">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="2fddb-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="2fddb-125">Example</span></span>

<span data-ttu-id="2fddb-126">L’exemple suivant écrit un message dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="2fddb-126">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="2fddb-127">Si vous exécutez [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration?view=powershell-5.1) avec cette ressource configurée, elle retourne toujours la valeur **$false**.</span><span class="sxs-lookup"><span data-stu-id="2fddb-127">If you run [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration?view=powershell-5.1) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
