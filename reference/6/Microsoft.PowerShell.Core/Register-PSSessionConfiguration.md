---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: ce52714d93cfce55ca36f89f16e37092b35c6b24
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204878"
---
# Register-PSSessionConfiguration

## SYNOPSIS
Crée et enregistre une configuration de session.

## SYNTAX

### NameParameterSet (par défaut)

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-SessionType <PSSessionType>]
 [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Register-PSSessionConfiguration` applet de commande crée et enregistre une nouvelle configuration de session sur l’ordinateur local. Il s’agit d’une applet de commande avancée que vous pouvez utiliser pour créer des sessions personnalisées pour les utilisateurs distants.

Chaque session PowerShell ( **PSSession** ) utilise une configuration de session, également appelée point de terminaison.
Quand les utilisateurs créent une session qui se connecte à l’ordinateur, ils peuvent sélectionner une configuration de session ou utiliser la configuration de session par défaut qui est inscrite lorsque vous activez la communication à distance PowerShell.
Les utilisateurs peuvent également définir la variable de préférence $PSSessionConfigurationName, qui spécifie une configuration par défaut pour les sessions à distance créées dans la session active.

La configuration de session définit l'environnement pour la session à distance. Cette configuration peut déterminer les commandes et les éléments de langage qui sont disponibles dans la session. Elle peut aussi inclure des paramètres qui protègent l'ordinateur, tels que ceux qui limitent la quantité de données que la session peut recevoir à distance dans un objet ou une commande unique. Le descripteur de sécurité de la configuration de session détermine quels utilisateurs sont autorisés à utiliser la configuration de session.

Vous pouvez définir les éléments de configuration en utilisant un assembly qui implémente une nouvelle classe de configuration, ainsi qu'un script qui s'exécute dans la session. À compter de PowerShell 3,0, vous pouvez également utiliser un fichier de configuration de session pour définir la configuration de session.

Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).
Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).

## EXEMPLES

### Exemple 1 : inscrire une configuration de session NewShell

Dans cet exemple, nous enregistrons la configuration de session **NewShell** . Les paramètres **AssemblyName** et **ApplicationBase** spécifient l’emplacement du fichier **MyShell.dll** , qui spécifie les applets de commande et les fournisseurs dans la configuration de session. Le paramètre **ConfigurationTypeName** spécifie la classe de configuration à utiliser à partir de l’assembly.

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

Pour utiliser cette configuration, tapez `New-PSSession -ConfigurationName newshell` .

### Exemple 2 : inscrire une configuration de session MaintenanceShell

Cet exemple enregistre la configuration de session **MaintenanceShell** sur l’ordinateur local. Le paramètre **StartupScript** spécifie le `Maintenance.ps1` script.

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

Quand un utilisateur utilise une `New-PSSession` commande et sélectionne la configuration **MaintenanceShell** , le `Maintenance.ps1` script s’exécute dans la nouvelle session. Le script peut configurer la session. Cela comprend l’importation de modules et la définition de la stratégie d’exécution pour la session. Si le script génère des erreurs, y compris des erreurs sans fin d’exécution, la `New-PSSession` commande échoue.

### Exemple 3 : inscrire une configuration de session

Cet exemple enregistre la configuration de session **AdminShell** .

La `$sessionParams` variable est une Hashtable contenant toutes les valeurs de paramètre. Ce Hashtable est passé à l’applet de commande à l’aide de la projection PowerShell. La `Register-PSSessionConfiguration` commande utilise le paramètre **SecurityDescritorSDDL** pour spécifier le SDDL dans la valeur de la `$sddl` variable et le paramètre **MaximumReceivedObjectSizeMB** pour augmenter la limite de taille d’objet. Elle utilise également le paramètre **StartupScript** pour spécifier un script qui configure la session.

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### Exemple 4 : retourner un élément de conteneur de configuration

Cet exemple montre comment inscrire la configuration **MaintenanceShell** .
`Register-PSSessionConfiguration` retourne un objet **WSManConfigContainerElement** stocké dans la `$s` variable. `Format-List` affiche toutes les propriétés de l’objet retourné. La propriété **PSPath** indique que l'objet est stocké dans un répertoire du lecteur WSMan:. `Get-ChildItem` (alias `dir` ) affiche les éléments dans le `WSMan:\LocalHost\PlugIn` chemin d’accès. Celles-ci incluent la nouvelle configuration **MaintenanceShell** et les deux configurations par défaut fournies avec PowerShell.

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### Exemple 5 : inscrire une configuration de session à l’aide d’un script de démarrage

Dans cet exemple, nous créons et enregistrons la configuration de session **WithProfile** . Le paramètre **StartupScript** indique à PowerShell d’exécuter le script spécifié pour toute session qui utilise la configuration de session.

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

Le script contient une commande unique qui utilise l'appel de source de type « dot sourcing » pour exécuter le profil **CurrentUserAllHosts** de l'utilisateur dans l'étendue actuelle de la session.

Pour plus d'informations sur les profils, consultez [about_Profiles](./About/about_Profiles.md). Pour plus d'informations sur l'appel de source de type « dot sourcing », consultez [about_Scopes](./About/about_Scopes.md).

## PARAMETERS

### -AccessMode

Active et désactive la configuration de session et détermine si elle peut être utilisée pour les sessions locales ou distantes sur l'ordinateur. Les valeurs valides pour ce paramètre sont :

- Désactivé. désactive la configuration de session. Elle ne peut pas être utilisée pour l'accès local ou distant à l'ordinateur.
- Local. Permet aux utilisateurs de l’ordinateur local d’utiliser la configuration de session pour créer une session de bouclage locale sur le même ordinateur, mais refuse l’accès aux utilisateurs distants.
- Distant. permet aux utilisateurs locaux et distants d'utiliser la configuration de session pour créer des sessions et exécuter des commandes sur l'ordinateur.

La valeur par défaut est Remote.

D’autres applets de commande peuvent remplacer la valeur de ce paramètre ultérieurement. Par exemple, l' `Enable-PSRemoting` applet de commande permet l’accès à distance à toutes les configurations de session, l’applet de commande `Enable-PSSessionConfiguration` active les configurations de session, et l' `Disable-PSRemoting` applet de commande empêche l’accès à distance à toutes les configurations de session.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationBase

Spécifie le chemin d’accès du fichier d’assembly ( \* . dll) qui est spécifié dans la valeur du paramètre **AssemblyName** . Utilisez ce paramètre quand la valeur du paramètre **AssemblyName** n'inclut pas de chemin d'accès. L'emplacement par défaut est le répertoire actif.

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssemblyName

Spécifie le nom d’un fichier d’assembly ( \* . dll) dans lequel le type de configuration est défini. Vous pouvez spécifier le chemin d’accès du fichier. dll dans ce paramètre ou dans la valeur du paramètre **ApplicationBase** .

Ce paramètre est obligatoire lorsque vous spécifiez le paramètre **ConfigurationTypeName** .

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationTypeName

Spécifie le nom qualifié complet du type Microsoft .NET Framework qui est utilisé pour cette configuration. Le type que vous spécifiez doit implémenter la classe **System.Management.Automation.Remoting.PSSessionConfiguration** .

Pour spécifier le fichier d’assembly ( \* . dll) qui implémente le type de configuration, spécifiez les paramètres **AssemblyName** et **ApplicationBase** .

La création d’un type vous permet de contrôler davantage d’aspects de la configuration de session, tels que l’exposition ou le masquage de certains paramètres des applets de commande, ou la définition de limites de taille d’objet et de taille des données que les utilisateurs ne peuvent pas remplacer.

Si vous omettez ce paramètre, la classe **DefaultRemotePowerShellConfiguration** est utilisée pour la configuration de session.

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Supprime toutes les invites utilisateur et redémarre le service **WinRM** sans demander confirmation. Le redémarrage du service permet d'appliquer la modification de configuration.

Pour éviter un redémarrage et supprimer l’invite de redémarrage, spécifiez le paramètre **NoServiceRestart** .

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

### -MaximumReceivedDataSizePerCommandMB

Spécifie une limite pour la quantité de données qui peut être envoyée à cet ordinateur dans une commande à distance unique. Entrez la taille des données en mégaoctets (Mo). La valeur par défaut est 50 Mo.

Si une limite de taille de données est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite figurant dans le type de configuration est utilisée et la valeur de ce paramètre est ignorée.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedObjectSizeMB

Spécifie une limite pour la quantité de données qui peuvent être envoyées à cet ordinateur dans un objet unique.
Entrez la taille des données en mégaoctets. La valeur par défaut est 10 Mo.

Si une limite de taille d'objet est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite figurant dans le type de configuration est utilisée et la valeur de ce paramètre est ignorée.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

Spécifie les modules qui sont importés automatiquement dans des sessions qui utilisent la configuration de session.

Par défaut, seul **Microsoft. PowerShell. Core** est importé dans les sessions. À moins que les applets de commande ne soient exclues, vous pouvez utiliser `Import-Module` pour ajouter des modules à la session.

Les modules spécifiés dans cette valeur de paramètre sont importés en compléments dans les modules spécifiés par le paramètre **SessionType** et ceux répertoriés dans la clé **ModulesToImport** du fichier de configuration de session ( `New-PSSessionConfigurationFile` ). Toutefois, les paramètres dans le fichier de configuration de session peuvent masquer les commandes exportées par les modules ou empêcher les utilisateurs de les utiliser.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un nom pour la configuration de session. Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoServiceRestart

Ne redémarre pas le service **WinRM** et supprime l’invite de redémarrage du service.

Par défaut, lorsque vous exécutez une `Register-PSSessionConfiguration` commande, vous êtes invité à redémarrer le service **WinRM** pour que la nouvelle configuration de session soit effective. Tant que le service **WinRM** n’est pas redémarré, la nouvelle configuration de session n’est pas effective.

Pour redémarrer le service **WinRM** sans demander confirmation, spécifiez le paramètre **force** . Pour redémarrer manuellement le service **WinRM** , utilisez l' `Restart-Service` applet de commande.

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

### -Path

Spécifie le chemin d’accès et le nom de fichier d’un fichier de configuration de session (. PSSC), tel que celui créé par `New-PSSessionConfigurationFile` . Si vous omettez le chemin d'accès, la valeur par défaut est le répertoire actif.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProcessorArchitecture

Détermine si une version 32 bits ou 64 bits du processus PowerShell est démarrée dans les sessions qui utilisent cette configuration de session. Les valeurs acceptables pour ce paramètre sont : x86 (32 bits) et AMD64 (64 bits). La valeur par défaut est déterminée par l'architecture de processeur de l'ordinateur qui héberge la configuration de session.

Vous pouvez utiliser ce paramètre pour créer une session 32 bits sur un ordinateur 64 bits. Échec des tentatives de création d'un processus 64 bits sur un ordinateur 32 bits.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSVersion

Spécifie la version de PowerShell dans les sessions qui utilisent cette configuration de session.

La valeur de ce paramètre est prioritaire sur la valeur de la clé **PowerShellVersion** dans le fichier de configuration de session.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsCredential

Spécifie des informations d’identification pour les commandes dans la session. Par défaut, les commandes s'exécutent avec les autorisations de l'utilisateur actuel.

Ce paramètre a été introduit dans PowerShell 3,0.

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

### -SecurityDescriptorSddl

Spécifie une chaîne SDDL (Security Descriptor Definition Language) pour la configuration.

Cette chaîne détermine les autorisations qui sont nécessaires pour utiliser la nouvelle configuration de session. Pour utiliser une configuration de session dans une session, les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour la configuration.

Si le descripteur de sécurité est complexe, envisagez d'utiliser le paramètre **ShowSecurityDescriptorUI** au lieu de ce paramètre. Vous ne pouvez pas utiliser les deux paramètres dans la même commande.

Si vous omettez ce paramètre, le SDDL racine pour le service **WinRM** est utilisé pour cette configuration.
Pour afficher ou modifier la chaîne SDDL racine, utilisez le fournisseur WSMan. Par exemple, `Get-Item wsman:\localhost\service\rootSDDL`. Pour plus d’informations sur le fournisseur WSMan, tapez `Get-Help wsman` .

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

### -SessionType

Spécifie le type de session créé à l'aide de la configuration de session. Les valeurs valides pour ce paramètre sont :

- Vide. Aucun module n’est ajouté à la session par défaut. Utilisez les paramètres de cette applet de commande pour ajouter des modules, fonctions, scripts et autres fonctionnalités à la session.
- Par défaut. Ajoute Microsoft. PowerShell. Core à la session. Ce module comprend l' `Import-Module` applet de commande que les utilisateurs peuvent utiliser pour importer d’autres modules, sauf si vous interdisez explicitement l’applet de commande.
- RestrictedRemoteServer. Comprend uniquement les applets de commande suivantes : `Exit-PSSession` , `Get-Command` , `Get-FormatData` , `Get-Help` ,, `Measure-Object` `Out-Default` et `Select-Object` . Utilisez un script ou un assembly, ou les clés figurant dans le fichier de configuration de session, pour ajouter des modules, des fonctions, des scripts et d'autres fonctionnalités à la session.

La valeur par défaut est Default.

La valeur de ce paramètre est prioritaire sur la valeur de la clé **SessionType** dans le fichier de configuration de session.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.PSSessionType
Parameter Sets: NameParameterSet
Aliases:
Accepted values: DefaultRemoteShell, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionTypeOption

Spécifie les options spécifiques au type pour la configuration de session. Entrez un objet d’options de type de session, tel que l’objet **PSWorkflowExecutionOption** retourné par l’applet de commande `New-PSWorkflowExecutionOption` .

Les options de sessions qui utilisent la configuration de session sont déterminées par les valeurs des options de session et par les options de configuration de session. Sauf indication contraire, les options définies dans la session, par exemple à l’aide de l’applet de commande `New-PSSessionOption` , sont prioritaires sur les options définies dans la configuration de session. Toutefois, les valeurs d'option de session ne peuvent pas dépasser les valeurs maximales définies dans la configuration de session.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowSecurityDescriptorUI

Indique que cette applet de commande affiche une feuille de propriétés qui vous aide à créer le SDDL pour la configuration de session. La feuille de propriétés s’affiche une fois que vous avez entré la `Register-PSSessionConfiguration` commande, puis redémarré le service **WinRM** .

Lorsque vous définissez les autorisations pour la configuration, n’oubliez pas que les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour utiliser la configuration de session dans une session.

Vous ne pouvez pas utiliser le paramètre **SecurityDescriptorSDDL** et ce paramètre dans la même commande.

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

### -StartupScript

Spécifie le chemin d’accès complet d’un script PowerShell. Le script spécifié est exécuté dans la nouvelle session qui utilise la configuration de session.

Vous pouvez utiliser le script pour configurer la session en plus. Si le script génère une erreur, même une erreur sans fin d’exécution, la session n’est pas créée et la `New-PSSession` commande échoue.

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

### -ThreadOptions

Spécifie la manière dont les threads sont créés et utilisés lors de l’exécution d’une commande dans la session. Les valeurs valides pour ce paramètre sont :

- Default
- ReuseThread
- UseCurrentThread
- UseNewThread

La valeur par défaut est **UseCurrentThread** .

Pour plus d’informations, consultez [énumération PSThreadOptions](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0).

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TransportOption

Spécifie l’option de transport.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSharedProcess

Utilisez un seul processus pour héberger toutes les sessions qui sont démarrées par le même utilisateur et utiliser la même configuration de session. Par défaut, chaque session est hébergée dans son propre processus.

Ce paramètre a été introduit dans PowerShell 3,0.

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

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Microsoft. WSMan. Management. WSManConfigContainerElement

## REMARQUES

Pour exécuter cette applet de commande, vous devez démarrer PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .

Cette applet de commande génère du code XML qui représente une configuration de plug-in WS-Management (Web Services for Management) et envoie le code XML à WS-Management, qui enregistre le plug-in sur l’ordinateur local ( `New-Item wsman:\localhost\plugin` ).

Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options. En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.

## LIENS CONNEXES

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[Fournisseur WSMan](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
