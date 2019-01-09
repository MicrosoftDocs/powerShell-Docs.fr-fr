---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Écriture d’une ressource de DSC d’instance unique (recommandation)
ms.openlocfilehash: 9494964b1b13eaa082ad5cbc279b4586bb7211cc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401810"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="d0902-103">Écriture d’une ressource de DSC d’instance unique (recommandation)</span><span class="sxs-lookup"><span data-stu-id="d0902-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="d0902-104">**Remarque :** cette rubrique décrit une meilleure pratique pour la définition d’une ressource DSC qui n’autorise qu’une seule instance dans une configuration.</span><span class="sxs-lookup"><span data-stu-id="d0902-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="d0902-105">Actuellement, il n’existe pas de fonctionnalité DSC intégrée pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="d0902-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="d0902-106">Cela pourrait changer à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="d0902-106">That might change in the future.</span></span>

<span data-ttu-id="d0902-107">Il existe des situations où vous ne souhaitez pas autoriser qu’une ressource soit utilisée plusieurs fois dans une configuration.</span><span class="sxs-lookup"><span data-stu-id="d0902-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="d0902-108">Par exemple, dans une précédente implémentation de la ressource [xTimeZone](https://github.com/PowerShell/xTimeZone), une configuration pouvait appeler la ressource plusieurs fois, en définissant un fuseau horaire différent dans chaque bloc de ressources :</span><span class="sxs-lookup"><span data-stu-id="d0902-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

<span data-ttu-id="d0902-109">Cela est dû à la manière dont les clés de ressources DSC fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="d0902-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="d0902-110">Une ressource doit avoir au moins une propriété de clé.</span><span class="sxs-lookup"><span data-stu-id="d0902-110">A resource must have at least one key property.</span></span> <span data-ttu-id="d0902-111">Une instance de ressource est considérée comme unique si la combinaison des valeurs de toutes ses propriétés de clé est unique.</span><span class="sxs-lookup"><span data-stu-id="d0902-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="d0902-112">Dans l’implémentation précédente, la ressource [xTimeZone](https://github.com/PowerShell/xTimeZone) n’avait qu’une seule propriété (**fuseau horaire**), qui devait nécessairement être une clé.</span><span class="sxs-lookup"><span data-stu-id="d0902-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="d0902-113">Pour cette raison, une configuration telle que celle ci-dessus était compilée et exécutée sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="d0902-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="d0902-114">Chacun des blocs de ressources **xTimeZone** est considéré comme unique.</span><span class="sxs-lookup"><span data-stu-id="d0902-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="d0902-115">Cela entraînerait l’application de la configuration au nœud à plusieurs reprises, en effectuant un cycle dans le fuseau horaire dans les deux sens.</span><span class="sxs-lookup"><span data-stu-id="d0902-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="d0902-116">Pour s’assurer qu’une configuration ne peut définir le fuseau horaire d’un nœud cible qu’une seule fois, la ressource a été mise à jour pour ajouter une deuxième propriété, **IsSingleInstance**, qui est devenue la propriété de clé.</span><span class="sxs-lookup"><span data-stu-id="d0902-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="d0902-117">La propriété **IsSingleInstance** a été limitée à une valeur unique, « Yes », à l’aide de **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="d0902-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="d0902-118">L’ancien schéma MOF de la ressource était :</span><span class="sxs-lookup"><span data-stu-id="d0902-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="d0902-119">Le schéma MOF mis à jour pour la ressource est :</span><span class="sxs-lookup"><span data-stu-id="d0902-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="d0902-120">Le script de ressources a été également mis à jour pour utiliser le nouveau paramètre.</span><span class="sxs-lookup"><span data-stu-id="d0902-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="d0902-121">Voici l’ancien script de ressources :</span><span class="sxs-lookup"><span data-stu-id="d0902-121">Here is the old resource script:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}


function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
            else
            {
                Write-Verbose -Verbose "TimeZone already set to $TimeZone"
            }
        }
        catch
        {
            $ErrorMsg = $_.Exception.Message
            Write-Verbose -Verbose $ErrorMsg
        }
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="d0902-122">Notez que la propriété **TimeZone** n’est plus une clé.</span><span class="sxs-lookup"><span data-stu-id="d0902-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="d0902-123">À présent, si une configuration tente de définir le fuseau horaire deux fois (à l’aide de deux blocs **xTimeZone** différents avec des valeurs **TimeZone** différentes), la tentative de compilation de la configuration génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="d0902-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```powershell
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```