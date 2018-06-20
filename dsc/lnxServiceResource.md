---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxService dans DSC pour Linux
ms.openlocfilehash: 9cab889368469f2c854a387b919aea58a49f2210
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187716"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="6b950-103">Ressource nxService dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="6b950-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="6b950-104">La ressource **nxService** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des services sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="6b950-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b950-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b950-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="6b950-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6b950-106">Properties</span></span>
|  <span data-ttu-id="6b950-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="6b950-107">Property</span></span> |  <span data-ttu-id="6b950-108">Description</span><span class="sxs-lookup"><span data-stu-id="6b950-108">Description</span></span> |
|---|---|
| <span data-ttu-id="6b950-109">Name</span><span class="sxs-lookup"><span data-stu-id="6b950-109">Name</span></span>| <span data-ttu-id="6b950-110">Nom du service/démon à configurer.</span><span class="sxs-lookup"><span data-stu-id="6b950-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="6b950-111">Controller</span><span class="sxs-lookup"><span data-stu-id="6b950-111">Controller</span></span>| <span data-ttu-id="6b950-112">Type de contrôleur de service à utiliser lors de la configuration du service.</span><span class="sxs-lookup"><span data-stu-id="6b950-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="6b950-113">Enabled</span><span class="sxs-lookup"><span data-stu-id="6b950-113">Enabled</span></span>| <span data-ttu-id="6b950-114">Indique si le service s’exécute au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="6b950-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="6b950-115">State</span><span class="sxs-lookup"><span data-stu-id="6b950-115">State</span></span>| <span data-ttu-id="6b950-116">Indique si le service est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6b950-116">Indicates whether the service is running.</span></span> <span data-ttu-id="6b950-117">Définissez cette propriété sur « Stopped » pour vous assurer que le service n’est pas en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6b950-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="6b950-118">Définissez cette propriété sur « Running » pour vous assurer que le service est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6b950-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="6b950-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6b950-119">DependsOn</span></span> | <span data-ttu-id="6b950-120">Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="6b950-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6b950-121">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6b950-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="additional-information"></a><span data-ttu-id="6b950-122">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="6b950-122">Additional Information</span></span>

<span data-ttu-id="6b950-123">La ressource **nxService** ne crée pas de fichier de définition ni de script pour le service si celui-ci n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="6b950-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="6b950-124">Vous pouvez utiliser la ressource **nxFile** dans DSC PowerShell pour gérer l’existence ou le contenu du fichier de définition ou script du service.</span><span class="sxs-lookup"><span data-stu-id="6b950-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="6b950-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b950-125">Example</span></span>

<span data-ttu-id="6b950-126">L’exemple suivant configure le service « httpd » (pour Apache HTTP Server) qui est inscrit auprès du contrôleur de service **SystemD**.</span><span class="sxs-lookup"><span data-stu-id="6b950-126">The following example shows configuration of the “httpd” service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```
Import-DSCResource -Module nx

Node $node {
#Apache Service
nxService ApacheService
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```