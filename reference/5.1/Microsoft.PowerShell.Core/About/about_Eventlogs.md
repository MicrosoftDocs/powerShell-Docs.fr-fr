---
description: Windows PowerShell crée un journal des événements Windows nommé « Windows PowerShell » pour enregistrer les événements Windows PowerShell. Vous pouvez consulter ce journal dans observateur d’événements ou en utilisant des applets de commande qui obtiennent des événements, tels que l’applet de commande `Get-EventLog` . Par défaut, les événements du moteur et du fournisseur Windows PowerShell sont enregistrés dans le journal des événements, mais vous pouvez utiliser les variables de préférence du journal des événements pour personnaliser le journal des événements. Par exemple, vous pouvez ajouter des événements sur les commandes Windows PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_eventlogs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Eventlogs
ms.openlocfilehash: eb92333c6a6e220e287dcbec1441d2d05aa9275b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208041"
---
# <a name="about-eventlogs"></a>À propos des EventLog

## <a name="short-description"></a>Description courte

Windows PowerShell crée un journal des événements Windows nommé « Windows PowerShell » pour enregistrer les événements Windows PowerShell. Vous pouvez consulter ce journal dans observateur d’événements ou en utilisant des applets de commande qui obtiennent des événements, tels que l’applet de commande `Get-EventLog` . Par défaut, les événements du moteur et du fournisseur Windows PowerShell sont enregistrés dans le journal des événements, mais vous pouvez utiliser les variables de préférence du journal des événements pour personnaliser le journal des événements. Par exemple, vous pouvez ajouter des événements sur les commandes Windows PowerShell.

## <a name="long-description"></a>Description longue

Le journal des événements Windows PowerShell enregistre les détails des opérations Windows PowerShell, telles que le démarrage et l’arrêt du moteur du programme, ainsi que le démarrage et l’arrêt des fournisseurs Windows PowerShell. Vous pouvez également consigner des détails sur les commandes Windows PowerShell.

Le journal des événements Windows PowerShell se trouve dans le groupe journaux des applications et des services. Le journal Windows PowerShell est un journal des événements classique qui n’utilise pas la technologie d’événements Windows. Pour afficher le journal, utilisez les applets de commande conçues pour les journaux des événements classiques, tels que `Get-EventLog` .

## <a name="viewing-the-windows-powershell-event-log"></a>Affichage du journal des événements Windows PowerShell

Vous pouvez consulter le journal des événements Windows PowerShell dans observateur d’événements ou à l’aide des `Get-EventLog` applets de commande et `Get-WmiObject` . Pour afficher le contenu du journal Windows PowerShell, tapez :

```powershell
Get-EventLog -LogName "Windows PowerShell"
```

Pour examiner les événements et leurs propriétés, utilisez l' `Sort-Object` applet de commande, l’applet de commande `Group-Object` et les applets de commande qui contiennent le `Format` verbe (les `Format` applets de commande).

Par exemple, pour afficher les événements du journal regroupés par ID d’événement, tapez :

```powershell
Get-EventLog "Windows PowerShell" | Format-Table -GroupBy EventID
```

Ou tapez :

```powershell
Get-EventLog "Windows PowerShell" |
  Sort-Object EventID |
  Group-Object EventID
```

Pour afficher tous les journaux des événements classiques, tapez :

```powershell
Get-EventLog -List
```

Vous pouvez également utiliser l' `Get-WmiObject` applet de commande pour utiliser les classes de Windows Management Instrumentation d’événements (WMI) pour examiner le journal des événements. Par exemple, pour afficher toutes les propriétés du fichier journal des événements, tapez :

```powershell
Get-WmiObject Win32_NTEventlogFile |
  where LogFileName -EQ "Windows PowerShell" |
  Format-List -Property *
```

Pour rechercher les classes WMI liées aux événements Win32, tapez :

```powershell
Get-WmiObject -List | where Name -Like "win32*event*"
```

Pour plus d’informations, tapez « obtenir-Help obtenir-EventLog » et « obtenir-Help obtenir-WmiObject ».

## <a name="selecting-events-for-the-windows-powershell-event-log"></a>Sélection d’événements pour le journal des événements Windows PowerShell

Vous pouvez utiliser les variables de préférence du journal des événements pour déterminer les événements qui sont enregistrés dans le journal des événements Windows PowerShell.

Il existe six variables de préférence du journal des événements : deux variables pour chacun des trois composants de journalisation : le moteur (le programme Windows PowerShell), les fournisseurs et les commandes. Les variables LifeCycleEvent journalisent les événements de démarrage et d’arrêt normaux. Les variables d’intégrité journalisent les événements d’erreur.

Le tableau suivant répertorie les variables de préférence du journal des événements.

|Variable                  |Description                                    |
|--------------------------|-----------------------------------------------|
|$LogEngineLifeCycleEvent  |Enregistre le démarrage et l’arrêt de PowerShell          |
|$LogEngineHealthEvent     |Journalise les erreurs de programme PowerShell                 |
|$LogProviderLifeCycleEvent|Enregistre le démarrage et l’arrêt des fournisseurs PowerShell|
|$LogProviderHealthEvent   |Journalise les erreurs du fournisseur PowerShell                |
|$LogCommandLifeCycleEvent |Enregistre le début et la fin des commandes   |
|$LogCommandHealthEvent    |Journalise les erreurs de commande                            |

