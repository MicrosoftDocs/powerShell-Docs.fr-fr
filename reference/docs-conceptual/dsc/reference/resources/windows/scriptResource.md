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
# <a name="dsc-script-resource"></a>Ressource Script dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource `Script` dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour exécuter des blocs de script Windows PowerShell sur des nœuds cibles. La ressource `Script` utilise les propriétés `GetScript`,
`SetScript` et `TestScript` qui contiennent des blocs de script que vous définissez pour effectuer les opérations d’état DSC correspondantes.

## <a name="syntax"></a>Syntaxe

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
> Les blocs `GetScript`, `TestScript` et `SetScript` sont stockés sous forme de chaînes.

## <a name="properties"></a>Propriétés

|  Propriété  |                                          Description                                          |
| ---------- | --------------------------------------------------------------------------------------------- |
| GetScript  | Un bloc de script qui retourne l’état actuel du nœud.                                    |
| SetScript  | Un bloc de script utilisé par DSC pour appliquer la conformité lorsque le nœud n’est pas dans l’état souhaité. |
| TestScript | Un bloc de script qui détermine si le nœud est dans l’état souhaité.                           |
| Informations d'identification | Indique les informations d’identification à utiliser pour exécuter ce script, si elles sont nécessaires.        |

## <a name="common-properties"></a>Propriétés communes

|       Propriété       |                                            Description                                            |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| DependsOn            | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. |
| PsDscRunAsCredential | Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.                                           |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

### <a name="additional-information"></a>Informations supplémentaires

#### <a name="getscript"></a>GetScript

DSC n’utilise pas la sortie de `GetScript`. L’applet de commande [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) exécute `GetScript` pour récupérer l’état actuel d’un nœud. Aucune valeur renvoyée n’est exigée de `GetScript`. Si vous spécifiez une valeur de retour, celle-ci doit être une table de hachage contenant une clé **Result** dont la valeur est de type String.

#### <a name="testscript"></a>TestScript

`TestScript` est exécuté par DSC pour déterminer si `SetScript` doit être exécuté. Si `TestScript` retourne `$false`, DSC exécute `SetScript` pour ramener le nœud à l’état souhaité. Il doit retourner une valeur booléenne. Un résultat de `$true` indique que le nœud est conforme et `SetScript` ne doit pas exécuté.

L’applet de commande [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) exécute `TestScript` pour récupérer la conformité des nœuds avec les ressources `Script`. Cependant, dans ce cas, `SetScript` ne s’exécute pas, quel que soit le résultat retourné par le bloc `TestScript`.

> [!NOTE]
> Toute sortie de votre `TestScript` fait partie de sa valeur de retour. PowerShell interprète une sortie non supprimée en tant que non nulle, ce qui signifie que votre `TestScript` retournera `$true` indépendamment de l’état de votre nœud. Cela entraîne des résultats imprévisibles, des faux positifs, et entraîne des difficultés lors de la résolution de problèmes.

#### <a name="setscript"></a>SetScript

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

Cet exemple récupère les informations de la version _conforme_ à partir d’un fichier texte sur l’ordinateur de création et stocke ces informations dans la variable `$version`. Lors de la génération du fichier MOF du nœud, DSC remplace les variables `$using:version` dans chaque bloc de script par la valeur de la variable `$version`.
Lors de l’exécution, la version _conforme_ est stockée dans un fichier texte sur chaque nœud, puis comparée et mise à jour lors des exécutions suivantes.

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

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a>Exemple 3 : Utilisation de paramètres dans une ressource Script

Cet exemple accède aux paramètres à partir de la ressource Script en utilisant l’étendue `using`.
Notez que **ConfigurationData** est accessible de la même façon. Comme dans l’exemple 2, une version est censée être stockée dans un fichier local sur le nœud cible. Toutefois, le chemin d’accès au fichier local et la version sont configurables, mais le code est découplé à partir des données de configuration.

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

Le fichier MOF qui en résulte comprend les variables et leurs valeurs accessibles par le biais de l’étendue `using`.
Elles sont injectées dans chaque bloc de script qui utilise les variables. Les scripts Test et Set ont été supprimés par souci de concision :

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```

### <a name="known-limitations"></a>Limites connues

- Les informations d’identification transmises au sein d’une ressource de script ne sont pas toujours fiables lors de l’utilisation d’un modèle de serveur de tirage (pull) ou d’envoi (push). Il est recommandé d’utiliser une ressource complète au lieu d’utiliser une ressource de script dans ce cas.
