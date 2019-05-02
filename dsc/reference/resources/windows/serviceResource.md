---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Service dans DSC
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076888"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="10ab6-103">Ressource Service dans DSC</span><span class="sxs-lookup"><span data-stu-id="10ab6-103">DSC Service Resource</span></span>

> <span data-ttu-id="10ab6-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="10ab6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="10ab6-105">La ressource **Service** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="10ab6-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="10ab6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10ab6-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="10ab6-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="10ab6-107">Properties</span></span>

|  <span data-ttu-id="10ab6-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="10ab6-108">Property</span></span>  |  <span data-ttu-id="10ab6-109">Description</span><span class="sxs-lookup"><span data-stu-id="10ab6-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="10ab6-110">Name</span><span class="sxs-lookup"><span data-stu-id="10ab6-110">Name</span></span>| <span data-ttu-id="10ab6-111">Indique le nom du service</span><span class="sxs-lookup"><span data-stu-id="10ab6-111">Indicates the service name.</span></span> <span data-ttu-id="10ab6-112">Notez qu’il peut être différent du nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="10ab6-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="10ab6-113">Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande Get-Service.</span><span class="sxs-lookup"><span data-stu-id="10ab6-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="10ab6-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="10ab6-114">BuiltInAccount</span></span>| <span data-ttu-id="10ab6-115">Indique le compte de connexion à utiliser pour le service.</span><span class="sxs-lookup"><span data-stu-id="10ab6-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="10ab6-116">Sont autorisées pour cette propriété les valeurs suivantes : **LocalService**, **LocalSystem** et **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="10ab6-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="10ab6-117">Credential</span><span class="sxs-lookup"><span data-stu-id="10ab6-117">Credential</span></span>| <span data-ttu-id="10ab6-118">Indique les informations d’identification pour le compte sous lequel s’exécute le service.</span><span class="sxs-lookup"><span data-stu-id="10ab6-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="10ab6-119">Cette propriété et la propriété __BuiltinAccount__ ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="10ab6-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="10ab6-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="10ab6-120">DependsOn</span></span>| <span data-ttu-id="10ab6-121">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="10ab6-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="10ab6-122">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="10ab6-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="10ab6-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="10ab6-123">StartupType</span></span>| <span data-ttu-id="10ab6-124">Indique le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="10ab6-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="10ab6-125">Sont autorisées pour cette propriété les valeurs suivantes : **Automatic**, **Disabled** et **Manual**</span><span class="sxs-lookup"><span data-stu-id="10ab6-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="10ab6-126">State</span><span class="sxs-lookup"><span data-stu-id="10ab6-126">State</span></span>| <span data-ttu-id="10ab6-127">Indique l’état que vous voulez assurer pour le service.</span><span class="sxs-lookup"><span data-stu-id="10ab6-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="10ab6-128">Description</span><span class="sxs-lookup"><span data-stu-id="10ab6-128">Description</span></span> | <span data-ttu-id="10ab6-129">Indique la description du service cible.</span><span class="sxs-lookup"><span data-stu-id="10ab6-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="10ab6-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="10ab6-130">DisplayName</span></span> | <span data-ttu-id="10ab6-131">Indique le nom complet du service cible.</span><span class="sxs-lookup"><span data-stu-id="10ab6-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="10ab6-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="10ab6-132">Ensure</span></span> | <span data-ttu-id="10ab6-133">Indique si le service cible existe sur le système.</span><span class="sxs-lookup"><span data-stu-id="10ab6-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="10ab6-134">Affectez la valeur **Absent** à cette propriété pour vous assurer que le service cible n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="10ab6-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="10ab6-135">La valeur **Present** (valeur par défaut) permet de s’assurer que le service cible existe.</span><span class="sxs-lookup"><span data-stu-id="10ab6-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="10ab6-136">Path</span><span class="sxs-lookup"><span data-stu-id="10ab6-136">Path</span></span> | <span data-ttu-id="10ab6-137">Indique le chemin du fichier binaire d’un nouveau service.</span><span class="sxs-lookup"><span data-stu-id="10ab6-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="10ab6-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="10ab6-138">Example</span></span>

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