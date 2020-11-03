---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: f8575c97c4279f285598e2b1bdf94786d92c841a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204726"
---
# Set-ExecutionPolicy

## SYNOPSIS
Définit les stratégies d’exécution de PowerShell pour les ordinateurs Windows.

## SYNTAX

### Tous

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Set-ExecutionPolicy` applet de commande modifie les stratégies d’exécution PowerShell pour les ordinateurs Windows. Pour plus d’informations, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).

À compter de PowerShell 6,0 pour les ordinateurs non-Windows, la stratégie d’exécution par défaut est **illimitée** et ne peut pas être modifiée. L' `Set-ExecutionPolicy` applet de commande est disponible, mais PowerShell affiche un message de console qui n’est pas pris en charge.

Une stratégie d’exécution fait partie de la stratégie de sécurité PowerShell. Les stratégies d’exécution déterminent si vous pouvez charger des fichiers de configuration, tels que votre profil PowerShell, ou exécuter des scripts. Et si les scripts doivent être signés numériquement avant leur exécution.

L' `Set-ExecutionPolicy` étendue par défaut de l’applet de commande est **LocalMachine** , ce qui affecte tous les utilisateurs de l’ordinateur. Pour modifier la stratégie d’exécution de **LocalMachine** , démarrez PowerShell avec **exécuter en tant qu’administrateur** .

Pour afficher les stratégies d’exécution pour chaque étendue dans l’ordre de priorité, utilisez `Get-ExecutionPolicy -List` . Pour afficher la stratégie d’exécution effective pour votre session PowerShell `Get-ExecutionPolicy` , utilisez sans paramètres.

## EXEMPLES

### Exemple 1 : définir une stratégie d’exécution

Cet exemple montre comment définir la stratégie d’exécution pour l’ordinateur local.

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
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

L' `Set-ExecutionPolicy` applet de commande utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **RemoteSigned** . Le paramètre **scope** spécifie la valeur de portée par défaut, **LocalMachine** . Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .

### Exemple 2 : définir une stratégie d’exécution qui est en conflit avec un stratégie de groupe

Cette commande tente de définir la stratégie d’exécution de l’étendue **LocalMachine** sur **Restricted** .
**LocalMachine** est plus restrictif, mais n’est pas la stratégie effective, car elle est en conflit avec une stratégie de groupe. La stratégie **restreinte** est écrite dans la ruche du Registre **HKEY_LOCAL_MACHINE** .

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

L' `Set-ExecutionPolicy` applet de commande utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **restreinte** . Le paramètre **scope** spécifie la valeur de portée par défaut, **LocalMachine** .
L' `Get-ChildItem` applet de commande utilise le paramètre **path** avec le fournisseur **HKLM** pour spécifier l’emplacement du Registre.

### Exemple 3 : appliquer la stratégie d’exécution d’un ordinateur distant à un ordinateur local

Cette commande obtient l’objet de stratégie d’exécution à partir d’un ordinateur distant et définit la stratégie sur l’ordinateur local. `Get-ExecutionPolicy` envoie un objet **Microsoft.PowerShell.ExecutionPolicy** dans le pipeline. `Set-ExecutionPolicy` accepte l’entrée de pipeline et ne nécessite pas le paramètre **ExecutionPolicy** .

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

L' `Invoke-Command` applet de commande est exécutée sur l’ordinateur local et envoie le **scriptblock** à l’ordinateur distant. Le paramètre **ComputerName** spécifie l’ordinateur distant **SERVEUR01** . Le paramètre **scriptblock** s’exécute `Get-ExecutionPolicy` sur l’ordinateur distant. L' `Get-ExecutionPolicy` objet est envoyé dans le pipeline au `Set-ExecutionPolicy` .
`Set-ExecutionPolicy` applique la stratégie d’exécution à l’étendue par défaut de l’ordinateur local, **LocalMachine** .

### Exemple 4 : définir l’étendue d’une stratégie d’exécution

Cet exemple montre comment définir une stratégie d’exécution pour une étendue spécifiée, **CurrentUser** . L’étendue **CurrentUser** affecte uniquement l’utilisateur qui définit cette étendue.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
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

`Set-ExecutionPolicy` utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **AllSigned** .
Le paramètre **scope** spécifie le **CurrentUser** . Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .

La stratégie d’exécution effective pour l’utilisateur devient **AllSigned** .

### Exemple 5 : supprimer la stratégie d’exécution de l’utilisateur actuel

Cet exemple montre comment utiliser la stratégie d’exécution **non définie** pour supprimer une stratégie d’exécution pour une étendue spécifiée.

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy` utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **non définie** .
Le paramètre **scope** spécifie le **CurrentUser** . Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .

### Exemple 6 : définir la stratégie d’exécution pour la session PowerShell active

