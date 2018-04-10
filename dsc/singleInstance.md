---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Écriture d’une ressource de DSC d’instance unique (recommandation)
ms.openlocfilehash: fc118fd8b0d91d2001030769ac7e3c6321972905
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Écriture d’une ressource de DSC d’instance unique (recommandation)

>**Remarque :** cette rubrique décrit une recommandation pour la définition d’une ressource DSC qui n’autorise qu’une seule instance dans une configuration. Actuellement, il n’existe pas de fonctionnalité DSC intégrée pour ce faire. Cela pourrait changer à l’avenir.

Il existe des situations où vous ne souhaitez pas autoriser qu’une ressource soit utilisée plusieurs fois dans une configuration. Par exemple, dans une précédente implémentation de la ressource [xTimeZone](https://github.com/PowerShell/xTimeZone), une configuration pouvait appeler la ressource plusieurs fois, en définissant un fuseau horaire différent dans chaque bloc de ressources :

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

Cela est dû à la manière dont les clés de ressources DSC fonctionnent. Une ressource doit avoir au moins une propriété de clé. Une instance de ressource est considérée comme unique si la combinaison des valeurs de toutes ses propriétés de clé est unique. Dans l’implémentation précédente, la ressource [xTimeZone](https://github.com/PowerShell/xTimeZone) n’avait qu’une seule propriété (**fuseau horaire**), qui devait nécessairement être une clé. Pour cette raison, une configuration telle que celle ci-dessus était compilée et exécutée sans avertissement. Chacun des blocs de ressources **xTimeZone** est considéré comme unique. Cela entraînerait l’application de la configuration au nœud à plusieurs reprises, en effectuant un cycle dans le fuseau horaire dans les deux sens.

Pour s’assurer qu’une configuration ne puisse définir le fuseau horaire d’un nœud cible qu’une seule fois, la ressource a été mise à jour pour ajouter une deuxième propriété, **IsSingleInstance**, qui est devenue la propriété de clé.
La propriété **IsSingleInstance** a été limitée à une valeur unique, « Yes », à l’aide de **ValueMap**. L’ancien schéma MOF de la ressource était :

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Le schéma MOF mis à jour pour la ressource est :

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Le script de ressources a été également mis à jour pour utiliser le nouveau paramètre. Voici l’ancien script de ressources :

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

Notez que la propriété **TimeZone** n’est plus une clé. À présent, si une configuration tente de définir le fuseau horaire deux fois (à l’aide de deux blocs **xTimeZone** différents avec des valeurs **TimeZone** différentes), la tentative de compilation de la configuration génère une erreur :

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