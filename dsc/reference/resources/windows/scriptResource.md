---
ms.date: 08/24/2018
keywords: dsc,powershell,configuration,setup
title: Ressource Script dans DSC
ms.openlocfilehash: 86dfb74bf52d8907686bb955fd722f4fb8b9131b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054745"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="0b78c-103">Ressource Script dans DSC</span><span class="sxs-lookup"><span data-stu-id="0b78c-103">DSC Script Resource</span></span>

> <span data-ttu-id="0b78c-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="0b78c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="0b78c-105">La ressource **Script** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour exécuter des blocs de script Windows PowerShell sur des nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="0b78c-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="0b78c-106">La ressource **Script** utilise les propriétés `GetScript`, `SetScript` et `TestScript` qui contiennent des blocs de script que vous définissez pour effectuer les opérations d’état DSC correspondantes.</span><span class="sxs-lookup"><span data-stu-id="0b78c-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="0b78c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b78c-107">Syntax</span></span>

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

> [!NOTE]
> <span data-ttu-id="0b78c-108">Les blocs `GetScript`, `TestScript` et `SetScript` sont stockés sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="0b78c-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="0b78c-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0b78c-109">Properties</span></span>

|<span data-ttu-id="0b78c-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="0b78c-110">Property</span></span>|<span data-ttu-id="0b78c-111">Description</span><span class="sxs-lookup"><span data-stu-id="0b78c-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="0b78c-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="0b78c-112">GetScript</span></span>|<span data-ttu-id="0b78c-113">Un bloc de script qui retourne l’état actuel du nœud.</span><span class="sxs-lookup"><span data-stu-id="0b78c-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="0b78c-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="0b78c-114">SetScript</span></span>|<span data-ttu-id="0b78c-115">Un bloc de script utilisé par DSC pour appliquer la conformité lorsque le nœud n’est pas dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="0b78c-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="0b78c-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="0b78c-116">TestScript</span></span>|<span data-ttu-id="0b78c-117">Un bloc de script qui détermine si le nœud est dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="0b78c-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="0b78c-118">Credential</span><span class="sxs-lookup"><span data-stu-id="0b78c-118">Credential</span></span>| <span data-ttu-id="0b78c-119">Indique les informations d’identification à utiliser pour exécuter ce script, si elles sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="0b78c-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="0b78c-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0b78c-120">DependsOn</span></span>| <span data-ttu-id="0b78c-121">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="0b78c-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0b78c-122">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0b78c-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="0b78c-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="0b78c-123">GetScript</span></span>

<span data-ttu-id="0b78c-124">DSC n’utilise pas la sortie à partir de `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="0b78c-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="0b78c-125">La cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) exécute `GetScript` pour récupérer l’état actuel d’un nœud.</span><span class="sxs-lookup"><span data-stu-id="0b78c-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="0b78c-126">Une valeur de retour n’est pas nécessaire à partir de `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="0b78c-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="0b78c-127">Si vous spécifiez une valeur de retour, elle doit être un `hashtable` contenant une clé **Result** dont la valeur est une `String`.</span><span class="sxs-lookup"><span data-stu-id="0b78c-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="0b78c-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="0b78c-128">TestScript</span></span>

<span data-ttu-id="0b78c-129">`TestScript` est exécuté par DSC pour déterminer si `SetScript` doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="0b78c-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="0b78c-130">Si `TestScript` retourne `$false`, DSC exécute `SetScript` pour rétablir le nœud à l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="0b78c-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="0b78c-131">Il doit retourner une valeur `boolean`.</span><span class="sxs-lookup"><span data-stu-id="0b78c-131">It must return a `boolean` value.</span></span> <span data-ttu-id="0b78c-132">Un résultat de `$true` indique que le nœud est conforme et `SetScript` ne doit pas exécuté.</span><span class="sxs-lookup"><span data-stu-id="0b78c-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="0b78c-133">La cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) exécute `TestScript` pour récupérer la conformité des nœuds avec les ressources **Script**.</span><span class="sxs-lookup"><span data-stu-id="0b78c-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="0b78c-134">Toutefois, dans ce cas, `SetScript` ne s’exécute pas, quel que soit ce que le bloc `TestScript` retourne.</span><span class="sxs-lookup"><span data-stu-id="0b78c-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="0b78c-135">Toute sortie de votre `TestScript` fait partie de sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="0b78c-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="0b78c-136">PowerShell interprète une sortie non supprimée en tant que non nulle, ce qui signifie que votre `TestScript` retournera `$true` indépendamment de l’état de votre nœud.</span><span class="sxs-lookup"><span data-stu-id="0b78c-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="0b78c-137">Cela entraîne des résultats imprévisibles, des faux positifs, et entraîne des difficultés lors de la résolution de problèmes.</span><span class="sxs-lookup"><span data-stu-id="0b78c-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="0b78c-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="0b78c-138">SetScript</span></span>

<span data-ttu-id="0b78c-139">`SetScript` modifie le nœud pour appliquer l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="0b78c-139">The `SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="0b78c-140">Il est appelé par DSC si le bloc de script `TestScript` retourne `$false`.</span><span class="sxs-lookup"><span data-stu-id="0b78c-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="0b78c-141">`SetScript` ne doit avoir aucune valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="0b78c-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="0b78c-142">Exemples</span><span class="sxs-lookup"><span data-stu-id="0b78c-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="0b78c-143">Exemple 1 : Écrire un exemple de texte à l’aide d’une ressource Script</span><span class="sxs-lookup"><span data-stu-id="0b78c-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="0b78c-144">Cet exemple teste l’existence de `C:\TempFolder\TestFile.txt` sur chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="0b78c-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="0b78c-145">S’il n’existe pas, il le crée à l’aide de `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="0b78c-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="0b78c-146">`GetScript` retourne le contenu du fichier et sa valeur de retour n’est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="0b78c-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="0b78c-147">Exemple 2 : Comparer les informations de version à l’aide d’une ressource Script</span><span class="sxs-lookup"><span data-stu-id="0b78c-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="0b78c-148">Cet exemple récupère les informations de la version *conforme* à partir d’un fichier texte sur l’ordinateur de création et stocke ces informations dans la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="0b78c-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="0b78c-149">Lors de la génération du fichier MOF du nœud, DSC remplace les variables `$using:version` dans chaque bloc de script par la valeur de la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="0b78c-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="0b78c-150">Lors de l’exécution, la version *conforme* est stockée dans un fichier texte sur chaque nœud, puis comparée et mise à jour lors des exécutions suivantes.</span><span class="sxs-lookup"><span data-stu-id="0b78c-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

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
}
```