---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Boucles et instructions conditionnelles dans les configurations
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401251"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Boucles et instructions conditionnelles dans les configurations

Vous pouvez rendre votre [Configurations](configurations.md) plus dynamique à l’aide de mots clés de contrôle de flux de PowerShell. Cet article vous explique comment vous pouvez utiliser des instructions conditionnelles et des boucles pour rendre vos Configurations plus dynamique. Combinaison conditionnelle et des boucles avec [paramètres](add-parameters-to-a-configuration.md) et [les données de Configuration](configData.md) vous permet de plus de souplesse et de contrôle lors de la compilation de vos Configurations.

Tout comme une fonction ou un bloc de Script, vous pouvez utiliser n’importe quel langage PowerShell au sein d’une Configuration. Les instructions que vous utilisez seront évaluées uniquement lorsque vous appelez votre Configuration pour compiler un fichier « .mof ». Les exemples ci-dessous illustrent des scénarios simples pour illustrer les concepts. Instructions conditionnelles sont boucles sont plus souvent utilisés avec des paramètres et données de Configuration.

Dans cet exemple simple, le **Service** bloc de ressources récupère l’état actuel d’un service au moment de la compilation pour générer un fichier « .mof » qui conserve son état actuel.

> [!NOTE]
> À l’aide de blocs de ressources dynamiques sera préempter l’efficacité d’Intellisense. L’Analyseur de PowerShell ne peut pas déterminer si les valeurs spécifiées sont acceptables jusqu'à ce que la Configuration est compilée.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

En outre, vous pouvez créer un **Service** bloquer les ressources pour chaque service sur l’ordinateur actuel, à l’aide un `foreach` boucle.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

Vous pouvez créer également uniquement des configurations pour les ordinateurs qui sont en ligne, à l’aide d’une simple `if` instruction.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> La ressource dynamique bloque, dans la référence d’exemples ci-dessus, l’ordinateur actuel. Dans ce cas, ce qui serait l’ordinateur que vous créez la Configuration sur, pas la nœud cible.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Résumé

En résumé, vous pouvez utiliser n’importe quel langage PowerShell au sein d’une Configuration.

Cela inclut des éléments tels que :

- Objets personnalisés
- Tables de hachage
- Manipulation de chaînes
- Communication à distance
- WMI et CIM
- Objets Active Directory
- et plus...

N’importe quel code PowerShell défini dans une Configuration sera évaluée à un moment de la compilation, mais vous pouvez également placer le code dans le script qui contient votre Configuration. N’importe quel code en dehors du bloc de Configuration sera exécuté lorsque vous importez votre Configuration.

## <a name="see-also"></a>Voir aussi

- [Ajouter des paramètres à une configuration](add-parameters-to-a-configuration.md)
- [Séparer des données de configuration des configurations](configData.md)