(Pour plus d’informations sur les fournisseurs Windows PowerShell, consultez [about_Providers](about_Providers.md).)

Par défaut, seuls les types d’événements suivants sont activés :

* $LogEngineLifeCycleEvent
* $LogEngineHealthEvent
* $LogProviderLifeCycleEvent
* $LogProviderHealthEvent

Pour activer un type d’événement, définissez la variable de préférence pour ce type d’événement sur $true. Par exemple, pour activer les événements de cycle de vie de commande, tapez :

```powershell
$LogCommandLifeCycleEvent
```

Ou tapez :

```powershell
$LogCommandLifeCycleEvent = $true
```

Pour désactiver un type d’événement, définissez la variable de préférence pour ce type d’événement sur $false. Par exemple, pour désactiver les événements de cycle de vie de commande, tapez :

```powershell
$LogProviderLifeCycleEvent = $false
```

Vous pouvez désactiver n’importe quel événement, à l’exception des événements qui indiquent que le moteur Windows PowerShell et les fournisseurs de base sont démarrés. Ces événements sont générés avant l’exécution des profils Windows PowerShell et avant que le programme hôte soit prêt à accepter les commandes.

Les paramètres de variable s’appliquent uniquement à la session Windows PowerShell active.
Pour les appliquer à toutes les sessions Windows PowerShell, ajoutez-les à votre profil Windows PowerShell.

## <a name="logging-module-events"></a>Journalisation des événements du module

À compter de Windows PowerShell 3,0, vous pouvez enregistrer les événements d’exécution des applets de commande et des fonctions dans les modules et les composants logiciels enfichables Windows PowerShell en affectant la valeur TRUE à la propriété LogPipelineExecutionDetails des modules et des composants logiciels enfichables. Dans Windows PowerShell 2,0, cette fonctionnalité est disponible uniquement pour les composants logiciels enfichables.

Lorsque la valeur de la propriété LogPipelineExecutionDetails est TRUE ( `$true` ), Windows PowerShell écrit les événements d’exécution des applets de commande et des fonctions dans la session dans le journal Windows PowerShell dans observateur d’événements. Le paramètre est effectif uniquement dans la session active.

Pour activer la journalisation des événements d’exécution des applets de commande et des fonctions dans un module, utilisez la séquence de commandes suivante.

```powershell
Import-Module <ModuleName>
$m = Get-Module <ModuleName>
$m.LogPipelineExecutionDetails = $true
```

Pour activer la journalisation des événements d’exécution des applets de commande dans un composant logiciel enfichable, utilisez la séquence de commandes suivante.

```powershell
$m = Get-PSSnapin <SnapInName> [-Registered]
$m.LogPipelineExecutionDetails = $True
```

Pour désactiver la journalisation, utilisez la même séquence de commandes pour définir la valeur de la propriété sur FALSe ( `$false` ).

Vous pouvez également utiliser le paramètre de stratégie de groupe activer la journalisation des modules pour activer et désactiver la journalisation des modules et des composants logiciels enfichables. La valeur de la stratégie comprend une liste de noms de modules et de composants logiciels enfichables. Les caractères génériques sont pris en charge.

Lorsque l’opération « activer la journalisation des modules » est définie pour un module, la valeur de la propriété LogPipelineExecutionDetails du module est TRUE dans toutes les sessions et ne peut pas être modifiée.

Le paramètre de stratégie de groupe activer la journalisation du module se trouve dans les chemins d’accès stratégie de groupe suivants :

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
     Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

La stratégie de configuration utilisateur est prioritaire sur la stratégie de configuration de l’ordinateur, et les deux stratégies prennent la préférence sur la valeur de la propriété LogPipelineExecutionDetails des modules et des composants logiciels enfichables.

Pour plus d’informations sur ce paramètre de stratégie de groupe, consultez [about_Group_Policy_Settings](about_Group_Policy_Settings.md).

## <a name="security-and-auditing"></a>Sécurité et audit

Le journal des événements Windows PowerShell est conçu pour indiquer l’activité et pour fournir des détails opérationnels pour la résolution des problèmes.

Toutefois, comme la plupart des journaux des événements des applications Windows, le journal des événements de Windows PowerShell n’est pas conçu pour être sécurisé. Elle ne doit pas être utilisée pour auditer la sécurité ou pour enregistrer des informations confidentielles ou propriétaires.

Les journaux d’événements sont conçus pour être lus et compris par les utilisateurs. Les utilisateurs peuvent lire et écrire dans le journal. Un utilisateur malveillant peut lire un journal des événements sur un ordinateur local ou distant, enregistrer les fausses données, puis empêcher la journalisation de leurs activités.

## <a name="notes"></a>Notes

Les auteurs des auteurs de module peuvent ajouter des fonctionnalités de journalisation à leurs modules. Pour plus d’informations, consultez [écriture d’un module Windows PowerShell](/powershell/scripting/developer/module/writing-a-windows-powershell-module).

## <a name="see-also"></a>Voir aussi

[Get-EventLog](xref:Microsoft.PowerShell.Management.Get-EventLog)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Preference_Variables](about_Preference_Variables.md)
