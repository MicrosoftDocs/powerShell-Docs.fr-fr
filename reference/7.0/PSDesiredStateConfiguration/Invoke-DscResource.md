---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 4703586008d9044ae68fd7375db65f0d0a9b9980
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "93206050"
---
# <span data-ttu-id="1bb8d-103">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="1bb8d-103">Invoke-DscResource</span></span>

## <span data-ttu-id="1bb8d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1bb8d-104">SYNOPSIS</span></span>
<span data-ttu-id="1bb8d-105">Exécute une méthode d’une ressource DSC (Desired State Configuration) PowerShell spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-105">Runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

## <span data-ttu-id="1bb8d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1bb8d-106">SYNTAX</span></span>

```
Invoke-DscResource [[-Method] <Object>] [[-Name] <Object>] [[-Property] <Object>]
 [[-ModuleName] <Object>] [-AsJob] [<CommonParameters>]
```

## <span data-ttu-id="1bb8d-107">Description</span><span class="sxs-lookup"><span data-stu-id="1bb8d-107">DESCRIPTION</span></span>

<span data-ttu-id="1bb8d-108">La cmdlet `Invoke-DscResource` exécute une méthode d’une ressource Desired State Configuration (DSC) PowerShell spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-108">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="1bb8d-109">Cette cmdlet appelle directement une ressource DSC sans créer de document de configuration.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-109">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="1bb8d-110">À l’aide de cette applet de commande, les produits de gestion de la configuration peuvent gérer Windows ou Linux à l’aide de ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-110">Using this cmdlet, configuration management products can manage windows or Linux by using DSC resources.</span></span> <span data-ttu-id="1bb8d-111">Cette cmdlet de commande permet également de déboguer des ressources lorsque le moteur DSC s’exécute avec le débogage activé.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-111">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="1bb8d-112">`Invoke-DscResource` est une fonctionnalité expérimentale de PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-112">`Invoke-DscResource` is an experimental feature in PowerShell 7.</span></span> <span data-ttu-id="1bb8d-113">Pour utiliser l’applet de commande, vous devez l’activer à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-113">To use the cmdlet, you must enable it using the following command.</span></span>
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## <span data-ttu-id="1bb8d-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1bb8d-114">EXAMPLES</span></span>

### <span data-ttu-id="1bb8d-115">Exemple 1 : appeler la méthode Set d’une ressource en spécifiant ses propriétés obligatoires</span><span class="sxs-lookup"><span data-stu-id="1bb8d-115">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

<span data-ttu-id="1bb8d-116">Cet exemple appelle la méthode **Set** d’une ressource nommée **WindowsProcess** et fournit les propriétés **path** et **arguments** obligatoires pour démarrer le processus Windows spécifié.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-116">This example invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### <span data-ttu-id="1bb8d-117">Exemple 2 : appeler la méthode de test d’une ressource pour un module spécifié</span><span class="sxs-lookup"><span data-stu-id="1bb8d-117">Example 2: Invoke the Test method of a resource for a specified module</span></span>

<span data-ttu-id="1bb8d-118">Cet exemple appelle la méthode de **test** d’une ressource nommée **WindowsProcess** , qui se trouve dans le module nommé **PSDesiredStateConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="1bb8d-118">This example invokes the **Test** method of a resource named **WindowsProcess** , which is in the module named **PSDesiredStateConfiguration** .</span></span>

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## <span data-ttu-id="1bb8d-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1bb8d-119">PARAMETERS</span></span>

### <span data-ttu-id="1bb8d-120">-Méthode</span><span class="sxs-lookup"><span data-stu-id="1bb8d-120">-Method</span></span>

<span data-ttu-id="1bb8d-121">Spécifie la méthode de la ressource appelée par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-121">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="1bb8d-122">Les valeurs acceptables pour ce paramètre sont les suivantes : **obtenir** , **définir** et **Tester** .</span><span class="sxs-lookup"><span data-stu-id="1bb8d-122">The acceptable values for this parameter are: **Get** , **Set** , and **Test** .</span></span>

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1bb8d-123">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="1bb8d-123">-ModuleName</span></span>

<span data-ttu-id="1bb8d-124">Spécifie le nom du module à partir duquel cette applet de commande appelle la ressource spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-124">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1bb8d-125">-Name</span><span class="sxs-lookup"><span data-stu-id="1bb8d-125">-Name</span></span>

<span data-ttu-id="1bb8d-126">Spécifie le nom de la ressource DSC à démarrer.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-126">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1bb8d-127">-Propriété</span><span class="sxs-lookup"><span data-stu-id="1bb8d-127">-Property</span></span>

<span data-ttu-id="1bb8d-128">Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-128">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span>

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1bb8d-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1bb8d-129">CommonParameters</span></span>

<span data-ttu-id="1bb8d-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1bb8d-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1bb8d-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1bb8d-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1bb8d-132">INPUTS</span></span>

## <span data-ttu-id="1bb8d-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1bb8d-133">OUTPUTS</span></span>

### <span data-ttu-id="1bb8d-134">Microsoft. Management. infrastructure. CimInstance, System. Boolean</span><span class="sxs-lookup"><span data-stu-id="1bb8d-134">Microsoft.Management.Infrastructure.CimInstance, System.Boolean</span></span>

## <span data-ttu-id="1bb8d-135">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1bb8d-135">NOTES</span></span>

- <span data-ttu-id="1bb8d-136">Auparavant, les ressources Windows PowerShell 5,1 étaient exécutées sous le contexte système, sauf si elles étaient spécifiées avec le contexte utilisateur à l’aide de la clé **PsDscRunAsCredential** .</span><span class="sxs-lookup"><span data-stu-id="1bb8d-136">Previously, Windows PowerShell 5.1 resources ran under System context unless specified with user context using the key **PsDscRunAsCredential** .</span></span> <span data-ttu-id="1bb8d-137">Dans PowerShell 7,0, les ressources s’exécutent dans le contexte de l’utilisateur, et **PsDscRunAsCredential** n’est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-137">In PowerShell 7.0, Resources run in the user's context, and **PsDscRunAsCredential** is no longer supported.</span></span> <span data-ttu-id="1bb8d-138">Les configurations précédentes qui utilisent cette clé lèveront une exception.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-138">Previous configurations using this key will throw an exception.</span></span>

- <span data-ttu-id="1bb8d-139">Depuis PowerShell 7, `Invoke-DscResource` ne prend plus en charge l’appel des ressources DSC WMI.</span><span class="sxs-lookup"><span data-stu-id="1bb8d-139">As of PowerShell 7, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="1bb8d-140">Sont incluses les ressources **File** et **Log** dans **PSDesiredStateConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="1bb8d-140">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration** .</span></span>

## <span data-ttu-id="1bb8d-141">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1bb8d-141">RELATED LINKS</span></span>

[<span data-ttu-id="1bb8d-142">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bb8d-142">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="1bb8d-143">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="1bb8d-143">Get-DscResource</span></span>](Get-DscResource.md)
