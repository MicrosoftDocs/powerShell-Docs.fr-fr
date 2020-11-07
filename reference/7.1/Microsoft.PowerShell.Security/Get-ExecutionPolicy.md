---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: 347ffa733068d4e7f4896eb18358c7a852c88d0a
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347276"
---
# Get-ExecutionPolicy

## SYNOPSIS
Obtient les stratégies d'exécution pour la session active.

## SYNTAXE

### Tous

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## DESCRIPTION

Pour afficher les stratégies d’exécution pour chaque étendue dans l’ordre de priorité, utilisez `Get-ExecutionPolicy -List` . Pour afficher la stratégie d’exécution effective pour votre session PowerShell `Get-ExecutionPolicy` , utilisez sans paramètres.

La stratégie d’exécution effective est déterminée par les stratégies d’exécution définies par `Set-ExecutionPolicy` et stratégie de groupe paramètres.

Pour plus d’informations, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).

## EXEMPLES

### Exemple 1 : récupération de toutes les stratégies d’exécution

Cette commande affiche les stratégies d’exécution pour chaque étendue dans l’ordre de priorité.

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

L' `Get-ExecutionPolicy` applet de commande utilise le paramètre **List** pour afficher la stratégie d’exécution de chaque étendue.

### Exemple 2 : définir une stratégie d’exécution

Cet exemple montre comment définir une stratégie d’exécution pour l’ordinateur local.

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

L' `Set-ExecutionPolicy` applet de commande utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **RemoteSigned** . Le paramètre **scope** spécifie la valeur de portée par défaut, **LocalMachine**. Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .

### Exemple 3 : récupération de la stratégie d’exécution en vigueur

Cet exemple montre comment afficher la stratégie d’exécution effective pour une session PowerShell.

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

L' `Get-ExecutionPolicy` applet de commande utilise le paramètre **List** pour afficher la stratégie d’exécution de chaque étendue. L' `Get-ExecutionPolicy` applet de commande est exécutée sans paramètre pour afficher la stratégie d’exécution effective, **AllSigned**.

### Exemple 4 : débloquer un script pour l’exécuter sans modifier la stratégie d’exécution

Cet exemple montre comment la stratégie d’exécution **RemoteSigned** vous empêche d’exécuter des scripts non signés.

Une bonne pratique consiste à lire le code du script et à vérifier qu’il est sûr **avant** d’utiliser l’applet de commande `Unblock-File` . L' `Unblock-File` applet de commande débloque les scripts pour qu’ils puissent s’exécuter, mais ne modifie pas la stratégie d’exécution.

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

`Set-ExecutionPolicy`Utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **RemoteSigned** . La stratégie est définie pour l’étendue par défaut, **LocalMachine**.

L' `Get-ExecutionPolicy` applet de commande montre que **RemoteSigned** est la stratégie d’exécution effective pour la session PowerShell active.

Le script **Start-ActivityTracker.ps1** est exécuté à partir du répertoire actif. Le script est bloqué par **RemoteSigned** car le script n’est pas signé numériquement.

Pour cet exemple, le code du script a été révisé et vérifié comme étant sécurisé pour l’exécution. L' `Unblock-File` applet de commande utilise le paramètre **path** pour débloquer le script.

Pour vérifier que `Unblock-File` la stratégie d’exécution n’a pas été modifiée, `Get-ExecutionPolicy` affiche la stratégie d’exécution effective, **RemoteSigned**.

Le script **Start-ActivityTracker.ps1** est exécuté à partir du répertoire actif. Le script commence à s’exécuter, car il a été débloqué par l’applet de commande `Unblock-File` .

## PARAMÈTRES

### -List

Obtient toutes les valeurs de stratégie d'exécution pour la session dans l'ordre de priorité. Par défaut, `Get-ExecutionPolicy` obtient uniquement la stratégie d’exécution effective.

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

### -Étendue

Spécifie l’étendue qui est affectée par une stratégie d’exécution.

La stratégie d’exécution effective est déterminée par l’ordre de priorité comme suit :

- **MachinePolicy**. Défini par un stratégie de groupe pour tous les utilisateurs de l’ordinateur.
- **UserPolicy**. Défini par un stratégie de groupe pour l’utilisateur actuel de l’ordinateur.
- **Processus**. Affecte uniquement la session PowerShell active.
- **CurrentUser**. Affecte uniquement l’utilisateur actuel.
- **LocalMachine**. Étendue par défaut qui affecte tous les utilisateurs de l’ordinateur.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

`Get-ExecutionPolicy` n’accepte pas d’entrée du pipeline.

## SORTIES

### Microsoft.PowerShell.ExecutionPolicy

L’applet de commande retourne toujours les plateformes non **restreintes** sur les plateformes Linux et MacOS.

## REMARQUES

Une stratégie d’exécution fait partie de la stratégie de sécurité PowerShell. Les stratégies d’exécution déterminent si vous pouvez charger des fichiers de configuration, tels que votre profil PowerShell, ou exécuter des scripts. Et si les scripts doivent être signés numériquement avant leur exécution.

## LIENS CONNEXES

[about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)
