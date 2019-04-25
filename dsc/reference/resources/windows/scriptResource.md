---
ms.date: 08/24/2018
keywords: dsc,powershell,configuration,setup
title: Ressource Script dans DSC
ms.openlocfilehash: 4eee5625add4d96ade7ababf7f534f597a26712d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076988"
---
# <a name="dsc-script-resource"></a>Ressource Script dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **Script** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour exécuter des blocs de script Windows PowerShell sur des nœuds cibles. La ressource **Script** utilise les propriétés `GetScript`, `SetScript` et `TestScript` qui contiennent des blocs de script que vous définissez pour effectuer les opérations d’état DSC correspondantes.

## <a name="syntax"></a>Syntaxe

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
> Les blocs `GetScript`, `TestScript` et `SetScript` sont stockés sous forme de chaînes.

## <a name="properties"></a>Propriétés

|Propriété|Description|
|--------|-----------|
|GetScript|Un bloc de script qui retourne l’état actuel du nœud.|
|SetScript|Un bloc de script utilisé par DSC pour appliquer la conformité lorsque le nœud n’est pas dans l’état souhaité.|
|TestScript|Un bloc de script qui détermine si le nœud est dans l’état souhaité.|
|Credential| Indique les informations d’identification à utiliser pour exécuter ce script, si elles sont nécessaires.|
|DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.

### <a name="getscript"></a>GetScript

DSC n’utilise pas la sortie à partir de `GetScript`. La cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) exécute `GetScript` pour récupérer l’état actuel d’un nœud. Une valeur de retour n’est pas nécessaire à partir de `GetScript`. Si vous spécifiez une valeur de retour, elle doit être un `hashtable` contenant une clé **Result** dont la valeur est une `String`.

### <a name="testscript"></a>TestScript

`TestScript` est exécuté par DSC pour déterminer si `SetScript` doit être exécuté. Si `TestScript` retourne `$false`, DSC exécute `SetScript` pour rétablir le nœud à l’état souhaité. Il doit retourner une valeur `boolean`. Un résultat de `$true` indique que le nœud est conforme et `SetScript` ne doit pas exécuté.

La cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) exécute `TestScript` pour récupérer la conformité des nœuds avec les ressources **Script**. Toutefois, dans ce cas, `SetScript` ne s’exécute pas, quel que soit ce que le bloc `TestScript` retourne.

> [!NOTE]
> Toute sortie de votre `TestScript` fait partie de sa valeur de retour. PowerShell interprète une sortie non supprimée en tant que non nulle, ce qui signifie que votre `TestScript` retournera `$true` indépendamment de l’état de votre nœud.
> Cela entraîne des résultats imprévisibles, des faux positifs, et entraîne des difficultés lors de la résolution de problèmes.

### <a name="setscript"></a>SetScript

`SetScript` modifie le nœud pour appliquer l’état souhaité. Il est appelé par DSC si le bloc de script `TestScript` retourne `$false`. `SetScript` ne doit avoir aucune valeur de retour.

## <a name="examples"></a>Exemples

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Exemple 1 : Écrire un exemple de texte à l’aide d’une ressource Script

Cet exemple teste l’existence de `C:\TempFolder\TestFile.txt` sur chaque nœud. S’il n’existe pas, il le crée à l’aide de `SetScript`. `GetScript` retourne le contenu du fichier et sa valeur de retour n’est pas utilisée.

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Exemple 2 : Comparer les informations de version à l’aide d’une ressource Script

Cet exemple récupère les informations de la version *conforme* à partir d’un fichier texte sur l’ordinateur de création et stocke ces informations dans la variable `$version`. Lors de la génération du fichier MOF du nœud, DSC remplace les variables `$using:version` dans chaque bloc de script par la valeur de la variable `$version`. Lors de l’exécution, la version *conforme* est stockée dans un fichier texte sur chaque nœud, puis comparée et mise à jour lors des exécutions suivantes.

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