L’étendue du **processus** affecte uniquement la session PowerShell active. La stratégie d’exécution est enregistrée dans la variable d’environnement `$env:PSExecutionPolicyPreference` et est supprimée lors de la fermeture de la session.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`Utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **AllSigned** . Le paramètre **scope** spécifie le **processus** de valeur. Pour afficher les paramètres de stratégie d’exécution, utilisez l' `Get-ExecutionPolicy` applet de commande avec le paramètre **List** .

### Exemple 7 : débloquer un script pour l’exécuter sans modifier la stratégie d’exécution

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

`Set-ExecutionPolicy`Utilise le paramètre **ExecutionPolicy** pour spécifier la stratégie **RemoteSigned** . La stratégie est définie pour l’étendue par défaut, **LocalMachine** .

L' `Get-ExecutionPolicy` applet de commande montre que **RemoteSigned** est la stratégie d’exécution effective pour la session PowerShell active.

Le script **Start-ActivityTracker.ps1** est exécuté à partir du répertoire actif. Le script est bloqué par **RemoteSigned** car le script n’est pas signé numériquement.

Pour cet exemple, le code du script a été révisé et vérifié comme étant sécurisé pour l’exécution. L' `Unblock-File` applet de commande utilise le paramètre **path** pour débloquer le script.

Pour vérifier que `Unblock-File` la stratégie d’exécution n’a pas été modifiée, `Get-ExecutionPolicy` affiche la stratégie d’exécution effective, **RemoteSigned** .

Le script **Start-ActivityTracker.ps1** est exécuté à partir du répertoire actif. Le script commence à s’exécuter, car il a été débloqué par l’applet de commande `Unblock-File` .

## PARAMETERS

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

### -ExecutionPolicy

Spécifie la stratégie d’exécution. S’il n’y a pas de stratégies de groupe et que la stratégie d’exécution de chaque étendue est définie sur non **définie, la** **restriction** devient la stratégie effective pour tous les utilisateurs.

Les valeurs de stratégie d’exécution acceptables sont les suivantes :

- **AllSigned** . Requiert que tous les scripts et fichiers de configuration soient signés par un éditeur approuvé, y compris les scripts écrits sur l’ordinateur local.
- **Ignorer** . rien n'est bloqué, et aucun avertissement, ni aucune invite ne s'affiche.
- **Par défaut** . Définit la stratégie d’exécution par défaut. **Limité** pour les clients Windows ou **RemoteSigned** pour les serveurs Windows.
- **RemoteSigned** . Requiert que tous les scripts et fichiers de configuration téléchargés à partir d’Internet soient signés par un éditeur approuvé. Stratégie d’exécution par défaut pour les ordinateurs Windows Server.
- **Limité** . Ne charge pas les fichiers de configuration ou n’exécute pas de scripts. La stratégie d’exécution par défaut des ordinateurs clients Windows.
- **Non défini** . Aucune stratégie d’exécution n’est définie pour l’étendue. Supprime une stratégie d’exécution affectée d’une étendue qui n’est pas définie par un stratégie de groupe. Si la stratégie d’exécution dans toutes les portées n’est **pas définie** , la stratégie d’exécution effective est **restreinte** .
- Non **restreint** . À compter de PowerShell 6,0, il s’agit de la stratégie d’exécution par défaut pour les ordinateurs non-Windows et ne peut pas être modifiée. charge tous les fichiers de configuration et exécute tous les scripts. Si vous exécutez un script non signé qui a été téléchargé à partir d’Internet, vous êtes invité à entrer l’autorisation avant son exécution.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Force

Supprime toutes les invites de confirmation. Soyez prudent avec ce paramètre pour éviter des résultats inattendus.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Étendue

Spécifie l’étendue qui est affectée par une stratégie d’exécution. La portée par défaut est **LocalMachine** .

La stratégie d’exécution effective est déterminée par l’ordre de priorité comme suit :

- **MachinePolicy** . Défini par un stratégie de groupe pour tous les utilisateurs de l’ordinateur.
- **UserPolicy** . Défini par un stratégie de groupe pour l’utilisateur actuel de l’ordinateur.
- **Processus** . Affecte uniquement la session PowerShell active.
- **CurrentUser** . Affecte uniquement l’utilisateur actuel.
- **LocalMachine** . Étendue par défaut qui affecte tous les utilisateurs de l’ordinateur.

L’étendue du **processus** affecte uniquement la session PowerShell active. La stratégie d’exécution est enregistrée dans la variable d’environnement `$env:PSExecutionPolicyPreference` , plutôt que dans le registre. Une fois la session PowerShell fermée, la variable et la valeur sont supprimées.

Les stratégies d’exécution de l’étendue **CurrentUser** sont écrites dans la ruche du Registre **HKEY_LOCAL_USER** .

Les stratégies d’exécution de l’étendue **LocalMachine** sont écrites dans la ruche du Registre **HKEY_LOCAL_MACHINE** .

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

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

### Microsoft.PowerShell.ExecutionPolicy, System. String

Vous pouvez diriger un objet de stratégie d’exécution ou une chaîne qui contient le nom d’une stratégie d’exécution vers `Set-ExecutionPolicy` .

## SORTIES

### Aucun

`Set-ExecutionPolicy` ne retourne aucune sortie.

## REMARQUES

`Set-ExecutionPolicy` ne modifie pas les étendues **MachinePolicy** et **UserPolicy** , car elles sont définies par des stratégies de groupe.

`Set-ExecutionPolicy` ne remplace pas un stratégie de groupe, même si la préférence de l’utilisateur est plus restrictive que la stratégie.

Si la stratégie de groupe **activer l’exécution du script** est activée pour l’ordinateur ou l’utilisateur, la préférence de l’utilisateur est enregistrée, mais elle n’est pas effective. PowerShell affiche un message expliquant le conflit.

## LIENS CONNEXES

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Unblock-File](../Microsoft.PowerShell.Utility/Unblock-File.md)
