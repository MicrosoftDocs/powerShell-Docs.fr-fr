---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource nxService dans DSC pour Linux
ms.openlocfilehash: 6bb58796c4deff1153f932f61c328d84f8c4d2ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954836"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="7d649-103">Ressource nxService dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="7d649-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="7d649-104">La ressource **nxService** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des services sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="7d649-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d649-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d649-105">Syntax</span></span>

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="7d649-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7d649-106">Properties</span></span>

|<span data-ttu-id="7d649-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="7d649-107">Property</span></span> |<span data-ttu-id="7d649-108">Description</span><span class="sxs-lookup"><span data-stu-id="7d649-108">Description</span></span> |
|---|---|
|<span data-ttu-id="7d649-109">Name</span><span class="sxs-lookup"><span data-stu-id="7d649-109">Name</span></span> |<span data-ttu-id="7d649-110">Nom du service/démon à configurer.</span><span class="sxs-lookup"><span data-stu-id="7d649-110">The name of the service/daemon to configure.</span></span> |
|<span data-ttu-id="7d649-111">Controller</span><span class="sxs-lookup"><span data-stu-id="7d649-111">Controller</span></span> |<span data-ttu-id="7d649-112">Type de contrôleur de service à utiliser lors de la configuration du service.</span><span class="sxs-lookup"><span data-stu-id="7d649-112">The type of service controller to use when configuring the service.</span></span> |
|<span data-ttu-id="7d649-113">Enabled</span><span class="sxs-lookup"><span data-stu-id="7d649-113">Enabled</span></span> |<span data-ttu-id="7d649-114">Indique si le service s’exécute au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="7d649-114">Indicates whether the service starts on boot.</span></span> |
|<span data-ttu-id="7d649-115">State</span><span class="sxs-lookup"><span data-stu-id="7d649-115">State</span></span> |<span data-ttu-id="7d649-116">Indique si le service est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7d649-116">Indicates whether the service is running.</span></span> <span data-ttu-id="7d649-117">Définissez cette propriété sur **Stopped** pour vous assurer que le service n’est pas en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7d649-117">Set this property to **Stopped** to ensure that the service is not running.</span></span> <span data-ttu-id="7d649-118">Définissez cette propriété sur **Running** pour vous assurer que le service est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7d649-118">Set it to **Running** to ensure that the service is running.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7d649-119">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="7d649-119">Common properties</span></span>

|<span data-ttu-id="7d649-120">Propriété</span><span class="sxs-lookup"><span data-stu-id="7d649-120">Property</span></span> |<span data-ttu-id="7d649-121">Description</span><span class="sxs-lookup"><span data-stu-id="7d649-121">Description</span></span> |
|---|---|
|<span data-ttu-id="7d649-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7d649-122">DependsOn</span></span> |<span data-ttu-id="7d649-123">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="7d649-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7d649-124">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7d649-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="7d649-125">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="7d649-125">Additional Information</span></span>

<span data-ttu-id="7d649-126">La ressource **nxService** ne crée pas de fichier de définition ni de script pour le service si celui-ci n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="7d649-126">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="7d649-127">Vous pouvez utiliser la ressource **nxFile** dans DSC PowerShell pour gérer l’existence ou le contenu du fichier de définition ou script du service.</span><span class="sxs-lookup"><span data-stu-id="7d649-127">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="7d649-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="7d649-128">Example</span></span>

<span data-ttu-id="7d649-129">L’exemple suivant configure le service 'httpd' (pour Apache HTTP Server) qui est inscrit auprès du contrôleur de service **SystemD**.</span><span class="sxs-lookup"><span data-stu-id="7d649-129">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```