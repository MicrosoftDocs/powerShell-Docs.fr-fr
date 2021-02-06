---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 732db5a049a68e059db6062d2f6c3f850d579adc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597764"
---
# <span data-ttu-id="d45ff-102">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="d45ff-102">Invoke-DscResource</span></span>

## <span data-ttu-id="d45ff-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d45ff-103">SYNOPSIS</span></span>
<span data-ttu-id="d45ff-104">Exécute une méthode d’une ressource DSC (Desired State Configuration) PowerShell spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d45ff-104">Runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

## <span data-ttu-id="d45ff-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d45ff-105">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [[-ModuleName] <ModuleSpecification>] [-Method] <String>
 [-Property] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="d45ff-106">Description</span><span class="sxs-lookup"><span data-stu-id="d45ff-106">DESCRIPTION</span></span>

<span data-ttu-id="d45ff-107">La cmdlet `Invoke-DscResource` exécute une méthode d’une ressource Desired State Configuration (DSC) PowerShell spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d45ff-107">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="d45ff-108">Cette cmdlet appelle directement une ressource DSC sans créer de document de configuration.</span><span class="sxs-lookup"><span data-stu-id="d45ff-108">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="d45ff-109">À l’aide de cette applet de commande, les produits de gestion de la configuration peuvent gérer Windows ou Linux à l’aide de ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="d45ff-109">Using this cmdlet, configuration management products can manage windows or Linux by using DSC resources.</span></span> <span data-ttu-id="d45ff-110">Cette cmdlet de commande permet également de déboguer des ressources lorsque le moteur DSC s’exécute avec le débogage activé.</span><span class="sxs-lookup"><span data-stu-id="d45ff-110">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="d45ff-111">`Invoke-DscResource` est une fonctionnalité expérimentale de PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="d45ff-111">`Invoke-DscResource` is an experimental feature in PowerShell 7.</span></span> <span data-ttu-id="d45ff-112">Pour utiliser l’applet de commande, vous devez l’activer à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="d45ff-112">To use the cmdlet, you must enable it using the following command.</span></span>
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## <span data-ttu-id="d45ff-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d45ff-113">EXAMPLES</span></span>

### <span data-ttu-id="d45ff-114">Exemple 1 : appeler la méthode Set d’une ressource en spécifiant ses propriétés obligatoires</span><span class="sxs-lookup"><span data-stu-id="d45ff-114">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

<span data-ttu-id="d45ff-115">Cet exemple appelle la méthode **Set** d’une ressource nommée **WindowsProcess** et fournit les propriétés **path** et **arguments** obligatoires pour démarrer le processus Windows spécifié.</span><span class="sxs-lookup"><span data-stu-id="d45ff-115">This example invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### <span data-ttu-id="d45ff-116">Exemple 2 : appeler la méthode de test d’une ressource pour un module spécifié</span><span class="sxs-lookup"><span data-stu-id="d45ff-116">Example 2: Invoke the Test method of a resource for a specified module</span></span>

<span data-ttu-id="d45ff-117">Cet exemple appelle la méthode de **test** d’une ressource nommée **WindowsProcess**, qui se trouve dans le module nommé **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="d45ff-117">This example invokes the **Test** method of a resource named **WindowsProcess**, which is in the module named **PSDesiredStateConfiguration**.</span></span>

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## <span data-ttu-id="d45ff-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d45ff-118">PARAMETERS</span></span>

### <span data-ttu-id="d45ff-119">-Méthode</span><span class="sxs-lookup"><span data-stu-id="d45ff-119">-Method</span></span>

<span data-ttu-id="d45ff-120">Spécifie la méthode de la ressource appelée par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d45ff-120">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="d45ff-121">Les valeurs acceptables pour ce paramètre sont les suivantes : **obtenir**, **définir** et **Tester**.</span><span class="sxs-lookup"><span data-stu-id="d45ff-121">The acceptable values for this parameter are: **Get**, **Set**, and **Test**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d45ff-122">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="d45ff-122">-ModuleName</span></span>

<span data-ttu-id="d45ff-123">Spécifie le nom du module à partir duquel cette applet de commande appelle la ressource spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d45ff-123">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d45ff-124">-Name</span><span class="sxs-lookup"><span data-stu-id="d45ff-124">-Name</span></span>

<span data-ttu-id="d45ff-125">Spécifie le nom de la ressource DSC à démarrer.</span><span class="sxs-lookup"><span data-stu-id="d45ff-125">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d45ff-126">-Propriété</span><span class="sxs-lookup"><span data-stu-id="d45ff-126">-Property</span></span>

<span data-ttu-id="d45ff-127">Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="d45ff-127">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d45ff-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d45ff-128">CommonParameters</span></span>

<span data-ttu-id="d45ff-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d45ff-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d45ff-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d45ff-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d45ff-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d45ff-131">INPUTS</span></span>

### <span data-ttu-id="d45ff-132">System.String</span><span class="sxs-lookup"><span data-stu-id="d45ff-132">System.String</span></span>

### <span data-ttu-id="d45ff-133">Microsoft. PowerShell. Commands. ModuleSpecification</span><span class="sxs-lookup"><span data-stu-id="d45ff-133">Microsoft.PowerShell.Commands.ModuleSpecification</span></span>

## <span data-ttu-id="d45ff-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d45ff-134">OUTPUTS</span></span>

### <span data-ttu-id="d45ff-135">System.Object</span><span class="sxs-lookup"><span data-stu-id="d45ff-135">System.Object</span></span>

## <span data-ttu-id="d45ff-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d45ff-136">NOTES</span></span>

- <span data-ttu-id="d45ff-137">Auparavant, les ressources Windows PowerShell 5,1 étaient exécutées sous le contexte système, sauf si elles étaient spécifiées avec le contexte utilisateur à l’aide de la clé **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="d45ff-137">Previously, Windows PowerShell 5.1 resources ran under System context unless specified with user context using the key **PsDscRunAsCredential**.</span></span> <span data-ttu-id="d45ff-138">Dans PowerShell 7,0, les ressources s’exécutent dans le contexte de l’utilisateur, et **PsDscRunAsCredential** n’est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d45ff-138">In PowerShell 7.0, Resources run in the user's context, and **PsDscRunAsCredential** is no longer supported.</span></span> <span data-ttu-id="d45ff-139">Les configurations précédentes qui utilisent cette clé lèveront une exception.</span><span class="sxs-lookup"><span data-stu-id="d45ff-139">Previous configurations using this key will throw an exception.</span></span>

- <span data-ttu-id="d45ff-140">Depuis PowerShell 7, `Invoke-DscResource` ne prend plus en charge l’appel des ressources DSC WMI.</span><span class="sxs-lookup"><span data-stu-id="d45ff-140">As of PowerShell 7, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="d45ff-141">Sont incluses les ressources **File** et **Log** dans **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="d45ff-141">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

## <span data-ttu-id="d45ff-142">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d45ff-142">RELATED LINKS</span></span>

[<span data-ttu-id="d45ff-143">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d45ff-143">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="d45ff-144">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="d45ff-144">Get-DscResource</span></span>](Get-DscResource.md)
