---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Utilisation de ressources avec plusieurs versions
ms.openlocfilehash: 6400d6506106657ba28fa1f9c83d9f8ee1c93ba3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187008"
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="fd448-103">Utilisation de ressources avec plusieurs versions</span><span class="sxs-lookup"><span data-stu-id="fd448-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="fd448-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fd448-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="fd448-105">Dans PowerShell 5.0, les ressources DSC peuvent avoir plusieurs versions et celles-ci peuvent être installées sur un ordinateur côte à côte.</span><span class="sxs-lookup"><span data-stu-id="fd448-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="fd448-106">L’implémentation inclut plusieurs versions d’un module de ressource qui sont contenues dans le même dossier de module.</span><span class="sxs-lookup"><span data-stu-id="fd448-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="fd448-107">Installation de plusieurs versions de ressources côte à côte</span><span class="sxs-lookup"><span data-stu-id="fd448-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="fd448-108">Vous pouvez utiliser les paramètres **MinimumVersion**, **MaximumVersion** et **RequiredVersion** de l’applet de commande [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) pour indiquer la version d’un module à installer.</span><span class="sxs-lookup"><span data-stu-id="fd448-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="fd448-109">L’appel de l’applet de commande **Install-Module** sans spécifier de version installe la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="fd448-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="fd448-110">Par exemple, il existe plusieurs versions du module **xFailOverCluster**, chacun contenant une ressource **xCluster**.</span><span class="sxs-lookup"><span data-stu-id="fd448-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="fd448-111">Le résultat de l’appel de l’applet de commande **Install-Module** sans spécifier de numéro de version est le suivant :</span><span class="sxs-lookup"><span data-stu-id="fd448-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="fd448-112">Maintenant, si vous rappelez **Install-Module**, mais indiquez la valeur 1.1.0.0 pour le paramètre **RequiredVersion**, le résultat est le suivant :</span><span class="sxs-lookup"><span data-stu-id="fd448-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="fd448-113">Spécification d’une version de ressource dans une configuration</span><span class="sxs-lookup"><span data-stu-id="fd448-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="fd448-114">Si plusieurs ressources sont installées sur un ordinateur, vous devez spécifier la version d’une ressource quand vous l’utilisez dans une configuration.</span><span class="sxs-lookup"><span data-stu-id="fd448-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="fd448-115">Pour cela, vous devez spécifier le paramètre **ModuleVersion** du mot-clé **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="fd448-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="fd448-116">Si vous ne parvenez pas à spécifier la version d’un module d’une ressource dont plusieurs versions sont installées, la configuration génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="fd448-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="fd448-117">La configuration suivante montre comment spécifier la version de la ressource à appeler :</span><span class="sxs-lookup"><span data-stu-id="fd448-117">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="fd448-118">Remarque : Le paramètre ModuleVersion d’Import-DscResource n’est pas disponible dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="fd448-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="fd448-119">Dans PowerShell 4.0, vous pouvez spécifier une version du module en passant un objet de spécification de module au paramètre ModuleName d’Import-DscResource.</span><span class="sxs-lookup"><span data-stu-id="fd448-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="fd448-120">Un objet de spécification de module est une table de hachage qui contient les clés ModuleName et RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="fd448-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="fd448-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="fd448-121">For example:</span></span>

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

<span data-ttu-id="fd448-122">Cela fonctionne également dans PowerShell 5.0, mais il est recommandé d’utiliser le paramètre **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="fd448-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd448-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd448-123">See also</span></span>
* [<span data-ttu-id="fd448-124">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="fd448-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="fd448-125">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="fd448-125">DSC Resources</span></span>](resources.md)