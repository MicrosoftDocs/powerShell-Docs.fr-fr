---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Computer
ms.openlocfilehash: e3d1c5c071a334bddbfbc547ef2cc07e9e5c90aa
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388346"
---
# Add-Computer

## SYNOPSIS
Ajoutez l’ordinateur local à un domaine ou à un groupe de travail.

## SYNTAXE

### Domaine (par défaut)

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>]
 [-UnjoinDomainCredential <PSCredential>] -Credential <PSCredential> [-DomainName] <String> [-OUPath <String>]
 [-Server <String>] [-Unsecure] [-Options <JoinOptions>] [-Restart] [-PassThru] [-NewName <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Groupe de travail

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>] [-Credential <PSCredential>]
 [-WorkgroupName] <String> [-Restart] [-PassThru] [-NewName <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

L' `Add-Computer` applet de commande ajoute l’ordinateur local ou les ordinateurs distants à un domaine ou à un groupe de travail, ou les déplace d’un domaine à un autre. Elle crée également un compte de domaine si l’ordinateur est ajouté sans compte au domaine.

Vous pouvez utiliser les paramètres de cette applet de commande pour spécifier une unité d’organisation (OU, Organizational Unit) et un contrôleur de domaine ou pour exécuter une jonction non sécurisée.

Pour obtenir les résultats de la commande, utilisez les paramètres **Verbose** et **PassThru**.

## EXEMPLES

### Exemple 1 : ajouter un ordinateur local à un domaine, puis redémarrer l’ordinateur

```powershell
Add-Computer -DomainName Domain01 -Restart
```

Cette commande ajoute l’ordinateur local au domaine Domain01, puis redémarre l’ordinateur pour que le changement devienne effectif.

### Exemple 2 : ajouter un ordinateur local à un groupe de travail

```powershell
Add-Computer -WorkgroupName WORKGROUP-A
```

Cette commande ajoute l’ordinateur local au groupe de travail Workgroup-A.

### Exemple 3 : ajouter un ordinateur local à un domaine

```powershell
Add-Computer -DomainName Domain01 -Server Domain01\DC01 -PassThru -Verbose
```

Cette commande ajoute l’ordinateur local au domaine Domain01 à l’aide du contrôleur de domaine Domain01\DC01.

La commande utilise les paramètres **PassThru** et **Verbose** pour obtenir des informations détaillées sur les résultats de la commande.

### Exemple 4 : ajouter un ordinateur local à un domaine à l’aide du paramètre OUPath

```powershell
Add-Computer -DomainName Domain02 -OUPath "OU=testOU,DC=domain,DC=Domain,DC=com"
```

Cette commande ajoute l’ordinateur local au domaine Domain02.
Elle utilise le paramètre OUPath pour spécifier l’unité d’organisation des nouveaux comptes.

### Exemple 5 : ajouter un ordinateur local à un domaine à l’aide des informations d’identification

```powershell
Add-Computer -ComputerName Server01 -LocalCredential Server01\Admin01 -DomainName Domain02 -Credential Domain02\Admin02 -Restart -Force
```

Cette commande ajoute l’ordinateur Server01 au domaine Domain02. Elle utilise le paramètre **LocalCredential** pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter à l’ordinateur Server01. Elle utilise le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation de joindre des ordinateurs au domaine. Elle utilise le paramètre **Restart** pour redémarrer l’ordinateur à la fin de l’opération de jonction et le paramètre **Force** pour supprimer les messages de confirmation de l’utilisateur.

### Exemple 6 : déplacer un groupe d’ordinateurs vers un nouveau domaine

```powershell
Add-Computer -ComputerName Server01, Server02, localhost -DomainName Domain02 -LocalCredential Domain01\User01 -UnjoinDomainCredential Domain01\Admin01 -Credential Domain02\Admin01 -Restart
```

Cette commande déplace les ordinateurs Server01 et Server02, et l’ordinateur local, de Domain01 vers Domain02.

Elle utilise le paramètre **LocalCredential** pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter aux trois ordinateurs concernés. Elle utilise le paramètre **UnjoinDomainCredential** pour spécifier un compte d’utilisateur qui a l’autorisation de disjoindre les ordinateurs du domaine Domain01 et le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation de joindre les ordinateurs au domaine Domain02. Elle utilise le paramètre **Restart** pour redémarrer les trois ordinateurs une fois le déplacement terminé.

### Exemple 7 : déplacement d’un ordinateur vers un nouveau domaine et modification du nom de l’ordinateur

```powershell
Add-Computer -ComputerName Server01 -DomainName Domain02 -NewName Server044 -Credential Domain02\Admin01 -Restart
```

Cette commande déplace l’ordinateur Server01 vers le domaine Domain02 et remplace le nom d’ordinateur par Server044.

La commande utilise les informations d’identification de l’utilisateur actuel pour se connecter à l’ordinateur Server01 et le disjoindre de son domaine actuel. Elle utilise le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation de joindre l’ordinateur au domaine Domain02.

### Exemple 8 : ajouter des ordinateurs listés dans un fichier à un nouveau domaine

```powershell
Add-Computer -ComputerName (Get-Content Servers.txt) -DomainName Domain02 -Credential Domain02\Admin02 -Options Win9xUpgrade  -Restart
```

Cette commande ajoute les ordinateurs qui sont répertoriés dans le fichier Servers.txt au domaine Domain02. Elle utilise le paramètre **Options** pour spécifier l’option **Win9xUpgrade**. Le paramètre **Restart** redémarre tous les ordinateurs nouvellement ajoutés à la fin de l'opération de jonction.

### Exemple 9 : ajouter un ordinateur à un domaine à l’aide des informations d’identification prédéfinies de l’ordinateur

Cette première commande doit être exécutée par un administrateur à partir d’un ordinateur qui est déjà joint au domaine `Domain03` :

```powershell
New-ADComputer -Name "Server02" -AccountPassword (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)

# Then this command is run from `Server02` which is not yet domain-joined:

$joinCred = New-Object pscredential -ArgumentList ([pscustomobject]@{
    UserName = $null
    Password = (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)[0]
})
Add-Computer -Domain "Domain03" -Options UnsecuredJoin,PasswordPass -Credential $joinCred
```

Cette combinaison de commandes crée un nouveau compte d’ordinateur avec un nom prédéfini et un mot de passe de jointure temporaire dans un domaine à l’aide d’un ordinateur joint à un domaine existant. Ensuite, un ordinateur avec le nom prédéfini joint le domaine en utilisant uniquement le nom de l’ordinateur et le mot de passe de jointure temporaire.
Le mot de passe prédéfini est utilisé uniquement pour prendre en charge l’opération de jointure et est remplacé dans le cadre des procédures de compte d’ordinateur normales une fois que l’ordinateur a terminé la jonction.

## PARAMÈTRES

### -ComputerName

Spécifie les ordinateurs à ajouter à un domaine ou à un groupe de travail.
La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP (Internet Protocol) ou un nom de domaine complet de chacun des ordinateurs distants. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point ( `.` ) ou « localhost ».

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell. Vous pouvez utiliser le paramètre **ComputerName** de `Add-Computer` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

Ce paramètre est introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation de joindre les ordinateurs à un nouveau domaine.
La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`. Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

Pour spécifier un compte d’utilisateur qui a l’autorisation de supprimer l’ordinateur de son domaine actuel, utilisez le paramètre **UnjoinDomainCredential**. Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter à un ordinateur distant, utilisez le paramètre **LocalCredential**.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain, Workgroup
Aliases: DomainCredential

Required: True (Domain), False (Workgroup)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DomainName

Spécifie le domaine auquel les ordinateurs sont ajoutés. Ce paramètre est obligatoire lors de l’ajout des ordinateurs à un domaine.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DN, Domain

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Supprime la demande de confirmation de l’utilisateur. Sans ce paramètre, `Add-Computer` vous devez confirmer l’ajout de chaque ordinateur.

Ce paramètre est introduit dans Windows PowerShell 3.0.

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

### -LocalCredential

Spécifie un compte d’utilisateur qui a l’autorisation de se connecter aux ordinateurs spécifiés par le paramètre **ComputerName**. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`. Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

Pour spécifier un compte d’utilisateur qui a l’autorisation d’ajouter les ordinateurs à un nouveau domaine, utilisez le paramètre **Credential**. Pour spécifier un compte d’utilisateur qui a l’autorisation de supprimer les ordinateurs de leur domaine actuel, utilisez le paramètre **UnjoinDomainCredential**.

Ce paramètre est introduit dans Windows PowerShell 3.0.

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

### -NewName

Spécifie un nouveau nom pour l’ordinateur dans le nouveau domaine. Ce paramètre n’est valide que lorsqu’un ordinateur est ajouté ou déplacé.

Ce paramètre est introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Options

Spécifie les options avancées pour l’opération de jonction **Add-Computer** . Entrez une ou plusieurs valeurs dans une chaîne séparée par des virgules.

Les valeurs valides pour ce paramètre sont :

- **AccountCreate** : crée un compte de domaine. L’applet de commande **Add-Computer** crée automatiquement un compte de domaine lorsqu’il ajoute un ordinateur à un domaine. Cette option est incluse par exhaustivité.

- **Win9XUpgrade** : indique que l’opération de jointure fait partie d’une mise à niveau du système d’exploitation Windows.

- **UnsecuredJoin** : effectue une jointure non sécurisée. Pour demander une jointure non sécurisée, utilisez le paramètre *unsecure* ou cette option. Si vous souhaitez transmettre un mot de passe d’ordinateur, vous devez utiliser cette option conjointement avec l' `PasswordPass` option.

- **PasswordPass** : définit le mot de passe de l’ordinateur à la valeur du paramètre *Credential* (DomainCredential) après l’exécution d’une jointure non sécurisée. Cette option indique également que la valeur du paramètre *Credential* (DomainCredential) est un mot de passe d’ordinateur et non un mot de passe d’utilisateur. Cette option est valide uniquement lorsque l' `UnsecuredJoin` option est spécifiée. Lorsque cette option est utilisée, les informations d’identification fournies au `-Credential` paramètre *doivent* avoir un nom d’utilisateur null.

- **JoinWithNewName** : renomme le nom de l’ordinateur dans le nouveau domaine par le nom spécifié par le paramètre *NewName* . Lorsque vous utilisez le paramètre *NewName* , cette option est définie automatiquement. Cette option est conçue pour être utilisée avec l’applet de commande Rename-Computer. Si vous utilisez l’applet de commande **Rename-Computer** pour renommer l’ordinateur, mais que vous ne redémarrez pas l’ordinateur pour que la modification soit effective, vous pouvez utiliser ce paramètre pour joindre l’ordinateur à un domaine avec son nouveau nom.

- **JoinReadOnly** : utilise un compte d’ordinateur existant pour joindre l’ordinateur à un contrôleur de domaine en lecture seule. Le compte d’ordinateur doit être ajouté à la liste autorisée pour la stratégie de réplication de mot de passe et le mot de passe du compte doit être répliqué sur le contrôleur de domaine en lecture seule avant l’opération de jointure.

- **InstallInvoke** : définit les indicateurs de création (0X2) et de suppression (0x4) du paramètre **FJoinOptions** de la méthode **JoinDomainOrWorkGroup** . Pour plus d’informations sur la méthode **JoinDomainOrWorkGroup** , consultez [méthode JoinDomainOrWorkGroup de la classe Win32_ComputerSystem](/windows/win32/cimwin32prov/joindomainorworkgroup-method-in-class-win32-computersystem).
  Pour plus d’informations sur ces options, consultez [fonction NetJoinDomain](/windows/win32/api/lmjoin/nf-lmjoin-netjoindomain).

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: Microsoft.PowerShell.Commands.JoinOptions
Parameter Sets: Domain
Aliases:
Accepted values: AccountCreate, Win9XUpgrade, UnsecuredJoin, PasswordPass, DeferSPNSet, JoinWithNewName, JoinReadOnly, InstallInvoke

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OUPath

Spécifie une unité d’organisation pour le compte de domaine. Entrez le nom unique complet de l’unité d’organisation entre guillemets. La valeur par défaut est l’unité d’organisation par défaut des objets ordinateur du domaine.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: OU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourne un objet représentant l’élément que vous utilisez. Par défaut, cette applet de commande ne génère aucun résultat.

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

### -Restart

Redémarre les ordinateurs qui ont été ajoutés au domaine ou au groupe de travail. Un redémarrage est souvent nécessaire pour que le changement devienne effectif.

Ce paramètre est introduit dans Windows PowerShell 3.0.

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

### -Server

Spécifie le nom d’un contrôleur de domaine qui ajoute l’ordinateur au domaine. Entrez le nom sous la forme DomainName\ComputerName. Par défaut, aucun contrôleur de domaine n’est spécifié.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UnjoinDomainCredential

Spécifie un compte d’utilisateur qui a l’autorisation de supprimer les ordinateurs de leurs domaines actuels. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`. Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

Utilisez ce paramètre lorsque vous déplacez des ordinateurs vers un autre domaine. Pour spécifier un compte d’utilisateur qui a l’autorisation de joindre le nouveau domaine, utilisez le paramètre **Credential**. Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter à un ordinateur distant, utilisez le paramètre **LocalCredential**.

Ce paramètre est introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Non sécurisé

Exécute une jonction non sécurisée au domaine spécifié.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkgroupName

Spécifie le nom d'un groupe de travail auquel les ordinateurs sont ajoutés. La valeur par défaut est « WORKGROUP ».

```yaml
Type: System.String
Parameter Sets: Workgroup
Aliases: WGN

Required: True
Position: 0
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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger les noms d’ordinateurs et les nouveaux noms vers l’applet de commande `Add-Computer` .

## SORTIES

### Microsoft. PowerShell. Commands. ComputerChangeInfo

Quand vous utilisez le paramètre **PassThru** , `Add-Computer` retourne un objet **ComputerChangeInfo** .
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

- Dans Windows PowerShell 2,0, le paramètre de **serveur** de `Add-Computer` échoue même lorsque le serveur est présent. Dans Windows PowerShell 3.0, l’implémentation du paramètre **Server** est modifiée pour qu’il fonctionne de façon fiable.

## LIENS CONNEXES

[Checkpoint-Computer](Checkpoint-Computer.md)

[Remove-Computer](Remove-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Rename-Computer](Rename-Computer.md)

[Restore-Computer](Restore-Computer.md)

[Stop-Computer](Stop-Computer.md)

[Test-Connection](Test-Connection.md)
