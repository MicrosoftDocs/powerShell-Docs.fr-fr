---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource Script dans DSC
ms.openlocfilehash: 50d4667396c8c619079288ec51599152ed2d6cd5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557020"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="abbbb-103">Ressource Script dans DSC</span><span class="sxs-lookup"><span data-stu-id="abbbb-103">DSC Script Resource</span></span>

> <span data-ttu-id="abbbb-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="abbbb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="abbbb-105">La ressource **Script** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour exécuter des blocs de script Windows PowerShell sur des nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="abbbb-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="abbbb-106">La ressource **Script** utilise les propriétés **GetScript**, **SetScript** et **TestScript** qui contiennent les blocs de script que vous définissez pour effectuer les opérations d’état DSC correspondantes.</span><span class="sxs-lookup"><span data-stu-id="abbbb-106">The **Script** resource uses **GetScript**, **SetScript**, and **TestScript** properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="abbbb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abbbb-107">Syntax</span></span>

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
> <span data-ttu-id="abbbb-108">Les blocs **GetScript**, **TestScript** et **SetScript** sont stockés sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="abbbb-108">**GetScript**, **TestScript**, and **SetScript** blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="abbbb-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="abbbb-109">Properties</span></span>

|<span data-ttu-id="abbbb-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="abbbb-110">Property</span></span> |<span data-ttu-id="abbbb-111">Description</span><span class="sxs-lookup"><span data-stu-id="abbbb-111">Description</span></span> |
|---|---|
|<span data-ttu-id="abbbb-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="abbbb-112">GetScript</span></span> |<span data-ttu-id="abbbb-113">Un bloc de script qui retourne l’état actuel du nœud.</span><span class="sxs-lookup"><span data-stu-id="abbbb-113">A script block that returns the current state of the Node.</span></span> |
|<span data-ttu-id="abbbb-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="abbbb-114">SetScript</span></span> |<span data-ttu-id="abbbb-115">Un bloc de script utilisé par DSC pour appliquer la conformité lorsque le nœud n’est pas dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="abbbb-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
|<span data-ttu-id="abbbb-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="abbbb-116">TestScript</span></span> |<span data-ttu-id="abbbb-117">Un bloc de script qui détermine si le nœud est dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="abbbb-117">A script block that determines if the Node is in the desired state.</span></span> |
|<span data-ttu-id="abbbb-118">Informations d'identification</span><span class="sxs-lookup"><span data-stu-id="abbbb-118">Credential</span></span> |<span data-ttu-id="abbbb-119">Indique les informations d’identification à utiliser pour exécuter ce script, si elles sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="abbbb-119">Indicates the credentials to use for running this script, if credentials are required.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="abbbb-120">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="abbbb-120">Common properties</span></span>

|<span data-ttu-id="abbbb-121">Propriété</span><span class="sxs-lookup"><span data-stu-id="abbbb-121">Property</span></span> |<span data-ttu-id="abbbb-122">Description</span><span class="sxs-lookup"><span data-stu-id="abbbb-122">Description</span></span> |
|---|---|
|<span data-ttu-id="abbbb-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="abbbb-123">DependsOn</span></span> |<span data-ttu-id="abbbb-124">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="abbbb-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="abbbb-125">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="abbbb-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="abbbb-126">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="abbbb-126">PsDscRunAsCredential</span></span> |<span data-ttu-id="abbbb-127">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="abbbb-127">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="abbbb-128">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="abbbb-128">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="abbbb-129">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="abbbb-129">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="abbbb-130">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="abbbb-130">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="abbbb-131">GetScript</span><span class="sxs-lookup"><span data-stu-id="abbbb-131">GetScript</span></span>

<span data-ttu-id="abbbb-132">DSC n’utilise pas la sortie de **GetScript**.</span><span class="sxs-lookup"><span data-stu-id="abbbb-132">DSC does not use the output from **GetScript**.</span></span> <span data-ttu-id="abbbb-133">L’applet de commande [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) exécute **GetScript** pour récupérer l’état actuel d’un nœud.</span><span class="sxs-lookup"><span data-stu-id="abbbb-133">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes **GetScript** to retrieve a node's current state.</span></span> <span data-ttu-id="abbbb-134">Une valeur de retour de **GetScript** n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="abbbb-134">A return value is not required from **GetScript**.</span></span> <span data-ttu-id="abbbb-135">Si vous spécifiez une valeur de retour, celle-ci doit être une table de hachage contenant une clé **Result** dont la valeur est de type String.</span><span class="sxs-lookup"><span data-stu-id="abbbb-135">If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="abbbb-136">TestScript</span><span class="sxs-lookup"><span data-stu-id="abbbb-136">TestScript</span></span>

<span data-ttu-id="abbbb-137">**TestScript** est exécuté par DSC pour déterminer si **SetScript** doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="abbbb-137">**TestScript** is executed by DSC to determine if **SetScript** should be run.</span></span> <span data-ttu-id="abbbb-138">Si **TestScript** retourne `$false`, DSC exécute **SetScript** pour ramener le nœud à l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="abbbb-138">If **TestScript** returns `$false`, DSC executes **SetScript** to bring the node back to the desired state.</span></span> <span data-ttu-id="abbbb-139">Il doit retourner une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="abbbb-139">It must return a boolean value.</span></span> <span data-ttu-id="abbbb-140">Le résultat `$true` indique que le nœud est conforme et que **SetScript** ne doit pas s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="abbbb-140">A result of `$true` indicates that the node is compliant and **SetScript** should not executed.</span></span>

