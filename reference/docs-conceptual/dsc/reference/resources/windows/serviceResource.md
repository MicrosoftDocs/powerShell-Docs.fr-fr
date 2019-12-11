---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource Service dans DSC
ms.openlocfilehash: 0bef6aa6d3526c9d8d92187c1e738d5c46b5665a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953046"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="1b1fa-103">Ressource Service dans DSC</span><span class="sxs-lookup"><span data-stu-id="1b1fa-103">DSC Service Resource</span></span>

> <span data-ttu-id="1b1fa-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="1b1fa-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="1b1fa-105">La ressource **Service** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b1fa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b1fa-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="1b1fa-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1b1fa-107">Properties</span></span>

|<span data-ttu-id="1b1fa-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="1b1fa-108">Property</span></span> |<span data-ttu-id="1b1fa-109">Description</span><span class="sxs-lookup"><span data-stu-id="1b1fa-109">Description</span></span> |
|---|---|
|<span data-ttu-id="1b1fa-110">Name</span><span class="sxs-lookup"><span data-stu-id="1b1fa-110">Name</span></span> |<span data-ttu-id="1b1fa-111">Indique le nom du service</span><span class="sxs-lookup"><span data-stu-id="1b1fa-111">Indicates the service name.</span></span> <span data-ttu-id="1b1fa-112">Notez qu’il peut être différent du nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="1b1fa-113">Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="1b1fa-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="1b1fa-114">BuiltInAccount</span></span> |<span data-ttu-id="1b1fa-115">Indique le compte de connexion à utiliser pour le service.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="1b1fa-116">Sont autorisées pour cette propriété les valeurs suivantes : **LocalService**, **LocalSystem** et **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="1b1fa-117">Credential</span><span class="sxs-lookup"><span data-stu-id="1b1fa-117">Credential</span></span> |<span data-ttu-id="1b1fa-118">Indique les informations d’identification pour le compte sous lequel s’exécute le service.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="1b1fa-119">Cette propriété et la propriété **BuiltinAccount** ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="1b1fa-120">StartupType</span><span class="sxs-lookup"><span data-stu-id="1b1fa-120">StartupType</span></span> |<span data-ttu-id="1b1fa-121">Indique le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="1b1fa-122">Sont autorisées pour cette propriété les valeurs suivantes : **Automatic**, **Disabled** et **Manual**.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-122">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="1b1fa-123">State</span><span class="sxs-lookup"><span data-stu-id="1b1fa-123">State</span></span> |<span data-ttu-id="1b1fa-124">Indique l’état que vous voulez assurer pour le service.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="1b1fa-125">Les valeurs sont : **Running** ou **Stopped**.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-125">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="1b1fa-126">Description</span><span class="sxs-lookup"><span data-stu-id="1b1fa-126">Description</span></span> |<span data-ttu-id="1b1fa-127">Indique la description du service cible.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-127">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="1b1fa-128">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1b1fa-128">DisplayName</span></span> |<span data-ttu-id="1b1fa-129">Indique le nom complet du service cible.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-129">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="1b1fa-130">Path</span><span class="sxs-lookup"><span data-stu-id="1b1fa-130">Path</span></span> |<span data-ttu-id="1b1fa-131">Indique le chemin du fichier binaire d’un nouveau service.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-131">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1b1fa-132">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="1b1fa-132">Common properties</span></span>

|<span data-ttu-id="1b1fa-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="1b1fa-133">Property</span></span> |<span data-ttu-id="1b1fa-134">Description</span><span class="sxs-lookup"><span data-stu-id="1b1fa-134">Description</span></span> |
|---|---|
|<span data-ttu-id="1b1fa-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1b1fa-135">DependsOn</span></span> |<span data-ttu-id="1b1fa-136">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1b1fa-137">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1b1fa-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="1b1fa-138">Ensure</span></span> |<span data-ttu-id="1b1fa-139">Indique si le service cible existe sur le système.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-139">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="1b1fa-140">Affectez la valeur **Absent** à cette propriété pour vous assurer que le service cible n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-140">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="1b1fa-141">Définissez-la sur **Present** pour être assuré que le service cible n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-141">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="1b1fa-142">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="1b1fa-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1b1fa-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="1b1fa-144">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="1b1fa-145">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="1b1fa-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1b1fa-146">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="1b1fa-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="1b1fa-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="1b1fa-147">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```