---
description: Fournit des informations générales sur Windows Management Instrumentation (WMI) et Windows PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI_Cmdlets
ms.openlocfilehash: c2099c005cedf64e9621d66d6757419320c9b43e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207882"
---
# <a name="about-wmi-cmdlets"></a>À propos des applets de commande WMI

## <a name="short-description"></a>DESCRIPTION COURTE

Fournit des informations générales sur Windows Management Instrumentation (WMI) et Windows PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Cette rubrique fournit des informations sur la technologie WMI, les applets de commande WMI pour Windows PowerShell, la communication à distance basée sur WMI, les accélérateurs WMI et la résolution des problèmes WMI. Elle propose également des liens vers d'autres informations sur WMI.

### <a name="about-wmi"></a>À PROPOS DE WMI

WMI est l’implémentation Microsoft de WBEM (Web-Based Enterprise Management), qui est une initiative de l’industrie pour développer une technologie standard permettant d’accéder aux informations de gestion dans un environnement d’entreprise. WMI utilise la norme industrielle CIM (Common Information Model) pour représenter les systèmes, applications, réseaux, périphériques et autres composants managés. La norme CIM est développée et gérée par Distributed Management Task Force (DMTF). Vous pouvez utiliser WMI pour gérer les ordinateurs locaux et distants. Par exemple, vous pouvez utiliser WMI pour effectuer les opérations suivantes :

- Démarrez un processus sur un ordinateur distant.
- Redémarrez un ordinateur à distance.
- Obtenir la liste des applications installées sur un ordinateur local ou distant.
- Interrogez les journaux des événements Windows sur un ordinateur local ou distant.

### <a name="the-wmi-cmdlets-for-windows-powershell"></a>APPLETS DE COMMANDE WMI POUR WINDOWS POWERSHELL

Windows PowerShell implémente les fonctionnalités WMI via un ensemble d’applets de commande qui sont disponibles dans Windows PowerShell par défaut. Vous pouvez utiliser ces applets de commande pour effectuer les tâches de bout en bout nécessaires à la gestion des ordinateurs locaux et distants.

Les applets de commande WMI suivantes sont incluses.

|Applet de commande           |Description                                   |
|-----------------|----------------------------------------------|
|Get-WmiObject    |Obtient des instances de classes ou d’informations WMI  |
|                 |sur les classes disponibles.                  |
|Invoke-WmiMethod |Appelle les méthodes WMI.                            |
|Register-WmiEvent|S’abonne à un événement WMI.                    |
|Remove-WmiObject |Supprime des instances et des classes WMI.            |
|Set-WmiInstance  |Crée ou modifie des instances de classes WMI. |

### <a name="sample-commands"></a>EXEMPLES DE COMMANDES
La commande suivante affiche les informations du BIOS de l’ordinateur local.

```powershell
C:\PS> get-wmiobject win32_bios | format-list *
```

La commande suivante affiche des informations sur le service WinRM pour trois ordinateurs distants.

```powershell
$wql = "select * from win32_service where name='WinRM'"
get-wmiobject -query $wql -computername server01, server01, server03
```

La commande plus complexe suivante quitte toutes les instances d’un programme.

```powershell
C:\PS> notepad.exe
C:\PS> $wql = "select * from win32_process where name='notepad.exe'"
C:\PS> $np = get-wmiobject -query $wql
C:\PS> $np | remove-wmiobject
```

### <a name="wmi-based-remoting"></a>COMMUNICATION À DISTANCE BASÉE SUR WMI

Bien que la possibilité de gérer un système local via WMI soit utile, il s’agit des fonctionnalités de communication à distance qui rendent WMI un outil d’administration puissant. WMI utilise le modèle DCOM (Distributed Component Object Model) de Microsoft pour se connecter aux systèmes et les gérer. Vous devrez peut-être configurer certains systèmes pour autoriser les connexions DCOM.
Les paramètres de pare-feu et les autorisations DCOM verrouillées peuvent bloquer la capacité de WMI à gérer à distance les systèmes.

### <a name="wmi-type-accelerators"></a>ACCÉLÉRATEURS DE TYPE WMI

Windows PowerShell comprend des accélérateurs de type WMI. Ces accélérateurs de type WMI (raccourcis) permettent un accès plus direct à un objet WMI qu’une approche d’accélérateur sans type.

Les accélérateurs de type suivants sont pris en charge avec WMI :

[WMISEARCHER]-raccourci pour la recherche d’objets WMI.

[WMICLASS]-raccourci pour accéder aux propriétés et méthodes statiques d’une classe.

[WMI]-raccourci pour obtenir une instance unique d’une classe.

[WMISEARCHER] est un accélérateur de type pour un ManagementObjectSearcher. Un constructeur de chaîne peut être utilisé pour créer un programme de recherche dans lequel vous pouvez ensuite effectuer une opération d’extraction () sur.

Par exemple :

