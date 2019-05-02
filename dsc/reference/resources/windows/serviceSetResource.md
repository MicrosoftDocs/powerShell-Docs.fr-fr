---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressources ServiceSet dans DSC
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076825"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="e88c5-103">Ressources ServiceSet dans DSC</span><span class="sxs-lookup"><span data-stu-id="e88c5-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="e88c5-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e88c5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e88c5-105">La ressource **ServiceSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="e88c5-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="e88c5-106">Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la [ressource Service](serviceResource.md) pour chaque service spécifié dans la propriété `Name`.</span><span class="sxs-lookup"><span data-stu-id="e88c5-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="e88c5-107">Utilisez cette ressource quand vous voulez configurer certains services au même état.</span><span class="sxs-lookup"><span data-stu-id="e88c5-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="e88c5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e88c5-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="e88c5-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e88c5-109">Properties</span></span>

|  <span data-ttu-id="e88c5-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="e88c5-110">Property</span></span>  |  <span data-ttu-id="e88c5-111">Description</span><span class="sxs-lookup"><span data-stu-id="e88c5-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="e88c5-112">Name</span><span class="sxs-lookup"><span data-stu-id="e88c5-112">Name</span></span>| <span data-ttu-id="e88c5-113">Indique les noms des services.</span><span class="sxs-lookup"><span data-stu-id="e88c5-113">Indicates the service names.</span></span> <span data-ttu-id="e88c5-114">Notez qu’ils peuvent être différents des noms d’affichages.</span><span class="sxs-lookup"><span data-stu-id="e88c5-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="e88c5-115">Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande [Get-Service](https://technet.microsoft.com/library/hh849804.aspx).</span><span class="sxs-lookup"><span data-stu-id="e88c5-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="e88c5-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="e88c5-116">StartupType</span></span>| <span data-ttu-id="e88c5-117">Indique le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="e88c5-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="e88c5-118">Les valeurs autorisées pour cette propriété sont : **Automatic**, **Disabled** et **Manual**</span><span class="sxs-lookup"><span data-stu-id="e88c5-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="e88c5-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="e88c5-119">BuiltInAccount</span></span>| <span data-ttu-id="e88c5-120">Indique le compte de connexion à utiliser pour les services.</span><span class="sxs-lookup"><span data-stu-id="e88c5-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="e88c5-121">Les valeurs autorisées pour cette propriété sont : **LocalService**, **LocalSystem** et **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="e88c5-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="e88c5-122">State</span><span class="sxs-lookup"><span data-stu-id="e88c5-122">State</span></span>| <span data-ttu-id="e88c5-123">Indique l’état que vous voulez assurer pour les services : **Arrêté** ou **Exécution en cours**.</span><span class="sxs-lookup"><span data-stu-id="e88c5-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="e88c5-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="e88c5-124">Ensure</span></span>| <span data-ttu-id="e88c5-125">Indique si les services existent sur le système.</span><span class="sxs-lookup"><span data-stu-id="e88c5-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="e88c5-126">Affectez la valeur **Absent** à cette propriété pour vous assurer que les services n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="e88c5-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="e88c5-127">La valeur **Present** (valeur par défaut) permet de s’assurer que le services cibles existent.</span><span class="sxs-lookup"><span data-stu-id="e88c5-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="e88c5-128">Credential</span><span class="sxs-lookup"><span data-stu-id="e88c5-128">Credential</span></span>| <span data-ttu-id="e88c5-129">Indique les informations d’identification pour le compte sous lequel s’exécute la ressource de service.</span><span class="sxs-lookup"><span data-stu-id="e88c5-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="e88c5-130">Cette propriété et la propriété **BuiltinAccount** ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="e88c5-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="e88c5-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e88c5-131">DependsOn</span></span>| <span data-ttu-id="e88c5-132">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="e88c5-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e88c5-133">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource *ResourceName* de type *ResourceType*, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e88c5-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="e88c5-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="e88c5-134">Example</span></span>

<span data-ttu-id="e88c5-135">La configuration suivante démarre les services « Audio Windows » et « Services Bureau à distance ».</span><span class="sxs-lookup"><span data-stu-id="e88c5-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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
