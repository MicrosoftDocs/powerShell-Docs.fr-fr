---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Boucles et instructions conditionnelles dans les configurations
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080133"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Boucles et instructions conditionnelles dans les configurations

Vous pouvez rendre vos [configurations](configurations.md) plus dynamiques à l’aide de mots clés de contrôle de flux de PowerShell. Cet article vous explique comment utiliser des instructions conditionnelles et des boucles pour rendre vos configurations plus dynamiques. La combinaison d’instructions conditionnelles et de boucles avec des [paramètres](add-parameters-to-a-configuration.md) et des [données de configuration](configData.md) vous offre plus de souplesse et de contrôle lors de la compilation de vos configurations.

Comme pour une fonction ou un bloc de script, vous pouvez utiliser n’importe quel langage PowerShell au sein d’une configuration. Les instructions que vous utilisez seront évaluées uniquement lorsque vous appelez votre configuration pour compiler un fichier « .mof ». Les exemples ci-dessous montrent des scénarios simples pour illustrer des concepts. Les instructions conditionnelles représentent des boucles plus souvent utilisées avec des paramètres et des données de configuration.

Dans cet exemple simple, le bloc de ressources **Service** récupère l’état actuel d’un service au moment de la compilation pour générer un fichier « .mof » qui conserve son état actuel.

> [!NOTE]
> L’utilisation de blocs de ressources dynamiques sera plus efficace qu’IntelliSense. L’analyseur PowerShell ne peut pas déterminer si les valeurs spécifiées sont acceptables tant que la configuration n’a pas été compilée.

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

Vous pouvez également créer uniquement des configurations pour les ordinateurs en ligne à l’aide d’une simple instruction `if`.

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
> Les blocs de ressources dynamiques des exemples ci-dessus font référence à l’ordinateur actuel. Dans ce cas, il s’agit de l’ordinateur sur lequel vous créez la configuration, et non pas le nœud cible.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Résumé

En résumé, vous pouvez utiliser n’importe quel langage PowerShell au sein d’une configuration.

Cela inclut des éléments tels que :

- Objets personnalisés
- Tables de hachage
- Manipulation de chaîne
- Communication à distance
- WMI et CIM
- Objets ActiveDirectory
- et plus...

Tout code PowerShell défini dans une configuration sera évalué lors d’une compilation, mais vous pouvez également placer le code dans le script contenant votre configuration. Tout code en dehors du bloc de configuration sera exécuté lorsque vous importez votre configuration.

## <a name="see-also"></a>Voir aussi

- [Ajouter des paramètres à une configuration](add-parameters-to-a-configuration.md)
- [Séparer des données de configuration des configurations](configData.md)
