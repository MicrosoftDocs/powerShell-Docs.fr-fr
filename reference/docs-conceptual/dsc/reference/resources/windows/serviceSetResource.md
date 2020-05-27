---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressources ServiceSet dans DSC
ms.openlocfilehash: a071a8cdd4a7dc6fd050fc1b88901aa0ce428615
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563967"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="4be96-103">Ressources ServiceSet dans DSC</span><span class="sxs-lookup"><span data-stu-id="4be96-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="4be96-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="4be96-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="4be96-105">La ressource **ServiceSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="4be96-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="4be96-106">Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la [ressource Service](serviceResource.md) pour chaque service spécifié dans la propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="4be96-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the **Name** property.</span></span>

<span data-ttu-id="4be96-107">Utilisez cette ressource quand vous voulez configurer certains services au même état.</span><span class="sxs-lookup"><span data-stu-id="4be96-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="4be96-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4be96-108">Syntax</span></span>

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="4be96-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4be96-109">Properties</span></span>

|<span data-ttu-id="4be96-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="4be96-110">Property</span></span> |<span data-ttu-id="4be96-111">Description</span><span class="sxs-lookup"><span data-stu-id="4be96-111">Description</span></span> |
|---|---|
|<span data-ttu-id="4be96-112">Nom</span><span class="sxs-lookup"><span data-stu-id="4be96-112">Name</span></span> |<span data-ttu-id="4be96-113">Indique les noms des services.</span><span class="sxs-lookup"><span data-stu-id="4be96-113">Indicates the service names.</span></span> <span data-ttu-id="4be96-114">Notez qu’ils peuvent être différents des noms d’affichages.</span><span class="sxs-lookup"><span data-stu-id="4be96-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="4be96-115">Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="4be96-115">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="4be96-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="4be96-116">StartupType</span></span> |<span data-ttu-id="4be96-117">Indique le type de démarrage pour les services.</span><span class="sxs-lookup"><span data-stu-id="4be96-117">Indicates the startup type for the services.</span></span> <span data-ttu-id="4be96-118">Sont autorisées pour cette propriété les valeurs suivantes : **Automatic**, **Disabled** et **Manual**.</span><span class="sxs-lookup"><span data-stu-id="4be96-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="4be96-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="4be96-119">BuiltInAccount</span></span> |<span data-ttu-id="4be96-120">Indique le compte de connexion à utiliser pour les services.</span><span class="sxs-lookup"><span data-stu-id="4be96-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="4be96-121">Sont autorisées pour cette propriété les valeurs suivantes : **LocalService**, **LocalSystem** et **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="4be96-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="4be96-122">State</span><span class="sxs-lookup"><span data-stu-id="4be96-122">State</span></span> |<span data-ttu-id="4be96-123">Indique l’état que vous voulez assurer pour les services : **Arrêté** ou **Exécution en cours**.</span><span class="sxs-lookup"><span data-stu-id="4be96-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span> |
|<span data-ttu-id="4be96-124">Informations d'identification</span><span class="sxs-lookup"><span data-stu-id="4be96-124">Credential</span></span> |<span data-ttu-id="4be96-125">Indique les informations d’identification pour le compte sous lequel s’exécute la ressource de service.</span><span class="sxs-lookup"><span data-stu-id="4be96-125">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="4be96-126">Cette propriété et la propriété **BuiltinAccount** ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="4be96-126">This property and the **BuiltinAccount** property cannot be used together.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4be96-127">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="4be96-127">Common properties</span></span>

|<span data-ttu-id="4be96-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="4be96-128">Property</span></span> |<span data-ttu-id="4be96-129">Description</span><span class="sxs-lookup"><span data-stu-id="4be96-129">Description</span></span> |
|---|---|
|<span data-ttu-id="4be96-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4be96-130">DependsOn</span></span> |<span data-ttu-id="4be96-131">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="4be96-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4be96-132">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4be96-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4be96-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="4be96-133">Ensure</span></span> |<span data-ttu-id="4be96-134">Indique si les services existent sur le système.</span><span class="sxs-lookup"><span data-stu-id="4be96-134">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="4be96-135">Affectez la valeur **Absent** à cette propriété pour vous assurer que les services n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="4be96-135">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="4be96-136">Définissez-la sur **Present** pour faire en sorte que les services cibles n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="4be96-136">Setting it to **Present** ensures that target services exist.</span></span> <span data-ttu-id="4be96-137">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="4be96-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="4be96-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4be96-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="4be96-139">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="4be96-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="4be96-140">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="4be96-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="4be96-141">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="4be96-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="4be96-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="4be96-142">Example</span></span>

<span data-ttu-id="4be96-143">La configuration suivante démarre les services « Audio Windows » et « Services Bureau à distance ».</span><span class="sxs-lookup"><span data-stu-id="4be96-143">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
