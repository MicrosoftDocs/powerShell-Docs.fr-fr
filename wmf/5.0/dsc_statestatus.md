---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 7b4e4dbeaf9c3c48e7b2dfc74435dfa2cd9c7ea7
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2018
---
# <a name="unified-and-consistent-state-and-status-representation"></a>État unifié et cohérent et représentation de l’état

Une série d’améliorations ont été apportées dans cette version pour l’état du gestionnaire de configuration local et le statut DSC générés par des automatisations. Il s’agit notamment de représentations de l’état et du statut unifiées et cohérentes, d’une propriété d’heure et de date facile à gérer pour les objets de statut retournés par l’applet de commande Get-DscConfigurationStatus, et d’une propriété améliorée pour les détails sur l’état du gestionnaire de configuration local retournés par l’applet de commande Get-DscLocalConfigurationManager.

La représentation de l’état du gestionnaire de configuration local et du statut de l’opération DSC a été revisitée et unifiée conformément aux règles suivantes :
1.  La ressource NotProcessed n’affecte pas l’état du gestionnaire de configuration local et le statut DSC.
2.  Le gestionnaire de configuration local cesse de traiter les ressources dès qu’il en rencontre une qui demande un redémarrage.
3.  Une ressource qui demande un redémarrage n’est pas à l’état souhaité tant que le redémarrage n’a pas eu lieu.
4.  Après avoir rencontré une ressource qui échoue, le gestionnaire de configuration local continue à traiter les ressources tant qu’elles ne sont pas dépendantes de celle qui a échoué.
5.  Le statut global retourné par l’applet de commande Get-DscConfigurationStatus est le surensemble du statut de toutes les ressources.
6.  L’état PendingReboot est un surensemble de l’état PendingConfiguration.

Le tableau ci-dessous illustre les propriétés d’état et de statut résultantes dans quelques scénarios classiques.

| Scénario                    | LCMState       | Statut | Redémarrage demandé  | ResourcesInDesiredState  | ResourcesNotInDesiredState |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S**^**                          | Idle                 | Opération réussie    | $false        | S                            | $null                          |
| F**^**                          | PendingConfiguration | Échec    | $false        | $null                        | F                              |
| S,F                             | PendingConfiguration | Échec    | $false        | S                            | F                              |
| F,S                             | PendingConfiguration | Échec    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Échec    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Échec    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Opération réussie    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | Échec    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Opération réussie    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Opération réussie    | $true         | $null                        | r                              |

^ S<sub>i</sub> : série de ressources appliquée avec succès F<sub>i</sub> : série de ressources appliquée sans succès r : ressource qui nécessite un redémarrage \*

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Améliorations apportées à l’applet de commande Get-DscConfigurationStatus

Quelques améliorations ont été apportées à l’applet de commande Get-DscConfigurationStatus dans cette version. Auparavant, la propriété StartDate des objets retournés par l’applet de commande était de type String. Elle est désormais de type Datetime, ce qui simplifie la sélection et le filtrage complexes basés sur les propriétés intrinsèques d’un objet Datetime.

```powershell
(Get-DscConfigurationStatus).StartDate | fl *
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

Voici un exemple qui retourne tous les enregistrements d’opérations DSC qui se sont produits, à ce jour, le même jour de la semaine.

```powershell
(Get-DscConfigurationStatus –All) | where { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Les enregistrements d’opérations qui ne modifient pas la configuration du nœud (par exemple les opérations en lecture seule) sont éliminés. Ainsi, les opérations Test-DscConfiguration et Get-DscConfiguration ne sont plus frelatées dans les objets retournés à partir de l’applet de commande Get-DscConfigurationStatus.
Les enregistrements de l’opération de définition de métaconfiguration sont ajoutés au retour de l’applet de commande Get-DscConfigurationStatus.

Voici un exemple de résultat retourné par l’applet de commande Get-DscConfigurationStatus –All.

```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a>Amélioration apportée à l’applet de commande Get-DscLocalConfigurationManager

Un nouveau champ LCMStateDetail a été ajouté à l’objet retourné à partir de l’applet de commande Get-DscLocalConfigurationManager. Ce champ est renseigné quand LCMState est « Occupé ». Vous pouvez le récupérer avec l’applet de commande suivante :

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Voici un exemple de sortie d’une surveillance continue sur une configuration qui nécessite deux redémarrages sur un nœud distant.

```powershell
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
