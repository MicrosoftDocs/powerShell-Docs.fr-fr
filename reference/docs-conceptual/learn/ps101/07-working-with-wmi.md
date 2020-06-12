---
title: Utilisation de WMI
description: PowerShell comprend depuis toujours des applets de commande pour l’utilisation de WMI.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 243685efa1f976ddb46a0d0efc4ed0635844606d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438290"
---
# <a name="chapter-7---working-with-wmi"></a>Chapitre 7 - Utilisation de WMI

## <a name="wmi-and-cim"></a>WMI et CIM

Par défaut, PowerShell est fourni avec des applets de commande permettant d’utiliser d’autres technologies telles que Windows Management Instrumentation (WMI). Il existe plusieurs applets de commande WMI natives dans PowerShell. Il n’est donc pas nécessaire d’installer d’autres logiciels ou modules.

PowerShell comprend depuis toujours des applets de commande pour l’utilisation de WMI. Vous pouvez utiliser `Get-Command` pour connaître les applets de commande WMI qui existent dans PowerShell. Les résultats suivants proviennent de mon ordinateur Windows 10 Lab Environment sur lequel j’exécute PowerShell version 5.1. Vos résultats peuvent différer selon la version de PowerShell que vous exécutez.

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

Les applets de commande CIM (Common Information Model) datent de la version 3.0 de PowerShell. Les applets de commande CIM sont conçues pour être utilisées sur des ordinateurs Windows et non Windows. Les applets de commande WMI sont aujourd’hui dépréciées, c’est pourquoi je vous recommande d’utiliser les applets de commande CIM à la place des anciennes WMI.

Les applets de commande CIM sont toutes contenues dans un module. Pour obtenir la liste des applets de commande CIM, utilisez `Get-Command` avec le paramètre **Module**, comme indiqué dans l’exemple suivant.

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

Les applets de commande CIM vous permettent toujours d’utiliser WMI. Ne soyez donc pas surpris si vous entendez quelqu’un dire : « Quand j’interroge WMI avec les applets de commande CIM PowerShell... »

Comme je l’ai déjà mentionné, WMI est une technologie distincte de PowerShell. Les applets de commande CIM vous permettent simplement d’accéder à WMI. Vous pouvez tomber sur un ancien VBScript qui utilise le langage de requêtes WMI (WQL) pour interroger WMI, comme dans l’exemple suivant.

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

Vous pouvez exécuter la requête WQL à partir de ce VBScript et l’utiliser avec l’applet de commande `Get-CimInstance` sans aucune modification.

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

Ce n’est pas comme ça que je m’y prends généralement pour interroger WMI avec PowerShell. Cela dit, cette méthode fonctionne et elle vous permet d’effectuer facilement la migration des scripts VBScript existants vers PowerShell. Lorsque je commence à écrire une ligne de code pour interroger WMI, j’utilise la syntaxe suivante.

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

Si je veux uniquement le numéro de série, je peux rediriger la sortie vers `Select-Object` et spécifier uniquement la propriété **SerialNumber**.

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

Par défaut, plusieurs propriétés sont récupérées en arrière-plan et ne sont jamais utilisées.
Cela peut ne pas avoir d’importance lorsque vous interrogez WMI sur un ordinateur local. Toutefois, une fois que vous commencez à interroger des ordinateurs distants, non seulement vous utilisez du temps de traitement supplémentaire pour obtenir les informations dont vous avez besoin, mais en plus, vous récupérez sur le réseau d’autres informations dont vous n’avez pas besoin. `Get-CimInstance` a un paramètre **Property** qui limite la quantité d’informations récupérées. Cela rend l’interrogation de WMI plus efficace.

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

Les résultats précédents ont retourné un objet. Pour retourner une chaîne simple, utilisez le paramètre **ExpandProperty**.

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

Vous pouvez également utiliser le style de syntaxe en pointillés pour retourner une chaîne simple. Cela vous évite d’avoir à rediriger les données vers `Select-Object`.

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a>Interroger des ordinateurs distants avec les applets de commande CIM

J’exécute toujours PowerShell en tant qu’administrateur local et utilisateur de domaine. Lorsque j’essaie d’interroger des informations à partir d’un ordinateur distant à l’aide de l’applet de commande `Get-CimInstance`, je reçois un message d’erreur de type Accès refusé.

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

De nombreux utilisateurs de PowerShell ont des inquiétudes quant à la sécurité. Pourtant, les autorisations PowerShell sont exactement les mêmes que celles de l’interface graphique utilisateur. Exactement les mêmes. Dans l’exemple précédent, le problème vient du fait que l’utilisateur qui exécute PowerShell ne dispose pas des droits nécessaires pour interroger les informations WMI à partir du serveur DC01. Je pourrais relancer PowerShell en tant qu’administrateur de domaine, puisque `Get-CimInstance` n’a pas de paramètre **Credential**. Cela dit, ce n’est vraiment pas une bonne idée, car cela signifierait que tout ce que j’exécute à partir de PowerShell le serait en tant qu’administrateur de domaine. Et selon la situation, cela pourrait engendrer d’importants risques de sécurité.

Si j’utilise le principe du « privilège minimum », je peux appliquer les privilèges de mon compte d’administrateur de domaine au niveau d’une seule commande, à l’aide du paramètre **Credential**, si la commande dispose de ce paramètre. `Get-CimInstance` n’a pas de paramètre **Credential**. Dans ce scénario, la solution consiste donc à créer d’abord un **CimSession**. J’utilise ensuite **CimSession** à la place d’un nom d’ordinateur pour interroger WMI sur l’ordinateur distant.

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

