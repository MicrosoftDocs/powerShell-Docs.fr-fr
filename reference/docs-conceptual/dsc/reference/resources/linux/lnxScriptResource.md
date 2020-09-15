---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: Ressource nxScript dans DSC pour Linux
ms.openlocfilehash: e39808e110d5ee4bf9d0ccd418ca3b15ac9fe420
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463650"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="8228f-103">Ressource nxScript dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="8228f-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="8228f-104">La ressource **nxScript** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant d’exécuter des scripts Linux sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="8228f-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8228f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8228f-105">Syntax</span></span>

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="8228f-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8228f-106">Properties</span></span>

|<span data-ttu-id="8228f-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="8228f-107">Property</span></span> |<span data-ttu-id="8228f-108">Description</span><span class="sxs-lookup"><span data-stu-id="8228f-108">Description</span></span> |
|---|---|
|<span data-ttu-id="8228f-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="8228f-109">GetScript</span></span> |<span data-ttu-id="8228f-110">Fournit un script pour retourner l’état actuel de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8228f-110">Provides a script to return current status of the machine.</span></span> <span data-ttu-id="8228f-111">Ce script s’exécute quand vous appelez le script [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer).</span><span class="sxs-lookup"><span data-stu-id="8228f-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="8228f-112">Le script doit commencer par un shebang, tel que `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="8228f-112">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="8228f-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="8228f-113">SetScript</span></span> |<span data-ttu-id="8228f-114">Fournit un script qui place l’ordinateur dans l’état correct.</span><span class="sxs-lookup"><span data-stu-id="8228f-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="8228f-115">Quand vous appelez le script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), **TestScript** s’exécute en premier.</span><span class="sxs-lookup"><span data-stu-id="8228f-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="8228f-116">Si le bloc **TestScript** retourne un code de sortie différent de 0, le bloc **SetScript** s’exécute.</span><span class="sxs-lookup"><span data-stu-id="8228f-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="8228f-117">Si **TestScript** retourne un code de sortie égal à 0, **SetScript** ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="8228f-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="8228f-118">Le script doit commencer par un shebang, tel que `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="8228f-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="8228f-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="8228f-119">TestScript</span></span> |<span data-ttu-id="8228f-120">Fournit un script qui évalue si le nœud est actuellement dans un état correct.</span><span class="sxs-lookup"><span data-stu-id="8228f-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="8228f-121">Quand vous appelez le script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), ce script s’exécute.</span><span class="sxs-lookup"><span data-stu-id="8228f-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="8228f-122">Si la propriété retourne un code de sortie différent de 0, **SetScript** s’exécute.</span><span class="sxs-lookup"><span data-stu-id="8228f-122">If it returns an exit code other than 0, the **SetScript** will run.</span></span> <span data-ttu-id="8228f-123">Si la propriété retourne un code de sortie égal à 0, **SetScript** ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="8228f-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="8228f-124">**TestScript** s’exécute également quand vous appelez le script [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer).</span><span class="sxs-lookup"><span data-stu-id="8228f-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="8228f-125">Toutefois, dans ce cas, la propriété **SetScript** ne s’exécute pas, quel que soit le code de sortie retourné par **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="8228f-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="8228f-126">**TestScript** doit contenir du contenu et retourner le code de sortie 0 si la configuration réelle correspond à la configuration actuelle de l’état souhaité. Sinon, elle doit retourner un code de sortie différent de 0.</span><span class="sxs-lookup"><span data-stu-id="8228f-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="8228f-127">La configuration d’état souhaité actuelle est la dernière configuration appliquée sur le nœud qui utilise DSC.</span><span class="sxs-lookup"><span data-stu-id="8228f-127">The current desired state configuration is the last configuration enacted on the node that is using DSC.</span></span> <span data-ttu-id="8228f-128">Le script doit commencer par un shebang, tel que `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="8228f-128">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="8228f-129">Utilisateur</span><span class="sxs-lookup"><span data-stu-id="8228f-129">User</span></span> |<span data-ttu-id="8228f-130">Nom d’utilisateur utilisé pour exécuter le script.</span><span class="sxs-lookup"><span data-stu-id="8228f-130">The user to run the script as.</span></span> |
|<span data-ttu-id="8228f-131">Groupe</span><span class="sxs-lookup"><span data-stu-id="8228f-131">Group</span></span> |<span data-ttu-id="8228f-132">Nom de groupe utilisé pour exécuter le script.</span><span class="sxs-lookup"><span data-stu-id="8228f-132">The group to run the script as.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="8228f-133">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="8228f-133">Common properties</span></span>

|<span data-ttu-id="8228f-134">Propriété</span><span class="sxs-lookup"><span data-stu-id="8228f-134">Property</span></span> |<span data-ttu-id="8228f-135">Description</span><span class="sxs-lookup"><span data-stu-id="8228f-135">Description</span></span> |
|---|---|
|<span data-ttu-id="8228f-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8228f-136">DependsOn</span></span> |<span data-ttu-id="8228f-137">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="8228f-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8228f-138">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8228f-138">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="8228f-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="8228f-139">Example</span></span>

<span data-ttu-id="8228f-140">L’exemple suivant utilise la ressource **nxScript** pour gérer une configuration supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="8228f-140">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
    }
}
```
