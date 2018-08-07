---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Registry dans DSC
ms.openlocfilehash: 8d74473d167b70182c3a16c1d39d2a9e797afb1b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267719"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="166e9-103">Ressource Registry dans DSC</span><span class="sxs-lookup"><span data-stu-id="166e9-103">DSC Registry Resource</span></span>

<span data-ttu-id="166e9-104">_S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="166e9-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="166e9-105">La ressource **Registry** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer les clés et les valeurs de Registre sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="166e9-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="166e9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="166e9-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="166e9-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="166e9-107">Properties</span></span>

| <span data-ttu-id="166e9-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="166e9-108">Property</span></span> | <span data-ttu-id="166e9-109">Description</span><span class="sxs-lookup"><span data-stu-id="166e9-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="166e9-110">Clé</span><span class="sxs-lookup"><span data-stu-id="166e9-110">Key</span></span>| <span data-ttu-id="166e9-111">Indique le chemin de la clé de Registre pour laquelle vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="166e9-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="166e9-112">Ce chemin doit inclure la ruche.</span><span class="sxs-lookup"><span data-stu-id="166e9-112">This path must include the hive.</span></span>|
| <span data-ttu-id="166e9-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="166e9-113">ValueName</span></span>| <span data-ttu-id="166e9-114">Indique le nom de la valeur de Registre.</span><span class="sxs-lookup"><span data-stu-id="166e9-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="166e9-115">Pour ajouter ou supprimer une clé de Registre, spécifiez cette propriété comme une chaîne vide sans définir ValueType ou ValueData.</span><span class="sxs-lookup"><span data-stu-id="166e9-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="166e9-116">Pour modifier ou supprimer la valeur par défaut d’une clé de Registre, spécifiez cette propriété comme une chaîne vide tout en définissant ValueType ou ValueData.</span><span class="sxs-lookup"><span data-stu-id="166e9-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="166e9-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="166e9-117">Ensure</span></span>| <span data-ttu-id="166e9-118">Indique si la clé et la valeur existent.</span><span class="sxs-lookup"><span data-stu-id="166e9-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="166e9-119">Pour vous assurer qu’elles existent, définissez cette propriété sur « Present ».</span><span class="sxs-lookup"><span data-stu-id="166e9-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="166e9-120">Pour vous assurer qu’elles n’existent pas, définissez la propriété sur « Absent ».</span><span class="sxs-lookup"><span data-stu-id="166e9-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="166e9-121">La valeur par défaut est « Present ».</span><span class="sxs-lookup"><span data-stu-id="166e9-121">The default value is "Present".</span></span>|
| <span data-ttu-id="166e9-122">Force</span><span class="sxs-lookup"><span data-stu-id="166e9-122">Force</span></span>| <span data-ttu-id="166e9-123">Si la clé de Registre spécifiée est présente, **Force** la remplace par la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="166e9-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="166e9-124">Si vous supprimez une clé de Registre avec des sous-clés, la valeur doit être **$true**</span><span class="sxs-lookup"><span data-stu-id="166e9-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="166e9-125">Hex</span><span class="sxs-lookup"><span data-stu-id="166e9-125">Hex</span></span>| <span data-ttu-id="166e9-126">Indique si les données sont exprimées au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="166e9-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="166e9-127">Si elles sont spécifiées, les données de valeur DWORD/QWORD sont présentées au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="166e9-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="166e9-128">Non valide pour les autres types.</span><span class="sxs-lookup"><span data-stu-id="166e9-128">Not valid for other types.</span></span> <span data-ttu-id="166e9-129">La valeur par défaut est **$false**.</span><span class="sxs-lookup"><span data-stu-id="166e9-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="166e9-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="166e9-130">DependsOn</span></span>| <span data-ttu-id="166e9-131">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="166e9-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="166e9-132">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="166e9-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="166e9-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="166e9-133">ValueData</span></span>| <span data-ttu-id="166e9-134">Les données de la valeur de Registre.</span><span class="sxs-lookup"><span data-stu-id="166e9-134">The data for the registry value.</span></span>|
| <span data-ttu-id="166e9-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="166e9-135">ValueType</span></span>| <span data-ttu-id="166e9-136">Indique le type de la valeur.</span><span class="sxs-lookup"><span data-stu-id="166e9-136">Indicates the type of the value.</span></span> <span data-ttu-id="166e9-137">Les types pris en charge sont : chaîne (REG_SZ), binaire (REG-BINARY), Dword 32 bits (REG_DWORD), Qword 64 bits (REG_QWORD), chaîne multiple (REG_MULTI_SZ), chaîne extensible (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="166e9-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="166e9-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="166e9-138">Example</span></span>

<span data-ttu-id="166e9-139">Cet exemple permet de s’assurer qu’une clé nommée « ExampleKey » est présente dans la ruche **HKEY\_LOCAL\_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="166e9-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="166e9-140">Le changement d’un paramètre de Registre dans la ruche `HKEY\CURRENT\USER` nécessite l’exécution de la configuration à l’aide des informations d’identification de l’utilisateur, et non celles du système.</span><span class="sxs-lookup"><span data-stu-id="166e9-140">Changing a registry setting in the `HKEY\CURRENT\USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="166e9-141">Vous pouvez utiliser la propriété **PsDscRunAsCredential** pour spécifier les informations d’identification de l’utilisateur pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="166e9-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="166e9-142">Pour obtenir un exemple, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="166e9-142">For an example, see [Running DSC with user credentials](runAsUser.md).</span></span>