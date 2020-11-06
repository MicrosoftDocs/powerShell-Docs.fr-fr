---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,installation
title: Boucles et instructions conditionnelles dans les configurations
description: Cet article vous explique comment utiliser des instructions et des boucles conditionnelles pour rendre votre configuration plus dynamique. La combinaison d’instructions et de boucles conditionnelles avec des paramètres et des Données de configuration vous offre plus de souplesse et de contrôle lors de la compilation de votre configuration.
ms.openlocfilehash: 7af8a360c17a0842fa2b95d1d1fb288323c327ef
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658456"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>Boucles et instructions conditionnelles dans une configuration

Vous pouvez rendre votre [configuration](configurations.md) plus dynamique à l’aide de mots clés de contrôle de flux de PowerShell. Cet article vous explique comment utiliser des instructions et des boucles conditionnelles pour rendre vos `Configuration` plus dynamiques. La combinaison d’instructions et de boucles conditionnelles avec des [paramètres](add-parameters-to-a-configuration.md) et des [Données de configuration](configData.md) vous offre plus de souplesse et de contrôle lors de la compilation de vos `Configuration`.

Comme pour une fonction ou un bloc de script, vous pouvez utiliser n’importe quelle fonctionnalité de langage PowerShell au sein d’une `Configuration`. Les instructions que vous utilisez seront évaluées uniquement lorsque vous appelez votre `Configuration` pour compiler un fichier `.mof`. Les exemples ci-dessous montrent des scénarios pour illustrer des concepts. Les instructions et les boucles conditionnelles sont plus souvent utilisées avec des paramètres et des Données de configuration.

Dans cet exemple simple, le bloc de ressources **Service** récupère l’état actuel d’un service au moment de la compilation pour générer un fichier `.mof` qui conserve son état actuel.

> [!NOTE]
> L’utilisation de blocs de ressources dynamiques sera plus efficace qu’IntelliSense. L’analyseur PowerShell ne peut pas déterminer si les valeurs spécifiées sont acceptables tant que `Configuration` n’a pas été compilée.

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

En outre, vous pouvez créer un bloc de ressources **Service** pour chaque service sur l’ordinateur actuel à l’aide d’une boucle `foreach`.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
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

Vous pouvez également créer un `Configuration` uniquement pour les ordinateurs qui sont en ligne à l’aide d’une instruction `if`.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> Les blocs de ressources dynamiques des exemples ci-dessus font référence à l’ordinateur actuel. Dans ce cas, il s’agit de l’ordinateur sur lequel vous créez `Configuration` et non pas le nœud cible.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Résumé

En résumé, vous pouvez utiliser n’importe quelle fonctionnalité de langage PowerShell au sein d’une `Configuration`.

Cela inclut des éléments tels que :

- Objets personnalisés
- Tables de hachage
- Manipulation de chaîne
- Communication à distance
- WMI et CIM
- Objets ActiveDirectory
- Etc.

Tout code PowerShell défini dans une `Configuration` sera évalué lors d’une compilation, mais vous pouvez également placer le code dans le script contenant votre `Configuration`. Tout code en dehors du bloc `Configuration` est exécuté lorsque vous importez votre `Configuration`.

## <a name="see-also"></a>Voir aussi

- [Ajouter des paramètres à une configuration](add-parameters-to-a-configuration.md)
- [Séparer des données de configuration des configurations](configData.md)
