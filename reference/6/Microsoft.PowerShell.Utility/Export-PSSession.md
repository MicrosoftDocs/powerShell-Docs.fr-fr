---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 5bc474883029f59eda199a5d93ef8a229c0f887e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389213"
---
# Export-PSSession

## SYNOPSIS

Exporte les commandes d’une autre session et les enregistre dans un module PowerShell.

## SYNTAXE

### Tous

```
Export-PSSession [-OutputModule] <String> [-Force] [-Encoding <Encoding>]
 [[-CommandName] <String[]>] [-AllowClobber] [-ArgumentList <Object[]>]
 [-CommandType <CommandTypes>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-FormatTypeName] <String[]>] [-Certificate <X509Certificate2>] [-Session] <PSSession>
 [<CommonParameters>]
```

## DESCRIPTION

L' `Export-PSSession` applet de commande obtient les applets de commande, les fonctions, les alias et d’autres types de commandes à partir d’une autre session PowerShell (PSSession) sur un ordinateur local ou distant et les enregistre dans un module PowerShell. Pour ajouter les commandes du module à la session active, utilisez l’applet de commande `Import-Module` .

Contrairement à `Import-PSSession` , qui importe les commandes d’une autre session PSSession dans la session active, `Export-PSSession` enregistre les commandes dans un module. Les commandes ne sont pas importées dans la session active.

Pour exporter des commandes, utilisez l' `New-PSSession` applet de commande pour créer une session PSSession qui contient les commandes que vous souhaitez exporter. Utilisez ensuite l' `Export-PSSession` applet de commande pour exporter les commandes.

Pour éviter les conflits de noms de commande, la valeur par défaut de `Export-PSSession` est d’exporter toutes les commandes, à l’exception des commandes qui existent dans la session active. Vous pouvez utiliser le paramètre **CommandName** pour spécifier les commandes à exporter.

L' `Export-PSSession` applet de commande utilise la fonctionnalité de communication à distance implicite de PowerShell. Lorsque vous importez des commandes dans la session active, elles s’exécutent implicitement dans la session d’origine ou dans une session similaire sur l’ordinateur d’origine.

## EXEMPLES

### Exemple 1 : exporter des commandes à partir d’une session PSSession

Cet exemple crée une session PSSession à partir de l’ordinateur local vers l’ordinateur SERVEUR01. Toutes les commandes, à l’exception de celles qui existent dans la session active, sont exportées vers le module nommé SERVEUR01 sur l’ordinateur local. L’exportation comprend les données de mise en forme pour les commandes.

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

La `New-PSSession` commande crée une session PSSession sur l’ordinateur SERVEUR01. La session PSSession est stockée dans la `$S` variable. La `Export-PSSession` commande exporte les `$S` commandes et les données de mise en forme de la variable dans le module SERVEUR01.

### Exemple 2 : exporter les commandes extraire et définir

Cet exemple exporte toutes les `Get` `Set` commandes et à partir d’un serveur.

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

Ces commandes exportent les `Get` `Set` commandes et à partir d’un composant logiciel enfichable Microsoft Exchange Server sur un ordinateur distant vers un module Exchange dans le `$PSHOME\Modules` Répertoire de l’ordinateur local.
Le fait de placer le module dans le `$PSHOME\Modules` répertoire le rend accessible à tous les utilisateurs de l’ordinateur.

### Exemple 3 : exporter des commandes à partir d’un ordinateur distant

Cet exemple exporte des applets de commande à partir d’une session PSSession sur un ordinateur distant et les enregistre dans un module sur l’ordinateur local. Les applets de commande du module sont ajoutées à la session active afin qu’elles puissent être utilisées.

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

La `New-PSSession` commande crée une session PSSession sur l’ordinateur SERVEUR01 et l’enregistre dans la `$S` variable. La `Export-PSSession` commande exporte les applets de commande dont les noms commencent par test à partir de la session PSSession dans `$S` le module TestCmdlets sur l’ordinateur local.

