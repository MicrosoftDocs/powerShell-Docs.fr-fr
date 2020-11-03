---
description: Windows Management Instrumentation (WMI) utilise le Common Information Model (CIM) pour représenter les systèmes, applications, réseaux, périphériques et autres composants gérables de l’entreprise moderne.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI
ms.openlocfilehash: d24b952ee167e51815d6d9920e95bbc9a6bb9608
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207890"
---
# <a name="about-wmi"></a>À propos de WMI

## <a name="short-description"></a>DESCRIPTION COURTE

Windows Management Instrumentation (WMI) utilise le Common Information Model (CIM) pour représenter les systèmes, applications, réseaux, périphériques et autres composants gérables de l’entreprise moderne.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Windows Management Instrumentation (WMI) est l’implémentation par Microsoft de Web-Based Enterprise Management (WBEM), la norme du secteur.

WMI classique utilise DCOM pour communiquer avec les appareils en réseau afin de gérer les systèmes distants. Windows PowerShell 3,0 introduit un modèle de fournisseur CIM qui utilise WinRM pour supprimer la dépendance sur DCOM. Ce modèle de fournisseur CIM utilise également de nouvelles API de fournisseur WMI qui permettent aux développeurs d’écrire des applets de commande Windows PowerShell en code natif (C \+ \+ ).

Ne confondez pas les fournisseurs WMI avec les fournisseurs Windows PowerShell. De nombreuses fonctionnalités Windows ont un fournisseur WMI associé qui expose leurs fonctionnalités de gestion. Pour obtenir des fournisseurs WMI, exécutez une requête WMI qui obtient des instances de la classe WMI __Provider, par exemple la requête suivante.

```powershell
Get-WmiObject -Class __Provider
```

## <a name="three-components-of-wmi"></a>TROIS COMPOSANTS DE WMI

Les trois composants suivants de WMI interagissent avec Windows PowerShell : espaces de noms, fournisseurs et classes.

Les espaces de noms WMI organisent les fournisseurs WMI et les classes WMI en groupes de composants associés. De cette façon, elles sont similaires aux espaces de noms .NET Framework.
Les espaces de noms ne sont pas des emplacements physiques, mais ils sont plus similaires aux bases de données logiques.
Tous les espaces de noms WMI sont des instances de la classe système __Namespace. L’espace de noms WMI par défaut est root \/ cimv2 (depuis Microsoft Windows 2000). Pour utiliser Windows PowerShell afin d’obtenir les espaces de noms WMI dans la session active, utilisez une commande au format suivant.

```powershell
Get-WmiObject -Class __Namespace
```

Pour récupérer les espaces de noms WMI dans d’autres espaces de noms, utilisez le paramètre Namespace pour modifier l’emplacement de la recherche. La commande suivante recherche les espaces de noms WMI qui résident dans l’espace de noms root/Cimv2/applications.

```powershell
Get-WmiObject -Class __Namespace -Namespace root/CIMv2/applications
```

Les espaces de noms WMI sont hiérarchiques. Par conséquent, l’obtention d’une liste de tous les espaces de noms sur un système particulier requiert l’exécution d’une requête récursive commençant au niveau de l’espace de noms racine.

Les fournisseurs WMI exposent des informations sur les objets Windows gérables. Un fournisseur récupère les données d’un composant et transmet ces données via WMI à une application de gestion, telle que Windows PowerShell. La plupart des fournisseurs WMI sont des fournisseurs dynamiques, ce qui signifie qu’ils obtiennent les données dynamiquement lorsqu’elles sont demandées via l’application de gestion.

## <a name="finding-wmi-classes"></a>RECHERCHE DE CLASSES WMI

Dans une installation par défaut de Windows 8, il y a plus de 1 100 classes WMI dans le \/ Cimv2 racine. Avec ces nombreuses classes WMI, le défi consiste à identifier la classe WMI appropriée à utiliser pour effectuer une tâche spécifique. Windows PowerShell 3,0 offre deux façons de rechercher des classes WMI associées à une rubrique spécifique.

Par exemple, pour rechercher des classes WMI dans l' \\ espace de noms WMI cimv2 racine qui sont liées aux disques, vous pouvez utiliser une requête telle que celle présentée ici.

```powershell
Get-WmiObject -List *disk*
```

Pour rechercher des classes WMI associées à la mémoire, vous pouvez utiliser une requête telle que celle présentée ici.

```powershell
Get-WmiObject -List *memory*
```

Les applets de commande CIM offrent également la possibilité de découvrir des classes WMI. Pour ce faire, utilisez l’applet de commande Get-CIMClass. La commande illustrée ci-dessous répertorie les classes WMI associées à la vidéo.

```powershell
Get-CimClass *video*
```

L’expansion de tabulation fonctionne lorsque vous modifiez les espaces de noms WMI et, par conséquent, l’utilisation de l’expansion de tabulation rend les espaces de noms sous-WMI facilement détectables. Dans l’exemple suivant, l’applet de commande Get-CimClass répertorie les classes WMI associées aux paramètres d’alimentation.
Pour le trouver, tapez l' `root/CIMV2/` espace de noms, puis appuyez plusieurs fois sur la touche Tab jusqu’à ce que l’espace de noms Power apparaisse. Voici la commande :

```powershell
Get-CimClass *power* -Namespace root/cimv2/power
```
