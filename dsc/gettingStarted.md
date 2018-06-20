---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Prise en main de la configuration de l’état souhaité (DSC) Windows PowerShell
ms.openlocfilehash: a449382c979e680ea311c887c86cb675ba6162b7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189718"
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a>Prise en main de la configuration de l’état souhaité (DSC) Windows PowerShell #

Ce guide explique comment créer des documents de configuration d’état souhaité PowerShell et comment les appliquer aux ordinateurs. Il suppose une connaissance de base des applets de commande PowerShell, des modules et des fonctions.


## <a name="create-a-configuration"></a>Créer une configuration ##

Les [**configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) sont des documents qui décrivent un environnement. Les environnements sont constitués de **nœuds** qui sont généralement des machines physiques ou virtuelles.

Les configurations peuvent se présenter sous différentes formes. Le moyen le plus simple de créer une nouvelle configuration consiste à créer un fichier .ps1 (script PowerShell). Pour ce faire, ouvrez l’éditeur de votre choix. PowerShell ISE constitue un bon choix, car il comprend DSC de manière native. Enregistrez ce qui suit dans un fichier PS1 :

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a>Composants d’une configuration ##
**Configuration** est un mot clé qui date de PowerShell 4.0. Il désigne un type spécial de fonction PowerShell utilisée par DSC. Dans cet exemple, la fonction se nomme myFirstConfiguration.

La ligne suivante est une instruction d’importation, similaire à l’importation d’un module. Nous l’aborderons plus tard.

Node définit le nom de l’ordinateur auquel est appliquée la configuration. Même si elles sont modifiées localement, les configurations peuvent atteindre les nœuds distants et les configurer.

Les nœuds peuvent être des noms d’ordinateurs ou des adresses IP. Vous pouvez avoir plusieurs nœuds dans un même document de configuration. À l’aide de [données de configuration](https://msdn.microsoft.com/powershell/dsc/configdata), vous pouvez également appliquer une même configuration à plusieurs nœuds. Ici, le nœud s’appelle « localhost », ce qui correspond à l’ordinateur local.

L’élément suivant est une [**ressource**](https://msdn.microsoft.com/powershell/dsc/resources). Les ressources sont les blocs de construction des configurations. Chaque ressource est un module qui définit la logique d’implémentation d’un aspect d’un ordinateur. Vous pouvez afficher toutes les ressources de votre ordinateur en exécutant **Get-DscResource** dans PowerShell. Les ressources doivent être présentes sur l’ordinateur local et importées avant de pouvoir être utilisées dans une configuration avec **Import-DscResource**, qui se trouve sur la deuxième ligne de cette configuration.

**Promulgation d’une configuration**

Si le script ci-dessus est enregistré et exécuté, vous n’obtiendrez aucune sortie. En effet, une configuration est une fonction, et le script ci-dessus a défini la fonction, mais ne l’a pas encore exécutée. Une fois la fonction définie, elle doit être appelée :
```powershell
myFirstConfiguration
```

Quand elles sont exécutées, les fonctions de configuration confirment que la configuration est valide. Elle ne doit comporter aucune erreur de syntaxe. Les paramètres obligatoires des ressources doivent être définis et toutes les ressources doivent être importées avant l’exécution.

Une fois la configuration exécutée, un dossier portant le nom de la configuration est créé. Il contient un **fichier .MOF** pour chaque nœud de la configuration. Le format .MOF est un format de gestion basé sur des normes qui est utilisé par DSC PowerShell pour communiquer sur le réseau.

Pour promulguer la configuration :
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
Cela crée une tâche PowerShell qui contacte les nœuds de la configuration et les configure. Pour afficher la sortie de la tâche, utilisez -Wait.
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```