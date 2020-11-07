---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 15aca668be08324f17a2a737214ede309370adf1
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342125"
---
# Get-HotFix

## SYNOPSIS
Obtient les correctifs logiciels installés sur les ordinateurs locaux ou distants.

## SYNTAXE

### Valeur par défaut (par défaut)

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### Description

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## DESCRIPTION

L' `Get-Hotfix` applet de commande obtient les correctifs logiciels, ou les mises à jour, qui sont installés sur l’ordinateur local ou les ordinateurs distants spécifiés. Les mises à jour peuvent être installées par Windows Update, Microsoft Update, Windows Server Update Services ou installées manuellement.

## EXEMPLES

### Exemple 1 : récupération de tous les correctifs logiciels sur l’ordinateur local

L' `Get-Hotfix` applet de commande obtient tous les correctifs logiciels installés sur l’ordinateur local.

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### Exemple 2 : obtenir des correctifs à partir de plusieurs ordinateurs filtrés par une chaîne

La `Get-Hotfix` commande utilise des paramètres pour installer les correctifs logiciels sur les ordinateurs distants. Les résultats sont filtrés par une chaîne de description spécifiée.

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

`Get-Hotfix` filtre la sortie avec le paramètre **Description** et la **sécurité** de chaîne incluant le caractère générique astérisque ( `*` ). Le paramètre **ComputerName** contient une chaîne séparée par des virgules de noms d’ordinateurs distants. Le paramètre **Credential** spécifie un compte d’utilisateur qui a l’autorisation d’accéder aux ordinateurs distants et d’exécuter des commandes.

### Exemple 3 : vérifier si une mise à jour est installée et écrire des noms d’ordinateur dans un fichier

Les commandes de cet exemple vérifient si une mise à jour particulière est installée. Si la mise à jour n’est pas installée, le nom de l’ordinateur est écrit dans un fichier texte.

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

La `$A` variable contient les noms d’ordinateur obtenus par `Get-Content` à partir d’un fichier texte. Les objets dans `$A` sont envoyés dans le pipeline à `ForEach-Object` . Une `if` instruction utilise l' `Get-Hotfix` applet de commande avec le paramètre **ID** et un numéro d’ID spécifique pour chaque nom d’ordinateur. Si l’ID de correctif logiciel spécifié n’est pas installé sur l’ordinateur, l' `Add-Content` applet de commande écrit le nom de l’ordinateur dans un fichier.

### Exemple 4 : récupérer le correctif logiciel le plus récent sur l’ordinateur local

Cet exemple obtient le correctif logiciel le plus récent installé sur un ordinateur.

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

`Get-Hotfix` envoie les objets dans le pipeline à l’applet de commande `Sort-Object` . `Sort-Object` trie les objets par ordre croissant et utilise le paramètre **Property** pour évaluer chaque date **InstalledOn** . La notation de tableau `[-1]` sélectionne le correctif logiciel le plus récent installé.

## PARAMÈTRES

### -ComputerName

Spécifie un ordinateur distant. Tapez le nom NetBIOS, une adresse IP (Internet Protocol) ou un nom de domaine complet (FQDN) d’un ordinateur distant.

Lorsque le paramètre **ComputerName** n’est pas spécifié, `Get-Hotfix` s’exécute sur l’ordinateur local.

Le paramètre **ComputerName** ne repose pas sur la communication à distance Windows PowerShell. Si votre ordinateur n’est pas configuré pour exécuter des commandes distantes, utilisez le paramètre **ComputerName** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’accéder à l’ordinateur et d’exécuter des commandes. La valeur par défaut est l’utilisateur actuel

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### Description

`Get-HotFix` utilise le paramètre **Description** pour spécifier les types de correctifs logiciels. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Id

Filtre les `Get-HotFix` résultats pour des ID de correctifs spécifiques. Les caractères génériques ne sont pas acceptés.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### String

Vous pouvez diriger un ou plusieurs noms d’ordinateur vers le correctif logiciel.

## SORTIES

### System. Management. ManagementObject # root\CIMV2\ Win32_QuickFixEngineering

`Get-HotFix` retourne des objets qui représentent les correctifs logiciels sur l’ordinateur.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

La **Win32_QuickFixEngineering** [classe WMI](/windows/desktop/WmiSdk/retrieving-a-class) Win32_QuickFixEngineering représente une petite mise à jour à l’échelle du système, communément appelée mise à jour du correctif QFE (rapide), appliquée au système d’exploitation actuel. Cette classe retourne uniquement les mises à jour fournies par la fonction de maintenance basée sur les composants (CBS). Ces mises à jour ne sont pas répertoriées dans le registre. Les mises à jour fournies par Microsoft Windows Installer (MSI) ou le site [Windows Update](https://update.microsoft.com) ne sont pas retournées par **Win32_QuickFixEngineering**. Pour plus d’informations, consultez [Win32_QuickFixEngineering classe](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).

La `Get-HotFix` sortie peut varier selon les systèmes d’exploitation.

## LIENS CONNEXES

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Add-Content](Add-Content.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Classe Win32_QuickFixEngineering](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