L' `Remove-PSSession` applet de commande supprime la session PSSession dans `$S` de la session active. Cette commande montre que la session PSSession n’a pas besoin d’être active pour utiliser les commandes qui ont été importées à partir de la session. L' `Import-Module` applet de commande ajoute les applets de commande du module TestCmdlets à la session active. La commande peut être exécutée dans n’importe quelle session à tout moment.

L' `Get-Help` applet de commande obtient de l’aide pour les applets de commande dont les noms commencent par test. Une fois que les commandes d’un module sont ajoutées à la session active, vous pouvez utiliser les `Get-Help` applets de commande et `Get-Command` pour en savoir plus sur les commandes importées. L' `Test-Files` applet de commande a été exportée à partir de l’ordinateur SERVEUR01 et ajoutée à la session. L' `Test-Files` applet de commande s’exécute dans une session à distance sur l’ordinateur à partir duquel la commande a été importée. PowerShell crée une session à partir des informations stockées dans le module TestCmdlets.

### Exemple 4 : commandes Export et écrasé dans la session active

Cet exemple exporte les commandes qui sont stockées dans une variable dans la session active.

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

Cette `Export-PSSession` commande exporte toutes les commandes et toutes les données de mise en forme de la session PSSession dans la `$S` variable vers la session active. Le paramètre **AllowClobber** comprend des commandes portant le même nom que les commandes de la session active.

### Exemple 5 : exporter des commandes à partir d’une session PSSession fermée

Cet exemple montre comment exécuter les commandes exportées avec des options spéciales lorsque la session PSSession qui a créé les commandes exportées est fermée.

Si la session à distance d’origine est fermée lors de l’importation d’un module, le module utilisera toute session à distance ouverte qui se connecte à l’ordinateur d’origine. S’il n’existe aucune session active sur l’ordinateur d’origine, le module rétablit une session.

Pour exécuter les commandes exportées avec des options spéciales dans une session à distance, vous devez créer une session à distance avec ces options avant d’importer le module. Utiliser l' `New-PSSession` applet de commande avec le paramètre **SessionOption**

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

L' `New-PSSessionOption` applet de commande crée un objet **PSSessionOption** et enregistre l’objet dans la `$Options` variable. La `New-PSSession` commande crée une session PSSession sur l’ordinateur SERVEUR01.
Le paramètre **SessionOption** utilise l’objet stocké dans `$Options` . La session est stockée dans la `$S` variable.

L' `Export-PSSession` applet de commande exporte les commandes de la session PSSession dans `$S` vers le module SERVEUR01.
L' `Remove-PSSession` applet de commande supprime la session PSSession dans la `$S` variable.

L' `New-PSSession` applet de commande crée une session PSSession qui se connecte à l’ordinateur SERVEUR01. Le paramètre **SessionOption** utilise l’objet stocké dans `$Options` . L' `Import-Module` applet de commande importe les commandes à partir du module SERVEUR01. Les commandes du module sont exécutées dans la session PSSession sur l’ordinateur SERVEUR01.

## PARAMÈTRES

### -AllowClobber

Exporte les commandes spécifiées, même si elles ont les mêmes noms que les commandes dans la session active.

Si vous exportez une commande portant le même nom qu’une commande dans la session active, la commande exportée masque ou remplace les commandes d’origine. Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).

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

### -ArgumentList

Exporte la variante de la commande obtenue suite à l'utilisation des arguments spécifiés (valeurs de paramètre).

