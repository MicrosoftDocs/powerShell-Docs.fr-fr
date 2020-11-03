---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: d73d8d6a30e6b7c08b5a0b7988ea2327be34002a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203942"
---
# <span data-ttu-id="4cad5-103">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="4cad5-103">Invoke-DscResource</span></span>

## <span data-ttu-id="4cad5-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4cad5-104">SYNOPSIS</span></span>
<span data-ttu-id="4cad5-105">Exécute une méthode d’une ressource DSC spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4cad5-105">Runs a method of a specified DSC resource.</span></span>

## <span data-ttu-id="4cad5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4cad5-106">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [-Method] <String> -ModuleName <ModuleSpecification> -Property <Hashtable>
 [<CommonParameters>]
```

## <span data-ttu-id="4cad5-107">Description</span><span class="sxs-lookup"><span data-stu-id="4cad5-107">DESCRIPTION</span></span>
<span data-ttu-id="4cad5-108">L’applet de commande **Invoke-DscResource** exécute une méthode d’une ressource DSC (Desired State Configuration) Windows PowerShell spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4cad5-108">The **Invoke-DscResource** cmdlet runs a method of a specified Windows PowerShell Desired State Configuration (DSC) resource.</span></span>
<span data-ttu-id="4cad5-109">Avant d’exécuter cette applet de commande, définissez le mode d’actualisation du Configuration Manager local (LCM) sur désactivé.</span><span class="sxs-lookup"><span data-stu-id="4cad5-109">Before you run this cmdlet, set the refresh mode of the Local Configuration Manager (LCM) to Disabled.</span></span>

<span data-ttu-id="4cad5-110">Cette cmdlet appelle directement une ressource DSC sans créer de document de configuration.</span><span class="sxs-lookup"><span data-stu-id="4cad5-110">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span>
<span data-ttu-id="4cad5-111">À l’aide de cette applet de commande, les produits de gestion de la configuration peuvent gérer Windows à l’aide des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="4cad5-111">Using this cmdlet, configuration management products can manage windows by using DSC resources.</span></span>
<span data-ttu-id="4cad5-112">Cette applet de commande permet également de déboguer des ressources lorsque le moteur DSC ou le LCM s’exécute avec le débogage activé.</span><span class="sxs-lookup"><span data-stu-id="4cad5-112">This cmdlet also enables debugging of resources when the DSC engine or LCM is running with debugging enabled.</span></span>

## <span data-ttu-id="4cad5-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4cad5-113">EXAMPLES</span></span>

### <span data-ttu-id="4cad5-114">Exemple 1 : appeler la méthode Set d’une ressource en spécifiant ses propriétés obligatoires</span><span class="sxs-lookup"><span data-stu-id="4cad5-114">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

```
PS C:\> Invoke-DscResource -Name Log -Method Set -Property @{Message = 'Hello World'} -ModuleName PSDesiredStateConfiguration
```

<span data-ttu-id="4cad5-115">Cette commande appelle la méthode **Set** d’une ressource nommée log et spécifie une propriété de **message** pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="4cad5-115">This command invokes the **Set** method of a resource named Log and specifies a **Message** property for it.</span></span>

### <span data-ttu-id="4cad5-116">Exemple 2 : appeler la méthode de test d’une ressource pour un module spécifié</span><span class="sxs-lookup"><span data-stu-id="4cad5-116">Example 2: Invoke the Test method of a resource for a specified module</span></span>

```
PS C:\> Invoke-DscResource -Name WindowsProcess -Method Test -Property @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''} -ModuleName PSDesiredStateConfiguration
```

<span data-ttu-id="4cad5-117">Cette commande appelle la méthode de **test** d’une ressource nommée WindowsProcess, qui se trouve dans le module nommé PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="4cad5-117">This command invokes the **Test** method of a resource named WindowsProcess, which is in the module named PSDesiredStateConfiguration.</span></span>

## <span data-ttu-id="4cad5-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4cad5-118">PARAMETERS</span></span>

### <span data-ttu-id="4cad5-119">-Méthode</span><span class="sxs-lookup"><span data-stu-id="4cad5-119">-Method</span></span>
<span data-ttu-id="4cad5-120">Spécifie la méthode de la ressource appelée par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4cad5-120">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="4cad5-121">Les valeurs acceptables pour ce paramètre sont les suivantes : obtenir, définir et tester.</span><span class="sxs-lookup"><span data-stu-id="4cad5-121">The acceptable values for this parameter are: Get, Set, and Test.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4cad5-122">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="4cad5-122">-ModuleName</span></span>
<span data-ttu-id="4cad5-123">Spécifie le nom du module à partir duquel cette applet de commande appelle la ressource spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4cad5-123">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4cad5-124">-Name</span><span class="sxs-lookup"><span data-stu-id="4cad5-124">-Name</span></span>
<span data-ttu-id="4cad5-125">Spécifie le nom de la ressource DSC à démarrer.</span><span class="sxs-lookup"><span data-stu-id="4cad5-125">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4cad5-126">-Propriété</span><span class="sxs-lookup"><span data-stu-id="4cad5-126">-Property</span></span>
<span data-ttu-id="4cad5-127">Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="4cad5-127">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="4cad5-128">Utilisez l’applet de commande **Get-DscResource** pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="4cad5-128">Use the **Get-DscResource** cmdlet to discover resource properties and their types.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4cad5-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4cad5-129">CommonParameters</span></span>
<span data-ttu-id="4cad5-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4cad5-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4cad5-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4cad5-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4cad5-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4cad5-132">INPUTS</span></span>

## <span data-ttu-id="4cad5-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4cad5-133">OUTPUTS</span></span>

### <span data-ttu-id="4cad5-134">Microsoft. Management. infrastructure. CimInstance, System. Boolean</span><span class="sxs-lookup"><span data-stu-id="4cad5-134">Microsoft.Management.Infrastructure.CimInstance, System.Boolean</span></span>

## <span data-ttu-id="4cad5-135">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4cad5-135">NOTES</span></span>

## <span data-ttu-id="4cad5-136">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4cad5-136">RELATED LINKS</span></span>

[<span data-ttu-id="4cad5-137">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4cad5-137">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="4cad5-138">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4cad5-138">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="4cad5-139">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="4cad5-139">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="4cad5-140">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="4cad5-140">Get-DscResource</span></span>](Get-DscResource.md)

[<span data-ttu-id="4cad5-141">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4cad5-141">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="4cad5-142">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4cad5-142">Set-DscLocalConfigurationManager</span></span>](Set-DscLocalConfigurationManager.md)

[<span data-ttu-id="4cad5-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4cad5-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="4cad5-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4cad5-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
