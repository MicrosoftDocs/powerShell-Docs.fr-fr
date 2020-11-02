---
ms.date: 07/16/2020
ms.topic: reference
title: Ressource Registry dans DSC
description: Ressource Registry dans DSC
ms.openlocfilehash: 075f64abffb429b83958d859b0328b4eeec4cee6
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142495"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="d6d96-103">Ressource Registry dans DSC</span><span class="sxs-lookup"><span data-stu-id="d6d96-103">DSC Registry Resource</span></span>

> <span data-ttu-id="d6d96-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="d6d96-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="d6d96-105">La ressource **Registry** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer les clés et les valeurs de Registre sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="d6d96-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="d6d96-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6d96-106">Syntax</span></span>

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="d6d96-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d6d96-107">Properties</span></span>

|<span data-ttu-id="d6d96-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="d6d96-108">Property</span></span> |<span data-ttu-id="d6d96-109">Description</span><span class="sxs-lookup"><span data-stu-id="d6d96-109">Description</span></span> |
|---|---|
|<span data-ttu-id="d6d96-110">Clé</span><span class="sxs-lookup"><span data-stu-id="d6d96-110">Key</span></span> |<span data-ttu-id="d6d96-111">Indique le chemin de la clé de Registre pour laquelle vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="d6d96-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="d6d96-112">Ce chemin doit inclure la ruche.</span><span class="sxs-lookup"><span data-stu-id="d6d96-112">This path must include the hive.</span></span> |
|<span data-ttu-id="d6d96-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="d6d96-113">ValueName</span></span> |<span data-ttu-id="d6d96-114">Indique le nom de la valeur de Registre.</span><span class="sxs-lookup"><span data-stu-id="d6d96-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="d6d96-115">Pour ajouter ou supprimer une clé de Registre, spécifiez cette propriété en tant que chaîne vide sans définir **ValueType** ou **ValueData** .</span><span class="sxs-lookup"><span data-stu-id="d6d96-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData** .</span></span> <span data-ttu-id="d6d96-116">Pour modifier ou supprimer la valeur par défaut d’une clé de Registre, spécifiez cette propriété en tant que chaîne vide tout en définissant également **ValueType** ou **ValueData** .</span><span class="sxs-lookup"><span data-stu-id="d6d96-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData** .</span></span> |
|<span data-ttu-id="d6d96-117">Force</span><span class="sxs-lookup"><span data-stu-id="d6d96-117">Force</span></span> |<span data-ttu-id="d6d96-118">Si la clé de Registre spécifiée est présente, **Force** la remplace par la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="d6d96-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="d6d96-119">Si vous supprimez une clé de Registre avec des sous-clés, la valeur doit être `$true`.</span><span class="sxs-lookup"><span data-stu-id="d6d96-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="d6d96-120">Hex</span><span class="sxs-lookup"><span data-stu-id="d6d96-120">Hex</span></span> |<span data-ttu-id="d6d96-121">Indique si les données sont exprimées au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="d6d96-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="d6d96-122">Si elles sont spécifiées, les données de valeur DWORD/QWORD sont présentées au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="d6d96-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="d6d96-123">Non valide pour les autres types.</span><span class="sxs-lookup"><span data-stu-id="d6d96-123">Not valid for other types.</span></span> <span data-ttu-id="d6d96-124">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="d6d96-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="d6d96-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="d6d96-125">ValueData</span></span> |<span data-ttu-id="d6d96-126">Les données de la valeur de Registre.</span><span class="sxs-lookup"><span data-stu-id="d6d96-126">The data for the registry value.</span></span> |
|<span data-ttu-id="d6d96-127">ValueType</span><span class="sxs-lookup"><span data-stu-id="d6d96-127">ValueType</span></span> |<span data-ttu-id="d6d96-128">Indique le type de la valeur.</span><span class="sxs-lookup"><span data-stu-id="d6d96-128">Indicates the type of the value.</span></span> <span data-ttu-id="d6d96-129">Les types pris en charge sont les suivants : **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (REG_DWORD 32 bits), **Qword** (REG_QWORD 64 bits), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span><span class="sxs-lookup"><span data-stu-id="d6d96-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d6d96-130">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="d6d96-130">Common properties</span></span>