Par exemple, pour exporter la variante de la `Get-Item` commande dans le certificat (CERT :) dans la session PSSession dans `$S` , tapez `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Certificat

Spécifie le certificat client utilisé pour signer les fichiers de format (* .Format.ps1XML) ou les fichiers de module de script (. psm1) dans le module `Export-PSSession` créé par. Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.

Pour rechercher un certificat, utilisez l' `Get-PfxCertificate` applet de commande ou utilisez l' `Get-ChildItem` applet de commande dans le certificat (CERT :) unités. Si le certificat n'est pas valide ou n'a pas une autorité suffisante, la commande échoue.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandName

Exporte uniquement les commandes avec les noms ou les modèles de noms spécifiés. Les caractères génériques sont autorisés. Utilisez **CommandName** ou son alias, **Name**.

Par défaut, `Export-PSSession` exporte toutes les commandes de la session PSSession, à l’exception des commandes qui ont les mêmes noms que les commandes dans la session active. Cela empêche les commandes d’être masquées ou remplacées par les commandes dans la session active. Pour exporter toutes les commandes, y compris celles qui masquent ou remplacent d’autres commandes, utilisez le paramètre **AllowClobber** .

Si vous utilisez le paramètre **CommandName** , les fichiers de mise en forme des commandes ne sont pas exportés, sauf si vous utilisez le paramètre **FormatTypeName** . De même, si vous utilisez le paramètre **FormatTypeName** , aucune commande n’est exportée, sauf si vous utilisez le paramètre **CommandName** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### -CommandType

Exporte uniquement les types spécifiés d'objets de commande. Utilisez **CommandType** ou son alias, **Type**.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- Affecté. Tous les alias PowerShell dans la session active.
- Tout le monde. tous les types de commandes. C’est l’équivalent de `Get-Command -Name *` .
- console. Tous les fichiers autres que les fichiers PowerShell dans les chemins d’accès figurant dans la variable d’environnement PATH ( `$env:path` ), y compris les fichiers. txt,. exe et. dll.
- PolicySchedule. applets de commande dans la session active. Est l’applet de commande par défaut.
- Configuration. Une configuration PowerShell. Pour plus d’informations, consultez [about_session_configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).
- ExternalScript. Tous les fichiers. ps1 dans les chemins d’accès figurant dans la variable d’environnement PATH ( `$env:path` ).
- Filtre et fonction. Toutes les fonctions PowerShell.
- Script. blocs de script dans la session active.
- Flux. Un flux de travail PowerShell. Pour plus d’informations, consultez [about_Workflows](/powershell/module/PSWorkflow/About/about_Workflows.md).

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Spécifie le type de codage du fichier cible. La valeur par défaut est `utf8NoBOM`.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).
- `bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).
- `oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.
- `unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).
- `utf7`: Encode au format UTF-7.
- `utf8`: Encode au format UTF-8.
- `utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)
- `utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)
- `utf32`: Encode au format UTF-32.

À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ). Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Remplace un ou plusieurs fichiers de sortie existants, même si le fichier possède l'attribut de lecture seule.

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

### -FormatTypeName

Exportations les instructions de mise en forme uniquement pour les types Microsoft .NET Framework spécifiés. Entrez les noms des types. Par défaut, `Export-PSSession` exporte des instructions de mise en forme pour tous les types de .NET Framework qui ne sont pas dans l’espace de noms **System. Management. Automation** .

La valeur de ce paramètre doit être le nom d’un type retourné par une `Get-FormatData` commande dans la session à partir de laquelle les commandes sont importées. Pour récupérer toutes les données de mise en forme dans la session à distance, tapez `*` .

Si vous utilisez le paramètre **FormatTypeName** , aucune commande n’est exportée, sauf si vous utilisez le paramètre **CommandName** .

Si vous utilisez le paramètre **CommandName** , les fichiers de mise en forme des commandes ne sont pas exportés, sauf si vous utilisez le paramètre **FormatTypeName** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** . Consultez la section Notes du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié dans l’un des formats suivants :

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif. Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** . les deux paramètres s’excluent mutuellement.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

Exporte uniquement les commandes dans les modules et les composants logiciels enfichables PowerShell spécifiés. Entrez les noms de composant logiciel enfichable et de module. Les caractères génériques ne sont pas autorisés.