```powershell
PS> $s = [WmiSearcher]'Select * from Win32_Process where Handlecount > 1000'
PS> $s.Get() |sort handlecount |ft handlecount,__path,name -auto

count  __PATH                                              name
-----  ------                                              ----
1105   \\SERVER01\root\cimv2:Win32_Process.Handle="3724"   PowerShell...
1132   \\SERVER01\root\cimv2:Win32_Process.Handle="1388"   winlogon.exe
1495   \\SERVER01\root\cimv2:Win32_Process.Handle="2852"   iexplore.exe
1699   \\SERVER01\root\cimv2:Win32_Process.Handle="1204"   OUTLOOK.EXE
1719   \\SERVER01\root\cimv2:Win32_Process.Handle="1912"   iexplore.exe
2579   \\SERVER01\root\cimv2:Win32_Process.Handle="1768"   svchost.exe
```

[WMICLASS] est un accélérateur de type pour ManagementClass. Il a un constructeur de chaîne qui prend un chemin d’accès WMI local ou absolu à une classe WMI et retourne un objet lié à cette classe.

Par exemple :

```powershell
PS> $c = [WMICLASS]"root\cimv2:WIn32_Process"
PS> $c |fl *
Name             : Win32_Process
__GENUS          : 1
__CLASS          : Win32_Process
__SUPERCLASS     : CIM_Process
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Process
__PROPERTY_COUNT : 45
__DERIVATION     : {CIM_Process, CIM_LogicalElement,
                   CIM_ManagedSystemElement}
__SERVER         : SERVER01
__NAMESPACE      : ROOT\cimv2
__PATH           : \\SERVER01\ROOT\cimv2:Win32_Process
```

[WMI] est un accélérateur de type pour ManagementObject. Il a un constructeur de chaîne qui prend un chemin d’accès WMI local ou absolu à une instance WMI et retourne un objet lié à cette instance.

Par exemple :

```powershell
PS> $p = [WMI]'\\SERVER01\root\cimv2:Win32_Process.Handle="1204"'
PS> $p.Name
OUTLOOK.EXE
```

### <a name="wmi-troubleshooting"></a>RÉSOLUTION DES PROBLÈMES WMI

Les problèmes suivants sont les problèmes les plus courants qui peuvent se produire lorsque vous essayez de vous connecter à un ordinateur distant.

Problème 1 : l’ordinateur distant n’est pas en ligne.

Si un ordinateur est hors connexion, vous ne pourrez pas vous y connecter à l’aide de WMI.
Vous pouvez recevoir le message d’erreur suivant :

```
Remote server machine does not exist or is unavailable
```

Si vous recevez ce message d’erreur, vérifiez que l’ordinateur est en ligne. Essayez d’exécuter une commande ping sur l’ordinateur distant.

Problème 2 : vous ne disposez pas de droits d’administrateur local sur l’ordinateur distant.

Pour utiliser WMI à distance, vous devez disposer de droits d’administrateur local sur l’ordinateur distant. Si vous ne le faites pas, l’accès à cet ordinateur sera refusé.

Pour vérifier la sécurité de l’espace de noms :

1. Cliquez sur Démarrer, cliquez avec le bouton droit sur Poste de travail, puis cliquez sur gérer.
2. Dans gestion de l’ordinateur, développez Services et applications, cliquez avec le bouton droit sur contrôle WMI, puis cliquez sur Propriétés.
3. Dans la boîte de dialogue Propriétés du contrôle WMI, cliquez sur l’onglet sécurité.

Problème 3 : un pare-feu bloque l’accès à l’ordinateur distant.

WMI utilise les protocoles DCOM (Distributed COM) et RPC (Remote Procedure Call) pour traverser le réseau. Par défaut, de nombreux pare-feu bloquent le trafic DCOM et RPC. Si votre pare-feu bloque ces protocoles, votre connexion échouera. Par exemple, le pare-feu Windows dans Microsoft Windows XP Service Pack 2 est configuré pour bloquer automatiquement tout le trafic réseau non sollicité, y compris DCOM et WMI. Dans sa configuration par défaut, le pare-feu Windows rejette une demande WMI entrante et vous recevez le message d’erreur suivant :

```
Remote server machine does not exist or is unavailable
```

## <a name="see-also"></a>VOIR AUSSI

[À propos de WMI](/windows/win32/wmisdk/about-wmi)

[Résolution des problèmes WMI](/windows/win32/wmisdk/wmi-troubleshooting)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[Invoke-WmiMethod](xref:Microsoft.PowerShell.Management.Invoke-WmiMethod)

[Register-WmiEvent](xref:Microsoft.PowerShell.Management.Register-WmiEvent)

[Remove-WmiObject](xref:Microsoft.PowerShell.Management.Remove-WmiObject)

[Set-WmiInstance](xref:Microsoft.PowerShell.Management.Set-WmiInstance)