|<span data-ttu-id="d6d96-131">Propriété</span><span class="sxs-lookup"><span data-stu-id="d6d96-131">Property</span></span> |<span data-ttu-id="d6d96-132">Description</span><span class="sxs-lookup"><span data-stu-id="d6d96-132">Description</span></span> |
|---|---|
|<span data-ttu-id="d6d96-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d6d96-133">DependsOn</span></span> |<span data-ttu-id="d6d96-134">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="d6d96-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d6d96-135">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d6d96-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d6d96-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="d6d96-136">Ensure</span></span> |<span data-ttu-id="d6d96-137">Indique si la clé et la valeur existent.</span><span class="sxs-lookup"><span data-stu-id="d6d96-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="d6d96-138">Pour faire en sorte qu’elles existent, définissez cette propriété sur **Present** .</span><span class="sxs-lookup"><span data-stu-id="d6d96-138">To ensure that they do, set this property to **Present** .</span></span> <span data-ttu-id="d6d96-139">Pour faire en sorte qu’elles n’existent pas, définissez la propriété sur **Absent** .</span><span class="sxs-lookup"><span data-stu-id="d6d96-139">To ensure that they do not exist, set the property to **Absent** .</span></span> <span data-ttu-id="d6d96-140">La valeur par défaut est **Present** .</span><span class="sxs-lookup"><span data-stu-id="d6d96-140">The default value is **Present** .</span></span> |
|<span data-ttu-id="d6d96-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d6d96-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="d6d96-142">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="d6d96-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="d6d96-143">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="d6d96-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="d6d96-144">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="d6d96-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="examples"></a><span data-ttu-id="d6d96-145">Exemples</span><span class="sxs-lookup"><span data-stu-id="d6d96-145">Examples</span></span>

### <a name="example-1-ensure-specified-value-and-data-under-specified-registry-key"></a><span data-ttu-id="d6d96-146">Exemple 1 : Vérifier une valeur et des données spécifiées sous une clé de Registre spécifiée</span><span class="sxs-lookup"><span data-stu-id="d6d96-146">Example 1: Ensure specified Value and Data under specified registry key</span></span>

<span data-ttu-id="d6d96-147">Cet exemple vérifie que la valeur de Registre « TestValue » sous une clé nommée « ExampleKey1 » est présente dans la ruche `HKEY\_LOCAL\_MACHINE` et contient les données « TestData ».</span><span class="sxs-lookup"><span data-stu-id="d6d96-147">This example ensures that the registry value "TestValue" under a key named "ExampleKey1" is present in the `HKEY\_LOCAL\_MACHINE` hive and has the data "TestData".</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey1"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

### <a name="example-2-ensure-specified-registry-key-exists"></a><span data-ttu-id="d6d96-148">Exemple 2 : Vérifier l’existence d’une clé de Registre spécifiée</span><span class="sxs-lookup"><span data-stu-id="d6d96-148">Example 2: Ensure specified registry key exists</span></span>

<span data-ttu-id="d6d96-149">Cet exemple vérifie qu’une clé nommée « ExampleKey2 » est présente dans la ruche **HKEY\_LOCAL\_MACHINE** .</span><span class="sxs-lookup"><span data-stu-id="d6d96-149">This example ensures that a key named "ExampleKey2" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey2"
        ValueName   = ""
    }
}
```

> [!NOTE]
> <span data-ttu-id="d6d96-150">Le changement d’un paramètre de Registre dans la ruche `HKEY_CURRENT_USER` nécessite l’exécution de la configuration à l’aide des informations d’identification de l’utilisateur, et non celles du système.</span><span class="sxs-lookup"><span data-stu-id="d6d96-150">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="d6d96-151">Vous pouvez utiliser la propriété **PsDscRunAsCredential** pour spécifier les informations d’identification de l’utilisateur pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="d6d96-151">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="d6d96-152">Pour obtenir un exemple, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](../../../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="d6d96-152">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>