<span data-ttu-id="abbbb-141">L’applet de commande [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) exécute **TestScript** pour récupérer la conformité des nœuds avec les ressources **Script**.</span><span class="sxs-lookup"><span data-stu-id="abbbb-141">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes **TestScript** to retrieve the nodes compliance with the **Script** resources.</span></span>
<span data-ttu-id="abbbb-142">Cependant, dans ce cas, **SetScript** ne s’exécute pas, quel que soit le résultat retourné par le bloc **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="abbbb-142">However, in this case, **SetScript** does not run, no matter what **TestScript** block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="abbbb-143">Toute la sortie de votre **TestScript** fait partie de sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="abbbb-143">All output from your **TestScript** is part of its return value.</span></span> <span data-ttu-id="abbbb-144">PowerShell interprète une sortie non supprimée comme étant non nulle, ce qui signifie que votre **TestScript** retournera `$true` quel que soit l’état de votre nœud.</span><span class="sxs-lookup"><span data-stu-id="abbbb-144">PowerShell interprets unsuppressed output as non-zero, which means that your **TestScript** will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="abbbb-145">Cela entraîne des résultats imprévisibles, des faux positifs, et entraîne des difficultés lors de la résolution de problèmes.</span><span class="sxs-lookup"><span data-stu-id="abbbb-145">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="abbbb-146">SetScript</span><span class="sxs-lookup"><span data-stu-id="abbbb-146">SetScript</span></span>

<span data-ttu-id="abbbb-147">**SetScript** modifie le nœud pour appliquer l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="abbbb-147">**SetScript** modifies the node to enforce the desired state.</span></span> <span data-ttu-id="abbbb-148">Il est appelé par DSC si le bloc de script **TestScript**  retourne `$false`.</span><span class="sxs-lookup"><span data-stu-id="abbbb-148">It is called by DSC if the **TestScript** script block returns `$false`.</span></span> <span data-ttu-id="abbbb-149">**SetScript** ne doit avoir aucune valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="abbbb-149">The **SetScript** should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="abbbb-150">Exemples</span><span class="sxs-lookup"><span data-stu-id="abbbb-150">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="abbbb-151">Exemple 1 : Écrire un exemple de texte à l’aide d’une ressource Script</span><span class="sxs-lookup"><span data-stu-id="abbbb-151">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="abbbb-152">Cet exemple teste l’existence de `C:\TempFolder\TestFile.txt` sur chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="abbbb-152">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="abbbb-153">S’il n’existe pas, il le crée à l’aide de `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="abbbb-153">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="abbbb-154">`GetScript` retourne le contenu du fichier et sa valeur de retour n’est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="abbbb-154">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="abbbb-155">Exemple 2 : Comparer les informations de version à l’aide d’une ressource Script</span><span class="sxs-lookup"><span data-stu-id="abbbb-155">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="abbbb-156">Cet exemple récupère les informations de la version *conforme* à partir d’un fichier texte sur l’ordinateur de création et stocke ces informations dans la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="abbbb-156">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="abbbb-157">Lors de la génération du fichier MOF du nœud, DSC remplace les variables `$using:version` dans chaque bloc de script par la valeur de la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="abbbb-157">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="abbbb-158">Lors de l’exécution, la version *conforme* est stockée dans un fichier texte sur chaque nœud, puis comparée et mise à jour lors des exécutions suivantes.</span><span class="sxs-lookup"><span data-stu-id="abbbb-158">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

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

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a><span data-ttu-id="abbbb-159">Exemple 3 : Utilisation de paramètres dans une ressource Script</span><span class="sxs-lookup"><span data-stu-id="abbbb-159">Example 3: Utilizing parameters in a Script resource</span></span>

<span data-ttu-id="abbbb-160">Cet exemple accède aux paramètres à partir de la ressource Script en utilisant l’étendue `using`.</span><span class="sxs-lookup"><span data-stu-id="abbbb-160">This example accesses parameters from within the Script resource by making use of the `using` scope.</span></span> <span data-ttu-id="abbbb-161">Notez que **ConfigurationData** est accessible de la même façon.</span><span class="sxs-lookup"><span data-stu-id="abbbb-161">Please note that **ConfigurationData** can be accessed in a similar way.</span></span> <span data-ttu-id="abbbb-162">Comme dans l’exemple 2, une version est censée être stockée dans un fichier local sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="abbbb-162">Like example 2, a version is expected to be stored inside a local file on the target node.</span></span> <span data-ttu-id="abbbb-163">Toutefois, le chemin d’accès au fichier local et la version sont configurables, mais le code est découplé à partir des données de configuration.</span><span class="sxs-lookup"><span data-stu-id="abbbb-163">Both the local file path as well as the version are configurable however, decoupling code from configuration data.</span></span>

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

<span data-ttu-id="abbbb-164">Le fichier MOF qui en résulte comprend les variables et leurs valeurs accessibles par le biais de l’étendue `using`.</span><span class="sxs-lookup"><span data-stu-id="abbbb-164">The resulting MOF file includes the variables and their values accessed through the `using` scope.</span></span>
<span data-ttu-id="abbbb-165">Elles sont injectées dans chaque bloc de script qui utilise les variables.</span><span class="sxs-lookup"><span data-stu-id="abbbb-165">They are injected into each scriptblock which uses the variables.</span></span> <span data-ttu-id="abbbb-166">Les scripts Test et Set ont été supprimés par souci de concision :</span><span class="sxs-lookup"><span data-stu-id="abbbb-166">Test and Set scripts have been removed for brevity:</span></span>

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```
