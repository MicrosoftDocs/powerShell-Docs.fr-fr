---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxScript dans DSC pour Linux
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189327"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="8a724-103">Ressource nxScript dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="8a724-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="8a724-104">La ressource **nxScript** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant d’exécuter des scripts Linux sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="8a724-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a724-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a724-105">Syntax</span></span>

```
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

## <a name="properties"></a><span data-ttu-id="8a724-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8a724-106">Properties</span></span>

|  <span data-ttu-id="8a724-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="8a724-107">Property</span></span> |  <span data-ttu-id="8a724-108">Description</span><span class="sxs-lookup"><span data-stu-id="8a724-108">Description</span></span> |
|---|---|
| <span data-ttu-id="8a724-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="8a724-109">GetScript</span></span>| <span data-ttu-id="8a724-110">Fournit un script qui s’exécute quand vous appelez l’applet de commande [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a724-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="8a724-111">Le script doit commencer par un shebang, tel que #!/bin/bash.</span><span class="sxs-lookup"><span data-stu-id="8a724-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="8a724-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="8a724-112">SetScript</span></span>| <span data-ttu-id="8a724-113">Fournit un script.</span><span class="sxs-lookup"><span data-stu-id="8a724-113">Provides a script.</span></span> <span data-ttu-id="8a724-114">Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), **TestScript** s’exécute en premier.</span><span class="sxs-lookup"><span data-stu-id="8a724-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="8a724-115">Si le bloc **TestScript** retourne un code de sortie différent de 0, le bloc **SetScript** s’exécute.</span><span class="sxs-lookup"><span data-stu-id="8a724-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="8a724-116">Si **TestScript** retourne un code de sortie égal à 0, **SetScript** ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="8a724-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="8a724-117">Le script doit commencer par un shebang, tel que `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="8a724-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="8a724-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="8a724-118">TestScript</span></span>| <span data-ttu-id="8a724-119">Fournit un script.</span><span class="sxs-lookup"><span data-stu-id="8a724-119">Provides a script.</span></span> <span data-ttu-id="8a724-120">Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), ce script s’exécute.</span><span class="sxs-lookup"><span data-stu-id="8a724-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="8a724-121">Si la propriété retourne un code de sortie différent de 0, SetScript s’exécute.</span><span class="sxs-lookup"><span data-stu-id="8a724-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="8a724-122">Si la propriété retourne un code de sortie égal à 0, **SetScript** ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="8a724-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="8a724-123">**TestScript** s’exécute également quand vous appelez l’applet de commande [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx).</span><span class="sxs-lookup"><span data-stu-id="8a724-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="8a724-124">Toutefois, dans ce cas, la propriété **SetScript** ne s’exécute pas, quel que soit le code de sortie retourné par **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="8a724-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="8a724-125">**TestScript** doit retourner le code de sortie 0 si la configuration réelle correspond à la configuration actuelle de l’état souhaité. Sinon, elle doit retourner un code de sortie différent de 0.</span><span class="sxs-lookup"><span data-stu-id="8a724-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="8a724-126">(La configuration actuelle de l’état souhaité est la dernière configuration appliquée sur le nœud qui utilise DSC.)</span><span class="sxs-lookup"><span data-stu-id="8a724-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="8a724-127">Le script doit commencer par un shebang, tel que 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="8a724-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="8a724-128">User</span><span class="sxs-lookup"><span data-stu-id="8a724-128">User</span></span>| <span data-ttu-id="8a724-129">Nom d’utilisateur utilisé pour exécuter le script.</span><span class="sxs-lookup"><span data-stu-id="8a724-129">The user to run the script as.</span></span>|
| <span data-ttu-id="8a724-130">Group</span><span class="sxs-lookup"><span data-stu-id="8a724-130">Group</span></span>| <span data-ttu-id="8a724-131">Nom de groupe utilisé pour exécuter le script.</span><span class="sxs-lookup"><span data-stu-id="8a724-131">The group to run the script as.</span></span>|
| <span data-ttu-id="8a724-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8a724-132">DependsOn</span></span> | <span data-ttu-id="8a724-133">Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="8a724-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8a724-134">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8a724-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="8a724-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a724-135">Example</span></span>

<span data-ttu-id="8a724-136">L’exemple suivant utilise la ressource **nxScript** pour gérer une configuration supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="8a724-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

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