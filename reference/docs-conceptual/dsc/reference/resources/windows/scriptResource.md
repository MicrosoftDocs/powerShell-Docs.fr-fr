---
ms.date: 07/16/2020
keywords: dsc,powershell,configuration,installation
title: Ressource Script dans DSC
ms.openlocfilehash: 9b89981c17e87b3681c6416c7dee44a75c432ea1
ms.sourcegitcommit: eb6a7c01e6385809656ac828b9211683e0b1a6fe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "89041127"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="a3728-103">Ressource Script dans DSC</span><span class="sxs-lookup"><span data-stu-id="a3728-103">DSC Script Resource</span></span>

> <span data-ttu-id="a3728-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="a3728-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="a3728-105">La ressource `Script` dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour exécuter des blocs de script Windows PowerShell sur des nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="a3728-105">The `Script` resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="a3728-106">La ressource `Script` utilise les propriétés `GetScript`,
`SetScript` et `TestScript` qui contiennent des blocs de script que vous définissez pour effectuer les opérations d’état DSC correspondantes.</span><span class="sxs-lookup"><span data-stu-id="a3728-106">The `Script` resource uses `GetScript`
`SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3728-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3728-107">Syntax</span></span>

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="a3728-108">Les blocs `GetScript`, `TestScript` et `SetScript` sont stockés sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a3728-108">`GetScript` `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="a3728-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a3728-109">Properties</span></span>

|  <span data-ttu-id="a3728-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="a3728-110">Property</span></span>  |                                          <span data-ttu-id="a3728-111">Description</span><span class="sxs-lookup"><span data-stu-id="a3728-111">Description</span></span>                                          |
| ---------- | --------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a3728-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="a3728-112">GetScript</span></span>  | <span data-ttu-id="a3728-113">Un bloc de script qui retourne l’état actuel du nœud.</span><span class="sxs-lookup"><span data-stu-id="a3728-113">A script block that returns the current state of the Node.</span></span>                                    |
| <span data-ttu-id="a3728-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="a3728-114">SetScript</span></span>  | <span data-ttu-id="a3728-115">Un bloc de script utilisé par DSC pour appliquer la conformité lorsque le nœud n’est pas dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="a3728-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
| <span data-ttu-id="a3728-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="a3728-116">TestScript</span></span> | <span data-ttu-id="a3728-117">Un bloc de script qui détermine si le nœud est dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="a3728-117">A script block that determines if the Node is in the desired state.</span></span>                           |
| <span data-ttu-id="a3728-118">Informations d'identification</span><span class="sxs-lookup"><span data-stu-id="a3728-118">Credential</span></span> | <span data-ttu-id="a3728-119">Indique les informations d’identification à utiliser pour exécuter ce script, si elles sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="a3728-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>        |

## <a name="common-properties"></a><span data-ttu-id="a3728-120">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="a3728-120">Common properties</span></span>

|       <span data-ttu-id="a3728-121">Propriété</span><span class="sxs-lookup"><span data-stu-id="a3728-121">Property</span></span>       |                                            <span data-ttu-id="a3728-122">Description</span><span class="sxs-lookup"><span data-stu-id="a3728-122">Description</span></span>                                            |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a3728-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a3728-123">DependsOn</span></span>            | <span data-ttu-id="a3728-124">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="a3728-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> |
| <span data-ttu-id="a3728-125">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a3728-125">PsDscRunAsCredential</span></span> | <span data-ttu-id="a3728-126">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="a3728-126">Sets the credential for running the entire resource as.</span></span>                                           |

> [!NOTE]
> <span data-ttu-id="a3728-127">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="a3728-127">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="a3728-128">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="a3728-128">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="a3728-129">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a3728-129">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="a3728-130">GetScript</span><span class="sxs-lookup"><span data-stu-id="a3728-130">GetScript</span></span>

