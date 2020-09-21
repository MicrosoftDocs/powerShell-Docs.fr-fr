---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource Service dans DSC
ms.openlocfilehash: f936f58ffd00f84d8c6d5d41d93378eaa8db5879
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463582"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="55806-103">Ressource Service dans DSC</span><span class="sxs-lookup"><span data-stu-id="55806-103">DSC Service Resource</span></span>

> <span data-ttu-id="55806-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="55806-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="55806-105">La ressource **Service** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="55806-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="55806-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55806-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupTimeout = [uint32]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DesktopInteract = [boolean]]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ TerminateTimeout = [uint32] ]
}
```

## <a name="properties"></a><span data-ttu-id="55806-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="55806-107">Properties</span></span>

|<span data-ttu-id="55806-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="55806-108">Property</span></span> |<span data-ttu-id="55806-109">Description</span><span class="sxs-lookup"><span data-stu-id="55806-109">Description</span></span> |
|---|---|
|<span data-ttu-id="55806-110">Nom</span><span class="sxs-lookup"><span data-stu-id="55806-110">Name</span></span> |<span data-ttu-id="55806-111">Indique le nom du service</span><span class="sxs-lookup"><span data-stu-id="55806-111">Indicates the service name.</span></span> <span data-ttu-id="55806-112">Notez qu’il peut être différent du nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="55806-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="55806-113">Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="55806-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="55806-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="55806-114">BuiltInAccount</span></span> |<span data-ttu-id="55806-115">Indique le compte de connexion à utiliser pour le service.</span><span class="sxs-lookup"><span data-stu-id="55806-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="55806-116">Sont autorisées pour cette propriété les valeurs suivantes : **LocalService**, **LocalSystem** et **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="55806-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="55806-117">Informations d'identification</span><span class="sxs-lookup"><span data-stu-id="55806-117">Credential</span></span> |<span data-ttu-id="55806-118">Indique les informations d’identification pour le compte sous lequel s’exécute le service.</span><span class="sxs-lookup"><span data-stu-id="55806-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="55806-119">Cette propriété et la propriété **BuiltinAccount** ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="55806-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="55806-120">StartupTimeout</span><span class="sxs-lookup"><span data-stu-id="55806-120">StartupTimeout</span></span> | <span data-ttu-id="55806-121">Délai d’attente de l’exécution du service en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="55806-121">The time to wait for the service to be running in milliseconds.</span></span>|
|<span data-ttu-id="55806-122">StartupType</span><span class="sxs-lookup"><span data-stu-id="55806-122">StartupType</span></span> |<span data-ttu-id="55806-123">Indique le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="55806-123">Indicates the startup type for the service.</span></span> <span data-ttu-id="55806-124">Sont autorisées pour cette propriété les valeurs suivantes : **Automatic**, **Disabled** et **Manual**.</span><span class="sxs-lookup"><span data-stu-id="55806-124">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="55806-125">State</span><span class="sxs-lookup"><span data-stu-id="55806-125">State</span></span> |<span data-ttu-id="55806-126">Indique l’état que vous voulez assurer pour le service.</span><span class="sxs-lookup"><span data-stu-id="55806-126">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="55806-127">Les valeurs sont : **Running** ou **Stopped**.</span><span class="sxs-lookup"><span data-stu-id="55806-127">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="55806-128">TerminateTimeout</span><span class="sxs-lookup"><span data-stu-id="55806-128">TerminateTimeout</span></span> |<span data-ttu-id="55806-129">Délai d’attente de l’arrêt du service en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="55806-129">The time to wait for the service to be stopped in milliseconds.</span></span>|
|<span data-ttu-id="55806-130">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="55806-130">Dependencies</span></span> | <span data-ttu-id="55806-131">Tableau des noms des dépendances que le service doit avoir.</span><span class="sxs-lookup"><span data-stu-id="55806-131">An array of the names of the dependencies the service should have.</span></span> |
|<span data-ttu-id="55806-132">Description</span><span class="sxs-lookup"><span data-stu-id="55806-132">Description</span></span> |<span data-ttu-id="55806-133">Indique la description du service cible.</span><span class="sxs-lookup"><span data-stu-id="55806-133">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="55806-134">DesktopInteract</span><span class="sxs-lookup"><span data-stu-id="55806-134">DesktopInteract</span></span> | <span data-ttu-id="55806-135">Indique si le service doit être en mesure de communiquer avec une fenêtre sur le bureau.</span><span class="sxs-lookup"><span data-stu-id="55806-135">Indicates whether or not the service should be able to communicate with a window on the desktop.</span></span> <span data-ttu-id="55806-136">Doit avoir la valeur false pour les services qui ne s’exécutent pas en tant que LocalSystem.</span><span class="sxs-lookup"><span data-stu-id="55806-136">Must be false for services not running as LocalSystem.</span></span>|
|<span data-ttu-id="55806-137">DisplayName</span><span class="sxs-lookup"><span data-stu-id="55806-137">DisplayName</span></span> |<span data-ttu-id="55806-138">Indique le nom complet du service cible.</span><span class="sxs-lookup"><span data-stu-id="55806-138">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="55806-139">Chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="55806-139">Path</span></span> |<span data-ttu-id="55806-140">Indique le chemin du fichier binaire d’un nouveau service.</span><span class="sxs-lookup"><span data-stu-id="55806-140">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="55806-141">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="55806-141">Common properties</span></span>

|<span data-ttu-id="55806-142">Propriété</span><span class="sxs-lookup"><span data-stu-id="55806-142">Property</span></span> |<span data-ttu-id="55806-143">Description</span><span class="sxs-lookup"><span data-stu-id="55806-143">Description</span></span> |
|---|---|
|<span data-ttu-id="55806-144">DependsOn</span><span class="sxs-lookup"><span data-stu-id="55806-144">DependsOn</span></span> |<span data-ttu-id="55806-145">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="55806-145">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="55806-146">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="55806-146">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="55806-147">Ensure</span><span class="sxs-lookup"><span data-stu-id="55806-147">Ensure</span></span> |<span data-ttu-id="55806-148">Indique si le service cible existe sur le système.</span><span class="sxs-lookup"><span data-stu-id="55806-148">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="55806-149">Affectez la valeur **Absent** à cette propriété pour vous assurer que le service cible n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="55806-149">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="55806-150">Définissez-la sur **Present** pour être assuré que le service cible n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="55806-150">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="55806-151">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="55806-151">The default value is **Present**.</span></span> |
|<span data-ttu-id="55806-152">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="55806-152">PsDscRunAsCredential</span></span> |<span data-ttu-id="55806-153">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="55806-153">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="55806-154">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="55806-154">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="55806-155">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="55806-155">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="55806-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="55806-156">Example</span></span>

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
