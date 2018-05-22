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
# <a name="dsc-script-resource"></a>Ressource Script dans DSC


> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **Script** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour exécuter des blocs de script Windows PowerShell sur des nœuds cibles. La ressource `Script` comprend les propriétés `GetScript`, `SetScript` et `TestScript`. Ces propriétés doivent être définies sur les blocs de script qui sont exécutés sur chaque nœud cible.

Le bloc de script `GetScript` doit retourner une table de hachage qui représente l’état du nœud actuel. La table de hachage doit contenir une seule clé `Result` et la valeur doit être de type `String`. Il n’a pas à retourner d’élément. DSC ne fait rien avec la sortie de ce bloc de script.

Le bloc de script `TestScript` doit déterminer si le nœud actuel doit être modifié. Il doit retourner `$true` si le nœud est à jour. Il doit retourner `$false` si la configuration du nœud est obsolète et doit être mise à jour par le bloc de script `SetScript`. Le bloc de script `TestScript` est appelé par DSC.

Le bloc de script `SetScript` doit modifier le nœud. Il est appelé par DSC si le bloc `TestScript` retourne `$false`.

Si vous devez utiliser des variables de votre script de configuration dans les blocs de script `GetScript`, `TestScript` ou `SetScript`, utilisez l’étendue `$using:` (voir ci-dessous pour obtenir un exemple).


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

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| GetScript| Fournit un bloc de script Windows PowerShell qui s’exécute quand vous appelez l’applet de commande [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx). Ce bloc doit retourner une table de hachage. La table de hachage doit contenir une seule clé **Result** et la valeur doit être de type **String**.|
| SetScript| Fournit un bloc de script Windows PowerShell. Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx), le bloc **TestScript** s’exécute en premier. Si le bloc **TestScript** retourne **$false**, le bloc **SetScript** s’exécute. Si le bloc **TestScript** retourne **$true**, le bloc **SetScript** ne s’exécute pas.|
| TestScript| Fournit un bloc de script Windows PowerShell. Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx), ce bloc s’exécute. Si elle retourne **$false**, le bloc SetScript s’exécute. Si elle retourne **$true**, le bloc SetScript ne s’exécute pas. Le bloc **TestScript** s’exécute également quand vous appelez l’applet de commande [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx). Toutefois, dans ce cas, la propriété **SetScript** ne s’exécute pas, quelle que soit la valeur retournée par le bloc TestScript. Le bloc **TestScript** doit retourner True si la configuration réelle correspond à la configuration d’état souhaité actuelle, sinon False. (La configuration d’état souhaité actuelle est la dernière configuration appliquée sur le nœud qui utilise DSC.)|
| Credential| Indique les informations d’identification à utiliser pour exécuter ce script, si elles sont nécessaires.|
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.

## <a name="example-1"></a>Exemple 1
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

## <a name="example-2"></a>Exemple 2
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

Cette ressource écrit la version de la configuration dans un fichier texte. Cette version étant disponible sur l’ordinateur client, mais pas sur les nœuds, elle doit être transmise à chacun des blocs de script de la ressource `Script` avec l’étendue `using` de PowerShell. Lors de la génération du fichier MOF du nœud, la valeur de la variable `$version` est lue à partir d’un fichier texte sur l’ordinateur client. DSC remplace les variables `$using:version` dans chaque bloc de script par la valeur de la variable `$version`.