<span data-ttu-id="a3728-131">DSC n’utilise pas la sortie de `GetScript`. L’applet de commande [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) exécute `GetScript` pour récupérer l’état actuel d’un nœud.</span><span class="sxs-lookup"><span data-stu-id="a3728-131">DSC does not use the output from `GetScript` The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="a3728-132">Aucune valeur renvoyée n’est exigée de `GetScript`. Si vous spécifiez une valeur de retour, celle-ci doit être une table de hachage contenant une clé **Result** dont la valeur est de type String.</span><span class="sxs-lookup"><span data-stu-id="a3728-132">A return value is not required from `GetScript` If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="a3728-133">TestScript</span><span class="sxs-lookup"><span data-stu-id="a3728-133">TestScript</span></span>

<span data-ttu-id="a3728-134">`TestScript` est exécuté par DSC pour déterminer si `SetScript` doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="a3728-134">`TestScript` is executed by DSC to determine if `SetScript` should be run.</span></span> <span data-ttu-id="a3728-135">Si `TestScript` retourne `$false`, DSC exécute `SetScript` pour ramener le nœud à l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="a3728-135">If `TestScript` returns `$false`, DSC executes `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="a3728-136">Il doit retourner une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="a3728-136">It must return a boolean value.</span></span> <span data-ttu-id="a3728-137">Un résultat de `$true` indique que le nœud est conforme et `SetScript` ne doit pas exécuté.</span><span class="sxs-lookup"><span data-stu-id="a3728-137">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="a3728-138">L’applet de commande [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) exécute `TestScript` pour récupérer la conformité des nœuds avec les ressources `Script`.</span><span class="sxs-lookup"><span data-stu-id="a3728-138">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes `TestScript` to retrieve the nodes compliance with the `Script` resources.</span></span> <span data-ttu-id="a3728-139">Cependant, dans ce cas, `SetScript` ne s’exécute pas, quel que soit le résultat retourné par le bloc `TestScript`.</span><span class="sxs-lookup"><span data-stu-id="a3728-139">However, in this case, `SetScript` does not run, no matter what `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="a3728-140">Toute sortie de votre `TestScript` fait partie de sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="a3728-140">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="a3728-141">PowerShell interprète une sortie non supprimée en tant que non nulle, ce qui signifie que votre `TestScript` retournera `$true` indépendamment de l’état de votre nœud.</span><span class="sxs-lookup"><span data-stu-id="a3728-141">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="a3728-142">Cela entraîne des résultats imprévisibles, des faux positifs, et entraîne des difficultés lors de la résolution de problèmes.</span><span class="sxs-lookup"><span data-stu-id="a3728-142">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="a3728-143">SetScript</span><span class="sxs-lookup"><span data-stu-id="a3728-143">SetScript</span></span>

<span data-ttu-id="a3728-144">`SetScript` modifie le nœud pour appliquer l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="a3728-144">`SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="a3728-145">Il est appelé par DSC si le bloc de script `TestScript` retourne `$false`.</span><span class="sxs-lookup"><span data-stu-id="a3728-145">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="a3728-146">`SetScript` ne doit avoir aucune valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="a3728-146">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="a3728-147">Exemples</span><span class="sxs-lookup"><span data-stu-id="a3728-147">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="a3728-148">Exemple 1 : Écrire un exemple de texte à l’aide d’une ressource Script</span><span class="sxs-lookup"><span data-stu-id="a3728-148">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="a3728-149">Cet exemple teste l’existence de `C:\TempFolder\TestFile.txt` sur chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="a3728-149">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="a3728-150">S’il n’existe pas, il le crée à l’aide de `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="a3728-150">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="a3728-151">`GetScript` retourne le contenu du fichier et sa valeur de retour n’est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="a3728-151">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="a3728-152">Exemple 2 : Comparer les informations de version à l’aide d’une ressource Script</span><span class="sxs-lookup"><span data-stu-id="a3728-152">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="a3728-153">Cet exemple récupère les informations de la version _conforme_ à partir d’un fichier texte sur l’ordinateur de création et stocke ces informations dans la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="a3728-153">This example retrieves the _compliant_ version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="a3728-154">Lors de la génération du fichier MOF du nœud, DSC remplace les variables `$using:version` dans chaque bloc de script par la valeur de la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="a3728-154">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="a3728-155">Lors de l’exécution, la version _conforme_ est stockée dans un fichier texte sur chaque nœud, puis comparée et mise à jour lors des exécutions suivantes.</span><span class="sxs-lookup"><span data-stu-id="a3728-155">During execution, the _compliant_ version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

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

                if( $state.Result -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state.Result,$using:version)
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

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a><span data-ttu-id="a3728-156">Exemple 3 : Utilisation de paramètres dans une ressource Script</span><span class="sxs-lookup"><span data-stu-id="a3728-156">Example 3: Utilizing parameters in a Script resource</span></span>

