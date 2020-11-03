---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-computersecurechannel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ComputerSecureChannel
ms.openlocfilehash: 20ea76e725a8ab53d7090078dc819a6297a639ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203458"
---
# Test-ComputerSecureChannel

## SYNOPSIS
Teste et répare le canal sécurisé entre l'ordinateur local et son domaine.

## SYNTAX

```
Test-ComputerSecureChannel [-Repair] [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description
L’applet de commande **Test-ComputerSecureChannel** vérifie que le canal entre l’ordinateur local et son domaine fonctionne correctement en vérifiant l’état de ses relations d’approbation.
Si une connexion échoue, vous pouvez utiliser le paramètre *Repair* pour essayer de la restaurer.

**Test-ComputerSecureChannel** retourne $true si le canal fonctionne correctement et $false si ce n’est pas le cas.
Ce résultat vous permet d’utiliser l’applet de commande dans des instructions conditionnelles dans des fonctions et des scripts.
Pour obtenir des résultats de test plus détaillés, utilisez le paramètre *Verbose* .

Cette applet de commande fonctionne un peu comme NetDom.exe.
NetDom et **Test-ComputerSecureChannel** utilisent tous deux le service **Netlogon** pour effectuer les actions.

## EXEMPLES

### Exemple 1 : tester un canal entre l’ordinateur local et son domaine

```
PS C:\> Test-ComputerSecureChannel
True
```

Cette commande teste le canal entre l’ordinateur local et le domaine auquel il est joint.

### Exemple 2 : tester un canal entre l’ordinateur local et un contrôleur de domaine

```
PS C:\> Test-ComputerSecureChannel -Server "DCName.fabrikam.com"
True
```

Cette commande spécifie un contrôleur de domaine par défaut pour le test.

### Exemple 3 : réinitialisation du canal entre l’ordinateur local et son domaine

```
PS C:\> Test-ComputerSecureChannel -Repair
True
```

Cette commande réinitialise le canal entre l’ordinateur local et son domaine.

### Exemple 4 : afficher des informations détaillées sur le test

```
PS C:\> Test-ComputerSecureChannel -verbose
VERBOSE: Performing operation "Test-ComputerSecureChannel" on Target "SERVER01".
True
VERBOSE: "The secure channel between 'SERVER01' and 'net.fabrikam.com' is alive and working correctly."
```

Cette commande utilise le paramètre commun *Verbose* pour demander des messages détaillés sur l’opération.
Pour plus d’informations sur les *Commentaires* , consultez about_CommonParameters.

### Exemple 5 : tester une connexion avant d’exécuter un script

```
PS C:\> Set-Alias tcsc Test-ComputerSecureChannel
if (!(tcsc))
{Write-Host "Connection failed. Reconnect and retry."}
else { &(.\Get-Servers.ps1) }
```

Cet exemple montre comment utiliser **Test-ComputerSecureChannel** pour tester une connexion avant d’exécuter un script qui requiert la connexion.

La première commande utilise l’applet de commande Set-Alias pour créer un alias pour le nom de l’applet de commande.
Cela permet d’économiser de l’espace et d’éviter les erreurs de frappe.

L’instruction **If** vérifie la valeur retournée par **Test-ComputerSecureChannel** avant d’exécuter un script.

## PARAMETERS

### -Credential
Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.
Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui retourné par l’applet de commande Get-Credential.
Par défaut, l'applet de commande utilise les informations d'identification de l'utilisateur actuel.

Le paramètre *Credential* est conçu pour être utilisé dans les commandes qui utilisent le paramètre *Repair* pour réparer le canal entre l’ordinateur et le domaine.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Repair
Indique que cette applet de commande supprime, puis reconstruit le canal établi par le service Netlogon.
Utilisez ce paramètre pour essayer de restaurer une connexion dont le test a échoué.

Pour utiliser ce paramètre, l’utilisateur actuel doit être membre du groupe Administrateurs sur l’ordinateur local.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Server
Spécifie le contrôleur de domaine pour exécuter la commande.
Si ce paramètre n’est pas spécifié, cette applet de commande sélectionne un contrôleur de domaine par défaut pour l’opération.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System.Boolean
Cette applet de commande retourne $True si la connexion fonctionne correctement et $False si elle ne l’est pas.

## REMARQUES

* Pour exécuter une commande **Test-ComputerSecureChannel** sur Windows Vista et les versions ultérieures du système d’exploitation Windows, ouvrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.
* **Test-ComputerSecureChannel** est implémenté à l’aide de la fonction **I_NetLogonControl2** , qui contrôle différents aspects du service Netlogon.

## LIENS CONNEXES

[Checkpoint-Computer](Checkpoint-Computer.md)

[Reset-ComputerMachinePassword](Reset-ComputerMachinePassword.md)

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