Pour plus d’informations, consultez `Import-Module` et [about_Pssnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputModule

Spécifie un chemin d’accès et un nom facultatifs pour le module créé par `Export-PSSession` . Le chemin d’accès par défaut est : `$home\Documents\WindowsPowerShell\Modules`. Ce paramètre est obligatoire.

Si le sous-répertoire du module ou l’un des fichiers `Export-PSSession` créés par est déjà présent, la commande échoue. Pour remplacer les fichiers existants, utilisez le paramètre **force** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

Spécifie la session PSSession à partir de laquelle les commandes sont exportées. Entrez une variable qui contient un objet de session ou une commande qui obtient un objet de session, tel qu’une `Get-PSSession` commande. Ce paramètre est obligatoire.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’objets vers `Export-PSSession` .

## SORTIES

### System. IO. FileInfo

`Export-PSSession` retourne une liste des fichiers qui composent le module qu’il a créé.

## REMARQUES

`Export-PSSession` s’appuie sur l’infrastructure de communication à distance PowerShell. Pour utiliser cette applet de commande, l'ordinateur doit être configuré pour la communication à distance. Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).

Vous ne pouvez pas utiliser `Export-PSSession` pour exporter un fournisseur PowerShell.

Les commandes exportées s'exécutent implicitement dans la session PSSession à partir de laquelle elles ont été exportées. Les détails de l’exécution des commandes à distance sont gérées entièrement par PowerShell. Vous pouvez exécuter les commandes exportées tout comme vous exécuteriez des commandes locales.

`Export-ModuleMember` capture et enregistre des informations sur la session PSSession dans le module qu’elle exporte. Si la session PSSession à partir de laquelle les commandes ont été exportées est fermée lorsque vous importez le module, et qu’il n’y a aucun sessions PSSession actif sur le même ordinateur, les commandes du module essaient de recréer la session PSSession. Si les tentatives de recréation de la session PSSession échouent, les commandes exportées ne sont pas exécutées.

Les informations de session `Export-ModuleMember` capturées et enregistrées dans le module n’incluent pas les options de session, telles que celles que vous spécifiez dans la `$PSSessionOption` variable de préférence ou à l’aide du paramètre **SessionOption** des `New-PSSession` applets de commande, `Enter-PSSession` ou `Invoke-Command` . Si la session PSSession d'origine est fermée quand vous importez le module, ce dernier utilisera une autre session PSSession sur le même ordinateur, si celle-ci est disponible. Pour permettre aux commandes importées de s'exécuter dans une session correctement configurée, créez une session PSSession avec les options que vous souhaitez avant d'importer le module.

Pour rechercher les commandes à exporter, `Export-PSSession` utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-Command` commande dans la session PSSession. Pour obtenir et enregistrer des données de mise en forme pour les commandes, elle utilise les `Get-FormatData` applets de commande et `Export-FormatData` . Vous pouvez voir des messages d’erreur de `Invoke-Command` ,, `Get-Command` `Get-FormatData` et `Export-FormatData` lorsque vous exécutez une `Export-PSSession` commande. En outre, `Export-PSSession` ne peut pas exporter des commandes à partir d’une session qui n’inclut pas les `Get-Command` applets de commande,, `Get-FormatData` `Select-Object` et `Get-Help` .

`Export-PSSession` utilise l' `Write-Progress` applet de commande pour afficher la progression de la commande. Vous pouvez voir la barre de progression pendant l'exécution de la commande.

Les commandes exportées présentent les mêmes restrictions que les autres commandes à distance, notamment l'impossibilité de démarrer un programme avec une interface utilisateur, tel que le Bloc-notes.

Étant donné que les profils PowerShell ne sont pas exécutés dans sessions PSSession, les commandes qu’un profil ajoute à une session ne sont pas disponibles pour `Export-PSSession` . Pour exporter des commandes à partir d’un profil, utilisez une `Invoke-Command` commande pour exécuter le profil dans la session PSSession manuellement avant d’exporter les commandes.

Le module que `Export-PSSession` crée peut inclure un fichier de mise en forme, même si la commande n’importe pas de données de mise en forme. Si la commande n'importe pas de données de mise en forme, les fichiers de mise en forme éventuellement créés ne contiennent pas de données de mise en forme.

## LIENS CONNEXES

[about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)

[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[Module d’importation](../Microsoft.PowerShell.Core/Import-Module.md)

[Import-PSSession](Import-PSSession.md)

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSSessionOption](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[Remove-PSSession](../Microsoft.PowerShell.Core/Remove-PSSession.md)