<span data-ttu-id="a3728-157">Cet exemple accède aux paramètres à partir de la ressource Script en utilisant l’étendue `using`.</span><span class="sxs-lookup"><span data-stu-id="a3728-157">This example accesses parameters from within the Script resource by making use of the `using` scope.</span></span>
<span data-ttu-id="a3728-158">Notez que **ConfigurationData** est accessible de la même façon.</span><span class="sxs-lookup"><span data-stu-id="a3728-158">Please note that **ConfigurationData** can be accessed in a similar way.</span></span> <span data-ttu-id="a3728-159">Comme dans l’exemple 2, une version est censée être stockée dans un fichier local sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="a3728-159">Like example 2, a version is expected to be stored inside a local file on the target node.</span></span> <span data-ttu-id="a3728-160">Toutefois, le chemin d’accès au fichier local et la version sont configurables, mais le code est découplé à partir des données de configuration.</span><span class="sxs-lookup"><span data-stu-id="a3728-160">Both the local file path as well as the version are configurable however, decoupling code from configuration data.</span></span>

```powershell
Configuration ScriptTest
{
    param
    (
        [Version]
        $Version,

        [string]
        $FilePath
    )

    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content -Path $using:FilePath
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:Version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }

                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                Set-Content -Path $using:FilePath -Value $using:Version
            }
        }
    }
}
```

<span data-ttu-id="a3728-161">Le fichier MOF qui en résulte comprend les variables et leurs valeurs accessibles par le biais de l’étendue `using`.</span><span class="sxs-lookup"><span data-stu-id="a3728-161">The resulting MOF file includes the variables and their values accessed through the `using` scope.</span></span>
<span data-ttu-id="a3728-162">Elles sont injectées dans chaque bloc de script qui utilise les variables.</span><span class="sxs-lookup"><span data-stu-id="a3728-162">They are injected into each scriptblock which uses the variables.</span></span> <span data-ttu-id="a3728-163">Les scripts Test et Set ont été supprimés par souci de concision :</span><span class="sxs-lookup"><span data-stu-id="a3728-163">Test and Set scripts have been removed for brevity:</span></span>

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```

### <a name="known-limitations"></a><span data-ttu-id="a3728-164">Limites connues</span><span class="sxs-lookup"><span data-stu-id="a3728-164">Known Limitations</span></span>

- <span data-ttu-id="a3728-165">Les informations d’identification transmises au sein d’une ressource de script ne sont pas toujours fiables lors de l’utilisation d’un modèle de serveur de tirage (pull) ou d’envoi (push).</span><span class="sxs-lookup"><span data-stu-id="a3728-165">Credentials being passed within a script resource are not always reliable when using a pull or push server model.</span></span> <span data-ttu-id="a3728-166">Il est recommandé d’utiliser une ressource complète au lieu d’utiliser une ressource de script dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="a3728-166">It is recommended to use a full resource rather than use a script resource in this case.</span></span>
