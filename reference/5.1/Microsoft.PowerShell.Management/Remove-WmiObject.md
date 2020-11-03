---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WmiObject
ms.openlocfilehash: 287eb02e7de2f4182e0ecfd7f6b6a7cafb66969e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203558"
---
# Remove-WmiObject

## SYNOPSIS
Supprime une instance d'une classe Windows Management Instrumentation (WMI) existante.

## SYNTAX

### classe (par défaut)

```
Remove-WmiObject [-Class] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### object

```
Remove-WmiObject -InputObject <ManagementObject> [-AsJob] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### path

```
Remove-WmiObject -Path <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### query

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### list

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description
L’applet de commande **Remove-WmiObject** supprime une instance d’une classe Windows Management Instrumentation (WMI) existante.

## EXEMPLES

### Exemple 1 : fermer toutes les instances d’un processus Win32

```
PS C:\> notepad
PS C:\> $np = Get-WmiObject -Query "select * from win32_process where name='notepad.exe'"
PS C:\> $np | Remove-WmiObject
```

Cet exemple ferme toutes les instances de Notepad.exe.

La première commande démarre une instance de Bloc-notes.

La deuxième commande utilise l’applet de commande Get-WmiObject pour récupérer les instances du Win32_Process qui correspondent à Notepad.exe, puis les stocke dans la variable $np.

La troisième commande passe l’objet dans la variable $np à **Remove-WmiObject** , qui supprime toutes les instances de Notepad.exe.

### Exemple 2 : supprimer un dossier

```
PS C:\> $a = Get-WMIObject -Query "Select * From Win32_Directory Where Name ='C:\\Test'"
PS C:\> $a | Remove-WMIObject
```

Cette commande supprime le dossier C:\Test.

La première commande utilise l’option **« obtenir-WmiObject »** pour interroger le dossier C:\test, puis stocke l’objet dans la variable $a.

La deuxième commande dirige la variable $a vers **Remove-WmiObject** , qui supprime le dossier.

## PARAMETERS

### -AsJob
Indique que cette applet de commande s’exécute en tant que tâche en arrière-plan.
Utilisez ce paramètre pour exécuter des commandes dont l'exécution nécessite beaucoup de temps.

De nouvelles applets de commande CIM, introduites dans Windows PowerShell 3.0, effectuent les mêmes tâches que les applets de commande WMI.
Les applets de commande CIM sont conformes aux normes WS-Management (WSMan) et à la norme Common Information Model (CIM), ce qui permet aux cmdlets d’utiliser les mêmes techniques pour gérer les ordinateurs qui exécutent le système d’exploitation Windows et ceux qui exécutent d’autres systèmes d’exploitation.
Au lieu d'utiliser **Remove-WmiObject** , songez à utiliser l'applet de commande Remove-CimInstancehttps://go.microsoft.com/fwlink/?LinkId=227964.

Quand vous utilisez le paramètre *AsJob* , la commande retourne un objet qui représente la tâche en arrière-plan, puis affiche l'invite de commandes.
Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche.
Si vous utilisez **Remove-WmiObject** sur un ordinateur distant, la tâche est créée sur l'ordinateur local, et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local.
Pour gérer le travail, utilisez les applets de commande qui contiennent le nom du **travail** (les applets de commande **Job** ).
Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.

Pour utiliser ce paramètre pour les ordinateurs distants, les ordinateurs locaux et distants doivent être configurés pour la communication à distance.
Démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.
Pour plus d'informations, consultez about_Remote_Requirements.

Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez about_Jobs et about_Remote_Jobs.

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

### -Authentification
Spécifie le niveau d’authentification à utiliser pour la connexion WMI.
Les valeurs valides pour ce paramètre sont :

- -1 : inchangé.
- 0 : Default.
- 1 : aucune.
Aucune authentification n’est effectuée.
- 2 : se connecter.
L’authentification est effectuée uniquement lorsque le client établit une relation avec l’application.
- 3 : appeler.
L’authentification est effectuée uniquement au début de chaque appel lorsque l’application reçoit la demande.
- 4 : paquet.
L’authentification est effectuée sur toutes les données reçues du client.
- 5 : PacketIntegrity.
Toutes les données transférées entre le client et l’application sont authentifiées et vérifiées.
- 6 : PacketPrivacy.
Les propriétés des autres niveaux d’authentification sont utilisées, et toutes les données sont chiffrées.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Autorité
Spécifie l'autorité à utiliser pour authentifier la connexion WMI.
Vous pouvez spécifier l'authentification Kerberos ou NTLM standard.
Pour utiliser NTLM, affectez au paramètre d'autorité la valeur ntlmdomain:\<DomainName\>, où \<DomainName\> identifie un nom de domaine NTLM valide.
Pour utiliser Kerberos, spécifiez Kerberos : \<DomainName\> \\ \<ServerName\> .
Vous ne pouvez pas inclure le paramètre d'autorité lorsque vous vous connectez à l'ordinateur local.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Classe
Spécifie le nom d’une classe WMI que cette applet de commande supprime.

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName
Spécifie le nom de l’ordinateur sur lequel cette applet de commande s’exécute.
La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ou de plusieurs ordinateurs.
Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.
Vous pouvez utiliser le paramètre *ComputerName* même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.
La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande Get-Credential.
Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges
Indique que cette applet de commande active toutes les autorisations de l’utilisateur actuel avant la commande qu’il effectue l’appel WMI.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Emprunt d’identité
Spécifie le niveau d'emprunt d'identité à utiliser.
Les valeurs valides pour ce paramètre sont :

- 0 : Default.
Lit le registre local pour le niveau d’emprunt d’identité par défaut, qui est généralement défini sur 3 : Impersonate.
- 1 : Anonymous.
Masque les informations d'identification de l'appelant.
- 2 : Identify.
Permet aux objets d'interroger les informations d'identification de l'appelant.
- 3 : Impersonate.
Permet aux objets d'utiliser les informations d'identification de l'appelant.
- 4 : Delegate.
Permet aux objets d'autoriser d'autres objets à utiliser les informations d'identification de l'appelant.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Spécifie un objet **ManagementObject** à utiliser comme entrée.
Lorsque ce paramètre est utilisé, tous les autres paramètres sont ignorés.

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### Paramètres régionaux
Spécifie les paramètres régionaux par défaut pour les objets WMI.
Les paramètres *régionaux* sont spécifiés sous la forme d’un tableau au \<LCID\> format MS_ dans l’ordre de préférence.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Espace de noms
Spécifie l’espace de noms de l’espace de stockage WMI dans lequel se trouve la classe WMI référencée lorsqu’elle est utilisée avec le paramètre de *classe* .

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Spécifie le chemin d'accès de l'objet WMI d'une classe WMI, ou spécifie le chemin d'accès de l'objet WMI d'une instance d'une classe WMI à supprimer.

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.
Ce paramètre est utilisé conjointement avec le paramètre *AsJob* .
La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

```yaml
Type: System.Int32
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

### System. Management. ManagementObject
Vous pouvez diriger un objet de gestion vers cette applet de commande.

## SORTIES

### Aucun, System. Management. Automation. RemotingJob
Cette applet de commande retourne un objet de traitement, si vous spécifiez le paramètre *AsJob* .
Sinon, elle ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Set-WmiInstance](Set-WmiInstance.md)
