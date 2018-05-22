---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Script dans DSC
ms.openlocfilehash: 1163d454972d8ee519d1c55b77bb85979faf3536
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-script-resource"></a><span data-ttu-id="6bace-103">Ressource Script dans DSC</span><span class="sxs-lookup"><span data-stu-id="6bace-103">DSC Script Resource</span></span>


> <span data-ttu-id="6bace-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6bace-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6bace-105">La ressource **Script** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour exécuter des blocs de script Windows PowerShell sur des nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="6bace-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="6bace-106">La ressource `Script` comprend les propriétés `GetScript`, `SetScript` et `TestScript`.</span><span class="sxs-lookup"><span data-stu-id="6bace-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="6bace-107">Ces propriétés doivent être définies sur les blocs de script qui sont exécutés sur chaque nœud cible.</span><span class="sxs-lookup"><span data-stu-id="6bace-107">These properties should be set to script blocks that will run on each target node.</span></span>

<span data-ttu-id="6bace-108">Le bloc de script `GetScript` doit retourner une table de hachage qui représente l’état du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="6bace-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="6bace-109">La table de hachage doit contenir une seule clé `Result` et la valeur doit être de type `String`.</span><span class="sxs-lookup"><span data-stu-id="6bace-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="6bace-110">Il n’a pas à retourner d’élément.</span><span class="sxs-lookup"><span data-stu-id="6bace-110">It is not required to return anything.</span></span> <span data-ttu-id="6bace-111">DSC ne fait rien avec la sortie de ce bloc de script.</span><span class="sxs-lookup"><span data-stu-id="6bace-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="6bace-112">Le bloc de script `TestScript` doit déterminer si le nœud actuel doit être modifié.</span><span class="sxs-lookup"><span data-stu-id="6bace-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="6bace-113">Il doit retourner `$true` si le nœud est à jour.</span><span class="sxs-lookup"><span data-stu-id="6bace-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="6bace-114">Il doit retourner `$false` si la configuration du nœud est obsolète et doit être mise à jour par le bloc de script `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="6bace-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="6bace-115">Le bloc de script `TestScript` est appelé par DSC.</span><span class="sxs-lookup"><span data-stu-id="6bace-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="6bace-116">Le bloc de script `SetScript` doit modifier le nœud.</span><span class="sxs-lookup"><span data-stu-id="6bace-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="6bace-117">Il est appelé par DSC si le bloc `TestScript` retourne `$false`.</span><span class="sxs-lookup"><span data-stu-id="6bace-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="6bace-118">Si vous devez utiliser des variables de votre script de configuration dans les blocs de script `GetScript`, `TestScript` ou `SetScript`, utilisez l’étendue `$using:` (voir ci-dessous pour obtenir un exemple).</span><span class="sxs-lookup"><span data-stu-id="6bace-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="6bace-119">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bace-119">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="6bace-120">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6bace-120">Properties</span></span>

|  <span data-ttu-id="6bace-121">Propriété</span><span class="sxs-lookup"><span data-stu-id="6bace-121">Property</span></span>  |  <span data-ttu-id="6bace-122">Description</span><span class="sxs-lookup"><span data-stu-id="6bace-122">Description</span></span>   |
|---|---|
| <span data-ttu-id="6bace-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="6bace-123">GetScript</span></span>| <span data-ttu-id="6bace-124">Fournit un bloc de script Windows PowerShell qui s’exécute quand vous appelez l’applet de commande [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx).</span><span class="sxs-lookup"><span data-stu-id="6bace-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="6bace-125">Ce bloc doit retourner une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="6bace-125">This block must return a hashtable.</span></span> <span data-ttu-id="6bace-126">La table de hachage doit contenir une seule clé **Result** et la valeur doit être de type **String**.</span><span class="sxs-lookup"><span data-stu-id="6bace-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>|
| <span data-ttu-id="6bace-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="6bace-127">SetScript</span></span>| <span data-ttu-id="6bace-128">Fournit un bloc de script Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bace-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="6bace-129">Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx), le bloc **TestScript** s’exécute en premier.</span><span class="sxs-lookup"><span data-stu-id="6bace-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="6bace-130">Si le bloc **TestScript** retourne **$false**, le bloc **SetScript** s’exécute.</span><span class="sxs-lookup"><span data-stu-id="6bace-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="6bace-131">Si le bloc **TestScript** retourne **$true**, le bloc **SetScript** ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="6bace-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>|
| <span data-ttu-id="6bace-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="6bace-132">TestScript</span></span>| <span data-ttu-id="6bace-133">Fournit un bloc de script Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bace-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="6bace-134">Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx), ce bloc s’exécute.</span><span class="sxs-lookup"><span data-stu-id="6bace-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="6bace-135">Si elle retourne **$false**, le bloc SetScript s’exécute.</span><span class="sxs-lookup"><span data-stu-id="6bace-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="6bace-136">Si elle retourne **$true**, le bloc SetScript ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="6bace-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="6bace-137">Le bloc **TestScript** s’exécute également quand vous appelez l’applet de commande [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx).</span><span class="sxs-lookup"><span data-stu-id="6bace-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="6bace-138">Toutefois, dans ce cas, la propriété **SetScript** ne s’exécute pas, quelle que soit la valeur retournée par le bloc TestScript.</span><span class="sxs-lookup"><span data-stu-id="6bace-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="6bace-139">Le bloc **TestScript** doit retourner True si la configuration réelle correspond à la configuration d’état souhaité actuelle, sinon False.</span><span class="sxs-lookup"><span data-stu-id="6bace-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="6bace-140">(La configuration d’état souhaité actuelle est la dernière configuration appliquée sur le nœud qui utilise DSC.)</span><span class="sxs-lookup"><span data-stu-id="6bace-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>|
| <span data-ttu-id="6bace-141">Credential</span><span class="sxs-lookup"><span data-stu-id="6bace-141">Credential</span></span>| <span data-ttu-id="6bace-142">Indique les informations d’identification à utiliser pour exécuter ce script, si elles sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="6bace-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
| <span data-ttu-id="6bace-143">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6bace-143">DependsOn</span></span>| <span data-ttu-id="6bace-144">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="6bace-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6bace-145">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6bace-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="6bace-146">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="6bace-146">Example 1</span></span>
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript =
        {
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
    }
}
```

## <a name="example-2"></a><span data-ttu-id="6bace-147">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="6bace-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = {
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }
        TestScript = {
            $state = $GetScript
            if( $state['Result'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = {
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

<span data-ttu-id="6bace-148">Cette ressource écrit la version de la configuration dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="6bace-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="6bace-149">Cette version étant disponible sur l’ordinateur client, mais pas sur les nœuds, elle doit être transmise à chacun des blocs de script de la ressource `Script` avec l’étendue `using` de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bace-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="6bace-150">Lors de la génération du fichier MOF du nœud, la valeur de la variable `$version` est lue à partir d’un fichier texte sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="6bace-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="6bace-151">DSC remplace les variables `$using:version` dans chaque bloc de script par la valeur de la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="6bace-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>