La session CIM a été stockée dans une variable nommée `$CimSession`. Notez que j’ai également spécifié l’applet de commande `Get-Credential` entre parenthèses pour qu’elle s’exécute en premier, en m’invitant à fournir d’autres informations d’identification avant de créer la nouvelle session. Plus loin dans ce chapitre, je vous montrerai une méthode plus efficace pour spécifier d’autres informations d’identification. Toutefois, il est important de comprendre ce concept de base avant qu’il ne devienne plus complexe.

La session CIM créée dans l’exemple précédent peut désormais être utilisée avec l’applet de commande `Get-CimInstance` pour interroger les informations du BIOS à partir de WMI sur l’ordinateur distant.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

L’utilisation des sessions CIM présente plusieurs avantages par rapport au simple fait de spécifier un nom d’ordinateur. Lorsque vous exécutez plusieurs requêtes sur un même ordinateur, l’utilisation d’une session CIM est plus efficace que le fait d’utiliser le nom de l’ordinateur pour chaque requête. La création d’une session CIM ne configure la connexion qu’une seule fois.
Ensuite, plusieurs requêtes utilisent cette même session pour récupérer des informations. L’utilisation du nom de l’ordinateur nécessite que les applets de commande configurent et suppriment la connexion pour chaque requête.

L’applet de commande `Get-CimInstance` utilise le protocole WSMan par défaut, ce qui signifie que l’ordinateur distant a besoin de PowerShell version 3.0 ou ultérieure pour se connecter. En fait, ce n’est pas la version de PowerShell qui importe, mais la version de la pile. Pour connaître la version de la pile, utilisez l’applet de commande `Test-WSMan`.
Il doit s’agir de la version 3.0. Il s’agit de la version que vous trouverez avec PowerShell version 3.0 et versions ultérieures.

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

Les anciennes applets de commande WMI utilisent le protocole DCOM, qui est compatible avec les versions antérieures de Windows. Toutefois, DCOM est généralement bloqué par le Pare-feu sur les versions récentes de Windows. L’applet de commande `New-CimSessionOption` vous permet de créer une connexion via le protocole DCOM, en vue de l’utiliser avec `New-CimSession`. Cela vous permet d’utiliser l’applet de commande `Get-CimInstance` pour communiquer avec les versions de Windows antérieures à Windows Server 2000. Cela signifie également que PowerShell n’est pas nécessaire sur l’ordinateur distant lorsque vous utilisez l’applet de commande `Get-CimInstance` avec un CimSession qui est configuré pour utiliser le protocole DCOM.

Créez l’option de protocole DCOM à l’aide de l’applet de commande `New-CimSessionOption` et stockez-la dans une variable.

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

Pour plus d’efficacité, vous pouvez stocker vos informations d’identification d’administrateur de domaine (ou avec privilèges élevés) dans une variable afin de ne pas avoir à les entrer pour chaque commande.

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

J’ai un serveur nommé SQL03 qui exécute Windows Server 2008 (non R2). Il s’agit du plus récent des systèmes d’exploitation Windows Server sur lesquels PowerShell n’est pas installé par défaut.

Créez un **CimSession** pour SQL03 en utilisant le protocole DCOM.

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

Notez que cette fois-ci, dans la commande précédente, j’ai spécifié la variable nommée `$Cred` comme la valeur du paramètre **Credential**, afin de ne pas avoir à entrer les informations d’identification manuellement une nouvelle fois.

La sortie de la requête est la même, quel que soit le protocole sous-jacent utilisé.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

L’applet de commande `Get-CimSession` est utilisée pour voir quels **CimSessions** sont actuellement connectés et quels protocoles ils utilisent.

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

Récupérez puis stockez les deux **CimSessions** créés précédemment dans une variable nommée `$CimSession`.

```powershell
$CimSession = Get-CimSession
```

Interrogez les deux ordinateurs à l’aide d’une seule commande, l’une utilisant le protocole WSMan et l’autre utilisant le protocole DCOM.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

J’ai écrit de nombreux articles de blog sur les applets de commande WMI et CIM. L’un des plus utiles concerne une fonction que j’ai créée pour déterminer automatiquement quel protocole utiliser entre WSMan et DCOM, et pour configurer la session CIM automatiquement et non manuellement. Cet article de blog est intitulé [PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom][].

Lorsque vous avez terminé une session CIM, vous devez la supprimer avec l’applet de commande `Remove-CimSession`. Pour supprimer toutes les sessions CIM, il suffit de rediriger `Get-CimSession` vers `Remove-CimSession`.

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a>Résumé

Dans ce chapitre, vous avez vu comment vous servir de PowerShell pour utiliser WMI sur des ordinateurs locaux et distants. Vous avez également vu comment utiliser les applets de commande CIM pour travailler sur des ordinateurs distants avec le protocole WSMan ou DCOM.

## <a name="review"></a>Révision

1. Quelle est la différence entre les applets de commande WMI et les applets de commande CIM ?
1. Par défaut, quel protocole l’applet de commande `Get-CimInstance` utilise-t-elle ?
1. Quels sont les avantages de l’utilisation d’une session CIM par rapport à la spécification d’un nom d’ordinateur avec `Get-CimInstance` ?
1. Comment spécifier un protocole autre que celui par défaut avec `Get-CimInstance` ?
1. Comment fermer ou supprimer des sessions CIM ?

## <a name="recommended-reading"></a>Lecture recommandée

- [about_WMI][]
- [about_WMI_Cmdlets][]
- [about_WQL][]
- [Module CimCmdlets][]
- [Vidéo : Utilisation des applets de commande CIM et des sessions CIM][]

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[Module CimCmdlets]: /powershell/module/cimcmdlets/
[Vidéo : Utilisation des applets de commande CIM et des sessions CIM]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
