---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Importer une version spécifique d’une ressource installée
description: Cet article explique comment installer et importer des versions spécifiques des modules de ressources dans vos configurations.
ms.openlocfilehash: bb7b3273a5a3fed94fecd90dd3ea1e623fbc332b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645047"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="a822d-104">Importer une version spécifique d’une ressource installée</span><span class="sxs-lookup"><span data-stu-id="a822d-104">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="a822d-105">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a822d-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a822d-106">Dans PowerShell 5.0, des versions distinctes des ressources DSC peuvent être installées sur un ordinateur côte à côte.</span><span class="sxs-lookup"><span data-stu-id="a822d-106">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="a822d-107">Un module de ressources peut stocker des versions distinctes d’une ressource dans des dossiers nommés selon la version.</span><span class="sxs-lookup"><span data-stu-id="a822d-107">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="a822d-108">Installation de versions de ressources distinctes côte à côte</span><span class="sxs-lookup"><span data-stu-id="a822d-108">Installing separate resource versions side by side</span></span>

<span data-ttu-id="a822d-109">Vous pouvez utiliser les paramètres **MinimumVersion** , **MaximumVersion** et **RequiredVersion** de l’applet de commande [Install-Module](/powershell/module/PowershellGet/Install-Module) pour indiquer la version d’un module à installer.</span><span class="sxs-lookup"><span data-stu-id="a822d-109">You can use the **MinimumVersion** , **MaximumVersion** , and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="a822d-110">L’appel de l’applet de commande **Install-Module** sans spécifier de version installe la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="a822d-110">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="a822d-111">Par exemple, il existe plusieurs versions du module **xFailOverCluster** , chacun contenant une ressource **xCluster**.</span><span class="sxs-lookup"><span data-stu-id="a822d-111">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="a822d-112">L’appel de l’applet de commande **Install-Module** sans spécifier de numéro de version installe la version la plus récente du module.</span><span class="sxs-lookup"><span data-stu-id="a822d-112">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName           Version    Properties
-------------   ----          ----------           -------    ----------
PowerShell      xCluster      xFailOverCluster     1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="a822d-113">Pour installer une version spécifique d’un module, vous devez spécifier une version 1.1.0.0 de **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="a822d-113">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="a822d-114">Cette opération installe la version spécifiée côte à côte avec la version installée.</span><span class="sxs-lookup"><span data-stu-id="a822d-114">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="a822d-115">Vous voyez à présent les deux versions du module lorsque vous utilisez `Get-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="a822d-115">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName            Version    Properties
-------------   ----          ----------            -------    ----------
PowerShell      xCluster      xFailOverCluster      1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster      xFailOverCluster      1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="a822d-116">Spécification d’une version de ressource dans une configuration</span><span class="sxs-lookup"><span data-stu-id="a822d-116">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="a822d-117">Si des versions de ressources distinctes sont installées sur un ordinateur, vous devez spécifier la version d’une ressource quand vous l’utilisez dans une configuration.</span><span class="sxs-lookup"><span data-stu-id="a822d-117">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="a822d-118">Pour cela, vous devez spécifier le paramètre **ModuleVersion** du mot-clé **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="a822d-118">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="a822d-119">Si vous ne parvenez pas à spécifier la version d’un module d’une ressource dont plusieurs versions sont installées, la configuration génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="a822d-119">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="a822d-120">La configuration suivante montre comment spécifier la version de la ressource à appeler :</span><span class="sxs-lookup"><span data-stu-id="a822d-120">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="a822d-121">le paramètre ModuleVersion d’Import-DscResource n’est pas disponible dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="a822d-121">The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="a822d-122">Dans PowerShell 4.0, vous pouvez spécifier une version du module en passant un objet de spécification de module au paramètre ModuleName d’Import-DscResource.</span><span class="sxs-lookup"><span data-stu-id="a822d-122">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="a822d-123">Un objet de spécification de module est une table de hachage qui contient les clés ModuleName et RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="a822d-123">A module specification object is a hash table that contains ModuleName and RequiredVersion keys.</span></span> <span data-ttu-id="a822d-124">Exemple :</span><span class="sxs-lookup"><span data-stu-id="a822d-124">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="a822d-125">Cela fonctionne également dans PowerShell 5.0, mais il est recommandé d’utiliser le paramètre **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="a822d-125">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="a822d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a822d-126">See also</span></span>

- [<span data-ttu-id="a822d-127">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="a822d-127">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="a822d-128">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="a822d-128">DSC Resources</span></span>](../resources/resources.md)
