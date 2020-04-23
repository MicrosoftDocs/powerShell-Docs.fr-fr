---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,installation
title: Boucles et instructions conditionnelles dans les configurations
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736894"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>Boucles et instructions conditionnelles dans une configuration

Vous pouvez rendre votre [configuration](configurations.md) plus dynamique à l’aide de mots clés de contrôle de flux de PowerShell. Cet article vous explique comment utiliser des instructions et des boucles conditionnelles pour rendre vos `Configuration` plus dynamiques. La combinaison d’instructions et de boucles conditionnelles avec des [paramètres](add-parameters-to-a-configuration.md) et des [Données de configuration](configData.md) vous offre plus de souplesse et de contrôle lors de la compilation de vos `Configuration`.

Comme pour une fonction ou un bloc de script, vous pouvez utiliser n’importe quelle fonctionnalité de langage PowerShell au sein d’une `Configuration`.
Les instructions que vous utilisez seront évaluées uniquement lorsque vous appelez votre `Configuration` pour compiler un fichier `.mof`. Les exemples ci-dessous montrent des scénarios pour illustrer des concepts. Les instructions et les boucles conditionnelles sont plus souvent utilisées avec des paramètres et des Données de configuration.

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
- et plus...

Tout code PowerShell défini dans une `Configuration` sera évalué lors d’une compilation, mais vous pouvez également placer le code dans le script contenant votre `Configuration`. Tout code en dehors du bloc `Configuration` est exécuté lorsque vous importez votre `Configuration`.

## <a name="see-also"></a>Voir aussi

- [Ajouter des paramètres à une configuration](add-parameters-to-a-configuration.md)
- [Séparer des données de configuration des configurations](configData.md)
