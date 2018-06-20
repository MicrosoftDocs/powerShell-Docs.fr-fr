---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 3f73b7cf0cdf033cbd561b3412734692bb7decd7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187531"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="e81a2-102">Autorisation des ressources en double identiques dans une configuration</span><span class="sxs-lookup"><span data-stu-id="e81a2-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="e81a2-103">DSC n’autorise pas et ne gère pas les définitions de ressources conflictuelles dans une configuration.</span><span class="sxs-lookup"><span data-stu-id="e81a2-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="e81a2-104">Au lieu d’essayer de résoudre le conflit, il échoue tout simplement.</span><span class="sxs-lookup"><span data-stu-id="e81a2-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="e81a2-105">Avec l’augmentation de la réutilisation des configurations due, entre autres, aux ressources composites, des conflits se produiront plus souvent.</span><span class="sxs-lookup"><span data-stu-id="e81a2-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="e81a2-106">Quand des définitions de ressources conflictuelles sont identiques, DSC doit agir intelligemment et les autoriser.</span><span class="sxs-lookup"><span data-stu-id="e81a2-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="e81a2-107">Dans cette version, l’existence de plusieurs instances de ressources ayant des définitions identiques est prise en charge :</span><span class="sxs-lookup"><span data-stu-id="e81a2-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="e81a2-108">Dans les versions précédentes, le résultat était un échec de compilation dû à un conflit, car les instances de WindowsFeature FE_IIS et WindowsFeature Worker_IIS essayaient de garantir l’installation du rôle « Serveur Web ».</span><span class="sxs-lookup"><span data-stu-id="e81a2-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="e81a2-109">Notez que *toutes* les propriétés configurées sont identiques dans ces deux configurations.</span><span class="sxs-lookup"><span data-stu-id="e81a2-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="e81a2-110">Étant donné que *toutes* les propriétés de ces deux ressources sont identiques, désormais la compilation réussit.</span><span class="sxs-lookup"><span data-stu-id="e81a2-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="e81a2-111">Si certaines propriétés des deux ressources sont différentes, elles ne sont pas considérées comme identiques et la compilation échoue :</span><span class="sxs-lookup"><span data-stu-id="e81a2-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="e81a2-112">Cette configuration très semblable échoue, car les ressources WindowsFeature FE_IIS et WindowsFeature Worker_IIS ne sont plus identiques et sont donc en conflit.</span><span class="sxs-lookup"><span data-stu-id="e81a2-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>
